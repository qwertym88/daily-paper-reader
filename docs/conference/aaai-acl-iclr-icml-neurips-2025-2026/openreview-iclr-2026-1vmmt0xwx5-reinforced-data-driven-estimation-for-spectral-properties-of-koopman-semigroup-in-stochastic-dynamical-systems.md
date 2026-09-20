---
title: Reinforced Data-Driven Estimation for Spectral Properties of Koopman Semigroup in Stochastic Dynamical Systems
title_zh: 随机动力系统中Koopman半群谱性质的强化数据驱动估计
authors: "Yuanchao Xu, Jing Liu, Zhongwei Shen, Isao Ishikawa"
date: 2025-09-07
pdf: "https://openreview.net/pdf?id=1VMmT0xwX5"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 用强化学习引导Koopman谱估计的数据采样
tldr: 数据驱动的Koopman谱估计方法（如EDMD）精度高度依赖采样轨迹的质量与位置，在随机系统中尤为脆弱。本文提出强化随机动态模式分解，将最优采样策略建模为强化学习问题，由智能体学习在何处采集数据。该方法自动引导数据收集，提升了随机动力系统中Koopman半群谱性质的估计精度，为Koopman理论与强化学习的结合提供了新思路。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: EDMD等数据驱动Koopman谱估计精度高度依赖采样轨迹的质量与位置。
method: 提出强化随机动态模式分解，将最优采样策略建模为强化学习问题由智能体学习。
result: 自动引导数据采集，提升随机动力系统中Koopman半群谱性质的估计精度。
conclusion: 为Koopman谱估计与强化学习结合提供了自动数据采集框架。
---

## Abstract
Analyzing the spectral properties of the Koopman operator is crucial for understanding and predicting the behavior of complex stochastic dynamical systems. However, the accuracy of data-driven estimation methods, such as Extended Dynamic Mode Decomposition (EDMD) and its variants, are heavily dependent on the quality and location of the sampled trajectory data. This paper introduces a novel framework, Reinforced Stochastic Dynamic Mode Decomposition, which integrates Reinforcement Learning (RL) with Stochastic Dynamic Mode Decomposition (SDMD) to automatically guide the data collection process in stochastic dynamical systems. We frame the optimal sampling strategy as an RL problem, where an agent learns a policy to select trajectory initial conditions. The agent is guided by a reward signal based on \emph{spectral consistency}, that is a measure of how well the estimated Koopman eigenpairs describe the system's evolution balanced with an exploration bonus to ensure comprehensive coverage of the state space. We demonstrate the effectiveness of our approach using Bandit algorithm, Deep Q-Network (DQN), and Proximal Policy Optimization (PPO) algorithms on canonical systems including the double-well potential, the stochastic Duffing oscillator and the FitzHugh-Nagumo model. Our results show that the RL agent automatically discovers dynamically significant regions without any prior knowledge of the system. Rigorous theoretical analysis establishes convergence guarantees for the proposed algorithms, directly linking the final estimation accuracy to the quality of the learned sampling policy. Our work presents a robust, automated methodology for the efficient spectral analysis of complex stochastic systems.

---

## 论文详细总结（自动生成）

> 说明：OpenReview PDF 提取文本仅显示 CAPTCHA 验证页，未包含论文正文；以下总结主要依据摘要与元数据，涉及实验细节、算力、消融等未在可用文本中明确说明。

## 1. 核心问题与整体含义

- **研究背景**：Koopman 算子/半群的谱性质对理解和预测复杂随机动力系统行为至关重要。
- **核心问题**：数据驱动估计方法，如扩展动态模式分解（EDMD）及其变体，其精度高度依赖采样轨迹的质量与位置；在随机系统中，这种依赖尤为脆弱。
- **整体含义**：论文试图将强化学习（RL）与随机动态模式分解（SDMD）结合，自动引导数据采集，从而提升随机动力系统中 Koopman 半群谱性质的估计精度，并为 Koopman 理论与 RL 的结合提供新思路。

## 2. 方法论

- **核心思想**：将“最优采样策略”建模为强化学习问题，由智能体学习在何处采集数据，即选择轨迹初始条件，以服务后续 Koopman 谱估计。
- **框架名称**：Reinforced Stochastic Dynamic Mode Decomposition，即强化随机动态模式分解，整合 RL 与 SDMD。
- **关键机制**：
  - 智能体根据策略选择轨迹初始条件；
  - 系统采集轨迹数据后，用 SDMD 类方法估计 Koopman 特征对/谱性质；
  - 奖励信号基于 **spectral consistency**，衡量估计的 Koopman 特征对描述系统演化的程度；
  - 同时加入 **exploration bonus**，以确保状态空间覆盖充分。
- **算法流程（文字说明）**：
  1. 初始化估计与采样策略；
  2. 智能体选择轨迹初始条件；
  3. 在随机动力系统中采集轨迹；
  4. 使用 SDMD 估计 Koopman 谱/特征对；
  5. 根据谱一致性与探索奖励计算回报；
  6. 更新 RL 策略；
  7. 迭代上述过程，直至估计精度或策略收敛。
- **理论部分**：论文声称建立收敛保证，并将最终估计精度与学习到的采样策略质量直接联系起来。
- **实验中使用算法**：Bandit 算法、Deep Q-Network（DQN）、Proximal Policy Optimization（PPO）。

## 3. 实验设计

- **使用场景/系统**：不是传统静态数据集，而是典型随机动力系统，包括：
  - double-well potential；
  - stochastic Duffing oscillator；
  - FitzHugh-Nagumo model。
- **Benchmark**：可用文本未明确给出标准 benchmark 名称；从研究动机看，基准应是这些系统上的 Koopman 谱估计精度，或与 EDMD/SDMD 及其变体的估计表现比较。
- **对比方法**：摘要明确提到使用 Bandit、DQN、PPO 三种 RL 算法来学习采样策略；是否与固定采样、随机采样或其他 EDMD/SDMD 变体进行严格对照，摘要未明确说明。
- **评价目标**：验证 RL 智能体能否在无系统先验知识下自动发现动态显著区域，并提升谱性质估计精度。

## 4. 资源与算力

- 提供的摘要和元数据中**未提及** GPU 型号、数量、训练时长、并行规模或具体计算资源。
- 因此无法判断该工作的算力消耗与可复现成本；需查阅论文全文或附录确认。

## 5. 实验数量与充分性

- 从摘要可推断，至少覆盖 **3 个随机动力系统 × 3 种 RL 算法**，即约 9 组主要实验配置。
- 是否包含消融实验、不同采样预算、不同噪声水平、不同网络结构、重复实验与统计显著性检验，摘要未说明。
- **充分性**：若仅限低维典型系统，能说明方法在概念上有效，但不足以证明高维、真实数据或大规模应用的可扩展性。
- **客观与公平性**：由于全文不可用，无法确认基线设置、超参数调优、评价指标和计算预算是否公平；目前只能认为实验设计方向合理，但公平性需全文验证。

## 6. 主要结论与发现

- RL 智能体能够在没有系统先验知识的情况下，自动发现对 Koopman 谱估计更重要的动态区域。
- 所提方法提升了随机动力系统中 Koopman 半群谱性质的估计精度。
- 理论分析给出了收敛保证，并表明最终估计精度与学习到的采样策略质量直接相关。
- 该工作提供了一个自动数据采集框架，将 Koopman 谱分析与强化学习结合，面向复杂随机系统的谱分析。

## 7. 优点

- **交叉创新**：将 RL 用于 Koopman 谱估计的数据采样，而非仅用于控制或决策，思路新颖。
- **奖励设计有针对性**：谱一致性奖励直接服务估计质量，探索奖励兼顾状态空间覆盖。
- **多算法验证**：同时尝试 Bandit、DQN、PPO，增强方法通用性说明。
- **理论支撑**：提供收敛保证，并建立估计精度与采样策略质量之间的联系。
- **自动化与无先验**：智能体可自动发现动态显著区域，减少人工设计采样策略的需求。

## 8. 不足与局限

- **全文不可用**：PDF 提取文本为验证页，导致无法核实正文中的公式、定理假设、实验细节与附录。
- **实验覆盖有限**：目前可见实验集中在低维典型随机系统，尚未展示高维系统、真实数据或复杂工程场景。
- **算力与复现信息缺失**：未提及 GPU、训练时长、代码与超参数，复现成本不明确。
- **基线与消融不明确**：是否公平对比 EDMD/SDMD 变体、是否进行充分消融和统计检验，摘要未说明。
- **方法限制**：RL 采样可能带来额外训练成本；谱一致性奖励与探索 bonus 的平衡可能需要调参；理论收敛条件可能较严格。
- **应用限制**：在随机动力系统中有效，但向高维、非平稳、部分观测或实时在线场景扩展仍待验证。

（完）
