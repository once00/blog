---
layout: post
title: 简单制作 OS X Yosemite 10.10 正式版U盘USB启动安装盘方法教程
tags: [blog]
---



#本文讲解的是用命令行制作
	一.准备工作
1.准备一个 8GB 或以上容量的 U 盘，确保里面的数据已经妥善备份好（该过程会抹掉 U 盘全部数据）

2.从这里下载苹果官方 OS X Yosemite 正式版的安装程序

3.如果你是从 Mac AppStore 下载的，下载完成后安装程序可能自动开始，这时先退出安装


4.把下载完的系统移动到「应用程序」文件夹里面

<!-- more -->
	二.格式化U盘
插入你的 U 盘，然后在「应用程序」->「实用工具」里面找到并打开「磁盘工具」如下图。

<!-- more -->
![我的图片](https://raw.githubusercontent.com/once00/once00.github.io/master/img/format-usb.jpg)

1. 1 - 在左方列表中找到 U 盘的名称并点击

2. 右边顶部选择 2 -「分区」，然后在 3 -「分区布局」选择「1个分区」

3. 在分区信息中的 4 -「名称」输入「iPlaySoft」 (名字随便起,因为在后面的命令行用到)

4. 在「格式」中选择 5 -「Mac OS 扩展 (日志式)」.

5. 在 6 -「选项」里面，如下图

![我的图片](https://raw.githubusercontent.com/once00/once00.github.io/master/img/guid.jpg)

6.选择「GUID 分区表」，然后点击「好」

7.最后再点「应用」开始对 U 盘进行格式化。
 
	三、输入终端命令开始制作启动盘
1. 请再次确保名为 “安装 OS X Yosemite” 的文件是保存在「应用程序」的目录中

2. 在「应用程序」->「实用工具」里面找到「终端」并打开。

3. 复制下面的命令，并粘贴到「终端」里，按回车运行：

```
sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume /Volumes/iPlaySoft --applicationpath /Applications/Install\ OS\ X\ Yosemite.app --nointeraction
```
回车后，系统会提示你输入管理员密码，接下来就是等待系统开始制作启动盘了,会如下提示就说明已经完成了

```
Erasing Disk: 0%... 10%... 20%... 30%...100%...
Copying installer files to disk...
Copy complete.
Making disk bootable...
Copying boot files...
Copy complete.
Done.
```

	四.U 盘启动安装系统

开机一直按住「option」(alt) 按键不放,后面步骤不详细介绍

