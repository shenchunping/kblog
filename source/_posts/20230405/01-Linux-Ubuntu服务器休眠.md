---
title: 01-Linux-Ubuntu服务器休眠
toc: true
date: 2023-04-05 14:26:13
tags:
  - Linux
  - Ubuntu
  - 休眠  
categories:
  - Linux
---


# 禁用
```shell
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```
# 启用
```shell
sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

