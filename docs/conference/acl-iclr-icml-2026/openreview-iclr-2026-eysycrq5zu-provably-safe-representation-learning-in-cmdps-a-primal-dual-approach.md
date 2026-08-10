---
title: "Provably Safe Representation Learning in CMDPs: A Primal-Dual Approach"
title_zh: CMDP中可证明安全的表示学习：原始-对偶方法
authors: "Chenhao Zhou, Chao Zhang, Hanbin Zhao, Hui Qian"
date: 2025-09-16
pdf: "https://openreview.net/pdf?id=eySyCrQ5zU"
tags: ["query:rl-control"]
score: 8.0
evidence: 低秩受限MDP中原对偶安全表示学习，处理安全约束
tldr: 在低秩受限马尔可夫决策过程中，安全约束下的表示学习与策略优化一直缺乏可靠算法。该工作提出REP-PD，通过最大似然估计迭代学习低秩转移表示，并利用与无约束拉格朗日量绑定的复合Q函数指导策略更新，首次在低秩受限马尔可夫决策过程中可证明地将表示学习与策略优化结合。算法兼顾奖励最大化与安全约束，并管理软约束违反，为表示学习向安全关键应用扩展提供了安全性保证。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 表示学习在无约束马尔可夫决策过程中成功，但低秩受限情形下安全探索与约束满足仍缺乏可证明方法。
method: 提出REP-PD原对偶算法，通过最大似然估计学习低秩转移表示，并用复合Q函数引导受限策略更新。
result: 首次在低秩受限马尔可夫决策过程中可证明整合表示学习与策略优化，同时管理软约束违反。
conclusion: 为安全关键的强化学习场景提供首个可证明安全的表示学习算法，扩展了表示学习的可用范围。
---

## Abstract
We study representation learning in low-rank  Constrained Markov Decision Processes (CMDPs) with unknown dynamics, where the agent must maximize rewards under safety constraints. While representation learning has significantly advanced for unconstrained MDPs, its extension to CMDPs remains open due to the critical challenge of safe exploration under learned features, particularly concerning the management of soft constraint violation. In this work, we propose REP-PD, the first algorithm that provably integrates representation learning with policy optimization in low-rank CMDPs. By iteratively learning a low-rank transition representation via MLE and utilizing a composite Q-function tied to the unconstrained Lagrangian, REP-PD guides policy updates to balance reward maximization, exploration, and robust constraint adherence. Through this approach, REP-PD achieves a near-optimal policy with a sampling complexity bound independent of the state space dimension without prior feature knowledge. Notably, REP-PD's regret matches the lower bounds for unconstrained low-rank MDPs, achieving strong performance concerning soft constraint violation. We then consider a stronger hard constraint violation metric, where the agent must strictly satisfy constraints at all times, and propose REP-PD-hard by designing a novel policy optimization
module. Our work thus provides a robust and theoretically grounded approach to representation learning in constrained reinforcement learning, with guarantees on bounded soft and hard constraint violation.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：在**低秩受限马尔可夫决策过程（Low-rank CMDP）**中，当动力学未知时，智能体必须在满足安全约束的前提下最大化奖励。现有表示学习方法在无约束 MDP 中已取得显著进展，但将其推广到 CMDP 仍存在关键挑战：如何在**学习到的特征下进行安全探索**，以及如何管理**软约束违反（soft constraint violation）**。
- **研究动机**：
  - 表示学习能够显著提升强化学习的样本效率和泛化能力，但此前缺乏在约束场景下可证明安全且高效的算法。
  - 安全关键应用（如自动驾驶、医疗决策）要求策略在优化奖励时严格或近似满足约束，而低秩结构下的安全表示学习仍是一个开放问题。
- **整体含义**：该论文旨在填补“表示学习 + 约束满足 + 可证明保证”这一交叉空白，为低秩 CMDP 提供第一个可证明整合表示学习与策略优化的算法框架，从而将表示学习的适用范围扩展到安全敏感的强化学习场景。

---

## 2. 方法论：核心思想、关键技术细节与算法流程（文字描述）

- **核心思想**：
  - 提出 **REP-PD**（Representation learning via Primal-Dual）算法，采用**原始-对偶（Primal-Dual）**框架，在策略优化过程中将奖励最大化与安全约束纳入统一目标。
  - 通过**最大似然估计（MLE）**迭代学习低秩转移表示，并将**复合 Q 函数（composite Q-function）**与无约束拉格朗日量绑定，用于指导策略更新。

- **关键技术细节**：
  - **低秩转移表示学习**：利用 MLE 从交互数据中估计低秩动态模型的特征表示，无需预先知道特征信息。
  - **复合 Q 函数**：构造与拉格朗日函数相关的 Q 函数，同时编码奖励和约束信息，从而在策略改进时平衡奖励最大化、探索与约束鲁棒性。
  - **原对偶更新**：原始变量更新策略，对偶变量（拉格朗日乘子）更新约束惩罚强度，动态调整以满足安全约束。
  - **软约束违反管理**：算法允许一定量的约束违反（软约束），并给出违反上界。
  - **硬约束违反处理**：进一步提出 **REP-PD-hard** 变体，通过设计新的策略优化模块，使智能体在**所有时刻**严格满足约束（硬约束）。

- **算法流程（文字说明）**：
  1. 初始化：随机初始化策略、拉格朗日乘子和特征表示。
  2. 迭代循环：
     - 与环境交互，收集转移样本；
     - 使用 MLE 更新低秩转移表示；
     - 基于当前表示构造复合 Q 函数；
     - 执行原始-对偶更新：策略向最大化拉格朗日目标方向移动，乘子向约束违反惩罚增大方向移动；
     - 根据算法变体（软/硬约束）进行策略投影或修正，保证约束满足。
  3. 输出：近最优策略。

---

## 3. 实验设计

- **注意**：在提供的论文提取文本中，**未包含具体的实验章节**（数据集、场景、基准（benchmark）和对比方法均未详细列出）。
- 从摘要和元数据推测，可能的实验设计方向包括：
  - **环境**：可能采用低秩 MDP 的合成环境或标准受限 RL 基准（如安全 gym 环境、随机低秩 CMDP 实例）。
  - **对比方法**：可能包括无约束 low-rank MDP 算法（如 REP-LSB 等）、其他 CMDP 算法（如基于模型或基于表格式的原对偶方法）以及无表示学习的基线。
  - **评估指标**：奖励（regret）、软约束违反、硬约束违反、样本复杂度等。
- **结论**：由于文本未提供实验细节，无法给出具体的 benchmark 和对比方法列表。若有需要，应查阅论文全文实验部分。

---

## 4. 资源与算力

- 论文提供内容中**未提及任何算力相关信息**，例如 GPU 型号、数量、训练时长、内存消耗等。
- 也未说明是否使用分布式训练或具体硬件平台。
- 因此，无法评估实验的可复现资源和计算成本。

---

## 5. 实验数量与充分性

- 由于提取文本缺少实验章节，无法判断实验的**组数**、**消融实验**、**多环境验证**等内容。
- 从理论贡献看，摘要给出了**样本复杂度界**和**遗憾界**，说明作者可能重点依靠理论分析而非大量实验对比来支撑结论。
- **充分性评价**：
  - 如果论文仅提供理论保证而未进行广泛实验，则实验充分性可能不足，尤其是在验证“可证明安全”在真实或模拟环境中的实际表现方面。
  - 但若实验章节在原文中存在，则需阅读原文判断其是否覆盖了不同维度、约束类型、表示学习困难度等。
- 总体上，基于当前信息，无法确认实验是否客观公平；建议审阅原文实验部分。

---

## 6. 主要结论与发现

- **主要贡献**：
  - 提出 **REP-PD**，是**首个**在低秩 CMDP 中可证明地整合表示学习与策略优化的算法。
  - 通过 MLE 学习低秩表示，无需先验特征知识即可达到**与状态空间维度无关**的样本复杂度。
  - **遗憾界匹配无约束低秩 MDP 的下界**，表明在安全约束下仍能保持与无约束场景同阶的强性能。
  - 能同时提供**软约束违反**和**硬约束违反**的有界保证。
- **理论意义**：表明在约束场景下，表示学习的优势（降维、避免维度灾难）依然可以被保留，且安全性不牺牲最优性。
- **实际意义**：为安全关键的强化学习应用（如机器人、自动驾驶）提供了理论上有保障的表示学习算法基础。

---

## 7. 优点

- **理论创新性强**：首次在低秩 CMDP 中统一表示学习与受限策略优化，填补了该方向空白。
- **可证明保证**：提供采样复杂度、遗憾界以及软/硬约束违反的明确上界，不是启发式方法。
- **无需先验特征**：依赖 MLE 自动学习低秩表示，避免对特征工程的需求，更具通用性。
- **遗憾匹配无约束下界**：说明增加约束条件并未导致明显的额外 regret 代价，理论上非常优雅。
- **软/硬约束双变体**：同时覆盖两种常见安全设定，增强了方法的适用性。

---

## 8. 不足与局限

- **实验信息缺失**：根据提供的文本，无法评估实验的规模和有效性，缺乏与现有基线在真实基准上的对比证据。
- **理论假设较强**：低秩 MDP 假设本身是较强的结构假设，在实际高维复杂环境中低秩性未必成立，算法迁移性可能受限。
- **软约束违反的“软”性**：虽然提供了违反上界，但仍允许一定程度的违反，并非真正的安全；对于严格禁止违反的应用需要依赖 REP-PD-hard，但硬约束变体的计算复杂度和适用条件未在摘要中详述。
- **泛化性未验证**：未讨论对部分可观测、非平稳或大状态空间环境的扩展。
- **可复现性风险**：未给出算法超参数选择、具体实现细节和算力资源，可能影响实际复现。

---

## 9. 总结

该论文提出了 REP-PD 和 REP-PD-hard，在低秩 CMDP 中首次实现了可证明安全的表示学习与策略优化，理论贡献突出，遗憾界与无约束情形下界匹配。但在给定材料中缺乏实验部分和算力信息，限制了对其实际有效性的全面评估。未来可关注其能否在更复杂、非低秩的真实世界中保持安全与高效。

（完）
