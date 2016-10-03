---
title: "Set up my own blog on Github, Ubuntu Kylin 14.04"
layout: post
date: 2016-10-02
permalink : /post/My-own-blog
tag:
- Github pages
- Jekyll
blog: true
---

### 前言  
  其实早在大一的时候，就已经知道了Github和Gitlab的存在，而且都已经创建了各自的账号。可是两年来，只能听到自己心里朦胧的声音:"我想当一名程序猿"，可是我想往哪个方面发展？我要怎么样做才有资格当一名程序猿？我现在的程度是怎么样的？无数的质疑声不断地敲打着自己，终于，熬到了大三。逝去的时间已无法挽回，未来，才是我应该去抓住的。尽管前路迷茫，不知道自己最终会走向何方，但我此时此刻，已经开始努力了，我在为我的将来而奋斗了，无悔。但行好事，莫问前路。抛弃以前的一切，从现在开始，一步一个脚印，我相信，会有收获的。Fighting ❤ ❤ ❤  
  抱着这样的想法，鼓足勇气，重新创建了一个Github账号，很认真地填了自己的个人信息，上传了照片，开始做大二一直想做却没做成功的事情--搭建个人博客。很高兴，我做到了，时隔半年吧，终于把自己的个人博客这件事实现了，虽然晚了很多，但总比一辈子没有去做的好。以后，我会把自己的学习(学习上的东西我会尝试用英文记载，努力提高自己的知识水平，可能会有很多语法、单词上的拼写错误，望见谅)、生活等各种事情记录在这里，坚持去维护这个自己努力得来的小空间。     
  下面就是我今天忙活了一下午+一晚上的过程，中间遇到困难的时候感谢Hareric的帮助，虽然没有帮我解决问题，但给了我思路，幸好自己没有再次放弃，而是一步一步去探索解决问题。实现后发现过程其实不难，关键是对于自己第一次摸索的东西，不能害怕，要坚持不懈！以下过程是在Ubuntu Kylin 14.04 64位环境下实现：   

## Sign in GitHub && new repository   

**Notice**:       

**1. The name of the repository must be the form of “username.github.io”.**  

**2. Description can be omitted.**    

**3. Check the box to generate a README file.** 

![](img/2016-10-02-1.png)      

## install Git Client  

GitHub is server, so we need to install Git client to use git in the local file. 

`$ sudo apt-get install git-core`    

If you wanna upload your local file to the repository, you need to follow these:  

**1. Set username and email. GitHub will record them on each commit**   

```    
$ git config --global user.name "your name"  

$ git config --global user.email "your_email@youremail.com"     
```    

**2. Clone repository from or to GitHub**    

```
git init   

git add .   

git commit –m “comment”    

git remote add origin https://the address of your repository  

git push -u origin master     

```        

During the process, it might ask you to input your username and password on GitHub.        

## Bind the free domain name for your blog

**1. Apply on Freenom, you can free using for one year**  

![](img/2016-10-02-2.png)      

**2. New file named “CNAME” and write your domain name in it**    

e.g. My CNAME: `xusiqi.tk`              

**3. Register a DNSPod account and then add some A records**  

![](img/2016-10-02-3.png)        

**4. Modify nameserver on** [**Freenom**](www.freenom.com) 

  We register domain name on Freenom, so the default DNS of domain name is provided by Freenom.   
  
  Therefore,we need to modify the DNS on Freenom and let DNSPod provide domain name resolving.    
  
  The steps are: MyDomains -> Manage Domain -> Management Tools -> NameServers.   
  
**5. Write the two NS records from DNSPod to Freenom.**   

![](img/2016-10-02-4.png)    

  
## Test       
`Dig domain name`  

## Reference  
[http://blog.bensonlin.me](http://blog.bensonlin.me)  
[http://www.jianshu.com/p/882f155897f0#](http://www.jianshu.com/p/882f155897f0#) 
[https://segmentfault.com/a/1190000004587329](https://segmentfault.com/a/1190000004587329) 
[http://www.jianshu.com/p/08656eb84974](http://www.jianshu.com/p/08656eb84974)  
[http://itcoding.tk/2016/06/26/set-up-custom-domain-for-github-pages/](http://itcoding.tk/2016/06/26/set-up-custom-domain-for-github-pages/)  
[https://support.dnspod.cn/Kb/showarticle/tsid/177/#ChangeDomainNS](https://support.dnspod.cn/Kb/showarticle/tsid/177/#ChangeDomainNS)  

