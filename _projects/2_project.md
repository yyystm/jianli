---
layout: page
title: 基于 IMU 和 3D 打印的步态解算与智能矫正系统
description: 面向可穿戴步态分析，围绕“稳定采集、实时解算、个性化校准、对称性反馈”构建 3D 打印传感鞋与混合算法系统。
img: assets/img/publication_preview/gait-shoe-graphical-abstract.png
importance: 1
category: 项目
featured_project: true
related_publications: true
---

<div class="gait-case-study">
  <section class="gait-case-intro">
    <p class="gait-case-eyebrow">Research Prototype / Wearable Gait Analysis</p>
    <div class="gait-case-hero">
      <p class="gait-case-lead">
        该项目是第一作者论文对应的系统原型，目标是把传感鞋硬件、IMU 数据采集、物理模型解算、少样本个性化校准和移动端反馈连成一套可验证的步态分析流程。项目重点在于“硬件先提升信号质量，算法再做实时估计和个体校正”，而不是孤立展示某一个传感器或模型。
      </p>
      <figure class="gait-case-visual">
        <img src="{{ '/assets/img/publication_preview/gait-shoe-graphical-abstract.png' | relative_url }}" alt="3D 打印传感鞋与步态解算系统图">
        <figcaption>3D 打印传感鞋、IMU 采集与步态参数反馈系统示意</figcaption>
      </figure>
    </div>
    <div class="gait-evidence-strip" aria-label="项目关键指标">
      <div>
        <span>信号一致性 PCC</span>
        <strong>0.848 → 0.913</strong>
      </div>
      <div>
        <span>步长误差 MAE</span>
        <strong>2.29 cm</strong>
      </div>
      <div>
        <span>支撑相误差</span>
        <strong>21.30 ms</strong>
      </div>
      <div>
        <span>摆动相误差</span>
        <strong>21.80 ms</strong>
      </div>
    </div>
  </section>

  <section class="gait-section">
    <div class="gait-section-heading">
      <span>01</span>
      <h2>项目问题</h2>
    </div>
    <div class="gait-two-column">
      <div class="gait-panel">
        <h3>硬件侧问题</h3>
        <p>传统绑带式 IMU 容易出现安装角度不一致、传感器与足部相对滑动、高频振动残留等问题。输入信号不稳定时，后续再复杂的算法也会受到限制。</p>
      </div>
      <div class="gait-panel">
        <h3>算法侧问题</h3>
        <p>单纯物理积分方法可解释、速度快，但会出现漂移；纯深度学习方法需要较多标注数据，且不一定适合端侧实时运行。项目采用物理模型与残差学习结合的方式降低这两类风险。</p>
      </div>
    </div>
  </section>

  <section class="gait-section">
    <div class="gait-section-heading">
      <span>02</span>
      <h2>系统流程</h2>
    </div>
    <div class="gait-pipeline">
      <div>
        <span>01</span>
        <strong>传感鞋集成</strong>
        <p>IMU 节点嵌入 3D 打印鞋体，减少外挂式传感器的相对晃动。</p>
      </div>
      <div>
        <span>02</span>
        <strong>机械滤波</strong>
        <p>中底 gyroid 晶格结构缓冲高频扰动，提高跨步信号一致性。</p>
      </div>
      <div>
        <span>03</span>
        <strong>ZUPT 基线</strong>
        <p>利用零速约束获得步长、步态事件和时相参数的初始估计。</p>
      </div>
      <div>
        <span>04</span>
        <strong>残差校准</strong>
        <p>自监督预训练提取通用表征，再用少量个人数据完成个性化补偿。</p>
      </div>
      <div>
        <span>05</span>
        <strong>反馈闭环</strong>
        <p>将步态参数转化为对称性指数和鞋体设计反馈，供移动端展示。</p>
      </div>
    </div>
  </section>

  <section class="gait-section">
    <div class="gait-section-heading">
      <span>03</span>
      <h2>核心实现</h2>
    </div>
    <div class="gait-method-grid">
      <div>
        <h3>3D 打印传感鞋</h3>
        <p>传感器被固定在鞋体结构中，中底使用 gyroid 晶格承担缓冲与机械低通滤波作用。相比绑带式方案，传感器和足部的耦合更稳定，输入数据更适合后续估计。</p>
      </div>
      <div>
        <h3>ZUPT 物理估计</h3>
        <p>系统通过 IMU 姿态与运动状态识别步态周期中的关键事件，在足部短暂停止阶段引入零速约束，得到可解释、低延迟的步态参数初值。</p>
      </div>
      <div>
        <h3>自监督残差网络</h3>
        <p>网络不直接替代物理模型，而是学习物理估计与参考值之间的偏差。先用未标注数据学习通用步态表征，再冻结编码器，用少量个人数据微调回归头。</p>
      </div>
      <div>
        <h3>移动端与个性化反馈</h3>
        <p>移动端接收数据并展示步长、支撑相、摆动相等结果，同时计算左右对称性指标，为后续定制化鞋体设计提供量化依据。</p>
      </div>
    </div>
    <div class="gait-equation">
      <span>输出逻辑</span>
      <strong>最终步态参数 = ZUPT 物理估计 + 个性化残差补偿</strong>
    </div>
  </section>

  <section class="gait-section">
    <div class="gait-section-heading">
      <span>04</span>
      <h2>验证结果</h2>
    </div>
    <div class="gait-result-list">
      <p><strong>信号质量：</strong>嵌入式传感鞋提高了跨步一致性，PCC 从 0.848 提升至 0.913；频域指标显示高频残余减少，三轴平均频谱信噪指标从 3.33 dB 提升至 7.52 dB。</p>
      <p><strong>参数估计：</strong>个性化残差补偿后，步长 MAE 为 2.29 cm，支撑相和摆动相时间误差分别为 21.30 ms 和 21.80 ms。</p>
      <p><strong>系统定位：</strong>该原型适合用于低成本步态监测和个性化鞋体设计反馈，不替代临床诊断。</p>
    </div>
  </section>

  <section class="gait-section">
    <div class="gait-section-heading">
      <span>05</span>
      <h2>建议补充图片</h2>
    </div>
    <div class="gait-figure-grid">
      <div class="gait-figure-slot">
        <span>Fig. 01</span>
        <strong>系统总览</strong>
        <p>放“传感鞋采集 → 算法解算 → 移动端反馈”的整体流程图。</p>
      </div>
      <div class="gait-figure-slot">
        <span>Fig. 02</span>
        <strong>鞋体结构</strong>
        <p>放实物鞋、IMU 安装位置、gyroid 晶格和传感节点腔体。</p>
      </div>
      <div class="gait-figure-slot">
        <span>Fig. 03</span>
        <strong>信号对比</strong>
        <p>放嵌入式方案与绑带式方案的波形、频谱或关键指标图。</p>
      </div>
      <div class="gait-figure-slot">
        <span>Fig. 04</span>
        <strong>算法框架</strong>
        <p>放 ZUPT、预训练、少样本校准和残差输出之间的关系图。</p>
      </div>
      <div class="gait-figure-slot">
        <span>Fig. 05</span>
        <strong>实验采集</strong>
        <p>放行走采集场景、足迹测量或高速相机参考系统。</p>
      </div>
      <div class="gait-figure-slot">
        <span>Fig. 06</span>
        <strong>移动端反馈</strong>
        <p>放 APP 界面、对称性指数展示或鞋体设计反馈流程。</p>
      </div>
    </div>
  </section>

  <section class="gait-section">
    <div class="gait-section-heading">
      <span>06</span>
      <h2>个人负责内容</h2>
    </div>
    <ul class="gait-responsibility-list">
      <li>负责整体系统方案设计，将 3D 打印鞋体、IMU 采集、算法估计和移动端展示组织为完整原型。</li>
      <li>参与传感鞋结构设计、IMU 数据采集流程、对比实验设计和数据处理。</li>
      <li>搭建 ZUPT 物理估计与自监督残差校准流程，完成步长和步态时相参数验证。</li>
      <li>整理实验结果并完成论文写作与返修，第一作者论文已进入 IEEE Sensors Journal 二审阶段。</li>
      <li>基于该系统参加全国大学生计算机设计大赛，已进入江苏省决赛。</li>
    </ul>
  </section>
</div>
