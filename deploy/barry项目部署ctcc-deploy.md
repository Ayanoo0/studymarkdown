# 1. 代码书写

1.开发完毕、本地测试、上传代码到GIT

2.git push

# 2. ctcc-depoly项目打包修改配置

1.appBins中创建项目目录

2.复制项目配置文件到指定目录

![image-20230321171038666](./项目部署ctcc-depoly/指定配置目录.png)

3.修改log4j2.xml文件字段，对应docker-compose中的特定**内部路径**：

![image-20230321171038666](./项目部署ctcc-depoly/log4j2修改.png)

![image-20230321171038666](./项目部署ctcc-depoly/docker服务配置.png)

4.修改backup备份项目配置，将路径改为新增项目路径：

![image-20230321171038666](./项目部署ctcc-depoly/backup修改.png)

5.package.sh详解：

```sh
#!/bin/sh

echo "backuping ..."

if [ -d "/data/appBaks/dcep/dcep-gateway/jar/" ];then
  echo ""
  else
  mkdir -p /data/appBaks/dcep/dcep-gateway/jar/
fi

# 备份 修改移动的项目路径
mv target/*.jar /data/appBaks/dcep/dcep-gateway/jar/

echo "done."

echo "packaging  ..."

mkdir -p workspace
cd workspace

# 下拉代码，注意分支名称，此处为master
git_par=$1
if [ -z "$git_par" ]; then
  git_par="-b master"
else
  git_par="-b $git_par"
fi
echo git执行参数:$git_par

# 项目git地址
git clone $git_par ssh://git@10.1.14.6:5022/bairx/dcep-gateway.git

# 进入项目
cd dcep-gateway/

# 每次删除重新下拉项目发布文件，刷新，为了避免发布版本号忘记迭代等发布问题
rm -rf /root/.m2/repository/com/bhz/sdictsm-common

# 跳过打包过程默认的test测试，由于测试环境可能有环境问题，莫名其妙出错。确认后台环境与开发环境一致后，跳过。
mvn package -Dmaven.test.skip=true

# 移动打包出来的jar到上级目录
cp target/dcep-gateway*.jar ../../target/

cd ../../

# 清空下拉依赖
rm -rf workspace

echo "done."

```

# 3. 配置docker-compose运行配置文件

```dockerfile
  # dcep/dcep-gateway
  dcep-gateway:
    image: service/springboot:latest			#镜像 同级目录images下
    hostname: dcep.dcep-gateway
    ports:																#端口设置  外网部(不可重复):内部(可重复，每一项docker容器相互独立)
      - 1288-1289:8080
    volumes:															#文件配置  外部路径：内部路径
      - /data/appDatas/dcep/dcep-gateway/volumns:/root/ctda/volumns
      - /data/appBins/dcep/dcep-gateway/target:/root/ctda/target
      - /data/appLogs/dcep/dcep-gateway:/root/ctda/log
    command: sh -c 'chmod a+x /root/ctda/target && cd /root/ctda/target/ && java -jar -server -Xms128m -Xmx256m dcep-gateway*.jar'								
    #授权使用java运行相关jar，java的jre环境是image，jar为外部生成。JRE+运行JAR==> service 相比传统 镜像==>service 每次修改上传的内容少，极大节省时间
    deploy:
      replicas: 2													#部署几个docker容器启动该服务 与上述ports的外部端口数量有关系 
      																		#此数量>=ports外部端口数量 随机启动相关端口号
```

2.-3.的打包修改与运行配置修改完成后，git push

# 4.服务器启动服务

1.ssh root@10.1.14.13登录服务器

2.cd /data

3../update.sh,运行脚本，更新depoly修改

4.cd appBins/[相关项目]/子目录，找到刚刚deploy中添加的package.sh

5.运行:./package.sh。若无权限，则增加权限:chmod a+x package.sh

6.首次部署服务:**compose up -d**，即新建全部应用，创建docker并启动。且不会覆盖已启动项目。

# 更新服务

1.本地修改项目代码，git push

2.服务器上重新打包项目，package.sh。(会从git上重新拉取业务更新代码)

3.restart相关服务service