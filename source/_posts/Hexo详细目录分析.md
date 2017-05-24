title: Hexo详细目录分析
date: 2015-01-16 17:18:59
tags:
---
##目录和文件
默认生成的一些文件
![我的图片](https://raw.githubusercontent.com/once00/once00.github.io/master/img/hexo-folder.png)
<!-- more -->
* scaffolds 脚手架，也就是一个工具模板
* scripts 写文件的js，扩展hexo的功能
* source 存放博客正文内容
* source/_drafts 草稿箱
* source/_posts 文件箱
* themes 存放皮肤的目录
* themes/landscape 默认的皮肤
* _config.yml 全局的配置文件
* db.json 静态常量

##全局配置

**站点配置用到两个文件，一个是对整站的配置H:\hexo\_config.yml，另一个是对主题的配置H:\hexo\themes\light_config.yml**

###H:\hexo\_config.yml下文件
* 这是全局配置文件,网站很多东西都需要在这里配置
* 站点信息: 定义标题，作者，语言
* URL: URL访问路径
* 文件目录: 正文的存储目录
* 写博客配置：文章标题，文章类型，外部链接等
* 目录和标签：默认分类，分类图，标签图
* 归档设置：归档的类型
* 服务器设置：IP，访问端口，日志输出
* 时间和日期格式： 时间显示格式，日期显示格式
* 分页设置：每页显示数量
* 评论：外挂的Disqus评论系统
* 插件和皮肤：换皮肤，安装插件
* Markdown语言：markdown的标准
* CSS的stylus格式：是否允许压缩
* 部署配置：github发布

```
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/tommy351/hexo/

# 整站的基本信息
title: #网站标题
subtitle: #网站副标题
description: blog.fens.me #对站点的描述
author: bsspirit #在站点左下角可以看到
email: bsspirit@gmail.com #邮箱
language: zh-CN #语言

# URL #这项暂不配置，绑定域名后，欲创建sitemap.xml需要配置该项
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://blog.fens.me
root: /
permalink: :year/:month/:day/:title/
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code

# 文件目录
source_dir: source
public_dir: public

# 写博客配置(文章布局.写作格式的定义)
new_post_name: :title.md # File name of new posts
default_layout: post
auto_spacing: false # Add spaces between asian characters and western characters
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
max_open_file: 100
multi_thread: true
filename_case: 0
render_drafts: false
post_asset_folder: false
highlight:
  enable: true
  line_number: true
  tab_replace:

# 目录和标签
default_category: uncategorized
category_map:
tag_map:

# 归档设置
## 2: Enable pagination
## 1: Disable pagination
## 0: Fully Disable
#默认值为2，这里都修改为1，相应页面就只会列出标题，而非全文
archive: 2
category: 2
tag: 2

# 服务器设置
## Hexo uses Connect as a server
## You can customize the logger format as defined in
## http://www.senchalabs.org/connect/logger.html
port: 4000
server_ip: 0.0.0.0
logger: false
logger_format:

# 时间和日期格式
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: MMM D YYYY
time_format: H:mm:ss

# 分页设置(每页显示文章数,可以自定义)
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# 评论
disqus_shortname:

# 插件和皮肤
## Plugins: https://github.com/tommy351/hexo/wiki/Plugins
## Themes: https://github.com/tommy351/hexo/wiki/Themes
theme: landscape
exclude_generator:

# Markdown语法
## https://github.com/chjj/marked
markdown:
  gfm: true
  pedantic: false
  sanitize: false
  tables: true
  breaks: true
  smartLists: true
  smartypants: true

# CSS的stylus格式
stylus:
  compress: false

# 部署配置
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type:
  repository: #自己博客地址
  branch: master
  
```

###H:\hexo\themes\light_config.yml目录下
####页面展示的全部逻辑都在每个主题控制

```
.
├── languages  #多语言
|   ├── default.yml#默认语言
|   └── zh-CN.yml  #中文语言
├── layout #布局，根目录下的*.ejs文件是对主页，分页，存档等的控制
|   ├── _partial   #局部的布局，此目录下的*.ejs是对头尾等局部的控制
|   └── _widget#小挂件的布局，页面下方小挂件的控制
├── source #源码
|   ├── css#css源码 
|   |   ├── _base  #*.styl基础css
|   |   ├── _partial   #*.styl局部css
|   |   ├── fonts  #字体
|   |   ├── images #图片
|   |   └── style.styl #*.styl引入需要的css源码
|   ├── fancybox   #fancybox效果源码
|   └── js #javascript源代码
├── _config.yml#主题配置文件
└── README.md  #用GitHub的都知道
```
####light_config.yml文件

```
# Header
menu:
  主页: /
  所有文章: /archives
  随笔: /tags

# SubNav
subnav:
  github: "https://github.com/once00"
  weibo: "http://weibo.com/5253699523/profile?topnav=1&wvr=6"
  rss: "#"
  facebook: "#"
  # google: "#"
  # twitter: "#"
  # linkedin: "#"

rss: /atom.xml

# Content
excerpt_link: more
fancybox: true

# Miscellaneous
google_analytics: ''
favicon: /favicon.png

#你的头像
avatar: "https://raw.githubusercontent.com/once00/once00.github.io/master/img/8552641.jpeg"
#是否开启分享
share: true
#是否开启多说评论，填写你在多说申请的项目名称
#若使用disqus，请在博客config文件中填写disqus_shortname，并关闭多说评论
duoshuo: true
#是否开启云标签
tagcloud: true

#是否开启友情链接
#不开启——
#friends: false
#开启——
friends:
  卡卡的美丽传说: http://localhost:4000/
  本泽马的博客: http://localhost:4000/
  吉格斯的博客: http://localhost:4000/
  习大大大不同: http://localhost:4000/
  托蒂的博客: http://localhost:4000/

#是否开启“关于我”。
#不开启——
#aboutme: false
#开启——
aboutme: 我是谁，我从哪里来，我到哪里去？我就是我，是颜色不一样的吃货…

```

##查看命令行帮助

```
$ hexo help
```

```
Usage: hexo 

Commands:
  help      Get help on a command
  init      Create a new Hexo folder
  migrate   Migrate your site from other system to Hexo
  version   Display version information

Global Options:
  --config   Specify config file instead of using _config.yml
  --debug    Display all verbose messages in the terminal
  --safe     Disable all plugins and scripts
  --silent   Hide output on console

For more help, you can use `hexo help [command]` for the detailed information
or you can check the docs: http://hexo.io/docs/

```
**命令行解释：**

* help 查看帮助信息
* init 创建一个hexo项目
* migrate 从其他系统向hexo迁移
* version 查看hexo的版本
* –config参数，指定配置文件，代替默认的_config.yml
* –debug参数，调试模式，输出所有日志信息
* –safe参数，安全模式，禁用所有的插件和脚本
* –silent参数，无日志输出模式
