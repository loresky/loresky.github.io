+++
title= "Podman"
date= "2022-04-04T12:31:58+08:00"
tags = []
featured_image = ""
description = ""
+++




## Podman常用命令
###  容器
```
podman run           创建并启动容器
podman start         启动容器
podman ps            查看容器
podman stop          终止容器
podman restart       重启容器
podman attach        进入容器
podman exec          进入容器
podman export        导出容器
podman import        导入容器快照
podman rm            删除容器
podman logs          查看日志
```

### 镜像
```
podman search                检索镜像
podman pull                  获取镜像
podman images                列出镜像
podman image Is              列出镜像
podman rmi                   删除镜像
podman image rm              删除镜像
podman save                  导出镜像
podman load                  导入镜像
podmanfile                   定制镜像（三个）
  podman build             构建镜像
    podman run               运行镜像
    podmanfile               常用指令（四个）
      COPY                 复制文件
        ADD                  高级复制
        CMD                  容器启动命令
        ENV                  环境变量
        EXPOSE               暴露端口
```

### Podman 加速器 /etc/containers/registries.conf
```
cp registries.conf registries.conf_bak
cat registries.conf
// /etc/containers/registries.conf
unqualified-search-registries = ["docker.io", 'k8s.gcr.io']
[[registry]]
prefix = "docker.io"
location = "docker.mirrors.ustc.edu.cn"

[[registry.mirror]]
prefix = "docker.io"
location = "hub-mirror.c.163.com"

[[registry]]
prefix = "k8s.gcr.io"
location = "gcr.azk8s.cn/google_containers"
```

### 开机自启 podman
sudo systemctl start podman


### 别名
alias docker = 'podman'