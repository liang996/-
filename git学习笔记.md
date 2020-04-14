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


# 6.GIT仓库基本操作（版本库）

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
你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

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
git reflog   //查看命令历史，以便确定要回到未来的哪个版本。 

```


**步骤2**.根据显示的版本号回到现在

如我现在的版本号是：169dcfaa558e3276b30b6b2e5cbbb9c00bbdca96

```
git rest --hard  169dcfaa558e3276b30b6b2e5cbbb9c00bbdca96

```

#### 5.撤销修改（git checkout --文件名称）

如果你在修改文件时，发现修改错了，想要撤销的话，可以使用以下命令：

```
git checkout --<file>     //file指的是文件的名称
```

命令git checkout -- gitNOte.txt意思就是，把gitNOte.txt文件在工作区的修改全部撤销，这里有两种情况：

一种是gitNOte.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是gitNOte.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次git commit或git add时的状态。

**注意1** ：git checkout -- <file>里面的双杠`--`不能漏掉，如果没有加，则又是一个命令的意思：切换到另一个分支命令

Git同样告诉我们，用命令git reset HEAD <file>可以把暂存区的修改撤销掉（unstage），重新放回工作区：
	
```
$ git reset HEAD  文件名
Unstaged changes after reset:
M	gitNOte.txt
git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。

```

**注意2** ：

* 当你只在工作区修改了文件内容，并且没有将该内容用`git add`命令添加到暂存区时，想直接丢弃工作区的修改时，适用于以下命令：

```
git checkout --file

```

* 当你只在工作区修改了文件内容，并且已经将该内容用`git add`命令添加到暂存区时，想丢弃修改，分两步，适用于以下命令：

（1）回到没有添加到暂存区之前

```
git reset HEAD  --<file>   //在Git中，用HEAD表示当前版本

```
（2）按照只在工作区修改了文件内容，没有将内容添加到暂存区的命令操作

```
git checkout --file

```


#### 6.删除文件（rm  文件名称）

一般情况下，你通常直接在文件管理器中把没用的文件删了，或者用rm命令删了：

```
rm  文件名                         //rm是remove单词的简称 （移除的意思）
```

Git知道你删除了文件，git status命令会立刻告诉你哪些文件被删除了，现在你有两个选择，一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit：

```
rm 文件名称
git status
git  rm 文件名称
git commit -m"移除文件"
```

**注意1.**：先手动删除文件，然后使用git rm <file>和git add<file>效果是一样的。
如果你不小心把不想删除的删除了，可以使用撤回命令.
	
```
git checkout --文件名称
```
	
**注意2.**：如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f

```
git rm -f <file>

```

**注意3.**：可以递归删除，即如果后面跟的是一个目录做为参数，则会递归删除整个目录中的所有子目录和文件：
```
git rm –r *   //建议这个命令不要轻易用
```
进入某个目录中，执行此语句，会删除该目录下的所有文件和子目录。


#### 7.文件移动或者重命名文件（mv ）

我们先把刚移除的 README 添加回来：
```	
$ git add gitNOte
```
然后对其重名:
```
$ git mv gitNOte  gitNOte.txt
$ ls
README.md
```


# 7.git远程仓库
Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。怎么分布呢？

好在这个世界上有个叫GitHub的神奇的网站，从名字就可以看出，这个网站就是提供Git仓库托管服务的，所以，只要注册一个GitHub账号，就可以免费获得Git远程仓库。

由于你的本地Git仓库和GitHub仓库之间的传输是通过SSH加密的，目的（为了确保数据传输的可靠性，因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的），如果你不配置相关命令，则每次本地仓库和远程仓库提交时，都需要验证密码，为了方便，所以，需要一点设置：

git设置免密码登录,生成ssh秘钥命令

#### 创建SSH Key

```
ssh-keygen -t rsa -C “<email>”
```
**步骤1**：命令输入完成后，一直回车。会在本地生成一个**.ssh**文件，打开该文件会看到默认保存位置当前   ~/.ssh/id_rsa（私密） 和id_rsa.pub（公密），将生成的公密用记事本打开，并复制。


**步骤2**：把id_rsa.pub里的复制内容添加到github的ssh keys里，一定不能有空格在密钥里面。
如下图：

![](https://www.liaoxuefeng.com/files/attachments/919021379029408/0)

“Add Key”，你就应该看到已经添加的Key：
![](https://www.liaoxuefeng.com/files/attachments/919021395420160/0)

点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容
![](https://images2015.cnblogs.com/blog/925240/201604/925240-20160423163456335-846446253.jpg
)

#### 测试连通性

在git Bash 中输入以下代码

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

**注意事项**：在GitHub上免费托管的Git仓库，任何人都可以看到喔（但只有你自己才能改）。所以，不要把敏感信息放进去，造成信息泄露。如果你不想让别人看到Git库，有两个办法，一是：让GitHub把公开的仓库变成私有的，这样别人就看不见了（不可读更不可写）。另一个办法是自己动手，搭一个Git服务器，因为是你自己的Git服务器，所以别人也是看不见的。


####　添加远程仓库（git　remote）
现在的情景是，你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。


首先，登陆GitHub，然后，在右上角找到“New repository”按钮，创建一个新的仓库：

![](https://images2015.cnblogs.com/blog/925240/201604/925240-20160423163533304-1142933178.jpg)

在Repository name填入ｓｔｕｄｙｇｉｔ，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库：

![](https://images2015.cnblogs.com/blog/925240/201604/925240-20160423155625991-435150420.jpg)

根据GitHub的提示，在本地的studygit仓库下运行命令

（１）将远程项目和本地项目进行关联
```
$ git remote add origin ＋　分支地址 //origin是远程库的名字，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库
```

（２）．第一次推送master分支的所有内容到远程仓库
```
$ git push -u origin master　　　//第一次提交需要这么做，第二次提交就可以直接用`git push origin master`或者 `git push `

```


把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样

#### 从远程库克隆（git clone）

使用 git clone 拷贝一个 Git 仓库到本地，让自己能够查看该项目，或者进行修改。

如果你需要与他人合作一个项目，或者想要复制一个项目，看看代码，你就可以克隆那个项目。 执行命令：
```
 git clone [url]   //[url] 为你想要复制的项目
 
```
克隆完成后，在当前目录下会生成一个新 目录，即会远程的目录名称。
***注意事项*：
要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。另外，Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。

#### Git 分支管理
几乎所有的版本控制系统都以某种形式支持分支。 使用分支意味着你可以把你的工作从开发主线上分离开来，以免影响开发主线。

有人把 Git 的分支模型称为必杀技特性，而正是因为它，将 Git 从版本控制系统家族里区分出来。

####  创建分支命令：
```
git branch 分支名称
```
####  切换分支命令:
```
git checkout (branchname)
```
当你切换分支的时候，Git 会用该分支的最后提交的快照替换你的工作目录的内容， 所以多个分支不需要多个目录。

####  创建并切换分支
git checkout命令加上-b参数表示创建并切换
```
git checkout -b + 分支名称
相当于以下两条命令
git branch 分支名称
git checkout (branchname)
```
####  列出分支基本命令：

```
git branch
```
没有参数时，git branch 会列出你在本地的分支,默认是master。
```
$ git branch
* master //意思是：有一个叫做 master 的分支，并且该分支是当前分支
```

如果需要查看每一个分支的最后一次提交，可以运行 git branch -v 命令：

如果我们要手动创建一个分支。执行 git branch (branchname) 即可。

```
$ git branch A  //A为分支名称
$ git branch
* master
  A
```
现在我们可以看到，有了一个新分支 A。

当你以此方式在上次提交更新之后创建了新分支，如果后来又有更新提交， 然后又切换到了 testing 分支，Git 将还原你的工作目录到你创建分支时候的样子。

使用分支将工作切分开来，从而让我们能够在不同开发环境中做事，并来回切换。

####  删除分支：
```
git breach -d 分支名称
```

例如我们要删除A分支：
```
$ git branch
* master
A
$ git branch -d A
Deleted branch A (was 85fc7e7).
$ git branch
* master
```
####  分支合并：
一旦某分支有了独立内容，你终究会希望将它合并回到你的主分支。 你可以使用以下命令将任何分支合并到当前分支中去：
```
git merge
```

切换回master分支后，把A分支的工作成果合并到master分支上：
```
$ git merge A
```
合并完后就可以删除分支:
```
$ git branch -d  A 
```
如果真的想要删除分支并丢掉那些工作，如同帮助信息里所指出的，可以使用 -D 选项强制删除它。

Git鼓励大量使用分支：
```


查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>
强制删除分支：git branch -D <name>
```

####  解决分支合并的冲突：

如果master分支和A分支各自都分别有新的提交，这种情况下，Git无法执行“快速合并”，只能试图把各自的修改合并起来，但这种合并就可能会有冲突，

Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容
再提交：
```
$ git add gitnote.txt 
$ git commit -m "conflict fixed"
[master cf810e4] conflict fixed

```

**注意**：
当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。

用git log --graph命令可以看到分支合并图。
  
####  多人协作：

当你从远程仓库克隆时，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且，远程仓库的默认名称是origin。

要查看远程库的信息，用`git remote`：
```
$ git remote
origin
```
或者，用`git remote -v`显示更详细的信息：
```
$ git remote -v
origin  git@github.com:michaelliao/learngit.git (fetch)
origin  git@github.com:michaelliao/learngit.git (push)
```
上面显示了可以抓取和推送的origin的地址。如果没有推送权限，就看不到push的地址。

####  推送分支：
推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：
```
$ git push origin master
```
如果要推送其他分支，比如dev，就改成：
```
$ git push origin dev
```

创建远程origin的dev分支到本地，于：
```
$ git checkout -b dev origin/dev
```


多人协作的工作模式通常是这样：

首先，可以试图用git push origin <branch-name>推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。

这就是多人协作的工作模式，一旦熟悉了，就非常简单。


# 8.git标签
发布一个版本时，我们通常先在版本库中打一个标签（tag），这样，就唯一确定了打标签时刻的版本。将来无论什么时候，取某个标签的版本，就是把那个打标签的时刻的历史版本取出来。所以，标签也是版本库的一个快照。你可以使用 git tag 给它打上标签。

####  创建标签

　　在Git中打标签非常简单，首先，切换到需要打标签的分支上
```
$ git branch -b master
Switched to branch 'master'  //切换到分支“master”
```
现在，我想为我的gitstudy 项目发布一个"1.0"版本。 我们可以用 git tag -a v1.0 命令给最新一次提交打上（HEAD）"v1.0"的标签。

指定标签并描述标签信息
	
```
$ git tag -a v1.0 -m “描述内容”
```
**注意1.**：-a 选项意为"创建一个带注解的标签",为标签名称，-m指定说明文字。 不用 -a 选项也可以执行的，但它不会记录这标签是啥时候打的，谁打的，也不会让你添加个标签的注解。 我推荐一直创建带注解的标签。　我们可以看到在提交对象信息上面，列出了此标签的提交者和提交时间，以及相应的标签说明





####  查看标签

默认标签是打在最新提交的commit上的。有时候，如果忘了打标签怎么办呢？方法是找到历史提交的commit id，然后打上就可以了

（1）.先用命令查看每次提交commit id

```
git log --oneline  //将会显示每次提交的commit id
```


（2）.比方说要对create b.txt这次提交打标签，它对应的commit id是9ac9296，敲入命令


```
git tag vo.9  9ac9296
```

**注意**，标签不是按时间顺序列出，而是按字母排序的。查看标签信息可以用以下命令：

（3）。可以用命令git tag查看所有标签：
```
$ git tag
v0.9
v1.0
```

（4）.可以用git show <tagname>查看标签信息


```
git show v1.0
```


####  删除标签

如果标签打错了，也可以删除
```
$ git tag -d  标签名称
```
因为创建的标签都只存储在本地，不会自动推送到远程。所以，打错的标签可以在本地安全删除。

　　默认情况下，git push并不会把标签传送到远端服务器上，只有通过显式命令才能推送标签到远端仓库
```
$ git push origin <tagname>
```
或者，一次性推送全部尚未推送到远程的本地标签
```
$ git push origin --tags
```
如果标签已经推送到远程，要删除远程标签就麻烦一点，先从本地删除
```
$ git tag -d  标签名称
```

然后，从远程删除。删除命令也是push，但是格式如下

```
git push origin  标签名称
```

最后一个问题，如何查看发送到远程的标签呢？

点击Github项目中的release即可看到。

# 8.忽略特殊文件

有些时候，你必须把某些文件放到Git工作目录中，但又不能提交它们，比如保存了数据库密码的配置文件啦，等等，这个时候，你急需要一个办法把不想提交的东西不上传到仓库。好在Git考虑到了大家的感受，这个问题解决起来也很简单，在Git工作区的根目录下创建一个特殊的.gitignore文件，然后把要忽略的文件名填进去，Git就会自动忽略这些文件。

#### 创建.gitignore文件

创建一个文件，文件名为：“.gitignore.”,注意前后都要有一个点，保存之后系统会自动重命名为“.gitignore”。或者用git bush创建touch.gitignore在文件夹就生成了一个“.gitignore”文件。

####  配置语法：

以问号“？”通配单个字符

以星号“*”通配多个字符

以斜杠“/”开头表示目录

以方括号“【】”包括单个字符的匹配列表；

以叹号“！”表示不忽视匹配到的文件或目录；

此外。git对于.ignore配置文件是按照从上往下进行匹配的，意思就是如果前面的规则匹配的范围更大，则后面的规则将不会生效。

####  举例：
（1）规则： fd1/*
　　说明：忽略目录 fd1 下的全部内容；注意，不管是根目录下的 /fd1/ 目录，还是某个子目录 /child/fd1/ 目录，都会被忽略；


（2）规则：/fd1/*
　　说明：忽略根目录下的 /fd1/ 目录的全部内容；


（3）规则：
    /*
    !.gitignore
    !/fw/bin/
    !/fw/sf/
    
 说明：忽略全部内容，但是不忽略 .gitignore 文件、根目录下的 /fw/bin/ 和 /fw/sf/ 目录；




