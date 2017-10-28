---
title: MySQL配置文件详解
date: 2017-04-18 12:16:18
categories: 数据库
tags: 数据库
---

找到C:\Program Files\MariaDB 5.5\data\my.ini
``` bash
[mysqld]下增加character-set-server=utf8
[client]下增加default-character-set=utf8
[MySQL] 下增加default-character-set=utf8
```

设置MySQL5.6的远程连接
``` mysql
use mysql; 
//为root添加远程连接的能力  
GRANT ALL PRIVILEGES ON *.* TO root@"%" IDENTIFIED BY "root";    
//设置root用户密码 
update user set Password = password('123456') where User='root';
//刷新刚才的内容
flush privileges;  
```