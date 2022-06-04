+++ 
title= "cronolog日志切割"
date = 2022-06-04T09:35:12+08:00
tags = []
featured_image = ""
description = ""
+++

### 查看cronolog
``` bash
which cronolog
/usr/local/sbin/cronolog
nohup java -jar log.jar | /usr/local/cronolog/sbin/cronolog logs/console-%Y-%m-%d.out &
```

### 配置nginx的conf文件
```
error_log "pipe:/usr/sbin/cronolog /home/admin/logs/cronolog/%Y/%m/%Y-%m-%d-error.log" error;
access_log "pipe:/usr/sbin/cronolog /home/admin/logs/cronolog/%Y/%m/%Y-%m-%d-%H-access.log" main;
```

### 结合apache使用
**编辑httpd.conf文件，将其中的**
```
vim /usr/local/apache2/conf/httpd.conf
将默认日志： CustomLog "logs/access_log" combined
修改为：CustomLog "|/usr/local/sbin/cronolog /log/www/access_%Y%m%d.log" combined 即可。其中%Y%m%d为日志文件分割方式，即为“年月日”
 /usr/local/apache2/bin/apachectl restart
```

### 对Tomcat日志的切割
**tomcat/bin/catalian.sh**
```
org.apache.catalina.startup.Bootstrap "$@" start / >> "$CATALINA_BASE"/logs/catalina.out 2&1 &
修改
org.apache.catalina.startup.Bootstrap "$@" start / |/usr/local/sbin/cronolog "$CATALINA_BASE"/logs/catalina.out.%Y-%m-%d>> /dev/null 2&1 &
```


### cronolog所支持的时间相关的pattern字符，如/www/log/%y/%m/%d/access.log。其pattern为％字符后跟一特殊字符，简述如下：
**转义符:** 
* %    %字符
* n    换行
* t    水平制表符

**时间域:** 
* H    小时(00..23)
* I    小时(01..12)
* p    该locale下的AM或PM标识
* M    分钟(00..59)
* S    秒 (00..61, which allows for leap seconds)
* X    该locale下时间表示符(e.g.: "15:12:47")
* Z    时区。若时区不能确定，则无意义

**日期域:**  
* a    该locale下的工作日简名(e.g.: Sun..Sat)
* A    该locale下的工作日全名(e.g.: Sunday ..  Satur-ay)
* b    该locale下的月份简称(e.g.: Jan .. Dec)
* B    该locale下的月份全称(e.g.:  January .. December)
* c    该locale下的日期和时间(e.g.: "Sun Dec 15  14:12:47 GMT 1996")
* d    当月中的天数 (01 .. 31)
* j    当年中的天数 (001 .. 366)
* m    月数 (01 .. 12)
* U    当年中的星期数，以周日作为一周开始,其中第一周为首个含星期天的星期(00..53)
* W    当年中的星期数，以星期一作为一周的开始,其中第一周为首个含星期天的星期(00..53)
* w    工作日数(0 .. 6, 0表示星期天)
* x    该locale下的日期表示(e.g. "13/04/97")
* y    两位数的年份(00 .. 99)
* Y    四位数的年份(1970 .. 2038)

https://www.91mszl.com/zhangwuji/article/details/1315