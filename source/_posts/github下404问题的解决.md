title: github下404问题的解决
date: 2015-01-15 17:12:03
tags:
---
```

非常喜欢jekyll的简洁,特别是github下可以自动生成网页,

但有的时候在本地是ok的,push到github无论如何总是显示404,检查各种设置也是正常的. 看 这里

解决的方法很简单,打开项目的setting,点击 Automatic page generator,先使用自带的功能创建页面,然后打开 username.github.io,确认可以访问了以后,clone 项目后,删除已有文件,替换你自己的jekyll就可以了. 这里应该是github的一个bug了.

```