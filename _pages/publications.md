---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

You can find the full list of publications on the [google scholar page](https://scholar.google.com/citations?user=TIG3o6EAAAAJ&hl=zh-CN&oi=sra).

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
