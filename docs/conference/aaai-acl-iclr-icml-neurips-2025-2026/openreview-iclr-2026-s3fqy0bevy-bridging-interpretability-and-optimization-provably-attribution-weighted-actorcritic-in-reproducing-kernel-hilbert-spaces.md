---
title: "Bridging Interpretability and Optimization: Provably Attribution-Weighted Actor–Critic in Reproducing-Kernel Hilbert Spaces"
title_zh: 连接可解释性与优化：再生核希尔伯特空间中的可证明归因加权演员-评论家
authors: "Na Li, Hangguan Shan, Wei Ni, Wenjie Zhang, Xinyu Li"
date: 2025-09-10
pdf: "https://openreview.net/pdf?id=s3Fqy0BeVY"
tags: ["query:rl-control"]
score: 6.0
evidence: 基于RKHS的属性加权演员-评论家算法
tldr: 演员-评论家方法虽为强化学习基石，却缺乏可解释性，现有可解释RL很少利用状态归因辅助训练，且平等对待所有状态维度。本文提出RSA2C，一种归因感知、核化的双时间尺度演员-评论家结构，演员位于带Mahalanobis加权算子值核的向量值RKHS，价值评论家与优势评论家位于标量RKHS。方法利用SHAP式归因对状态特征加权，兼顾优化与可解释性。理论分析给出可证明保证，为RL策略优化提供了新的架构设计思路。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 演员-评论家RL缺乏可解释性，且忽视不同状态维度对奖励的异质影响。
method: 提出RSA2C，将演员与评论家置于RKHS，用SHAP式状态归因加权并采用双时间尺度训练。
result: 在可解释性与优化上均获可证明保证，改善信用分配。
conclusion: 为归因感知的强化学习架构提供了理论与方法参考。
---

## Abstract
Actor--critic (AC) methods are a cornerstone of reinforcement learning (RL) but offer limited interpretability. Current explainable RL methods seldom use *state attributions* to assist training. Rather, they treat all state features equally, thereby neglecting the heterogeneous impacts of individual state dimensions on the reward. We propose *RKHS--SHAP-based Advanced Actor--Critic (RSA2C)*, an attribution-aware, kernelized, two–timescale AC, including Actor, Value Critic, and Advantage Critic. The Actor is instantiated in a vector-valued reproducing kernel Hilbert space (RKHS) with a Mahalanobis-weighted operator-valued kernel, while the Value Critic and Advantage Critic reside in scalar RKHSs. These RKHS-enhanced components use sparsified dictionaries: the Value Critic maintains its own dictionary, while the Actor and Advantage Critic share one. State attributions, computed from the Value Critic via RKHS--SHAP (kernel mean embedding for on-manifold expectations and conditional mean embedding for off-manifold expectations), are converted into Mahalanobis-gated weights that modulate Actor gradients and Advantage Critic targets. Theoretically, we derive a global, non-asymptotic convergence bound under *state perturbations*, showing stability through the perturbation-error term and efficiency through the convergence-error term. Empirical results on three standard continuous-control environments show that RSA2C achieves efficiency, stability, and interpretability.

---

## 论文详细总结（自动生成）

# 论文总结：连接可解释性与优化：再生核希尔伯特空间中的可证明归因加权演员–评论家

> 说明：提供的“论文 PDF 提取文本”实际为 OpenReview 人机验证页面，未包含论文正文。以下总结严格依据标题、摘要与 Markdown 元数据；凡正文未提供的信息，均标注为“未说明/无法确认”。

## 1. 核心问题与整体含义
- **研究动机**：演员–评论家（Actor–Critic, AC）是强化学习（RL）的基石方法，但可解释性有限。
- **现有问题**：当前可解释 RL 方法很少利用“状态归因”来辅助训练；它们通常平等对待所有状态特征，忽略不同状态维度对奖励的异质影响。
- **整体含义**：论文试图把可解释性与优化更紧密地连接起来，提出一种归因感知、核化、双时间尺度的 AC 架构，使状态归因既用于解释，也用于调制策略与优势学习，并给出可证明的理论保证。

## 2. 方法论
- **核心思想**：提出 **RSA2C**（RKHS–SHAP-based Advanced Actor–Critic），即基于 RKHS–SHAP 的先进演员–评论家。
- **组件结构**：包含 Actor、Value Critic、Advantage Critic 三个部分。
- **函数空间设计**：
  - Actor 位于**向量值 RKHS**，使用 **Mahalanobis 加权算子值核**。
  - Value Critic 与 Advantage Critic 位于**标量 RKHS**。
- **稀疏字典机制**：
  - Value Critic 维护自己的稀疏字典。
  - Actor 与 Advantage Critic 共享一个稀疏字典。
- **状态归因计算**：
  - 从 Value Critic 通过 **RKHS–SHAP** 计算状态归因。
  - 其中 on-manifold 期望使用 **kernel mean embedding**，off-manifold 期望使用 **conditional mean embedding**。
- **归因加权机制**：
  - 状态归因被转换为 **Mahalanobis-gated weights**。
  - 这些权重用于调制 Actor 的梯度以及 Advantage Critic 的目标。
- **训练框架**：采用**双时间尺度**的 Actor–Critic 更新结构。
- **理论分析**：在**状态扰动**下推导了全局、非渐近收敛界；稳定性由扰动误差项体现，效率由收敛误差项体现。

## 3. 实验设计
- **场景**：摘要称在**三个标准连续控制环境**上评估。
- **数据集/环境名称**：未在提供的摘要与元数据中列出，无法确认具体是哪些环境。
- **Benchmark**：未说明。
- **对比方法**：未说明具体对比了哪些基线或已有可解释 RL/AC 方法。
- **评估维度**：摘要概括为效率、稳定性和可解释性；但未给出具体指标、实验协议或可解释性评估方式。

## 4. 资源与算力
- 提供的材料中**未提及** GPU 型号、数量、训练时长、CPU/内存、实验平台等算力信息。
- 因此无法总结资源消耗，也无法判断其计算成本与可复现性。

## 5. 实验数量与充分性
- 根据摘要，至少有**三个连续控制环境**上的实验。
- 是否包含消融实验、超参数敏感性分析、统计显著性检验、不同归因方法对比等，**未说明**。
- 由于缺少具体环境、基线、指标和训练细节，**无法客观判断实验是否充分、公平、可复现**。
- 元数据标注来源为“ICLR-2026-Rejected-Public”，评分 6.0，提示该稿曾被拒稿；但这不能替代对正文实验质量的核验。

## 6. 主要结论与发现
- RSA2C 在效率、稳定性和可解释性方面取得效果。
- 理论上给出了状态扰动下的全局非渐近收敛保证，并区分了稳定性与效率对应的误差项。
- 方法通过状态归因加权改善了信用分配，为归因感知的强化学习架构提供了理论与方法参考。
- 整体上，论文主张可解释性信号可以嵌入 AC 优化过程，而不仅作为事后解释工具。

## 7. 优点
- **方法创新性强**：将 RKHS、SHAP 式归因、Mahalanobis 加权、双时间尺度 AC 结合。
- **兼顾解释与优化**：状态归因不仅用于解释，还直接调制 Actor 梯度和 Advantage Critic 目标。
- **理论贡献**：提供非渐近收敛界，并尝试将稳定性与效率分别对应到扰动误差项和收敛误差项。
- **架构设计细致**：Actor 使用向量值 RKHS，评论家使用标量 RKHS，并通过稀疏字典控制核方法复杂度。
- **关注状态维度异质性**：不再平等对待所有状态特征，而是利用归因反映不同维度对奖励的不同影响。

## 8. 不足与局限
- **文本不完整**：提供的 PDF 提取内容仅为 CAPTCHA 页面，无法核验正文、公式、实验细节与理论证明。
- **实验覆盖有限**：仅摘要提到三个连续控制环境，未说明是否覆盖离散控制、真实任务或高维任务。
- **对比与消融不足**：未说明基线方法、消融实验和可解释性定量评估，难以判断优势来源。
- **算力与复现信息缺失**：未报告 GPU、训练时长、超参数、代码等关键复现信息。
- **计算复杂度风险**：RKHS、SHAP、核均值嵌入、条件均值嵌入和稀疏字典可能带来较高计算与调参成本。
- **理论假设限制**：状态扰动下的收敛界依赖具体假设，实际适用性需正文验证。
- **可解释性评估主观性**：若仅依赖归因可视化，可能缺乏统一、客观的评估标准。
- **发表状态信号**：元数据显示该稿为 ICLR 2026 被拒公开稿，提示可能存在审稿人认为的实验或理论不足。

（完）
