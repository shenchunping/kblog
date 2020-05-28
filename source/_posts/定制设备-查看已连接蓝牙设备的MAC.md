---
title: 定制设备-查看已连接蓝牙设备的MAC
date: 2018-08-06
toc: true
comments: 定制设备开发
categories:
  - 软件开发
  - 程序语言
  - Android
tags:
  - Android
  - 蓝牙
---


**开始之前,要Root设备，并先配对蓝牙模块**

# 使用到的命令
adb shell  --进入Android Shell命令环境
```
input keyevent 3  //--回到首页
input keyevent 4  // 返回上一页
```


# 查看配对信息

找到读卡器蓝牙MAC地址，依次执行下面三个命令

```
adb shell 
su 
cat /data/misc/bluedroid/bt_config.conf
```


*示例结果,试验中可能是json格式*

```
<Bluedroid>
    <N1 Tag="Local">
        <N1 Tag="Adapter">
            <N1 Tag="BluezMigrationDone" Type="int">1</N1>
            <N2 Tag="Address" Type="string">22:22:58:90:d9:a4</N2>
            <N3 Tag="LE_LOCAL_KEY_IR" Type="binary">5ba8bf27a463c9567c913117276b
2830</N3>
            <N4 Tag="LE_LOCAL_KEY_IRK" Type="binary">656ad1d26de62d43c628b77f16f
e8f86</N4>
            <N5 Tag="LE_LOCAL_KEY_DHK" Type="binary">a9990c91bb98626db3fe7f01d6f
2753f</N5>
            <N6 Tag="ScanMode" Type="int">1</N6>
            <N7 Tag="DiscoveryTimeout" Type="int">120</N7>
        </N1>
        <N2 Tag="AutoPairBlacklist">
            <N1 Tag="AddressBlacklist" Type="string">00:02:C7,00:16:FE,00:19:C1,
00:1B:FB,00:1E:3D,00:21:4F,00:23:06,00:24:33,00:A0:79,00:0E:6D,00:13:E0,00:21:E8
,00:60:57,00:0E:9F,00:12:1C,00:18:91,00:18:96,00:13:04,00:16:FD,00:22:A0,00:0B:4
C,00:60:6F,00:23:3D,00:C0:59,00:0A:30,00:1E:AE,00:1C:D7,00:80:F0,00:12:8A,00:09:
93,00:80:37,00:26:7E,00:26:e8</N1>
            <N2 Tag="ExactNameBlacklist" Type="string">Motorola IHF1000,i.TechBl
ueBAND,X5 Stereo v1.3,KML_CAN</N2>
            <N3 Tag="FixedPinZerosKeyboardBlacklist" Type="string">00:0F:F6</N3>

            <N4 Tag="PartialNameBlacklist" Type="string">BMW,Audi,Parrot,Car</N4
>
        </N2>
    </N1>
    <N2 Tag="Remote">
        <N1 Tag="68:3e:34:2b:0d:9b">
            <N1 Tag="Timestamp" Type="int">1482914768</N1>
            <N2 Tag="Name" Type="string">MEIZU PRO 5</N2>
            <N3 Tag="DevClass" Type="int">5898764</N3>
            <N4 Tag="DevType" Type="int">1</N4>
            <N5 Tag="AddrType" Type="int">0</N5>
        </N1>
        <N2 Tag="9c:f3:87:bd:3c:47">
            <N1 Tag="Timestamp" Type="int">1482914769</N1>
            <N2 Tag="Name" Type="string">APPLE-PC</N2>
            <N3 Tag="DevClass" Type="int">131340</N3>
            <N4 Tag="DevType" Type="int">1</N4>
            <N5 Tag="AddrType" Type="int">0</N5>
        </N2>
        <N3 Tag="1c:77:f6:37:f1:67">
            <N1 Tag="Timestamp" Type="int">1482914769</N1>
            <N2 Tag="Name" Type="string">OPPO R9tm</N2>
            <N3 Tag="DevClass" Type="int">5898764</N3>
            <N4 Tag="DevType" Type="int">1</N4>
            <N5 Tag="AddrType" Type="int">0</N5>
        </N3>
        <N4 Tag="20:14:00:44:54:12">
            <N1 Tag="Timestamp" Type="int">1488532736</N1>
            <N2 Tag="DevClass" Type="int">7936</N2>
            <N3 Tag="DevType" Type="int">1</N3>
            <N4 Tag="AddrType" Type="int">0</N4>
            <N5 Tag="Name" Type="string">iBuy_445412</N5>
            <N6 Tag="Manufacturer" Type="int">10</N6>
            <N7 Tag="LmpVer" Type="int">4</N7>
            <N8 Tag="LmpSubVer" Type="int">4192</N8>
            <N9 Tag="LinkKeyType" Type="int">0</N9>
            <N10 Tag="PinLength" Type="int">4</N10>
            <N11 Tag="LinkKey" Type="binary">58bdeab8a33b96a140842c08e507c3f6</N
11>
            <N12 Tag="Service" Type="string">00001101-0000-1000-8000-00805f9b34f
b </N12>
        </N4>
        <N5 Tag="ac:c1:ee:10:0a:84">
            <N1 Tag="Timestamp" Type="int">1488532738</N1>
            <N2 Tag="DevClass" Type="int">5898764</N2>
            <N3 Tag="DevType" Type="int">1</N3>
            <N4 Tag="AddrType" Type="int">0</N4>
            <N5 Tag="Name" Type="string">小米手机</N5>
            <N6 Tag="Manufacturer" Type="int">29</N6>
            <N7 Tag="LmpVer" Type="int">8</N7>
            <N8 Tag="LmpSubVer" Type="int">602</N8>
        </N5>
        <N6 Tag="22:bf:16:cf:a2:9b">
            <N1 Tag="Timestamp" Type="int">1488531622</N1>
            <N2 Tag="DevClass" Type="int">5898764</N2>
            <N3 Tag="DevType" Type="int">1</N3>
            <N4 Tag="AddrType" Type="int">0</N4>
            <N5 Tag="Name" Type="string">Samsung Galaxy S7</N5>
        </N6>
    </N2>
</Bluedroid>
```

*例如我链接的是“小米手机”那么我们找到的蓝牙mac就是“ac:c1:ee:10:0a:84”*


# 退出Su权限，以免误操作。
```
exit
```

---



**以下为实际项目使用,请看官忽略.**

# 示例
* 创建文件
```
touch /sdcard/blueToothAddress.txt
```
* 假如文件已经存在，或者你想重新执行一遍，请先删除文件。
```
rm -f /sdcard/blueToothAddress.txt
```
* 写入蓝牙MAC地址到文件中
```
echo ac:c1:ee:10:0a:84 > /sdcard/blueToothAddress.txt
```
*将mac地址换成你的mac地址*

* 查看写入文件信息是否成功
```
cat /sdcard/blueToothAddress.txt
```
*如果看到你刚刚写的mac地址，则表示成功。*
