# 1. 什么是git

#### 简单的理解

* git是一个开源的分布式控制版本控制系统
* 可以有效记录每一次的修改提交操作
* 可以配合多个开发人员相互协调性的工作
* 可以将工程放在本地和远程操作

# 2.git与svn的区别

* git是分布式的，svn是集中式的，这个区别也是最为核心的区别：因为 Git 是分布式的，所以 Git 支持离线工作，在本地可以进行很多操作。而 SVN 必须联网才能正常工作。
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

#### 详细安装步骤如下：

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

# 4.git的基本配置
git提供了一个叫** git config** 的工具，它用于专门配置或读取相应的工作环境变量

在gGit安装之后需要进行一些基本信息设置：

a.设置用户名：

```
git config --global  user.name   【空格】"你在github上面注册的用户名"；
```

b.设置用户邮箱：

```
git config --global  user.email 【空格】 "你在github上面注册的用户邮箱"；
```

c.配置ok之后，我们用如下命令来看看是否配置成功:git config --list，或者在使用`vim ~/.gitconfig` 
命令,如果显示内容是下面信息，则配置成功

```
[http]
    postBuffer = 2M
[user]
    name = runoob
    email = test@runoob.com
  ```

#### 注意如下：
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
#### 补充：

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

# 5.git的核心概念

#### Git 最核心的一个概念就是工作流。

* 工作区(Workspace)是电脑中实际的目录: 主要执行添加，编辑，修改文件等动作。

* 暂存区(Index)类似于缓存区域，临时保存你的改动： 主要是暂存已经修改的文件最后统一提交到git仓库中。

* 仓库区(Repository)，分为本地仓库和远程仓库： 是最终确定文件保存到仓库，成为一个新的版本，并对他人可见。

####  简单的说,Git 工作的基本流程是：
* 克隆 Git 资源作为工作目录。
* 在克隆的资源上添加或修改文件。
* 如果其他人修改了，你可以更新资源。
* 在提交前查看修改。
* 提交修改。
* 如果发现错误，可以撤回提交并再次修改并提交。


# 6.GIT创建仓库（版本库）

#### 版本库的介绍（何为版本库）：

版本库又名也叫仓库，英文名repositotry,可以简单的理解为一个目录，这个目录里面的使用文件都被给git管理起来，每个文件的修改、删除，git都会实时记录下来，这样方便了将每个每个时刻的更改恢复。

*首先，选择一个合适的地方（我选择了D盘，我的电脑是Win 7），常见一个空目录：
```
$ cd D:      //切换到D盘
$ mkdir Git  //创建文件夹命令
$ cd Git     //切换到指定文件夹命令
$ git  init     //切换到指定文件夹命令
```
**注意**: 如果你使用Windows系统，为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文。

#### 1. 初始化本地git仓库（git init）
Git 使用 git init 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 git init 是使用 Git 的第一个命令。

在执行完成 git init 命令后，Git 仓库会生成一个 .git 目录，它是git进行跟踪和管理版本库，禁止修改删改此文件(如果没看到可能是您的电脑不显示隐藏文件,在命令行工具运行 ls -ah可查看);该目录包含了资源的所有元数据，其他的项目目录保持不变（不像 SVN 会在每个子目录生成 .svn 目录，Git 只在仓库的根目录生成 .git 目录）。


#### 2.把文件添加到版本库（git add <文件名>）

我们新建一个文件，如gitNOte.txt文件，内容随便编辑，不过内容尽可能的有价值，内容编辑好后，一定要放到 你刚才创建的Git目录下（子目录也行），因为这是一个Git仓库，放到其他地方Git再厉害也找不到这个文件。


将一个文件放到Git仓库需要二步：

(1)使用git add将文件添加到仓库：

  ```
$ git add gitNOte.txt
```


(2)使用git commit将文件提交到仓库：

```
git commit -m "提交内容说明"
```

注：git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

* git commit详解

commit可以一次提交多个自己想要指定提交的文件：
```
$ git add file1.txt
$ git add file2.txt
$ git add file3.txt
$ git commit -m "add 3 files."
```

也可以将全部文件添加

```
$ git add .   //将全部文件添加
$ git commit -m "将全部文件添加"
```

* git status详解

我们已经成功地添加并提交了一个gitNOte.txt文件，现在我想继续修改gitNOte.txtt文件，

(1).查看文件内容命令

```
cat  gitNOte.txt  //查看文件内容命令 
```

(2).编辑文件内容命令 

```
vi gitNOte.txt  //编辑文件内容命令 
```

修改完成后现在，运行git status命令看看结果：

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:  gitNOte.txt

no changes added to commit (use "git add" and/or "git commit -a")

```

这句话的大致意思是，你已经对gitNOte.txt文件进行了修改操作，，但还没有准备提交的修改，提交使用`使用“git add<file>`,放弃工作目录中的更改使用`git checkout -- <file> `

**注意**：前面讲了我们把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；
第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。
因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。

一旦提交后，如果你又没有对工作区做任何修改，那么工作区就是“干净”的,控制台将显示：

```
$ git status
On branch master
nothing to commit, working tree clean
```

* git diff(查看修改内容)
比如你想知道gitNOte.txt文件在上一次更新时做了哪些改动 ，所以，需要用git diff这个命令看看，这个命令会显示你没改动前和改动后的内容显示给你，形成对比。

#### 3.git回退到某个历史版本（版本回退）

* 使用`git log`命令查看所有的历史版本 

当你每提交一个更改时，会形成一个行新版本，实际上Git就会把它们自动串成一条时间线。如果使用可视化工具查看Git历史，就可以更清楚地看到提交历史的时间线

**注意**：最新的提交版本在最上面，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成`git reset –hard HEAD~100`。 如果觉得上面的 git log 显示的信息太多的话，可以使用命令 `git log --pretty = online `(注意是两个杠哦)


* 回滚到指定的版本
获取某个历史版本的id，假设查到历史版本的id是`139dcfaa558e3276b30b6b2e5cbbb9c00bbdca96`

```
git reset -- hard  139dcfaa558e3276b30b6b2e5cbbb9c00bbdca96

```

(3).把修改推到远程服务器(强制提交)

```
git push -u origin master
```

#### 4.回到现在（版本还原）
当你用$ git reset --hard HEAD^回退到过去版本时，再想恢复到回来，就必须找到你现在版本的id。Git提供了一个命令git reflog用来记录你的每一次命令：

**步骤1**.获取到版本号

```
git reflog
```


**步骤2**.根据显示的版本号回到现在

如我现在的版本号是：169dcfaa558e3276b30b6b2e5cbbb9c00bbdca96

```
git rest --hard  169dcfaa558e3276b30b6b2e5cbbb9c00bbdca96

```







