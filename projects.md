---
layout: default
title: Projects
order: 3
permalink: /projects/
---
# My GitHub Repositories

Here are my public repositories:

<ul id="repo-list" style="list-style: none; padding-left: 0;"></ul>

<script>
  const username = "MatteoD00"; // ← Replace with your GitHub username
  const repoList = document.getElementById("repo-list");

  fetch(`https://api.github.com/users/${username}/repos?per_page=100`)
    .then(response => response.json())
    .then(repos => {
      // Sort repos alphabetically (case-insensitive)
      repos.sort((a, b) => a.name.toLowerCase().localeCompare(b.name.toLowerCase()));

      // Optional: filter out forks or archived repos if needed
      repos = repos.filter(repo => !repo.fork); //&& !repo.archived

      repos.forEach(repo => {
        const li = document.createElement("li");
        li.innerHTML = `<span style="margin-right: 0.5em;">📁</span>
          <a href="${repo.html_url}" target="_blank">${repo.name}</a>`;
        repoList.appendChild(li);
      });
    })
    .catch(error => {
      console.error("Error fetching repositories:", error);
      repoList.innerHTML = "<li>Error loading repositories.</li>";
    });
</script>