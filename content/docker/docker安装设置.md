---
title: docker安装设置
date: 2017-06-13 18:00:00
---

## * [Docker 中国](https://www.docker-cn.com/)

## * [官网安装教程](https://docs.docker.com/engine/installation/#supported-platforms)

***


## Docker 官方为了简化安装流程，提供了一套安装脚本，Ubuntu 和 Debian 系统可以使用这套脚本安装：
`curl -sSL https://get.docker.com/ | sh`

## 阿里云的安装脚本
`curl -sSL http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -`

[阿里服务器安装Docker](https://help.aliyun.com/document_detail/60742.html?spm=5176.11065259.1996646101.searchclickresult.3ba3232c91aYPa)

## DaoCloud 的安装脚本
`curl -sSL https://get.daocloud.io/docker | sh`

## docker添加用户到组
``` bash
sudo gpasswd -a ${USER} docker
sudo service docker restart
newgrp - docker
```