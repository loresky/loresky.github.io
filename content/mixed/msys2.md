+++
title= "Msys2"
date = "2022-03-27T19:14:27+08:00"
tags = []
featured_image = ""
description = ""
+++

#### 参考 https://jingyan.baidu.com/article/4b07be3ca9406648b280f357.html
#### 参考 https://www.thinbug.com/q/47379214

清华源 https://mirrors.tuna.tsinghua.edu.cn/msys2/

pacman 配置 https://mirrors.tuna.tsinghua.edu.cn/help/msys2/


1.  打开msys2终端，输入：curl https://sh.rustup.rs -sSf | sh
2.  default host triple:输入x86_64-pc-windows-gnu
3.  ./rustup default stable-x86_64-pc-windows-gnu /更新Rust：rustup update
4. /etc/profile 最后一行输入 export PATH=$PATH:/d/art/rust/cargo/bin:/d/art/starship:/d/art/Git/bini:/d/art/fd:

