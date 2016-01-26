---
title: Reference

permalink: /:path/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign groups = site.references | group_by: "category" | sort_by: "name" %}
{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for group in groups %}
<h1 class="secondary">{{ group.name | upcase }}</h1>
{% for item in group.items %}
{% if item.path contains context %}
{% assign found_content = true %}
<article>
    <h1 id="{{ item.title | slugify }}">{{ item.title }}
    </h1>
    {{ item.content }}
{% include feedback.html %}
</article>
{% endif %}
{% endfor %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
