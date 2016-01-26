---
title: "Testing & Debugging"
author: "virtualtraveler"
permalink: developer/testing/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for article in site.testing %}
{% if article.path contains context %}
{% assign found_content = true %}
{{ article.content }}
{% endif %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
