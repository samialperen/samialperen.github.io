---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<div class="home">
  {% assign total = 0 %}
  {% for post in site.posts %}

    {% assign total = total | plus: 1 %}

  {% endfor %}
  <h1 class="page-heading">Recent Posts ({{ total }})</h1>

  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>
        <!-- <script>
          img {
              display:block;
              margin:auto;
          }
        </script> -->
        {% if post.image %}<a href="{{ post.url | prepend: site.baseurl }}" style="display:block;margin:auto"><img src="{{ post.image }}" style="display:block;margin:auto" /></a>{% endif %}
      </li>
    {% endfor %}
  </ul>

  <p class="rss-subscribe">subscribe <a href="{{ '/feed.xml' | prepend: site.baseurl }}">via RSS</a></p>

</div>
