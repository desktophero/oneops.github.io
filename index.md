---
title: Overview
permalink: /
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign context = site.contexts | first | last | prepend: '/' %}

{% for article in site.overview %}
{% if article.path contains context %}
{{ article.content }}
{% include feedback.html %}
{% endif %}
{% endfor %}
