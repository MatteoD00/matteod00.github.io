---
layout: page
title: Projects
order: 3
permalink: /projects/
---
# My GitHub Repositories

Here are my public repositories:

<style>
  ul {
    list-style: none; /* Remove default bullets */
    padding-left: 0;  /* Optional: Align to the left */
  }
  li::before {
    content: ":file_folder:"; /* Replace bullet with emoji */
    font-size: 1.2em; /* Adjust size if needed */
    margin-right: 0.5em; /* Optional: Add spacing */
  }
</style>

<ul>
  {% for repo in site.github.public_repositories %}
    {% if repo.name != "TO_SysTest" and repo.name != "InterlockBox_SummerDESY"%}
     <li>
       <a href="https://github.com/{{ repo.owner.login }}/{{ repo.name }}" target="_blank">
         {{ repo.name }}
       </a>
     </li>
    {% endif %}
  {% endfor %}
</ul>
