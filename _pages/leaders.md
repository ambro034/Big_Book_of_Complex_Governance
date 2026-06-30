---
title: Contributor Leader Board 
author: Graham Ambrose
date: 2026-06-29
category: Jekyll
layout: post 
---

<!-- Summary Counts of total Contributions -->

{% assign target_string = "%&%" %}
{% assign total_count = 0 %}

{% comment %} Loop through all blog posts {% endcomment %}
{% for post in site.posts %}
  {% if post.content contains target_string %}
    {% assign parts = post.content | split: target_string %}
    {% assign occurrences = parts.size | minus: 1 %}
    {% assign total_count = total_count | plus: occurrences %}
  {% endif %}
{% endfor %}

<p>Our community has contributed <strong>{{ total_count }}</strong> resources to produce this site.</p>



## Tags by Count

<!-- Summary Counts at the Top -->
<div class="tag-cloud">
  {% for tag in site.tags %}
    {% assign name = tag | first %}
    {% assign count = tag | last | size %}
    <a href="#{{ name | slugify }}" style="margin-right: 15px;">
      {{ name }} ({{ count }})
    </a>
  {% endfor %}
</div>

<hr>

<!-- Detailed Section with Posts -->
{% for tag in site.tags %}
  {% assign name = tag | first %}
  <h4 id="{{ name | slugify }}">{{ name }}</h4>
  <ul>
    {% for post in site.tags[name] %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a> 
      </li>
    {% endfor %}
  </ul>
{% endfor %}


### Test
{% for post in site.posts %}
  {% if post.comments %}
    {% for comment in post.comments %}
      <div class="comment-item">
        <strong>{{ comment.name }}</strong> in 
        <a href="{{ post.url }}">{{ post.title }}</a>
        <br>
        <small>{{ comment.date | date: "%B %d, %Y" }}</small>
        <p>{{ comment.message }}</p>
      </div>
    {% endfor %}
  {% endif %}
{% endfor %}

### Test 2

{% assign total_comments = 0 %}
{% for post in site.posts %}
  {% assign post_comments = site.data.comments[post.slug] %}
  {% if post_comments %}
    {% assign total_comments = total_comments | plus: post_comments.size %}
  {% endif %}
{% endfor %}
<p>Total Site Comments: {{ total_comments }}</p>