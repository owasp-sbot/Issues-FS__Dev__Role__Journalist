---
layout: page
title: "Investigations"
permalink: /investigations/
---

In-depth investigations into systemic patterns and root causes across the Issues-FS ecosystem.

{% assign sorted = site.investigations | sort: "date" | reverse %}
{% for doc in sorted %}
<article class="listing-item">
  {% include badge.html type=doc.type %}
  <h3 class="listing-item__title"><a href="{{ doc.url | relative_url }}">{{ doc.title }}</a></h3>
  <div class="listing-item__meta">
    <time datetime="{{ doc.date | date_to_xmlschema }}">{{ doc.date | date: "%B %-d, %Y" }}</time>
    {% if doc.author %}<span class="metadata__separator">&middot;</span> {{ doc.author }}{% endif %}
    {% assign words = doc.content | number_of_words %}{% assign minutes = words | divided_by: 200 %}{% if minutes < 1 %}{% assign minutes = 1 %}{% endif %}
    <span class="metadata__separator">&middot;</span> {{ minutes }} min read
  </div>
  {% if doc.summary %}<p class="listing-item__summary">{{ doc.summary }}</p>{% endif %}
  {% if doc.topics and doc.topics.size > 0 %}
  <div class="listing-item__topics">
    {% for topic in doc.topics %}<span class="topic-pill">{{ topic }}</span>{% endfor %}
  </div>
  {% endif %}
</article>
{% endfor %}
