---
layout: page
title: "Investigations"
permalink: /investigations/
---

In-depth investigations into systemic patterns and root causes across the Issues-FS ecosystem.

{% assign sorted = site.investigations | sort: "date" | reverse %}
{% for doc in sorted %}
### [{{ doc.title }}]({{ doc.url | relative_url }})

**{{ doc.date | date: "%B %-d, %Y" }}** | By {{ doc.author }}

{{ doc.summary }}

---
{% endfor %}
