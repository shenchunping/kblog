---
title: Android源码下载-Centos7
toc: true
date: 2018-08-06
tags:
  - Android
categories:
  - 软件开发
  - 环境配置
---


# 下载 repo
```
$ mkdir ~/bin
$ PATH=~/bin:$PATH
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
```

* 编辑~/bin/repo文件，改为国内镜像
```
https://gerrit.googlesource.com/git-repo
改为
https://mirrors.tuna.tsinghua.edu.cn/git/git-repo
```

# 指定branch，下载代码
* 查看所有分支
```
cd .repo/manifests
git branch -a
```
* 同步代码
```
$ cd aosp
$ repo init -u https://aosp.tuna.tsinghua.edu.cn/platform/manifest -b android-6.0.1_r1
$ repo sync
```

#  编译
```
# source 环境
$ . build/envsetup.sh

# 选择编译项目
$ lunch 2

# 编译，可以使用-j选项设置并行编译的数量
$ make -j8
```



# 参考资料
> - []()
> - []()
