---
title: "Direct Preference Optimization for Primitive-Enabled Hierarchical RL: A Bilevel Approach"
title_zh: 基于直接偏好优化的基元使能分层强化学习：一种双层方法
authors: "Utsav Singh, Souradip Chakraborty, Wesley A. Suttle, Brian M. Sadler, Derrik E. Asher, Anit Kumar Sahu, Mubarak Shah, Vinay P. Namboodiri, Amrit Singh Bedi"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=wleUyyqTz2"
tags: ["query:rl-control"]
score: 6.0
evidence: 分层强化学习采用直接偏好优化并建模为双层优化，推进强化学习策略学习。
tldr: 分层强化学习面临非平稳性和底层策略产生的不可行子目标等问题。本文将目标条件分层强化学习建模为双层优化，提出DIPPER框架，用直接偏好优化在子目标序列上训练高层策略。实验表明该方法在长程任务中能生成可行子目标并显著提升性能。该工作为分层强化学习提供了一种偏好驱动的稳定训练范式。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 分层强化学习存在非平稳性和不可行子目标问题，导致高层学习不稳定。
method: 提出DIPPER框架，将目标条件分层强化学习建模为双层优化，利用直接偏好优化训练高层策略，避免对底层策略变化的依赖。
result: 在长程任务中验证了DIPPER能生成可行的子目标序列，性能优于现有分层强化学习方法。
conclusion: 偏好驱动的双层优化有效解决分层强化学习中的非平稳性与不可行子目标挑战。
---

## Abstract
Hierarchical reinforcement learning (HRL) enables agents to solve complex, long-horizon tasks by decomposing them into manageable sub-tasks. However, HRL methods face two fundamental challenges: (i) non-stationarity caused by the evolving lower-level policy during training, which destabilizes higher-level learning, and (ii) the generation of infeasible subgoals that lower-level policies cannot achieve. To address these challenges, we introduce DIPPER, a novel HRL framework that formulates goal-conditioned HRL as a bi-level optimization problem and leverages direct preference optimization (DPO) to train the higher-level policy. By learning from preference comparisons over subgoal sequences rather than rewards that depend on the evolving lower-level policy, DIPPER mitigates the impact of non-stationarity on higher-level learning. To address infeasible subgoals, DIPPER incorporates lower-level value function regularization that encourages the higher-level policy to propose achievable subgoals. We introduce two novel metrics to quantitatively verify that DIPPER mitigates non-stationarity and infeasible subgoal generation issues in HRL. Empirical evaluation on challenging robotic navigation and manipulation benchmarks shows that DIPPER achieves upto 40% improvements over state-of-the-art baselines on challenging sparse-reward scenarios, highlighting the potential of preference-based learning for addressing longstanding HRL limitations.

---

## 论文详细总结（自动生成）

## 论文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究背景**：分层强化学习（HRL）通过将复杂的长程任务分解为若干子任务，使智能体能够解决更加复杂的问题。
- **核心挑战**：
  - **非平稳性（Non-stationarity）**：训练过程中底层策略持续演化，导致高层策略的学习目标不稳定，影响整体收敛。
  - **不可行子目标（Infeasible Subgoals）**：高层策略可能生成底层策略无法实现的子目标，造成任务执行失败或训练停滞。
- **研究意义**：解决上述两个长期制约 HRL 的关键问题，是实现稳定且可扩展的层级决策的重要一步。该工作为偏好驱动的 HRL 训练范式提供了全新的视角。

### 2. 论文提出的方法论
- **核心思想**：将目标条件分层强化学习（Goal-Conditioned HRL）建模为 **双层优化问题**，利用**直接偏好优化（DPO）**训练高层策略，从而减少对底层策略奖励信号的依赖。
- **关键技术进步**：
  - **偏好驱动的训练**：高层策略通过子目标序列间的偏好比较（而非依赖底层策略的奖励）进行优化，从根本上缓解非平稳性带来的不稳定。
  - **可行子目标引导**：引入**底层价值函数正则化**，鼓励高层策略生成底层策略能够实现的子目标，降低不可行子目标出现的概率。
  - **双向优化架构**：高层目标（偏好优化）与底层目标（价值函数约束）相互耦合，构成双层优化框架。
- **算法流程示意**：
  1. 高层策略生成候选子目标序列；
  2. 通过成对偏好数据（人类偏好或可自动构造的偏好信号）对高层策略进行 DPO 训练；
  3. 同时用底层价值函数对子目标可行性进行正则化约束；
  4. 底层策略在约束后的子目标上进行强化学习；
  5. 交替更新直至收敛。

### 3. 实验设计
- **Benchmark 与场景**：
  - 机器人导航任务（Robotic Navigation)
  - 机器人操作任务（Robotic Manipulation）
  - 主要面向 **稀疏奖励（Sparse-Reward）** 的困难长程任务场景。
- **对比方法**：与当前最先进（State-of-the-Art）的分层强化学习基线方法进行对比。
- **评估指标**：
  - 论文额外设计了 **两个新颖的量化指标**，用于直接测量：
    - 非平稳性的缓解程度；
    - 不可行子目标的生成频率。
  - 用于验证 DIPPER 在缓解上述两类问题上的效果。

### 4. 资源与算力
- 论文提供的提取内容中**未明确说明**所使用的算力资源，包括 GPU 型号、数量、训练时长等信息。
- 在原文（若包含实验章节）中可能包含相关细节，但在当前可获得的摘要与元数据中无法确认。

### 5. 实验数量与充分性
- **实验数量**：摘要提及在导航和操作两大基准上进行了实验，并与 SOTA 基线比较，但未提供具体实验组数、消融实验数量或统计显著性分析。
- **充分性与客观性评估**：
  - 优点：引入了两个新量化指标，有助于更直接地评估方法的实际效果，不仅仅依赖任务平均回报，评估视角具有一定创新性。
  - 不足：当前可见信息中缺少：
    - 消融研究的具体设置（如去掉正则化的效果）；
    - 对不同超参数（偏好数据规模、底层策略更新频率等）的敏感性分析；
    - 对偏好标注来源（人工 vs 合成）及其偏差的讨论。
  - 公平性：披露程度有限，无法判断基线调参强度、运行次数方差等信息，需查阅完整论文才能做出全面评估。

### 6. 论文的主要结论与发现
- DIPPER 在具有挑战性的稀疏奖励长程任务中，相较于最优基线可实现 **最高约 40% 的性能提升**。
- 偏好驱动的双层优化有效缓解了 HRL 中高层学习的非平稳性问题。
- 通过底层价值函数正则化，显著降低了不可行子目标的生成。
- 两个新评估指标从量化角度验证了该方法对 HRL 长期难题的实质性改进。

### 7. 优点
- **方法新颖性**：首次将 DPO 与双层优化结合应用于 HRL，跳出了底层奖励驱动的传统训练范式。
- **问题针对性**：直接瞄准非平稳性和不可行子目标两个根本痛点，而非仅从任务性能的单一维度出发。
- **可解释评估**：引入新指标单独测量非平稳性和子目标可行性，为 HRL 领域提供了更细粒度的评测手段。
- **实证效果**：在稀疏奖励场景下带来的最高 40% 性能改进令人印象深刻，充分展示了偏好学习的潜力。

### 8. 不足与局限
- **算力与实验细节缺失**：未报告 GPU 型号/数量、训练时间、重复运行次数等关键信息，限制了可复现性和成本评估。
- **实验覆盖可能有限**：仅涉及机器人导航和操作，未验证在更广泛领域（如游戏、推荐系统或语言智能体）中的泛化性。
- **对偏好数据质量的依赖**：偏好比较的构造方式、数量及一致性对 DPO 效果影响极大，文中若未深入分析则会构成潜在风险。
- **大规模部署的工程挑战**：高层与底层的交替训练、偏好数据的获取与清洗，可能在实际应用（特别是真实物理机器人）中带来额外成本。
- **基元（Primitive）设计的隐性依赖**：标题中强调了“基元使能”（Primitive-Enabled），这意味着系统的性能可能在一定程度上受限于底层基元库的设计质量，可推广性有待验证。

---

（完）
