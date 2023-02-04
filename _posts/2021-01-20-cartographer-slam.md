---
layout: post
title:  "ROS Cartographer SLAM Installation Guide & Tutorials"
author: Alperen
date:   2021-01-20
image: /images/carto-slam/0.jpg
categories:
  - Software
  - Robotics
---

In my experience, cartographer slam gives the best mapping result among the common ROS SLAM algorithms. Below, you can find installation guide and tutorials regarding Cartographer SLAM. 

Tested on: 
* Ubuntu 16.04 with ROS Kinetic


## Installation
[Official resource](https://google-cartographer-ros.readthedocs.io/en/latest/compilation.html#building-installation)

* Go to your home directory
```
$ cd ~
```
* Create a new catkin_ws to install cartographer_ros
```
$ mkdir cartog_ws
```
* Install **rosdep**, **wstool** and **rosdep**. Also install ninja to make build process faster
```
$ sudo apt-get update
$ sudo apt-get install -y python-wstool python-rosdep ninja-build
```
* Now install cartographer_ros
```
$ wstool init src
$ wstool merge -t src https://raw.githubusercontent.com/googlecartographer/cartographer_ros/master/cartographer_ros.rosinstall
$ wstool update -t src
$ ./src/cartographer/scripts/install_proto3.sh
$ rosdep update
$ rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
$ catkin_make_isolated --install --use-ninja
```


## Tutorials

### Tutorial 1: Run Cartographer ROS with a Recorded Bag File
[Official source](https://google-cartographer-ros.readthedocs.io/en/latest/your_bag.html)

**WARNING:** Don't forget to source bash file in cartog_ws to run nodes related to cartographer_ros.
* 
```
$ source cartog_ws/install_isolated/setup.bash
```

* First, check whether recorded bag file is usable by cartographer or not.
```
$ cartographer_rosbag_validate -bag_filename your_bagfile.bag
```

If you don't see any error, then you can go further. If you see error, try to fix it. Otherwise, keep the error in mind and proceed further. However, if you can not obtain a map, download a bag file from [this link](https://google-cartographer-ros.readthedocs.io/en/latest/demos.html) and follow the steps there. Then try to arrange your bag file accordingly!

* As an example, you can try to launch my launch file oko_cartographer.launch. It calls [kamu_robotu.lua](https://github.com/samialperen/oko_slam/blob/master/ros_ws/src/kamu_robotu/kamu_robotu_launch/params/kamu_robotu.lua) file which you need to copy to /home/user/cartog_ws/install_isolated/share/cartographer_ros/configuration_files directory. 
```
$ cp oko_slam/ros_ws/src/kamu_robotu/kamu_robotu_launch/params/kamu_robotu.lua /home/$USER/cartog_ws/install_isolated/share/cartographer_ros/configuration_files
$ roslaunch kamu_robotu_launch oko_slam.launch slam_type:=cartographer
```

* Lastly play your bag file with clock
```
$ cd oko_slam/ros_ws/bagfiles/real_data
$ rosbag play --clock realmap3objects-linearvel30-lidar-4hz2.bag
```

If everything is okay you should be able to see the rviz output like below:
![Cartographer Rviz Output](/images/carto-slam/1.png)
<center> Cartographer Rviz Output </center>

**NOTE:** The example bag file starts to publish data after some time. Therefore, if you see **no mapping received** warning in Rviz, please wait some time. However, if you can not see anything at the end even rosbag comes to end, then this means there is a problem about either installation or launch.

<center> 
  <script type='text/javascript' src='https://storage.ko-fi.com/cdn/widget/Widget_2.js'></script><script type='text/javascript' style="text-align:center">kofiwidget2.init('Buy Me a Coffee', '#e08428', 'V7V3IDOGW');kofiwidget2.draw();</script> 
</center>