---
title: "Online Multi-objective Convex Optimization: A Unified Framework and Joint Gradient Descent"
title_zh: 在线多目标凸优化：统一框架与联合梯度下降
authors: "Jieyuan Guo, Lizhen Shao, Fangyuan Zhao"
date: 2025-09-04
pdf: "https://openreview.net/pdf?id=RnNqSYqEcm"
tags: ["query:rl-control"]
score: 8.0
evidence: 提出在线多目标凸优化框架，结合强对偶与联合梯度下降算法。
tldr: 已有在线凸优化通常只处理单一目标，难以应对现实中的多目标冲突问题。本文提出在线多目标凸优化（OMCO）框架，定义新的多目标遗憾并利用凸优化强对偶理论推导其等价形式。进一步提出在线联合梯度下降算法，证明可实现亚线性多目标遗憾。该工作将单目标OCO统一为OMCO的特例，为多目标在线学习提供了理论支撑。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有在线凸优化研究多针对单一目标，无法直接处理实际应用中的多目标冲突优化问题。
method: 提出OMCO框架，用强对偶推导多目标遗憾的等价形式，并设计在线联合梯度下降算法。
result: 证明当目标数退化为1时OMCO遗憾退化为OCO遗憾，且联合梯度下降实现亚线性遗憾。
conclusion: 该框架统一了单目标与多目标在线凸优化，为多目标在线学习提供了新理论工具。
---

## Abstract
Online Convex Optimization (OCO) usually addresses the learning task with a single objective; however, in real-world applications, multiple conflicting objectives often need to be optimized simultaneously. In this paper, we present an Online Multi-objective Convex Optimization (OMCO) framework with a novel multi-objective regret. We prove that, when the number of objectives in OMCO decreases to one, the regret is equal to the regret in OCO, thus unifying the OCO and OMCO frameworks. To facilitate the analysis of the proposed novel regret, we derive its equivalent form using the strong duality theory of convex optimization. Moreover, we propose an Online Joint Gradient Descent algorithm and prove that it achieves a sublinear multi-objective regret according to the equivalent regret form. Experimental results on several real-world datasets validate the effectiveness of our proposed algorithm.

---

## 论文详细总结（自动生成）

# 在线多目标凸优化：统一框架与联合梯度下降——论文总结

## 1. 核心问题与整体含义

- **研究动机**：传统的在线凸优化（OCO）通常只针对单一目标函数进行在线学习，但在实际应用中（如资源调度、推荐系统、网络优化等）经常需要同时优化多个相互冲突的目标，而现有OCO框架难以直接处理这类多目标冲突问题。
- **核心问题**：如何将在线凸优化从单目标扩展到多目标，并定义合理的多目标遗憾（multi-objective regret）来衡量算法性能，同时设计高效的在线优化算法。
- **整体含义**：该论文提出一个在线多目标凸优化（OMCO）统一框架，并在理论上将单目标OCO作为其特例，从而为多目标在线学习提供了统一的理论基础和新的工具，具有重要的理论意义。

## 2. 方法论

- **统一框架（OMCO）**：
  - 提出一个在线多目标凸优化框架，在该框架中，学习者每一轮需要同时最小化多个凸损失函数。
  - 定义了新颖的多目标遗憾（multi-objective regret）概念，用于衡量算法与最优固定决策之间的累积目标差异。
  - 利用凸优化中的**强对偶理论**，推导出该多目标遗憾的**等价形式**，从而便于理论分析。
- **关键性质——统一性**：
  - 证明了当目标数量退化为1时，所提出的多目标遗憾恰好退化为标准OCO中的遗憾，由此将OCO统一为OMCO的特例。
- **算法——在线联合梯度下降**：
  - 提出“Online Joint Gradient Descent”算法，该算法在每一轮同时对所有目标的梯度信息进行联合处理并更新决策。
  - 基于等价的遗憾形式，证明了该算法能够实现**亚线性多目标遗憾**（即遗憾随轮数增长的速度低于线性）。
- **技术要点**：核心在于利用强对偶将复杂的多目标遗憾转换为更易分析的形式，进而将多目标优化问题分解或降维处理，使梯度类方法的收敛性分析成为可能。

## 3. 实验设计

- 根据摘要，论文在**多个真实世界数据集**上进行了实验（具体数据集名称未在提供的摘要中列出）。
- 实验用于验证所提出的在线联合梯度下降算法的**有效性**。
- 摘要中未明确说明具体的基准（benchmark）方法、对比算法或评估指标。由于仅提供摘要文本，无法获知实验的详细设置、基线方法和具体结果数值。
- 需要指出：由于缺少正文信息，实验部分的具体细节（如数据集名称、任务类型、对比算法等）在现有材料中**不可见**，只能确认作者声称在真实数据集上取得了有效结果。

## 4. 资源与算力

- 在提供的摘要与元数据中，**没有提及**任何计算资源信息，包括GPU型号、数量、训练时长、集群配置等。
- 因此，无法评估该论文的算力消耗或可复现性所需资源。这一点需要阅读论文全文或附录才能补充。

## 5. 实验数量与充分性

- 从摘要看，作者只提到“多个真实世界数据集”上的实验结果，但**没有给出具体实验组数**，如数据集数量、消融实验、参数敏感性实验、不同目标数量下的对比等。
- 由于缺乏细节，**无法判断实验的充分性、客观性和公平性**。常见的多目标优化实验应至少包含不同目标数设定、与单目标基线的对比、与已有重标量化和Pareto方法的对比，以及多目标遗憾的收敛曲线等，但当前摘要未展示这些内容。
- 总体而言，从摘要看实验覆盖度有限，需要在全文确认。

## 6. 主要结论与发现

- 提出了在线多目标凸优化（OMCO）框架，并定义了一种新的多目标遗憾，该遗憾在目标数=1时与OCO遗憾一致，从而实现了单目标与多目标在线凸优化的**统一**。
- 利用强对偶理论推导了多目标遗憾的等价形式，简化了分析。
- 提出了在线联合梯度下降算法，并证明其具有**亚线性多目标遗憾**界。
- 在多个真实世界数据集上的实验验证了算法的有效性。

## 7. 优点

- **理论贡献突出**：将单目标OCO统一为多目标OMCO的特例，拓展了在线优化的研究范围。
- **遗憾定义合理**：新定义的多目标遗憾与经典OCO遗憾自然衔接，便于与已有理论对比。
- **分析工具新颖**：将凸优化的强对偶理论引入在线多目标遗憾分析，提供了新的理论视角。
- **算法简洁有效**：提出的联合梯度下降算法思路直观，同时具备理论保证（亚线性遗憾），易于实现。
- **潜在应用广泛**：为资源分配、在线决策等真实多目标冲突问题提供了可用的学习框架。

## 8. 不足与局限

- **实验信息不充分**：摘要中仅提到真实数据集，但未列出具体数据集、任务、对比方法、指标等，无法评估实验的完整性和说服力。
- **缺少与已有方法的对比**：多目标优化领域已有在线Pareto优化、标量化等方法，论文是否与之比较未知。
- **理论方面可能存在限制**：强对偶等价形式依赖于凸性和某些约束条件，对于非凸或多约束问题是否成立未在摘要中说明。
- **应用范围局限**：OMCO框架主要面向凸损失函数，而许多实际问题是非凸的，可能导致算法在这些场景下失效。
- **未报告算力与可复现性细节**：无法判断训练过程的计算成本。
- **缺乏消融和鲁棒性分析**：不清楚目标数量变化、损失函数尺度差异、决策空间维度等因素对算法性能的影响。

（完）
