---
title: "AI Learning Guide"
permalink: /ai-learning-guide/
layout: single
author_profile: false
---

# AI Learning Guide

Welcome to my AI Learning Guide! Here you'll find a curated collection of articles, tutorials, and resources to help you master Artificial Intelligence and Machine Learning.

## Featured Series: Ranking & Recommendation Systems

### Part 1: Foundations
{% assign foundational_post = site.posts | where_exp: "post", "post.title contains 'Foundational Papers'" | first %}
{% if foundational_post %}
<div class="blog-post-preview" style="margin-bottom: 1.5em; padding: 1.2em; border: 1px solid #e9ecef; border-radius: 8px; background-color: #f8f9fa;">
  <h4 style="margin-top: 0; margin-bottom: 0.5em; font-size: 1.1em; font-weight: 600;">
    <a href="{{ foundational_post.url }}" style="color: #1e3a8a; text-decoration: none;">{{ foundational_post.title }}</a>
  </h4>
  <p style="margin: 0.5em 0; color: #666; font-size: 0.9em; text-align: left;">
    {{ foundational_post.date | date: "%B %d, %Y" }}
  </p>
  {% if foundational_post.excerpt %}
  <p style="margin: 0.5em 0; line-height: 1.4; font-size: 0.9em; text-align: left;">
    {{ foundational_post.excerpt | strip_html | truncatewords: 25 }}
  </p>
  {% endif %}
</div>
{% endif %}

### Part 2: Deep Learning Era
{% assign deeplearning_post = site.posts | where_exp: "post", "post.title contains 'Deep Learning Era'" | first %}
{% if deeplearning_post %}
<div class="blog-post-preview" style="margin-bottom: 1.5em; padding: 1.2em; border: 1px solid #e9ecef; border-radius: 8px; background-color: #f8f9fa;">
  <h4 style="margin-top: 0; margin-bottom: 0.5em; font-size: 1.1em; font-weight: 600;">
    <a href="{{ deeplearning_post.url }}" style="color: #1e3a8a; text-decoration: none;">{{ deeplearning_post.title }}</a>
  </h4>
  <p style="margin: 0.5em 0; color: #666; font-size: 0.9em; text-align: left;">
    {{ deeplearning_post.date | date: "%B %d, %Y" }}
  </p>
  {% if deeplearning_post.excerpt %}
  <p style="margin: 0.5em 0; line-height: 1.4; font-size: 0.9em; text-align: left;">
    {{ deeplearning_post.excerpt | strip_html | truncatewords: 25 }}
  </p>
  {% endif %}
</div>
{% endif %}

## All AI Learning Guide Articles

{% assign ai_posts = site.posts | where_exp: "post", "post.categories contains 'AI Learning Guide'" | sort: 'date' | reverse %}
{% for post in ai_posts %}
<div class="blog-post-preview" style="margin-bottom: 2em; padding: 1.5em; border: 1px solid #e9ecef; border-radius: 8px; background-color: #f8f9fa;">
  <h3 style="margin-top: 0; margin-bottom: 0.5em; font-size: 1.2em; font-weight: 600;">
    <a href="{{ post.url }}" style="color: #1e3a8a; text-decoration: none;">{{ post.title }}</a>
  </h3>
  <p style="margin: 0.5em 0; color: #666; font-size: 0.9em; text-align: left;">
    {{ post.date | date: "%B %d, %Y" }}
    {% if post.categories %}
    <span style="margin-left: 1em;">
      {{ post.categories | join: ", " }}
    </span>
    {% endif %}
    {% if post.read_time %}
    <span style="margin-left: 1em;">
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