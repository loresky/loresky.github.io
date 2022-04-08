+++
title= "Archlinux安装"
date= "2022-04-02T13:18:56+08:00"
tags = []
featured_image = ""
description = ""
+++

打开网卡  ip link  set ens192 up
wifi      iwctl

Arch Linux 软件仓库镜像修改文件 /etc/pacman.d/mirrorlist:  

Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch




### 挂载磁盘
mount /dev/sdX1 /mnt  
### 安装系统 顺便安装一些常用工具  
pacstrap /mnt base base-devel linux linux-firmware networkmanager dhcpcd vim zsh git 

### 配置Fstab/Fstab 定义了存储设备和分区整合系统的方式。详情可见 Wiki
genfstab -L /mnt >> /met/etc/fstab

### Chroot使用 Arch Chroot 进入刚安装的白板系统
arch-chroot /mnt

### 时区/设置时区为上海
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

### 同步时钟
hwclock --systohc --utc

### 本地化/只使用英文 tty 避免报错的时候全是方块或者不能识别的的奇妙符号。
```
echo 'en_US.UTF-8 UTF-8' >> /etc/locale.gen
echo 'zh_CN.UTF-8 UTF-8' >> /etc/locale.gen
locale-gen
echo LANG=en_US.UTF-8 > /etc/locale.conf
```

### Hostname
设置主机名称 要设置 hostname，将其添加 到 /etc/hostname,myhostname 是需要的主机名

echo myhostname > /etc/hostname

### 查看你的网卡
```
ip link
//ens33 通常是你非 lo 的另外一个
systemctl enable dhcpd@ens33
```

### grub[地址](https://wiki.archlinux.org/title/GRUB_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#%E5%AE%89%E8%A3%85)
```
sudo pacman -S grub
//验证安装
grub-install --recheck /dev/sda
//安装 GRUB 的磁盘/--target=i386-pc指示grub-install是为使用BIOS的系统安装. 推荐一直标明这点以防混淆
grub-install --target=i386-pc /dev/sda
//UEFI 系统
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
```

### 生成 grub.cfg
grub-mkconfig -o /boot/grub/grub.cfg

### 设置密码
passwd

### 添加用户
//创建用户的同时创建 Home 目录
useradd -m username

### 重启
exit
umount -R /mnt
reboot










