---
title: Stabilizing PPO via Latent-Space Regularization and KDE-Driven Exploration
title_zh: 通过潜空间正则化与KDE驱动探索稳定PPO
authors: "Meiyu Du, Yuqing Gao, Wei Wang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/9ba66d3ac2ac17a845bc563185c7e163ba858e5f.pdf"
tags: ["query:rl-control"]
score: 9.0
evidence: 通过CKA批评者约束、无翻转演员正则与KDE优势塑形稳定PPO中的演员-评论家结构，不改变网络架构
tldr: 针对PPO在神经网络逼近策略与价值函数时对训练动力学敏感的问题，提出SPPO，在保留PPO裁剪目标与网络结构的前提下，通过CKA约束评论家表征、无翻转正则化演员更新以及KDE驱动的优势塑形来稳定演员-评论家几何。理论分析表明该机制收紧了一步自举误差界并改善动作更新方向对齐。实验显示SPPO可提升连续控制任务中PPO的训练稳定性与探索效果，同时保持算法现有结构不变。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: PPO在连续控制任务中应用广泛，但神经网络逼近策略和价值函数时对训练动力学高度敏感，导致性能不稳定。
method: 提出SPPO，结合CKA表征约束、无翻转正则化方法与KDE驱动的优势塑形，稳定演员-评论家的几何结构。
result: 理论分析收紧自举误差界，改善动作更新方向对齐；实验表明增强PPO的训练稳定性和探索性能。
conclusion: SPPO作为PPO的即插即用增强，能在不改变原始目标和架构的情况下提高连续控制训练的稳健性。
---

## Abstract
Proximal Policy Optimization (PPO) is widely used in continuous-control tasks, yet its performance is often highly sensitive to training dynamics when neural networks approximate the policy and value functions. This paper introduces SPPO, a drop-in augmentation that preserves PPO’s clipped objective and network architecture while stabilizing actor-critic geometry via three mechanisms: (i) a CKA-based constraint on critic representations, (ii) a no-flip regularizer on actor updates, and (iii) KDE-driven advantage shaping. Theoretical analysis shows that these mechanisms tighten bounds on one-step bootstrapping error, improve expected directional alignment of action updates, and ensure non-decreasing occupancy mass over high-novelty regions. Experiments on standard continuous-control benchmarks demonstrate consistent gains over PPO and recent PPO stabilization methods. Ablation studies further quantify the contribution and complementary effects of each component. Additional training-dynamics analyses indicate that SPPO reduces instability and oscillations in both actor and critic updates, improving training stability and final performance.

---

## 论文详细总结（自动生成）

# 论文总结：通过潜空间正则化与KDE驱动探索稳定PPO（SPPO）

## 1. 核心问题与整体含义

- **研究背景**：Proximal Policy Optimization（PPO）是连续控制任务中最常用的强化学习算法之一，但当使用神经网络逼近策略和价值函数时，PPO 对训练动力学高度敏感，容易出现训练不稳定、性能波动大的问题。
- **核心问题**：在保持 PPO 原始裁剪目标和网络结构不变的前提下，如何提高 PPO 在连续控制任务中的训练稳定性与探索效率。
- **整体含义**：论文提出一种名为 SPPO 的即插即用增强方法，通过稳定演员-评论家（actor-critic）的几何结构来缓解 PPO 的训练不稳定性，旨在让现有 PPO 系统无需改动架构即可获得更稳健的训练表现。

## 2. 方法论

- **核心思想**：不修改 PPO 的裁剪目标函数和网络结构，而是从表征几何、更新方向一致性和探索优势三个层面施加正则化与塑形约束，从而稳定演员-评论家的学习动态。
- **三大关键技术机制**：
  1. **基于 CKA 的评论家表征约束（CKA-based constraint on critic representations）**：使用 CKA（Centered Kernel Alignment，中心核对齐）度量来约束评论家网络内部表征的变化，防止表征在训练过程中发生剧烈漂移，从而稳定价值函数的学习。
  2. **无翻转正则化器（no-flip regularizer on actor updates）**：对演员网络的更新施加约束，避免动作更新方向发生“翻转”（即大幅度反向变化），保证策略更新的方向一致性和平滑性。
  3. **KDE 驱动的优势塑形（KDE-driven advantage shaping）**：利用核密度估计（Kernel Density Estimation, KDE）识别状态空间中高新颖性（高探索价值）的区域，并据此对优势函数进行塑形，引导策略增加对这些区域的访问概率。
- **理论分析**：
  - 证明这些机制能够收紧一步自举误差（one-step bootstrapping error）的界。
  - 改善动作更新的期望方向对齐（expected directional alignment）。
  - 确保高新颖性区域上的占位质量（occupancy mass）非递减，即探索覆盖持续增强。

## 3. 实验设计

- **Benchmark**：标准连续控制基准任务（standard continuous-control benchmarks），具体环境名称在摘要中未列出，通常可能包括 MuJoCo 或类似连续动作空间环境。
- **对比方法**：
  - 原始 PPO。
  - 近期提出的 PPO 稳定化方法（recent PPO stabilization methods），具体名称未在摘要中给出。
- **实验类型**：
  - 主要性能对比实验：在多个连续控制任务上比较 SPPO 与基线方法。
  - 消融实验：量化每个机制（CKA 约束、无翻转正则化、KDE 优势塑形）的单独贡献及其互补效果。
  - 训练动力学分析：观察演员和评论家更新过程中的不稳定性和振荡情况，用于验证 SPPO 的稳定效果。

## 4. 资源与算力

- 论文摘要中**未明确说明**使用的 GPU 型号、数量、训练时长等算力信息。
- 因此无法提供具体的硬件配置或训练成本数据。若要评估实际计算开销，需要查阅论文正文或附录。

## 5. 实验数量与充分性

- **实验数量**：摘要仅概括性地提到在标准连续控制基准上开展了对比实验、消融实验和训练动力学分析，但未给出具体的任务数量、独立种子数、训练步数等细节。
- **充分性评估**：
  - 从摘要看，实验设计包含基本性能对比、消融和动态分析，结构较为完整。
  - 但缺乏具体数值、任务列表和统计显著性描述，难以判断实验覆盖面的广泛程度。例如，是否包含高维连续控制任务、是否在多个随机种子下报告均值方差等未说明。
  - **客观性**：对比对象包括原始 PPO 和近期的稳定化方法，并做了消融，整体设计较规范，但受限于摘要信息，无法评估实现细节和超参数调优的公平性。

## 6. 主要结论与发现

- SPPO 在连续控制基准任务上一致地优于原始 PPO 和近期 PPO 稳定化方法。
- 理论分析支持该方法的稳定性：收紧自举误差界、改善动作更新方向对齐、保证高新颖性区域的占位质量非递减。
- 训练动力学分析表明，SPPO 能够降低演员和评论家更新过程中的不稳定性和振荡，提升训练稳定性并改善最终性能。
- SPPO 作为 PPO 的即插即用增强，可以在不改变原始目标和架构的情况下提高连续控制训练的稳健性。

## 7. 优点

- **即插即用**：不改变 PPO 的裁剪目标与网络结构，易于集成到现有 PPO 实现中，实用性强。
- **多角度稳定**：同时从评论家表征（CKA）、演员更新方向（无翻转正则化）和探索激励（KDE）三个层面入手，覆盖了演员-评论家训练的主要不稳定来源。
- **理论支撑**：不仅给出实验验证，还提供了自举误差界、方向对齐和探索占位质量的理论分析，增强了方法的可信度。
- **机制互补**：消融实验显示三个组件具有互补效果，说明设计不是简单叠加，而是有机组合。

## 8. 不足与局限

- **实验信息不完整**：摘要中未列出具体任务名、版本、奖励设置、训练步数、随机种子数量等，实验覆盖范围难以全面评估。
- **基准范围有限**：仅提到“标准连续控制基准”，未涉及离散动作空间、真实机器人或更复杂的视觉-运动控制任务，泛化性证据不足。
- **算力成本未报告**：未说明计算资源消耗，无法判断 SPPO 在引入 CKA、KDE 等额外计算后相对 PPO 的实际训练开销增加情况。
- **超参数敏感性未讨论**：CKA 约束的权重、KDE 带宽、无翻转正则化的阈值等关键超参数如何选择、是否敏感，摘要中未提及。
- **公平性风险**：对比的“近期 PPO 稳定化方法”具体名称和基线调优程度未知，存在潜在的比较偏差。
- **应用限制**：作为依托 PPO 和连续控制场景的方法，可能不适用于离策略算法、离散动作环境或对实时性要求极高的部署场景。

（完）
