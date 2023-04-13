# 基于现有web容器在服务器中部署web

## 1. 本地操作

> 目的：指明要部署的文件来源，以及各部分应该对应储存在服务器的什么位置

1.复制rp-web文件夹为testtsm-web。

- 具体解释：复制一个现有的同类型的部署文档，并更名为自己此次部署的内容。
- 目的：复制容器的环境配置以及打包指令。

2.根据所复制的项目，查看并修改package.sh中git的地址

- 如果是来源于同一个项目的不同分支，则直接查看package.sh中是否存在修改分支的指令
- $是指指令中的某一个参数
注：在直接收到的是dist文件时可直接用指令发送至服务器相应地址

```sh
scp dist.zip root@10.1.14.14:/data/appBins/dcep/rp-web/
```

-目的：让服务器能够拉到git中的项目

3.修改此项目下的nginx/conf.d/default.conf  修改端口（不同）和地址（服务器中实际存放的地址）即可

4.根据以上配置，修改docker-compose.yml 端口避免占用


5.提交修改

## 2. 服务器操作

```sh
# 6.连接服务器
ssh root@10.1.14.14
# 7.运行update拉取更新
cd /data
sh update.sh #./update.sh也一样
# 8.修改对package.sh的操作权限执行package.sh打包代码
cd /data/appBins/decp/testtsm-web
chmod a+x package.sh
.package.sh
# 9.服务器起服务
compose up -d
```

## 3. 将ssh公钥放入服务器

```sh
# 进入公钥存放路径
cd .ssh
# 使用vi编辑器 将公钥放入服务器访客ssh公钥路径
vi authorized_keys 
ese #进入编辑模式
#鼠标右键复制密钥
#进入编辑模式后保存并推出vi
:wq 
```