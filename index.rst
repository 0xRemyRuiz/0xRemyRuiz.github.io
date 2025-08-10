---
title: Homepage
---

Page d'accueil
==============

Index
-----

---
raw: html

    <ul>
    {% for post in site.posts %}
      <li><strong><a href="{{ post.url }}">{{ post.title }}</a></strong> — {{ post.date | date: "%B %d, %Y" }}</li>
    {% endfor %}
    </ul>
