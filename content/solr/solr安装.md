+++
title= "Solr安装"
date= "2022-06-03T14:17:31+08:00"
tags = []
featured_image = ""
description = ""
+++

### 启动

``` bash
solr start -m 3g
./solr start -p 8983 -force
```

### 关闭

``` bash
solr stop -all
```

### 创建项目

``` bash
solr create -c product
```

### 删除所有

``` xml
<delete><query>*:*</query></delete>
<commit/>
```

### 全量更新

<http://localhost:8024/solr/yx_products/dataimport?command=full-import&entity=yx_products&clean=false&commit=true>

### 增量更新

<http://localhost:8024/solr/yx_products/dataimport?command=delta-import&entity=yx_products&clean=true&commit=true>

###### **配置解释**

solr/yx_products： yx_products项目名称
entity：solr-data-config.xml里entity标签里的name值
command：全量 full-import  增量 delta-import
clean：数据清空

### solr对mysql中tinyint字段的处理方法

``` mysql
convert(danger,SIGNED) as danger
```



