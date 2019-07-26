# 1. 什么是git

### 简单的理解

* git是一个开源的分布式控制版本控制系统
* 可以有效记录每一次的修改提交操作
* 可以配合多个开发人员相互协调性的工作
* 可以将工程放在本地和远程操作

# 2.git与svn的区别

* git是分布式的，svn是集中式的，这个区别也是最为核心的区别：因为 Git 是分布式的，所以 Git 支持离线工作，在本地可以进行很多操作，包括接下来将要重磅推出的分支功能。而 SVN 必须联网才能正常工作。
* 在易用性这方面，SVN相对于git会好得多，简单易上手，对新手很友好。而git的使用，必须要先了解git的一些基本命令，如git init 、git pull、git push等等...
* Git 没有一个全局的版本号，而 SVN 有：目前为止这是跟 SVN 相比 Git 缺少的最大的一个特征。

# 4.git的安装及其配置流程

要使用Git，第一步当然是安装Git了

#### 在Linux上安装Git
首先，你可以试着输入git，看看系统有没有安装Git：
```
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```
像上面的命令，有很多Linux会友好地告诉你Git没有安装，还会告诉你如何安装Git。

如果你碰巧用Debian或Ubuntu Linux，通过一条**sudo apt-get install git**就可以直接完成Git的安装，非常简单。

老一点的Debian或Ubuntu Linux，要把命令改为**sudo apt-get install git-core`**

如果是其他Linux版本，可以直接通过源码安装。先从Git官网下载源码，然后解压，依次输入：**./config，make，sudo make install**这几个命令安装就好了。

#### Mac 平台上安装
在 Mac 平台上安装 Git 最容易的当属使用图形化的 Git 安装工具，下载地址为：

http://sourceforge.net/projects/git-osx-installer/

#### Windows 平台上安装
###### 目前我个人的电脑用的是windows,所以我主要记录git在windows上面的安装操作
在 Windows 平台上安装 Git 同样轻松，有个叫做 msysGit 的项目提供了安装包，可以到 GitHub 的页面上下载 exe 安装文件并运行：

安装包下载地址：https://gitforwindows.org/

# 3.git的核心概念

### Git 最核心的一个概念就是工作流。

* 工作区(Workspace)是电脑中实际的目录。
* 暂存区(Index)类似于缓存区域，临时保存你的改动。
* 仓库区(Repository)，分为本地仓库和远程仓库。

