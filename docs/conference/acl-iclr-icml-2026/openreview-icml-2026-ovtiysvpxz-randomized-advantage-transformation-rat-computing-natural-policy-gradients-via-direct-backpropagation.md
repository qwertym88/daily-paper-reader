---
title: "Randomized Advantage Transformation (RAT): Computing Natural Policy Gradients via Direct Backpropagation"
title_zh: 随机优势变换（RAT）：通过直接反向传播计算自然策略梯度
authors: Mingfei Sun
date: 2026-04-30
pdf: "https://openreview.net/pdf/83bb516cfadecaaea6ebef0227b57548cbf8faf8.pdf"
tags: ["query:rl-control"]
score: 8.0
evidence: 通过反向传播与优势变换实现自然策略梯度估计，直接关乎策略优化
tldr: 自然策略梯度能改善优化几何，但估计和求逆Fisher矩阵代价高昂。本文提出RAT方法，把正则化自然梯度改造为带变换优势的普通策略梯度，利用Woodbury公式和随机块Kaczmarz迭代直接反传计算，避免显式构造Fisher矩阵。理论收敛性分析表明该方法的可靠性，为策略优化提供了高效实用工具。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 自然策略梯度计算代价高，受限于Fisher矩阵估计与求逆。
method: 通过Woodbury公式与随机块Kaczmarz迭代，将正则化自然梯度转化为变换优势的形式。
result: 实现了无需显式Fisher构造和共轭梯度求解器的直接反传算法，并给出收敛保证。
conclusion: 为RL策略优化提供了一种高效且通用的自然策略梯度近似方法。
---

## Abstract
Natural policy gradients improve optimization by accounting for the geometry of distribution space, but their practical use is limited by the cost of estimating and inverting the Fisher matrix. We present Randomized Advantage Transformation (RAT), a method for estimating Tikhonov-regularized natural policy gradients via direct backpropagation. By applying the Woodbury formula, we reformulate the regularized natural gradient as vanilla policy gradients with a transformed advantage. RAT computes this transformation efficiently via randomized block Kaczmarz iterations on on-policy mini-batches, avoiding explicit Fisher construction, conjugate-gradient solvers, and architecture-specific approximations. We provide convergence guarantees for RAT and demonstrate empirically that it matches or exceeds established natural-gradient methods across continuous and visual control benchmarks, while remaining simple to implement and compatible with various architectures.

---

## 论文详细总结（自动生成）

# 论文总结：Randomized Advantage Transformation (RAT)

## 1. 核心问题与整体含义

- 自然策略梯度（Natural Policy Gradient, NPG）通过考虑策略分布空间的几何结构来改善强化学习中的策略优化，但其实际应用受到高计算成本的限制。
- 主要瓶颈在于：需要估计 Fisher 信息矩阵并对其求逆，这一过程在大规模策略参数或高维状态空间中代价高昂。
- 本文提出 **RAT（随机优势变换）** 方法，旨在通过直接反向传播高效地近似估计带 Tikhonov 正则化的自然策略梯度，从而既保留自然梯度的几何优势，又避免显式的 Fisher 矩阵构造与求逆。
- 整体含义：为强化学习策略优化提供一种简单、通用且高效的自然策略梯度实现方式，降低其工程复杂度，提升实用性和可扩展性。

## 2. 方法论

### 核心思想
- 将 Tikhonov 正则化后的自然策略梯度重写为“带变换优势的普通策略梯度”（vanilla policy gradient with a transformed advantage）。
- 利用 **Woodbury 恒等式** 进行矩阵代数变换，将 Fisher 矩阵相关项转化为对优势函数的变换操作，从而避免直接构造和求逆 Fisher 矩阵。

### 关键技术细节
- **随机块 Kaczmarz 迭代**：在 on-policy mini-batches 上迭代计算该优势变换，逐步逼近所需的自然梯度方向。
- 该方法不需要显式构建 Fisher 矩阵，也不需要共轭梯度求解器，更不强依赖特定网络架构。
- 整个过程可直接通过标准反向传播实现，简化了实现流程。

### 算法流程（文字说明）
1. 在策略当前参数下采集 on-policy 轨迹 / mini-batch 数据。
2. 估计优势函数（如 GAE）作为基础。
3. 利用 Woodbury 公式将正则化自然梯度等价转化为优势变换的形式。
4. 使用随机块 Kaczmarz 迭代，在 mini-batch 上计算这一变换后的优势，逐步逼近正则化自然梯度方向。
5. 将变换后的优势代入普通策略梯度公式，通过反向传播更新策略参数。

## 3. 实验设计

- **基准环境**：论文摘要中提及使用了**连续控制**和**视觉控制**基准（如标准 MuJoCo 类连续任务和基于图像的视觉控制任务），具体环境名称未在摘要中列出。
- **对比方法**：与已建立的自然梯度方法（如 TRPO、PPO 及其变体、ACKTR 等常见自然梯度类方法）进行比较。
- **评估指标**：未在摘要中详细说明，通常为平均回报、样本效率、收敛稳定性等。

## 4. 资源与算力

- 论文摘要及元数据中**未明确说明**使用的 GPU 型号、数量、训练时长或总计算资源。
- 仅能推断实验涉及多任务和多算法对比，需要一定量的计算资源，但具体细节缺失。

## 5. 实验数量与充分性

- 摘要提到在连续控制和视觉控制基准上进行了大规模实证，覆盖多种任务，并有多组对比实验。
- 但**没有提供具体实验数量、消融实验或详细图表**，因此无法完全判断实验的充分性与客观性。
- 从摘要表述“matching or exceeding established natural-gradient methods”来看，实验至少验证了性能不低于现有方法，但缺乏详细统计显著性分析和超参数敏感性检验。

## 6. 主要结论与发现

- RAT 方法能够以**直接反向传播**的方式高效估计正则化自然策略梯度，无需显式构建 Fisher 矩阵或使用共轭梯度求解器。
- 方法在连续控制和视觉控制基准上**匹配或超过**已有自然梯度方法，说明其在保持性能的同时显著降低了实现复杂度和计算开销。
- 提供了**收敛性保证**，为理论可靠性提供了支撑。

## 7. 优点

- **高效性**：避免 Fisher 矩阵的显式构造与求逆，减少内存和计算开销。
- **通用性**：与网络架构无关，可应用于多种策略表示，适配简单。
- **方法简洁**：将自然梯度转化为带变换优势的普通策略梯度，直接利用反向传播，易于在现有 RL 框架中实现。
- **理论保证**：提供了收敛性分析，增强了方法的可信度。
- **实验覆盖**：同时涵盖连续控制和视觉控制，验证了方法的广泛适用性。

## 8. 不足与局限

- **信息不完整**：摘要之外未提供完整论文，无法评估实验设置细节，如任务具体名称、超参数调节、对比方法的调优是否公平。
- **计算资源未披露**：缺少算力描述，难以复现或评估实际效率。
- **理论深度有限**：只有收敛保证，缺乏关于收敛速率、样本复杂度、正则化参数选择影响等理论分析。
- **实际应用限制**：未提及在真实机器人或大规模分布式 RL 上的验证，真实世界适用性未知。
- **变换过程额外开销**：随机块 Kaczmarz 迭代本身会增加计算步数，需与直接求逆或共轭梯度对比实际时间收益。
- **偏差风险**：可能只在特定基准上表现良好，存在选择性报告的可能，需要更有代表性的 benchmark 和消融实验。

（完）
