---
title: mongodb可视化
date: 2017-09-26 10:17:09
---

## mongo-express
**复制创建配置文件**
``` bash
cp config.default.js config.js
```

**配置Mongo数据库的连接信息：**
```
mongo = {
    db:       'db',
    host:     'localhost',
    password: 'pass',
    port:     27017,
    ssl:      false,
    url:      'mongodb://localhost:27017/db',
    username: 'admin',
  }
```

**配置Web服务的信息**
其中根据场景需求，可能需要把
``
host:             process.env.VCAP_APP_HOST                 || 'localhost'
``
修改为
``
host:             process.env.VCAP_APP_HOST                 || '0.0.0.0',
``

**修改登录网页所需要的用户名、密码，默认为admin和pass：**
``` 
basicAuth: {
    username: process.env.ME_CONFIG_BASICAUTH_USERNAME || 'admin',
    password: process.env.ME_CONFIG_BASICAUTH_PASSWORD || 'pass',
  }
```

**admin feature需要打开，才能够同时管理多个DB**
```
admin: process.env.ME_CONFIG_MONGODB_ENABLE_ADMIN ? process.env.ME_CONFIG_MONGODB_ENABLE_ADMIN.toLowerCase() === 'true' : false,
```

