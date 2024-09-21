---
layout:     post
title:      "在Android 11 上使用 LLDV 调试原生程序"
subtitle:   "LLDB on Android 11"
date:       2021-11-08 12:00:00
author:     "xgDebug"
catalog: false
header-style: text
tags:
  - LLDB
  - ANDROID
---

# 手机端

## PUSH调试服务器到手机
````shell
adb push lldb-server /data/local/tmp  
chmod 755 /data/local/tmp/lldb-server  
````

## 启动调试器服务  
````shell
/data/local/tmp/lldb-server platform --listen "*:8888" --server
````
---------------------------
# 电脑端
## 端口转发
````shell
adb forward tcp:8888 tcp:8888
````
## 启动LLDB
````shell
.\lldb.exe
````
## 查看支持平台
````shell
platform list
````
## 选ANDROID平台
````shell
platform select remote-android
````
## 连接到手机 手机序列号: **9643e0ec0604** 要换成当前调试的手机,使用 adb devices 查看序列号
````shell
platform connect connect://9643e0ec0604:8888
````
## 查看当前正在运行的进程
````shell
platform process list
````
## 附加上去
````shell
attach 9053
````

## 下断点
````shell
b send
````
## 跑起来
````shell
c
````
## 查看线程列表
````shell
thread list
````
## 查看调用栈
````shell
bt
````