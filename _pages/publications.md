---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% assign pubs = site.publications | sort: "date" | reverse %}

{% assign first_author_pubs = pubs | where: "first_author", true %}
{% assign contrib_pubs = pubs | where_exp: "p", "p.first_author != true" %}

## First-author works

{% assign first_by_year = first_author_pubs | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for year in first_by_year %}
  ### {{ year.name }}
  {% for post in year.items %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}

## Co-authored works

{% assign contrib_by_year = contrib_pubs | group_by_exp: "p", "p.date | date: '%Y'" %}
{% for year in contrib_by_year %}
  ### {{ year.name }}
  {% for post in year.items %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}