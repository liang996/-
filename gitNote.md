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

# 3.git的安装及其配置流程

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
  目前我个人的电脑用的是windows,所以我主要记录git在windows上面的安装操作
在 Windows 平台上安装 Git 同样轻松，有个叫做 msysGit 的项目提供了安装包，可以到 GitHub 的页面上下载 exe 安装文件并运行：

安装包下载地址：https://gitforwindows.org/ 或者直接搜索给git的安装

###### 详细安装步骤如下：

1.从git官网下一个git安装包。

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708094628081-1720506945.png)

2.点击git.exe安装程序，点击【next】

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708095223800-1578957376.png)

3、选择安装目录

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708095553956-959136009.png)

4、选择组件

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708095746081-2118617935.png)

5、开始菜单目录名设置

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708100131315-255359377.png)

6、选择使用命令行环境

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708100626534-974313591.png)

7、以下三步默认，直接点击下一步

![alt text](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708100920581-338347945.png)

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708101058815-844780321.png)

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708101627534-2061727948.png)

 8、安装完成
 
![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708102108237-112030650.png)

9、检验是否安装成功

回到电脑桌面，鼠标右击如果看到有两个git单词则安装成功

![](https://images2015.cnblogs.com/blog/810514/201707/810514-20170708104121206-372739.png)


# 4.git的核心概念

#### Git 最核心的一个概念就是工作流。

* 工作区(Workspace)是电脑中实际的目录: 主要执行添加，编辑，修改文件等动作。

* 暂存区(Index)类似于缓存区域，临时保存你的改动： 主要是暂存已经修改的文件最后统一提交到git仓库中。

* 仓库区(Repository)，分为本地仓库和远程仓库： 是最终确定文件保存到仓库，成为一个新的版本，并对他人可见。

#### 简单的说,Git 工作的基本流程是：
* 克隆 Git 资源作为工作目录。
* 在克隆的资源上添加或修改文件。
* 如果其他人修改了，你可以更新资源。
* 在提交前查看修改。
* 提交修改。
* 如果发现错误，可以撤回提交并再次修改并提交。

# 5.git的基本配置
git提供了一个叫** git config** 的工具，它用于专门配置或读取相应的工作环境变量

在gGit安装之后需要进行一些基本信息设置：
a.设置用户名：git config --global  user.name   【空格】"你在github上面注册的用户名"；

b.设置用户邮箱：git config --global  user.email 【空格】 "你在github上面注册的用户邮箱"；

c.配置ok之后，我们用如下命令来看看是否配置成功:git config --list，或者在使用`vim ~/.gitconfig` 
命令,如果显示内容是下面信息，则配置成功
```
[http]
    postBuffer = 2M
[user]
    name = runoob
    email = test@runoob.com
  ```

###### 注意如下：
* git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址.

* 设置用户名和用户邮箱时 ，一定不要忘记**打空格**，不然会报如下错误：
```
*** Please tell me who you are.  
Run
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
to set your account's default identity.
Omit --global to set the identity only in this repository.
fatal: unable to auto-detect email address (got 'Administrator@V92I2BPQSUKZBCB.(          
```
###### 补充：

git设置免密码登录,生成ssh秘钥命令

```
ssh-keygen -t rsa -C “<email>”
```
**步骤1**：命令输入完成后，一直回车。会在本地生成一个**.ssh**文件，打开该文件会看到默认保存位置当前   ~/.ssh/id_rsa（私密） 和id_rsa.pub（公密），将生成的公密用记事本打开，并复制。

**步骤2**：把id_rsa.pub里的复制内容添加到github的ssh keys里，一定不能有空格在密钥里面。

**测试连通性**：在git Bash 中输入以下代码
```
$ ssh -T git@github.com
```
当你输入以上代码时，会有一段警告代码，如：
```
The authenticity of host 'github.com (192.30.255.112)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
```
这是正常的，你输入 yes 回车既可。如果你创建 SSH key 的时候设置了密码，接下来就会提示你输入密码，如：
```
Enter passphrase for key '/home/jeremy/.ssh/id_rsa':
```
当然如果你密码输错了，会再要求你输入，直到对了为止。

密码正确后你会看到下面这段话，如：
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```
如果用户名是正确的,你已经成功设置SSH密钥。如果你看到 “access denied” ，则表示拒绝访问，那么你就需要使用 https 去访问，而不是 SSH 。

可以参考网站：
<a  href ="https://blog.csdn.net/haifeng_gu/article/details/72512026">git使用以及免密码登陆</a>
<a  href ="https://blog.csdn.net/chunyang_guo/article/details/12500577">解决每次push代码到github都需要输入用户名和密码的方法</a>
<a  href ="https://hetaoo.iteye.com/blog/2323944">git-ssh 配置和使用</a>

