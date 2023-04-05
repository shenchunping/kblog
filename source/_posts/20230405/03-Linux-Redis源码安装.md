---
title: 03-Linux-Redis源码安装
toc: true
date: 2023-04-05 14:54:38
tags:
  - Linux
  - Redis
categories:
  - Linux
---

# Redis 源码安装
```shell 
mkdir install-program
cd install-program
wget https://download.redis.io/releases/redis-6.2.11.tar.gz
tar -zxvf redis-6.2.11.tar.gz
cd redis-6.2.11/
make install
```

* 看到如下提示则表示安装成功
```shell
Hint: It's a good idea to run 'make test' ;)

    INSTALL redis-server
    INSTALL redis-benchmark
    INSTALL redis-cli

```

* 默认安装目录在 `/usr/local/bin`
* 如果安装需要指定目录，执行 `make PREFIX=/usr/local/redis install`
* 复制默认的配置文件到安装目录 `cp redis.conf /usr/local/redis/`

## 修改配置文件

```shell
cd /usr/local/redis

vim redis.conf
```
### 配置外网访问（云服务器请开启网络策略）

* 在vim查看模式输入 `/bind` 快速定位到修改位置
* 找到 `bind 127.0.0.1 -::1` 修改为 `bind 0.0.0.0` 如果前面有#号请去掉

### 配置密码

* 找到 `# requirepass foobared` 修改为 `requirepass 123456` 去掉前面的#号
* 上面的`123456`就是密码，替换成你的密码就可以

## 验证配置

```shell 
cd /usr/local/redis/bin
./redis-server ../redis.conf

```

## 开机启动配置
### 创建配置文件
```shell
vi /etc/systemd/system/redis.service
```

### 配置文件内容
* 键盘点`i` 然后粘贴下面的内容
```shell
[Unit]
#Description:描述服务
Description=Redis
#After:描述服务类别 
After=network.target

#服务运行参数的设置 
[Service]
#Type=forking是后台运行的形式 
Type=forking
#ExecStart为服务的具体运行命令，路径必须是绝对路径 
ExecStart=/usr/local/redis/bin/redis-server /usr/local/redis/redis.conf
#ExecReload为重启命令 ，路径必须是绝对路径 
ExecReload=/usr/local/redis/bin/redis-server -s reload
#ExecStop为停止命令 ，路径必须是绝对路径 
ExecStop=/usr/local/redis/bin/redis-server -s stop
#PrivateTmp=True表示给服务分配独立的临时空间 
PrivateTmp=true

#运行级别下服务安装的相关设置，可设置为多用户，即系统运行级别为3
[Install]
WantedBy=multi-user.target

```


* 执行开机启动命令 `systemctl enable redis.service`
* 执行手动启动命令 `systemctl start redis` 或者 `service redis start`
## 如果出现错误
### 启动超时错误
```shell 
Job for redis.service failed because a timeout was exceeded.
```
* 修改配置文件，注释掉 `Type=forking`
* 执行命令 `systemctl daemon-reload` 然后再次启动服务

