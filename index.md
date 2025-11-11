---
layout: default
title: Home
permalink: /
---

## 📌 Latest

<div class="card-grid">

  {% for post in site.posts limit:6 %}
  <div class="card">
    <a href="{{ site.baseurl }}{{ post.url }}" class="card-link">
      <h3>{{ post.title }}</h3>
      <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
      <p class="excerpt">{{ post.description | truncatewords: 10 }}</p>
    </a>
  </div>
  {% endfor %}

</div>

