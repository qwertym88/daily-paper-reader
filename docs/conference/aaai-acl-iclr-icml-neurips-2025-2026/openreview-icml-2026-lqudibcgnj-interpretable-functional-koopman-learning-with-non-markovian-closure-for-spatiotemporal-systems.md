---
title: Interpretable Functional Koopman Learning with Non-Markovian Closure for Spatiotemporal Systems
title_zh: 面向时空系统的可解释泛函Koopman学习与非马尔可夫闭合
authors: "Wanfeng Lu, He Ma, Wei Lin, Qunxi Zhu"
date: 2026-04-30
pdf: "https://openreview.net/pdf/74ab18c7322e515f3c7951a9cebc2190126bb0a8.pdf"
tags: ["query:koopman-rl"]
score: 9.0
evidence: 面向非线性时空动力学的泛函Koopman理论
tldr: 高保真求解器计算代价高、数据稀疏含噪且不规则，严重限制时空动力学长程预测。本文提出MERLIN，用学习到的观测泛函将动力学提升到近线性演化空间，并借助Mori-Zwanzig形式化引入非马尔可夫记忆项弥补有限维线性不变性的损失。方法结合离散不变函数编码器，实现任意分辨率下的全场重构。实验表明其在稀疏噪声数据上预测更准，为PDE类非线性系统提供了可解释的Koopman建模新范式。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 高保真求解器代价高、数据稀疏含噪，限制了时空非线性动力学的长程精确预测。
method: 提出MERLIN，将动力学提升到学习到的观测泛函上做近线性演化，并用Mori-Zwanzig形式化加入非马尔可夫记忆项。
result: 在稀疏噪声数据上实现任意分辨率的全场重构，提升了预测精度。
conclusion: 为PDE类非线性系统提供了可解释的Koopman建模框架。
---

## Abstract
Precise prediction of spatiotemporal dynamics over predictive horizons is constrained by the computational cost of high-fidelity solvers and the sparsity, noise, and irregularity of data. We introduce MERLIN, a Koopman-based framework that lifts dynamics to the evolution of learned *observation functionals* with near-linear progression, enabling full-field reconstruction at arbitrary resolutions. Theoretically, we develop a functional Koopman theory for PDEs and compensate for the loss of finite-dimensional linear invariance via the Mori–Zwanzig formalism, which augments the linear backbone with non-Markovian memory terms to improve predictive accuracy. Practically, MERLIN employs discretization-invariant *function encoders* that map partial, irregular observations to observables, and resolution-free *function decoders* that reconstruct states at arbitrary query points. Training under linear constraints yields an interpretable, low-dimensional model
that captures principal modes and supports reduced-order modeling, while memory
correction further enables stable long-horizon rollouts even in ultra-low-dimensional
latent spaces. Our code is available at: https://github.com/RobinLufdu/MERLIN.

---

## 论文详细总结（自动生成）

> 说明：提供的“论文 PDF 提取文本”实际为 OpenReview 浏览器验证页面，未包含论文正文。以下总结主要依据论文摘要与给定元数据整理；凡正文未提供的信息，均标注为“未说明/无法确认”，避免臆测。

# 论文总结：面向时空系统的可解释泛函 Koopman 学习与非马尔可夫闭合

## 1. 核心问题与整体含义
- **研究动机**：高保真数值求解器计算代价高；实际观测数据往往稀疏、含噪且不规则，严重限制非线性时空动力学在长预测时域上的精确预测。
- **核心问题**：如何在数据受限条件下，对 PDE 类时空系统进行高保真、可解释、可长程 rollout 的建模与预测。
- **整体含义**：论文提出 MERLIN，将 Koopman 理论从有限维状态/观测提升到“学习到的观测泛函”层面，并引入 Mori–Zwanzig 非马尔可夫记忆项，试图为非线性 PDE 系统提供一种兼具可解释性与预测能力的降阶建模新范式。

## 2. 方法论
- **核心思想**：
  - 不直接在原始状态空间中建模，而是学习一组**观测泛函**，将时空动力学提升到一个近似线性演化的空间中。
  - 由于有限维线性不变性在 PDE 中通常会丢失，进一步用 **Mori–Zwanzig 形式化**加入非马尔可夫记忆项，形成“线性主干 + 记忆校正”的闭合模型。
- **关键技术细节**：
  - **泛函 Koopman 理论**：面向 PDE 建立泛函 Koopman 框架，使动力学在学习到的观测泛函上近似线性推进。
  - **非马尔可夫闭合**：用记忆项补偿有限维线性近似造成的信息损失，提升预测精度与长时稳定性。
  - **离散化不变函数编码器**：将部分、不规则观测映射为可学习的观测量，降低对规则网格与完整数据的依赖。
  - **无分辨率函数解码器**：支持在任意查询点重构全场状态，实现任意分辨率下的全场重建。
  - **线性约束训练**：在训练中施加线性约束，得到低维、可解释的模型，能够捕捉主模态并支持降阶建模。
  - **长程 rollout 稳定性**：记忆校正使模型即使在超低维潜在空间中也能进行稳定长时滚动预测。
- **算法流程（文字概括）**：
  1. 从稀疏、噪声、不规则观测中学习观测泛函/函数编码器；
  2. 将动力学提升到近线性 Koopman 演化空间；
  3. 在低维潜空间中训练满足线性约束的可解释表示；
  4. 用 Mori–Zwanzig 记忆项修正非马尔可夫效应；
  5. 通过无分辨率函数解码器在任意查询点重构全场；
  6. 利用记忆校正进行稳定长时预测与降阶建模。

## 3. 实验设计
- **数据集/场景**：摘要仅说明面向时空动力学与 PDE 类非线性系统，并在“稀疏、噪声、不规则数据”上验证；未列出具体数据集、方程名称或应用场景。
- **Benchmark**：未说明具体 benchmark。
- **对比方法**：未说明对比了哪些基线模型或 Koopman 方法。
- **评价目标**：摘要提到预测更准、任意分辨率全场重构、超低维潜空间下稳定长时 rollout，以及支持降阶建模。
- **代码**：论文提供代码链接：`https://github.com/RobinLufdu/MERLIN`。

## 4. 资源与算力
- 提供的摘要与元数据中**未说明** GPU 型号、数量、训练时长、参数量或计算开销。
- 因此无法判断该方法的训练成本、可复现算力需求，以及是否适合大规模 PDE 场景。

## 5. 实验数量与充分性
- 从摘要可见，实验至少涉及以下维度：稀疏噪声数据预测、任意分辨率重构、长时 rollout、超低维潜空间稳定性、降阶建模。
- 但**具体实验组数、数据集数量、消融实验、基线对比和统计显著性均未提供**，无法评估实验充分性。
- 元数据中 `score: 9.0`、`source: ICML-2026-Accepted` 可作为接收/评审信号，但不能替代正文中的实验细节与公平性验证。
- 因此，基于当前材料无法客观判断实验是否覆盖全面、对比是否公平、结论是否稳健。

## 6. 主要结论与发现
- 提出 MERLIN：一种基于 Koopman 的时空动力学学习框架。
- 通过学习观测泛函，将 PDE 动力学提升到近线性演化空间，实现任意分辨率全场重构。
- 建立面向 PDE 的泛函 Koopman 理论，并用 Mori–Zwanzig 非马尔可夫记忆项补偿有限维线性不变性的损失。
- 在稀疏、噪声数据上取得更准预测，并支持稳定长时 rollout。
- 训练得到的低维模型具有可解释性，能捕捉主模态并支持降阶建模。
- 为 PDE 类非线性系统提供了一种可解释的 Koopman 建模框架。

## 7. 优点
- **理论结合有新意**：将泛函 Koopman 理论与 Mori–Zwanzig 非马尔可夫闭合结合，兼顾线性主干与记忆修正。
- **数据适应性强**：函数编码器面向部分、不规则观测，函数解码器支持任意查询点重构，适合稀疏/不规则数据场景。
- **可解释与降阶建模**：线性约束训练带来低维、可解释表示，利于主模态分析与 reduced-order modeling。
- **长时稳定性**：记忆项有望改善长程 rollout，在超低维潜空间中仍保持稳定。
- **代码开源**：提供 GitHub 链接，有利于复现与后续研究。

## 8. 不足与局限
- **正文缺失导致信息不足**：当前无法核实具体公式、算法细节、实验设置与理论证明。
- **实验覆盖未知**：未列出数据集、benchmark、基线方法和消融实验，无法判断泛化性与公平性。
- **算力与效率未说明**：未报告训练资源、推理成本和复杂度，难以评估实际可扩展性。
- **潜在额外复杂度**：Mori–Zwanzig 记忆项可能引入历史依赖、额外超参数和计算开销。
- **应用限制未知**：对高维、强噪声、复杂边界条件、非周期/非平稳 PDE 的表现尚未从现有材料中确认。
- **偏差风险**：元数据评分与接收信息不能替代对正文实验的独立审查；若缺少多场景对比，结论可能存在选择性展示风险。

（完）
