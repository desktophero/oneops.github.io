---
title: "Typical Usage Scenarios"
author: "virtualtraveler"
permalink: developer/typical-scenarios/
---

<h1 class="primary">{{ page.title | upcase }}</h1>

{% assign url_parts = page.url | split: '/' %}
{% assign context = url_parts[1] | prepend: '/' | append: '/' %}

{% for scenario in site.typical_scenarios %}
{% if scenario.path contains context %}
{% assign found_content = true %}
<article>
    <h1 id="{{ scenario.title | slugify }}" class="secondary">{{ scenario.title }}
    </h1>
    <div class="article-meta">
      {% include author.html author=scenario.author %}
      <span class="date">{{scenario.publication-date}}</span>
    </div>
    <div class="article-content">
      {{ scenario.content }}
    </div>
{% include feedback.html %}    
</article>
{% endif %}
{% endfor %}
{% unless found_content %}
{% include empty-article.html %}
{% endunless %}
