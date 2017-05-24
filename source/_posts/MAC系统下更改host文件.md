title: MAC系统下更改host文件
---

##1.终端更改

* 1.在应用程序里面打开终端(terminal)

* 2.输入sudo vi /etc/hosts

* 3.提示输入系统密码(输入密码是默认隐藏的，直接输入回车)hosts文件	就自动打开了(有时候打不开,在敲次回车)
	
* 4.打开此网站生成host文件:
	
	<http://serve.netsh.org/pub/gethosts.php>


* 5.接着输入 i 进入编辑模式将添加的网站,ip拷贝进去

* 6.编辑完成之后,按esc,输入 : wq

##2.直接修改本地文件

* 1.打开finder ,在前往里面选择前往文件夹(快捷键shift+comman+g) 	在弹出框里输入 /private/etc
<!-- more -->
* 2.到了etc目录下,找到hosts文件
	
* 4.打开此网站生成host文件:
	
	<http://serve.netsh.org/pub/gethosts.php>
	
* 4.打开(用文本编辑),拷贝或编辑,完成后保存即可.(一般会提示输入管理	员密码,输入完成保存即可)