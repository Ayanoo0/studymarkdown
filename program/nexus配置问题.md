# 

## 用户机器上配置settings.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" 
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
 
  <servers>
  
      <server>
          <id>nexus-snapshots</id>
          <username>chencan</username>
          <password>We5*&^%$#@!</password>
      </server>

  </servers>
  
  <mirrors>
  
      <mirror>
          <id>nexus</id>
          <name>internal nexus repository</name>
          <url>http://10.1.14.80:8081//nexus/content/groups/public/</url>
          <mirrorOf>central</mirrorOf>
      </mirror>
      
  </mirrors>
  
</settings>
```

## 配置maven项目的pom文件

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 2     xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
 3 
 4     <modelVersion>4.0.0</modelVersion>
 5     <groupId>my.work</groupId>
 6     <artifactId>newlife</artifactId>
 7     <version>0.0.1-SNAPSHOT</version>
 8     <packaging>war</packaging>
 9     <name />
10     <!-- 配置部署的远程仓库 -->
11     <distributionManagement>
12         <snapshotRepository>
13             <id>nexus-snapshots</id>
14             <name>nexus distribution snapshot repository</name>
15             <url>http://10.1.14.80:8081/nexus/content/repositories/snapshots/</url>
16         </snapshotRepository>
17     </distributionManagement>
18 </project>
```

