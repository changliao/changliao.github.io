---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% assign author = site.author %}
{% if author.googlescholar %}
  <p>You can also find my articles on <u><a href="{{author.googlescholar}}" target="_blank" rel="noopener noreferrer">my Google Scholar profile</a></u>.</p>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
