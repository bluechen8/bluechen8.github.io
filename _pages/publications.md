---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% include base_path %}

{% if page.author and site.data.authors[page.author] %}
  {% assign author = site.data.authors[page.author] %}{% else %}{% assign author = site.author %}
{% endif %}

You can also find my articles on <a href="{{author.googlescholar}}"> Google Scholar</a>.


{% include citations.html %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
