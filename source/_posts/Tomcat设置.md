---
title: Tomcat设置
date: 2017-04-23 10:49:47
categories: tomcat
tags: tomcat
---

## tomcat配置虚拟目录
*apache-tomcat-8.0.18\conf\Catalina\localhost  下建一个xml*
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Context path="/qqq"  docBase="E:\qqq" reloadable="false" />
```
文件名改成你自己的譬如http://localhost:8080/qqq ，文件名就为qqq.xml 
再打开Tomcat安装目录,打开conf/web.xml 文件，在其中找到
```xml
<init-param>
<param-name>listings</param-name>
<param-value>false</param-value>
</init-param>
```
将false设成true保存，重启Tomcat。
在浏览器输入  http://localhost/demo/，就可以显示文件列表了。