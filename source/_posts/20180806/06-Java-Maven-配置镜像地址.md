---
title: Maven-配置镜像地址
toc: true
date: 2018-08-06
tags:
  - Maven
  - Java
categories:
  - Java
---

# 创建settings.xml文件

```shell
// Windows路径:

C:\Users\用户名\.m2\settings.xml

// Linux or Mac

~/.m2/settings.xml

```

# 添加文件内容

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">

    <mirrors>
        <!-- 阿里云仓库 -->
        <mirror>
            <id>alimaven</id>
            <mirrorOf>central</mirrorOf>
            <name>aliyun maven</name>
            <url>http://maven.aliyun.com/nexus/content/repositories/central/</url>
        </mirror>

        <!-- 中央仓库1 -->
        <mirror>
            <id>repo1</id>
            <mirrorOf>central</mirrorOf>
            <name>Human Readable Name for this Mirror.</name>
            <url>http://repo1.maven.org/maven2/</url>
        </mirror>

        <!-- 中央仓库2 -->
        <mirror>
            <id>repo2</id>
            <mirrorOf>central</mirrorOf>
            <name>Human Readable Name for this Mirror.</name>
            <url>http://repo2.maven.org/maven2/</url>
        </mirror>
    </mirrors>
    <servers>
        <!-- 私库配置 -->
        <server>
            <id>ptf-rdc-releases</id>
            <username>[replace username]</username>
            <password>[replace pwd]</password>
        </server>
        <server>
            <id>ptf-rdc-snapshots</id>
            <username>[replace username]</username>
            <password>[replace pwd]</password>
        </server>
    </servers>
</settings>
```

# 项目中加载私库密码
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    
    <!-- ... -->
    <!-- 加载依赖 -->
    <repositories>
        <!-- 稳定仓库 -->
        <repository>
            <id>ptf-rdc-releases</id>
            <url>https://packages.aliyun.com/maven/repository/2112582-release-lzcGxm/</url>
            <releases>
                <enabled>true</enabled>
            </releases>
            <snapshots>
                <enabled>false</enabled>
            </snapshots>
        </repository>
        <!-- 迭代仓库 -->
        <repository>
            <id>ptf-rdc-snapshots</id>
            <url>https://packages.aliyun.com/maven/repository/2112582-snapshot-FXoe3y/</url>
            <releases>
                <enabled>false</enabled>
            </releases>
            <snapshots>
                <enabled>true</enabled>
            </snapshots>
        </repository>
    </repositories>
    <!-- 发布依赖 -->
    <distributionManagement>
        <!-- 稳定仓库 -->
        <repository>
            <id>ptf-rdc-releases</id>
            <name>Release Repository</name>
            <url>https://packages.aliyun.com/maven/repository/2112582-release-lzcGxm/</url>
            <uniqueVersion>true</uniqueVersion>
            <layout>default</layout>
        </repository>
        <!-- 迭代仓库 -->
        <snapshotRepository>
            <id>ptf-rdc-snapshots</id>
            <name>Snapshot Repository</name>
            <url>https://packages.aliyun.com/maven/repository/2112582-snapshot-FXoe3y/</url>
            <uniqueVersion>false</uniqueVersion>
            <layout>default</layout>
        </snapshotRepository>
    </distributionManagement>
</project>

```

