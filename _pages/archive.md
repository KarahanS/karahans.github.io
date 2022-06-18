---
layout: page
title: archive
permalink: /archive/
description: A collection of photos taken by me or someone close to me. Some of the photos here are taken with a professional camera, others by phone.
nav: true
nav_order: 3
display_categories: 
horizontal: false 
---

<!-- pages/projects.md -->
<div class="projects" >
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized archive -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_archive = site.archive | where: "category", category -%}
  {%- assign sorted_archive = categorized_archive | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  
  <div class="container">
    <div class="row row-cols-2">
    {%- for archive in sorted_archive -%}
      {% include pictures_horizontal.html %}  <!-- pictures_horizontal.html takes archive --> 
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for archive in sorted_archive -%}
      {% include pictures.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display archive without categories -->
  {%- assign sorted_archive = site.archive | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for archive in sorted_archive -%}
      {% include pictures_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for archive in sorted_archive -%}
      {% include pictures.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
