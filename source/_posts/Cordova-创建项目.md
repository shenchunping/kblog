---
title: Cordova 创建项目
toc: true
date: 2018-08-06
tags:
  - Cordova
categories:
  - 软件开发
  - 程序语言
---


# 下载最新Note.js安装

```shell
node -v  
npm -v
```
# 设置镜像服务器

```shell
npm config set registry http://registry.cnpmjs.org
```

# 开始安装

```shell
sudo npm install -g cordova
// sudo cnpm install -g cordova
```
# 测试是否安装成功

```shell
cordova -v
```

# 创建项目

```shell
cordova create hello com.example.hello HelloWorld
``` 


# 进入文件夹

```shell
cd hello
``` 

# 添加ISO平台

```shell
cordova platform add ios
``` 

# build项目

```shell
cordova build ios
``` 


# 启动ios模拟器

```shell
cordova emulate ios
``` 




# 参考资料
> - []()
> - []()
