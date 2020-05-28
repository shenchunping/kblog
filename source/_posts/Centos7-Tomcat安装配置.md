---
title: Centos7-Tomcat安装配置
toc: true
date: 2018-08-06
tags:
  - Linux
  - CentOS
  - Tomcat
categories:
  - 软件开发
  - 系统与环境
---



# Java环境安装（略）
# 下载安装Tomcat
``` shell
//进入opt目录
cd /opt

//下载
wget http://mirrors.shu.edu.cn/apache/tomcat/tomcat-8/v8.5.27/bin/apache-tomcat-8.5.27.zip

//解压
unzip apache-tomcat-8.5.27.zip

//修改文件夹名称
mv apache-tomcat-8.5.27 tomcat8

//手动启动tomcat
./tomcat8/bin/startup.sh

//可以在浏览器输入localhost:8080测试
//关闭tomcat
./tomcat8/bin/shutdown.sh
```

# 配置tomcat系统服务,及自启动。

## Linux配置

* 创建服务文件
``` shell
cp /tomcat/path/catalina.sh /etc/init.d/
cd /etc/init.d/
mv catalina.sh tomcat
```

* 添加服务文件内容

``` shell
vim tomcat 

## 在文件开头添加如下内容
CATALINA_HOME=/tomcat/path
JAVA_HOME=/jdk/home

```


* 服务开机启动

``` shell
chkconfig --add tomcat 
```

