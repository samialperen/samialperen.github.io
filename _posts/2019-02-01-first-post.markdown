---
layout: post
title:  "How to Create Your Own Blog with Github Pages and Jekyll"
date:   2019-02-01 11:49:13 +0300
---

In this tutorial, I will try to explain all the necessary steps to create your 
own blog using github pages and Jekyll. I will assume that you have already 
known git and how to use it. If you don't, you do not need to worry at all.
There are many tutorials to learn github like [this one](https://guides.github.com/activities/hello-world/).

**First Step:**
The first thing you need is to create a github repository for your blog and
match it with your local files. In order to do this, follow [github pages
tutorial](https://pages.github.com/). It explains how to setup your own website.

**Second Step:**
So far we managed to create our own website on github, but whatabout Jekyll?
What is it? Jekyll is some kind of a system that allows you to create nice HTML
webpages without any need to write ugly HTML codes. Instead, it converts your 
writings which are in markdown format (don't worry it is super easy) to HTML
webpage format. Sounds nice, right?

Until here you should be able to see your website https://username.github.io/
Now it is time to install jekyll.

* First install ruby. 
Ubuntu 16.04 or 18.04:
```
sudo apt-get install ruby-dev
```
Ubuntu 14.04:
```
sudo apt-get install rubygems-integration
```
Ubuntu 12
```
sudo apt-get install rubygems
```

* Install jekyll using rubygem
```
sudo gem install jekyll
```

* Go your website directory
```
cd username.github.io
```
* It needs to be empty so delete everything
```
rm -rf * 
```
* Now create new jekyll 
```
jekyll new .
```
* Run ls to check.
```
$ ls
config.yaml    _layouts    _sass ....
_posts      _includes       about.md ...
```
* Thanks to jekyll we can view our website locally without committing to 
github. This allows to easily check changes we have made before commits.
```
jekyll serve
```
This command will publish your website locally. Look for the line
```
Server address: http://127.0.0.1:4000/
```
You can see what your website will look like by visiting this local adress in 
your webbrowser.






















