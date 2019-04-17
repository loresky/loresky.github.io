+++
title= "docker库命令"
date= "2019-01-21T10:39:11+08:00"
tags = []
featured_image = ""
description = ""
+++


## nginx
```
docker run  -idt -p 80:80 -v /www:/usr/share/nginx/html:ro  -v /config/nginx.conf:/etc/nginx/nginx.conf:ro -d nginx
```

## mysql
```
 docker run  -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456  -v ~/mysql/conf:/etc/mysql/conf.d  -v ~/mysql/data:/var/lib/mysql -d mysql
```

## redis
```
docker run -d -p 6379:6379 -v ~/redis/data:/data -d redis:latest redis-server --appendonly yes --requirepass "123456"
```

## mongodb
```
docker run -itd  -p 27017:27017 -v /data/mongoDb/:/data/db -d mongo:latest
```

## mongo-express
```
docker run -it --rm \
	--name mongo-express \
	--link {id/name}mongo \
	-p 8088:8081 \
	-e ME_CONFIG_OPTIONS_EDITORTHEME="ambiance" \
	-e ME_CONFIG_BASICAUTH_USERNAME="admin" \
	-e ME_CONFIG_BASICAUTH_PASSWORD="pass" \
	mongo-express
```