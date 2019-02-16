---
layout: post
title:  "How to Create Your Own Blog with Github Pages and Jekyll"
date:   2019-02-01 11:49:13 +0300
comments: true
---

In this tutorial, I will try to explain all the necessary steps to create your 
own blog using github pages and Jekyll. I will assume that you have already 
known git and how to use it. If you don't, you do not need to worry at all.
There are many tutorials to learn github like [this one](https://guides.github.com/activities/hello-world/).

## 1-)SETTING UP THE BLOG
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
$ sudo apt-get install ruby-dev
```
Ubuntu 14.04:
```
$ sudo apt-get install rubygems-integration
```
Ubuntu 12
```
$ sudo apt-get install rubygems
```

* Install jekyll using rubygem

```
$ sudo gem install jekyll
```
* Go your website directory

```
$ cd username.github.io
```
* It needs to be empty so delete everything

```
$ sudo rm -rf * 
```
* Now create new jekyll
 
```
$ jekyll new .
```
If you have any problem about bundler in this step install bundler as well
```
$ sudo gem install bundler
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
$ jekyll serve
```
This command will publish your website locally. Look for the line
```
Server address: http://127.0.0.1:4000/
```
You can see what your website will look like by visiting this local adress in 
your web browser.

**Third Step**

If you are happy with the look of your website, you need to publish all the 
changes to github to make it available at [https://username.github.io/](https://username.github.io/)
```
$ git add *
$ git commit -m "Website is online"
$ git push origin master
```

Now you and everybody else can see your website at https://username.github.io
Congratulations!!

## 2-)CUSTOMIZE YOUR BLOG 
**Add Comment Section Into Your Blog**
In order to allow readers to comment on your posts, you can use very common
service named [Disqus](https://disqus.com/home). Sign up and do not forget 
your Disqus username.
Go username.github.io directory and create a directory named _includes
```
$ cd username.github.io
$ mkdir _includes
```
Go _includes directory and create a html snippet code named comments.html
```
$ cd _includes
$ touch comments.html 
$ gedit comments.html
```
Paste this code:
```{% raw %}
{% if page.comments %}
<!-- Add Disqus comments. -->
<div id="disqus_thread"></div>
<script type="text/javascript">
  /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
  var disqus_shortname = 'YOUR_DISQUS_USERNAME'; // required: replace example with your forum shortname
  var disqus_identifier = "{{ site.disqusid }}{{ page.url | replace:'index.html','' }}";

  /* * * DON'T EDIT BELOW THIS LINE * * */
  (function() {
    var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
    dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
  })();
</script>
<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}
{% endraw %}```



Change YOUR_DISQUS_USERNAME with yours.

Now create another directory named _layouts under username.github.io if it 
does not exist.
```
$ cd ..
$ mkdir _layouts
 

























