---
layout: page
title: 项目
permalink: /projects/
description: 当前重点展示步态解算与智能矫正系统这一项代表性项目。
nav: true
nav_order: 2
---

<div class="project-showcase">
  <a class="project-showcase-media" href="{{ '/projects/2_project/' | relative_url }}" aria-label="查看步态解算与智能矫正系统项目详情">
    <img src="{{ '/assets/img/publication_preview/gait-shoe-graphical-abstract.png' | relative_url }}" alt="3D 打印传感鞋与步态解算系统示意图">
  </a>
  <div class="project-showcase-body">
    <div class="project-showcase-kicker">Representative Project</div>
    <h2>
      <a href="{{ '/projects/2_project/' | relative_url }}">基于 IMU 和 3D 打印的步态解算与智能矫正系统</a>
    </h2>
    <p>
      面向低成本可穿戴步态分析，构建“3D 打印传感鞋 + ZUPT 物理基线 + 自监督残差校准 + 移动端反馈”的系统原型，覆盖稳定采集、实时估计、个性化校准和对称性反馈等关键环节。
    </p>
    <div class="project-showcase-tags">
      <span>3D 打印传感鞋</span>
      <span>IMU 步态分析</span>
      <span>ZUPT</span>
      <span>自监督学习</span>
      <span>移动端反馈</span>
    </div>
    <div class="project-showcase-metrics" aria-label="项目关键结果">
      <div>
        <span>信号一致性 PCC</span>
        <strong>0.848 → 0.913</strong>
      </div>
      <div>
        <span>步长 MAE</span>
        <strong>2.29 cm</strong>
      </div>
      <div>
        <span>时相误差</span>
        <strong>21.30 / 21.80 ms</strong>
      </div>
    </div>
    <a class="project-showcase-link" href="{{ '/projects/2_project/' | relative_url }}">查看项目详情</a>
  </div>
</div>
