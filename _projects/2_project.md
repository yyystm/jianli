---
layout: page
title: 基于 IMU 和 3D 打印的步态解算与智能矫正系统
description: 以 3D 打印机械滤波传感鞋为载体，完成嵌入式采集、BLE 传输、个性化步态解算、移动端展示与云端分析的完整系统。
img: assets/img/publication_preview/gait-shoe-graphical-abstract.png
importance: 1
category: 项目
featured_project: true
related_publications: true
---

该项目是当前阶段最核心的代表性项目，也是第一作者论文对应的系统原型，担任主要负责人。

- **项目目标：** 面向可穿戴步态分析，设计集成 IMU 的 3D 打印机械滤波传感鞋，提升信号稳定性，并实现实时、个性化步态参数估计。
- **硬件与通信：** 以 ESP32-S3 为主控，实现 IMU 数据采集与 BLE 低功耗无线传输。
- **算法方法：** 融合 ZUPT 物理模型与自监督残差网络，并结合少样本个性化校准，支持步长、足高、站立相、摆动相等 10 余项参数估计。
- **应用落地：** 基于 Flutter 开发移动端 APP，用于数据接收、结果展示与分析反馈。
- **云端部署：** 基于阿里云 ECS 搭建后端与数据库，记录步态数据，并部署模型用于身高、体重及行走地形反推。
- **阶段成果：** 第一作者论文 *3D-Printed Mechanical Filtering Shoes for Hybrid Self-Supervised Gait Analysis* 已进入 IEEE Sensors Journal 二审阶段；相关专利已提交；基于该项目的全国大学生计算机设计大赛已进入江苏省决赛。
