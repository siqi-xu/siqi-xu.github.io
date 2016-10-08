---
title: "Some Linux Commands"
layout: post
date: 2016-10-04
permalink : /post/Some-Linux-Commands
tag:
- Linux
- Ubuntu
blog: true
---  

大一开始就有机会去接触Ubuntu，可是那时候一直抱着我用不到的想法，懒得去接触新的东西，一直拖到现在，终于，要用到的时候，发现一点都不熟悉。没事，那就从现在开始一点一点积累吧，加油！  

## 一些常用的命令行  

#### 将tgz文件解压到指定目录  

`sudo tar zxvf 文件名.tgz -C 指定目录`   

#### 解压windows下常用的zip压缩文件包    

`sudo unzip 文件名.zip`       

#### 创建目录  

`sudo mkdir dirname`  

#### 拷贝文件或目录       

`sudo cp 源文件或目录 目标文件或目录`   

#### 移动、重命名文件或目录         

`sudo mv 源文件或目录 目标文件或目录`    

#### 删除文件或目录            

`sudo rm -r 文件或目录`         

### 修改文件权限   

- 添加权限   `sudo chmod 对象 + 操作 文件或目录`     

如：`sudo chmod a+w test`     
   
- 删除权限   `sudo chmod 对象 - 操作 文件或目录`      

如：`sudo chmod go-rw test.txt`         

对象：     

u 代表所有者（user）   

g 代表所有者所在的组群（group）    

o 代表其他人，但不是u和g （other）    

a 代表全部的人，也就是包括u，g和o     

操作：      

r 表示文件可以被读（read）  

w 表示文件可以被写（write）           

x 表示文件可以被执行（如果它是程序的话）                  

#### 修改ReadOnly文件目录下所有文件的可读可写可执行的权限   

`sudo chmod -R 777 文件夹名`     

#### 

## Reference   
[http://www.111cn.net/sys/linux/43880.htm](http://www.111cn.net/sys/linux/43880.htm)    
[http://www.cppblog.com/deercoder/articles/110129.html](http://www.cppblog.com/deercoder/articles/110129.html)  



