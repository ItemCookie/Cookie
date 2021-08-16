---
title: "Page Archive"
permalink: /pages/
layout: archive
sidebar:
  nav: "archives"
---

{% assign pages_by_title = site.pages | sort_natural: "title" %}

{% for post in pages_by_title %}
  {% assign title = post.title | strip_newlines %}
  {% unless title == "" %}
    {% include archive-single.html %}
  {% endunless %}
{% endfor %}