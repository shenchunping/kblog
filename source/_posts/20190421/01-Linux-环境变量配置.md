---
title: 环境变量配置
toc: true
date: 2019-04-21 16:21:01
tags:
  - Linux
  - Mac
categories:
  - Linux
---

# Android
```shell
vim .bash_profile
# 或者
vim .profile

# 然后输入以下内容
export ANDROID_HOME=/Users/kuper/sowftware/android-sdk-macosx
export PATH=${PATH}:${ANDROID_HOME}/platform-tools
export PATH=${PATH}:${ANDROID_HOME}/tools
export PATH=${PATH}:${ANDROID_HOME}/build-tools/29.0.2

# 保存后，生效文件
source .bash_profile


```


