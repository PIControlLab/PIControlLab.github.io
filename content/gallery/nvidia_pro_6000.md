---
title: "英伟达显卡 RTX PRO 6000"
image: "/img/gallery/equipment/nvidia_pro_6000.jpg"
category: "实验设备"
slug: "nvidia_pro_6000"
date: 2025-08-01  
# layout: "single-gallery"  ← 如无特殊模板，可删除
---

本工作站专为高性能 AI 训练、3D 渲染与科学计算设计，配备双 NVIDIA RTX PRO 6000 Blackwell GPU 与双路 Intel Xeon 处理器，提供强大的并行计算能力。

## 🔧 硬件配置

### 🖥️ 主板
- **型号**：Supermicro Super Server  
- **特点**：支持多 GPU、高内存带宽、企业级稳定性

### 💾 内存
- **容量**：256 GiB（32 GiB × 8）
- **型号**：MTA36ASF4G72PZ – 32GB DDR4 RDIMM（ECC）
- **规格书**：[MTA36ASF4G72PZ | DigiKey](https://www.digikey.cn/zh/htmldatasheets/production/1959036/0/0/1/mta36asf4g72pz)

### ⚙️ 处理器
- **型号**：Intel® Xeon® Platinum 8368Q × 2  
- **频率**：2.60 GHz（基础）  
- **核心/线程**：38 核 / 76 线程（每颗）

### 🎮 显卡
- **型号**：NVIDIA RTX PRO 6000 Blackwell × 2  
- **显存**：96 GB GDDR7（每卡）  
- **用途**：AI 推理、3D 渲染、实时光线追踪  
- **官方详情**：[NVIDIA RTX PRO 6000 Blackwell](https://www.nvidia.com/zh-tw/products/workstations/professional-desktop-gpus/rtx-pro-6000-family/)

### 💽 存储
- **系统盘**：1 TB WD_BLACK SN7100（NVMe SSD）  
- **数据盘**：6 TB Seagate ST6000NM019B（企业级 HDD）  
- **总容量**：7 TB  
- **硬盘链接**：
  - [WD_BLACK SN7100](https://www.westerndigital.com/)
  - [ST6000NM019B | 希捷企业官网](https://www.hchdd.net/productinfo/2988309.html)

### 🐧 操作系统
- **发行版**：Ubuntu 24.04 LTS  
- **内核**：Linux 6.x（默认）  
- **预装环境**：CUDA 12.x, Docker, ROS 2

## 📌 应用场景
- 大模型训练与微调
- 实时 3D 可视化仿真
- 计算流体力学（CFD）模拟
- 自动驾驶算法验证平台