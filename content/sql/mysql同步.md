+++
title= "Mysql同步"
date= "2022-06-04T09:17:27+08:00"
tags = []
featured_image = ""
description = ""
+++

### 1.mysql开启 Binlog

``` mysql
server_id         = 223344
binlog_format     = row
binlog_row_image  = full
expire_logs_days  = 1
log_bin           = mysql-bin
```

**配置解释**

server-id: 对于 MySQL 中的每个服务器和复制客户端必须是唯一的
binlog_format：必须设置为 row 或者 ROW
binlog_row_image：必须设置为 full
expire_logs_days：二进制日志文件保留的天数，到期会自动删除
log_bin：binlog 序列文件的基本名称

### 2.重启 MySQ

### 3.验证 binlog、binlog_row_image

``` mysql
show variables like 'binlog_format';
show variables like 'binlog_row_image';
```

**输出的结果：**
format value 应该是"ROW"
binlog_row_image value 应该是"FULL"

### 4.创建MySQL账号

``` mysql
FLUSH PRIVILEGES;
-- 创建用户
CREATE USER canal IDENTIFIED BY 'canal';
-- 数据库赋于全局权限
GRANT SELECT, REPLICATION SLAVE, REPLICATION CLIENT ON *.* TO 'canal'@'%';
-- GRANT ALL PRIVILEGES ON *.* TO 'canal'@'%' ;
FLUSH PRIVILEGES;
```

