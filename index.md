---
layout: default
title: Home
---

# Welcome

Hi, I'm Carolina Rubio.

I'm a software developer and linguist interested in NLP, AI and data science.

## Projects

- RASFF: investigating the Rapid Alert System for Food and Feed of the European Union

## Contact

- GitHub: https://github.com/caruhi

## Blog

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})** — {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}

Posts count: {{ site.posts | size }}