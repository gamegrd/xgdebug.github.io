---
title: 'Debugging native applications with LLDV on Android 11'
date: Fri, 11 Aug 2023 01:14:06 +0000
draft: false
tags: ['Android']
---

Mobile
------

PUSH debug server to mobile
---------------------------

```
adb push lldb-server /data/local/tmp  
chmod 755 /data/local/tmp/lldb-server 
```

Start the debugger service
--------------------------

```
/data/local/tmp/lldb-server platform --listen "*:8888" --server 
```

* * *

Computer side
-------------

Port forwarding
---------------

```
adb forward tcp:8888 tcp:8888 
```

Start LLDB
----------

```
. \lldb.exe 
```

View supported platforms
------------------------

```
platform list 
```

Select ANDROID platform
-----------------------

```
platform select remote-android 
```

Connect to the phone Phone serial number: **9643e0ec0604** To change to the current debugging phone, use adb devices to check the serial number
-----------------------------------------------------------------------------------------------------------------------------------------------

```
platform connect connect://9643e0ec0604:8888 
```

View the currently running process
----------------------------------

```
platform process list 
```

Attach to
---------

```
attach 9053 
```

Breakpoint
----------

```
b send 
```

Run up
------

```
c 
```

View the list of threads
------------------------

```
thread list 
```

View the call stack
-------------------

```
bt 
```