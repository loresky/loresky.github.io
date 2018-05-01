+++
title= "Linux和Windows双启动带来的时间同步问题"
date= "2018-04-28T17:48:31+08:00"
tags = []
featured_image = ""
description = ""
+++

**via:**http://www.theitstuff.com/how-to-sync-time-between-linux-and-windows-dual-boot-2 

+ 点击 Windows 系统中的开始菜单，然后搜索 regedit
+ HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation。
+ 在右边窗口，右键点击空白位置，然后选择 New >> DWORD(32 bit) Value。
+ 之后，你会新生成一个条目，而且这个条目默认是高亮的。将这个条目重命名为 RealTimeIsUniversal 并设置值为 1
+ 所有的配置就完成了，下次重启，就不会再有时间同步问题了。
