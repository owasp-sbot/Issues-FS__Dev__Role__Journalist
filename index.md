---
layout: home
title: "Issues-FS News"
---

## Recent Publications

{% assign all_docs = site.articles | concat: site.daily-briefs | concat: site.interviews | concat: site.investigations | concat: site.corrections %}
{% assign sorted_docs = all_docs | sort: "date" | reverse %}

{% for doc in sorted_docs limit:20 %}
### [{{ doc.title }}]({{ doc.url | relative_url }})

**{{ doc.date | date: "%B %-d, %Y" }}** | {{ doc.collection | replace: "-", " " | capitalize }}

{{ doc.summary }}

---
{% endfor %}

## Categories

- [Articles](/articles/) -- Feature articles and analysis
- [Daily Briefs](/briefs/) -- Daily and weekly briefs
- [Interviews](/interviews/) -- Published interviews
- [Investigations](/investigations/) -- In-depth investigations
- [Corrections](/corrections/) -- Corrections and updates
