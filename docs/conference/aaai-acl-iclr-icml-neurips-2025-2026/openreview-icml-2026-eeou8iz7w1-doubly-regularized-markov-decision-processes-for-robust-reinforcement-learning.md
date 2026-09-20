---
title: Doubly Regularized Markov Decision Processes for Robust Reinforcement Learning
title_zh: 面向鲁棒强化学习的双正则化马尔可夫决策过程
authors: "Yiting He, Zhishuai Liu, Pan Xu"
date: 2026-04-30
pdf: "https://openreview.net/pdf/631ef490b04c4af919d8164648d22418e43b9044.pdf"
tags: ["query:rl-control"]
score: 5.0
evidence: 面向鲁棒强化学习的正则化MDP及遗憾保证
tldr: 正则化能提升强化学习的稳定性与效率，但正则化MDP的理论分析多局限于标准设定。本文从鲁棒RL视角研究正则化MDP，提出结合策略与动态正则化的双正则化MDP框架，可自然处理连续动作空间。作者给出基于乐观的在线算法，并在表格与线性设定下提供首个有限样本遗憾保证，为鲁棒策略学习提供了理论支撑。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 正则化提升RL稳定性，但正则化MDP的理论分析多局限于标准设定。
method: 从鲁棒RL视角提出结合策略与动态正则化的双正则化MDP框架及乐观在线算法。
result: 在表格与线性设定下给出首个有限样本遗憾保证。
conclusion: 为鲁棒策略学习提供了理论基础。
---

## Abstract
Empirical successes show that regularization improves the stability and efficiency of reinforcement learning (RL), with applications in robotics and post-training of large language models. Yet, theoretical analyses of regularized Markov decision processes (MDPs) have mostly been confined to the standard RL setting. In this work, we investigate regularized MDPs through the lens of robust RL. We introduce a doubly regularized MDP framework that combines policy and dynamics regularizations, enabling robust policy learning while naturally accommodating continuous action spaces. Within this framework, we develop an optimism-based online algorithm and provide the first finite-sample regret guarantees in both tabular and linear settings. Our results show that algorithms for doubly regularized MDPs are as sample-efficient as well-studied robust MDP algorithms, while additionally benefiting from the flexibility of soft policies. We further design practical algorithmic variants for both settings and demonstrate empirically that our approach efficiently and effectively handles function approximation and exploration in large state-action spaces, achieving robust performances.

---

## 论文详细总结（自动生成）

# 论文总结：面向鲁棒强化学习的双正则化马尔可夫决策过程

> 说明：提供的 PDF 提取文本仅为 OpenReview 的浏览器验证页面，未包含论文正文。以下总结主要依据论文摘要与元数据，因此涉及公式、算法细节、实验环境和算力等信息时，只能给出摘要层面可确认的内容，无法对正文细节做完整核验。

## 1. 核心问题与整体含义
- **研究动机**：正则化在强化学习（RL）中被证明能提升稳定性与效率，已应用于机器人控制和大型语言模型后训练等场景。
- **理论缺口**：现有关于正则化马尔可夫决策过程（MDP）的理论分析大多局限于标准 RL 设定，缺少从鲁棒 RL 视角的系统研究。
- **整体含义**：论文试图把“策略正则化”和“动态/转移动态正则化”结合，提出双正则化 MDP 框架，使鲁棒策略学习不仅能应对模型不确定性，还能自然适配连续动作空间。
- **目标**：为鲁棒策略学习提供新的理论框架、有限样本遗憾保证，以及可用于大状态-动作空间的实用算法变体。

## 2. 方法论
- **核心思想**：在鲁棒 RL 视角下研究正则化 MDP，提出 **doubly regularized MDP** 框架，同时引入：
  - **策略正则化**：鼓励软策略、提升灵活性与稳定性，并自然支持连续动作空间。
  - **动态正则化**：对动态/转移模型进行正则化，以增强对不确定性的鲁棒性。
- **算法思路**：提出一种基于 **乐观（optimism-based）** 的在线算法。乐观原则通常用于在探索与利用之间平衡，通过对不确定性给予奖励或构造乐观估计来实现高效探索。
- **理论保证**：在 **表格设定** 和 **线性设定** 下，给出首个有限样本遗憾保证。摘要称，双正则化 MDP 算法的样本效率可与已有成熟鲁棒 MDP 算法相当，同时额外获得软策略的灵活性。
- **实用变体**：针对表格与线性两种设定设计实际算法变体，用于处理大状态-动作空间中的函数逼近和探索问题。
- **未提供细节**：具体正则项形式、Bellman 算子、乐观构造方式、遗憾界阶数及其依赖项等，在提供的文本中均未给出，无法进一步展开。

## 3. 实验设计
- **实验场景**：摘要提到在 **表格设定** 和 **线性设定** 下设计实用算法变体，并声称能处理大状态-动作空间中的函数逼近与探索。
- **Benchmark**：提供内容未明确列出具体 benchmark、环境名称或数据集。
- **对比方法**：摘要暗示与“well-studied robust MDP algorithms”进行比较，即成熟鲁棒 MDP 算法，但未给出具体基线名称。
- **评价指标**：摘要提到“样本效率”和“鲁棒性能”，但未给出具体指标、曲线或数值结果。
- **结论**：由于正文缺失，无法确认实验是否覆盖连续控制、机器人任务或语言模型后训练等具体应用。

## 4. 资源与算力
- 提供的摘要与元数据中 **未提及** GPU 型号、GPU 数量、训练时长、CPU/内存等算力信息。
- 因此无法总结该论文的实验资源消耗，也无法判断实验规模与可复现性。

## 5. 实验数量与充分性
- 提供内容未说明具体做了多少组实验、是否包含消融实验、是否覆盖多个随机种子或多种环境。
- 仅从摘要可知作者声称在表格和线性设定下进行了实证验证，并处理大状态-动作空间中的函数逼近与探索。
- 因此，**无法客观评估实验是否充分、是否存在偏差、对比是否公平**。需要正文中的实验章节才能判断。

## 6. 主要结论与发现
- 双正则化 MDP 框架能够将策略正则化与动态正则化结合，从而在鲁棒 RL 中实现鲁棒策略学习。
- 该框架可自然容纳连续动作空间，并受益于软策略的灵活性。
- 在表格和线性设定下，作者给出了首个有限样本遗憾保证，说明算法具有理论上的样本效率。
- 摘要称其样本效率与已有鲁棒 MDP 算法相当，同时额外获得软策略优势。
- 实用算法变体在大状态-动作空间中能有效处理函数逼近与探索，并取得鲁棒性能。

## 7. 优点
- **理论新颖性**：从鲁棒 RL 视角研究正则化 MDP，提出双正则化框架，结合策略正则化与动态正则化。
- **理论贡献明确**：在表格和线性设定下给出有限样本遗憾保证，并声称是首个此类保证。
- **兼顾连续动作空间**：策略正则化使方法更适合连续动作场景，扩展了正则化 MDP 的适用范围。
- **理论与实践结合**：不仅给出理论算法，还设计实用变体，面向大状态-动作空间中的函数逼近与探索。
- **潜在应用价值**：可服务于机器人控制、大模型后训练等需要稳定性与鲁棒性的 RL 场景。

## 8. 不足与局限
- **材料不完整**：提供的 PDF 文本只是验证页面，缺少正文，无法验证公式、定理、算法流程和实验细节。
- **实验信息不足**：未列出数据集、环境、benchmark、基线方法和具体数值，无法判断实验覆盖度与公平性。
- **算力未说明**：未提供任何算力资源信息，影响可复现性评估。
- **理论条件未知**：有限样本遗憾保证所依赖的假设、正则化强度选择、线性设定具体形式等均未在摘要中说明。
- **应用限制未知**：连续动作空间的理论保证是否成立、线性函数逼近之外的深度 RL 场景是否适用，仍需正文确认。
- **潜在偏差风险**：元数据评分为 5.0，且来源为 ICML-2026-Accepted，但在缺少正文的情况下，无法独立评估其方法优越性与实验客观性。

（完）
