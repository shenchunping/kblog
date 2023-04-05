---
title: Centos7-开机启动网卡
date: 2018-08-06
toc: true
comments: 默认启动网卡
tags:
  - Linux
  - CentOS
categories:
  - Linux
---


# 步骤


1. 进入目录/etc/sysconfig/network-scripts/
2. 修改ifcfg-enxxxxxxxx 文件  (即你的网卡标识命名的配置文件)
3. 将ONBOOT=no改成yes


```
cd /etc/sysconfig/network-scripts/
vim ifcfg-enxxxxxxxx

//或者

vim /etc/sysconfig/network-scripts/ifcfg-enxxxxxxxx

```