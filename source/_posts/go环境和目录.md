---
title: go环境和目录
date: 2017-09-20 01:53:21
categories: golang
tags: golang
---

## 最为重要的环境变量:
**$GOROOT **表示 Go 在你的电脑上的安装位置,它的值一般都是$HOME/go,当然,你也可以安装在别的地方。
**$GOARCH **表示目标机器的处理器架构,它的值可以是 386、amd64 或 arm。
**$GOOS **表示目标机器的操作系统,它的值可以是 darwin、freebsd、linux 或 windows。
**$GOBIN **表示编译器和链接器的安装位置,默认是$GOROOT/bin

## Go 安装目录
* /bin :包含可执行文件,如:编译器,Go 工具
* /doc :包含示例程序,代码工具,本地文档等
* /lib :包含文档模版
* /misc:包含与支持 Go 编辑器有关的配置文件以及 cgo 的示例
* /os_arch
* /src:包含标准库的包的对象文件(.a):包含源代码构建脚本和标准库的包的完整源代码(Go 是一门开源语言)
* /src/cmd:包含 Go 和 C 的编译器和命令行脚本