---
layout: page
permalink: /repositories/
title: repositories
description: GitHub profile and selected open-source repositories, including the GGenemy R package, overdose risk prediction models, and federated learning demos.
nav: true
nav_order: 6
---

{% if site.data.repositories.github_users %}

## GitHub users

{% comment %}
Inline the profile stats card so we can pass owner_affiliation:
the include only emits fixed params, and counting COLLABORATOR /
ORGANIZATION_MEMBER repos reflects org work (UBC-MDS, UBC-DSCI).
Keep in sync with al-org-dev/al-folio-core \_includes/repository/repo_user.liquid.
{% endcomment %}
{% assign stats_url = site.external_services.github_readme_stats_url | default: 'https://github-stats-extended.vercel.app' %}
{% assign lang = site.lang | split: '-' | first %}

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    <div class="repo p-2 text-center">
      <a href="https://github.com/{{ user }}">
        <img
          class="only-light w-100"
          alt="{{ user }}"
          src="{{ stats_url }}/api/?username={{ user }}&theme=transparent&locale={{ lang }}&show_icons=true&rank_icon=github&include_all_commits=true&owner_affiliation=OWNER,COLLABORATOR,ORGANIZATION_MEMBER"
          onerror="this.closest('.repo').style.display='none'"
        >
        <img
          class="only-dark w-100"
          alt="{{ user }}"
          src="{{ stats_url }}/api/?username={{ user }}&theme=dark&locale={{ lang }}&show_icons=true&rank_icon=github&include_all_commits=true&owner_affiliation=OWNER,COLLABORATOR,ORGANIZATION_MEMBER"
          onerror="this.closest('.repo').style.display='none'"
        >
      </a>
    </div>
  {% endfor %}
</div>

---

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}

  <h4>{{ user }}</h4>
  {% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% include repository/repo_trophies.liquid username=user %}
  </div>

---

{% endfor %}
{% endif %}
{% endif %}

{% if site.data.repositories.github_repos %}

## GitHub Repositories

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.liquid repository=repo %}
  {% endfor %}
</div>
{% endif %}
