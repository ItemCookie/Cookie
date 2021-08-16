---
title: "Sitemap"
exerpt: "Everything this site has to offer"
permalink: /sitemap/
layout: archive
sidebar:
  nav: "archives"
---

A list of all the posts and pages found on the site. For you robots out there is an [XML version]({{ "sitemap.xml" | relative_url }}) available for digesting as well

## Pages
{% assign pages_by_title = site.pages | sort_natural: "title" %}

{% for post in pages_by_title %}
  {% assign title = post.title | strip_newlines %}
  {% unless title == "" %}
    {% include archive-single.html %}
  {% endunless %}
{% endfor %}

## Posts
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}

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