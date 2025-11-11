---
layout: default
title: Beginner Guide
permalink: /beginner-guide/
---

## 🧠 Beginner Guide & Resources

<div class="card-grid">
  {% for post in site.categories.beginner %}
  <div class="card">
    <a href="{{ site.baseurl }}{{ post.url }}" class="card-link">
      <h3>{{ post.title }}</h3>
      <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
      <p class="excerpt">{{ post.description | truncatewords: 10 }}</p>
    </a>
  </div>
  {% endfor %}
</div>

<hr><hr>

### Still Have Questions?
Contact our support team for personalized guidance.
