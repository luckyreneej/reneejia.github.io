---
title: "AI Learning Guide"
permalink: /ai-learning-guide/
layout: single
author_profile: false
---

# AI Learning Guide

Welcome to my AI Learning Guide! Here you'll find a curated collection of articles, tutorials, and resources to help you master Artificial Intelligence and Machine Learning.

## General AI Learning Guide

{% assign ai_posts = site.posts | where_exp: "post", "post.categories contains 'AI Learning Guide'" | sort: 'date' | reverse %}
{% assign other_posts = ai_posts | where_exp: "post", "post.title contains 'AI Beginner'" %}
{% for post in other_posts %}
<div class="blog-post-preview" style="margin-bottom: 2em; padding: 1.5em; border: 1px solid #e9ecef; border-radius: 8px; background-color: #f8f9fa;">
  <h3 style="margin-top: 0; margin-bottom: 0.5em; font-size: 1.2em; font-weight: 600;">
    <a href="{{ post.url }}" style="color: #1e3a8a; text-decoration: none;">{{ post.title }}</a>
  </h3>
  <p style="margin: 0.5em 0; color: #666; font-size: 0.9em; text-align: left;">
    <i class="fas fa-calendar-alt" style="margin-right: 0.5em;"></i>
    {{ post.date | date: "%B %d, %Y" }}
    {% if post.read_time %}
    <span style="margin-left: 1em;">
      <i class="fas fa-clock" style="margin-right: 0.5em;"></i>
      {{ post.read_time }}
    </span>
    {% endif %}
  </p>
  {% if post.excerpt %}
  <p style="margin: 0.5em 0; line-height: 1.5; text-align: left;">
    {{ post.excerpt | strip_html | truncatewords: 30 }}
  </p>
  {% endif %}
  <a href="{{ post.url }}" style="color: #1e3a8a; text-decoration: none; font-size: 0.9em;">
    Read more
  </a>
</div>
{% endfor %}

## Quick Resources

### Essential Tools
- **Python Libraries**: NumPy, Pandas, Scikit-learn, TensorFlow/PyTorch
- **Development**: Jupyter Notebooks, VS Code, Google Colab
- **Learning Platforms**: Coursera, edX, Fast.ai, Kaggle

### Key Areas
- **Machine Learning**: Supervised/Unsupervised learning, model evaluation
- **Deep Learning**: Neural networks, CNN, RNN
- **Applications**: NLP, Computer Vision, Reinforcement Learning

---

*"The future belongs to those who believe in the beauty of their dreams." - Eleanor Roosevelt*

*Keep learning, keep building, and most importantly, keep believing in the power of AI to transform our world!*

---