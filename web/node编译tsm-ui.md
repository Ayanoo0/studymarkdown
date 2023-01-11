# README 编译vue工程tsm-ui前提

- node install；
- download url:`https://registry.npmmirror.com/binary.html?path=node/latest-v10.x/`，选择系统对应的版本，例如linux选择node-v10.24.1-linux-x64.tar.gz；
- windows选node-v10.24.1-x64.msi
- 由于tsm-ui需要使用node10进行编译，估选择老版本；

## 1. nodejs安装

```sh
# 进入安装目录
cd /usr/local
# 下载安装包
wget https://registry.npmmirror.com/-/binary/node/latest-v10.x/node-v10.24.1-linux-x64.tar.gz
# 解压
tar -xzvf node-v10.24.1-linux-x64.tar.gz
# 重命名
/usr/local/node-v10.24.1-linux-x64 /usr/local/node
```

## 2. 配置node环境变量

```sh
# 修改环境变量配置文件
vi /etc/profile
# 增加node/bin指令到PATH
export PATH=$PATH:/usr/local/node/bin
# 立即生效/etc/profile
source /etc/profile
```

## 3. 配软连接

```sh
# 相当于全局变量，在任何文件夹都能查看版本信息
ln -s /usr/local/node/bin/node /usr/local/bin/
ln -s /usr/local/node/bin/npm /usr/local/bin/
```

## 4. 验证安装

```sh
node -v
npm -v
```

## 5. vue工程打包

### 5.1. 一般步骤

```sh
# 进入项目根目录，包含package.json
cd tsm-ui/

# 下载依赖
npm install

# 编译
npm run build

# 启动
npm run serve
```

### 5.2. 异常处理

#### 5.2.1. 权限错误

- 错误报文：

```sh
gyp ERR! stack Error: EACCES: permission denied, mkdir'/ var / www / project_name / node_modules / node-sass / build'
```

- 处理方法：

- 尝试以下命令：

```sh
sudo npm i --unsafe-perm
```

- 如果不起作用，请尝试以下操作：

```sh
sudo rm -rf ~/.node-gyp
sudo npm cache clean -f
sudo npm install -g n
sudo n stable
sudo npm i --unsafe-perm
```

#### 5.2.2. gcc错误

- 错误报文：

```sh
gyp ERR! stack Error: `make` failed with exit code: 2
```

- 处理方法：

```sh
yum -y update gcc
yum -y install gcc+ gcc-c++
```

### 无法识别vue-cli-serve

- 错误报文：

```sh
 Error: 'vue-cli-service' 不是内部或外部命令，也不是可运行的程序 或批处理文件。
```

- 处理方法：

删除node_modules

```sh
npm i
```
