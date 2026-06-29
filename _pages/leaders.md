---
title: Contributor Leader Board 
author: Graham Ambrose
date: 2026-06-29
category: Jekyll
layout: post 
---

<p>Total pages across site: <strong>{{ site.pages.size }}</strong></p>
<p>Total blog posts: <strong>{{ site.posts.size }}</strong></p>


## Tags by Count

{% capture tag_string %}
  {% for tag in site.tags %}
    {{ tag | last | size | prepend: "000000" | slice: -6, 6 }}#{{ tag | first }}
    {% unless forloop.last %}|{% endunless %}
  {% endfor %}
{% endcapture %}

{% assign sorted_tag_array = tag_string | split: "|" | sort | reverse %}

<ul>
  {% for item in sorted_tag_array %}
    {% assign tag_pairs = item | split: "#" %}
    {% assign count = tag_pairs[0] | plus: 0 %}
    {% assign name = tag_pairs[1] | strip %}
    <li>
      <strong>{{ name }}</strong>: {{ count }} posts
    </li>
  {% endfor %}
</ul>