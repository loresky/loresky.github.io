---
title: Virtualbox中win7虚拟机中U盘不可用问题的解决
date: 2017-11-13 19:51:18
---

### 主机运行多是Ubuntu17.04，虚拟机是Win7,U盘无反映
安装‘Oracle VM VirtualBox Extension Pack’
下载地址：http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack

用户权限添加
添加usbfs 用户组（virtualbox 装完成后会有 vboxusers 和vboxsf ）                  
sudo groupadd usbfs   

将你的linux常用用户添加到vboxusers、usbfs这个两个组中
sudo adduser kuein vboxusers  
sudo adduser kuein usbfs  