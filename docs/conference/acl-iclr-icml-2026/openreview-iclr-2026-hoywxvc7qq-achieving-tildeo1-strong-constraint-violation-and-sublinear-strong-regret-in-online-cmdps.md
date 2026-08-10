---
title: "Achieving $\\tilde{O}(1)$ Strong Constraint Violation and Sublinear Strong Regret in Online CMDPs"
title_zh: 在线约束马尔可夫决策过程中的强约束违反与强遗憾的最优界限
authors: "Qian Zuo, Zhiyong Wang, Fengxiang He"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=hOywXVc7Qq"
tags: ["query:rl-control"]
score: 9.0
evidence: 提出FlexDOME算法，在线CMDP中实现近常数强约束违反与亚线性强遗憾。
tldr: 在线CMDP中，现有算法虽能实现亚线性强遗憾，但累计强约束违反会随回合数增长。本文提出FlexDOME算法，基于正则化原始-对偶框架并在约束阈值上引入衰减安全边际。理论上首次实现近常数O~(1)强约束违反和亚线性O~(T^(7/8))强遗憾。该结果为在线安全强化学习在硬约束衡量下提供了可证明的更优保证。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 在线CMDP中，已有亚线性遗憾算法的累计强约束违反随回合数增长，难以满足硬安全需求。
method: 提出FlexDOME，基于正则化原始-对偶框架，在约束阈值上加入衰减安全边际以同时优化遗憾和违反。
result: 理论上首次达到近常数强约束违反和亚线性强遗憾，显著优于现有在线CMDP方法。
conclusion: 为在线安全RL提供新的可证明边界，强化了硬约束场景下的安全性保证。
---

## Abstract
We study safe online reinforcement learning in Constrained Markov Decision Processes (CMDPs) under strong regret and violation metrics. Existing methods that achieve sublinear strong reward regret inevitably incur cumulative strong constraint violation that grows with the number of episodes $T$. To address this limitation, we propose Flexible safety Domain Optimization via Margin-regularized Exploration (FlexDOME), the first algorithm in the literature that provably achieves near-constant $\tilde{O}(1)$ strong constraint violation and ensures a sublinear $\tilde{O}(T^{7/8})$ strong reward regret. FlexDOME, built on the regularized primal-dual framework, introduces a decaying safety margin to the constraint threshold. This margin tightens the feasible region to avoid constraint violation, which relaxes in order $\tilde{O}(t^{-1/8})$ to guarantee feasibility, offering a proper safety-performance trade-off. We then propose a policy-dual divergence potential function that helps establish a non-asymptotic last-iterate convergence guarantee. Experiments demonstrate that FlexDOME significantly enhances safety with negligible reward sacrifice, in full agreement with the theory.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究背景**：在线安全强化学习（safe online RL）中，约束马尔可夫决策过程（CMDP）是核心建模框架。已有工作通常关注**强遗憾（strong reward regret）**和**强约束违反（strong constraint violation）**两类指标。
- **核心问题**：现有能在强遗憾指标下达到亚线性（sublinear）界限的算法，其累计强约束违反会随回合数 $T$ 增长。这意味着在需要硬安全保证的场景（如机器人控制、自动驾驶）中，算法无法保证长期安全。
- **研究目标**：设计一种算法，首次在理论上同时实现：
  - 近常数强约束违反：$\tilde{O}(1)$（不随 $T$ 增长或增长极慢）
  - 亚线性强遗憾：$\tilde{O}(T^{7/8})$
- **整体意义**：该工作为在线CMDP在硬约束衡量下提供了首个可证明的“安全-性能”双优保证，弥补了现有理论空白，推动了安全强化学习在真实高风险场景中的应用基础。

## 2. 论文提出的方法论

- **算法名称**：FlexDOME（Flexible safety Domain Optimization via Margin-regularized Exploration）
- **核心思想**：基于**正则化原始-对偶框架（regularized primal-dual framework）**，在约束阈值上引入一个**衰减安全边际（decaying safety margin）**。
- **关键技术细节**：
  - 安全边际会**收紧可行域**，使算法在学习初期更保守，从而减少约束违反。
  - 边际随时间按 $\tilde{O}(t^{-1/8})$ 的速率衰减，逐渐放松约束，保证长期可行性与奖励优化之间取得平衡。
  - 提出一种**策略-对偶散度势函数（policy-dual divergence potential function）**，用于建立非渐近的**最后迭代收敛保证（last-iterate convergence guarantee）**，而非仅保证平均迭代收敛。
- **算法流程（文字概述）**：
  1. 在每回合内，基于当前策略和对偶变量更新原始变量（策略），并引入正则化项控制探索。
  2. 在约束阈值中加入当前回合的衰减安全边际，更新对偶变量。
  3. 利用策略-对偶散度势函数分析迭代轨迹，证明最后迭代的策略满足约束和奖励界。
- **理论结果**：在标准CMDP假设下，证明强约束违反为 $\tilde{O}(1)$，强遗憾为 $\tilde{O}(T^{7/8})$。

## 3. 实验设计

- **实验场景/数据集**：论文摘要中仅提及“Experiments demonstrate...”，**未给出具体环境名称、数据集或任务类型**。根据领域惯例，可能涉及经典CMDP benchmark（如安全 Gym、Safety Gym、网格世界等），但文本中无详细信息。
- **Benchmark 与对比方法**：摘要中未列出具体对比算法，但从问题背景推断，应与已有的在线CMDP亚线性遗憾算法（如基于原始-对偶或乐观优化的方法）进行对比。
- **对比指标**：强约束违反量、强奖励遗憾、奖励代价权衡。

## 4. 资源与算力

- 论文提供的文本中**未明确提及任何算力资源**，包括 GPU 型号、数量、训练时长、TPU、集群规模等。
- 因此无法从现有内容总结具体计算开销，只能指出该论文未报告资源细节。

## 5. 实验数量与充分性

- **实验数量**：摘要中仅提到“Experiments demonstrate...”，没有说明具体进行了多少组实验（如几个环境、几组超参数、是否包含消融实验）。
- **充分性评估**：
  - 从文本看，实验证据较简略，缺少复现所需的关键细节（环境设置、baseline配置、随机种子数、标准差等）。
  - 虽然结论与理论一致，但实验覆盖面和可复现性信息不足，难以独立评判其充分性和公平性。
  - 未提及消融实验（如安全边际衰减速率的影响、正则化参数敏感性等），因此不能判断方法各组件贡献。

## 6. 论文的主要结论与发现

- 首次提出并证明了**近常数强约束违反**（$\tilde{O}(1)$）与**亚线性强遗憾**（$\tilde{O}(T^{7/8})$）可以同时实现，突破了现有算法“遗憾亚线性但违反随 $T$ 增长”的限制。
- 衰减安全边际是实现安全-性能折中的关键机制：先收紧可行域避免初期违反，再逐步放松以保证长期最优性。
- 策略-对偶散度势函数提供了最后迭代收敛的强保证，算法在实际中显著提升安全性，且奖励牺牲可忽略不计。

## 7. 优点

- **理论贡献新颖**：首次达到 $\tilde{O}(1)$ 强约束违反，是安全RL理论的重要突破。
- **方法设计巧妙**：衰减安全边际简单而有效，在原始-对偶框架中直接嵌入安全先验；势函数分析支持最后迭代收敛，实用性强。
- **安全-性能权衡清晰**：理论界限明确展示两个指标的可调关系（边际衰减速率决定违反与遗憾的折中）。
- **实验结论与理论一致**：虽然细节缺失，但至少说明方法在实践中的有效性。

## 8. 不足与局限

- **实验描述过于简略**：未提供环境、基准方法、参数设置、重复实验等细节，降低了可复现性和说服力。
- **缺少消融研究**：无法验证安全边际衰减、正则化项、势函数等各组件对结果的独立贡献。
- **未报告资源与计算成本**：在部署层面缺乏参考。
- **理论假设可能较强**：文中未列出CMDP的具体假设（如遍历性、奖励有界性、约束结构等），因此适用范围有待明确。
- **仅关注强指标**：未讨论与弱指标（如累计约束违反）的对比，也未分析在实际高维连续控制中的拓展性。

（完）
