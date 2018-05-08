+++
title= "Ftp服务器"
date= "2018-05-08T16:12:44+08:00"
tags = []
featured_image = ""
description = ""
+++

## sudo apt-get install vsftpd

### 运行
```
sudo service vsftpd status
sudo service vsftpd stop
sudo service vsftpd restart
sudo service vsftpd status
```

### 配置vsftpd.conf
sudo gedit /etc/vsftpd.conf
```
listen=YES
local_root=/
anon_root=/
#允许匿名访问
anonymous_enable=YES
#允许本地用户对FTP服务器文件有写权限
write_enable=YES
#系统自动维护上传和下载日志
xferlog_enable=YES
#设定FTP服务器将启用FTP数据端口的连接请求
connect_from_port_20=YES
#标准格式写日志文件
xferlog_std_format=YES
#设置本地用户默认掩码
local_umask=022
#不允许匿名用户上传文件
anon_upload_enable=YES
#不允许匿名用户写文件
anon_mkdir_write_enable=YES
#打开匿名用户删除和重命名的权
anon_other_write_enable=YES
#设置PAM外挂模块提供的认证服务所使用的配置文件名
pam_service_name=vsftpd
#是否允许ftpusers文件中得用户登录FTP服务器，默认为NO
userlist_enable=YES
#是否使用tcp_wrappers作为主机访问控制方式
tcp_wrappers=YES
idle_session_timeout=600
data_connection_timeout=120
max_clients=10
max_per_ip=5
local_max_rate=50000
utf8_filesystem=YES
```