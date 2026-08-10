---
title: Achieve Performatively Optimal Policy for Performative Reinforcement Learning
title_zh: 实现表现性强化学习中的表现最优策略
authors: "Ziyi Chen, Heng Huang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=urElUkCUXq"
tags: ["query:rl-control"]
score: 7.0
evidence: 应用零阶Frank-Wolfe数值优化方法求解表现性强化学习策略
tldr: 表现性强化学习考虑智能体策略会改变环境动态的场景，现有方法仅追求表现稳定策略，与真实最优策略存在固定差距。本文在Frank-Wolfe框架中引入零阶近似表现策略梯度，提出0-FW算法。该算法首次在多项式复杂度内获得表现最优策略，突破了以往只能得到稳定策略的限制。该工作为策略与环境动态相互作用的问题提供了更优的理论与算法保证。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有表现性RL仅能达到表现稳定策略，与理想的表现最优策略存在常数差距。
method: 在Frank-Wolfe框架中使用零阶梯度近似，提出0-FW算法优化表现策略目标。
result: 获得首个多项式复杂度的表现最优策略，证明优于稳定策略。
conclusion: 为政策影响环境动态的RL场景提供了更优策略的求解方法。
---

## Abstract
Performative reinforcement learning is an emerging dynamical decision making framework, which extends reinforcement learning to the common applications where the agent's policy can change the environmental dynamics. Existing works on performative reinforcement learning only aim at a performatively stable (PS) policy that maximizes an approximate value function. However, there is a provably positive constant gap between the PS policy and the desired performatively optimal (PO) policy that maximizes the original value function. In contrast, this work proposes a zeroth-order Frank-Wolfe algorithm (0-FW) algorithm with a zeroth-order approximation of the performative policy gradient in the Frank-Wolfe framework, and obtains the first polynomial computation complexity result to converge to the desired PO policy under the standard regularizer dominance condition. For the convergence analysis, we prove two important properties of the nonconvex value function. First, when the policy regularizer dominates the environmental shift, the value function satisfies a certain gradient dominance property, so that any stationary point of the value function is a desired PO. Second, though the value function has unbounded gradient, we prove that all the sufficiently stationary points lie in a convex and compact policy subspace $\Pi _ {\Delta}$, where the policy value has a constant lower bound $\Delta>0$ and thus the gradient becomes bounded and Lipschitz continuous. Experimental results also demonstrate that our 0-FW algorithm is more effective than the existing algorithms in finding the desired PO policy.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

论文标题：**Achieve Performatively Optimal Policy for Performative Reinforcement Learning**  
（实现表现性强化学习中的表现最优策略）  
作者：Ziyi Chen, Heng Huang  
来源：ICLR-2026-Rejected-Public（会议检索收录）

---

## 1. 核心问题与整体含义（研究动机与背景）

- **研究背景**：表现性强化学习（Performative Reinforcement Learning, Performative RL）是一种新兴的动态决策框架，其核心特征是**智能体的策略会反过来改变环境动态**。这与传统强化学习假设环境动态固定不变有本质区别，更贴近推荐系统、市场定价、交通调度等真实应用场景。
- **现有方法的不足**：以往针对表现性 RL 的研究仅致力于求解**表现稳定策略（Performatively Stable, PS）**，即最大化一个**近似价值函数**的策略。然而，PS 策略与真正理想的目标——**表现最优策略（Performatively Optimal, PO）**（最大化原始价值函数）之间存在一个**已被证明是严格正的常数差距（constant gap）**。这意味着现有方法无法真正达到系统的最优性能。
- **本文的核心目标**：在多项式计算复杂度内，收敛到**表现最优（PO）策略**，突破前人只能达到表现稳定（PS）策略的限制。这是该领域首次从理论层面获得 PO 策略的求解保证。

---

## 2. 方法论：核心思想、技术细节与算法流程

- **核心思想**：将**零阶（Zeroth-Order）梯度近似**与数值优化中的**Frank-Wolfe 框架**相结合，来求解最大化原始价值函数的表现最优策略。
- **提出的算法**：**0-FW 算法（Zeroth-Order Frank-Wolfe Algorithm）**。具体来说：
  - 在 Frank-Wolfe 迭代框架下，用零阶方法近似计算**表现策略梯度（performative policy gradient）**，从而规避了直接计算梯度可能面临的困难（如环境动态不可微或难以显式建模）。
  - 目标是在**标准正则化主导条件（regularizer dominance condition）**下，实现对 PO 策略的收敛。
- **理论分析中的两个关键性质（针对非凸价值函数）**：
  1. **梯度支配性质（Gradient Dominance）**：当策略正则化项主导环境偏移（environmental shift）时，价值函数满足某种梯度支配条件，使得价值函数的**任意驻点（stationary point）都恰好是期望的 PO 策略**。这一性质保证了优化过程不会陷入坏的局部最优。
  2. **有界梯度与策略子空间**：尽管价值函数的梯度在全局上无界，作者证明了**所有“充分驻点”（sufficiently stationary points）都位于一个凸且紧致的策略子空间 Π_Δ 中**，在该子空间上策略值存在一个正常数下界 Δ > 0，从而梯度在该子空间上变为**有界且 Lipschitz 连续**——这为收敛性分析提供了关键前提。
- **最终理论结果**：获得了**首个多项式计算复杂度**的收敛结果，证明 0-FW 算法能够收敛到 PO 策略，且其性能严格优于此前的 PS 策略。

---

## 3. 实验设计

- **实验场景/数据集**：论文摘要中仅指出“实验结果也表明我们的 0-FW 算法在寻找期望 PO 策略方面比现有算法更有效”，但**没有明确说明具体使用了哪些数据集或模拟场景**。
- **Benchmark**：基于摘要推断，对比对象为现有表现性 RL 算法（即求解 PS 策略的方法）。
- **对比方法**：摘要未列出具体对比算法名称。
- **说明**：由于所获材料仅为摘要，实验设计的完整细节（场景设置、环境动态模型、任务类型）在可获取的文本中**未被详细披露**。

---

## 4. 资源与算力

- **原文未提供任何关于 GPU 型号、数量、训练时长或计算资源的说明。**
- 当前可获取的内容（摘要与元数据）中不涉及算力描述，因此无法总结该信息。

---

## 5. 实验数量与充分性

- **实验数量**：摘要仅提及进行了实验并验证了有效性，**未给出具体实验组数、消融实验或不同数据集的对比信息**。
- **充分性与客观性评估**：
  - 从摘要文字无法判断实验的覆盖范围与公平性。
  - 由于本文是理论导向型工作（以多项式复杂度收敛证明为核心贡献），实验可能主要作为理论结果的补充验证，但在缺乏细节的情况下，难以评估其充分性。
  - 需要获取论文全文中的实验章节才能做出客观判断。

---

## 6. 主要结论与发现

- **理论突破**：提出了 0-FW 算法，**首次在多项式复杂度内收敛到表现最优（PO）策略**，弥补了此前只能收敛到表现稳定（PS）策略的不足。
- **关键证明**：证明了价值函数在正则化主导条件下的梯度支配性质，以及驻点所在凸紧致子空间的存在性，为算法收敛性提供扎实的数学基础。
- **实验验证**：初步实验结果表明 0-FW 算法在求解 PO 策略上的效果优于已有算法。

---

## 7. 优点

- **理论创新性强**：突破了表现性 RL 领域长期停留在 PS 策略的局限，首次给出 PO 策略的多项式复杂度收敛保证，属于领域内的重要进步。
- **方法设计巧妙**：将零阶优化与 Frank-Wolfe 框架结合，规避了策略与环境动态耦合时梯度难以精确计算的问题，实用性较强。
- **理论分析扎实**：通过证明梯度支配性和驻点的有界性两个关键性质，为非凸优化问题提供了清晰的收敛路径，逻辑严密。
- **意义深远**：为“策略影响环境动态”的现实场景（如推荐、定价、调控）提供了可求解的更优策略方案，有较强的应用潜力。

---

## 8. 不足与局限

- **实验信息匮乏**：摘要未披露具体实验场景、数据集、基线和消融研究，无法验证实验的广度与结论的普适性。
- **假设条件较强**：理论与算法依赖于“策略正则化项主导环境偏移”等条件，这在部分真实场景中可能难以满足，限制了其适用范围。
- **存在拒稿记录**：该论文在 ICLR-2026 被拒稿（来源标注为 Rejected-Public），可能说明审稿人认为论文在实验部分、写作或贡献显著性上仍有不足，需谨慎参考其结论。
- **实际部署距离未知**：零阶方法通常面临样本效率较低的挑战，但摘要中未讨论样本复杂度或真实环境部署的可行性，这可能是实际应用中的潜在瓶颈。

---

（完）
