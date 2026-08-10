---
title: Doubly Regularized Markov Decision Processes for Robust Reinforcement Learning
title_zh: 双重正则化马尔可夫决策过程用于鲁棒强化学习
authors: "Yiting He, Zhishuai Liu, Pan Xu"
date: 2026-04-30
pdf: "https://openreview.net/pdf/631ef490b04c4af919d8164648d22418e43b9044.pdf"
tags: ["query:rl-control"]
score: 7.0
evidence: 双重正则化MDP框架面向鲁棒策略学习，属于强化学习策略优化方向
tldr: 该工作针对现有正则化马尔可夫决策过程理论局限于标准强化学习的问题，提出结合策略与动力学双重正则化的框架，以支持连续动作空间上的鲁棒策略学习。作者设计了基于乐观原理的在线算法，并在表格与线性设定下给出首批有限样本遗憾界，为鲁棒强化学习提供了新理论分析工具，对机器人等应用中的策略训练稳定性有参考价值。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有正则化马尔可夫决策过程理论大多停留在标准强化学习，缺少鲁棒学习视角下的统一分析与连续动作空间支持。
method: 提出策略与动力学双重正则化的马尔可夫决策过程框架，并设计基于乐观原理的在线算法进行鲁棒策略学习。
result: 在表格与线性设定下给出首批有限样本遗憾界，证明算法在连续动作空间中的理论有效性。
conclusion: 将正则化马尔可夫决策过程理论拓展到鲁棒强化学习，为实际策略训练稳定性提供新分析工具。
---

## Abstract
Empirical successes show that regularization improves the stability and efficiency of reinforcement learning (RL), with applications in robotics and post-training of large language models. Yet, theoretical analyses of regularized Markov decision processes (MDPs) have mostly been confined to the standard RL setting. In this work, we investigate regularized MDPs through the lens of robust RL. We introduce a doubly regularized MDP framework that combines policy and dynamics regularizations, enabling robust policy learning while naturally accommodating continuous action spaces. Within this framework, we develop an optimism-based online algorithm and provide the first finite-sample regret guarantees in both tabular and linear settings. Our results show that algorithms for doubly regularized MDPs are as sample-efficient as well-studied robust MDP algorithms, while additionally benefiting from the flexibility of soft policies. We further design practical algorithmic variants for both settings and demonstrate empirically that our approach efficiently and effectively handles function approximation and exploration in large state-action spaces, achieving robust performances.

---

## 论文详细总结（自动生成）

## 论文总结

### 1. 核心问题与整体含义（研究动机与背景）
- 研究动机：正则化在强化学习（RL）中已被经验证明能提升训练稳定性与效率，广泛应用于机器人控制和大语言模型后训练等场景；但现有正则化马尔可夫决策过程（MDP）的理论分析大多局限于标准 RL 设定，缺乏鲁棒学习视角下的统一分析。
- 核心问题：如何在鲁棒强化学习框架下引入正则化，并支持连续动作空间上的策略学习，同时给出有理论保证的算法。
- 整体含义：该工作将正则化 MDP 理论拓展到鲁棒 RL，提出“双重正则化”框架，兼顾策略柔性与动力学不确定性，为鲁棒策略学习提供了新的建模与分析方法。

### 2. 方法论：核心思想、技术细节与算法流程
- 核心思想：提出双重正则化 MDP 框架，同时引入**策略正则化**（policy regularization）与**动力学正则化**（dynamics regularization）。
  - 策略正则化：鼓励策略保持“软性”（soft policy），提升探索能力和灵活性。
  - 动力学正则化：对转移动力学进行正则化，使策略对环境不确定性具有鲁棒性。
- 框架优势：该框架能够自然适应连续动作空间，突破了以往理论多局限于离散/标准设定的限制。
- 算法设计：基于**乐观原理**（optimism-based）设计在线算法，即在估计模型/策略时采用乐观偏差以鼓励探索。
- 理论结果：在**表格设定**（tabular）与**线性设定**（linear）下，首次给出双重正则化 MDP 的**有限样本遗憾界**（finite-sample regret guarantees）。
- 算法变体：针对两种设定分别设计了实用性算法变体，用于处理函数逼近和大规模状态-动作空间下的探索问题。

### 3. 实验设计（数据集、场景与基准）
- 论文摘要提到“通过实验展示方法能高效处理函数逼近和大规模状态-动作空间中的探索问题，并取得鲁棒性能”。
- 但提供的文本中**没有给出具体数据集、基准环境、对比方法或评估指标**。
- 因此，根据现有材料只能确认：实验涉及大规模状态-动作空间、函数逼近与探索场景，但无法具体说明其 benchmark 设置和对比对象。

### 4. 资源与算力
- 提供的文本中**未提及任何算力信息**，包括 GPU 型号、数量、训练时长等。
- 因此无法评估其计算成本或资源需求。

### 5. 实验数量与充分性
- 从摘要可见，实验主要用于验证算法在实际问题中的有效性和鲁棒性，但**缺少具体实验数量、消融实验、对比实验等细节**。
- 由于提取文本不含实验章节，无法判断实验是否充分、客观、公平。
- 仅从摘要表述看，功能函数逼近与探索的实验可能具有一定代表性，但证据不足以做系统性评估。

### 6. 主要结论与发现
- 双重正则化 MDP 算法在理论上具有与已有鲁棒 MDP 算法相同的样本效率，同时额外获得软策略带来的灵活性。
- 在表格与线性设定下，算法具有可证明的有限样本遗憾界，属于该方向的首批结果。
- 实验表明该框架能有效处理大规模状态-动作空间中的函数逼近与探索，并实现鲁棒性能。

### 7. 优点
- **理论创新**：首次将正则化 MDP 与鲁棒 RL 统一在双重正则化框架下，填补了理论空白。
- **连续动作支持**：框架天然适配连续动作空间，比传统离散设定更具实用价值。
- **可证明保证**：在表格和线性设定下给出有限样本遗憾界，理论保障明确。
- **策略灵活性**：结合软策略，在保证鲁棒性的同时保留探索与策略多样性。
- **算法实用性**：设计了适用于函数逼近场景的变体，兼顾理论与实践。

### 8. 不足与局限
- **实验细节缺失**：提供的文本中未给出具体数据集、基线方法、评价指标和实验规模，难以验证实证部分的充分性与公平性。
- **理论范围有限**：当前保证仅限于表格与线性设定，非线性函数逼近或更一般 MDP 仍未覆盖。
- **算力与资源不明**：未报告计算资源，不利于复现和成本评估。
- **鲁棒性建模的具体形式未说明**：动力学正则化的具体实现方式、不确定性集合构造等细节在摘要中未展开，可能影响实际应用推广。
- **应用边界仍需验证**：虽然提及机器人和大语言模型后训练，但理论实验是否覆盖这些真实场景尚不清楚。

（完）
