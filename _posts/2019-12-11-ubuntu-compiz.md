---
layout: post
title:  "Use Ubuntu Properly: Workspaces, Shortcuts and Sliding Windows"
author: Alperen
date:   2019-12-11
image: /images/ubuntu-compiz/ubuntu-logo.jpg
categories: 
  - Software
---

![Ubuntu Logo](/images/ubuntu-compiz/ubuntu-logo.jpg)


In this post, I am going to explain my way of configuring Ubuntu to make my life easier. I hope it will be useful for you as well!

**WARNING:** I tested these methods on Ubuntu 16.04. Probably, they are going to be more or the less same for other versions, but there might be small differences!

First of all, you should start using **workspaces**. Workspaces refer to the grouping of windows on your desktop. You can create multiple workspaces, which act like virtual desktops. Workspaces are meant to reduce clutter and make the desktop easier to navigate. Workspaces can be used to organize your work. For example, you could have all your communication windows, such as e-mail and your chat program, on one workspace, and the work you are doing on a different workspace. Your music manager could be on a third workspace. Believe me workspaces are one of the great features of Linux!

To enable workspaces:
* Go ```Systems Setting->Appearance```
* Select ```behavior``` tab.
* Tick ```enable workspaces``` box.
![Enable workspaces](/images/ubuntu-compiz/1.png)

By default, Ubuntu provides 2x2 workspaces. I personally, don't like this. I prefer 3x1. You can change number of workspaces using **CompizConfig Settings Manager**.
* Install CompizConfig Settings Manager
```
$ sudo apt-get install compizconfig-settings-manager
```

* After installation, run CompizConfig. You can find it by typing Compiz after hitting Windows key button.
* Navigate to General -> General Options -> Desktop Size tab.
![](/images/ubuntu-compiz/4.png)

* In here, you can adjust number of horizontal and vertical virtual size.
* Now you can be able to navigate between workspaces using keyboard shortcut Ctrl + Alt + Arrow Keys.

CompizConfig Settings Manager (CCSM) provides also a good way to divide your screen into 4 or more spaces. To enable this feature:
* Launch CCSM
* Go Window Management category and click Grid.
![](/images/ubuntu-compiz/3.png)

* I like to divide the screen into 4 pieces. To do this select everything like below:
![](/images/ubuntu-compiz/2.png)

* You can see keyboard shortcuts to move pieces to desired locations in bindings tab.
 ![](/images/ubuntu-compiz/5.png)

I like the default shortcuts. For example, if you press Ctrl + Alt + 7, selected window moves to top left, or if you press Ctrl + Alt + 6, it moves to right. You can achieve this behaviour by dragging selected windows with mouse to right, left, bottom left, top left etc.

**WARNING:** The CompizConfig Settings Manager is a powerful application. You might break your desktop configuration by mistake. If you encounter problems after tweaking your setup with CompizConfig, you can reset settings by:
```
$ unity --reset
```

CCSM has many to offer, but this post is limited with the features above. 

I hope thanks to this post, I can manage to make your Linux experience more enjoyable.
 

