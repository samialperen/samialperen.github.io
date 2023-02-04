---
layout: post
title:  "Saving Bash History in a Docker Container for Better Debugging"
author: Alperen
date:   2022-04-22
categories:
  - Software
---

If you are regularly using docker or another container tool during your development process, I highly suggest to follow [this](https://zwischenzugs.com/2015/06/14/my-favourite-docker-tip/) blog post by [Ian Miell](https://www.linkedin.com/in/ian-miell-694496/) who is a software professional and partner of the Container Solutions company. In his post, he explains how to save all the commands run in a container (bash history). Normally, if you check **bash_history** in your Linux terminal, you won't be able to see all the commands run inside a container. They are not captured by default. Believe me you want to capture them as well. This will become handy at some point where you want to remember something you did cool to fix an issue in a command line inside container.

You have to be careful though! Due to bash size, you might lose some part of your local bash history. Therefore, I modified the suggested way a bit. I am copying bash history inside docker (```/root/.bash_history```) to a new file on my local machine (```~/.docker_bash_history```) instead of appending it to local bash history. Here is how:
```
	touch $(HOME)/.docker_bash_history
	xhost +
	docker run \
    		-v $(HOME)/.docker_bash_history:/root/.bash_history: \
		-it \
		...
		add whatever you want
		...
		/bin/bash
```

<center> 
  <script type='text/javascript' src='https://storage.ko-fi.com/cdn/widget/Widget_2.js'></script><script type='text/javascript' style="text-align:center">kofiwidget2.init('Buy Me a Coffee', '#e08428', 'V7V3IDOGW');kofiwidget2.draw();</script> 
</center>