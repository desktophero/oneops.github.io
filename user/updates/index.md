---
title: "Updates"
permalink: user/updates/
---

<h1 class="primary" data-product-name="{{ site.name }}">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for update in site.updates reversed %}
{% if update.path contains context %}
{% assign found_content = true %}
<h1 id="{{ update.title | slugify }}" class="secondary">
{% if update.link %}
<a href="{{ update.link }}" class="post-link">
{% endif %}
{{ update.title }}
{% if update.link %}
</a>
{% endif %}
</h1>
<article data-category="{{ update.category | downcase }}" data-hidden="{{ update.hidden }}">

  <div class="description article-content">
    {{ update.content }}
  </div>
{% include feedback.html %}  
</article>
{% endif %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
