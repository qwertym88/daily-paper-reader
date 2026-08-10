---
title: "Learning in Circles: Rotational Dynamics in Competitive Reinforcement Learning"
title_zh: 循环学习：竞争性强化学习中的旋转动力学
authors: "Baraah A. M. Sidahmed, Tatjana Chavdarova"
date: 2025-09-14
pdf: "https://openreview.net/pdf?id=O2EPgTawRq"
tags: ["query:rl-control"]
score: 8.0
evidence: actor-critic旋转动力学与基于变分不等式的Lookahead稳定化训练
tldr: 竞争性强化学习中的actor-critic优化涉及耦合目标，容易围绕均衡点循环旋转而导致不稳定。论文从算子角度解释这一旋转动力学，并采用面向变分不等式的Lookahead方法来抑制该现象。所提出的Lookahead-(MA)RL在单智能体与多智能体任务中提升了训练稳定性与收敛性，为理解actor-critic行为提供了新的理论视角。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 单多智能体actor-critic训练不稳定，其优化本质是寻求均衡而非独立下降。
method: 基于变分不等式框架，利用Lookahead方法抑制actor-critic中的旋转动力学。
result: 在单多智能体RL任务上改善了稳定性与收敛性能。
conclusion: 为竞争性RL中的actor-critic优化提供了理论解释与有效改进工具。
---

## Abstract
Optimization in competitive reinforcement learning (RL) differs from standard minimization. Actor–critic methods, in single- and multi-agent (MARL) settings, involve coupled objectives, so optimizing them jointly requires finding an equilibrium rather than performing independent descent. Through operator-theoretic viewpoint, we show that actor–critic models inherently exhibit rotational dynamics during learning, cycling around equilibria, thereby explaining in part the instability often observed in practice.  Through the variational inequality (VI) framework for studying equilibrium seeking problems, we adopt the Lookahead method for VIs, which suppresses these rotations in actor–critic RL. Building on this, we introduce *Lookahead-(MA)RL (LA-(MA)RL)* to efficiently mitigate rotational dynamics. Across classical two-player games and multi-agent benchmarks, including *Rock--paper--scissors*, *Matching pennies*, and *Multi-Agent Particle environments*, LA-MARL consistently improves convergence and stability. Our results highlight optimization as a critical yet underexplored lever in RL: by rethinking the equilibrium-seeking dynamics, one can achieve substantial stability and performance gains.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究背景**：竞争性强化学习（Competitive RL）中的优化问题与标准的最小化问题有本质不同。在单智能体和多智能体（MARL）场景中，Actor-Critic 方法涉及**耦合目标函数**，因此联合优化需要寻找**均衡点（equilibrium）**，而非进行独立的梯度下降。
- **核心问题**：实践中 Actor-Critic 训练常常表现出不稳定性，论文认为其原因在于学习过程中存在**旋转动力学（rotational dynamics）**，即模型参数会围绕均衡点循环打转，而非直接收敛。
- **整体意义**：论文通过算子论视角揭示了这种旋转现象，并提出将变分不等式（VI）框架下的 **Lookahead 方法**引入 Actor-Critic 优化，从而抑制旋转、提升训练稳定性与收敛性。该工作强调优化方法作为 RL 中一个被忽视但关键的杠杆。

## 2. 论文提出的方法论

- **核心思想**：将竞争性 RL 中的 Actor-Critic 优化问题建模为**变分不等式（VI）问题**，利用 Lookahead 方法对更新方向进行“前瞻”调整，以抵消旋转分量。
- **关键技术细节**：
  - 从**算子理论（operator-theoretic viewpoint）**出发，证明 Actor-Critic 的学习更新天然具有旋转特性，导致围绕均衡点的振荡。
  - 采用面向 VI 的 **Lookahead 方法**：在每次更新前，先通过“快照”参数进行试探性更新，再基于更远视界的信息修正主更新方向，从而阻尼旋转。
- **算法流程（文字描述）**：
  1. 初始化主模型参数。
  2. 保存一份“慢”参数（或快照参数）。
  3. 在每次迭代中，基于当前参数计算 VI 更新方向，并通过 Lookahead 机制对方向进行修正（例如，先沿更新方向走一小步，再评估损失或均衡残差）。
  4. 用修正后的方向更新主参数，并周期性地将主参数同步到慢参数。
- **提出方法名称**：**Lookahead-(MA)RL（LA-(MA)RL）**，适用于单智能体（LA-RL）与多智能体（LA-MARL）场景。

## 3. 实验设计

- **Benchmark 与场景**：
  - 经典双人博弈：**石头剪刀布（Rock–paper–scissors）**
  - **匹配 pennies（Matching pennies）** 游戏
  - **多智能体粒子环境（Multi-Agent Particle environments）**
- **对比方法**：论文未在摘要中明确列出所有基线，但从上下文推断，应与标准 Actor-Critic、原始 VI 求解方法及已有的稳定化算法进行对比。
- **评价指标**：主要关注**收敛性（convergence）** 和**训练稳定性（stability）**。

## 4. 资源与算力

- 论文提供的元数据和摘要中**未明确提及** GPU 型号、数量或训练时长等具体算力信息。
- 由于所涉实验为经典小规模博弈和粒子环境，通常不需要大规模算力，但论文原文未给出细节，因此无法确认。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，至少包含 3 类任务环境（石头剪刀布、匹配 pennies、多智能体粒子环境），其中粒子环境可能包含多个子任务（如协作、竞争、通信等），但具体数量未列出。
- **充分性评估**：
  - 覆盖了从简单博弈到多智能体基准的多个层级，能初步验证方法的有效性。
  - 但缺少消融实验、不同超参数敏感性分析、以及与其他 SOTA 方法的系统性对比细节，因此充分性有限。
  - 由于只有摘要性描述，无法判断实验是否存在随机性控制、多次重复等公平性保障，需阅读全文进一步确认。

## 6. 论文的主要结论与发现

- Actor-Critic 方法在竞争性 RL 中会天然产生**旋转动力学**，这解释了训练不稳定的部分原因。
- 通过 VI 框架和 **Lookahead 方法** 可以高效抑制旋转。
- 所提出的 **LA-(MA)RL** 在多个经典博弈和多智能体基准上**持续改善收敛性与稳定性**。
- 结论：重新设计均衡寻求的优化动态，可以带来显著的稳定性和性能提升。

## 7. 优点

- **理论视角新颖**：用算子论和变分不等式统一解释 Actor-Critic 的不稳定性，为理解 RL 优化行为提供了新工具。
- **方法迁移性强**：将领域成熟的 Lookahead 方法引入 RL 均衡求解，思路简洁且具备一般性。
- **实验场景有代表性**：从简单博弈到多智能体环境，覆盖了竞争性 RL 的关键挑战。
- **强调优化杠杆**：提醒社区关注优化器设计对 RL 训练稳定性的影响。

## 8. 不足与局限

- **实验细节不完整**：缺少具体的数据量、训练回合数、超参数设置、消融实验和基线细节，难以完全评估方法的稳健性。
- **仅集中在竞争性/博弈场景**：未涉及合作式或混合式 MARL 任务，泛化性有待验证。
- **理论分析深度未展示**：可能未给出严格的收敛率证明，或对旋转动力学的刻画停留在定性层面。
- **算力信息缺失**：无法评估方法的计算开销相对于标准 Actor-Critic 的增加程度。
- **论文状态为 ICLR-2026 拒稿**：说明审稿人可能认为存在某些弱点，但元数据未提供审稿意见，需注意方法可能仍有争议。

（完）
