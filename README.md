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

This project explores dual-arm robotic manipulation of flexible objects such as plastic bags. It combines **Transformer-based imitation learning**, computer vision, and visual servoing in an unfolding-to-grasping workflow.

本项目探索双机械臂对塑料袋等柔性物体的操作，将**基于 Transformer 的模仿学习**、计算机视觉与视觉伺服结合到“展开-抓取”流程中。

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

## AI Highlight | AI 技术亮点

> Built a **Transformer-based behavioral cloning policy** from expert demonstrations to learn dual-arm bag-opening and stretching trajectories.

> 基于专家示范训练 **Transformer 行为克隆策略**，学习双机械臂的开袋与拉伸轨迹。

## Highlights | 项目亮点

- Transformer-based imitation learning for dual-arm manipulation
- YOLOv8 perception and calibrated 2D-to-3D grasp localization
- Visual enhancement for reflective and low-texture objects
- Multi-stage coordination between learned motion and visual servoing

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
