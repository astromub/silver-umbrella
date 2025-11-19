---
layout: default
title: Home
permalink: /
---

## 📌 Latest Trading Strategies

<div class="card-grid">
  {% if site.posts.size > 0 %}
    {% for post in site.posts limit:6 %}
      <div class="card">
        <a href="{{ post.url | relative_url }}" class="card-link">
          <h3>{{ post.title }}</h3>
          <p class="date">{{ post.date | date: "%B %d, %Y" }}</p>
          <p class="excerpt">{{ post.excerpt | strip_html | truncatewords: 25 }}</p>
          {% if post.categories contains 'beginner' %}
            <span class="card-badge beginner">Beginner</span>
          {% elsif post.categories contains 'strategy' %}
            <span class="card-badge strategy">Strategy</span>
          {% endif %}
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

## 📱 Trade Anywhere With Our Mobile App

<div class="mobile-app-promo">
  <div class="app-features">
    <h3>Mobile Trading Tracker</h3>
    <p>Access your trading strategies and track performance directly from your mobile device.</p>
    
    <div class="feature-list">
      <div class="feature">
        <span class="feature-icon">📊</span>
        <span>Real-time strategy tracking</span>
      </div>
      <div class="feature">
        <span class="feature-icon">📱</span>
        <span>Mobile-optimized interface</span>
      </div>
      <div class="feature">
        <span class="feature-icon">📚</span>
        <span>Offline access to guides</span>
      </div>
      <div class="feature">
        <span class="feature-icon">🔔</span>
        <span>Push notifications</span>
      </div>
    </div>
    
    <a href="https://astronuri-trade-tracker.netlify.app/" target="_blank" class="app-cta-button">
      Open Mobile App
    </a>
    
    <p class="app-note">Optimized for mobile browsers - No download required</p>
  </div>
</div>
