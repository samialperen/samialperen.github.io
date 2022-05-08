---
layout: post
title:  "Scaling Angles in Radians to [-&pi;, &pi;] Range in Code for Robotics Applications"
author: Alperen
date:   2022-05-06
categories:
  - Software
  - Robotics
---

If you are working in robotics, there will be moment where you need to scale angles into range of [-&pi;_, &pi;_] since many control laws require this range as input constraint. Here is a trick to normalize given angles in radians to [-&pi;_, &pi;_] range. The trick is to usage of built-in **atan2** function.

### C++
```
#include <math.h> // cos, sin
#include <cmath.h> // atan2
...
def normalize(angle)
{
	// Input angle is in radians
	return atan2(sin(angle),cos(angle))
}
```

### Python
```
import numpy as np # if using numpy version
import math # if using math version
...
def normalize(angle):
	# Numpy version is faster
	return np.arctan2(np.sin(angle),np.cos(angle))
	# If you do not want to deal with numpy, here is math version
	return math.arctan2(np.sin(angle),np.cos(angle))
```
