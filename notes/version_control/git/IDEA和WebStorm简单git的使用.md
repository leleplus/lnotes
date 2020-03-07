## IDEA和WebStorm简单git的使用



--------------------------

作者:乐乐



### 一、Windows下的终端

Windows平台下由于自身的cmd终端非常的low。各种不兼容，所以出现了在Windows平台下第三方终端，支持自定义样式，支持Linux命令行（当然也支持vi编辑器），而且自带git和ssh等客户端，非常实用，推荐使用！

[cmder介绍地址，点击直达](https://segmentfault.com/a/1190000021029858)

<img src="C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219130909919.png" alt="image-20200219130909919" style="zoom:150%;" />



### 二、IDEA或WebStorm配置gitbash

上面刚刚介绍过cmder终端，里面自带git客户端，需要配置环境变量，IDEA和WebStorm同为JetBrains公司出产的软件，配置方式都一样

#### 1、IDEA配置

依次打开菜单栏-->`File`-->`settings`或者`Other Setting`-->`Settings for New Project`

![image-20200219131519717](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219131519717.png)

`Settings`里搜`git`-->左侧选择`git`，右边配置`gir.exe`的路径（一般配置了git的环境变量就可以直接找到），点击`Test`,能够出现`git`的版本号，配置成功

![image-20200219131934905](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219131934905.png)

#### 2、WebStorm配置

WebStorm一模一样的操作

![image-20200219132252657](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219132252657.png)



>   这里的Settings和Other Settings里的Setting for new Project的区别：
>
>   前者只对当前项目生效，后者对除了当前项目的其它项目生效，自己配置即可



### 三、JetBrains团队免费License获取

IDEA、WebStorm、PyCharm等都是优秀的IDE开发工具，但是收费昂贵，学生、老师、具有开源项目的团队都是可以免费申请的,提交学生证等相关的证件即可，通过可能需要一段时间

[面向学生的申请通道地址](https://www.jetbrains.com/zh-cn/student/)

![image-20200219132929553](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219132929553.png)

![image-20200219132941619](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219132941619.png)

### 四、IDEA或WebStorm配置Terminal终端

前面已经介绍过Cmder，安装到电脑上的cmder并不能在类似VSCode、IDEA、WebStorm、STS这一类工具里使用，它们的Terminal是一个单独的模块，默认调用的就是电脑本地的`cmd.exe`,所以更改方式有两种

1>干掉默认的`cmd.exe`,使用`cmder.exe`的`init.bat`批处理文件生成软连接，存放在`cmd.exe`原来的目录下，巧妙替换

>   缺点，电脑容易出问题，一更新全白费，当然只改一处就好

2>让每一款IDE集成开发工具的Terminal终端指向`cmder.exe`

>   缺点，每次重装软件都要改，每一款软件都要修改，优点，方便简单

采用方法二介绍

#### 1、同样打开`Settings`或者`Settings for new project`

#### 2、搜索`Terminal`,选择`Terminal`,修改`Shell path`的

![image-20200219134043342](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219134043342.png)

```bash
"cmd.exe" /k ""%CMDER_HOME%\vendor\init.bat""
# %CMDER_HOME%为我电脑cmder的家目录，看见bin即可，上面的这个路径要定位到init.bat的位置
```

![image-20200219134237562](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219134237562.png)

`Tab Name`可改可不改，无影响

这行代码的意思是，使用系统的`cmd.exe`,打开`init.bat`,通过`/k`传递打开路径，即`start directory`,打开目路idea或自动添加

#### 3、Terminal使用

不管是IDEA还是WebStorm，都可以在底部找到`Terminal`打开，快捷键`ALT+F12`(可能需要FN配合)

![image-20200219134844882](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219134844882.png)



这里面就可以使用一些Linux命令了

![image-20200219135045021](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219135045021.png)

### 五、git的简单使用

前面已经配置好了git,其实可以不用在外面的cmder里使用git的，idea、WebStorm里的Terminal就可以，还省去了进入本地git版本库的命令

#### 1、开发流程

一般工作，接到任务的流程如下:

1>查看任务单

2>拉取最新代码

3>新建任务分支

4>编写代码

5>提交代码

6>将任务分支推送到远程代码仓库

7.给TL(项目主管)提交代码分支合并请求，即`Merge Request`

8.任务结束

>   有的可能不存在第七点，还需要如下操作(接上6)
>
>   7.将任务分支合并到主分支
>
>   8.将最新的主分支代码推送到远程，并删除任务分支
>
>   9.任务结束

#### 2、相关git操作

>   以下操作都建议在IDEA或者WebStorm的Terminal终端完成
>
>   前面的`$`是命令提示符

1> 切换到基于开发的分支

```bash
$ git checkout 分支名  # 需要从哪个分支的代码开始做，就切换到哪个分支
```

![image-20200219140650422](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219140650422.png)



2>确保工作空间干净

```bash
$ git status  # 查看当前工作空间的状态
```

![image-20200219140732017](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219140732017.png)

显示`nothing to commit, working tree clean`就是干净的，没有任何的修改，没有任何提交，跟远程一模一样，如果有修改的文件，建议回退(`git checkout <filename>.`)或者封存(`git stash`),或者直接推到远程，注意确认好



>   ```bash
>   $ git status
>   ```
>
>   查看工作区的状态，这个是最常用的命令，如果你忘了要干嘛，或者不知道做到了哪一步，执行这个命令，它会告诉你



3>拉取最新的代码

```bash
$ git pull  # 拉取最新的仓库代码到本地
```

如果停留在某个操作太久了，比如去上厕所，或者午饭，有同事在这个空隙提交了代码，你的本地版本库代码就不是最新了，使用`$ git status`它会提示你拉取最新代码(网络差的时候，也会提示不到)，但是我们可以有个好习惯，过一段时间就执行一次，避免提交代码时，跟同事发生冲突

![image-20200219141514486](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219141514486.png)

4>新建开发分支

此时可以新建一个分支，专属于你，有两种方法

第一种，简单便捷

```bash
$ git checkout -b 分支名  # 创建并切换分支
```

`-b`参数是`branch`分支的意思

第二种，逻辑清晰

```bash
$ git branch 分支名     # 新建分支
$ git checkout 分支名   # 切换到分支
```

我一般使用第一种

![image-20200219142120039](C:\Users\logic\AppData\Roaming\Typora\typora-user-images\image-20200219142120039.png)

5> 此时就可以愉快的修改代码了

6>提交代码

代码修改完毕后，由于修改时间比较长，可能你的团队，已经有很多人提交了代码，此时一定要检查代码状态

```bash
$ git status   # 查看当前工作空间的状态
```

![image-20200220105110164](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220105110164.png)

仔细检查需要提交的文件，可以与工作空间的

```bash
$ git diff <file>  # 查看某个文件修改的内容
```

![image-20200220105351840](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220105351840.png)

如果这个文件不需要提交，可以回滚

```bash
$ git checkout <file>  # 还原文件版本成未修改状态
```

![image-20200220105528264](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220105528264.png)

7> 提交已修改的代码

确认你的代码没有问题，并且都是需要提交的文件，就可以提交了

```bash
$ git add .  # 提交所有文件
$ git add <file> # 提交单个文件
```

![image-20200220105729289](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220105729289.png)

提交已经添加到暂存区的文件

```bash
$ git commit -m "注释"
```

![image-20200220110008854](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220110008854.png)

>   注意:可以`git add`很多次，最后`git commit`一次提交所有

此时如果不小心写错了提交注释导致已经提交，恰好本次提交是最后一次，可以使用命令

```bash
$ git commit --amend -m "新的注释" # 仅限最后一次提交注释出错
```

如果是其中某次注释写错，可以使用`git rebase`的操作，属于git 高级应用，比较复杂

8>将分支推送到远程

如果你的代码全部写完，任务全部完成，都已经`commit`了，就可以推送到远程了

>   多次`git commit`可以使用一次命令推送到远程

一般的做法是，直接将该分支推送到远程，先查看状态

```bash
$ git status # 查看工作区状态
```

![image-20200220110536777](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220110536777.png)

虽然说你的工作空间很干净，但是，一定要注意，提交之前拉取最新代码的更改

```bash
$ git pull  # 拉取最新的远程代码到本地
```

![image-20200220110743607](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220110743607.png)

查看当前所在的分支

直接查看

![image-20200220110817542](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220110817542.png)

使用命令

```bash
$ git branch # 查看所在的分支
```

![image-20200220110858747](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220110858747.png)

把当前的新分支代码推送到远程

```bash
$ git push # 推送代码到远程
```

此时直接输入该代码会报错，因为，远程并不存在此分支，但是报错后会给出提示

![image-20200220111116252](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220111116252.png)

因为命令长，记不住，可以等报错之后，复制命令执行

第一次推送，正确的命令

```bash
$ git push --set-upstream origin bugfix/XSYY-365
```

![image-20200220111420691](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220111420691.png)



使用该命令推送到远程后，下次推送，直接就可以使用`git push`了

#### 3、合并分支

各个团队工作方式不一样，大部分团队只有项目TL才能修改项目主线分支，列举两种情况

1> 创建Merge Request

进入gitLab页面，选择Merge Request

![image-20200220111633966](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220111633966.png)

![image-20200220111722846](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220111722846.png)

选择对应的项目，创建

![image-20200220112001577](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220112001577.png)

![image-20200220112252994](D:\Documents\note\IDEA和WebStorm简单git的使用.assets\image-20200220112252994.png)

任务完成

2>合并分支到主线

前面已经将分支推送到了远程，但是和主线是截然不同的，下面简单介绍合并流程

1)先切换到主线分支，即你要往哪个分支上合并，就切换到哪个分支

```bash
$ git checkout <要合并到的分支名>
```

2)拉取分支最新代码

```bash
$ git pull
```

3)合并分支

```bash
$ git merge <需要合并的分支>
```

4)提交合并的commit

合并之后，原来分支所有的commit信息就到了主分支上,但是只有本地存在，必须要推送到远程才算完成

```bash
$ git push
```

5)删除无用的分支

既然修改之后的分支已经被合并了，完全可以删除

```bash
$ git branch -d <分支名>
```

上面删除分支的代码，如果该分支没有被合并，会报错的

```bash
$ git branch -D <分支名>
```

强行删除分支

此时任务结束