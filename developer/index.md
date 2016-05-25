---
title: Overview
permalink: developer/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for article in site.overview %}
{% if article.path contains context %}
{{ article.content }}
{% include feedback.html %}
{% endif %}
{% endfor %}
