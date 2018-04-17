---
title: linux配置
date: 2017-04-23 10:55:13
---

``` bash
依赖: sudo apt-get install gdebi-core
语言支持不见了: sudo apt-get install language-selector-gnome
64位系统lib: sudo apt-get install lib32ncurses5
配置lib: sudo apt-get install -f
```

## 环境
``` bash
export GOROOT=/opt/go
export GOPATH=/home/cy/GoProjects
export GRADLE_HOME=/opt/gradle
export NODE_HOME=/opt/node
export JAVA_HOME=/opt/jdk1.8
export JRE_HOME=/opt/jdk1.8/jre
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export ANDROID_HOME=/opt/android-sdk-linux
export PATH=:$PATH:$JAVA_HOME/bin:$JRE_HOME/bin:$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$GRADLE_HOME/bin:$NODE_HOME/bin:$GOROOT/bin:$GOPATH/bin:

```

## 桌面图标
``` bash
[Desktop Entry]
Name = Genymotion
comment= genymotion
Exec=/opt/genymotion/genymotion
Icon=/opt/genymotion/icons/icon.png
Terminal=false
Type=Application
Categories=Utility;TextEditor;Development;IDE;

[Desktop Entry]
Version=1.0
Type=Application
Name=xmind
Comment=
Exec=/opt/xmind/XMind_amd64/XMind
Icon=/opt/xmind/XMind_amd64/xmind_file.ico
Path=/opt/xmind/XMind_amd64
Terminal=false
StartupNotify=false
```

## 五笔
`sudo apt-get install fcitx-table-wbpy`

## Fcitx输入中文不显示候选词框的解决办法
`sudo apt remove fcitx-module-kimpanel`
