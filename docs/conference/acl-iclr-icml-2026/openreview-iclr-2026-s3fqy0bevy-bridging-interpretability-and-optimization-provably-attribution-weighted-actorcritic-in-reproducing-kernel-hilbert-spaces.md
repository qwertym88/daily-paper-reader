---
title: "Bridging Interpretability and Optimization: Provably Attribution-Weighted Actor–Critic in Reproducing-Kernel Hilbert Spaces"
title_zh: 桥接可解释性与优化：在再生核希尔伯特空间中可证明的归因加权Actor-Critic
authors: "Na Li, Hangguan Shan, Wei Ni, Wenjie Zhang, Xinyu Li"
date: 2025-09-10
pdf: "https://openreview.net/pdf?id=s3Fqy0BeVY"
tags: ["query:rl-control"]
score: 9.0
evidence: 基于属性加权与再生核希尔伯特空间的Actor-Critic架构
tldr: Actor-Critic是强化学习的基石，但可解释性有限且忽视状态特征对奖励的差异影响。本文提出RSA2C，一种基于RKHS-SHAP的先进Actor-Critic算法，包含Actor、价值评论家和优势评论家，将Actor置于向量值RKHS中并采用Mahalanobis加权核，评论家在标量RKHS中。该方法利用状态归因引导训练，在提升策略性能的同时增强了可解释性，为可解释强化学习提供了新范式。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有可解释强化学习很少利用状态归因辅助训练，且对所有状态特征一视同仁，忽视了其对奖励的异质影响。
method: 提出RSA2C，在RKHS中实例化Actor与两类Critic，用Mahalanobis加权算子核和SHAP归因加权进行策略学习。
result: 理论上提供了双时间尺度收敛保证，并在实验中展示了归因加权带来的性能和可解释性提升。
conclusion: 融合归因加权的核化Actor-Critic能够同时改善优化效果与模型解释能力。
---

## Abstract
Actor--critic (AC) methods are a cornerstone of reinforcement learning (RL) but offer limited interpretability. Current explainable RL methods seldom use *state attributions* to assist training. Rather, they treat all state features equally, thereby neglecting the heterogeneous impacts of individual state dimensions on the reward. We propose *RKHS--SHAP-based Advanced Actor--Critic (RSA2C)*, an attribution-aware, kernelized, two–timescale AC, including Actor, Value Critic, and Advantage Critic. The Actor is instantiated in a vector-valued reproducing kernel Hilbert space (RKHS) with a Mahalanobis-weighted operator-valued kernel, while the Value Critic and Advantage Critic reside in scalar RKHSs. These RKHS-enhanced components use sparsified dictionaries: the Value Critic maintains its own dictionary, while the Actor and Advantage Critic share one. State attributions, computed from the Value Critic via RKHS--SHAP (kernel mean embedding for on-manifold expectations and conditional mean embedding for off-manifold expectations), are converted into Mahalanobis-gated weights that modulate Actor gradients and Advantage Critic targets. Theoretically, we derive a global, non-asymptotic convergence bound under *state perturbations*, showing stability through the perturbation-error term and efficiency through the convergence-error term. Empirical results on three standard continuous-control environments show that RSA2C achieves efficiency, stability, and interpretability.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- 强化学习中的 Actor-Critic（AC）方法虽然应用广泛，但存在两大不足：
  - **可解释性有限**：难以解释策略为何做出某个决策。
  - **特征处理粗糙**：现有可解释强化学习方法很少利用状态归因（state attributions）辅助训练，且通常将所有状态特征视为同等重要，忽略了不同状态维度对奖励的异质影响。
- 论文旨在解决“如何让 AC 方法在提升优化性能的同时具备可解释性”这一核心问题，提出一种将归因加权与核方法（RKHS）融合的新型 AC 算法，为可解释强化学习提供新范式。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程（文字说明）

- **核心思想**：利用 SHAP 类归因方法从价值函数中提取状态特征的重要性，并将这些归因转化为权重，用于引导 Actor 的策略梯度和 Advantage Critic 的更新目标，从而让模型在训练过程中关注对奖励影响更大的特征，同时增强可解释性。
- **框架名称**：RSA2C（RKHS–SHAP-based Advanced Actor–Critic），一种归因感知、核化、双时间尺度的 AC 框架。
- **关键组件**：
  - **Actor**：在向量值再生核希尔伯特空间（vector-valued RKHS）中实例化，使用 Mahalanobis 加权算子值核（Mahalanobis-weighted operator-valued kernel）。
  - **Value Critic**：在标量 RKHS 中实例化，维护自己的稀疏字典（sparsified dictionary）。
  - **Advantage Critic**：同样在标量 RKHS 中实例化，与 Actor 共享一个稀疏字典。
- **归因计算**：通过 RKHS–SHAP 计算状态归因：
  - 使用核均值嵌入（kernel mean embedding）计算流形上的期望（on-manifold expectations）。
  - 使用条件均值嵌入（conditional mean embedding）计算流形外的期望（off-manifold expectations）。
- **归因加权机制**：
  - 归因被转换为 Mahalanobis 门控权重（Mahalanobis-gated weights），用于调制：
    - Actor 的梯度更新。
    - Advantage Critic 的目标值。
- **理论保证**：在状态扰动（state perturbations）下推导出全局非渐近收敛界，通过扰动误差项体现稳定性，通过收敛误差项体现效率。

### 3. 实验设计：数据集 / 场景、benchmark、对比方法

- **实验场景**：三个标准连续控制环境（standard continuous-control environments），具体环境名称论文摘要未列出（如 MuJoCo 中的 HalfCheetah、Walker2d、Hopper 等常见 benchmark，但原文未明示）。
- **对比方法**：摘要未明确列出具体的基线算法，但通常此类工作会对比普通 Actor-Critic、核化 AC 方法、以及未使用归因加权的变体。
- **评价指标**：效率（efficiency）、稳定性（stability）、可解释性（interpretability）。

### 4. 资源与算力

- 论文摘要和提供的元数据中**未明确提及**使用的 GPU 型号、数量、训练时长、计算集群等算力信息。
- 无法从现有文本中总结具体资源消耗，只能指出该信息缺失。

### 5. 实验数量与充分性

- 摘要仅说明在三个标准连续控制环境上进行了实验，未给出具体实验数量、消融实验设置、重复次数、随机种子数等细节。
- 由于提供的文本是论文摘要（或简短版本），**实验充分性无法全面评估**。但论文宣称同时验证了效率、稳定性和可解释性，暗示可能包含：
  - 与基线方法的性能对比实验。
  - 归因加权有效性的消融（例如关闭归因加权）。
  - 可解释性可视化或定量评估。
- 总体来看，若仅依赖这段文本，**实验数量与公平性的信息不充分**，需查看论文全文才能判断。

### 6. 论文的主要结论与发现

- RSA2C 能够在三个标准连续控制任务上同时实现**效率、稳定性和可解释性**的提升。
- 理论上提供了双时间尺度收敛保证，说明归因加权不会破坏收敛性，反而能通过状态扰动误差项增强稳定性。
- 将状态归因引入训练过程，不仅改善策略性能，还使得模型决策依据更加透明，证明了“归因辅助训练”这一思路的有效性。

### 7. 优点

- **创新性**：首次将 SHAP 类归因与核化 Actor-Critic 深度结合，利用归因直接引导策略优化，而非仅作后验解释。
- **理论贡献**：提供了在状态扰动下的全局非渐近收敛界，为归因加权的稳定性提供了数学基础。
- **方法完备性**：Actor、Value Critic、Advantage Critic 均置于 RKHS 中，并采用稀疏字典控制计算复杂度；归因计算兼顾 on-manifold 与 off-manifold 期望，设计细致。
- **可解释性**：通过 Mahalanobis 门控权重，模型能够显式利用特征重要性，提高了透明程度。

### 8. 不足与局限

- **实验信息不足**：摘要未列出具体的环境名称、基线算法、超参数设置、消融实验细节，无法充分评估实验的广泛性和公平性。
- **算力与复现成本未披露**：未说明计算资源，可能影响复现的便利性（不过这在论文摘要中常见）。
- **应用范围有限**：只在连续控制任务上验证，未涉及离散动作空间、多智能体或真实世界任务，泛化性未知。
- **理论假设**：收敛性分析依赖“状态扰动”这一设定，实际环境中是否存在此类扰动以及扰动界的紧性需要进一步研究。
- **依赖 SHAP 计算**：RKHS–SHAP 的计算可能带来额外开销，尤其在高维状态空间中，效率优势需要更充分的实验证明。

（完）
