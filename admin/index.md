---
title: Overview
permalink: admin/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for article in site.overview %}
{% if article.path contains context %}
{{ article.content }}
{% endif %}
{% endfor %}
