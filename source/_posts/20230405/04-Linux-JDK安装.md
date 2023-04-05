---
title: 04-Linux-JDK安装
toc: true
date: 2023-04-05 15:00:39
tags:
  - Linux
  - JDK
categories:
  - Linux
---

* 下载地址： [https://www.oracle.com/java/technologies/downloads/#java8](https://www.oracle.com/java/technologies/downloads/#java8)
* 这里下载的是 `jdk-8u361-linux-x64.rpm`
* 安装命令 `rpm -ivh jdk-8u361-linux-x64.rpm`
* 现在可以执行Java命令，查看安装版本 `java -version`
* 默认安装到 `/usr/java/jdk1.8.0_361-amd64` 目录
* 环境变量配置 `vim /etc/profile` 添加下面的配置，注意修改到自己的目录

```shell 
export JAVA_HOME=/usr/java/jdk1.8.0_361-amd64
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

* 生效配置 `source /etc/profile`
* 验证是否支持JDK `java -version`

