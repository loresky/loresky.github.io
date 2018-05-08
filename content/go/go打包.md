+++
title= "Go打包"
date= "2018-05-08T14:42:56+08:00"
tags = []
featured_image = ""
description = ""
+++

```
CGO_ENABLED=0 GOOS=windows GOARCH=386 go build main.go 
```

## GOOS：目标平台的操作系统  
darwin、freebsd、linux、windows

## GOARCH：目标平台的体系架构  
386、amd64、arm

交叉编译不支持 CGO 所以要禁用它
