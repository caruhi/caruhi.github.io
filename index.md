---
layout: default
title: Home
---

# Welcome

Hi, I'm Carolina Rubio.

I'm a software developer and linguist interested in NLP, AI and data science. I am a co-founder of a NLP SDK called Wowool. 

## Projects

- RASFF: investigating the Rapid Alert System for Food and Feed of the European Union

## LinkedIn

- GitHub: https://github.com/caruhi

## Blog

{% for post in site.posts %}
- **[{{ post.title }}]({{ post.url }})** — {{ post.date | date: "%Y-%m-%d" }}
{% endfor %}

Posts count: {{ site.posts | size }}