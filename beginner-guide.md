---
layout: default
title: Beginner Guide
permalink: /beginner-guide/
---

## 📖 Beginner Guide & Resources

Welcome to the beginner's hub! Here are the core topics and blog posts dedicated to getting you started safely and effectively.

<div class="card-grid">
    
    {% for post in site.categories.Beginner %}
    
    <div class="card">
        <a href="{{ site.baseurl }}{{ post.url }}" class="card-link">
            
            <h3>{{ post.title }}</h3>
            
            <p class="date">{{ post.date | date: "%b %d, %Y" }}</p>
            
            <p class="excerpt">{{ post.excerpt }}</p>
        </a>
    </div>

    {% endfor %}
    </div>

<hr>

### Still Have Questions?
Contact our support team for personalized guidance.
