---
title: "宇树 G1 人形机器人 (23DOF教育版)"
image: "img/gallery/equipment/g1_robot.jpg"
category: "实验设备"
slug: "g1_robot"
date: 2026-01-30
---

宇树 G1 是一款23自由度的通用人形机器人教育平台，提供丰富的软硬件开发接口，适用于具身智能、强化学习和人形机器人运动控制等方向的科研与实验教学。

## 基本参数

| 参数 | 值 |
|------|-----|
| **产品名称** | Unitree G1 |
| **总自由度 (关节电机)** | 23 |
| **带电池重量** | 约 35kg |
| **高宽厚 (站立)** | 1320 × 450 × 200 mm |
| **续航时间** | 约 2 小时 |

## 关节配置 (23 DOF)

### 自由度分布

| 部位 | 自由度数 | 说明 |
|------|----------|------|
| **腿** | 6 × 2 = 12 | 左右腿各6个自由度 |
| **腰部** | 1 | 腰部yaw旋转 |
| **单臂** | 5 × 2 = 10 | 左右臂各5个自由度 |
| **单手** | 0 | 23DOF版本不带灵巧手 |
| **总计** | **23** | |

### 腿部关节 (12 DOF)

| 编号 | URDF 关节名称 | 关节中文名称 |
|------|---------------|--------------|
| 0 | left_hip_pitch_joint | 左髋关节 Pitch (前后) |
| 1 | left_hip_roll_joint | 左髋关节 Roll (内外) |
| 2 | left_hip_yaw_joint | 左髋关节 Yaw (水平) |
| 3 | left_knee_joint | 左膝关节 |
| 4 | left_ankle_pitch_joint | 左踝关节 Pitch (前后) |
| 5 | left_ankle_roll_joint | 左踝关节 Roll (内外) |
| 6 | right_hip_pitch_joint | 右髋关节 Pitch (前后) |
| 7 | right_hip_roll_joint | 右髋关节 Roll (内外) |
| 8 | right_hip_yaw_joint | 右髋关节 Yaw (水平) |
| 9 | right_knee_joint | 右膝关节 |
| 10 | right_ankle_pitch_joint | 右踝关节 Pitch (前后) |
| 11 | right_ankle_roll_joint | 右踝关节 Roll (内外) |

### 手臂关节 (10 DOF)

| 编号 | URDF 关节名称 | 关节中文名称 |
|------|---------------|--------------|
| 15 | left_shoulder_pitch_joint | 左肩关节 Pitch (前后) |
| 16 | left_shoulder_roll_joint | 左肩关节 Roll (内外) |
| 17 | left_shoulder_yaw_joint | 左肩关节 Yaw (水平) |
| 18 | left_elbow_joint | 左肘关节 |
| 19 | left_wrist_roll_joint | 左腕关节 Roll |
| 22 | right_shoulder_pitch_joint | 右肩关节 Pitch (前后) |
| 23 | right_shoulder_roll_joint | 右肩关节 Roll (内外) |
| 24 | right_shoulder_yaw_joint | 右肩关节 Yaw (水平) |
| 25 | right_elbow_joint | 右肘关节 |
| 26 | right_wrist_roll_joint | 右腕关节 Roll |

### 腰部关节 (1 DOF)

| 编号 | URDF 关节名称 | 关节中文名称 |
|------|---------------|--------------|
| 12 | waist_yaw_joint | 腰部 Yaw (水平旋转) |

## 传感器配置

### 感知传感器

| 传感器 | 说明 |
|--------|------|
| **深度相机** | 用于视觉感知和障碍物检测 |
| **3D 激光雷达 (LiDAR)** | 用于SLAM导航和环境建图 |
| **4麦克风阵列** | 用于语音交互和声源定位 |
| **5W 扬声器** | 用于音频播放和语音反馈 |

### 内部传感器

| 传感器 | 说明 |
|--------|------|
| **双编码器** | 每个关节电机配备双编码器，提高控制精度 |
| **IMU (惯性测量单元)** | 用于姿态估计和运动控制 |

### 通信模块

| 模块 | 规格 |
|------|------|
| **WiFi** | WiFi6 |
| **蓝牙** | 蓝牙 5.2 |

## 开发资源

- G1 SDK开发指南: [https://support.unitree.com/home/zh/G1_developer/about_G1](https://support.unitree.com/home/zh/G1_developer/about_G1)
- 官方开源: [https://www.unitree.com/cn/opensource](https://www.unitree.com/cn/opensource)
- **动作数据集与机器人学习**
  - [AMASS](https://amass.is.tue.mpg.de/) - 人体动作数据集
  - [Ubisoft LaForge Animation Dataset](https://github.com/ubisoft/ubisoft-laforge-animation-dataset) - Ubisoft动画数据集
  - [GMR](https://github.com/YanjieZe/GMR) - 人体数据重定向
  - [GVHMR](https://github.com/zju3dv/GVHMR) - 通过视频获取人体运动数据
  - [BeyondMimic](https://beyondmimic.github.io/) - 动作跟踪框架
  - [RoboJuDo](https://github.com/HansZ8/RoboJuDo) - 强化学习部署框架

## 快速开始

**获取URDF模型：**
```bash
git clone https://github.com/unitreerobotics/unitree_ros.git
# G1 23DOF URDF位于:
# unitree_ros/robots/g1_description_23of/g1_23dof_rev_1_0.urdf
```

**可视化模型：**
```bash
pip install mujoco
python -m mujoco.viewer
# 拖拽 g1_23dof_rev_1_0.xml 文件到查看器
```

**强化学习训练 (G1-29dof)：**
```bash
git clone https://github.com/unitreerobotics/unitree_rl_lab.git
cd unitree_rl_lab
./unitree_rl_lab.sh -t --task Unitree-G1-29dof-Velocity
```

## 演示视频

<video src="/video/dance.mp4" controls width="640"></video>

> **视频说明**: G1 机器人舞蹈演示
