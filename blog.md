---
layout: page
title: Blog
permalink: /blog/
---

I try to blog about everything and share my experience. Although I mostly focus on academic life, robotics and software development, this is not a professional blog, so it is not surprising to encounter various topics in this blog. 

You can find full list of my blog posts chronically from most recent to oldest below. If you are interested in posts related to specific topic, here is the link to see posts divided based on categories:
<a href="/categories" style="font-size:150%">Posts Based on Categories</a>


<ul id="archive">
{% for post in site.posts %}
  {% capture y %}{{post.date | date:"%Y"}}{% endcapture %}
  {% if year != y %}
    {% assign year = y %}
    <h2 style="font-size:250%" class="blogyear">{{ y}} </h2>
  {% endif %}
<li class="archiveposturl"><span><a href="{{ post.url }}" style="font-size:150%" title="{{ post.title }}">{{ post.title }}</a></span><br/>
<span class = "postlower">

<!--<strong>Author:</strong> {{post.author}} -->
<strong style="font-size:150%;"> Category:</strong>  {% if post.categories %}
 
  {% for cat in post.categories %}
  <a href="/categories/#{{ cat }}" style="font-size:150%" title="{{ cat }}">{{ cat }}</a>&nbsp;
  {% endfor %}

{% endif %} <!-- {{ post.categories | first }} -->
<strong style="font-size:150%; font-family: 'Titillium Web', sans-serif; float:right; padding-right: .5em">{{ post.date | date: '%d %b %Y' }}</strong> 

{% if post.image %}<a href="{{ post.url | prepend: site.baseurl }}" ><img src="{{ post.image }}" /></a>{% endif %}
</span> 

</li>

<h2></h2>
{% endfor %}
</ul>

<!-- {{ post.date | date: '%m %d, %Y' }} -->

