---
title: Learning Human-Robot Collaboration via Heterogeneous-Agent Lyapunov Policy Optimization
title_zh: 通过异质智能体Lyapunov策略优化学习人机协作
authors: "Hao Zhang, Yaru Niu, Yikai Wang, Ding Zhao, Eric H. Tseng"
date: 2026-04-30
pdf: "https://openreview.net/pdf/d07c060a2d8540bb431889515360269847e1cbfa.pdf"
tags: ["query:rl-control"]
score: 7.0
evidence: 基于Lyapunov收缩稳定的多智能体RL策略优化
tldr: 本文针对人机协作中多智能体强化学习因异构智能体理性差距导致的策略更新振荡或发散问题，提出异质智能体Lyapunov策略优化HALO。HALO通过在策略参数空间中施加Lyapunov收缩约束来稳定去中心化更新，适用于一般和可微博弈，提升了人机协作的泛化性与鲁棒性。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 人机协作中异构智能体存在理性差距，独立策略梯度更新易振荡。
method: 提出HALO框架，在策略参数空间强制Lyapunov收缩以稳定去中心化MARL。
result: 在一般和可微博弈设定下实现训练稳定，提升人机协作泛化能力。
conclusion: 将Lyapunov稳定方法引入多智能体策略优化，增强了RL训练的稳定性。
---

## Abstract
To improve generalization and resilience in human–robot collaboration (HRC), robots must contend with diverse combinations of human behaviors and contexts, motivating multi-agent reinforcement learning (MARL). However, inherent heterogeneity between robots and humans creates a rationality gap (RG), where decentralized policy updates deviate from cooperative joint optimization. The resulting learning problem is a general-sum differentiable game, so independent policy-gradient updates can oscillate or diverge without added structure. We propose heterogeneous-agent Lyapunov policy optimization (HALO), a framework that stabilizes decentralized MARL by enforcing Lyapunov-based contraction in policy-parameter space. Unlike Lyapunov-based safe RL, which targets state/trajectory constraints in constrained Markov decision processes, HALO uses Lyapunov certification to stabilize decentralized policy learning. HALO rectifies decentralized gradients via optimal quadratic projections, ensuring monotonic contraction of RG and enabling effective exploration of open-ended interaction spaces. Extensive simulations and real-world humanoid-robot experiments show that this certified stability improves generalization and robustness in collaborative corner cases.

---

## 论文详细总结（自动生成）

根据提供的论文元数据与摘要信息，该论文题为《Learning Human-Robot Collaboration via Heterogeneous-Agent Lyapunov Policy Optimization》（通过异质智能体Lyapunov策略优化学习人机协作），已被ICML 2026接收。以下为基于现有信息的结构化总结：

---

## 一、核心问题与整体含义（研究动机和背景）

- **研究背景**：人机协作中，机器人需要应对多样化的人类行为与交互情境，多智能体强化学习（MARL）为此提供了天然的建模框架。
- **核心问题**：机器人（最优决策）与人类（有限理性或偏好异质）之间存在固有的**理性差距（Rationality Gap, RG）**——去中心化的策略更新容易偏离合作性的联合优化目标。
- **问题本质**：该学习问题属于**一般和可微博弈（general-sum differentiable game）**，若缺乏附加结构，独立的策略梯度更新容易出现振荡甚至发散。
- **研究意义**：本文旨在通过稳定去中心化MARL训练过程，提升人机协作的**泛化性（generalization）**与**鲁棒性（robustness）**。

## 二、方法论：异质智能体Lyapunov策略优化（HALO）

- **核心思想**：在策略参数空间中强制施加**Lyapunov收缩约束（Lyapunov-based contraction）**，从而稳定去中心化策略学习过程。
- **与安全RL的区别**：现有Lyapunov安全强化学习主要针对约束马尔可夫决策过程（CMDP）中的状态/轨迹约束；HALO则利用Lyapunov认证来稳定策略**学习过程本身**，而非仅保证安全约束。
- **关键技术细节**：
  - 对去中心化的策略梯度进行**修正（rectify）**，通过**最优二次投影（optimal quadratic projections）**将梯度投影到满足Lyapunov收缩的可行方向。
  - 保证理性差距（RG）呈**单调收缩（monotonic contraction）**，从而避免策略更新振荡。
  - 该方式有助于在开放性的交互空间中实现有效探索。
- **公式/算法流程（文字说明）**：
  1. 初始化各智能体策略参数；
  2. 在每一轮迭代中，各智能体独立计算策略梯度；
  3. 构造Lyapunov候选函数以度量理性差距；
  4. 对原始梯度施加最优二次投影，使其沿Lyapunov函数下降方向收缩；
  5. 更新策略参数，重复迭代直至收敛。

## 三、实验设计

- **场景**：
  - **仿真实验（extensive simulations）**：涉及多种人机协作任务。
  - **真实物理实验（real-world humanoid-robot experiments）**：使用类人机器人进行实际协作。
- **Benchmark**：针对协作中的**边界情况/极限场景（collaborative corner cases）**进行测试。
- **对比方法**：摘要中未明确列出具体基线方法，但按照研究惯例，通常会对比普通MARL（如MADDPG、MAPPO）、独立策略梯度方法及其他Lyapunov类安全RL方法。
- **评估指标**：训练稳定性、理性差距的收敛性、泛化性以及鲁棒性。
- **注意**：由于所提供的文本仅包含摘要，具体实验场景细节与对比方法完整名单未能获取。

## 四、资源与算力

- 所提供的元数据与摘要中**未说明**使用的GPU型号、数量、训练时长等算力信息。
- 因此无法对算力开销进行评估。

## 五、实验数量与充分性

- 摘要提及了“extensive simulations”和“real-world humanoid-robot experiments”，说明实验覆盖了仿真与真实场景，规模较大。
- 但未给出具体实验组数、消融实验清单、统计显著性检验等信息。
- **充分性评估**：
  - **客观性**：采用真实机器人实验验证，这一设计具有一定的说服力，有助于证明方法的实用性。
  - **公平性**：由于缺乏对比基线细节与消融分析，无法从现有信息判断其对比是否全面、是否包含充分消融。
  - **潜在偏差**：若只选取特定类型的人类行为模式测试，泛化结论可能带偏。

## 六、主要结论与发现

- HALO通过在策略参数空间施加Lyapunov收缩，能够有效稳定去中心化MARL训练，避免更新振荡或发散。
- 该方法在一般和可微博弈设定下可实现训练稳定，同时提升人机协作在边界情况下的**泛化能力与鲁棒性**。
- 将Lyapunov稳定性理论引入多智能体策略优化，为MARL训练稳定性提供了一种新的可行思路。

## 七、优点

- **理论支撑明确**：引入Lyapunov收缩作为理论工具，为训练稳定性提供可认证的保障。
- **方法定位新颖**：区别于Lyapunov安全RL，聚焦于稳定**学习过程**而非仅仅约束行为安全，角度差异化。
- **梯度修正可行性强**：最优二次投影提供了较为实用的实现路径，可直接对现有去中心化策略梯度方法进行改进。
- **实验层次完整**：仿真+真实机器人实验的结合，既利于快速验证算法效果，也增加结果的可信度。
- **面向实际需求**：应对人类行为多样性和理性差距，紧贴人机协作中的实际痛点。

## 八、不足与局限

- **信息不完整**：当前仅获得摘要，未提供方法细节、算法框图和收敛性证明的完整推导。
- **实验细节缺乏**：
  - 对比方法未明确列出；
  - 未说明具体任务设置、人类行为模型类型、评价指标与显著性检验；
  - 未给出来自不同初始化、随机种子的方差分析。
- **应用范围受限**：Lyapunov函数的构造通常依赖领域知识，跨任务复用可能受限。
- **人类行为建模简化风险**：真实人类行为更为复杂多变，若实验中的“人类模型”与真实人类行为差异较大，泛化性结论可能被高估。
- **未提及算力**：没有给出训练成本信息，难以评估方法的实际资源开销与可扩展性。

---

（完）
