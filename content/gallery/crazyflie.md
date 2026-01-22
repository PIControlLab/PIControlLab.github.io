---
title: "Crazyflie 2.1+"
image: "/img/gallery/equipment/crazyflie.png"
category: "实验设备"
slug: "crazyflie"
date: 2025-05-01  
# layout: "single-gallery"  ← 如无特殊模板，可删除
---

Crazyflie2.1是一个多功能的开源微型无人机平台，能够支持从简单飞行到复杂任务的多种应用。通过与ROS2的结合，它可以实现精准的自动飞行、群体协同控制以及自主飞行任务。
## 主要特点：
- **轻量级设计**：每台无人机重约 27 克，适合多种复杂环境中的飞行实验。
- **稳定性强**：具有高精度的飞行控制系统，适合进行精密实验。
- **开源硬件和软件**：提供丰富的 API 和开发工具，能够方便地进行自定义编程。
- **扩展性强**：支持各种传感器、相机、定位模块等硬件的扩展，能够根据实际需求定制功能。
## 平台详细介绍：
该平台由Crazyflie无人机和Crazyradio无线电模块构成，无人机支持手机蓝牙遥控或上位机无线电模块控制。Crazyflie2.1通过集成IMU、气压计等机载传感器，并结合上层动捕系统的数据， 能够实时获取无人机的位姿、速度等状态信息，可以实现精确的飞行控制和姿态调整。借助CrazySwarm2与ROS 2框架，Crazyflie 2.1支持多架无人机的同步控制与协同飞行，能够根据预设任务和路径执行群体飞行操作，适用于队形飞行、灾害救援、农业监测等实验场景。通过Python脚本结合Crazyflie API，可实现无人机在不同控制层面的操作，包括飞行轨迹、位置、速度、升力及角速度等的精细控制。

<figure>
  <img src="/img/gallery/equipment/crazyflie_1.png" alt="系统组成">
  <figcaption>图1 部分系统组成</figcaption>
</figure>

<figure>
  <img src="/img/gallery/equipment/crazyflie_2.png" alt="控制框图">
  <figcaption>图2 Crazyflie控制框图</figcaption>
</figure>