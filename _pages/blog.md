---
title: "Blog"
permalink: /blog/
layout: single
author_profile: false
---

# Blog Posts

Welcome to my blog! Here I share my thoughts, research insights, and experiences in AI and machine learning.

## Recent Posts

{% assign posts = site.posts | sort: 'date' | reverse %}
{% for post in posts %}
  {% unless post.categories contains 'AI Learning Guide' %}
<div class="blog-post-preview" style="margin-bottom: 2em; padding: 1.5em; border: 1px solid #e9ecef; border-radius: 8px; background-color: #f8f9fa;">
  <h3 style="margin-top: 0; margin-bottom: 0.5em;">
    <a href="{{ post.url }}" style="color: #1e3a8a; text-decoration: none;">{{ post.title }}</a>
  </h3>
  <p style="margin: 0.5em 0; color: #666; font-size: 0.9em;">
    <i class="fas fa-calendar-alt" style="margin-right: 0.5em;"></i>
    {{ post.date | date: "%B %d, %Y" }}
    {% if post.categories %}
    <span style="margin-left: 1em;">
      <i class="fas fa-folder" style="margin-right: 0.5em;"></i>
      {{ post.categories | join: ", " }}
    </span>
    {% endif %}
  </p>
  {% if post.excerpt %}
  <p style="margin: 0.5em 0; line-height: 1.5;">
    {{ post.excerpt | strip_html | truncatewords: 30 }}
  </p>
  {% endif %}
  <a href="{{ post.url }}" style="color: #1e3a8a; text-decoration: none; font-size: 0.9em;">
    Read more <i class="fas fa-arrow-right" style="margin-left: 0.3em;"></i>
  </a>
</div>
  {% endunless %}
{% endfor %}

---

*More posts coming soon! Feel free to reach out if you have any questions or suggestions.*
