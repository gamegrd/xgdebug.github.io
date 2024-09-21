

---
layout:     post
title:      "修复 Redmi pro 15（I7 12）在 Arch Linux 下亮度突然变 0 的问题"
subtitle:   "pytorch on Android 11"
date:       2022-05-05 12:00:00
author:     "xgDebug"
catalog: false
header-style: text
tags:
  - Linux
  - Arch
  - Manjaro
---


我的  Redmi pro 15 休眠/睡眠/插电/断电/开机后可能亮度降为 0。解决办法：启动时使用以下内核参数。

````
acpi_backlight=vendor
````

如果你用 GRUB，就修改 /etc/default/grub，在 GRUB_CMDLINE_LINUX_DEFAULT 加上内核参数，如果有多个参数就以空格分开。
````
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=5 acpi_backlight=vendor"
````
然后刷新配置文件：

````
sudo grub-mkconfig -o /boot/grub/grub.cfg
````
