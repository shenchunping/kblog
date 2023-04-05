---
title: key和pem生成HTTPS证书
toc: true
date: 2019-03-Android-Android源码下载-Windows-26 13:51:39
tags:
  - HTTPS
  - 证书
categories:
  - Linux
---

# MAC下直接命令生成.p12文件

```shell
openssl pkcs12 -export -inkey private.key -in full_chain.pem -name tomcat -out tomcat.p12
```

# 通过keytool生成.jks文件

``` shell 
keytool -importkeystore -srckeystore C:\tomcat.p12 -srcstoretype pkcs12 -destkeystore C:\tomcat.jks
```

