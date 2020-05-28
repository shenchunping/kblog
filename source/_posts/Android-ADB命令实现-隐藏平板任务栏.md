---
title: Android-ADB命令实现-隐藏平板任务栏
toc: true
date: 2018-08-06
tags:
  - Android
categories:
  - 软件开发
  - 程序语言
  - Android
---



**请先ROOT设备**

# 进入shell环境
```
adb shell
```
# 获取超级管理员权限
```
su 
```
> 注意平板提示同意即可

# 备份原始文件
```
cp /system/build.prop /system/build.prop.back
```

# 如果提示readonly错误
> 先挂载 /system目录可读写重试上一个命令
```
mount -o rw,remount /system
```

# 添加代码到文件
```
echo 'qemu.hw.mainkeys=1' >> /system/build.prop
```

# 查看文件是否添加成功
```
cat /system/build.prop
```

# 重启完成
```
reboot
```

