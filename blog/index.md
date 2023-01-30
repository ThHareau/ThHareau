---
layout: post
sitemap: true
type: article
title: Blog
---
<ul>
  {% for post in site.blog_posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <p>{{ post.description }}</p>
    </li>
  {% endfor %}
</ul>
