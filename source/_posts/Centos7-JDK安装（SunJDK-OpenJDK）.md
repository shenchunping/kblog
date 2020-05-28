---
title: Centos7 JDK安装（SunJDK OpenJDK）
toc: true
date: 2018-08-06
tags:
  - Linux
  - CentOS
  - JDK
categories:
  - 软件开发
  - 系统与环境
---


# OpenJDK安装

# 安装
```
yum install java-1.7.0-openjdk
```
# 设置环境变量
```
//安装目录在/usr/lib/jvm/
vi /etc/profile

//添加一下内容
#set java environment
JAVA_HOME=/usr/lib/jvm/java-1.7.0-openjdk-1.7.0.75.x86_64
JRE_HOME=$JAVA_HOME/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```

# 生效修改的文件
```
source /etc/profile
```

# 测试
```
java -version
```
# SunJDK安装

# 创建安装目录
```
mkdir /usr/java
cd /usr/java
```

# 下载JDK
```
wget http://download.oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.tar.gz 
```

# 解压
```
tar -zxvf jdk-7u79-linux-x64.tar.gz
```

# 配置环境变量
```
vi /etc/profile

//添加内容
#set java environment
JAVA_HOME=/usr/java/jdk1.7.0_79
JRE_HOME=/usr/java/jdk1.7.0_79/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH

```

# 生效修改的文件
```
source /etc/profile
```

# 测试
```
java -version
```
