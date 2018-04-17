---
title: grub2命令启动win7
date: 2017-07-03 14:49:26
---

##  grub2命令启动win7
**假设win7安装在第一硬盘第一分区（即hd0,1，如果不是，自行修改）：**
``` shell
grub>insmod ntfs
grub>set root='hd0,1'
grub>chainloader +1
grub>boot
```
**或者试试：**
``` shell
grub>insmod ntfs
grub>search --no-floppy --set=root  /bootmgr
grub>chainloader +1
grub>boot
```