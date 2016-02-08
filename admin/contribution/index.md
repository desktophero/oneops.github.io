---
title: Contribution

permalink: admin/contribution/
--- 

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for article in site.contribution %}
{% if article.path contains context %}
{% assign found_content = true %}
{{ article.content }}
{% include feedback.html %}
{% endif %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
