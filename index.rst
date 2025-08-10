---
layoute: post
title: Homepage
---

Page d'accueil
==============

Index
-----

{% for post in site.posts %}
- **`{{ post.title }} <{{ post.url }}>`_** — {{ post.date | date: "%B %d, %Y" }}
{% endfor %}
