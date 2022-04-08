+++
title= "Fcitx5输入法"
date= "2022-04-03T09:48:17+08:00"
tags = []
featured_image = ""
description = ""
+++

### 卸载Fcitx4
sudo pacman -Rs $(pacman -Qsq fcitx)

### 安装Fcitx5
sudo pacman -S fcitx5-im fcitx5-chinese-addons fcitx5-gtk fcitx5-qt fcitx5-configtool fcitx5-material-color fcitx5-pinyin-moegirl fcitx5-pinyin-zhwiki

* fcitx5: 输入法基础框架主程序
* fcitx5-im 包组提供了fcitx5 本体、配置工具、和必要的输入法模块
* fcitx5-chinese-addons: 中文输入的支持：拼音、五笔拼音等
* fcitx5-gtk: GTK程序的支持
* fcitx5-qt: QT5程序的支持
* fcitx5-configtool: 图形化配置工具
* kcm-fcitx5: KDE桌面环境的支持
* fcitx5-material-color: Material Design 配色主题[地址](https://github.com/hosxy/Fcitx5-Material-Color)
* fcitx5-pinyin-zhwiki: 肥猫制作的维基百万词库，没有版权风险,[地址](https://github.com/felixonmars/fcitx5-pinyin-zhwiki)
* fcitx5-pinyin-moegirl: outloudvi制作的萌娘百科词库，[地址](https://github.com/outloudvi/mw2fcitx)


### 环境变量 /etc/environment
```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
```

### 系统登录后默认启动Fcitx5输入法  ~/.xprofile
fcitx5 &

### 配置输入法皮肤fcitx5-material-color
#### 然后修改配置文件 ~/.config/fcitx5/conf/classicui.conf
```
# 垂直候选列表
Vertical Candidate List=False

# 按屏幕 DPI 使用
PerScreenDPI=True

# Font (设置成你喜欢的字体)
Font="思源黑体 CN Medium 13"

# 主题
Theme=Material-Color-Pink
```