---
layout: post
title:  "Lessons Learned Working with High Resolution Color & Depth Images in ROS"
author: Alperen
date:   2022-09-21
categories:
  - Software
  - Robotics
  - Computer Vision
---

If you are working with images in ROS, the recommended way to transport images in ROS is to use [image_transport](http://wiki.ros.org/image_transport) package. It allows image compressions, streaming with different video codes that helps a lot when you have a limited bandwidth on the robot. There are various [image_transport_plugins](http://wiki.ros.org/image_transport_plugins). The most common ones that are used by 3D cameras like **OAK-D**, **Realsense** or **Kinect** are:
* raw
* [compressed](http://wiki.ros.org/compressed_image_transport): png/jpg compression of the raw image for faster transport
* [compressedDepth](http://wiki.ros.org/compressed_depth_image_transport): png/jpg compression of raw depth image for faster transport
* [theora](http://wiki.ros.org/theora_image_transport): uses **Theora** codec suitable for live video feeds
...


Image transport works with a base topic, let's say your camera is publishing raw depth data to topic ```/stereo/image```. This means 
* raw data (base topic) --> ```/stereo/image``` 
* compressed --> ```/stereo/image/compressed```
* compressedDepth --> ```/stereo/image/compressedDepth```
* theora --> ```/stereo/image/theora```

If you are working with offline data, I highly suggest to use **compressed** or **compressedDepth** version of topics to record **rosbags** then republish a raw data later using the compressed version. For instance, let's say you recorded ```/stereo/image/compressedDepth``` and you want to use raw version ```/stereo/image```. Then, you can use **image transport republish**:
```
    <node pkg="image_transport" type="republish" name="republish_depth" args="compressedDepth in:=/stereo/image raw out:=/stereo/image"/>
```

**IMPORTANT NOTE:** If you happen to use compressed topics, the default configuration of image_transport might result in **low fps** values. To solve that, before recording your data, do NOT forget to change compression level using parameters ```<base_topic>/compressed/png_level```. By default, it is set to 9 meaning max compression to save space. You might need to decrease it. For more information, check parameters section of [compressedDepth](http://wiki.ros.org/compressed_depth_image_transport) and [compressed](http://wiki.ros.org/compressed_image_transport) plugins.
