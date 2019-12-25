---
typora-root-url: img-git
---

## Git

### 1.Git的起源

#### “自由主义教皇”林纳斯·托瓦兹

“有些人生来就具有统率百万人的领袖风范；另一些人则是为写出颠覆世界的软件而生。唯一一个能同时做到这两者的人，就是托瓦兹。”美国《[时代](https://baike.baidu.com/item/%E6%97%B6%E4%BB%A3/1944848)》周刊对“[Linux](https://baike.baidu.com/item/Linux/27050)之父”林纳斯·托瓦兹（Linus Torvalds）给出了极高的评价。

1969 年，Linus Torvalds 生于芬兰一个知识分子家庭。父亲 Nils Torvalds 毕业于赫尔辛基大学，是一名活跃的电台记者。母亲 Anna Torvalds 同样毕业于赫尔辛基大学，也是一名记者。有趣的是，他的祖父奥 Ole Torvalds 也是一名记者。除此之外，**Torvalds 的外祖父 Leo Tornqvist 是芬兰第一批统计学教授**。优秀的家庭背景为 Torvalds 奠定了接受良好教育的基础。**Torvalds 在 11 岁时，应其外祖父要求用 BASIC 语言编写一些统计学方面的小程序**。大众普遍认为，这是他编程经历之始。

1988年，Torvalds 进入赫尔辛基大学计算机科学系就读。在兴趣的趋势下，**Torvalds 创造并发布了自制的操作系统，并将其命名为 Linux**。1996 年硕士毕业并移居美国，后拥有美国国籍。2003 年，为专心维护 Linux 从全职公司辞职。

芬兰人性格内敛，这与 Torvalds 的行事方式不谋而合。但他对开源的信念是近乎执着的，为此不少树敌。

> 赫尔辛基大学，成立于1640年，是芬兰最大且历史最悠久的最高学府。Torvalds 一家三口都毕业于此。



#### 与 BitKeeper 分道扬镳：git 诞生的导火索

在 git 诞生之前，Torvalds 选择使用 BitKeeper 进行 Linux 版本管理。BitKeeper 是一个闭源的商业软件，这个决定长期受到社区的质疑和争议。

2005 年，一位 Linux 开发成员 Andrew（Samba 协议之父）写了一个可以连接 BitKeeper 仓库的外挂，因此 BitMover 公司（BitKeeper 持有者）认为他反编译了 BitKeeper。BitMover 决定中止 Linux 免费使用 BitKeeper 的授权。最终 Linux 团队与 BitMover 磋商无果，Torvalds 决定开发自己的版本管理系统。

**十天后，git 诞生了。**

你没有看错。git 从开始到诞生，Torvalds 这位天才只用了 10 天的时间。

#### 极具前瞻性的三个诉求

在确定开发 git 前，Torvalds 对市面上多个版本管理方案进行过评估，但现有的方案都不令人满意，最终决定开发自己的版本管理系统。

Torvalds 认为，**健壮的版本管理系统应当有以下三个特性**：

- 可靠性（reliable）
- 高效（high-performance）
- 分布式（distributed）

**这三个特性，被视为 git 的核心灵魂所在，深远的影响了 git 及其他 SCM 的后续发展**。

**可靠性（reliable）**

**数据的存入取出必须是安全的、一致的。所有行为都要校验，仓库任何部分不允许篡改。**在今天看来，这并不是什么高明之举，但在当时，绝大多数的 SCM 都做不到这一点。那时候，人们依赖保护中央服务器来保证数据不被篡改，而不是依靠版本管理自身的设计来保证。

Torvalds 认为，应当通过算法来保证，仓库任何一个字节被篡改，都能够被发现。

**高效（high-performance）**

这是 git 极具优势的特性。Torvalds 认为，**版本管理的所有操作都必须在毫秒级内完成**：这是对 svn 最大的批评。查日志、拉分支、合并、提交这些高频率操作，必须能够在本地能够完成，而不是等待服务器响应。这一特性直接决定了 git 能够被广泛传播。

作为对比，svn 每一步操作都在等待数据包成为了人们口中的诟病。

**分布式（distributed）**

以往人们在备份资料上花了很大精力：传统的中央服务器，资料受损是灾难性事故。现在，**所有人电脑中的 git 仓库都是一致的，每个人的仓库都是完整的副本**。完整的副本意味着可以在本地做所有事；允许相互同步促使它被设计成为自带数据校验。

最终，Torvalds 围绕着这三个诉求，用 10 天的时间创造出 git。

事实证明，这些想法是极具前瞻性的。git 在解决原有诉求的前提下，还解决了长久以来的一些痛点。

#### 刺破痛点

从工程的角度看，许多 SCM 方案都有各自的杀手锏，例如 BitKeeper 在超大型项目的优越性能，以及 SVN 精准的权限控制。但在实际生产方面，则有所欠缺。

**代码政治**

**大多数 SCM 都存在权限争议问题，特别是在超大型项目上**。开发者最常见的发问是，你凭啥不给我权限？在有些企业，代码管理被沦为政治工具，权限则被视为权利的象征。分布式的 git 则不存在此问题，如果你拥有该仓库，你就拥有了所有的权限。

**提交粒度**

**如果「提交代码」容易对他人造成影响，那么就没人愿意频繁提交**。在开发阶段，由于代码始终无法完美（例如，包含测试代码、代风格错误、还有待改动），以至于总是无法提交代码（强行提交将造成他人无法运行）。导致的结果是，大量改动堆积，最后一次性提交。这样的后果是，单个 commit 提交粒度极大，还会导致合并、code review、乃至回滚的困难。而 git 的 commit 操作不需要推送到远程，因此随意提交也不会不影响他人。

**创建新分支**

在许多 SCM，创建新分支是「重量级操作」，并且所有人可见。在许多项目看来，创建新分支是重大行为。因为**创建新分支影响重大，因此开发人员不会随意创建新分支。这直接导致了同一个分支上需要承载大量的业务**。而由于 git 的操作是本地化的，你可以随意创建分支（毫秒级操作）并行多个子迭代，迭代完毕且合并分支后，再删除分支标签。最后推送到远程服务器，他人并不知晓你创建过什么分支。

#### 开源，共筑，影响力

**革新总是艰难的**。当 Linux 开发团队决定使用 git 作为版本管理的时候，社区反对声音并不小，理由是 git 太难用了。实际上，确实是这样的，Torvalds 也承认了这点。

技术服众还不够。Torvalds 的领导力是惊人的，他发动社区力量让大家投入到 git 的开发当中。随着开发的深入，git 命令变得更简单，更易用。另一方面，开源有助于集思广益，并且避免腐败。

后来的事，大家都知道了。git 逐渐被大众接受，为 git 提供托管服务的 github 于 2008 年 2 月上线，从此 git 点亮万家灯火。

另外，2016 年 5 月，BitKeeper 宣布以 Apache 2.0 许可证开源。但人们说，太晚了。

Torvalds 与妻子 Tove 育有三名孩子。Tove 曾获得六次芬兰空手道冠军头衔。

2000 年，在时代 100 人：本世纪最重要的人物投票中，他位居第 17 名。

2004 年，他被评为世界最有影响力的人之一。

2010 年，宣誓成为美国公民。

2018 年 10 月，在休假反省一个多月之后，Torvalds 继续接管内核开发。Torvalds 在维护项目上一向言行激烈，不少人因此而受到伤害。他表示「对自己过去的行为表示反悔，对因为他的言行而受到伤害的人表示道歉」。



发明了Linux系统(22岁发明的).发明了Git,免费,开源

window和mac都是系统

#### Linux

[Linux](https://baike.baidu.com/item/Linux)是一类Unix计算机操作系统的统称。Linux操作系统的[内核](https://baike.baidu.com/item/%E5%86%85%E6%A0%B8)的名字也是“Linux”。Linux操作系统也是自由软件和[开放源代码](https://baike.baidu.com/item/%E5%BC%80%E6%94%BE%E6%BA%90%E4%BB%A3%E7%A0%81)发展中最著名的例子。严格来讲，Linux这个词本身只表示Linux内核，但在实际上人们已经习惯了用Linux来形容整个基于Linux内核，并且使用GNU 工程各种工具和数据库的操作系统。

#### Git

Git是目前世界上最先进的分布式版本控制系统（没有之一）。

Git 是用于 Linux[内核](https://baike.baidu.com/item/%E5%86%85%E6%A0%B8)开发的[版本控制](https://baike.baidu.com/item/%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6)工具

Git是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。 

Git 是 [Linus Torvalds](https://baike.baidu.com/item/Linus%20Torvalds/9336769) 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

优点：

适合[分布式开发](https://baike.baidu.com/item/%E5%88%86%E5%B8%83%E5%BC%8F%E5%BC%80%E5%8F%91)，强调个体。

公共服务器压力和数据量都不会太大。

速度快、灵活。

任意两个开发者之间可以很容易的解决冲突。

离线工作。

### 2.Git的使用

#### 1)Git安装

Windows版的Git，从https://git-scm.com/download/win下载然后按默认选项安装即可。
安装完成后，右键打开菜单栏找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

安装完成后，还需要最后一步设置，在命令行输入：
​	git config --global user.name "Your Name" 
​	git config --global user.email "email@example.com" 
​	git config user.name 查看配置的姓名
​	git config user.email 查看配置的邮箱
​	因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。

#### 2)Linux命令

	mkdir xxx 新建文件夹
	vi x.txt 新建文件（Visual editor）
		输入 i 进入编辑模式
	ESC + ：+ wq 保存并退出
	cd xxx 进入xxx目录
	cd .. 返回上一级目录 或者 cd ../   cd../../ 上一层的上一层 
	ls  列出当前文件夹中所有文件
	ll  查看所在路径下的文件
		ll |less  查看当前文件中显示文件
	pwd 显示当前目录
	cat x.txt 显示文件内容
	clear 清屏

#### 3)创建版本库

1.初始化git仓库

```
Administrator@DESKTOP-PK38TIF MINGW64 ~/desktop (master)                 
$ cd test 进入到test目录
Administrator@DESKTOP-PK38TIF MINGW64 ~/desktop/test (master)
$ git init 初始化一个git仓库
Initialized empty Git repository in C:/Users/Administrator/Desktop/test/.git/ 初始化一个空的git仓库
```

![01初始化git](/01初始化git.png)

2.将工作区的文件提交到版本区

```
Administrator@DESKTOP-PK38TIF MINGW64 ~/desktop/test (master)                                   $ vi a.js   
Administrator@DESKTOP-PK38TIF MINGW64 ~/desktop/test (master)
$ cat a.js
console.log('hello git 1')
Administrator@DESKTOP-PK38TIF MINGW64 ~/desktop/test (master)
$ git add a.js  
warning: LF will be replaced by CRLF in a.js.
The file will have its original line endings in your working directory
Administrator@DESKTOP-PK38TIF MINGW64 ~/desktop/test (master)  
$ git commit -m "新建一个a.js文件" 
[master (root-commit) ecf4fa0] 新建一个a.js文件
 1 file changed, 1 insertion(+)
 create mode 100644 a.js
```

![01初始化git](/02将文件添加到版本区.png)

3.查看文件在哪个区

```
git status
```

![01初始化git](/03查看文件在哪个区.png)

4.提交到版本区后查看状态

```
git commit -m "新建b c d文件"
```

![01初始化git](/04提交版本区后查看状态.png)

5. 如果输入的命令是错误的,则会进入到不可描述的区域,两种方式退出

   1)直接关闭命令窗口,差掉

   2)esc+:q! 强制退出,不管文件是否损坏 



#### Git的三个分区

1.工作区:开发代码的地方,新建/修改/删除文件,这些在工作区

2.暂存区:暂时保存代码的地方

3.版本区:进行版本控制的地方

git指令:

cd test 切换到指定目录

vi a.js 创建a.js文件

键盘输入i 进入编辑模式,编写代码

按下键盘esc键,按下shift+分号键----->输入冒号,输入wq

esc+:wq + 回车----->保存当前文件并退出

git init 初始化仓库

git add a.js 把a.js文件提交到暂存区(git add * 或者git add . 或者git add -A 这三个命令都可以提交多个文件), 说明:-A 是all 的简写

git commit -m '注释内容' 将文件从暂存区提交到版本区进行版本控制

git status 查看文件的状态

 红色:说明文件位于工作区

绿色:说明文件位于暂存区

没有颜色/显示:说明文件位于版本区

注意:git开头的是git指令,其他的是linux指令



#### 4)版本还原

```
先修改a.js文件,然后查看状态,提交到暂存区,然后查看状态
再次修改a.js文件,然后查看状态
命令如下:
```

![01初始化git](/05修改文件提交到暂存区.png)

![01初始化git](/05修改文件提交到暂存区并再次修改文件查看状态.png)

​	工作区和暂存区文件的差异对比

```
git diff 差异对比  用的比较多
```



![01初始化git](/06工作区和暂存区的文件差异对比.png)

暂存区和版本区差异对比

```
git diff --cached
```

![01初始化git](/07暂存区和版本区对比.png)

```
git diff master 工作区和版本区对比
```

![01初始化git](/08工作区和版本区差异对比.png)

```
git commit -m "修改a.js文件"
git log 查看版本日志记录

```

![01初始化git](/09全部提交后查看版本信息.png)

上面的方式看起来比较多,有些麻烦

我们关心的日志信息和id,id是用来回退的

```
$ git reflog
95d263d (HEAD -> master) HEAD@{0}: commit: 修改a.js文件
5f06148 HEAD@{1}: commit: 新建b c d 文件 
ecf4fa0 HEAD@{2}: commit (initial): 新建一个a.js文件 
```

回退到某个版本------------>从版本区回退回来(版本区回退到工作区)

```
git reset --hard 95d263d 回到某个版本
git reset --hard HEAD^ 回到上一个版本
git reset --hard HEAD^^ 回到上上一个版本
git reset --hard HEAD^~100 回到前100个版本 很少用
其他的回退指令:

```

![01初始化git](/10回到对应版本.png)



![01初始化git](/git各个区.png)



```
git status 查看状态
vi a.js 添加一行新内容,esc:wq 保存并退出
git add . 添加到暂存区
vi a.js 再次添加一行新内容,esc:wq 保存并退出
git status 查看状态
然后把暂存区的文件回退到工作区中
git checkout -- a.js
cat a.js 查看a.js文件

```



![01初始化git](/11暂存区回退指定文件到工作区.png)



![01初始化git](/12删除暂存区中的文件并还原到工作区中.png)



上面两种方式的区别:git checkout  -- a.js 和git rm --cached a.js 的区别在于前者是把暂存区的文件回退到工作区中,暂存区中仍然有a.js这个文件,而后者是干掉了暂存区中的a.js文件,这个文件被还原到工作区中



![01初始化git](/13工作区被暂存区替换及版本区把工作区和暂存区全部替换.png)



```
删除工作区中的目录(当前目录为test目录)
mkdir index 创建目录
cd index 进入到index目录
vi 1.txt 创建文件,编辑文件,并保存后退出
cd .. 回到原来的test目录
git add * 添加到暂存区
git commit -m "添加index目录及内部的文件"
git rm -r index 
下面是删除文件的时候可能会有的问题
git rm a.js 如果删除不了,那么可以使用强制删除 git rm -f a.js
```

![01初始化git](/14删除工作区中的目录.png)





#### 5)分支操作----------很重要

```
mkdir mycode 创建mycode目录
cd mycode 切换到mycode目录
git init 初始化仓库
vi index.js 编辑index.js文件,保存并退出
git add . 工作区提交到暂存区
git commit -m "新建index.js" 暂存区提交到版本区
git checkout -b dev 创建并切换到dev分支
cat index.js 查看当前文件中的内容
vi index.js 编辑这个文件,保存并退出
git add . 提交到暂存区
git commit -m "修改了index.js文件" 提交到版本区
git checkout master 切换到master主分支
git merge dev 在master主分支中合并dev分支
cat index.js 查看index.js文件
git branch 查看当前有哪些分支
```





![01初始化git](/15分支切换及合并.png)

![01初始化git](/15分支切换及合并后查看.png)

![01初始化git](/16查看当前有哪些分支.png)



```
合并分支的冲突操作
git checkout -b a 切换a分支
vi index.js 编辑a分支中的文件并保存
git add . 提交到暂存区
git commit -m "修改a分支中的index.js文件" 提交到版本区中
git checkout master 切换到master 主分支中
git checkout -b b 切换b分支
vi index.js 编辑b分支中的文件并保存
git add . 提交到暂存区
git commit -m "修改b分支中的index.js文件" 提交到版本区中
git checkout master 切换到master 主分支中
git merge a  合并a分支
git merge b  合并b分支  出现冲突
cat index.js 查看冲突文件
vi index.js 编辑冲突文件
git add . 再次提交到暂存区
git commit -m "解决冲突" 再次提交到版本区中
cat index.js 再次查看修改冲突后的文件
```

![01初始化git](/17切换a分支修改index文件.png)

![01初始化git](/17切换b分支修改index文件.png)

![01初始化git](/17修改冲突文件并提交.png)



### 3.版本控制的区别

#### 1. 集中式版本控制系统

代表有SVN、CVS

       集中式版本控制系统，版本库是集中存放在中央服务器的，每个开发人员电脑里只有其中一个版本。

#### 2.分布式版本控制系统

代表有Git、BitKeeper

​	每个开发人员电脑里都有一个完整的版本库。同时，它也需要一台充当“中央服务器”的电脑，来方便“交换”大家的代码修改。

svn 20%,git 80%

| 类别    项目                             | 集中式版本控制系统                                           | 分布式版本控制系统                          |
| ---------------------------------------- | ------------------------------------------------------------ | ------------------------------------------- |
| 主要区别                                 | 每个开发者只有应用代码库的一个版本。                         | 每个开发者都有整个代码库的所有版本。        |
| 在离线状态下开发者无法进行版本管理开发。 | 在离线状态下开发者可以进行版本管理开发, 等到有网时再push到仓库中。 |                                             |
| 交互模型                                 | ![01初始化git](/集中式版本控制交互模型.png)                  | ![01初始化git](/分布式版本控制交互模型.png) |





### 4.GitHub

GitHub是一个面向[开源](https://baike.baidu.com/item/%E5%BC%80%E6%BA%90/20720669)及私有[软件](https://baike.baidu.com/item/%E8%BD%AF%E4%BB%B6/12053)项目的托管平台，因为只支持git 作为唯一的版本库格式进行托管，故名GitHub。

GitHub于2008年4月10日正式上线，除了Git代码仓库托管及基本的 Web管理界面以外，还提供了订阅、讨论组、文本渲染、在线文件编辑器、协作图谱（报表）、代码片段分享（Gist）等功能。目前，其注册用户已经超过350万，托管版本数量也是非常之多，其中不乏知名开源项目 [Ruby](https://baike.baidu.com/item/Ruby/11419) on Rails、[jQuery](https://baike.baidu.com/item/jQuery/5385065)、[python](https://baike.baidu.com/item/python/407313) 等。

2018年6月4日，微软宣布，通过75亿美元的股票交易收购代码托管平台GitHub。

```
本地仓库内容要推送到远程仓库
1)	新建本地仓库
	git init
	git add .
	git commit -m “first commit”
2)	新建远程仓库
	GitHub上New repository
3)	本地仓库和远程仓库进行关联
	git remote add origin https://github.com/xpromise/oa.git 	(HTTPS)
4)	把本地仓库内容推送到远程仓库中
	git push -u origin master （首次）
	由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送到远程新的master分支，还会把本地master分支和远程的master分支关联起来，在以后的推送或者拉取时可以简化命令git push origin master。

```

#### 本地仓库推送到远程仓库

```
mkdir testone 本地新建目录
cd testone 切换本地目录
git init 初始化本地仓库
vi index.js 编辑index.js文件并保存退出
git add . 提交到暂存区
git commit -m "新建index.js文件" 提交到版本区
git remote add origin 地址 关联远程仓库
  git remote remove origin 删除远程仓库的关联--此步骤可不写
git push -u origin master 将本地仓库推送到远程仓库  (-u 第一次需要,下一次不用)
vi index.js 再次修改本地文件
git add . 提交到暂存区
git commit -m "修改index.js文件" 提交到版本区
git push origin master 本地仓库推送到远程仓库
```



![01初始化git](/18github关联.png)

![01初始化git](/18github关联2.png)



![01初始化git](/18github关联3.png)



#### 远程仓库有东西,本地没有任何内容,要在本地看远程仓库的内容

```
git clone 地址 或者直接下载压缩包
先修改远程仓库(别人的仓库内容更新了,本地要更新远程仓库的内容)
git pull origin master 拉取远程仓库并合并到本地的master分支
```

![01初始化git](/19拉取远程仓库到本地.png)



![01初始化git](/19拉取远程仓库到本地2.png)



注意:无论是push还是pull操作,都要先进行本地版本控制

git add .

git commit -m "描述"

克隆下来的默认是master分支

```
git checkout -b dev 创建本地分支
git push origin dev 将本地dev分支推送到远程仓库中
```

![01初始化git](/20本地创建dev分支并推送到远程仓库.png)



如何克隆dev分支

```
git clone 地址
cd 目录    此时发现克隆的默认是master分支
git branch 查看的分支是master,没有dev
git fetch origin dev1:dev2 将远程仓库的dev1分支克隆到本地dev2分支中
git branch 此时查看就有了dev分支
git checkout dev 切换dev分支
ls 查看文件
cat index.js 查看文件内容 
```

![01初始化git](/21克隆dev分支.png)

![01初始化git](/21克隆dev分支2.png)











