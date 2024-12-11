---
layout: page
title: Projects
order: 3
permalink: /projects/
---
# My GitHub Repositories

Here are my public repositories:

<h2>My Public Repositories</h2>
<ul>
  {% for repo in site.github.public_repositories %}
    <li>
      <a href="https://github.com/{{ repo.owner.login }}/{{ repo.name }}" target="_blank">
        {{ repo.name }}
      </a>
    </li>
  {% endfor %}
</ul>
