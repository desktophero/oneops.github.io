---
title: "Key Concepts"
permalink: admin/key-concepts/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for key_concept in site.key_concepts %}
{% if key_concept.path contains context %}
{% assign found_content = true %}
{{ key_concept.content }}
{% include feedback.html %}
{% endif %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
