---
title: APK 反编译-基础篇
toc: true
date: 2019-04-21 16:33:21
tags:
  - Android
categories:
  - 软件开发
  - 程序语言
  - Android
---



# Dex2jar 

下载地址： https://sourceforge.net/projects/dex2jar/files/

功能：dex转jar

操作说明：

1，将要反编译的APK后缀名改为.rar或者 .zip，并解压，得到其中的classes.dex文件（它就是java文件编译再通过dx工具打包而成的）

2，d2j-dex2jar classes.dex
反编译classes.dex得到classes-dex2jar.jar文件之后，就可以使用【jd-gui】工具将class文件反编译成java源代码了

# Apktool
下载地址：https://bitbucket.org/iBotPeaches/apktool/downloads/

功能：反编译资源文件

操作说明：

java -jar apktool_2.0.1.jar d -f E:\AndroidDevelopTool\Android反编译工具包\测试apk\MMTS-release-1.0.2.apk -o MMTS

这个命令是启动apktool_2.0.1.jar将位于【E:\AndroidDevelopTool\Android反编译工具包\测试apk\】目录下的"MMTS-release-1.0.2.apk"这个apk反编译，然后将反编译生成的文件存放到当前目录（apktool_2.0.1.jar所在的目录，也就是"E:\AndroidDevelopTool\Android反编译工具包"目录）下的一个【MMTS】文件夹中。这个文件夹的名字是可以随便取的，喜欢叫啥都行。

