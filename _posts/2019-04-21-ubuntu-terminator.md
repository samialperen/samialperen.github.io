---
layout: post
title:  "Terminator: A Linux Terminal Emulator with Multiple Terminals in One"
author: Alperen
date:   2019-04-21
image: /images/terminator/8.png
categories:
  - Software
---
![My Terminal with ROS](/images/terminator/8.png)

As linux users, we all suffer from the default linux terminal when we try to call multiple terminals. We open new terminal each time and after some time, it becomes quite difficult to navigate between terminals. I had suffered from this during the time where I was trying to learn **Robot Operating System (ROS)** because you need to call each script of ROS from another terminal, and default linux terminal made me crazy. Thanks to my friend Jean Pierre, I discovered an amazing Linux Terminal Emulator **Terminator**.

The beauty about **Terminator** is that it provides the ability to create multiple terminals in just one window. IT also allows you to change other terminal properties such as fonts, fonts colours, background color etc. In this post, I will try to explain installation of Terminator in Linux and give some tips that I frequently use.

### Installation

* Ubuntu-Based Distributions
```
$ sudo apt-get install terminator
```

* Fedore & Other Derivatives
```
$ dnf install terminator
```

That's it. It is installed successfully.

### Usage & Tips

After installation, just call the terminal with ```CTRL + ALT + T``` 
![Initial Terminator Startup](/images/terminator/1.png)

Right click to terminal and choose split-horizontally or vertically.
![Split](/images/terminator/2.png)

As you can see, now we have two terminals in one window. You can navigate between terminals using ```ALT+Arrow Keys```
![Multiple Terminals](/images/terminator/3.png)

You can further split terminals.
![Further Split](/images/terminator/4.png)

Right click to **Preferences**. You can customize your terminal as you wish.
![Preferences](/images/terminator/5.png)

When you go **Keybindings** tab, you will see that there is a keyboard shortcut for almost every operation. I prefer to use default shortcuts, but you can change if you want. 
![Keyboard Shortcuts](/images/terminator/6.png)

Here are some shortcuts that I use commonly:
* Ctrl + Shift + O  --> Split Horizontally
* Ctrl + Shift + E  --> Split Vertically
* Ctrl + Shift + W  --> Close the Selected Terminal Window
* Alt + Arrow Keys --> Navigate Between Terminal Windows
* Ctrl + Shift + X --> (De)Maximise the Selected Terminal Window
* Alt + A --> Select all Terminals (For example, very useful when you try to connect using ssh and you need more terminals)
* Alt + G --> Deselect all Terminals

My terminal looks like below while I am working with ROS.
![My Terminal with ROS](/images/terminator/7.png)

That's all for this post. I wish it would be useful :)

<center> 
  <script type='text/javascript' src='https://storage.ko-fi.com/cdn/widget/Widget_2.js'></script><script type='text/javascript' style="text-align:center">kofiwidget2.init('Buy Me a Coffee', '#e08428', 'V7V3IDOGW');kofiwidget2.draw();</script> 
</center>