---
title: linux硬盘安装
date: 2017-07-03 14:56:38
---
## Ubuntu
``` bash
title Install Ubuntu
root (hd0,0)
kernel (hd0,0)/vmlinuz.efi boot=casper iso-scan/filename=/ubuntu.iso locale=zh_CN.UTF-8
initrd (hd0,0)/initrd.lz
title reboot
reboot
title halt
halt
```