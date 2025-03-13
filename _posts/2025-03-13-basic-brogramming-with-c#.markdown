---
layout: post
title: "Basic Programming with C#"
date: 2025-03-13 06:39:50 +0800
categories: Programming 
tags: Programming C#
---

Reserved post for Basic Programming with C# tutorial. 

Use this `highlight` emphasize important things. 

Use code snippet for c#: 
{% highlight c#%}
public void OnCollision() 
{
  // Checking the elevation
  if(gameObject.transform.position.y <= 1.0f) 
  {
    Debug.Log("Low elevation.");
  }
}
{% endhighlight %}

Check out another [Post][post] for more. 

[post]: https://ardiawanbagusharisa.github.io/blog

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