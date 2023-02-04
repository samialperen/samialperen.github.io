---
layout: post
title:  "How to Upgrade CMake without Removing the Old Version"
author: Alperen
date:   2023-01-20
categories:
  - Software
  - Robotics
---

If you are **ROS** developer, then there might a time, you need to write a wrapper for a library but requires a higher version of **CMake** coming with ROS. In this situation, removing CMake with ```apt-get remove``` or ```apt purge``` will remove all the packages CMake depends which includes ROS packages. 

Instead, you need to install another CMake with preferred version and override the old version. Here are the steps: 

* 1-) Download the required [CMake](https://cmake.org/download/) version. (Try to download source file since they include Bootstrap and CMakeLists.txt)
```
$ wget https://github.com/Kitware/CMake/releases/download/v3.25.2/cmake-3.25.2.tar.gz
```

* 2-) Since you are already have an existing CMake, we can use system CMake to build the new CMake
```
$ Unzip the downloaded CMake file (name might differ depending on the version)
$ tar -xf cmake-3.25.2.tar.gz 
$ cd cmake-3.25.2/ 
$ cmake -DCMAKE_INSTALL_PREFIX=$HOME/cmake-install . 
$ make 
$ make install 
```
* 3-) If you do not have CMake installed your system, you can use Bootstrap. **Only follow this step if Step 2 does not work for you!**
	* Install bootstrap if it is not installed on your system
	```
        $ # I will use yarn, but feel free to use any other method you find online
        $ curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
        $ echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
        $ apt-get update && apt-get install -y yarn 
        $ yarn add bootstrap
	```
	* Install CMake with bootstrap
	```
        $ tar -xf cmake-3.25.2.tar.gz 
        $ cd cmake-3.25.2/ \
        $ ./bootstrap --prefix=$HOME/cmake-install 
        $ make 
        $ make install 
	```
* 4-) Now, it is time to update **CMake Paths** in bashrc so that by default we will use the upgraded CMake.
```
$ echo "PATH=$HOME/cmake-install/bin:$PATH" >> ~/.bashrc
$ echo "CMAKE_PREFIX_PATH=$HOME/cmake-install:$CMAKE_PREFIX_PATH" >> ~/.bashrc
```
* 5-) Congrats you are done. Do not forget to source bashrc before using CMake.
```
$ source ~/.bashrc
```

**NOTE:** If you want to use the old CMake, make sure that you removed ```$HOME/cmake-install``` from ```PATH``` as well as ```CMAKE_PREFIX_PATH```.

I hope this helps someone to save time :) 

<center> 
  <script type='text/javascript' src='https://storage.ko-fi.com/cdn/widget/Widget_2.js'></script><script type='text/javascript' style="text-align:center">kofiwidget2.init('Buy Me a Coffee', '#e08428', 'V7V3IDOGW');kofiwidget2.draw();</script> 
</center>