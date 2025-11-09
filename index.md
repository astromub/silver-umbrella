---
layout: default
title: Home
permalink: /index.html
---

## Welcome to ASTROMub

Explore binary trading strategies, risk management tools, and our Trade Tracker.

---

## 📌 Latest Strategies

<div class="card-grid">
  {% for post in site.posts %}
  <div class="card">
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <p>{{ post.description }}</p>
    <small>{{ post.date | date: "%b %d, %Y" }}</small>
  </div>
  {% endfor %}
</div>
