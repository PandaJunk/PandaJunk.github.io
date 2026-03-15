---
permalink: /zh/
title: ""
excerpt: ""
author_profile: true
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<span class='anchor' id='about-me'></span>

# 🏷 关于我
{% include_relative includes_zh/about.md %}

# 🔥 最新动态
{% include_relative includes_zh/news.md %}

# 📝 论文发表
{% include_relative includes_zh/pub.md %}

# 🎓 教育经历
{% include_relative includes_zh/edu.md %}

# 🎖 荣誉奖项
{% include_relative includes_zh/honors.md %}
