---
title: Zeroth-Order Constrained Optimization from a Control Perspective via Feedback Linearization
title_zh: 基于反馈线性化的控制视角零阶约束优化
authors: "Runyu Zhang, Gioele Zardini, Asuman E. Ozdaglar, Jeff S Shamma, Na Li"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=nzRosESf0H"
tags: ["query:rl-control"]
score: 7.0
evidence: 从控制视角用反馈线性化处理约束零阶优化，无需凸子问题即可保证可行性。
tldr: 未知约束下的安全无导数优化是学习与控制中的挑战，现有零阶方法多假设白盒约束或凸设置。本文提出控制论框架ZOFL，利用反馈线性化处理等式与不等式约束，只依赖噪声采样的梯度估计即可保证可行性。该方法无需求解昂贵的凸子问题，适用于非凸黑盒约束场景。该工作为约束优化提供了新的控制理论工具。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有零阶约束优化多假设白盒约束或凸设置，无法处理一般非凸黑盒约束。
method: 提出ZOFL系列算法，用反馈线性化处理等式与不等式约束，仅需噪声梯度估计。
result: 在非凸黑盒约束下可证地保证可行性，且避免求解昂贵凸子问题。
conclusion: 为黑盒约束优化提供了一种可证明的安全控制视角方法，拓展了实用范围。
---

## Abstract
Designing safe derivative-free optimization algorithms under unknown constraints is a fundamental challenge in modern learning and control. Most existing zeroth-order (ZO) approaches typically assume white-box constraints or focus on convex settings, leaving the general case of nonconvex optimization with black-box constraints largely open. We propose a control-theoretic framework for ZO constrained optimization that enforces feasibility without relying on solving costly convex subproblems. Leveraging feedback linearization, we introduce a family of ZO feedback linearization (ZOFL) algorithms applicable to both equality and inequality constraints. Our method requires only noisy, sample-based gradient estimates yet provably guarantees constraint satisfaction under mild regularity conditions. We establish finite-time bounds on constraint violation and further present a midpoint discretization variant that further improves feasibility without sacrificing optimality. Empirical results demonstrate that ZOFL consistently outperforms standard ZO baselines, achieving competitive objective values while maintaining feasibility.

---

## 论文详细总结（自动生成）

# 基于反馈线性化的控制视角零阶约束优化（ZOFL）——论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题定义**：在未知的、黑盒约束条件下，设计安全且无需梯度的（导数自由 / zeroth-order, ZO）优化算法，是学习与控制领域的基础性挑战。
- **现有缺口**：
  - 大多数零阶方法假设约束是白盒的（即约束函数解析形式已知），或仅关注凸优化设置。
  - 对于“非凸目标 + 非凸黑盒约束”的一般情形，目前缺乏可证明可行性的算法。
- **核心动机**：在现实应用（如安全控制、参数调优）中，目标函数和约束往往只能通过噪声采样观测，无法获得解析梯度；同时约束必须严格满足。因此需要一种不依赖梯度信息、不假设凸性、且能保证可行性的零阶优化框架。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **核心思想**：将约束优化问题视为一个动态系统的控制问题，利用反馈线性化（Feedback Linearization）将约束追踪转化为线性系统的镇定问题，从而在不求解昂贵凸子问题的情况下保证可行性。
- **算法族**：提出一类零阶反馈线性化算法（ZOFL），统一适用于等式约束与不等式约束。
- **关键技术细节**：
  - 仅使用基于噪声采样的梯度估计（即零阶梯度估计），不依赖约束的解析梯度或二阶信息。
  - 通过反馈线性化设计控制器，使约束度量（constraint violation）随时间衰减并保持在可行域内。
  - 针对不等式约束，通过适当的约束转换（如激活机制或松弛变量）纳入反馈线性化框架。
  - 还提出了“中点离散化变体”（midpoint discretization variant），进一步提高可行性的精细程度而不牺牲最优性。
- **理论保证**：在温和的正则性条件下，给出了约束违反量的有限时间界（finite-time bounds）。
- **算法流程（文字说明）**：
  1. 初始化可行或不可行的状态点，设定约束动力学。
  2. 在每次迭代中，对目标函数和约束函数进行噪声采样，估计零阶梯度。
  3. 根据反馈线性化控制律计算更新方向，使约束度量（如等式残差或不等式违量）沿期望的线性动态收敛到零。
  4. 更新状态变量，重复直至收敛。
- **与现有方法的区别**：不要求求解凸子问题（如投影或QP子问题），因此计算成本较低，且可处理非凸黑盒约束。

## 3. 实验设计

- 由于论文完整PDF无法获取，仅依据摘要和元数据，实验部分细节有限。但从摘要可知：
  - **场景/基准**：使用了若干标准零阶优化基准问题（具体名称未在摘要中提及），包含等式与不等式约束场景。
  - **对比方法**：与“标准零阶优化基线”（standard ZO baselines）进行对比。
  - **评估指标**：目标函数值（objective values）和约束可行性（feasibility）。
- **主要结果**：ZOFL 一致优于标准零阶基线，在保持可行性的同时达到有竞争力的目标值。

## 4. 资源与算力

- 文中（摘要和元数据）**未提及**任何具体的计算资源信息，如GPU型号、数量、训练时长、集群规模等。
- 由于该工作属于优化算法研究，实验规模可能较小（典型为合成函数或低维控制问题），但现有提供的信息不足以确认。
- 需要指出：该论文文本未提供算力相关说明，因此无法评估其计算成本。

## 5. 实验数量与充分性

- **已知实验数量**：从摘要看，至少包含对等式约束和不等式约束两类场景的实验，且与多个标准零阶基线做了对比，并验证了中点离散化变体的效果（可能包含消融性质的对比）。
- **充分性评估**：
  - **优点**：覆盖了等式与不等式两种主要约束类型，并对比了基线，说明了可行性与目标值之间的权衡。
  - **不足**：由于无法查看正文，不确定是否包含不同维度、不同噪声水平、不同约束复杂度的系统性实验，也未明确消融实验的数量。因此**无法充分判断实验的全面性与公平性**。仅凭摘要，实验证据较为有限。

## 6. 主要结论与发现

- 提出了一个全新的控制论视角来求解零阶约束优化问题，利用反馈线性化实现了对等式和不等式黑盒约束的可行保证。
- 该方法**无需求解昂贵凸子问题**，且仅依赖噪声梯度估计即可在温和正则性条件下获得有限时间的约束违反界。
- 提出了中点离散化变体，在保持最优性的前提下改善可行性。
- 实验表明，ZOFL 相比标准零阶基线在保持可行性方面具有明显优势，目标值也具有竞争力。

## 7. 优点

- **理论创新**：将反馈线性化这一经典控制工具引入零阶约束优化，为黑盒约束优化提供了新思路。
- **强可行性保证**：在非凸、黑盒约束下仍能给出约束违反的有限时间界，这是现有零阶方法难以做到的。
- **计算高效**：避免求解凸子问题，只依赖采样梯度，降低了每步迭代的计算开销。
- **适用性广**：同时适用于等式和不等式约束，且不要求约束凸性，面向实际工程问题。
- **理论-实践结合**：从理论界到算法变体设计（中点离散化）都体现了对实用性的考虑。

## 8. 不足与局限

- **实验信息不够透明**：由于无法获取完整论文，实验细节未知；从摘要看，对比基线仅表述为“标准ZO基线”，缺乏具体名称和配置，难以独立复现与验证。
- **未报告算力资源**：没有提供任何计算开销数据，无法评估实际工程成本。
- **可能依赖条件**：理论保证依赖于“温和正则性条件”，但具体条件（如约束满足约束规格、目标光滑性、噪声分布等）未在摘要中说明，实际应用中可能受限。
- **黑盒约束的采样成本**：虽然避免凸子问题，但零阶梯度估计通常需要大量采样，尤其在高维问题中可能带来较高的样本复杂度；文中未提及样本复杂度的具体分析。
- **应用范围限制**：反馈线性化通常要求系统具有特定结构（匹配条件），尽管该文将其用于优化问题，但推广到一般非控制场景的普适性仍需验证。

---

（完）
