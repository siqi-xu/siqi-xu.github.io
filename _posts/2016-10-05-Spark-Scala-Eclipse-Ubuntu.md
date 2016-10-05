---
title: "Spark Scala Eclipse Ubuntu"
layout: post
date: 2016-10-05
permalink : /post/Spark-Scala-Eclipse-Ubuntu
tag:
- Spark 
- Scala 
- Eclipse 
- Ubuntu
blog: true
---  

Spark,第一次听到这个词，其实并没有反应是星火英语，也没有反应是美剧中常表示的擦出火花的意思（本人英语比较差啦，但挺喜欢看美剧的），刚开始听到实验室师兄说要学习这个东西的时候，
就只觉得“哇，好高大上啊，好厉害啊，我都不懂这些”。然后默默去搜索了一些，看看到底spark是什么东东，那时候，对spark有了一个模糊的概念：类似于Hadoop的一个框架，可以更高效地处理大规模的数据。
但自己心心念念想要试着去用这个东西，是在师兄有关spark的分享会之后。分享会是在九月份开学第一天晚上的，那天还是我的生日。开学第一天，仅有的几个人在实验室，我也怀着忐忑的心情参加了。
其实自己很害怕有关实验室的一切东西，因为我自认为我能力不足，也没有尽全力投入到实验室中，我害怕面对，可能我是害怕被看穿这种心理吧。但我说过，大三，我想要改变自己，我要努力，我要充实自己！
（学习是我生命中最重要的事情.jpg）所以我试着去做了，虽然时间跨度有点大，九月初到十月初，嗯，就是今天，才把Ubuntu下eclipse中使用spark的环境配置好。看过我前面blog的可能会知道，我对Ubuntu还不熟悉，
所以为了去学习使用spark，我还去学习了Ubuntu快速入门教程、操作系统以及鸟叔的教程（我的专业没有开设操作系统这门课）等。现在回头想想，好像自己去做这些看起来不应该花费那么多时间的事情，
总会花费不短的时间才能做到，这让我一度怀疑自己的学习能力。既然选择了远方，便只顾风雨兼程。我选择了这条路，我会坚持走下去的，因为我不讨厌做这些，只是坎坷了点。      

既然配置好了，就把自己的配置过程列一下吧，当是自己总结反思，或许还会帮助到想要学习这方面的人呢。      

Spark是由scala开发，目前提供java, python的接口.      

### 下载             
　 - 下载scala压缩包，进入链接http://www.scala-lang.org/,点击download下载scala，并解压到/opt/  
    
   - 下载jdk压缩包，进入链接http://www.oracle.com/technetwork/java/javase/downloads/index.html，下载最新版jdk，若为64位系统请下载jdk-8u101-linux-x64.tar.gz, 32位系统下载jdk-8u101-linux-i586.tar.gz，下载完成后解压到opt目录下。           
   
　 - 下载spark压缩包，进入链接https://spark.apache.org/downloads.html，当前spark最新的版本是2.1.0，但目前请不要下载2.0以上的新版本！！！因为spark2.0以上的最新版本解压后都缺少了lib目录！！！ 而lib目录里面有一个spark-assembly...hadoop.jar包对于能够成功运行scala project非常重要！我之前就一直被困在这里，明明命令行运行都已经成功了，但在eclipse中就一直不行了，终于，自己实在找不到办法了，就去请教了jingda，才得知要选择**1.6.2版本以下才有lib目录**。最后，终于配置成功了。   

![](img/2016-10-05-0.jpg)    
 
 - 下载带Scala-SDK的eclipse，配置好spark、scala环境之后就可以直接运行scala project了，不用再去安装其他插件，因此我推荐下载带Scala SDK版eclipse，解压到相应目录就可以使用了。          
 
![](img/2016-10-05-1.jpg)    

### 配置环境变量
　　配置环境变量,编辑/etc/profile,执行以下命令     
　　sudo gedit /etc/profile
       在文件最下方增加（注意版本）：
       ```  
          #Seeting JDK JDK环境变量    
            export JAVA_HOME=/opt/jdk1.8.0_101   
            export JRE_HOME=${JAVA_HOME}/jre        
            export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib               
            export PATH=${JAVA_HOME}/bin:${JRE_HOME}/bin:$PATH               
          #Seeting Scala Scala环境变量       
            export SCALA_HOME=/opt/scala-2.11.8                
            export PATH=${SCALA_HOME}/bin:$PATH          
          #setting Spark Spark环境变量      
            export SPARK_HOME=/opt/spark-hadoop/                
          #PythonPath 将Spark中的pySpark模块增加的Python环境中        
            export PYTHONPATH=/opt/spark-hadoop/python         
            ```   
　　保存文件， 重启电脑，使/etc/profile永久生效，临时生效，打开命令窗口，执行 source /etc/profile  在当前窗口生效.

### 测试  
测试安装结果,打开命令窗口，切换到Spark根目录 `cd /opt/spark-hadoop`    
打开Scala到Spark的连接窗口  `sudo ./bin/spark-shell`              
![](img/2016-10-05-01.jpg)    
![](img/2016-10-05-02.jpg)    
![](img/2016-10-05-03.jpg)   
        
这里我们可以通过word count这个例子来感受下Spark任务的执行过程。启动spark-shell后，会打开Scala命令行，然后按照以下步骤输入脚本：    

步骤1   输入val lines = sc.textFile("./README.md", 2)，执行结果如图     
![](img/2016-10-05-a.jpg)     
步骤2   输入val words = lines.flatMap(line => line.split(" "))，执行结果             
![](img/2016-10-05-b.jpg)           
步骤3   输入val ones = words.map(w => (w,1))，执行结果                            
![](img/2016-10-05-c.jpg)            
步骤4   输入val counts = ones.reduceByKey(_ + _)，执行结果     
![](img/2016-10-05-d.jpg)             
步骤5   输入counts.foreach(println)，任务执行过程如图，输出结果          
![](img/2016-10-05-e.jpg)              
![](img/2016-10-05-f.jpg)                     
![](img/2016-10-05-g.jpg)                       
在这些输出日志中，我们先是看到Spark中任务的提交与执行过程，然后看到单词计数的输出结果，最后打印一些任务结束的日志信息。   

## 单机eclipse下运行WordCount程序   
创建scala工程，工程名字为WordCount     

![](img/2016-10-05-2.jpg)  
![](img/2016-10-05-3.jpg)   

修改依赖的scala版本为scala2.10.x,默认下是scala 2.11.7   
![](img/2016-10-05-4.jpg)   
加入spark的jar包    
![](img/2016-10-05-5.jpg)      
![](img/2016-10-05-6.jpg)    
![](img/2016-10-05-7.jpg)   
![](img/2016-10-05-8.jpg)  
![](img/2016-10-05-class.jpg)     
![](img/2016-10-05-9.jpg)       
![](img/2016-10-05-10.jpg)  
程序的入口函数是main，所以要先定义mian，同时把class修改为object    
![](img/2016-10-05-11.jpg)        

## Reference    
[http://www.cnblogs.com/adienhsuan/p/5654484.html](http://www.cnblogs.com/adienhsuan/p/5654484.html)               
[https://yq.aliyun.com/articles/4246?spm=5176.100240.searchblog.20.jgF4uA#](https://yq.aliyun.com/articles/4246?spm=5176.100240.searchblog.20.jgF4uA#)           
[http://www.it610.com/article/5107569.htm](http://www.it610.com/article/5107569.htm)      


