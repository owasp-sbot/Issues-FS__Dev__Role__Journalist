---
layout: page
title: "Daily Briefs"
permalink: /briefs/
---

Daily and weekly briefs from the Issues-FS ecosystem.

{% assign sorted = site.daily-briefs | sort: "date" | reverse %}
{% for doc in sorted %}
### [{{ doc.title }}]({{ doc.url | relative_url }})

**{{ doc.date | date: "%B %-d, %Y" }}** | By {{ doc.author }}

{{ doc.summary }}

---
{% endfor %}
