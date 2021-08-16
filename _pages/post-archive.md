---
title: "Post Archive"
permalink: /posts/
collection: posts
layout: archive
sidebar:
  nav: "archives"
---
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}