---
title: "Tools"
permalink: admin/tools/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for tool in site.tools %}
{% if tool.path contains context %}
{% assign found_content = true %}
<article>
  <h1 id="{{ tool.title | slugify }}" class="secondary">{{ tool.title }}
  </h1>
  <div class="article-meta">
    {% include author.html author=tool.author %}    
    <span class="date">{{ tool.publication-date }}</span>
  </div>
  <div class="article-content">
  {{ tool.content }}
  </div>
{% include feedback.html %}  
</article>
{% endif %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
