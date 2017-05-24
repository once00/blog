title: UploadImageByAFNetworking
date: 2015-01-20 17:08:16
tags:
---

准备工作：界面放置UIImageView，设置默认的图片属性，生成相应的输出口，声明图像选取器(UIImagePickerController)属性，然后在viewDidLoad方法中添加如下代码：

1. 给图像视图添加轻拍手势2. 设置手势属性：一个手指单击一次3. 给界面图像视图绑定手势4. 设置界面图像视图能够与用户交互5. 初始化图像选取控制器6. 设置图像选取器的委托    **参考代码：**
1.给图像视图添加轻拍手势
```UITapGestureRecognizer *tap = [[UITapGestureRecognizer alloc]initWithTarget:self action:@selector(tapImage:)];```2.设置手势属性：一个手指单击一次
<!-- more -->
```tap.numberOfTapsRequired = 1;tap.numberOfTouchesRequired = 1;```3.给界面图像视图绑定手势
```[self.imageView addGestureRecognizer:tap];
```4.设置界面图像视图能够与用户交互

```self.imageView.userInteractionEnabled = YES;```5.初始化图像选取控制器
```self.imagePicker = [UIImagePickerController new];```6.设置图像选取器的委托
```self.imagePicker.delegate = self;```**完成以下方法：**
```#pragma mark 单击界面图像视图调用的方法- (void)tapImage:(UIGestureRecognizer *)recognizer {    // 打开图片库选取图片    }
```
```#pragma mark 图像选取控制器委托方法- (void)imagePickerController:(UIImagePickerController *)picker didFinishPickingMediaWithInfo:(NSDictionary *)info {	// 从info字典参数中获取选中的图片（通过UIImagePickerControllerOriginalImage键获取）    // 设置界面imageView的image属性为选中的图片    // 关闭图片库}
```**参考代码：**
```#pragma mark 单击界面图像视图调用的方法- (void)tapImage:(UIGestureRecognizer *)recognizer {    // 打开图片库选取图片    [self presentViewController:self.imagePickerController animated:YES completion:nil];}
```
```#pragma mark 图像选取控制器委托方法- (void)imagePickerController:(UIImagePickerController *)picker didFinishPickingMediaWithInfo:(NSDictionary *)info {    // 从info字典参数中获取选中的图片（通过UIImagePickerControllerOriginalImage键获取）
    UIImage * image=info[UIImagePickerControllerOriginalImage];
    // 设置界面imageView的image属性为选中的图片
    self.imageView.image=image;
    // 关闭图片库
    [self dismissViewControllerAnimated:YES completion:nil];
    }
```**完成上传图片，使用AFNetworking**
```- (IBAction)uploadImage:(id)sender {
    // 把图片对象转换成data对象（UIImagePNGRepresentation方法）        // 保存图片到沙盒中（获取文件完整目录，使用data对象的writeToFile:atomically:	方法写入）    // 使用AFNetworking上传图片    // 创建http请求操作管理器（AFHTTPRequestOperationManager类的对象）        // 设置接收响应类型    //manager.responseSerializer.acceptableContentTypes = 	[NSSetsetWithObjects:@"text/html", nil];    // 使用AFHTTPRequestOperationManager类的对象POST:parameters: 	constructingBodyWithBlock: success: failure:方法创建http请求操作对象	(AFHTTPRequestOperation)        constructingBodyWithBlock代码块参数中执行以下代码：        // 文件路径方式上传图片		// 通过沙盒中文件完整路径创建NSURL对象（NSURL 的类方法fileURLWithPath:）        // 调用代码块的formData参数的appendPartWithFileURL: name:error:方法		上传图片（注意此处name参数是服务端上传图片时接口中的参数名称）                // data方式上传图片        /*[formData appendPartWithFileData:imageData name:@"fileName" 		fileName:@"upload.png" mimeType:@"image/png"];*/    	//最后http请求操作对象发送请求    ```**参考代码：**
**//上传图片，使用AFNetworking**
**- (IBAction)uploadImage:(id)sender {**

1.把图片对象转换成data对象(UIImagePNGRepresentation方法）

```NSData *imageData = UIImagePNGRepresentation(self.imageView.image);
```
2.保存图片到沙盒中
```NSString *filePath = [self getFilePath:@"upload.png"];
[imageData writeToFile:filePath atomically:YES];
```3.使用AFNetworking上传图片
```
// 创建http请求操作管理器（AFHTTPRequestOperationManager类的对象）

AFHTTPRequestOperationManager * manage=[AFHTTPRequestOperationManager new];
```4.创建http请求操作管理器(AFHTTPRequestOperationManager类的对象）
```AFHTTPRequestOperationManager *manager = [AFHTTPRequestOperationManager new];
```5.设置接收响应类型
```manager.responseSerializer.acceptableContentTypes = [NSSet setWithObjects:@"text/html", nil];
```6.创建http请求操作对象
```AFHTTPRequestOperation *op = [manager POST:kUploadFileURL parameters:nil constructingBodyWithBlock:^(id<AFMultipartFormData> formData) {**菊花**[MMProgressHUD setPresentationStyle:MMProgressHUDPresentationStyleFade];[MMProgressHUD showWithTitle:@"上传图片" status:@"上传中。。。"];
```
7.文件路径方式上传图片
```NSURL *url = [NSURL fileURLWithPath:filePath];[formData appendPartWithFileURL:url name:@"fileName" error:nil];
```8.data方式上传图片
```[formData appendPartWithFileData:imageData name:@"fileName" fileName:@"upload.png" mimeType:@"image/png"];*/    } success:^(AFHTTPRequestOperation *operation, id responseObject) {        [MMProgressHUD dismissWithSuccess:@"上传成功！"];        NSLog(@"responseObject:%@",responseObject);    } failure:^(AFHTTPRequestOperation *operation, NSError *error) {        [MMProgressHUD dismissWithError:@"上传失败！"];        NSLog(@"error:%@",[error localizedDescription]);    }];
```8.http请求操作对象发送请求
```[op start];
```}
```