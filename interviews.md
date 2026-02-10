---
layout: page
title: "Interviews"
permalink: /interviews/
---

Published interviews with roles, stakeholders, and contributors in the Issues-FS ecosystem.

{% assign sorted = site.interviews | sort: "date" | reverse %}
{% for doc in sorted %}
### [{{ doc.title }}]({{ doc.url | relative_url }})

**{{ doc.date | date: "%B %-d, %Y" }}** | By {{ doc.author }}

{{ doc.summary }}

---
{% endfor %}
