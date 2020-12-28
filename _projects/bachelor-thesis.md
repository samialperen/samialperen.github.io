---
layout: project
title: "Mobile Robotic Platform Design and Implementation for Simultaneous Localization and Mapping (SLAM)"
permalink: /projects/bachelor-thesis
image: /images/project-images/bachelor-slam/robot.jpg
---

# [Github Link for this project](https://github.com/samialperen/oko_slam)

This project was my bachelor capstone project. We were asked to design and implement a mobile robot
to create the map of an unknown indoor environment. 

The project is about:
* Custom made cost-effective LIDAR 
    * Communication with ROS
* Simultaneous Localization and Mapping (SLAM)
* Robot Operating System
    * Navigation Stack (Autonomous Navigation)
    * Hector SLAM, Cartographer SLAM, Gmapping, Karto SLAM, Lago SLAM, Core SLAM
    * ROS Serial
    * Frontier Exploration
* Gazebo
* CAD Design (Solidworks)
* OpenCV
* PID Controllers
* Embedded Programming (ARM Cortex M10 & STM microprocessors)
* PCB Design
* 3D Printing


Here is a mapping result after robot autonomosly navigated in the unknown area:
![mapping-result](/images/project-images/bachelor-slam/mapping-result.jpg)

Here is a video of the robot in action:
<iframe width="100%" height="478" src="https://www.youtube.com/embed/eFyuFZXPAJI" frameborder="0" allowfullscreen></iframe>
<br />

# Overall Block Diagram
![Block Diagram](/images/project-images/bachelor-slam/block-diagram.png)

Green filled blocks represents physical blocks while blue filled blocks represents ROS packages/nodes. Connection labels describes the data content that is transferred. Three microcontrollers are used synchronously in this project:
![Microcontrollers](/images/project-images/bachelor-slam/microcontrollers.png)

# Mechanical Design
In the Solidworks environment, the robot was designed from scratch. A proper environment with real world dimensions were also created in the same way.
![CAD Designs](/images/project-images/bachelor-slam/solidworks.jpg)

In the end, everything was rendered and these mechanical designs were transferred to ROS environment to test mapping performance in Gazebo simulator.

![Gazebo](/images/project-images/bachelor-slam/gazebo.png){:width="450px"}.

SLAM performance was tested in Gazebo with our custom made LIDAR parameters. For example, a LIDAR with a frequency 2hz and 64 samples per rotation yielded the following mapping:
![Gazebo Mapping](/images/project-images/bachelor-slam/test-gazebo.gif)

# Custom-made LIDAR
The LIDAR collects information about the environment by using 4 x VL53L0X Time of Flight (ToF) sensors and it sends measured data via bluetooth connection. A Nema 17 stepper motor with 1.8 angle resolution (42SHD0001) is used to rotate LIDAR unit. To be able to measure the angle of the lidar with respect to robot, we used optical encoder with 128 point incremental pattern and 1 point index pattern. We are using wireless power to run the LIDAR.

Here is an expansion of LIDAR design in solidworks:
![LIDAR solidworks](/images/project-images/bachelor-slam/lidar_2way.gif)

Optical encoder design tests & PCB electrical tests:

![LIDAR solidworks optical encoder](/images/project-images/bachelor-slam/lidar-solidworks.gif){:width="420px"}
![LIDAR PCB](/images/project-images/bachelor-slam/lidar-pcb.gif){:width="420px"}

LIDAR in action and data transfer to ROS:

![LIDAR rotates](/images/project-images/bachelor-slam/lidar-rotate.gif){:width="420px"}
![LIDAR ROS](/images/project-images/bachelor-slam/lidar-ros.gif){:width="420px"}


# Localization
Locazation of the robot was achieved using two encoders on Namiki 22CL-3501PG 12V DC Motors, laser scan data from LIDAR and IMU data. These sensors were read on main STM Controller and they were combined in ROS environment using Extended Kalman Filter (EKF).

![Localization](/images/project-images/bachelor-slam/odometry.png){:width="600px"}


# Graphical User Interface (GUI)
A GUI was designed to operate robot easily.
* Connects the robot via bluetooth
* Different modes:
    * Autonomous navigation
    * Manual, i.e. teleoperation
* Change LIDAR or odometry parameters
* Shows extracted map

![GUI](/images/project-images/bachelor-slam/gui.JPG){:width="500px"}
![GUI map](/images/project-images/bachelor-slam/gui-map.JPG){:width="350px"}

# Results 
In the end, the robot was tested in real life where it can both autonomously navigate (explore) and extract the mapping of the environment (SLAM) at the same time. 

![robot](/images/project-images/bachelor-slam/robot.jpg){:width="420px"}
![robot](/images/project-images/bachelor-slam/test-real.png){:width="460px"}

Various SLAM techniques and autonomous navigation algorithms (exploration) were tested such as 
* Hector SLAM
* Gmapping
* KartoSLAM
* CoreSLAM
* LagoSLAM
* Explore-LITE
* Frontier Exploration

Gmapping result on the left and Cartographer SLAM on the right:

![robot](/images/project-images/bachelor-slam/test-gmapping.png){:width="350px"}
![robot](/images/project-images/bachelor-slam/test-carto.png){:width="351px"}

# More Information
To learn more about the project, you can read [the technical report](/docs/bachelor-slam/final-report.pdf) or refer to [Github repository](https://github.com/samialperen/oko_slam).