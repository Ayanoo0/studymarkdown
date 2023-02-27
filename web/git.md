# Git

了解概念\_版本控制

## 1. 版本控制

> 版本控制:版本迭代,新的版本

- 版本控制(Revision control)是一种在开发的过程中用于管理我们对文件、目录或工程等内容的修改历史,方便查看更改历史记录,备份以便恢复以前的版本的软件工程技术
  - 实现跨区域多人协同开发
  - 追踪和记载一个或者多个文件的历史记录
  - 组织和保护你的源代码和文档
  - 统计工作量
  - 并行开发、提高开发效率
  - 跟踪记录整个软件的开发过程
  - 减轻开发人员的负担,节省时间,同时降低人为错误
- 简单说就是用于管理多人协同开发项目的技术
- 没有进行版本控制或者版本控制本身缺乏正确的流程管理,在软件开发过程中将会引入很多问题,如软件代码的一致性、软件内容的冗余、软件过程的事物性、软件开发过程中的并发性、软件源代码的安全性,以及软件的整合等问题
- 多人开发必须使用版本控制,否则代价较大

### 1.1. 常见的版本控制工具

- 主流的版本控制器如下:
  - Git
  - SVN(Subversion)
  - CVS(Concurrent Versions System)
  - VSS(Micorosoft Visual SourceSafe)
  - TFS(Team Foundation Server)
  - Visual Studio Online
- 版本控制产品非常的多(Perforce、Rational ClearCase、RCS(GNU Revision Control System)、Serena Dimention、SVK、BitKeeper、Monotone、Bazaar、Mercurial、SourceGear Vault),现在影响力最大且使用最广泛的是 Git 与 SVN

#### 1.1.1. Git 与 SVN 最主要区别

- SVN 是集中式版本控制系统,版本库是集中放在中央服务器的,而工作的时候,用的都是自己的电脑,所以首先要从中央服务器得到最新的版本,然后工作,完成工作后,需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作,对网络带宽要求较高
- Git 是分布式版本控制系统,没有中央服务器,每个人的电脑就是一个完整的版本库,工作的时候不需要联网了,因为版本都在自己电脑上。协同的方法是这样的:比如说自己在电脑上改了文件 A,其他人也在电脑上改了文件 A,这时,你们两之间只需把各自的修改推送给对方,就可以互相看到对方的修改了。Git 可以直接看到更新了哪些代码和文件
- Git 是目前世界上最先进的分布式版本控制系统

### 1.2. 版本控制分类

#### 1.2.1. 本地版本控制

- 记录文件每次的更新,可以对每个版本做一个快照,或是记录补丁文件,适合个人用,如 RCS
- ![img](./image/本地版本控制.png)

#### 1.2.2. 集中版本控制

- 所有的版本数据都保存在服务器上,协同开发者从服务器上同步更新或上传自己的修改

<a align="center">

- ![img](./image/集中版本控制.png)

<a/>
- 所有的版本数据都存在服务器上,用户的本地只有自己以前所同步的版本,如果不连网的话,用户就看不到历史版本,也无法切换版本验证问题,或在不同分支工作。而且,所有数据都保存在单一的服务器上,有很大的风险这个服务器会损坏,这样就会丢失所有的数据,当然可以定期备份。代表产品:SVN、CVS、VSS

#### 1.2.3. 分布式版本控制

- 每个人都拥有全部的代码\_安全隐患
- 所有版本信息仓库全部同步到本地的每个用户,这样就可以在本地查看所有版本历史,可以离线在本地提交,只需在连网时 push 到相应的服务器或其他用户那里。由于每个用户那里保存的都是所有的版本数据,只要有一个用户的设备没有问题就可以恢复所有的数据,但这增加了本地存储空间的占用
- 不会因为服务器损坏或者网络有问题,造成不能工作的情况
- ![img](./image/分布式版本控制.png)

## 2. Git 历史

- 同生活中的许多伟大事物一样，Git 诞生于一个极富纷争大举创新的年代
- Linux 内核开源项目有着为数众广的参与者。 绝大多数的 Linux 内核维护工作都花在了提交补丁和保存归档的繁琐事务上(1991－2002 年间)。到 2002 年，整个项目组开始启用一个专有的分布式版本控制系统 BitKeeper 来管理和维护代码
- 到了 2005 年，开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用 BitKeeper 的权力。这就迫使 Linux 开源社区(特别是 Linux 的缔造者 Linus Torvalds)基于使用 BitKeeper 时的经验教训，开发出自己的版本系统。也就是后来的 Git
- Git 是目前世界上最先进的分布式版本控制系统
- Git 是免费、开源的，最初 Git 是为辅助 Linux 内核开发的，来替代 BitKeeper
- ![img](./image/李纳斯·托沃兹.png)

## 3. Git 环境配置

### 3.1. 启动 Git

- Git Bash:Unix 与 Linux 风格的命令行
- Git CMD:Windows 风格命令行
- Git GUI:图形界面 Git

### 3.2. 基本 Linux 命令

```cmd
cd       #改变目录
cd . .   #回退到上一个目录,直接cd进入默认目录
pwd      #显示当前所在的目录路径
ls(ll)   #都是列出当前目录中的所有文件,只不过ll(两个ll)列出的内容更为详细
touch    #新建一个文件 如 touch index.js 就会在当前目录下新建一个index.js文件
rm       #删除一个文件, rm index.js 就会把index.js文件删除
mkdir    #新建一个目录,就是新建一个文件夹
rm -r    #删除一个文件夹, rm -r src 删除src目录
rm -rf / #删除电脑中全部文件
mv       #移动文件, mv index.html src index.html 是我们要移动的文件, src 是目标文件夹,当然, 这样写,必须保证文件和目标文件夹在同一目录下
reset    #重新初始化终端/清屏
clear    #清屏
history  #查看命令历史
help     #帮助
exit     #退出
#表示注释
```

### 3.3. Git 配置

```bash
git config -l #查看配置

#查看不同级别的配置文件
git config --system --list #查看系统config
git config --global --list #查看当前用户(global)配置
```

- Git 相关的配置文件:

1. Git\etc\gitconfig : Git 安装目录下的 gitconfig --system 系统级
2. C:\Users\Administrator\ .gitconfig : 只适用于当前登录用户的配置 --global 全局
   这里可以直接编辑配置文件,通过命令设置后会响应到这里

- 设置用户名及邮箱

```bash
git config --global user.name "刘志昊" #名称
git config --global user.email liuzh@bhz.com.cn #邮箱
```

## 4. Git 基本理论(核心)

> 工作区域

Git 本地有三个工作区域:工作目录(Working Directory)、暂存区(Stage/Index)、资源库(Repository 或 Git Directory),还有远程的 git 仓库(Remote Directory)。文件再在四个区域之间的转换关系如下:

![img](./image/工作区域.png)

- Workspace:工作区,就是你平时存放项目代码的地方
- Index/Stage:暂存区,用于临时存放你的改动,事实上它只是一个文件,保存即将提交到文件列表信息
- Repository:仓库区(或本地仓库),就是安全存放数据的位置,这里面有你提交到所有版本的数据。其中 HEAD 指向最新放入仓库的版本
- Remote:远程仓库,托管代码的服务器,可以简单的认为是你项目组中的一台电脑用于远程数据交换

本地的三个区域确切的说应该是 git 仓库中 HEAD 指向的版本:

![img](./image/HEAD指向的版本.png)

- Directory:使用 Git 管理的一个目录,也就是一个仓库,包含我们的工作空间和 Git 的管理空间
- WorkSpace:需要通过 Git 进行版本控制的目录和文件,这些目录和文件组成了工作空间
- .git:存放 Git 管理信息的目录,初始化仓库的时候自动创建
- Index/Stage:暂存区,或者叫待提交更新区,在提交进入 repo 之前,我们可以把所有的更新放在暂存区
- Local Repo:本地仓库,一个存放在本地的版本库;HEAD 会只是当前的开发分支(branch)
- Stash:隐藏,是一个工作状态保存栈,用于保存/恢复 WorkSpace 中的临时状态

> git 工作流程

git 工作流程一般为:

1. 在工作目录中添加、修改文件
2. 将需要进行版本管理的文件放入暂存区域
3. 将暂存区域的文件提交到 git 仓库

git 管理的文件有三种状态:已修改(modified),已暂存(staged),已提交(committed)

![img](./image/git工作流程.png)

## 5. Git 项目搭建

> 创建工作目录与常用指令

工作目录(WorkSpace)一般就是你希望 Git 帮助你管理的文件夹,可以是你项目的目录,也可以是一个空目录,建议不要有中文

日常使用只要记住下图 6 个命令:

![img](./image/6个命令.png)

> 本地仓库创建

创建本地仓库的方法有两种:一种就是创建全新的仓库,另一种就是克隆远程仓库

1. 创建全新的仓库,需要用 GIT 管理的项目的根目录执行:

   ```bash
   git init #在当前目录新建一个Git代码库
   ```

2. 执行后可以看到,仅仅在项目目录多出了一个.git 目录,关于版本等的所有信息都在这个目录里面

> 克隆远程仓库

1. 另一种方式是克隆远程目录,由于是将远程服务器上的仓库完全镜像一份至本地

   ```bash
   git clone [url] #克隆一个项目和它的整个版本信息
   ```

## 6. Git 文件操作

> 文件的 4 种状态

版本控制就是对文件的版本控制,要对文件进行修改、提交等操作,首先要知道文件当前在什么状态,不然可能会提交了现在还不想提交的文件,或者要提交的文件没提交上

- Untracked: 未跟踪, 此文件在文件夹中, 但并没有加入到 git 库, 不参与版本控制. 通过`git add`状态变为`Staged`
- Unmodify: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为`Modified`. 如果使用`git rm`移出版本库, 则成为`Untracked`文件
- Modified: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过`git add`可进入暂存`staged`状态, 使用`git checkout`则丢弃修改过, 返回到`unmodify`状态, 这个`git checkout`即从库中取出文件, 覆盖当前修改
- Staged: 暂存状态. 执行`git commit`则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为`Unmodify`状态. 执行`git reset HEAD filename`取消暂存, 文件状态为`Modified`

> 查看文件状态

通过如下命令可以查看文件状态:

```bash
#查看文件状态
git status [filename]
#查看文件状态
git status

git add . #添加所有文件到暂存区
git commit -m "commit" # 提交暂存区中的内容到本地仓库 -m 提交信息
```

> 忽略版本

不想将某些文件纳入版本控制中,如数据库文件、临时文件、设计文件等

在主目录下建立`.gitignore`文件,此文件有如下规则:

1. 忽略文件中的空格或以"#"开始的行将会被忽略
2. 可以使用 Linux 通配符,如星号(\*)代表任意多个字符,问号(？)代表一个字符,方括号([abc])代表可选字符范围,大括号({string1,string2,...})代表可选的字符串等
3. 如果名称的最前面有一个感叹号(!),表示例外规则,将不被忽略
4. 如果名称的最前面是一个路径分隔符(/),表示要忽略的文件在此目录下,而子目录中的文件不忽略
5. 如果名称的最后面是一个路径分隔符(/),表示要忽略的是此目录下该名称的子目录,而非文件(默认文件或目录都忽略)

```bash
# 为注释
*.txt     # 忽略所有的.txt文件
!lib      # 但lib.txt除外
/temp     # 仅忽略项目跟目录下的TODO文件,不包括其他目录temp
build/    # 忽略build/目录下的所有文件
doc/*.txt # 会忽略doc/noteds.txt但不包括doc/server/arch.txt
```

## 7. 使用码云

> github 有墙,国内一般使用 gitee,公司中会搭建自己的 git 服务器

码云使用方法:

1. 注册登录码云,完善个人信息
2. 设置本机绑定 SSH 公钥,实现免密登录

   ```bash
   # 进入 C:\Users\23032\.ssh 目录
   # 生成公钥  在git中生成
   ssh-keygen -t rsa
   ```

   本地创建并配置 config 文件

   在.ssh 目录下创建 config 文件,并添加如下内容

   ```bash
   # 远程仓库自定义名称,建议设置为仓库地址
   Host github.com
   # 远程仓库真实host
   HostName github.com
   # 权限认证类型,可设为publickey,password,keyboard-interactive等
   PreferredAuthentications publickey
   # 密钥文件地址
   IdentityFile C:\Users\23032\.ssh\github_id_rsa
   # 登录用户名
   User lbushisan@gmail.com

   # 第二个远程仓库的配置
   Host http://10.1.14.6:5080/
   HostName http://10.1.14.6:5080/
   PreferredAuthentications publickey
   IdentityFile C:\Users\23032\.ssh\id_rsa.pub
   User liuzh@bhz.com.cn
   ```

3. 将公钥信息 public key 添加到码云账户中

   ```sh
   cat ~/ssh/id rsa.pub #获得公钥
   再直接添加到个人设置中
   ```

4. 创建仓库

## 8. IDEA 中集成 Git

1. 新建项目,绑定 git
   - 将远程的 git 文件目录拷贝到项目中即可
2. 修改文件,使用 IDEA 操作 git
   - 添加到暂存区
   - commit 提交
   - push 到远程仓库

> 有道无术 术尚可求 有术无道 止于术

## 9. 说明:Git 分支

约等于电影中的平行宇宙，若两个平行宇宙互不干扰，则没什么影响。但在某个时间点下，两个宇宙合并了，则需要处理一些问题

![img](./image/git分支.png)

git 分支中常用的指令:

```bash
# 列出所有本地分支
git branch
# 列出所有远程分支
git branch -r
# 新建一个小分支，但依旧停留在当前分支
git branch [branch-name]
# 新建一个分支，并切换到该分支
git checkout -b [branch]
# 合并指定分支到当前分支
git merge [branch]
# 删除分支
git branch -d [branch-name]
# 删除远程分支
git push origin --delete [branch]
git branch -dr [remote/branch]
```

如果同一个文件在合并分支时都被修改了则会引起冲突：解决的办法是我们可以修改冲突文件后重新提交

master 主分支应该非常稳定，用来发布新版本，一般情况下不允许在上面工作，工作一般情况下在新建的 dev 分支上工作，工作完后，比如上要发布，或者说 dev 分支代码稳定后可以合并到主分支 master 上来

## 10. git 同步至多个仓库

```sh
# 新增上传url
git remote set-url --add origin #newUrl#
# 完成url新增后上传至所有
git push --all
```

## 11. ssh 密钥

### 11.1. 密钥介绍

> 密钥是通过加密算法得到的一个巨大的数字。可分为：

- 对称加密：只需要一把密钥
- 非堆成加密：需要两个密钥成对使用，分为公钥（public key）和私钥（private key）

### 11.2. ssh 密钥介绍

> SSH 密钥登录使用非对称加密

- 用户通过自己的密钥登录注意：私钥必须自己保存，不能泄漏，公钥则是公开，可以对外发送保存。
- 公钥和私钥是一对一的关系：只有对应的私钥才能解密对应公钥加密的数据。

### 11.3. ssh 密钥常用指令

```sh
#-t:tpye,类型，指密钥的加密算法（ed25519，rsa），默认rsa
ssh-keygen -t rsa
#-b:bits,数值越大安全性越高，一般1024或2048
ssh-keygen -b 1024
# 根目录下获取ssh公钥
cd ~  #回到根目录
# 进入ssh
cd  .ssh tab
#  查看公钥
cat ssh tab
```
