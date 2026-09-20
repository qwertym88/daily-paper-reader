---
title: Learning Human-Robot Collaboration via Heterogeneous-Agent Lyapunov Policy Optimization
title_zh: 通过异构智能体Lyapunov策略优化学习人机协作
authors: "Hao Zhang, Yaru Niu, Yikai Wang, Ding Zhao, Eric H. Tseng"
date: 2026-04-30
pdf: "https://openreview.net/pdf/d07c060a2d8540bb431889515360269847e1cbfa.pdf"
tags: ["query:rl-control"]
score: 5.0
evidence: 基于Lyapunov的收缩稳定去中心化多智能体策略优化
tldr: 人机协作中机器人需应对多样的人类行为与情境，去中心化多智能体强化学习因机器人与人之间的异质性产生理性差距，导致策略更新振荡甚至发散。本文提出异构智能体Lyapunov策略优化HALO，通过在策略参数空间施加Lyapunov收缩约束来稳定学习。实验显示该方法提升了协作任务的泛化性与稳定性，为异构多智能体协同控制提供了理论化的稳定机制。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 人机协作中机器人需应对多样人类行为，去中心化MARL存在理性差距导致策略更新发散。
method: 提出HALO框架，在策略参数空间强制Lyapunov收缩以稳定去中心化多智能体策略优化。
result: 实验表明该方法提升人机协作的泛化性与稳定性。
conclusion: 为异构多智能体协同提供了稳定的策略优化机制。
---

## Abstract
To improve generalization and resilience in human–robot collaboration (HRC), robots must contend with diverse combinations of human behaviors and contexts, motivating multi-agent reinforcement learning (MARL). However, inherent heterogeneity between robots and humans creates a rationality gap (RG), where decentralized policy updates deviate from cooperative joint optimization. The resulting learning problem is a general-sum differentiable game, so independent policy-gradient updates can oscillate or diverge without added structure. We propose heterogeneous-agent Lyapunov policy optimization (HALO), a framework that stabilizes decentralized MARL by enforcing Lyapunov-based contraction in policy-parameter space. Unlike Lyapunov-based safe RL, which targets state/trajectory constraints in constrained Markov decision processes, HALO uses Lyapunov certification to stabilize decentralized policy learning. HALO rectifies decentralized gradients via optimal quadratic projections, ensuring monotonic contraction of RG and enabling effective exploration of open-ended interaction spaces. Extensive simulations and real-world humanoid-robot experiments show that this certified stability improves generalization and robustness in collaborative corner cases.

---

## 论文详细总结（自动生成）

## 说明
- 提供的 PDF 提取文本实际为 OpenReview 浏览器验证页面，未包含论文正文。
- 以下总结主要基于论文元数据与 Abstract；正文中的公式、实验细节、算力信息等若未出现，将明确标注为“未说明”或“无法验证”。

## 1. 核心问题与整体含义
- **研究背景**：人机协作（HRC）中，机器人需要面对多样的人类行为与情境组合，因此需要多智能体强化学习（MARL）来提升泛化性与韧性。
- **核心问题**：机器人与人类之间存在固有异质性，导致“理性差距”（rationality gap, RG）。去中心化策略更新会偏离合作式联合优化。
- **问题本质**：该学习问题可视为一般和可微博弈，独立策略梯度更新可能振荡甚至发散，除非引入额外结构。
- **整体含义**：论文试图为异构多智能体协同控制提供一种理论化的稳定机制，使去中心化 MARL 在人机协作中更稳定、更可泛化。

## 2. 方法论：HALO
- **方法名称**：Heterogeneous-Agent Lyapunov Policy Optimization（HALO，异构智能体 Lyapunov 策略优化）。
- **核心思想**：在**策略参数空间**施加 Lyapunov 收缩约束，以稳定去中心化 MARL 学习过程。
- **与安全强化学习的区别**：
  - 传统 Lyapunov-based safe RL 通常针对约束马尔可夫决策过程中的状态/轨迹约束。
  - HALO 则使用 Lyapunov 认证来稳定**去中心化策略学习**本身。
- **关键技术细节**：
  - 通过**最优二次投影**修正去中心化梯度。
  - 目标是确保理性差距（RG）单调收缩。
  - 进而支持对开放式交互空间的有效探索。
- **算法流程的文字描述**：
  1. 识别去中心化策略更新与联合优化之间的偏差，即 RG；
  2. 在策略参数空间中构造 Lyapunov 收缩条件；
  3. 将梯度修正表述为最优二次投影问题；
  4. 对去中心化梯度进行投影修正；
  5. 执行策略更新，使 RG 满足单调收缩；
  6. 在稳定约束下探索人机交互空间。
- **注意**：具体公式、Lyapunov 函数构造、投影求解方式与理论证明细节未在可用文本中给出。

## 3. 实验设计
- **场景类型**：摘要称进行了大量仿真实验与真实世界人形机器人实验。
- **实验目标**：验证这种“认证稳定性”是否能提升人机协作在 corner cases 中的泛化性与鲁棒性。
- **数据集 / Benchmark**：未说明。
- **对比方法**：未说明。
- **具体任务与平台**：仅提到 real-world humanoid-robot experiments，具体机器人平台、任务设置、评价指标均未在可用文本中提供。

## 4. 资源与算力
- 可用文本中**未提及** GPU 型号、GPU 数量、训练时长、仿真规模或真实实验计算资源。
- 因此无法评估该工作的算力需求与训练成本。

## 5. 实验数量与充分性
- 摘要称有“extensive simulations”和真实机器人实验，但未给出具体实验组数。
- 未说明是否有消融实验、不同数据集/场景数量、统计显著性检验、基线公平性设置等。
- 从可用信息看，仿真加真实人形机器人实验有助于增强外部效度，但**无法判断实验是否充分、客观与公平**。
- 若要评估实验充分性，需要论文正文、附录或项目页中的详细实验表格与协议。

## 6. 主要结论与发现
- HALO 能通过策略参数空间中的 Lyapunov 收缩稳定去中心化多智能体策略学习。
- 通过最优二次投影修正去中心化梯度，可使理性差距单调收缩。
- 该方法支持在开放式交互空间中有效探索。
- 实验表明，这种认证稳定性提升了人机协作的泛化性与鲁棒性，尤其是在协作 corner cases 中。
- 论文为异构多智能体协同控制提供了稳定的策略优化机制。

## 7. 优点
- **问题定位清晰**：聚焦人机异质性导致的 RG，以及一般和博弈中独立策略梯度更新不稳定问题。
- **理论视角有新意**：将 Lyapunov 方法从传统安全约束扩展到策略参数空间的稳定学习。
- **技术路线明确**：用最优二次投影修正梯度，并追求 RG 单调收缩。
- **验证形式较全面**：包含仿真与真实人形机器人实验，若细节充分则说服力较强。
- **应用价值高**：面向人机协作中的泛化、鲁棒与极端场景，具有实际机器人意义。

## 8. 不足与局限
- 由于可用文本不含正文，**无法核验理论假设、收敛条件、公式推导与算法细节**。
- 未说明算力、代码、数据、benchmark、对比方法、消融实验与统计显著性。
- Lyapunov 函数的构造难度、投影计算开销、可扩展性到更多智能体或更复杂任务的能力尚不明确。
- 真实人类行为的多样性、安全约束、样本效率与部署限制未在可用信息中讨论。
- 可能存在特定任务或平台偏差，方法向更广泛人机协作场景的泛化仍需验证。
- 实验的客观性与公平性目前无法评估。

（完）
