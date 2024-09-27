---
layout: page
title: Team
permalink: /team/
description:
nav: true
nav_order: 3
display_categories: [Principal Investigator, Pre- and PostDocs, Research Assistants]
horizontal: false
---



<!-- pages/team.md -->
<div class="team">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display team categories -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.team | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include team.liquid %}
    {% endfor %}
  </div>
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.team | sort: "importance" %}

  <!-- Generate cards for each project -->
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include team.liquid %}
    {% endfor %}
  </div>
{% endif %}
</div>
