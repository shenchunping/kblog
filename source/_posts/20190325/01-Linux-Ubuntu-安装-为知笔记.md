---
title: Ubuntu 安装'为知笔记'
toc: true
date: 2019-03-Android-Android源码下载-Windows-25 16:26:44
tags:
  - Linux
  - Ubuntu
categories:
  - Linux
---


# 安装
安装具体步骤可以参考[官方文档](http://www.wiz.cn/compile-client.html),按文档操作即可完成安装.


# 无法使用搜狗拼音
```shell 
# 安装fcitx-libs-dev
sudo apt-get install fcitx-libs-dev

# 设置qmake的环境变量 
export PATH="/[Qt5.7_main_path]/5.7/gcc_64/bin":$PATH

# 下载fcitx-qt5源码,安装
	 
git clone https://github.com/fcitx/fcitx-qt5.git
cd fcitx-qt5
cmake .
make 
sudo make install
Could NOT find XKBCommon_XKBCommon
	 
wget http://xkbcommon.org/download/libxkbcommon-0.5.0.tar.xz
tar xf libxkbcommon-0.5.0.tar.xz 
./configure —prefix=/usr —libdir=/usr/lib/x86_64-linux-gnu —disable-x11 
make 
sudo make install
​
```
