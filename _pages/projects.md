---
layout: page
title: 项目
permalink: /projects/
description: 当前重点展示步态解算与智能矫正系统这一项代表性项目。
nav: true
nav_order: 2
horizontal: true
---

当前项目页只保留一项主线最清晰、材料最完整的代表性项目。其他经历仍保留在首页和简历页中，项目页用于集中展示步态系统的完整逻辑。

<!-- pages/projects.md -->
<div class="projects">
{% assign selected_projects = site.projects | where: "featured_project", true | sort: "importance" %}

{% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in selected_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
{% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in selected_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
{% endif %}
</div>
