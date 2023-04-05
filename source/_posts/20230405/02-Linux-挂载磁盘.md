---
title: 02-Linux-挂载磁盘
toc: true
date: 2023-04-05 14:44:35
tags:
  - Linux
  - 磁盘挂载
categories:
  - Linux    
---

# 依赖更新
```shell 
yum update -y 
```

# 挂载磁盘（无则忽略）
## 查看所有磁盘

* 执行命令 `fdisk -l`

```shell 
磁盘 /dev/vda：64.4 GB, 64424509440 字节，125829120 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：dos
磁盘标识符：0x000b770c

   设备 Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048   125829086    62913519+  83  Linux

磁盘 /dev/vdb：107.4 GB, 107374182400 字节，209715200 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节

```

> /dev/vda 已经挂载，/dev/vdb 未挂载

## 磁盘分区
* 执行命令 `fdisk /dev/vdb`
* 然后依次输入 `n 、p、 1、 回车、回车、wq`

## 磁盘格式化
* 执行命令 `mkfs.ext3 /dev/vdb1`

## 挂载新分区
* 临时挂载(重启后失效) `mount /dev/vdb1 /data`
* 永久挂载 `echo '/dev/vdb1 /data ext3 defaults 0 0' >>/etc/fstab`

## 查看挂载信息
* 查看磁盘信息 `fdisk -l`

```shell
磁盘 /dev/vda：64.4 GB, 64424509440 字节，125829120 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：dos
磁盘标识符：0x000b770c

   设备 Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048   125829086    62913519+  83  Linux

磁盘 /dev/vdb：107.4 GB, 107374182400 字节，209715200 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：dos
磁盘标识符：0x4e36872a

   设备 Boot      Start         End      Blocks   Id  System
/dev/vdb1            2048   209715199   104856576   83  Linux

```
> 磁盘都已挂载

* 查看磁盘空间 `df -h`

```shell
文件系统        容量  已用  可用 已用% 挂载点
devtmpfs        7.7G     0  7.7G    0% /dev
tmpfs           7.7G     0  7.7G    0% /dev/shm
tmpfs           7.7G  628K  7.7G    1% /run
tmpfs           7.7G     0  7.7G    0% /sys/fs/cgroup
/dev/vda1        59G  6.6G   50G   12% /
tmpfs           1.6G     0  1.6G    0% /run/user/0
/dev/vdb1        99G   60M   94G    1% /data
```
> 挂载成功



