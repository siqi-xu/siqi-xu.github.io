---
title: "Adding an existing project to GitHub using the Git Plugin"
layout: post
date: 2016-10-09
permalink : /post/Adding-an-existing-project-to-GitHub-using-the-Git-Plugin
tag:
- Eclipse
- Github
- Git
blog: true
---     

## eclipse下使用git插件上传代码至github   

弄了两天，想尝试在同一个repository中push多个不同的Java project，多番尝试都无法成功，尽管我相信是可以做到的！在查找解决方法的时候有了解到有Submodule，Subtree这些概念，浏览了大概意思后没有去实现，因为感觉自己目前还没有需求，以后有机会去实践之后再总结一下。
经过请教hareric，还是决定new不同的repository，下面总结我自己的步骤。  

### 安装Git插件  

我使用的eclipse是自带git插件的，所以直接省掉了安装这一步骤，安装的相关资料请自己去查找一下，我这里就不再讲述。     

### 在github上创建仓库    

在Github主页面右上角“+”下拉列表中点击New repository，创建一个新的库。    

![](img/2016-10-09-new.png)  

点击新建好库，选中HTTP，复制后面的地址，后面将会用到。  

### eclipse创建本地git仓库  

在eclipse中选择一个项目，右键->Team->Share Project, 选择 Git，接下来输入本地仓库名称，本地仓库即可创建成功。  

![](img/2016-10-09-share.png)    

![](img/2016-10-09-git.png)    

![](img/2016-10-09-use.png)   

### commit代码到本地git仓库    

![](img/2016-10-09-commit.png)   

![](img/2016-10-09-commitMessage.png)  

### push代码到github远程仓库   

选中需要 Push 的项目，右键->Team->Remote->Push      

![](img/2016-10-09-push.png)    

URL 填写上面获取到的 HTTP 地址，User 和 Password 填写你的github帐号和密码，完成后点击next进入下一步   

![](img/2016-10-09-url.png)    

Source ref 和 Destination ref 均选择 master 即可，点击后面的 Add Spec, 点击Finish。其中注意**Force Update**，
我尝试不选中，点击Finish后Github上没有push我的工程上去，也试过没有勾选也可以push，查资料说这是强制推送，但还没有进一步去深究这个东西。    

![](img/2016-10-09-ref.png)  

最后，去自己的Github账号查看repository是否已上传文件。  

## Reference   

[http://blog.csdn.net/shichaosong/article/details/9007759](http://blog.csdn.net/shichaosong/article/details/9007759)   
[http://blog.csdn.net/csu_max/article/details/40555819](http://blog.csdn.net/csu_max/article/details/40555819)



