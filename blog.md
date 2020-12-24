---
layout: page
title: Blog
permalink: /blog/
---

I try to blog about everything and share my experience. Although I mostly focus on academic life, robotics and software development, this is not a professional blog, so it is not surprising to encounter various topics in this blog. 

You can find full list of my blog posts chronically from most recent to oldest below. If you are interested in posts related to specific topic, here is the link to see posts divided based on categories: 

<a href="/categories">Categories on my Blog</a>

Here is a list of all categories with number of blog posts:

{% assign sorted_cats = site.categories | sort  %}{% for category in sorted_cats %}{% if forloop.last == true %}and {% endif %}<a href="/categories/#{{category[0]}}" style="font-weight:normal;"> {{category[0] | camelcase }}</a> ({{ category[1].size  }}){% if forloop.last == false %}, {% endif %}{% endfor %} 


<ul id="archive">
{% for post in site.posts %}
  {% capture y %}{{post.date | date:"%Y"}}{% endcapture %}
  {% if year != y %}
    {% assign year = y %}
    <h2 class="blogyear">{{ y}}</h2>
  {% endif %}
<li class="archiveposturl"><span><a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a></span><br/>
<span class = "postlower">

<!--<strong>Author:</strong> {{post.author}} -->
<strong>Category:</strong>  {% if post.categories %}
 
  {% for cat in post.categories %}
  <a href="/categories/#{{ cat }}" title="{{ cat }}">{{ cat }}</a>&nbsp;
  {% endfor %}

{% endif %} <!-- {{ post.categories | first }} -->
<strong style="font-size:100%; font-family: 'Titillium Web', sans-serif; float:right; padding-right: .5em">{{ post.date | date: '%d %b %Y' }}</strong> 
</span> 

</li>
{% endfor %}
</ul>

<!-- {{ post.date | date: '%m %d, %Y' }} -->
