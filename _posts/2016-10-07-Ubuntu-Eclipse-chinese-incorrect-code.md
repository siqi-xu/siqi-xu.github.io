---
title: "Ubuntu, Eclipse: chinese incorrect code"
layout: post
date: 2016-10-07
permalink : /post/Ubuntu-Eclipse-chinese-incorrect-code
tag:
- Ubuntu
- eclipse
- Java
blog: true
---   

以前一直在windows下开发，现在想把所有工程转移到Ubuntu下进行，所以把Windows下的工程都导入到Ubuntu下Eclipse中，由于以前的工程代码，都是GBK编码的（Windows下的Eclipse 默认会去读取系统的编码，所以Widnwos下的Eclipse的编码为GBK），而Ubuntu默认是不支持GBK编码的。所以，首先我们要先让 Ubuntu支持GBK，方法如下：
    
    
首先要修改/var/lib/locales/supported.d这个文件夹的权限，否则不能修改该文件夹下的local文件，使用如下命令 `sudo chmod -R 777 /var/lib/locales/supported.d`   
修改/var/lib/locales/supported.d/local文件: `gedit /var/lib/locales/supported.d/local`,在文件中添加     
```  
zh_CN.GBK GBK   

zh_CN.GB2312 GB2312    
```  

`sudo dpkg-reconfigure --force locales`,然后在输出的结果中会出现   

zh_CN.GB2312 done    

zh_CN.GBK done   
如下所示：    
![](img/2016-10-07-local.jpg)   

![](img/2016-10-07-minglinghang.png)   

这样， Ubuntu就支持GBK编码了， 下面开始设置eclipse，    

首先选择eclipse菜单栏中的Windows->Preferences, 然后选择General下面的Workspace， Text file encoding下选择Other GBK，如果没有GBK的选项， 没关系， 直接输入GBK三个字母， Apply， GBK编码的中文， 已经不是乱码了。   
![](img/2016-10-07-xiugaichenggong.png)

