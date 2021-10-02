---
layout: project
title: "Gesture Recognition for Internet of Things (IoT) Application"
permalink: /projects/human-action-recognition-iot
image: /images/project-images/human-action-recognition-iot/block-diagram.png
---

# [Github Link for this project](https://github.com/samialperen/openni2_tracker_listener)

<img src="/images/project-images/human-action-recognition-iot/demo.gif" width="25%" height="25%">


In this project, gesture recognition was achieved by tracking user's skeleton with RGB-D data obtained through Asus Xtion Pro camera. The system was connected to main IoT server in the lab. As a proof of concept, recognized gestures of users were used to turn off or on the lamp connected to IoT network.
  

<img src="/images/project-images/human-action-recognition-iot/block-diagram.png" width="80%" height="80%">

 
Keywords about the project:
* Computer Vision
    * Human Detection
    * Skeleton Tracking
    * 3D Image
    * Gesture Recognition
    * Human Activity Recognition	
* Robot Operating System (ROS)
    * NITE2.2
    * OpenNi2.2
    * Rviz
* Internet of Things (IoT)
* NodeMCU 
* C++
* Python
* Lua



## Skeleton Tracking
Open source computer vision libraries OpenNi2.2 and NITE2.2 were used to process RGB-D data. As a result, the algorithm output is 15 joint vector of the tracked person. 

<img src="/images/project-images/human-action-recognition-iot/skeleton-tracking.png" width="50%" height="50%">

## IoT Network
An IoT network was created with Raspberry Pi as the main server and NodeMCU's were used to connect devices in the lab to the network. In this project, we connected a lamp to the network with NodeMCU.


<img src="/images/project-images/human-action-recognition-iot/standing-lightoff.png" width="75%" height="75%">

<img src="/images/project-images/human-action-recognition-iot/leaning-lighton.png" width="75%" height="75%">















