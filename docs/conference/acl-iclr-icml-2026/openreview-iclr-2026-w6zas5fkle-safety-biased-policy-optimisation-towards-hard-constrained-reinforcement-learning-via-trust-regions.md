---
title: "Safety-Biased Policy Optimisation: Towards Hard-Constrained Reinforcement Learning via Trust Regions"
title_zh: 安全偏置策略优化：通过信任域实现硬约束强化学习
authors: "Ankit Kanwar, Dominik Wagner, Luke Ong"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=W6zas5fKle"
tags: ["query:rl-control"]
score: 9.0
evidence: 面向硬约束强化学习的信任域算法，在最大化奖励的同时保证约束满足。
tldr: 硬约束下强化学习需要在严格安全的同时最大化奖励，现有Lagrangian和投影方法常顾此失彼。本文提出安全偏置信任域策略优化(SB-TRPO)，用代价与奖励的自然策略梯度凸组合进行信任域更新，自适应偏向约束满足。在安全强化学习基准上，SB-TRPO实现了近零违规并保持高奖励。该方法为硬约束强化学习提供了一种简单有效的策略更新范式。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有Lagrangian和投影方法难以在硬约束下同时做到近似零违规和高奖励，常牺牲其中一个目标。
method: 提出SB-TRPO，在信任域更新中使用代价和奖励的自然策略梯度的凸组合，自适应偏向约束满足且保持奖励提升。
result: 在多个安全强化学习基准上，SB-TRPO显著降低安全违规且保持高奖励，优于现有硬约束方法。
conclusion: 该算法在硬约束强化学习中达成了约束满足与奖励优化的良好平衡。
---

## Abstract
Reinforcement learning (RL) in safety-critical domains requires agents to maximise rewards while strictly adhering to safety constraints. Existing approaches, such as Lagrangian and projection-based methods, often either fail to ensure near-zero safety violations or sacrifice reward performance in the face of hard constraints. We propose Safety-Biased Trust Region Policy Optimisation (SB-TRPO), a new trust-region algorithm for hard-constrained RL. SB-TRPO adaptively biases policy updates toward constraint satisfaction while still seeking reward improvement. Concretely, it performs trust-region updates using a convex combination of the natural policy gradients of cost and reward, ensuring a fixed fraction of optimal cost reduction at each step. We provide a theoretical guarantee of local progress toward safety, with reward improvement when gradients are suitably aligned. Experiments on standard and challenging Safety Gymnasium tasks show that SB-TRPO consistently achieves the best balance of safety and meaningful task completion compared to state-of-the-art methods.

---

## 论文详细总结（自动生成）

# 中文总结：Safety-Biased Policy Optimisation: Towards Hard-Constrained Reinforcement Learning via Trust Regions

## 1. 核心问题与研究动机

- 在安全关键的强化学习场景中，智能体不仅要最大化任务奖励，还必须严格满足安全约束。
- 现有方法主要分为两类：
  - **Lagrangian 类方法**：通过拉格朗日乘子将约束转化为惩罚项，但难以在硬约束下保证近零违规，且乘子调节不稳定。
  - **投影类方法**：将策略更新投影到可行安全域内，但往往以牺牲奖励性能为代价。
- 核心难点是：**在“硬约束”（必须满足）条件下，同时实现近似零安全违规和良好的奖励表现**，而现有方法常顾此失彼。
- 该问题对自动驾驶、机器人控制、电力系统等安全关键应用具有重要意义，是安全强化学习中的核心问题之一。

## 2. 方法论：SB-TRPO

- 论文提出 **Safety-Biased Trust Region Policy Optimisation（SB-TRPO）**，一种面向硬约束强化学习的信任域算法。
- **核心思想**：在信任域策略更新中，将“安全/代价方向”的更新与“奖励方向”的更新进行**凸组合**，从而自适应地偏向约束满足，同时仍追求奖励改进。
- **关键技术细节**：
  - 使用**代价自然策略梯度**和**奖励自然策略梯度**的凸组合作为更新方向。
  - 每次更新中，确保一定比例的“最优代价降低量”被实现，从而保证安全侧的局部进展。
  - 当奖励梯度与安全梯度方向适当时，算法仍能保证奖励提升。
- **理论保证**：
  - 作者提供了局部安全进展的理论保证；
  - 并给出在梯度方向适当对齐时奖励改进的保证。
- 在流程上，SB-TRPO 仍属于信任域策略优化（TRPO）框架，但在更新方向和约束处理上与标准 TRPO 不同，核心是引入了“安全偏置”的更新策略。

## 3. 实验设计

- **基准场景**：使用了“标准且具有挑战性的 Safety Gymnasium 任务”。
  - Safety Gymnasium 是安全强化学习常用的基准测试平台，包含多种机器人导航、避障等任务。
- **对比方法**：与“最先进的（state-of-the-art）方法”进行比较，但摘要中未具体列出方法名称。
- **评价指标**：主要关注安全违规率和任务完成/奖励表现之间的平衡。
- **总体设计**：在多个 Safety Gymnasium 任务上评估 SB-TRPO 相对于现有硬约束算法的表现。

## 4. 资源与算力

- 论文提供的信息有限，**摘要中没有明确说明**：
  - 使用的 GPU 型号与数量；
  - 训练轮数、训练时长；
  - 计算资源总量。
- 因此，无法从现有材料中评估其计算成本或可复现性所需的硬件条件。

## 5. 实验数量与充分性

- 从摘要可见，实验覆盖了多个 Safety Gymnasium 任务，但**没有披露具体实验数量、任务清单、消融实验或超参数敏感性分析**。
- 由于缺少：
  - 不同任务上的量化结果；
  - 与各对比方法的统计显著性检验；
  - 对安全偏置系数等关键超参数的消融研究；
  - 更多样的安全基准（如真实机器人或模拟控制任务）；
  
  目前只能认为实验**初具说明性，但不够充分**，难以全面验证方法的泛化能力和稳健性。
- 评审信息显示该论文为 ICLR-2026 Rejected，可能也暗示其实验或论证存在某些不足。

## 6. 主要结论与发现

- SB-TRPO 在硬约束强化学习任务上，能够**同时实现较低的安全违规和较高的任务奖励**。
- 相比现有方法，SB-TRPO 在“安全－奖励”权衡上取得了更好的平衡。
- 理论分析与实验结果共同支持：通过安全偏置的信任域更新，可以在不显著牺牲奖励的情况下实现硬约束满足。

## 7. 优点与亮点

- **方法简单且有效**：使用自然策略梯度的凸组合，概念清晰，易于在 TRPO 框架上实现。
- **理论扎实**：给出了局部安全进展和奖励改进的理论保证，具有较好的可解释性。
- **针对痛点**：直接面向“硬约束”场景，解决 Lagrangian 方法违规率高和投影方法奖励损失大的问题。
- **自适应偏置**：更新方向可自适应偏向安全，有助于在不同安全需求下灵活调整。
- **基准选择合理**：Safety Gymnasium 是该领域公认的标准测试平台，实验结果具有一定的可比性。

## 8. 不足与局限

- **实验细节不足**：摘要未给出具体任务列表、基线和具体量化结果，无法独立验证其优越性。
- **对比信息不明确**：“state-of-the-art methods”未列出具体名称，公平性难以判断。
- **缺少消融与分析**：未说明安全偏置系数的选择、收敛性、敏感性等，难以了解方法适用范围。
- **应用场景有限**：仅在模拟环境 Safety Gymnasium 上评估，缺少真实机器人或更复杂工业场景验证。
- **理论假设不明确**：“梯度适当对齐”这一条件的具体含义与成立范围未被说明，可能限制其泛化性。
- **评审状态提示风险**：作为 ICLR-2026 Rejected 论文，可能仍存在方法或实验上的关键缺陷，因此对其结论应持谨慎态度。

（完）
