---
layout: post
title:  "The Difference Between catkin_make & catkin build"
author: Alperen
date:   2022-09-19
categories:
  - Robotics
  - Software
---

After getting familiar with ROS2 ecosystem and **colcon build**, I was looking for other tools to compile ROS1 packages as efficient as ROS2. My search led me to find **catkin build**. It is a way better and useful way of compiling your packages than **catkin_make**. Here are the main differences between them:
* catkin build provides an isolated environment for the build which makes adding/removing packages and handling dependencies easier (like catkin_make_isolated but parallelized version)
* catkin build provides a user friendly colored cmd output 
* catkin build allows users to get advantage of different catkin_tools like catkin locate, catkin list etc. 
...

If you want to learn more about the differences, check [catkin tools official webpage](https://catkin-tools.readthedocs.io/en/latest/migration.html). Maybe we should start changing ROS1 tutorials a bit! :) 
