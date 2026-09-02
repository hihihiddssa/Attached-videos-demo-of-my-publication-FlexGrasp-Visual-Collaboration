<div align="center">

# Research on Flexible Object Grasping

### Visual Enhancement and Multi-Stage Collaboration

**A dual-arm robotic framework for unfolding and grasping reflective, low-texture flexible objects**

[![Paper](https://img.shields.io/badge/Paper-ScienceDirect-ff6c00?logo=elsevier&logoColor=white)](https://doi.org/10.1016/j.procs.2025.10.104)
[![DOI](https://img.shields.io/badge/DOI-10.1016%2Fj.procs.2025.10.104-blue)](https://doi.org/10.1016/j.procs.2025.10.104)
[![Journal](https://img.shields.io/badge/Procedia_Computer_Science-2025-2b6cb0)](https://www.sciencedirect.com/science/article/pii/S1877050925034441)
[![License](https://img.shields.io/badge/Paper-CC_BY--NC--ND_4.0-lightgrey)](https://creativecommons.org/licenses/by-nc-nd/4.0/)

**[Read the paper](https://www.sciencedirect.com/science/article/pii/S1877050925034441)** · **[DOI](https://doi.org/10.1016/j.procs.2025.10.104)**

</div>

---

## Overview | 项目简介

This work addresses the manipulation of reflective, transparent, and low-texture flexible objects such as plastic bags. The system combines a **Transformer-based behavioral cloning policy** for bag unfolding with **YOLOv8-based visual perception and 3D coordinate mapping** for grasping. A quantitative phase-transition mechanism connects the two stages and limits error accumulation.

本研究面向透明塑料袋等高反光、低纹理柔性物体的操作难题。系统在展开阶段采用**基于 Transformer 的行为克隆策略**，在抓取阶段结合 **YOLOv8 视觉检测与三维坐标映射**，并通过可量化的阶段转换机制衔接两个闭环，从而降低纯模仿学习在长任务中的累积误差。

```text
Camera observations + expert demonstrations
                    │
                    ▼
     Stage 1: Transformer behavioral cloning
           Bag opening and stretching
                    │
          Joint-state transition trigger
                    │
                    ▼
       Stage 2: YOLOv8 + visual servoing
       Detection → 2D-to-3D → grasp command
```

## What the Transformer Does | Transformer 的作用

The Transformer is used in **Stage 1 (unfolding)** as the policy backbone of a behavioral cloning model. It is trained from expert demonstrations of plastic-bag unfolding and drives the robot arms through opening and stretching trajectories. Joint-encoder feedback helps maintain a stable initial pose. Once joint-angle variation remains below the calibrated threshold, the system pauses the imitation-learning policy and hands control to the vision-guided grasping stage.

Transformer 被用于**第一阶段（展开）**，作为行为克隆策略的模型骨干。模型从塑料袋展开的专家示范数据中学习，驱动双臂执行开袋与拉伸轨迹，并结合关节编码器反馈保持稳定的初始姿态。当关节角变化持续低于标定阈值后，系统暂停模仿学习策略，将控制权交给视觉引导的抓取阶段。

> **Scope note:** The paper specifies a Transformer-based behavioral cloning policy but does not report layer counts, attention-head counts, or a detailed encoder-decoder configuration. This repository therefore describes the model only at the level supported by the publication.

## Key Contributions | 核心贡献

| Component | Contribution |
| --- | --- |
| **Multi-stage collaboration** | Decomposes the task into imitation-learning-based unfolding and vision-servoed grasping, reducing long-horizon error accumulation. |
| **Quantitative phase transition** | Uses 100 Hz joint-angle feedback and a three-level trigger to detect completion of unfolding and switch control modes. |
| **Visual enhancement** | Applies brightness/contrast adjustment, Gaussian smoothing, Canny edge detection, and morphological closing to suppress glare and strengthen structural cues. |
| **Detection and localization** | Uses YOLOv8 and calibrated 2D-to-3D coordinate mapping to generate grasp commands from the unfolded state. |

## Experimental Results | 实验结果

| Evaluation | Proposed method | Baseline | Improvement |
| --- | ---: | ---: | ---: |
| Full-task success rate | **83/100 (83%)** | Mobile ALOHA: 48/100 (48%) | **+35 percentage points** |
| Success with image preprocessing | **83/100 (83%)** | Without preprocessing: 57/100 (57%) | **+26 percentage points** |

The experiments show that separating unfolding from visually corrected grasping substantially improves task completion, while preprocessing strengthens robustness under glare and changing illumination.

实验结果表明，将展开阶段与视觉校正抓取阶段分离能够显著提升任务完成率；视觉预处理则增强了系统在反光和光照变化条件下的稳定性。

## System Setup | 系统配置

| Component | Specification |
| --- | --- |
| Robot arms | 2 × DOBOT Nova5, 6-DOF |
| Cameras | 4 × Intel RealSense D405 depth cameras |
| End effectors | Custom 3D-printed dual-finger soft-rubber grippers |
| Stage 1 policy | Transformer-based behavioral cloning |
| Stage 2 perception | YOLOv8 detection and calibrated 2D-to-3D mapping |
| Control | Position control → visual servo control |

## Demo Videos | 演示视频

### 1. Phase Transition | 阶段转换

The system detects completion of bag unfolding from joint-state feedback and switches from imitation learning to visual servoing.

https://github.com/user-attachments/assets/4603b509-eaeb-4aa5-a8ca-4bf48f7e3d74

https://github.com/user-attachments/assets/dd9c6639-5c8a-4a28-a563-27a95cc84f63

https://github.com/user-attachments/assets/b4c0b1f5-3735-443a-9ce6-d556ef0892df

### 2. Full Task: Unfolding to Placement | 完整任务流程

Dual-arm collaborative unfolding followed by vision-guided placement of an object into the bag.

https://github.com/user-attachments/assets/84d46608-2374-4f60-b5bf-87ac89c7346e

### 3. Color and Illumination Generalization | 颜色与光照泛化

Robustness tests across flexible objects with different colors and reflective appearances.

https://github.com/user-attachments/assets/7d8bd20f-4a2c-40ec-834e-5635cf33dba4

https://github.com/user-attachments/assets/3c84b179-5823-441b-bf56-33200c4242fa

### 4. Rigid-Object Generalization | 刚性物体泛化

https://github.com/user-attachments/assets/134cfb46-261f-4229-b06f-ba3fa7a28b49

### 5. Expert Demonstration Collection | 专家示范采集

Collection of high-quality demonstrations used to train the Transformer-based behavioral cloning policy.

https://github.com/user-attachments/assets/c1db5af7-147a-4636-ae44-fd71ac63577b

## Publication | 论文信息

**Cila Aga, Zhijun Cao, Junchen Chi, Jin Liu, Chaoqun Wang, Tianyu Fu, and Rui Song.**<br>
“Research On Flexible Object Grasping Method Based on Visual Enhancement and Multi-Stage Collaboration.”<br>
*Procedia Computer Science*, Volume 271, 2025, Pages 7-13.<br>
[ScienceDirect](https://www.sciencedirect.com/science/article/pii/S1877050925034441) · [DOI: 10.1016/j.procs.2025.10.104](https://doi.org/10.1016/j.procs.2025.10.104)

## Citation

```bibtex
@article{aga2025flexible,
  title   = {Research On Flexible Object Grasping Method Based on Visual Enhancement and Multi-Stage Collaboration},
  author  = {Aga, Cila and Cao, Zhijun and Chi, Junchen and Liu, Jin and Wang, Chaoqun and Fu, Tianyu and Song, Rui},
  journal = {Procedia Computer Science},
  volume  = {271},
  pages   = {7--13},
  year    = {2025},
  doi     = {10.1016/j.procs.2025.10.104}
}
```

## License

The published article is available under the [CC BY-NC-ND 4.0 license](https://creativecommons.org/licenses/by-nc-nd/4.0/). The videos in this repository remain subject to their respective ownership and usage terms.
