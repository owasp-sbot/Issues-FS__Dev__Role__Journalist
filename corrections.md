---
layout: page
title: "Corrections"
permalink: /corrections/
---

Corrections and updates to previously published content.

{% assign sorted = site.corrections | sort: "date" | reverse %}
{% for doc in sorted %}
### [{{ doc.title }}]({{ doc.url | relative_url }})

**{{ doc.date | date: "%B %-d, %Y" }}** | By {{ doc.author }}

{{ doc.summary }}

---
{% endfor %}
