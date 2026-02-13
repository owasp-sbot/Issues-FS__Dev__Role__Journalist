---
layout: home
title: "Issues-FS News"
---

<h2 class="section-heading">Recent Publications</h2>

{% assign all_docs = site.articles | concat: site.daily-briefs | concat: site.interviews | concat: site.investigations | concat: site.corrections %}
{% assign sorted_docs = all_docs | sort: "date" | reverse %}

{% for doc in sorted_docs limit:20 %}
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

<h2 class="section-heading">Categories</h2>

- [Articles](/articles/) -- Feature articles and analysis
- [Daily Briefs](/briefs/) -- Daily and weekly briefs
- [Interviews](/interviews/) -- Published interviews
- [Investigations](/investigations/) -- In-depth investigations
- [Corrections](/corrections/) -- Corrections and updates
