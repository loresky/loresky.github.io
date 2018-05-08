---
title: maven配置
date: 2017-06-26 08:23:45
---

## 本地仓库的配置
```xml
 <localRepository>/opt/maven/repo</localRepository>
 ```
 
## 国内maven repository
### **在</mirrors>前添加**
```xml
<mirror>  
        <id>nexus-aliyun</id>  
        <mirrorOf>*</mirrorOf>  
        <name>Nexus aliyun</name>  
        <url>http://maven.aliyun.com/nexus/content/groups/public</url>  
</mirror>  
```


打包不测试idea-->maven-->package-->Command line:    clean package -DskipTests
