---
layout: page
title: Projects
permalink: /projects/
---
# My GitHub Repositories

Here are my public repositories:

<ul>
  {% for repo in site.github.repos %}
    <li><a href="{{ repo.html_url }}">{{ repo.name }}</a></li>
  {% endfor %}
</ul>