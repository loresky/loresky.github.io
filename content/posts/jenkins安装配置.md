+++ 
title= "jenkins安装配置"
date = 2022-06-04T09:25:44+08:00
tags = []
featured_image = ""
description = ""
+++


### 地址

<https://www.jenkins.io/>

### 启动

命令行运行命令解压war包：java -jar jenkins.war　（默认情况下端口是8080，如果要使用其他端口启动，可以通过命令行”java –jar Jenkins.war --httpPort=80”的方式修改）

### 配置 jdk maven

**Manage Jenkins > Global Tool Configuration**

[![XZxPzR.png](https://s1.ax1x.com/2022/05/27/XZxPzR.png)](https://imgtu.com/i/XZxPzR)

### 插件安装
**Manage Jenkins > Plugin Manager**

|名称|描述|
|---|---|
|Publish over SSH|通过SSH连接其他Linux机器,远程传输文件及执行Shell命令|
|Deploy to container Plugin|插件将应用发布到tomcat|
|Post build task|构建后进行的操作|

### 设置邮箱[网上文档](https://www.cnblogs.com/xksy/p/15790421.html)

### 配置gitee

**gitee设置私人令牌**
[![XeSxdf.png](https://s1.ax1x.com/2022/05/27/XeSxdf.png)](https://imgtu.com/i/XeSxdf)

**设置gitee私人令牌 Manage Jenkins > Configure System**
[![XeCeGF.png](https://s1.ax1x.com/2022/05/27/XeCeGF.png)](https://imgtu.com/i/XeCeGF)

### 新建项目
**设置gitee私人令牌 Manage Jenkins > Configure System**
[![XePgk6.png](https://s1.ax1x.com/2022/05/27/XePgk6.png)](https://imgtu.com/i/XePgk6)

**gitee项目地址**
[![XePqtf.png](https://s1.ax1x.com/2022/05/27/XePqtf.png)](https://imgtu.com/i/XePqtf)

**构建触发器 gitee项目代码更新jenkins就更新代码**
[![XeFS2D.png](https://s1.ax1x.com/2022/05/27/XeFS2D.png)](https://imgtu.com/i/XeFS2D)
[![XeFWsH.png](https://s1.ax1x.com/2022/05/27/XeFWsH.png)](https://imgtu.com/i/XeFWsH)

**构建**
``` java
clean package -Dmaven.test.skip=true
```

[![Xe26SJ.png](https://s1.ax1x.com/2022/05/27/Xe26SJ.png)](https://imgtu.com/i/Xe26SJ)

**构建后操作**

[![Xe2b6A.png](https://s1.ax1x.com/2022/05/27/Xe2b6A.png)](https://imgtu.com/i/Xe2b6A)

``` shell
#!/bin/sh
cp /root/.jenkins/workspace/yangxin_erp_solr/erp-solr/target/erp-solr-4.0.0.jar /data/project/back/erp-solr.jar

#PID=`ps -ef |grep 项目名称 |grep -v grep | awk '{print $2}'`
PID=`ps -ef |grep 'erp-solr.jar' |grep -v grep | awk '{print $2}'`
if [ ! "$PID" ]
then # 这里判断TOMCAT进程是否存在
 echo $PID"erp-solr进程不存在"
else
 echo "erp-solr进程存在 杀死进程PID$PID"
 kill -9 $PID
fi
#nohup java -jar /data/project/back/erp-solr.jar --spring.profiles.active=prod > /data/project/back/logs/erp_solr/erp_solr_$(date +%Y%m%d).log &
nohup java -jar /data/project/back/erp-solr.jar --spring.profiles.active=prod | cronolog -l /data/project/back/logs/erp_solr/erp_solr.log /data/project/back/logs/erp_solr/erp_solr.log.%Y-%m-%d &
#根据重启后是否有当前应用判断启动是否成功
pid=$(ps -ef | grep java| grep 'erp-solr.jar'|awk -F '[ ]+' '{print $2}')
echo $pid
if [ -z $pid ]
then
 echo "erp-solr启动失败"
 exit 1
else
 echo 'erp-solr.jar' : $pid "启动成功"
fi
```