---
title: 05-Linux-Mysql安装
toc: true
date: 2023-04-05 15:06:39
comments: true
tags:
  - Linux
  - MySql
categories:
  - Linux
---

* 下载地址 [https://dev.mysql.com/downloads/repo/yum/](https://dev.mysql.com/downloads/repo/yum/)
* 这里下载的是： https://repo.mysql.com//mysql80-community-release-el7-7.noarch.rpm
* 安装Mysql安装源 `rpm -ivh mysql80-community-release-el7-7.noarch.rpm`
* 更新安装源 `yum update -y`
* 安装Mysql `yum install mysql-community-server -y`
* 开机启动 `systemctl enable mysqld`
* 启动Mysql `systemctl start mysqld`
* 查看初始密码 `cat /var/log/mysqld.log | grep password` 或者 `grep "A temporary password" /var/log/mysqld.log`
* 登录Mysql `mysql -uroot -p` 输入密码
* 修改root密码 `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '你的密码';`
* 刷新权限 `flush privileges;`
* 创建新用户 `create user 'user1'@'%' IDENTIFIED WITH mysql_native_password BY 'User@123';`
* 创建数据库 `create database db_name default character set utf8mb4 collate utf8mb4_unicode_ci`
* 授予数据库读写权限 `grant all privileges on db_name.* to 'user1'@'%' with grant option;`
* 授予数据库增删改查权限 `grant SELECT,INSERT,UPDATE,DELETE on db_name.* to 'user1';`
* 授予所有数据库权限 `grant ALL on *.* to '用户名'@'主机名';`
* 撤销授权 `revoke 权限列表 on 数据库名.表名 from '用户名'@'主机名';`
* 查看授权 `show grants for '用户名'@‘主机名’;`

  ```shell 
      systemctl start mysqld		#启动mysql服务
      systemctl status mysqld		#查看mysql服务状态
      systemctl stop mysqld		#停止mysql服务
  ```

* 全文搜索配置
    ``` shell
    shellinnodb_ft_min_token_size=2
    ft_min_word_len=2
    ngram_token_size=2
    ```
