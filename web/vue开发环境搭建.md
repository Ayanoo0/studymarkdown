# vue开发环境搭建<淘宝镜像>

## 1. 相关内容解释

### 1.1. vue.js简介

Vue (发音为 /vjuː/，类似 view) 是一款用于构建用户界面的JavaScript框架。

- Vue 只关注视图层， 采用自底向上增量开发的设计  
- Vue 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件。

### 1.2. node.js简介

Node.js 就是运行在服务端的 JavaScript

- Node.js 是一个基于 Chrome JavaScript 运行时建立的一个平台
- Node.js 是一个事件驱动 I/O 服务端 JavaScript 环境，基于 Google 的 V8 引擎，V8 引擎执行 Javascript 的速度非常快，性能非常好

### 1.3. npm简介

npm是随同NodeJS一起安装的包管理工具，能解决Node.JS代码部署上的很多问题，常见的使用场景有以下几种：

- 允许用户从npm服务器下载别人编写的第三方包到本地使用。
- 允许用户从npm服务器下载并安装别人编写的命令行程序到本地使用。
- 允许用户将自己编写的包或命令行程序上传到npm服务器供别人使用。
由于新版的nodejs已经集成了npm，所以之前npm也一并安装好了。

### 1.4. Cli简介

命令行界面（英语：command-line interface，缩写：CLI）是在图形用户界面得到普及之前使用最为广泛的用户界面，它通常不支持鼠标，用户通过键盘输入指令，计算机接收到指令后，予以执行。

#### 1.4.1. Vue Cli介绍

- Vue CLI 是一个基于 Vue.js 进行快速开发的完整系统。 使用Vue 脚手架之后我们开发的页面将是一个完整系统(项目)。
- vue/cli内嵌了webpack和webpack-dev-server对vue进行打包，所以vue/vli也只是在开发时依赖，搞清楚在哪里配置webpack规则即可。

#### 1.4.2. Vue Cli的优势

- 通过 vue-cli 搭建交互式的项目脚手架。
通过 @vue/cli + @vue/cli-service-global 快速开始零配置原型开发
- 一个运行时依赖 (@vue/cli-service)，该依赖：
  - 可升级;
  - 基于 webpack 构建，并带有合理的默认配置； webpack 前端打包工具 index.html vue组件 用户组件 学生组件 … 路由 dist目录
  - 可以通过项目内的配置文件进行配置； cli 项目配置文件 添加
  - 可以通过插件进行扩展。 cli 项目里
- 一个丰富的官方插件集合，集成了前端生态中最好的工具。 webpack打包工具===>dist目录 nodejs 服务器(tomcat java) 热部署插件 npm包
- 一套完全图形化的创建和管理 Vue.js 项目的用户界面

## 2. nodejs安装

### 2.1. 完成node.js的安装

- download url:`https://registry.npmmirror.com/binary.html?path=node/latest-v10.x/`，选择系统对应的版本，例如linux选择node-v10.24.1-linux-x64.tar.gz；
- windows选node-v10.24.1-x64.msi
- 默认安装
- 验证```node -v```

### 2.2. 配置node.js的环境变量

- 进入计算机高级属性，环境变量NODE_HOME=node.js的安装目录
- 下面系统变量中 PATH中添加%NODE_HOME%

### 2.3. 配置npm镜像

```sh
npm config set registry https://registry.npm.taobao.org
npm config get registry
```

### 2.4. 配置npm下载依赖的位置

- 查看nmp的prefix和cache的路径配置信息

```sh
npm config get cache
npm config get prefix
```

- 配置依赖下载位置

```sh
#路径为刚刚查出来的路径
npm config set cache "D:\nodereps\npm-cache" 
npm config set prefix "D:\nodereps\npm_global"
```

## 3. Vue及Vue-Cli 脚手架安装

```sh
#安装 vue
cnpm install vue -g
#卸载2.x版本脚手架
npm uninstall vue-cli -g
# 安装2.x版本脚手架
cnpm install vue-cli -g
#卸载3.x版本脚手架
cnpm install -g @vue/cli

npm install vue –g
 
npm install -g @vue/cli
 
npm uninstall vue-cli -g
 
npm uninstall vue-cli -g
 
cnpm install vue-cli -g
 
cnpm install -g @vue/cli
```
