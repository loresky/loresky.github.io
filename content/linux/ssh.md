+++
title= "Ssh"
date= "2022-04-03T12:50:11+08:00"
tags = []
featured_image = ""
description = ""
+++

### pacman -Sy openssh

### 配置/etc/ssh/sshd_config
echo PermitRootLogin yes > /etc/ssh/sshd_config

### 开启sshd服务
systemctl start sshd

### 开机启动sshd服务
systemctl enable sshd

### 重启sshd服务
systemctl restart sshd
