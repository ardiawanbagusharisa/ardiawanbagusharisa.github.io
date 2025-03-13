---
layout: page
title: Blog
permalink: /blog/
---

Find an article you think is interesting. 

<h2>Categories</h2>
{% for category in site.categories %}
  <h3>{{ category[0] }}</h3>
  <ul>
    {% for post in category[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        {{ post.excerpt }}
      </li>
    {% endfor %}
  </ul>
{% endfor %}