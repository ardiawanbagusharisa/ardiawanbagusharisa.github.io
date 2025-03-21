---
layout: post
title: "List of Game Journals and Conferences"
date: 2025-03-21 23:59:59 +0800
categories: Research
tags: Research 
---

The followings are list of game journals and conferences. 

<p><strong>Categories:</strong> 
  {% for category in page.categories %}
    <a href="/category/{{ category | slugify }}/">{{ category }}</a>{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</p>

<p><strong>Tags:</strong> 
  {% for tag in page.tags %}
    <a href="/tag/{{ tag | slugify }}/">{{ tag }}</a>{% unless forloop.last %}, {% endunless %}
  {% endfor %}
</p>