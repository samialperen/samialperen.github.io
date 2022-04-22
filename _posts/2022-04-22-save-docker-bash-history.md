---
layout: post
title:  "Saving Bash History in a Docker Container for Better Debugging"
author: Alperen
date:   2022-04-22
categories:
  - Software
---

If you are regularly using docker or another container tool during your development process, I highly suggest to follow [this](https://zwischenzugs.com/2015/06/14/my-favourite-docker-tip/) blog post by [Ian Miell](https://www.linkedin.com/in/ian-miell-694496/) who is a software professional and partner of the Container Solutions company. In his post, he explains how to save all the commands run in a container (bash history). Normally, if you check **bash_history** in your Linux terminal, you won't be able to see all the commands run inside a container. They are not captured by default. Believe me you want to capture them as well. This will become handy at some point where you want to remember something you did cool to fix an issue in a command line inside container.
