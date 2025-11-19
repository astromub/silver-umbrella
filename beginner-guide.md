---
layout: default
title: Beginner Guide
permalink: /beginner-guide/
---

## 🧠 Beginner Guide & Resources

<div class="card-grid">
  {% if site.categories.beginner.size > 0 %}
    {% for post in site.categories.beginner %}
    <div class="card">
      <a href="{{ site.baseurl }}{{ post.url }}" class="card-link">
        <h3>{{ post.title }}</h3>
        <p class="date">{{ post.date | date: "%B %d, %Y" }}</p>
        <p class="excerpt">{{ post.description | default: post.excerpt | truncatewords: 20 }}</p>
        <span class="card-badge beginner">Beginner Friendly</span>
      </a>
    </div>
    {% endfor %}
  {% else %}
    <div class="card no-posts">
      <h3>🚫 No Beginner Posts Found</h3>
      <p>We couldn't find any beginner strategies at the moment.</p>
      <p>Check back soon or explore our Trade Tracker for insights.</p>
    </div>
  {% endif %}
</div>
