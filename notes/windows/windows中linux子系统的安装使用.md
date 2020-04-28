# Windows中Linux子系统的使用

作者: 乐乐

> 本教程适用于最新版Windows10，阅读前请先在设置-->更新，更新到最新版Windows操作系统


# 一、开启Windows对Linux子系统支持

1.打开运行
使用快捷键`Windows`+`R`键打开，或者鼠标右键点击开始菜单，选择`运行`
![image-20200425194002943](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200425194002943.png)

输入`control`，然后确定，打开控制面板
![image-20200425194205295](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200425194205295.png)

2.在控制面板的`类别`分类下点击`程序`
![image-20200425194314360](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200425194314360.png)

继续点击`启用或关闭Windows功能`
![image-20200425194411211](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200425194411211.png)


3.启用如图所示功能并确定
![image-20200425195100536](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200425195100536.png)

![image-20200425195128265](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200425195128265.png)

4.更改完成后，重启系统

# 二、安装Linux子系统

1.打开Microsoft Store商店
![image-20200426212951482](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200426212951482.png)

2.在商店中搜索`Ubuntu`或者`Linux`，会看到可用的Linux系统
![image-20200426213530274](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200426213530274.png)


3.选择好系统后，点击`获取`,哪个版本都可以，我选择最新版

> Windows 商店连接很慢的，微软服务器慢，需要多尝试几次

![image-20200426213951099](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200426213951099.png)

4.等待下载完成
![image-20200427124437152](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200427124437152.png)

5.下载安装完成后，打开开始菜单，就能看到安装好的Linux系统

![image-20200428205624864](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428205624864.png)

6.点击图标，打开Ubuntu Linux
![image-20200428205928868](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428205928868.png)

7.敲击回车键，开始配置

![image-20200428210026577](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428210026577.png)

8.默认用户名为`root`,已经存在，新建一个普通用户，输入用户名点击回车
![image-20200428210157912](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428210157912.png)

9.输入密码，点击回车，再次确认输入后，点击回车，用户创建完成
![image-20200428210348627](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428210348627.png)

10.安装完成后，Linux子系统就可以使用了，并且集成了git等常用工具
![image-20200428210522772](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428210522772.png)

# 三、使用Linux子系统
访问Linux子系统的方式很多，比如：桌面点击Ubuntu图标，使用`ssh`服务，通过命令行访问。下面介绍

由于日常使用Linux都是命令，这里推荐使用`cmder`代替Windows下的`cmd`，[点击了解](https://segmentfault.com/a/1190000021029858)

1.通过桌面访问，直接点击Ubuntu图标即可

2.通过终端访问
打开cmd，直接输入命令`bash`,挂在到`/mnt/`下的当前磁盘，想回到家目录，再次敲击`cd`
![image-20200428211729270](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428211729270.png)

3.访问Windows磁盘下的文件，直接到`/mnt/`下即可，例如`C`盘`cd /mnt/c/`,`D`盘`cd /mnt/d`
![image-20200428212446710](windows%E4%B8%ADlinux%E5%AD%90%E7%B3%BB%E7%BB%9F%E7%9A%84%E5%AE%89%E8%A3%85%E4%BD%BF%E7%94%A8.assets/image-20200428212446710.png)

其余就是Linux基本操作。
