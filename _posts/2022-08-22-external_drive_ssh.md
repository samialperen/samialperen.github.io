---
layout: post
title:  "How to Transfer Files Between External Drive on Linux Terminal"
author: Alperen
date:   2022-08-22
categories:
  - Software
  - Robotics
---

Recently, I have been finding myself transfering a lot of files to external drive on Linux terminal. I personally did not have a chance to use any GUI since I have been using ssh to connect different machines and transfer data to external drive connected to these machines. If you happen to have the same problem, here are the simple steps:


```
# Connect via ssh to machine which has external drive connected

# Find out where your external drive is connected
$ lsblk
# that gives something like this 
 NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
├─sda1   8:1    0 925.5G  0 part /
├─sda2   8:2    0     1K  0 part 
└─sda5   8:5    0     6G  0 part [SWAP]

sdb      8:16   0   1.8T  0 disk 
└─sdb1   8:17   0   1.8T  0 part 

# In this case, my external drive is connected to /dev/sdb1

# Mount the device 
$ udisksctl mount --block-device /dev/sdb1
# It will give an output like this
==== AUTHENTICATING FOR org.freedesktop.udisks2.filesystem-mount-other-seat ===
Authentication is required to mount WDC WD30EZRX-00DC0B0 (/dev/sdb1)
Authenticating as: $USER,,, ($USER)
Password: **********  
==== AUTHENTICATION COMPLETE ===
Mounted /dev/sdb1 at /media/$USER/USB-exfat.

# Now you can go into /media/$USER/USB-exfat 
$ cd /media/$USER/USB-exfat

# You can copy from/to from this location (external drive) to the device you are connected via ssh
```

<center> 
  <script type='text/javascript' src='https://storage.ko-fi.com/cdn/widget/Widget_2.js'></script><script type='text/javascript' style="text-align:center">kofiwidget2.init('Buy Me a Coffee', '#e08428', 'V7V3IDOGW');kofiwidget2.draw();</script> 
</center>