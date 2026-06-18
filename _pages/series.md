---
title: "Series"
permalink: /series/
layout: single
author_profile: true
---

{% assign series_groups = site.posts | where_exp: "post", "post.series" | group_by: "series" | sort: "name" %}

{% if series_groups.size > 0 %}
{% for series in series_groups %}
## {{ series.name }}

{% assign series_posts = series.items | sort: "series_order" %}
{% for post in series_posts %}
- [{{ post.title }}]({{ post.url | relative_url }}){% if post.date %} - {{ post.date | date: "%B %-d, %Y" }}{% endif %}
{% endfor %}
{% endfor %}
{% else %}
No series yet.
{% endif %}
