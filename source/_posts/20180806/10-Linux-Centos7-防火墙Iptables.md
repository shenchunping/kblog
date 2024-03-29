---
title: Centos7-防火墙Iptables
toc: true
date: 2018-08-06
tags:
  - Linux
  - CentOS
categories:
  - Linux
---

# 命令行设置

* 简单操作
```
//关闭默认是防火墙Filerwall
systemctl stop firewalld.service

//禁用默认防火墙
systemctl disable firewalld.service 

//安装Iptables
yum install iptables-services

// 启动iptables 
service iptables start

//设置开机启动
systemctl enable iptables.service

//重启iptables
service iptables restart
```


## 基本设置

```
//查看iptables现有规则  
iptables -L -n  
//先允许所有,不然有可能会杯具  
iptables -P INPUT ACCEPT  
//清空所有默认规则  
iptables -F  
//清空所有自定义规则  
iptables -X  
//所有计数器归0  
iptables -Z  
//允许来自于lo接口的数据包(本地访问)  
iptables -A INPUT -i lo -j ACCEPT  
//开放22端口  
iptables -A INPUT -p tcp --dport 22 -j ACCEPT  
//开放21端口(FTP)  
iptables -A INPUT -p tcp --dport 21 -j ACCEPT  
//开放80端口(HTTP)  
iptables -A INPUT -p tcp --dport 80 -j ACCEPT  
//开放443端口(HTTPS)  
iptables -A INPUT -p tcp --dport 443 -j ACCEPT  
//允许ping  
iptables -A INPUT -p icmp --icmp-type 8 -j ACCEPT  
//允许接受本机请求之后的返回数据 RELATED,是为FTP设置的  
iptables -A INPUT -m state --state  RELATED,ESTABLISHED -j ACCEPT  
//其他入站一律丢弃  
iptables -P INPUT DROP  
//所有出站一律绿灯  
iptables -P OUTPUT ACCEPT  
//所有转发一律丢弃  
iptables -P FORWARD DROP  

//保存设置，一定不要忘记
service iptables save
```

## 其他设置

```
//如果要添加内网ip信任（接受其所有TCP请求）  
iptables -A INPUT -p tcp -s 45.96.174.68 -j ACCEPT  
//过滤所有非以上规则的请求  
iptables -P INPUT DROP  
//要封停一个IP，使用下面这条命令：  
iptables -I INPUT -s ***.***.***.*** -j DROP  
//要解封一个IP，使用下面这条命令:  
iptables -D INPUT -s ***.***.***.*** -j DROP 
```


# 手动编辑

```
vim /etc/sysconfig/iptables
```

```
# Generated by iptables-save v1.4.21 on Thu Jan 18 11:55:42 2018
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [8:824]
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 8080 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 8443 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 1521 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 3306 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 3389 -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
COMMIT
# Completed on Thu Jan 18 11:55:42 2018
```


