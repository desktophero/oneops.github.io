---
title: Best practices

permalink: user/best-practices/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign categories = site.best_practices | group_by: "category" %}
{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% if categories.size == 1 and categories[0].name.size == 0 %}
{% for practice in site.best_practices %}
{% if practice.path contains context %}
{% assign found_content = true %}
<article>
<h1 id="{{ practice.title | slugify }}" class="secondary">{{ practice.title }}
</h1>
<div class="article-meta">
{% include author.html author=practice.author %}
<span class="date">{{practice.publication-date}}</span>
</div>
<div class="article-content">
{{ practice.content }}
</div>
{% include feedback.html %}
</article>
{% endif %}
{% endfor %}
{% else %}
{% for category in categories %}
{% for practice in category.items %}
{% if practice.path contains context %}
<article>
<h1 id="{{ practice.title | slugify }}" class="secondary">{{ practice.title }}
</h1>
<div class="article-meta">
{% include author.html author=practice.author %}
<span class="date">{{practice.publication-date}}</span>
</div>
<div class="article-content">
{{ practice.content }}
</div>
{% include feedback.html %}
</article>
{% endif %}
{% endfor %}
{% endfor %}
{% endif %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
