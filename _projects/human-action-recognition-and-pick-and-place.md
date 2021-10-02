---
layout: project
title: "Gesture Recognition and Teleoperation of PhantomX Robotic Arm"
permalink: /projects/human-action-recognition-and-pick-and-place
image: /images/project-images/human-action-recognition-and-pick-and-place/1.png
---

# [Github Link for this project](https://github.com/samialperen/phantomx_controller)

<img src="/images/project-images/human-action-recognition-and-pick-and-place/demo.gif" width="100%" height="100%">


In this project, gesture recognition was achieved by tracking user's skeleton with RGB-D data obtained through Asus Xtion Pro camera. Predefined gestures were matched with particular robot arm movements to allow user to control robotic arm in a high level. Moreover, joint information of skeleton tracking algorithm was mapped with the joints of PhantomX Pincher (4 Dof) Robotic Arm. This mapping was used to teleoperate the robotic arm instead of using recognized human gestures to perform pick and place task. 

<img src="/images/project-images/human-action-recognition-and-pick-and-place/overall-diagram.png" width="100%" height="100%">


 
Keywords about the project:
* Robotic Arm
    * PhantomX Pincher
* Pick and Place
* Computer Vision
    * Human Detection
    * Skeleton Tracking
    * 3D Image
    * Gesture Recognition
    * Human Activity Recognition	
* Robot Operating System (ROS)
    * MoveIt
    * NITE2.2
    * OpenNi2.2
* C++
* Python
* MATLAB


## Skeleton Tracking
Open source computer vision libraries OpenNi2.2 and NITE2.2 were used to process RGB-D data. As a result, the algorithm output is 15 joint vector of the tracked person. 

<img src="/images/project-images/human-action-recognition-and-pick-and-place/skeleton-tracking.png" width="50%" height="50%">

## Gesture Recognition
Resulted 15 joint vector from skeleton tracking algorithm were processed to derive the angle between legs and body of the human. Then, this angle was used to classify whether human is standing or leaning. A dataset with 30 people were collected with the help of ROSBags and after probability analysis, a specific angle was selected as a threshold.

<img src="/images/project-images/human-action-recognition-and-pick-and-place/PMF2.png" width="75%" height="75%">

## Driving Robot Arm
First, the mapping between the result of skeleton tracking algorithm and joints of PhantomX Pincher was simulated thanks to [pxpincher_ros](https://github.com/rst-tu-dortmund/pxpincher_ros).

<img src="/images/project-images/human-action-recognition-and-pick-and-place/phantomjoints.png" width="50%" height="50%">

<img src="/images/project-images/human-action-recognition-and-pick-and-place/simulation.png" width="50%" height="50%">

After verifying simulation, MoveIt interaction interface was used to teleoperate robot either continious mapping or with predefined gestures.

<img src="/images/project-images/human-action-recognition-and-pick-and-place/moveit.png" width="50%" height="50%">












