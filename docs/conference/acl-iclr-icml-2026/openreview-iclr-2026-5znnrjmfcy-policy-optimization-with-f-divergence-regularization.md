---
title: Policy Optimization with $f$-Divergence Regularization
title_zh: 基于f散度正则化的策略优化
authors: "Dawei Zhang, Junfeng Wen"
date: 2025-09-14
pdf: "https://openreview.net/pdf?id=5ZnNrjmFCY"
tags: ["query:rl-control"]
score: 8.0
evidence: 基于f散度正则化的广义策略迭代，扩展TRPO和PPO
tldr: 在强化学习策略迭代中，KL散度正则化（如TRPO、PPO）虽广泛使用，但未必是各类环境的最佳选择。该工作将策略迭代的散度正则化推广到更一般的f散度，设计出一族新算法，在理论上保证策略改进。这使得研究者能根据环境特性灵活选择散度函数，扩展了策略优化工具箱，对提升训练稳定性和避免灾难性失败具有直接帮助。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 信任域策略优化等算法局限于KL散度，而KL散度未必适合所有环境，需要更一般化的策略迭代框架。
method: 将策略迭代中的KL正则化推广到f散度正则化，设计新一族策略优化算法并给出理论改进保证。
result: 新算法族在理论上有策略改进保证，并允许针对不同环境选择合适的散度函数。
conclusion: 拓展了策略优化的正则化设计空间，为稳定高效强化学习提供更通用的算法族。
---

## Abstract
Policy iteration is a common algorithm framework in reinforcement learning (RL) to find the optimal policy for a Markov decision process (MDP). To improve training stability and prevent catastrophic failure, researchers have developed several policy iteration algorithms based on the Kullback-Leibler (KL) divergence, such as the well-known trust region policy optimization (TRPO) and proximal policy optimization (PPO). However, these methods are limited to the KL divergence, which may not be the best choice for all environments. In this work, we generalize previous work using a more general form of divergence, the $f$-divergence, and design a new family of algorithms that can improve learning policy with theoretical improvement guarantees. Our method, $f$-divergence-regularized policy optimization ($f$RPO), can be applied to both online and offline RL settings. Empirical studies show that $f$RPO can outperform existing methods, including the commonly used KL divergence, on common benchmark problems in RL.

---

## 论文详细总结（自动生成）

# 论文总结：基于f散度正则化的策略优化（Policy Optimization with $f$-Divergence Regularization）

## 1. 核心问题与整体含义

- 强化学习（RL）中，策略迭代（Policy Iteration）是求解马尔可夫决策过程（MDP）最优策略的常用框架。
- 为了提高训练稳定性并避免灾难性失败，研究者提出了基于 KL 散度正则化的策略迭代算法，典型代表包括 TRPO 和 PPO。
- 然而，这些方法局限于 KL 散度，而 KL 散度未必是所有环境下的最佳选择。
- 本文的核心问题：**能否将散度正则化从 KL 散度推广到更一般的 $f$-散度，从而设计出通用且具有理论改进保证的策略优化算法族？**
- 整体意义：该工作为策略优化中正则化项的选择提供了更广泛的设计空间，使研究者可以根据环境特性灵活选择散度函数，有助于提升训练稳定性与算法适应性。

## 2. 提出的方法论

- 核心思想：将传统策略优化中的 KL 散度正则项替换为更一般的 $f$-散度，构造一类广义正则化策略迭代算法。
- $f$-散度定义：$D_f(p \| q) = \int q(x) f\left(\frac{p(x)}{q(x)}\right) dx$，其中 $f$ 为凸函数且 $f(1)=0$。KL 散度是 $f(t)=t\log t$ 时的特例。
- 算法框架：通过在策略迭代目标中加入 $f$-散度正则项（或约束），在更新策略时限制新策略与参考策略（如旧策略或行为策略）的偏离程度。
- 理论保证：文中给出了策略改进的理论下界，保证在适当条件下目标策略单调改进。
- 提出算法族：命名为 $f$-散度正则化策略优化（$f$RPO），通过选取不同的 $f$ 函数可恢复或推广 TRPO、PPO 等已有方法。
- 适用范围：该方法可同时应用于**在线 RL** 与**离线 RL** 设置：在线时将新策略与旧策略进行散度约束，离线时约束新策略与行为策略（behavior policy）的距离。
- 注意：由于提供文本仅有摘要，具体目标函数形式、优化步骤、实现细节未详细披露，以上属于基于摘要和领域知识的合理概括。

## 3. 实验设计

- 摘要中仅提及在“常见强化学习基准问题”（common benchmark problems in RL）上进行实验。
- 对比方法：主要包括现有策略优化方法，尤其是基于 KL 散度的 TRPO、PPO 等。
- 未列出具体环境名称（如 MuJoCo、Atari、DM Control 等），也未说明在线/离线具体数据集。
- 评估指标、任务数量、超参数设置等细节本文档未提供。

## 4. 资源与算力

- 原始论文文本（摘要及元数据）中**未提及**任何关于 GPU 型号、数量、训练时长、计算资源等具体信息。
- 因此无法判断该研究的算力投入与训练成本。

## 5. 实验数量与充分性

- 摘要仅给出了定性结论：$f$RPO 在常见基准上优于包括 KL 散度在内的现有方法。
- **没有提供实验数量、消融实验、统计显著性分析、重复次数等细节**，因此无法评估其实验充分性与公平性。
- 从元数据看，该工作有一个审稿评分（score 8.0），但这属于外部评价，不能代替对实验证据的具体分析。

## 6. 主要结论与发现

- 将策略迭代从 KL 散度正则化推广到一般 $f$-散度正则化是可行的。
- 所提出的 $f$RPO 算法族具有理论上的策略改进保证。
- 实验表明，在常见基准任务上，$f$RPO 可以优于现有方法（包括 KL 散度正则化方法）。
- 这为强化学习策略优化提供了更通用、更灵活的正则化方案。

## 7. 优点

- **理论统一性**：将 TRPO、PPO 等 KL 散度方法纳入一个更一般的 $f$-散度框架，具有理论普适性。
- **设计灵活性**：允许根据具体环境特点选择合适的 $f$ 散度，可能获得更好的稳定性与性能。
- **兼顾在线与离线**：同一框架同时适用于在线和离线 RL，应用范围更广。
- **有改进保证**：并非简单启发式扩展，而是带有策略改进理论下界。

## 8. 不足与局限

- **实验信息不足**：摘要中未给出具体基准、任务数量、对比细节，难以验证结论的普遍性。
- **缺乏消融分析**：未说明不同 $f$ 函数的影响、超参数敏感性等，用户难以判断何时应选择何种散度。
- **计算开销未讨论**：更一般的 $f$-散度可能在计算或采样上比 KL 散度更复杂，文中未提及。
- **实际性能增益有限**：仅定性宣称“优于现有方法”，未给出量化提升幅度。
- **可复现性受限**：由于提供文本缺少伪代码和实验细节，第三方难以直接复现。

（完）
