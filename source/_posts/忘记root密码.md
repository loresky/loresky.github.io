---
title: linux忘记root密码
date: 2017-04-23 10:56:13
categories: linux
tags: linux
---

进入grub的时候，按上下箭头
选择平时启动的那个内核
按 e 编辑这么一行：
``` shell
kernel /vmlinuz root=/dev/sda2 init=/bin/bash rw
```
**注意黑体字，就是在你原有的内核选项上增加的内容**
按 enter 生效
按 b 启动
然后就在命令行了，输入passwd root 进行密码修改