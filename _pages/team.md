---
layout: page
title: team
permalink: /team/
description: 
nav: true
nav_order: 2
display_categories: [Prinicipal Investigator, Pre- and PostDocs, Research Assistants]
horizontal: false
---

<!-- pages/teams.md -->
<div class="teams">
{% if site.enable_team_categories and page.display_categories %}
  <!-- Display categori3w -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_teams = site.teams | where: "category", category %}
  {% assign sorted_teams = categorized_teams | sort: "importance" %}
  <!-- Generate cards for each team -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for team in sorted_teams %}
      {% include teams_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for team in sorted_teams %}
      {% include teams.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display teams without categories -->

{% assign sorted_teams = site.teams | sort: "importance" %}

  <!-- Generate cards for each team -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for team in sorted_teams %}
      {% include teams_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for team in sorted_teams %}
      {% include teams.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
