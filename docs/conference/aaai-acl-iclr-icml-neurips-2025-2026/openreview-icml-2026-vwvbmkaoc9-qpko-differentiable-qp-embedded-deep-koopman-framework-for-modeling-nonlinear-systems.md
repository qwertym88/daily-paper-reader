---
title: "QPKO: Differentiable QP-Embedded Deep Koopman Framework for Modeling Nonlinear Systems"
title_zh: QPKO：面向非线性系统建模的可微QP嵌入式深度Koopman框架
authors: "Runze Tian, Peng Kou"
date: 2026-04-30
pdf: "https://openreview.net/pdf/3f2e9bd86af53b44fe6a81170c961f4f927e1ec5.pdf"
tags: ["query:koopman-rl"]
score: 9.0
evidence: 用于非线性系统建模的可微二次规划嵌入式深度Koopman框架
tldr: 现有深度Koopman建模的训练范式要么优化复杂度高，要么难以端到端训练，限制了建模精度与效率。本文提出可微二次规划嵌入式深度Koopman框架QPKO，将单步精度目标与多步精度约束构成QP问题嵌入训练过程。该框架实现了可微的端到端学习，在非线性系统建模中兼顾精度与训练效率，为数据驱动Koopman观测函数学习提供了新的训练范式。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有深度Koopman训练范式优化复杂度高或阻碍端到端训练，限制了建模精度与效率。
method: 提出可微QP嵌入式深度Koopman框架，将单步精度目标与多步精度约束组成二次规划嵌入训练。
result: 该框架实现可微端到端学习，在非线性系统建模中同时提升建模精度与训练效率。
conclusion: 为数据驱动Koopman观测函数学习提供了高效且可微的训练范式。
---

## Abstract
Deep learning has been widely regarded as a powerful tool for Koopman operator theory-based modeling, as it provides a promising architecture for data-driven learning of observable functions. To fully leverage this advantage, a well-designed training paradigm is required. However, the existing training paradigms typically either incur high optimization complexity or hinder effective end-to-end training, limiting modeling accuracy and training efficiency. To address this issue, we propose a differentiable quadratic programming (QP)-embedded deep Koopman framework (QPKO). In QPKO, a QP problem, which comprises a one-step accuracy-oriented objective function and a set of multi-step accuracy-oriented constraints, is formulated to introduce a mapping from observable functions to the global linear model. By doing so, the global linear model no longer needs to be treated as an independent trainable component, thereby effectively reducing optimization complexity. This QP-based mapping is implemented as a differentiable and computationally efficient module by leveraging OptNet (a differentiable QP layer), enabling effective end-to-end training. Experiments on four nonlinear dynamical systems show that QPKO achieves satisfactory improvements in modeling accuracy, training efficiency, and control performance.

---

## 论文详细总结（自动生成）

# QPKO 论文中文总结

> 说明：提供的 PDF 提取文本实际为 OpenReview 验证页面，未包含论文正文。以下总结主要依据论文元数据、TLDR、Abstract 与结论信息；未明确说明之处将标注为“文中未给出/无法确认”。

## 1. 核心问题与整体含义

- **研究背景**：深度学习被广泛用于基于 Koopman 算子理论的建模，尤其是数据驱动地学习可观测量函数（observable functions）。但要充分发挥该优势，需要合适的训练范式。
- **核心问题**：现有深度 Koopman 训练范式通常存在两类问题：
  - 优化复杂度高；
  - 难以进行有效的端到端训练。
  这限制了建模精度与训练效率。
- **整体含义**：论文提出 **QPKO**，即“可微二次规划嵌入式深度 Koopman 框架”，试图把 QP 求解嵌入训练过程，使全局线性模型不再作为独立可训练组件，从而降低优化复杂度并实现可微端到端学习。
- **定位**：为数据驱动 Koopman 观测函数学习提供一种新的、高效且可微的训练范式，兼顾建模精度、训练效率与控制性能。

## 2. 方法论

- **核心思想**：
  - 将深度 Koopman 建模中的全局线性模型求解，转化为一个 **二次规划（QP）问题**。
  - 该 QP 由两部分构成：
    - 一个面向**单步精度**的目标函数；
    - 一组面向**多步精度**的约束条件。
  - 通过该 QP 建立从“可观测量函数”到“全局线性模型”的映射。
- **关键技术细节**：
  - 全局线性模型不再被视为独立可训练组件，而是由 QP 求解得到，因此可减少优化复杂度。
  - 使用 **OptNet**，即一个可微 QP 层，将该 QP 映射实现为可微且计算高效的模块。
  - 由于 QP 层可微，梯度可以从全局线性模型反传到可观测量函数/深度网络，实现端到端训练。
- **算法流程（文字描述）**：
  1. 深度网络学习可观测量函数；
  2. 根据当前可观测量，构造单步精度目标与多步精度约束，形成 QP；
  3. 通过可微 QP 层求解该 QP，得到全局线性模型；
  4. 利用可微性反向传播，更新可观测量函数相关参数；
  5. 以端到端方式联合优化单步与多步建模精度。

## 3. 实验设计

- **实验场景**：
  - 在 **四个非线性动力系统** 上进行实验。
  - 但给定材料中未列出这四个系统的具体名称、数据生成方式或数据集细节。
- **Benchmark / 评估指标**：
  - 摘要提到评估 **建模精度、训练效率、控制性能**。
  - 具体 benchmark 设置、评价指标定义、控制任务形式在给定材料中未明确。
- **对比方法**：
  - 摘要仅概括性提到“现有训练范式”存在高优化复杂度或难以端到端训练的问题。
  - 未给出具体对比基线名称、实现细节或公平性设置。

## 4. 资源与算力

- 给定材料中 **未明确说明** 使用的 GPU 型号、数量、训练时长、内存、计算平台等算力资源。
- 因此无法从现有信息判断该方法的计算开销、可复现成本或训练规模。
- 仅能从方法描述推断：由于嵌入可微 QP 层，训练中可能涉及 QP 求解开销，但具体成本未披露。

## 5. 实验数量与充分性

- **实验数量**：
  - 至少包含 **四个非线性动力系统** 的实验。
  - 是否包含消融实验、不同 QP 约束设置、不同网络结构、不同噪声条件等，给定材料未说明。
- **充分性判断**：
  - 从摘要层面看，实验覆盖多个非线性系统，并同时考察建模精度、训练效率与控制性能，具有一定多维验证意图。
  - 但缺少以下关键信息，难以完全判断充分性与公平性：
    - 具体对比方法；
    - 数据集与任务细节；
    - 随机种子、重复次数、统计显著性；
    - 消融实验与超参数敏感性；
    - 计算资源与训练成本。
- **客观性/公平性**：
  - 元数据给出 ICML-2026-Accepted 与 score 9.0，说明评审层面有一定认可。
  - 但仅凭摘要无法验证实验是否完全客观、公平或可复现。

## 6. 主要结论与发现

- QPKO 在四个非线性动力系统上取得了 **建模精度、训练效率和控制性能** 方面的满意提升。
- 通过将 QP 嵌入训练过程，并利用可微 QP 层，QPKO 实现了有效的 **端到端训练**。
- 全局线性模型不再作为独立可训练组件，有助于 **降低优化复杂度**。
- 该框架为数据驱动 Koopman 观测函数学习提供了一种高效且可微的新训练范式。

## 7. 优点

- **方法设计亮点**：
  - 将 QP 嵌入深度 Koopman 训练，把单步精度目标与多步精度约束结合，兼顾短期拟合与多步预测/长期精度。
  - 使用 OptNet 可微 QP 层，使 QP 求解可嵌入端到端训练流程。
  - 避免将全局线性模型作为独立训练组件，可能降低优化复杂度。
- **实验设计亮点**：
  - 在四个非线性动力系统上验证，覆盖多个系统。
  - 同时评估建模精度、训练效率和控制性能，不局限于单一指标。
- **学术认可**：
  - 元数据显示论文被 ICML-2026 接收，评审分数 9.0，表明方法新颖性与潜在价值受到认可。

## 8. 不足与局限

- **信息完整性不足**：
  - 给定 PDF 文本为验证页面，缺少正文，无法核实具体公式、算法细节、实验设置与结果。
- **实验覆盖有限或未充分披露**：
  - 仅知使用四个非线性动力系统，未说明是否覆盖高维系统、真实世界数据、噪声、部分观测、分布外泛化等场景。
  - 未说明消融实验数量与结果。
- **对比与公平性风险**：
  - 未列出具体基线方法与调参策略，难以判断对比是否公平。
- **计算与扩展性限制**：
  - 可微 QP 层可能带来额外求解开销，尤其在大规模或高维系统中。
  - QP 的构造可能依赖问题结构、凸性或约束设计；这些假设在正文中是否充分讨论，现有材料无法确认。
- **应用限制**：
  - 若实际系统难以构造合适的单步目标与多步约束 QP，方法适用性可能受限。
  - 控制性能虽有提及，但未说明控制器类型、稳定性保证或安全约束。

（完）
