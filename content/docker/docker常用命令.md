---
title: docker常用命令
date: 2017-06-27 13:12:12
---
## 查看当前机器上的镜像：
```xml
docker images
```

## 下载镜像：
```xml
docker pull <image>
```

## 删除镜像：
```xml
docker rmi <image>
```

## 运行镜像：
```xml
docker run -d -p 3306:3306 hub.c.163.com/library/tomcat:latest
```

## 查看容器列表及状态：
```xml
docker ps -a
```