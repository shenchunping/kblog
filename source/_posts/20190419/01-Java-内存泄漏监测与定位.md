---
title: Java 内存泄漏监测与定位
toc: true
date: 2019-04-19 14:59:58
tags:
  - Java
  - 内存
  - JVM
categories:
  - Java
  
---


# 使用到的命令
jps jstat jmap 都是jdk自带的命令，

# 查看java进程
```shell
    [sz-java@test bin]$ ./jps -l
    19715 fts-1.2.0.war
    1220 sun.tools.jps.Jps
    11462 org.apache.catalina.startup.Bootstrap
    16904 cams-1.0.0.war
    4458 ems-1.0.war
    5390 ems-admin-1.0.war
    30719 org.apache.catalina.startup.Bootstrap
    1023 org.apache.catalina.startup.Bootstrap
```


# 查看GC

```shell
[sz-java@test bin]$ ./jstat -gcutil 19715 1000
  S0     S1     E      O      M     CCS    YGC     YGCT    FGC    FGCT     GCT   
 51.46   0.00  57.92  83.34  98.05  97.00    534    9.024    15    9.628   18.652
 51.46   0.00  57.92  83.34  98.05  97.00    534    9.024    15    9.628   18.652
 51.46   0.00  57.92  83.34  98.05  97.00    534    9.024    15    9.628   18.652
 51.46   0.00  57.92  83.34  98.05  97.00    534    9.024    15    9.628   18.652
 51.46   0.00  57.92  83.34  98.05  97.00    534    9.024    15    9.628   18.652
 51.46   0.00  57.93  83.34  98.05  97.00    534    9.024    15    9.628   18.652
 ```

19715 是进程编号
1000 是1000毫秒




# 查看堆信息
``` shell
jmap -histo:live 19715  
# 或者
jcmd 26964 GC.class_histogram | more
```

# 堆栈信息存储到文件
```shell
jcmd 26964 GC.heap_dump /home/ciadmin/pos-gateway-cloud/heap_dump.hprof
# 或者
jmap -dump:live,file=/home/ciadmin/pos-gateway-cloud/heap_dump2.hprof 26964
```

# 分析工具
## jhat 命令

先执行命令
```shell
jhat heap_dump.hprof
```

然后打开网页地址
http://localhost:7000/ 可以看到分析结果

## Eclipse Memory Analyzer 图形工具

* 下载Eclipse Memory Analyzer
* 安装好后，打开保存的堆栈信息文件，可看到分析结果


