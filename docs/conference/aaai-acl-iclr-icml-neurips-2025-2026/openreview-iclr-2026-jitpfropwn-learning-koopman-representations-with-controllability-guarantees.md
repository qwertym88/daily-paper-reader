---
title: Learning Koopman Representations with Controllability Guarantees
title_zh: 学习具有可控性保证的Koopman表示
authors: "Keyan Miao, Han Wang, Xuda Ding, Konstantinos Gatsis, Andreas Krause, Antonis Papachristodoulou"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=jITPFROpWN"
tags: ["query:koopman-rl"]
score: 9.0
evidence: 学习带可控性保证的Koopman表示用于控制
tldr: 针对从有限数据学习精确非线性动力学模型并保证其适用于控制的难题，本文提出在Koopman表示学习中强制标称系统的可控性这一先验性质。可控性保证存在能将模型从任意初态驱动到任意目标态的控制策略，同时捕捉系统结构特征以提升数据效率，并支持模型预测控制等下游方法。结果表明该约束改善了建模与控制性能，为面向控制的Koopman表示学习提供新思路。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 如何从有限数据学习精确且适合控制的非线性动力学模型是核心难题。
method: 在学习Koopman表示时强制标称系统的可控性先验，捕捉结构特征并支持MPC等控制设计。
result: 提升数据效率并保证存在驱动系统到目标态的控制策略。
conclusion: 为面向控制的Koopman表示学习提供了可控性保证的新范式。
---

## Abstract
Learning nonlinear dynamical models from data is central to control. Two fundamental challenges exist: (1) how to learn accurate models from limited data, and (2) how to ensure the learned models are suitable for control design of the nominal system. We address both by enforcing a critical \emph{a priori} property of the nominal system during learning: \emph{controllability}. Controllability guarantees the existence of control policies that can drive the learned model from any initial state to any desired state. From a modeling perspective, it captures key structural features of the nominal system, thereby improving data efficiency. For downstream control, it enables the use of modern techniques such as model predictive control (MPC). Our approach is based on controllability-preserving Koopman representation learning. Rather than learning dynamics directly in the nominal state space, we learn in a latent space where the system admits a linear representation. We prove that controllability of the learned latent model implies controllability in the nominal state space. To enforce this property, we introduce a novel canonical parameterization of the latent dynamics matrices. We further incorporate Gramian-based regularization to shape the degree of controllability, yielding well-conditioned models for control. Implemented as an end-to-end Neural ODE framework, our method learns models that are both predictive and controllable from limited data. Experiments on nonlinear benchmarks demonstrate accurate long-horizon prediction, reliable MPC performance, and substantially improved data efficiency.

---

## 论文详细总结（自动生成）

# 论文总结：Learning Koopman Representations with Controllability Guarantees

> 说明：OpenReview PDF 正文因 CAPTCHA 未能获取，以下总结主要依据论文摘要与元数据；涉及具体数据集、基线、算力、实验组数等信息，材料中未提供处已明确标注。

## 1. 核心问题与整体含义
- **研究动机**：从有限数据学习非线性动力学模型是控制领域的核心问题，但存在两个挑战：
  - 如何在有限数据下学习**准确**的模型；
  - 如何保证学习到的模型**适合标称系统的控制设计**。
- **背景**：Koopman 表示可将非线性动力学嵌入线性潜空间，便于控制设计，但仅追求预测精度不一定保证可控性，可能导致下游控制方法（如 MPC）不可靠。
- **整体含义**：论文提出在 Koopman 表示学习中强制引入**可控性先验**，使模型既能捕捉系统结构、提升数据效率，又能保证存在控制策略将系统从任意初态驱动到任意目标态，为面向控制的表示学习提供新范式。

## 2. 方法论
- **核心思想**：不直接在原始状态空间学习非线性动力学，而是在潜空间中学习线性表示，并强制学习到的潜模型满足**可控性**。
- **理论保证**：论文证明，若学习到的潜模型可控，则标称状态空间中的系统也可控，从而保证控制策略的存在性。
- **关键技术细节**：
  - 引入潜动力学矩阵的**规范参数化**，用于在参数化层面强制可控性；
  - 加入**基于 Gramian 的正则化**，调节可控程度，使模型具有良态性，更适合控制；
  - 整体实现为**端到端 Neural ODE 框架**，从有限数据中同时学习表示与动力学。
- **算法流程概述**：
  - 数据 → Neural ODE 潜空间线性动力学建模；
  - 通过规范参数化保证潜模型可控；
  - 通过 Gramian 正则塑造可控性；
  - 潜模型可控 ⇒ 标称系统可控 ⇒ 支持 MPC 等下游控制方法。

## 3. 实验设计
- **场景/数据**：摘要称在**非线性基准**上进行实验。
- **评估任务**：包括长期预测、模型预测控制（MPC）性能、数据效率。
- **Benchmark**：给定材料未列出具体 benchmark 名称。
- **对比方法**：未提供具体基线方法或对比算法。
- **结果描述**：实验展示出准确的长期预测、可靠的 MPC 性能以及显著提升的数据效率。具体实验平台、指标与基线细节无法从现有材料确认。

## 4. 资源与算力
- 材料中**未明确说明**使用的 GPU 型号、数量、训练时长、计算资源规模。
- 也未提供 Neural ODE 求解器设置、训练成本或推理成本等信息。

## 5. 实验数量与充分性
- 未给出具体实验组数、数据集数量、消融实验数量。
- 从摘要可推断，实验至少覆盖三类评估：长期预测、MPC、数据效率；可能包含多个非线性基准场景。
- 由于缺少基线、超参数、统计显著性、重复次数等信息，**无法客观判断实验是否充分、公平**。
- 若仅依据摘要，实验设计直接面向控制目标，具有一定针对性，但仍需全文验证。

## 6. 主要结论与发现
- 在 Koopman 表示学习中强制可控性，可同时改善建模与控制性能。
- 该约束能捕捉系统结构特征，提高有限数据下的数据效率。
- 潜模型的可控性可传递到标称状态空间，保证存在驱动系统到目标态的控制策略。
- 方法支持 MPC 等现代控制技术，实验中表现出准确长期预测与可靠 MPC 性能。
- 为面向控制的 Koopman 表示学习提供了“可控性保证”的新思路。

## 7. 优点
- 将**可控性作为先验约束**，而非仅事后验证，理论动机清晰。
- 提供潜空间可控性到标称空间可控性的理论证明。
- 规范参数化与 Gramian 正则化结合，兼顾可控性存在性与数值良态性。
- 端到端 Neural ODE 框架适合从数据学习连续时间动力学。
- 评估任务直接面向控制（预测、MPC、数据效率），与动机一致。
- 元数据表明论文被 ICLR 2026 接收，评分 9.0，反映评审对其新颖性与质量的认可。

## 8. 不足与局限
- **材料限制**：无法获取全文，实验细节、算力、数据集、基线、消融等均不可核实。
- **实验覆盖**：未知是否覆盖真实系统、高维系统、噪声、部分观测、分布外泛化等场景。
- **偏差风险**：若基线或指标选择偏向自身方法，可能影响公平性；需全文确认。
- **应用限制**：可控性保证可能依赖潜空间线性、标称系统、参数化条件及 Gramian 正则超参数；在强非线性、约束、不确定性下是否稳健未知。
- **计算成本**：Neural ODE 与 Gramian 正则可能增加训练或求解成本，文中未说明。
- **控制性能边界**：可控性不等同于约束满足、安全性与鲁棒性，MPC 性能仍受模型误差影响。

（完）
