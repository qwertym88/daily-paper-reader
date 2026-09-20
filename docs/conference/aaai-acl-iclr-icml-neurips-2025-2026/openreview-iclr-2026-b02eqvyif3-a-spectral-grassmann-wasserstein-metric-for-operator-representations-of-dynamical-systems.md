---
title: A Spectral-Grassmann Wasserstein metric for operator representations of dynamical systems
title_zh: 面向动态系统算子表示的谱-Grassmann Wasserstein度量
authors: "Thibaut Germain, Rémi Flamary, Vladimir R Kostic, Karim Lounici"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=B02EqvyiF3"
tags: ["query:koopman-rl"]
score: 6.0
evidence: Koopman与转移算子表示的动态系统间度量
tldr: 从轨迹数据估计的动态系统几何比较是机器学习的重要难题，Koopman与转移算子通过谱分解提供非线性动态的线性表示。本文将每个系统表示为联合算子特征值与谱投影上的分布，利用最优输运定义系统间度量。该度量对采样频率不变、计算高效并具有限样本收敛保证，还可计算Fréchet均值，为动态系统表示的比较与插值提供了原则性工具。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 从轨迹数据估计的动态系统几何比较困难，Koopman算子表示缺乏合适的系统间度量。
method: 将系统表示为算子特征值与谱投影分布，用最优输运定义不变于采样频率的度量。
result: 该度量计算高效、具有限样本收敛保证并支持Fréchet均值插值。
conclusion: 为动态系统算子表示的比较与插值提供了原则性工具。
---

## Abstract
The geometry of dynamical systems estimated from trajectory data is a major challenge for machine learning applications. Koopman and transfer operators provide a linear representation of nonlinear dynamics through their spectral decomposition, offering a natural framework for comparison. We propose a novel approach that represents each system as a distribution over its joint operator eigenvalues and spectral projectors and defines a metric between systems leveraging optimal transport. The proposed metric is invariant to the sampling frequency of trajectories. It is also computationally efficient, supported by finite-sample convergence guarantees, and enables the computation of Fréchet means, providing interpolation between dynamical systems. Experiments on simulated and real-world datasets show that our approach consistently outperforms standard operator-based distances in machine learning applications, including dimensionality reduction and classification, and provides meaningful interpolation between dynamical systems.

---

## 论文详细总结（自动生成）

# 论文总结：面向动态系统算子表示的谱-Grassmann Wasserstein 度量

> 说明：提供的 PDF 提取文本实际为 OpenReview 的浏览器验证页，未包含论文正文。以下总结主要依据给定元数据、摘要与 TLDR 信息；涉及具体实验设置、算力、消融数量等细节时，若材料未说明，将明确标注为“未提供/无法确认”。

## 1. 核心问题与整体含义

- **研究动机**：从轨迹数据估计得到的动态系统，其几何比较是机器学习中的关键难题。Koopman 算子与转移算子能够通过谱分解，为非线性动态提供线性表示，因此成为比较动态系统的自然框架。
- **核心问题**：现有 Koopman/转移算子表示缺乏合适的“系统间度量”，难以直接比较、聚类、降维或插值不同动态系统。
- **整体含义**：论文提出一种新的系统间度量，将动态系统视为其算子谱信息的分布，并利用最优输运定义距离，为动态系统表示的比较与插值提供原则性工具。
- **元数据背景**：论文标注为 ICLR-2026-Accepted，OpenReview score 6.0，标签与 Koopman、强化学习等方向相关。

## 2. 方法论

- **核心思想**：
  - 对每个动态系统，从轨迹数据估计 Koopman 或转移算子。
  - 对算子进行谱分解，提取联合的“特征值 + 谱投影”信息。
  - 将每个系统表示为其算子特征值与谱投影上的一个分布。
  - 使用最优输运（Wasserstein 距离）定义两个系统分布之间的距离。
- **关键技术细节**：
  - **谱分解**：利用算子的特征值与对应谱投影描述动态模态。
  - **Grassmann 几何**：谱投影对应特征子空间，子空间之间的比较可借助 Grassmann 流形上的距离。
  - **联合分布表示**：每个谱分量可视为“特征值—谱投影”联合对象上的点，系统整体成为这些点的分布。
  - **最优输运度量**：系统间距离由两个分布之间的最小传输成本给出，成本同时考虑特征值差异与谱投影子空间差异。
- **理论性质**：
  - 对轨迹采样频率具有不变性。
  - 计算高效。
  - 具有有限样本收敛保证。
  - 支持计算 Fréchet 均值，从而可在动态系统之间进行插值。
- **算法流程（文字说明）**：
  1. 从轨迹数据估计动态系统的算子。
  2. 对算子做谱分解，得到特征值和谱投影。
  3. 构造每个系统的联合谱分布。
  4. 定义点间代价，融合特征值距离与 Grassmann 子空间距离。
  5. 求解最优输运问题，得到系统间度量。
  6. 可选地计算 Fréchet 均值，实现系统插值。

## 3. 实验设计

- **数据集/场景**：
  - 摘要提到使用“模拟数据集”和“真实世界数据集”。
  - 具体数据集名称、规模、来源未在提供材料中说明。
- **任务/应用**：
  -  dimensionality reduction（降维）。
  -  classification（分类）。
  - 动态系统之间的插值。
- **Benchmark 与对比方法**：
  - 对比对象为“标准 operator-based distances”，即基于算子的常规距离。
  - 具体基线名称、实现细节、参数设置未提供。
- **评价目标**：
  - 在降维与分类任务中是否优于标准算子距离。
  - 插值结果是否具有实际意义。

## 4. 资源与算力

- 提供的材料中**未说明**使用的 GPU 型号、数量、训练时长、计算集群或任何算力资源。
- 因此无法评估该工作的计算开销、可复现成本或资源规模。

## 5. 实验数量与充分性

- 从摘要可推断至少包含：
  - 模拟数据实验。
  - 真实世界数据实验。
  - 降维、分类、插值等不同任务。
- 但具体实验组数、数据集数量、消融实验数量、统计检验、超参数搜索等均未提供。
- 作者声称该方法“consistently outperforms”标准算子距离，但仅凭摘要无法判断：
  - 基线是否公平调参。
  - 是否进行了充分消融。
  - 是否报告方差、置信区间或显著性。
  - 真实数据集是否具有代表性。
- 结论：实验覆盖面从摘要看较广，但材料不足以独立评估其充分性、客观性与公平性。

## 6. 主要结论与发现

- 提出了一种基于谱信息与最优输运的动态系统间度量。
- 该度量对轨迹采样频率不变，计算高效，并具有有限样本收敛保证。
- 支持 Fréchet 均值，可实现动态系统之间的插值。
- 在模拟与真实数据上的降维、分类任务中，持续优于标准算子距离。
- 在动态系统插值方面能够给出有意义的结果。

## 7. 优点

- **理论性质明确**：采样频率不变性、有限样本收敛保证、计算高效。
- **表示方式有原则**：将 Koopman/转移算子的谱分解与最优输运结合，兼顾特征值与谱投影子空间。
- **支持插值**：通过 Fréchet 均值实现动态系统之间的插值，扩展了系统比较的用途。
- **应用导向**：直接面向降维、分类和插值等机器学习任务，具有实用潜力。
- **框架通用**：适用于 Koopman 算子与转移算子等谱表示框架。

## 8. 不足与局限

- **材料限制**：提供的 PDF 提取文本为验证页，缺少正文，无法核实公式、理论证明和实验细节。
- **实验细节缺失**：未提供具体数据集、基线方法、评价指标、超参数和统计显著性。
- **算力未说明**：无法评估计算资源需求与可复现成本。
- **鲁棒性未知**：对噪声、部分观测、有限轨迹、谱估计误差的敏感性未在材料中说明。
- **计算复杂度风险**：最优输运与谱投影子空间比较可能随模态数量或谱维度增加而变贵，尽管摘要声称计算高效。
- **应用限制**：方法依赖算子谱分解质量；若 Koopman/转移算子估计不稳定，度量与插值效果可能受限。
- **公平性无法验证**：摘要声称优于标准算子距离，但缺少完整实验协议，难以独立判断公平性。

（完）
