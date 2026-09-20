---
title: "KIND: Blending Stationary and Transient Koopman Dynamics with Learned Uncertainty"
title_zh: KIND：融合稳态与瞬态Koopman动力学并学习不确定性
authors: "Andrei Maalberg, Pablo Echevarria, Dr. Axel Neumann, Jens Knobloch"
date: 2025-09-16
pdf: "https://openreview.net/pdf?id=O4itsgc4fS"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 融合稳态与瞬态动力学的Koopman算子预测
tldr: 经典系统辨识依赖固定模型，而现代神经预测牺牲结构换灵活，二者难以兼顾。本文提出KIND，将时间序列分解为稳态（模型驱动）与瞬态（注意力驱动）两部分，分别在提升嵌入上用Koopman算子建模，再通过类卡尔曼的不确定性加权机制融合。方法还能学习估计自身预测置信度，从而识别不可靠预测。实验表明该混合架构在保持结构先验的同时提升了预测质量，为不确定性感知的Koopman预测提供了新思路。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 经典系统辨识过于固定，而神经预测牺牲结构，二者难以兼顾可预测性与灵活性。
method: 提出KIND，将序列分解为稳态与瞬态分量，分别用Koopman算子建模并以类卡尔曼机制融合。
result: 生成带不确定性感知的预测，并能识别不可靠输出。
conclusion: 为结构化且具置信度的Koopman预测提供了混合架构。
---

## Abstract
We introduce KIND, a hybrid forecasting architecture that produces uncertainty-aware predictions by blending stationary and transient dynamics through Koopman operators. Classical system identification relies on fixed models of predictable behavior, while modern neural forecasting often sacrifices structure for flexibility. KIND operates at their intersection: it decomposes time series into components governed by stationary (model-driven) and transient (attention-driven) dynamics. These components are modeled independently via Koopman operators acting on lifted embeddings and fused through a Kalman-inspired, uncertainty-weighted blending mechanism. Crucially, KIND learns to estimate its own predictive confidence, enabling it to identify unfamiliar dynamics, adapt its forecasts, and express when its outputs can be trusted. A physics-informed pretraining strategy further strengthens its stationary pathway, encouraging robust separation of dynamic modes. Across both real-world and benchmark datasets - including superconducting radio frequency cavity measurements and electricity load forecasting - KIND demonstrates competitive accuracy, interpretable uncertainty, and resilience to distributional shifts, outperforming classical methods like Online DMD and competing neural models such as Koopa.

---

## 论文详细总结（自动生成）

> 说明：提供的 PDF 提取文本实际为 OpenReview 的浏览器验证/CAPTCHA 页面，未包含论文正文。因此以下总结主要依据论文元数据、摘要与 TLDR 信息；凡正文未提供的内容，均标注为“未说明”或“无法确认”。

## 1. 核心问题与整体含义

- **研究动机**：经典系统辨识依赖固定模型，对可预测行为建模较好，但灵活性不足；现代神经预测方法灵活，却往往牺牲结构先验。二者难以同时兼顾可预测性、结构性与适应性。
- **整体含义**：论文提出 KIND，试图位于经典系统辨识与神经预测的交集，将时间序列分解为稳态与瞬态动态，并用 Koopman 算子建模，从而在保持结构先验的同时提升预测质量。
- **关键目标**：不仅输出预测，还要学习估计自身预测置信度，识别不熟悉动态、适应预测，并表达输出何时可信。

## 2. 方法论

- **核心思想**：KIND 是一种混合预测架构，将时间序列分解为两类分量：
  - **稳态分量**：模型驱动，强调可预测、结构化动态；
  - **瞬态分量**：注意力驱动，强调灵活、突发或非稳态变化。
- **关键技术细节**：
  - 对稳态与瞬态分量分别构建提升嵌入；
  - 在提升嵌入上使用 Koopman 算子独立建模；
  - 通过类卡尔曼、不确定性加权的融合机制合并两部分预测；
  - 学习估计自身预测置信度，用于识别不可靠输出；
  - 使用物理信息预训练策略增强稳态通路，促进动态模式的稳健分离。
- **算法流程文字说明**：
  1. 输入时间序列；
  2. 分解为稳态与瞬态分量；
  3. 分别构造提升嵌入；
  4. 分别用 Koopman 算子推进动力学；
  5. 基于不确定性进行类卡尔曼加权融合；
  6. 输出预测结果及其置信度/不确定性；
  7. 通过物理信息预训练强化稳态分支。
- 摘要未给出具体公式、损失函数、网络结构或超参数。

## 3. 实验设计

- **数据集/场景**：摘要提到在真实世界与基准数据集上评估，包括：
  - 超导射频腔测量；
  - 电力负荷预测。
- **Benchmark**：摘要称使用 “benchmark datasets”，但未具体列出基准名称、划分方式或评价指标。
- **对比方法**：
  - 经典方法：Online DMD；
  - 神经模型：Koopa；
  - 摘要还泛称优于竞争神经模型，但未列出完整基线集合。

## 4. 资源与算力

- 提供的材料中**未说明** GPU 型号、数量、训练时长、参数量或计算预算。
- 因此无法总结算力资源，也无法判断训练成本与可复现性。

## 5. 实验数量与充分性

- 从摘要可确认至少覆盖两类应用/数据场景：超导射频腔测量与电力负荷预测。
- 明确对比方法至少包括 Online DMD 与 Koopa。
- 但未提供：
  - 具体实验组数；
  - 消融实验；
  - 多随机种子与统计显著性；
  - 不确定性校准评估；
  - 分布偏移实验细节；
  - 完整基线与指标。
- 因此，基于现有材料**无法判断实验是否充分、客观、公平**；需要正文与附录验证。

## 6. 主要结论与发现

- KIND 在真实世界和基准数据集上表现出竞争性精度。
- 它能够提供可解释的不确定性，并对分布偏移具有一定韧性。
- 相比 Online DMD 和 Koopa，KIND 表现更优。
- 模型可学习预测置信度，从而识别不可靠预测。
- 该工作为结构化且具备置信度的 Koopman 预测提供了混合架构思路。

## 7. 优点

- **结构先验与灵活性结合**：稳态模型驱动分支保留结构，瞬态注意力分支提供灵活性。
- **不确定性感知融合**：类卡尔曼加权融合使不同动态分支按置信度贡献预测。
- **自估计置信度**：能识别不熟悉动态并表达输出可信度，有利于安全关键应用。
- **物理信息预训练**：增强稳态通路，有助于动态模式分离。
- **跨领域潜力**：在超导射频腔与电力负荷等不同场景中验证。
- **分布偏移韧性**：摘要强调对分布变化具有鲁棒性。

## 8. 不足与局限

- **材料限制**：当前提取文本为验证页面，无法核验方法公式、实验细节与结论强度。
- **实验细节不足**：数据集、划分、指标、统计检验、消融、算力均未说明。
- **基线覆盖有限**：摘要仅明确对比 Online DMD 与 Koopa，缺少更多强基线。
- **方法假设较强**：依赖稳态/瞬态分解、Koopman 提升嵌入、注意力瞬态建模与物理预训练，可能对复杂非平稳系统敏感。
- **不确定性校准未知**：学习到的置信度是否校准、是否在部署中可靠，未在现有材料中说明。
- **应用限制**：目前展示场景集中在特定真实数据与基准，泛化到其他领域仍需验证。

（完）
