---
layout: default
title: Home
permalink: /
---

## 📌 Latest

<div class="card-grid">
  {% if site.posts.size > 0 %}
    {% for post in site.posts limit:6 %}
      <div class="card">
        <a href="{{ post.url | relative_url }}" class="card-link">
          <h3>{{ post.title }}</h3>
          <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
          <p class="excerpt">{{ post.excerpt | strip_html | truncatewords: 25 }}</p>
        </a>
      </div>
    {% endfor %}
  {% else %}
    <div class="card no-posts">
      <h3>🚫 No Posts Available</h3>
      <p>Sorry, we couldn't find any strategies or updates at the moment.</p>
      <p>Please check back later or explore our Beginner Guide for resources.</p>
    </div>
  {% endif %}
</div>
