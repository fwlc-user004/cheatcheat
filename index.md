---
layout: default
title: CheatSheet - IT & Programming
---

# 📌 لیست همه‌ی CheatSheetها

{% for file in site.pages %}
{% if file.name contains ".md" and file.name != "index.md" %}
- [{{ file.title | default: file.name }}]({{ file.url }})
{% endif %}
{% endfor %}
