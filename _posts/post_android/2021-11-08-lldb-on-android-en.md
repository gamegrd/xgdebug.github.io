---
layout:     post
title:      "Debugging native applications with LLDV on Android 11"
subtitle:   "LLDB on Android 11"
date:       2021-11-08 12:00:00
author:     "xgDebug"
catalog: false
header-style: text
tags:
  - LLDB
  - ANDROID
---


## Mobile

## PUSH debug server to mobile
````shell
adb push lldb-server /data/local/tmp  
chmod 755 /data/local/tmp/lldb-server  
````

## Start the debugger service  
````shell
/data/local/tmp/lldb-server platform --listen "*:8888" --server
````
---------------------------
## Computer side
## Port forwarding
````shell
adb forward tcp:8888 tcp:8888
````
## Start LLDB
````shell
. \lldb.exe
````
## View supported platforms
````shell
platform list
````
## Select ANDROID platform
````shell
platform select remote-android
````
## Connect to the phone Phone serial number: **9643e0ec0604** To change to the current debugging phone, use adb devices to check the serial number
````shell
platform connect connect://9643e0ec0604:8888
````
## View the currently running process
````shell
platform process list
````
## Attach to
````shell
attach 9053
````

## Breakpoint
````shell
b send
````
## Run up
````shell
c
````
## View the list of threads
````shell
thread list
````
## View the call stack
````shell
bt
````