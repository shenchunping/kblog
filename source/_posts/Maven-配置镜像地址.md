---
title: Maven-配置镜像地址
toc: true
date: 2018-08-06
tags:
  - Maven
categories:
  - 软件开发
  - 环境配置
---

# 创建settings.xml文件

```
// Windows路径:

C:\Users\用户名\.m2\settings.xml

```

# 添加文件内容
```

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

</settings>

```




# 参考资料
> - []()
> - []()
