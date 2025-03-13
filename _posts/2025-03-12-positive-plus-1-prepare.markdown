---
layout: post
title:  "Positive+: 1. Prepare"
date:   2025-03-12 16:30:56 +0800
categories: Business
tags: Cafe Manager101
---

This is a another post template. I also love to talk about business. 

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