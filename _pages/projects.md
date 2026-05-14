---
layout: page
title: 项目
permalink: /projects/
description: 仅保留两项最能代表当前研究与工程能力的项目。
nav: true
nav_order: 2
horizontal: true
---

目前项目页只保留两张代表性卡片。这个数量对你现在的阶段更合适：内容集中，信息密度高，也不会因为模板占位或较弱项目影响整体判断。

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
