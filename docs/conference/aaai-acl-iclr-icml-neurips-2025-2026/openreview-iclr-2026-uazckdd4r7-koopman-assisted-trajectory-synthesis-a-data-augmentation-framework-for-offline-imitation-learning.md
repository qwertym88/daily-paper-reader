---
title: "Koopman-Assisted Trajectory Synthesis: A Data Augmentation Framework for Offline Imitation Learning"
title_zh: Koopman辅助轨迹合成：面向离线模仿学习的数据增广框架
authors: "Jin Wang, Pengcheng He, Ke Jiang, Xiaoyang Tan"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=UAZCKdd4R7"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 面向离线模仿学习的Koopman轨迹合成
tldr: 离线模仿学习中数据增广对缓解协变量偏移至关重要，但单步方法常违反系统动力学，轨迹级方法又受累积误差与可扩展性困扰，已有Koopman方法多停留在单步层面。本文提出KATS，一种轨迹级Koopman辅助数据增广框架，通过Koopman算子生成完整多步轨迹，规避动作等变要求带来的计算瓶颈与近似误差。实验表明该方法能有效提升离线模仿学习性能，为结合Koopman表示与序列级数据生成提供了新途径。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 离线模仿学习的单步增广违反动力学，轨迹级方法受累积误差与可扩展性限制。
method: 提出KATS，用Koopman算子在轨迹级生成完整多步轨迹以增广数据。
result: 规避动作等变瓶颈与近似误差，提升离线模仿学习效果。
conclusion: 为Koopman表示与序列级数据生成结合提供了新途径。
---

## Abstract
Data augmentation plays a pivotal role in offline imitation learning (IL) by alleviating covariate shift, yet existing methods remain constrained. Single-step techniques frequently violate underlying system dynamics, whereas trajectory-level approaches are plagued by compounding errors or scalability limitations. Even recent Koopman-based methods typically function at the single-step level, encountering computational bottlenecks due to action-equivariance requirements and vulnerability to approximation errors. To overcome these challenges, we introduce Koopman-Assisted Trajectory Synthesis (KATS), a novel framework for generating complete, multi-step trajectories. By operating at the trajectory level, KATS effectively mitigates compounding errors. It leverages a state-equivariant assumption to ensure computational efficiency and scalability, while incorporating a refined generator matrix to bolster robustness against Koopman approximation errors. This approach enables a more direct and efficacious mechanism for distribution matching in offline IL. Extensive experiments demonstrate that KATS substantially enhances policy performance and achieves state-of-the-art (SOTA) results, especially in demanding scenarios with narrow expert data distributions.

---

## 论文详细总结（自动生成）

> 说明：提供的 PDF 提取文本实际为 OpenReview 人机验证页，未包含论文正文；以下总结主要依据元数据中的标题、摘要与 TL;DR，因此实验细节、算力与公式等内容无法完整核验。

## 1. 论文的核心问题与整体含义

- **研究背景**：离线模仿学习（Offline IL）中，数据增广对缓解协变量偏移（covariate shift）至关重要。
- **核心问题**：
  - 单步数据增广方法常违反系统底层动力学。
  - 轨迹级增广方法又容易受到累积误差与可扩展性限制。
  - 近期 Koopman 方法多停留在单步层面，存在动作等变（action-equivariance）要求导致的计算瓶颈，并且对 Koopman 近似误差较敏感。
- **整体含义**：论文提出 **KATS（Koopman-Assisted Trajectory Synthesis）**，一种轨迹级、Koopman 辅助的数据增广框架，通过生成完整多步轨迹来提升离线模仿学习性能，并为 Koopman 表示与序列级数据生成结合提供新途径。

## 2. 论文提出的方法论

- **核心思想**：
  - 在**轨迹级**而非单步级使用 Koopman 算子生成完整多步轨迹。
  - 通过轨迹级生成缓解单步拼接或单步增广带来的复合误差问题。
- **关键技术细节**：
  - 采用**状态等变假设（state-equivariant assumption）**，以提升计算效率与可扩展性。
  - 引入**精化生成矩阵（refined generator matrix）**，增强方法对 Koopman 近似误差的鲁棒性。
  - 规避了已有 Koopman 方法中动作等变要求带来的计算瓶颈与近似误差。
- **算法流程（依据摘要概括）**：
  1. 构建或利用 Koopman 表示来刻画系统动力学。
  2. 基于状态等变假设与精化生成矩阵生成完整多步轨迹。
  3. 将合成轨迹用于离线模仿学习的数据增广。
  4. 通过更直接、有效的机制进行分布匹配，从而提升策略学习效果。
- **公式与实现细节**：提供的文本未给出具体公式、算法伪代码或网络结构，无法进一步展开。

## 3. 实验设计

- **数据集 / 场景**：
  - 摘要仅称在“demanding scenarios with narrow expert data distributions”（专家数据分布狭窄的苛刻场景）中表现突出。
  - 未提供具体数据集名称、环境类型或 benchmark 名称。
- **Benchmark**：
  - 未在提供文本中明确说明。
- **对比方法**：
  - 摘要中概念性对比了：
    - 单步数据增广技术；
    - 轨迹级方法；
    - 近期 Koopman-based 方法。
  - 但未列出具体基线方法名称。
- **评价指标**：
  - 主要提及策略性能（policy performance），并声称达到 SOTA。
  - 未给出具体指标、统计方式或实验协议。

## 4. 资源与算力

- 提供的摘要与元数据中**未提及**：
  - GPU 型号与数量；
  - 训练时长；
  - 参数量、环境步数或总算力消耗。
- 因此无法总结算力资源使用情况。

## 5. 实验数量与充分性

- 摘要称进行了“extensive experiments”，但未说明：
  - 使用了多少个数据集或任务；
  - 做了多少组对比实验；
  - 是否包含消融实验；
  - 是否报告随机种子、置信区间或统计显著性。
- 从现有信息看，**无法判断实验是否充分、客观、公平**。
- 若要评估充分性，需要查看正文中：
  - 基线是否公平调参；
  - 是否验证状态等变假设与精化生成矩阵的贡献；
  - 是否覆盖不同专家数据分布、不同动力学复杂度和不同离线 IL 算法。

## 6. 论文的主要结论与发现

- KATS 能在轨迹级生成完整多步轨迹，从而有效缓解复合误差。
- 通过状态等变假设，方法具备较好的计算效率与可扩展性。
- 通过精化生成矩阵，方法对 Koopman 近似误差更具鲁棒性。
- 实验表明 KATS 能显著提升离线模仿学习策略性能，并达到 SOTA，尤其在专家数据分布狭窄的场景中表现突出。
- 该工作为 Koopman 表示与序列级数据生成相结合提供了新方向。

## 7. 优点

- **问题定位清晰**：明确指出现有单步增广、轨迹级增广和 Koopman 方法的各自瓶颈。
- **方法思路有针对性**：以轨迹级生成替代单步生成，直接针对复合误差和协变量偏移。
- **兼顾效率与鲁棒性**：状态等变假设提升可扩展性，精化生成矩阵增强抗近似误差能力。
- **应用场景有价值**：强调专家数据分布狭窄的困难场景，贴近实际离线模仿学习需求。
- **据元数据**：该论文被 ICLR 2026 接收，评分为 8.0，说明具有一定认可度。

## 8. 不足与局限

- **正文不可核验**：提供的 PDF 提取文本仅为 OpenReview 验证页，无法确认公式、算法和实验细节。
- **实验信息缺失**：未说明数据集、benchmark、基线、指标、实验组数和算力，难以评估可复现性与公平性。
- **潜在方法限制**：
  - 依赖 Koopman 表示质量，对强非线性、高维或非平稳系统的适用性需验证。
  - 状态等变假设可能限制适用范围。
  - 精化生成矩阵对近似误差的鲁棒性需要正文实验与理论支撑。
- **偏差风险**：摘要可能选择性强调有利结果，缺少失败案例、负结果或边界条件讨论。
- **应用限制**：轨迹级合成可能带来额外计算开销；在真实系统或安全关键场景中，合成数据偏差是否可控尚不明确。

（完）
