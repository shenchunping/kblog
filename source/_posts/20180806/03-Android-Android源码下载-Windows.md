---
title: Android源码下载-Windows
toc: true
date: 2018-08-06
tags:
  - Android
categories:
  - Android
---



# 安装Python
 [官网地址](http://www.python.org/) 我下载的是3.6.3的版本

# 安装GIT
 [官网地址](https://git-scm.com/) 下载最新版本即可


# 克隆主仓库，查看源码版本分支
* 找一个容量大的硬盘分区，至少有120G可用空间，克隆仓库。假如你要编译源代码的话，需要更大的空间准备160G以上吧。
```
C:\Users\shenchunping>cd E:\

C:\Users\shenchunping>E:

E:\>mkdir android

E:\>cd android

E:\android>git clone https://aosp.tuna.tsinghua.edu.cn/platform/manifest.git

```

> https://aosp.tuna.tsinghua.edu.cn/platform/manifest.git 是国内镜像地址，如果不能下载可以翻墙直接通过google官方下载，直接将地址替换为  https://android.googlesource.com/platform/manifest.git

执行完成之后将在android文件夹下生成manifest文件夹，该文件夹下还没有代码。
* 查看版本分支
```
E:\android>cd manifest

E:\android\manifest>git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/adt_23.0.3
  remotes/origin/afw-test-harness-1.5
  remotes/origin/afw-test-harness-2.1
  remotes/origin/afw-test-harness-marshmallow-dev
  remotes/origin/afw-test-harness-nougat-dev
  remotes/origin/android-1.6_r1
  remotes/origin/android-1.6_r1.1
  remotes/origin/android-1.6_r1.2
  remotes/origin/android-1.6_r1.3
  remotes/origin/android-1.6_r1.4
  remotes/origin/android-1.6_r1.5
  remotes/origin/android-1.6_r2
  remotes/origin/android-2.0.1_r1
  remotes/origin/android-2.0_r1
  remotes/origin/android-2.1_r1
  remotes/origin/android-2.1_r2
  remotes/origin/android-2.1_r2.1p
  remotes/origin/android-2.1_r2.1p2
  remotes/origin/android-2.1_r2.1s
  remotes/origin/android-2.2.1_r1
  remotes/origin/android-2.2.1_r2
  remotes/origin/android-2.2.2_r1
...略
```
最后一个“/”后面既是版本分支名称，下载我们选择一个分支下载

* 下载前我们注意观察manifest文件夹中的default.xml文件的default标签，大概在第六行
```
 <default revision="master"
           remote="aosp"
           sync-j="4" />
```
* 切换到最新的版本分支,你也可以选择你想要的版本。
```
E:\android\manifest>git checkout android-8.1.0_r2
Note: checking out 'android-8.1.0_r2'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 85739ae... Manifest for Android 8.1.0 Release 2 (OPM2.171019.012)

E:\android\manifest>
```

* 再次查看default.xml文件的default标签
```
  <default revision="refs/tags/android-8.1.0_r2"
           remote="aosp"
           sync-j="4" />
```
此时你已经选择好你想要下载的源码版本了。就来准备开始下载吧。


# 编辑Python下载脚本
* 创建一个文本文档，然后编辑如下代码，保存。
```
import xml.dom.minidom
import os
from subprocess import call

# downloaded source path
#源码根目录，android-8.1.0_r2可以自定义。
rootdir = "E:/android/android-8.1.0_r2"

# git program path
#GIT 可执行文件路径
git = "D:/Program Files/Git/bin/git.exe"

#将要解析的文件
dom = xml.dom.minidom.parse("E:/android/manifest/default.xml")
root = dom.documentElement

#GIT命令前缀
prefix = git + " clone https://aosp.tuna.tsinghua.edu.cn/"
#GIT命令后缀
suffix = ".git"
#创建根目录
if not os.path.exists(rootdir):
    os.mkdir(rootdir)
#遍历defualt.xml，执行Git命令克隆源码。
for node in root.getElementsByTagName("project"):
    os.chdir(rootdir)
    d = node.getAttribute("path")
    last = d.rfind("/")
    if last != -1:
        d = rootdir + "/" + d[:last]
        if not os.path.exists(d):
            os.makedirs(d)
        os.chdir(d)
    cmd = prefix + node.getAttribute("name") + suffix
    call(cmd)
```

# 执行Python 开始下载源码。


* 打开Python IDLE 
![TIM截图20180102191300.png](./20180806-03-Android源码下载-Windows/2093886-2a293e366bdcba76.webp)

* 打开刚刚编辑的代码文档
![TIM截图20180102192032.png](./20180806-03-Android源码下载-Windows/2093886-dcbfb890c573a27f.webp)

![TIM截图20180102192255.png](./20180806-03-Android源码下载-Windows/2093886-a856b025d87fedac.webp)

* 执行代码

![TIM截图20180102192255.png](./20180806-03-Android源码下载-Windows/2093886-9aee698760fe6da6.webp)

此时将看到命令窗口在不断的下载文件。就算大功告成，等待下载结束即可。


