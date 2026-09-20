---
title: Memory-Augmented Functional Koopmanism for Interpretable Learning of Spatiotemporal Dynamics
title_zh: 记忆增强的功能性Koopman方法用于时空动力学的可解释学习
authors: "Wanfeng Lu, He Ma, Wei Lin, Qunxi Zhu"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=QzCOeNN3vJ"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 基于Koopman算子的非线性时空动力学框架
tldr: 针对高保真求解器计算昂贵、时空数据稀疏含噪且不规则导致预测困难的问题，本文提出MERLIN，一种基于Koopman的框架，将动力学提升为学习到的观测泛函近线性演化，并借助Mori-Zwanzig形式引入非马尔可夫记忆项以弥补有限维线性不变性的损失，配合离散不变函数编码器实现任意分辨率全场重构。实验表明其预测精度优于基线，为PDE时空动力学提供可解释学习途径。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 高保真求解器计算代价高，且数据稀疏、含噪、不规则，难以精确预测时空动力学。
method: 提出MERLIN框架，将动力学提升到观测泛函近线性演化，用Mori-Zwanzig形式补充记忆项并采用离散不变函数编码器。
result: 实现任意分辨率全场重构，预测精度优于基线方法。
conclusion: 为PDE时空动力学提供了可解释的Koopman学习框架。
---

## Abstract
Precise prediction of spatiotemporal dynamics over predictive horizons is constrained by the computational cost of high-fidelity solvers and the sparsity, noise, and irregularity of data. We introduce MERLIN, a Koopman-based framework that lifts dynamics to the evolution of learned *observation functionals* with near-linear progression, enabling full-field reconstruction at arbitrary resolutions. Theoretically, we develop a functional Koopman theory for PDEs and compensate for the loss of finite-dimensional linear invariance via the Mori–Zwanzig formalism, which augments the linear backbone with non-Markovian memory terms to improve predictive accuracy. Practically, MERLIN employs discretization-invariant *function encoders* that map partial, irregular observations to observables, and resolution-free *function decoders* that reconstruct states at arbitrary query points. Training under linear constraints yields an interpretable, low-dimensional model that captures principal modes, supports reduced-order modeling, and—augmented with memory correction—delivers stable long-horizon rollouts even in ultra-low-dimensional latent spaces.

---

## 论文详细总结（自动生成）

> 说明：提供的“论文 PDF 提取文本”实际为 OpenReview 的浏览器验证页面，未包含论文正文；以下总结主要依据摘要与元数据。因此，实验细节、算力、实验数量等信息无法从当前材料中完整核实。

## 1. 核心问题与整体含义
- **研究动机**：时空动力学的高精度预测通常依赖高保真求解器，但计算代价高昂；同时实际数据常存在稀疏、噪声和不规则采样问题，导致长预测时域上的精确预测困难。
- **背景**：Koopman 类方法试图将非线性动力学提升到观测函数空间，从而获得近似线性演化，兼顾可解释性与预测能力。但 PDE 等复杂时空系统中，有限维线性不变性往往难以严格保持。
- **整体含义**：论文提出 **MERLIN**，一个基于 Koopman 的框架，将动力学提升为学习到的“观测泛函”的近线性演化，并支持任意分辨率的全场重构。其目标是为 PDE 时空动力学提供可解释、低维且可长期稳定推演的学习框架。

## 2. 方法论：核心思想与关键技术
- **核心思想**：
  - 不直接在原始状态空间建模，而是学习一组观测泛函，使复杂时空动力学在提升空间中呈现近线性演化。
  - 用线性 Koopman 骨干提供可解释低维表示，再用记忆项补偿有限维线性化造成的信息损失。
- **理论构造**：
  - 为 PDE 发展 **功能性 Koopman 理论**。
  - 借助 **Mori–Zwanzig 形式** 引入 **非马尔可夫记忆项**，弥补有限维线性不变性的缺失，从而提升预测精度。
- **网络与表示设计**：
  - **离散不变函数编码器**：将部分、不规则观测映射为观测泛函/可观测量。
  - **分辨率无关函数解码器**：在任意查询点上重构状态，实现任意分辨率全场重构。
- **训练与建模特点**：
  - 在线性约束下训练，得到可解释的低维模型。
  - 模型可捕捉主要模态，支持降阶建模。
  - 加入记忆修正后，即使在超低维潜空间中也能实现稳定的长期 rollout。
- **文字化算法流程**：
  1. 输入部分、不规则、可能含噪的时空观测；
  2. 通过离散不变函数编码器映射到观测泛函空间；
  3. 在 Koopman 线性骨干上演化潜在动力学；
  4. 使用 Mori–Zwanzig 记忆项进行非马尔可夫校正；
  5. 通过分辨率无关函数解码器在任意时空查询点重构全场状态。

## 3. 实验设计
- **数据集 / 场景**：
  - 当前材料仅说明面向 **PDE 时空动力学**，数据具有稀疏、噪声、不规则等特点。
  - 未列出具体 PDE 数据集、物理系统名称或仿真场景。
- **Benchmark**：
  - 未说明使用的 benchmark 名称、评价指标或数据划分方式。
- **对比方法**：
  - 仅提到“预测精度优于基线方法”，但未列出具体基线模型、Koopman 变体或神经 PDE 方法。
- **评估目标**：
  - 声称实现任意分辨率全场重构；
  - 声称预测精度优于基线；
  - 声称在超低维潜空间中支持稳定长期推演。

## 4. 资源与算力
- 当前摘要与元数据中 **未提及** GPU 型号、数量、训练时长、参数量或计算开销。
- 因此无法总结具体算力使用情况，也无法评估训练成本和可复现性。

## 5. 实验数量与充分性
- 当前材料未给出：
  - 使用了多少个数据集或 PDE 场景；
  - 进行了多少组对比实验；
  - 是否有消融实验、鲁棒性实验、噪声实验、稀疏采样实验；
  - 是否报告统计显著性、误差棒或多随机种子结果。
- 因此无法判断实验是否充分、客观、公平。
- 仅能确认作者声称预测精度优于基线；但基线选择、调参公平性、数据划分一致性等均需全文验证。

## 6. 主要结论与发现
- 提出 **MERLIN**：一种记忆增强的功能性 Koopman 框架，用于可解释学习 PDE 时空动力学。
- 功能性 Koopman 理论可将 PDE 动力学提升到观测泛函的近线性演化。
- Mori–Zwanzig 记忆项能够补偿有限维线性不变性损失，提高预测精度。
- 离散不变编码器与分辨率无关解码器支持从部分、不规则观测中进行任意分辨率全场重构。
- 线性约束训练产生可解释低维模型，可捕捉主要模态并支持降阶建模。
- 加入记忆修正后，即使潜空间维度极低，也能保持稳定的长期 rollout。
- 总体结论：为 PDE 时空动力学提供了一条可解释的 Koopman 学习途径。

## 7. 优点
- **理论结合实践**：将功能性 Koopman 理论与 Mori–Zwanzig 形式结合，兼顾线性可解释性与非马尔可夫修正。
- **处理不规则观测**：离散不变函数编码器适合部分、不规则甚至含噪数据。
- **任意分辨率重构**：分辨率无关解码器使模型可在任意查询点输出状态，适合连续时空场。
- **可解释低维表示**：线性约束训练有助于捕捉主模态，支持降阶建模。
- **长期稳定性**：记忆项增强后，在超低维潜空间中仍声称可稳定长时推演。
- **应用潜力**：面向高保真求解器昂贵、数据稀疏含噪的 PDE 预测场景，具有实际价值。

## 8. 不足与局限
- **全文不可得**：当前仅能依据摘要与元数据，无法验证公式、算法细节和理论证明。
- **实验信息缺失**：未说明数据集、benchmark、基线方法、评价指标、消融实验和统计检验。
- **算力未报告**：缺少 GPU 型号、数量、训练时长等，影响复现性和成本评估。
- **公平性无法判断**：基线是否公平调参、是否使用相同数据划分和评价协议均不明确。
- **泛化范围有限**：方法针对 PDE 时空动力学，是否适用于更广泛动力系统、混沌系统、多尺度系统或真实实验数据尚不清楚。
- **潜在复杂性**：引入记忆项可能增加训练与推断复杂度，且理论假设、超参数敏感性和数值稳定性未在摘要中说明。
- **偏差风险**：摘要通常选择性报告有利结果；元数据来源标注为 ICLR-2026-Rejected-Public，需结合全文与评审意见进一步判断。
- **应用限制**：在极端稀疏、高噪声、强外推或边界条件复杂场景下，编码器与解码器的泛化能力仍需验证。

（完）
