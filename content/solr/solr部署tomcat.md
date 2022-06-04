+++
title= "Solr部署tomcat"
date= "2022-06-03T14:18:57+08:00"
tags = []
featured_image = ""
description = ""
+++

### solr在tomcat上的部署

* solr\server\solr-webapp 复制到apache-tomcat\webapps目录下改名为solr
* 复制solr\server\lib下metrics的jar，到apache-tomcat\webapps\solr\libs
* 复制solr\server\resources下的log4j.properties，到apache-tomcat\webapps\solr\WEB-INF\classes
* 修改apache-tomcat\webapps\solr\WEB-INF下的web.xml，添加solrhome目录注释全安认证

``` xml
<env-entry>
    <env-entry-name>solr/home</env-entry-name>
    <env-entry-value>F:/solrhome</env-entry-value>
    <env-entry-type>java.lang.String</env-entry-type>
</env-entry>

  <!-- 注释掉<security-constraint>整个标签，这个标签负责安全认证，不注释会报403错误 -->
<!-- <security-constraint>
  </security-constraint> -->
```

#### 启动Tomcat后访问http://ip:port/solr/index.html

### java处理solr的特殊字符

``` java
ClientUtils.escapeQueryChars(keyword);
```