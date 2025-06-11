---
layout: default
title: Projects
order: 3
permalink: /projects/
---
# My GitHub Repositories

Here are my public repositories:

<ul style="list-style: none; padding-left: 0;">
  {% for repo in site.github.public_repositories %}
    <!-- {% if repo.name != "TO_SysTest" and repo.name != "InterlockBox_SummerDESY"%} -->
    <li><span style="margin-right: 0.5em;">:file_folder:</span>
      <a href="https://github.com/{{ repo.owner.login }}/{{ repo.name }}" target="_blank">
        {{ repo.name }}
      </a>
    </li>
    <!-- {% endif %} -->
  {% endfor %}
</ul>
