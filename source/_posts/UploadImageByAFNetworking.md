title: UploadImageByAFNetworking
date: 2015-01-20 17:08:16
tags:
---

准备工作：界面放置UIImageView，设置默认的图片属性，生成相应的输出口，声明图像选取器(UIImagePickerController)属性，然后在viewDidLoad方法中添加如下代码：

1. 给图像视图添加轻拍手势


<!-- more -->


```

```









    UIImage * image=info[UIImagePickerControllerOriginalImage];
    // 设置界面imageView的image属性为选中的图片
    self.imageView.image=image;
    // 关闭图片库
    [self dismissViewControllerAnimated:YES completion:nil];







1.把图片对象转换成data对象(UIImagePNGRepresentation方法）

```
```


[imageData writeToFile:filePath atomically:YES];
```

// 创建http请求操作管理器（AFHTTPRequestOperationManager类的对象）

AFHTTPRequestOperationManager * manage=[AFHTTPRequestOperationManager new];
```





```




```

```
