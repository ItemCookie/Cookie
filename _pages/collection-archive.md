---
title: "Posts by Collection"
permalink: /collections/
layout: archive
sidebar:
  nav: "archives"
---

{% assign collections_by_label = site.collections | sort_natural: "label" %}

{% capture written_label %}'None'{% endcapture %}

{% for collection in collections_by_label %}
  {% unless collection.output == false or collection.label == "posts" %}
    {% capture label %}{{ collection.label }}{% endcapture %}
    {% if label != written_label %}
      <h2 id="{{ label | slugify }}" class="archive__subtitle">{{ label }}</h2>
      {% capture written_label %}{{ label }}{% endcapture %}
    {% endif %}
  {% endunless %}
  {% for post in collection.docs %}
    {% unless collection.output == false or collection.label == "posts" %}
      {% include archive-single.html %}
    {% endunless %}
  {% endfor %}
{% endfor %}