---
layout: page
title: "Corrections"
permalink: /corrections/
---

Corrections and updates to previously published content. See also our [Corrections Policy](/corrections-policy/).

{% assign sorted = site.corrections | sort: "date" | reverse %}
{% for doc in sorted %}
<article class="listing-item">
  {% include badge.html type=doc.type %}
  <h3 class="listing-item__title"><a href="{{ doc.url | relative_url }}">{{ doc.title }}</a></h3>
  <div class="listing-item__meta">
    <time datetime="{{ doc.date | date_to_xmlschema }}">{{ doc.date | date: "%B %-d, %Y" }}</time>
    {% if doc.author %}<span class="metadata__separator">&middot;</span> {{ doc.author }}{% endif %}
  </div>
  {% if doc.summary %}<p class="listing-item__summary">{{ doc.summary }}</p>{% endif %}
</article>
{% endfor %}
