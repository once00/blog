title: hexo搭建
date: 2015-01-16 14:13:16
tags:
---

##一.安装Hexo

打开终端

```
$ npm install -g hexo
```
##二.部署Hexo

在电脑任意位置新建文件夹利用终端进入此文件夹.执行此命令(Hexo随后会自动在目标文件夹建立网站所需要的所有文件).


```
$ hexo init
```
必须执行此命令才可被保存

```
$ hexo generate
```
<!-- more -->
可把**hexo generate**简写为**hexo g**
	
启动Hexo服务器

```
$ hexo server
```
可把**hexo server**简写为**hexo s**

这时端口4000被打开了，我们能过浏览器打开地址，<http://localhost:4000/>.

##克隆主题

```
$ git clone https://github.com/cnfeat/cnfeat.git themes/jacman
```
###启用主题
修改Hexo目录下的config.yml配置文件中的theme属性，将其设置为jacman

注:最后一组改的属性

**deploy:**

**type: github**
  
**repository: git@github.com:once00/once00.github.io.git**
  
**branch: master**

##推送

执行此命令进行保存推送到自己的github库

```
$ hexo g
```

```
$ hexo d
```

##Hexo命令

###常用命令：

```
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #将.deploy目录部署到GitHub
```
###常用复合命令：

```
hexo d -g #生成加部署
hexo s -g #预览加部署
```
###简写：

```
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```
**官方hexo**
<https://github.com/hexojs/hexo/wiki/Themes>