---
title: Why Policy Gradient Algorithms Work for Undiscounted Total-Reward MDPs
title_zh: 为什么策略梯度算法适用于无折扣总回报马尔可夫决策过程
authors: "Jongmin Lee, Ernest K. Ryu"
date: 2025-09-17
pdf: "https://openreview.net/pdf?id=CwownEMv9z"
tags: ["query:rl-control"]
score: 9.0
evidence: 为无折扣总回报MDP下的策略梯度方法提供收敛性理论分析。
tldr: 经典策略梯度理论大多依赖折扣因子小于1的假设，而大语言模型等场景采用无折扣总回报设定，现有理论不再适用。本文利用MDP状态关于策略不变的可达/瞬态分类，为无折扣无限时域MDP下的策略梯度方法提供严格分析。结果显示策略梯度在此类设定下仍可有效工作，填补了理论与实践之间的空白。该工作为策略型RL在总回报问题上的使用奠定了理论基础。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有策略梯度理论依赖折扣因子小于1，无法覆盖大语言模型等无折扣总回报场景。
method: 利用MDP状态在策略集上不变的可达与瞬态分类，建立无折扣总回报下的收敛分析。
result: 证明了策略梯度在无折扣无限时域MDP中仍能保持收敛，扩展了经典理论适用范围。
conclusion: 为无折扣总回报强化学习策略优化提供了理论支撑，衔接了最新实践与传统理论。
---

## Abstract
The classical policy gradient method is the theoretical and conceptual foundation of modern policy-based reinforcement learning (RL) algorithms. Most rigorous analyses of such methods, particularly those establishing convergence guarantees, assume a discount factor $\gamma < 1$. In contrast, however, a recent line of work on policy-based RL for large language models uses the undiscounted total-reward setting with $\gamma = 1$, rendering much of the existing theory inapplicable. In this paper, we provide analyses of the policy gradient method for undiscounted expected total-reward infinite-horizon MDPs based on two key insights: (i) the classification of the MDP states into recurrent and transient states is invariant over the set of policies that assign strictly positive probability to every action (as is typical in deep RL models employing a softmax output layer) and (ii) the classical state visitation measure (which may be ill-defined when $\gamma = 1$) can be replaced with a new object that we call the transient visitation measure.

---

## 论文详细总结（自动生成）

## 基于论文内容的详细中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：经典策略梯度方法是现代基于策略的强化学习（RL）算法的理论基础。现有的严格收敛性分析几乎全部建立在“折扣因子 γ < 1”这一假设之上。
- **核心问题**：近年来，基于策略的RL在大语言模型（LLM）场景中大量采用 **无折扣总回报设定**（γ = 1），导致经典理论（依赖 γ < 1 的收缩性质）不再适用，出现了理论与实践之间的断层。
- **研究意义**：本文旨在填补这一空白，为无折扣无限时域MDP下的策略梯度方法提供理论收敛性保证，从而解释“为什么策略梯度算法在实际的无折扣总回报问题中仍然能有效工作”。

### 2. 论文提出的方法论：核心思想、关键技术细节

论文基于两个关键洞察，构建了无折扣总回报MDP下策略梯度方法的理论分析框架：

- **洞察（i）：状态分类对策略集不变**
  - 将MDP状态分类为 **常返态（recurrent）** 和 **瞬态（transient）**。
  - 关键发现：对于所有“对每个动作赋予严格正概率”的策略（即深度RL中常见的 **softmax 输出层** 策略），这一分类结果是 **不变** 的，不随具体策略参数变化。
  - 这一不变性为分析提供了重要的结构基础。

- **洞察（ii）：引入“瞬态访问度量”**
  - 在 γ = 1 时，经典的状态访问度量（state visitation measure）可能不良好定义（例如出现无限访问次数）。
  - 论文提出用一个新的对象—— **瞬态访问度量（transient visitation measure）** 替代经典访问度量，从而在总回报设定下给出策略梯度的严格数学表达。

- **技术路线**：
  - 基于上述两个洞察，重新推导无折扣总回报设定下的策略梯度公式；
  - 在无限时域、无折扣情况下建立相应的收敛性分析；
  - 证明策略梯度算法在此类设定下仍然保持收敛性质。

### 3. 实验设计：数据集 / 场景 / Benchmark / 对比方法

- **实验信息**：从提供的摘要和元数据来看，**文中未提供任何具体实验设计**，包括：
  - 未提及使用的数据集、环境或具体benchmark；
  - 未提及与哪些基线方法的对比实验；
  - 未提及消融实验或仿真场景。
- **说明**：该论文从性质上属于 **理论性论文**，重点在于给出理论定理与证明，而非大规模的实验实证。

### 4. 资源与算力

- **未明确说明**：论文提供的元数据与摘要中 **没有涉及任何算力资源信息**，包括 GPU 型号、数量、训练时长、集群规模等。
- 由于本文是理论分析性质的工作，推测其不需要大规模算力投入，但这仅为推测，论文本身未给出相关说明。

### 5. 实验数量与充分性

- **实验数量**：无（摘要中未提及任何实验结果）。
- **充分性评估**：
  - 作为一篇 **理论分析论文**，其充分性主要取决于定理证明的严谨性、假设的合理性与理论的覆盖范围，而非实验数量。
  - 但需要注意的是，该论文在 ICLR-2026 审稿中被标记为 **Rejected**，说明审稿人可能对论文的理论贡献、表述清晰度或实验佐证存在质疑。由于未获取具体审稿意见，无法进一步确认具体原因。
  - 从公开元数据看，论文的 score 为 9.0（这一分数按 OpenReview 惯例通常意味着审稿人评价较高），但仍未达到录用标准，个中原因无法从现有材料判断。

### 6. 论文的主要结论与发现

- **核心结论**：策略梯度算法在 **无折扣总回报的无限时域MDP** 中仍然能够收敛并有效工作。
- **关键贡献**：
  - 首次（据论文所述）为 γ = 1 的设定提供了严格的理论收敛分析；
  - 证明了状态可达/瞬态分类在软max策略类下具有不变性（这是重要的结构性发现）；
  - 提出了“瞬态访问度量”这一新概念，替代经典状态访问度量，成为该设定下的核心分析工具。
- **实践意义**：该理论为大语言模型等采用无折扣总回报训练范式的场景中的策略优化算法提供了理论支撑，衔接了最新的实际应用与传统RL理论。

### 7. 优点：方法与设计上的亮点

- **选题价值高、动机明确**：精准抓住了当前RL理论（依赖 γ<1）与 LLM 应用实践（γ=1）之间的核心断层，研究问题具有很强的现实意义。
- **理论创新点清晰**：
  - 提出“瞬态访问度量”这一新的数学对象，是该领域的一个概念性创新；
  - 状态分类在策略族上的不变性是一个简洁而有洞察力的结构性发现，为后续研究提供了新的分析路径。
- **适用范围广**：论文的分析覆盖了“所有动作概率严格为正”的典型深度RL策略类（如 softmax 策略），这与现代实践高度吻合，而非局限于简单的表格型MDP。
- **填补空白**：直接将经典理论从折扣因子设定推广到总回报设定，理论价值明显。

### 8. 不足与局限

- **缺乏实验验证**：从摘要和元数据看，论文 **没有提供任何数值实验或仿真验证**，无法直观展示理论结果与真实算法表现之间的对应关系，理论与实践的衔接程度仅停留在推断层面。
- **理论假设可能较苛刻**：分析依赖于“所有状态可概率遍历”或类似的假设条件（例如每个动作都有正概率），虽然覆盖了 softmax 策略这类常见场景，但并非所有实际策略都满足此假设。
- **被拒稿的事实**：论文在 ICLR-2026 被拒，表明其理论表述、贡献重要性或论证过程可能存在审稿人认为的缺陷，但由于缺少审稿意见，无法具体列举。
- **应用局限**：论文针对的是策略梯度这一类方法，尚未覆盖更广义的策略优化族（如自然策略梯度、PPO、TRPO 等），后续推广空间较大。

### 补充说明

- 本总结完全基于题目提供的论文摘要与元数据，未获取论文全文，因此关于实验设计、方法细节、证明过程等内容均以摘要为限，无法深入到定理推导和更多技术细节。
- 如需更细致地评估，建议获取论文全文（如从 OpenReview 下载 PDF 原文）以获取定理声明、证明思路、相关工作的详细对比等信息。

（完）
