title: "Xcode6 使用MJRefresh，Too many arguments to function call, expected 0, have *"
date: 2015-01-20 16:50:06
tags:
---

将Xcode升级到6后，报Too many arguments to function call, expected 0, have *，在Xcode5.1里能编译通过的，到Xcode6就报错

```
objc_msgSend(self.beginRefreshingTaget, self.beginRefreshingAction, self);Too many arguments to function call, expected 0, have *
```选中项目 **- Project - Build Settings - ENABLE_STRICT_OBJC_MSGSEND** 将其设置为 **NO** 即可
<!-- more -->如果编译还是出现错误,修改**MJRefreshConst.m**,在文件头部添加一下代码即可: `#import <CoreGraphics/CoreGraphics.h>`