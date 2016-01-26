---
title: Prerequisites
permalink: developer/prerequisites/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for article in site.prerequisites %}
{% if article.path contains context %}
{% assign found_content = true %}
<article>
  <h1 id="{{ article.title | slugify }}" class="secondary">{{ article.title }}</h1>
  <div class="article-meta">
    {% include author.html author=article.author %}
    <span class="date">{{article.publication-date}}</span>
  </div>
  <div class="article-content">
  {{ article.content }}
  </div>
{% include feedback.html %}  
</article>
{% endif %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
