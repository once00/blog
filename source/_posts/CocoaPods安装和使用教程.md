title: CocoaPods安装和使用教程
date: 2015-01-21 12:07:19
tags:
---
##如何下载和安装CocoaPods？
我们可以用淘宝的Ruby镜像来访问cocoapods。按照下面的顺序在终端中敲入依次敲入命令：

```
 $ gem sources --remove https://rubygems.org/
```
等有反应之后再敲入以下命令

```
$ gem sources -a http://ruby.taobao.org/
```
为了验证你的Ruby镜像是并且仅是taobao，可以用以下命令查看：

```
$ gem sources -l
```
只有在终端中出现下面文字才表明你上面的命令是成功的：
<!-- more -->
```
*** CURRENT SOURCES ***
<!-- more -->
http://ruby.taobao.org/
```
再次在终端中运行：

```
$ sudo gem install cocoapods
```
系统会提示输入管理员密码(如果没密码,请设置一个密码)

等待输入完成时候如果是如下提示,则是成功的表现

```
Installing ri documentation for cocoapods-trunk-0.4.1
Parsing documentation for molinillo-0.1.2
Installing ri documentation for molinillo-0.1.2
Parsing documentation for escape-0.0.4
Installing ri documentation for escape-0.0.4
Parsing documentation for open4-1.3.4
Installing ri documentation for open4-1.3.4
Parsing documentation for cocoapods-0.35.0
Installing ri documentation for cocoapods-0.35.0
20 gems installed

```

##如果安装第三方类库
###如在项目中导入AFNetworking类库:
为了确定AFNetworking是否支持CocoaPods，可以用CocoaPods的搜索功能验证一下。在终端中输入：

```
$ pod search AFNetworking
```
等待几秒就能看到如下提示

```
-> AFNetworking (2.5.0)
   A delightful iOS and OS X networking framework.
   pod 'AFNetworking', '~> 2.5.0'
   - Homepage: https://github.com/AFNetworking/AFNetworking
   - Source:   https://github.com/AFNetworking/AFNetworking.git
   - Versions: 2.5.0, 2.4.1, 2.4.0, 2.3.1, 2.3.0, 2.2.4, 2.2.3, 2.2.2, 2.2.1,
   2.2.0, 2.1.0, 2.0.3, 2.0.2, 2.0.1, 2.0.0, 2.0.0-RC3, 2.0.0-RC2, 2.0.0-RC1,
   1.3.4, 1.3.3, 1.3.2, 1.3.1, 1.3.0, 1.2.1, 1.2.0, 1.1.0, 1.0.1, 1.0, 1.0RC3,
   1.0RC2, 1.0RC1, 0.10.1, 0.10.0, 0.9.2, 0.9.1, 0.9.0, 0.7.0, 0.5.1 [master
   repo]
   - Sub specs:
     - AFNetworking/Serialization (2.5.0)
     - AFNetworking/Security (2.5.0)
     - AFNetworking/Reachability (2.5.0)
     - AFNetworking/NSURLConnection (2.5.0)
     - AFNetworking/NSURLSession (2.5.0)
     - AFNetworking/UIKit (2.5.0)
```

**此时新建一个项目,在终端中输入命令进入你的项目目录输入:

```
pod init
```
此时你的项目目录里面多了`Podfile`文件,用文本编辑模式打开,输入刚验证的版本号:`pod 'AFNetworking', '~> 2.5.0'`

这时候，你就可以利用CocoPods下载AFNetworking类库了。还是在终端中的当前项目目录下，运行以下命令：

```
$ pod install 
```
因为是在你的项目中导入AFNetworking，这就是为什么这个命令需要你进入你的项目所在目录中运行。

运行上述命令之后，小编的终端出现以下信息:

```
Analyzing dependencies

CocoaPods 0.36.0.beta.1 is available.
To update use: `gem install cocoapods --pre`
[!] This is a test version we'd love you to try.

For more information see http://blog.cocoapods.org
and the CHANGELOG for this version http://git.io/BaH8pQ.

Downloading dependencies
Installing AFNetworking (2.5.0)
Generating Pods project
Integrating client project

[!] From now on use `CocoaPods.xcworkspace`.
```

**注意最后一句话，意思是：以后打开项目就用 CocoaPodsDemo.xcworkspace 打开，而不是之前的.xcodeproj文件。
