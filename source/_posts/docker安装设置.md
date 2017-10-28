---
title: docker安装设置
date: 2017-06-13 18:00:00
categories: docker
tags: docker
---

## * [Docker 中国](https://www.docker-cn.com/)

## * [官网安装教程](https://docs.docker.com/engine/installation/#supported-platforms)

## * [docker-engine地址](https://apt.dockerproject.org/repo/pool/main/d/docker-engine/)

***


## Docker 官方为了简化安装流程，提供了一套安装脚本，Ubuntu 和 Debian 系统可以使用这套脚本安装：
`curl -sSL https://get.docker.com/ | sh`

## 阿里云的安装脚本
`curl -sSL http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -`

## DaoCloud 的安装脚本
`curl -sSL https://get.daocloud.io/docker | sh`

## docker添加用户到组
``` bash
sudo gpasswd -a ${USER} docker
sudo service docker restart
newgrp - docker
```