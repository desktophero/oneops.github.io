---
title: "Releases"

permalink: /releases/
---

<h1 class="primary" data-product-name="{{ site.name }}">{{ page.title | upcase }}</h1>

{% for release in site.releases reversed %}
<h1 id="{{ release.title | slugify }}" class="secondary">{{ release.title }}</h1>
<article data-category="release">
  <div class="article-meta">
    {% include author.html author=release.author %}
	<span class="date">{{ release.publication-date }}</span>
    <p class="description">{{ release.description }}</p>
  </div>
  <div class="article-content">
    {{ release.content }}
  </div>
{% include feedback.html %}  
</article>
{% else %}
{% include empty-article.html %}
{% endfor %}
