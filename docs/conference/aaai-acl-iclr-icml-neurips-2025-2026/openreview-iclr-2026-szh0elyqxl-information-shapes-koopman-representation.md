---
title: Information Shapes Koopman Representation
title_zh: 信息塑造Koopman表征
authors: "Xiaoyuan Cheng, Wenxuan Yuan, Yiming Yang, Yuanzhao Zhang, Sibo Cheng, Yi He, Zhuo Sun"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=Szh0ELyQxL"
tags: ["query:koopman-rl"]
score: 7.0
evidence: 从信息瓶颈视角研究Koopman表征学习
tldr: Koopman算子为动态系统建模提供强大框架，但其无限维特性使寻找合适有限维子空间困难，尤其在深度架构中。本文从信息瓶颈视角重新审视Koopman学习，指出潜在互信息促进简洁性，但过度强调简洁会导致潜空间坍缩。研究揭示了表达性与简洁性的权衡机制，为深度Koopman表征学习提供了理论指导与改进方向。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: Koopman算子无限维特性使深度架构难以找到合适有限维子空间，表征学习次优。
method: 从信息瓶颈视角分析Koopman学习，研究潜在互信息对表达性与简洁性权衡的影响。
result: 发现潜在互信息促进简洁性，但过度强调会导致潜空间坍缩。
conclusion: 为深度Koopman表征学习提供了理论指导。
---

## Abstract
The Koopman operator provides a powerful framework for modeling dynamical systems and has attracted growing interest from the machine learning community. However, its infinite-dimensional nature makes identifying suitable finite-dimensional subspaces challenging, especially for deep architectures. We argue that these difficulties come from suboptimal representation learning, where latent variables fail to balance expressivity and simplicity. This tension is closely related to the information bottleneck (IB) dilemma: constructing compressed representations that are both compact and predictive. Rethinking Koopman learning through this lens, we demonstrate that latent mutual information promotes simplicity, yet an overemphasis on simplicity may cause latent space to collapse onto a few dominant modes. In contrast, expressiveness is sustained by the von Neumann entropy, which prevents such collapse and encourages mode diversity. This insight leads us to propose an information-theoretic Lagrangian formulation that explicitly balances this tradeoff. Furthermore, we propose a new algorithm based on the Lagrangian formulation that encourages both simplicity and expressiveness, leading to a stable and interpretable Koopman representation. Beyond quantitative evaluations, we further visualize the learned manifolds under our representations, observing empirical results consistent with our theoretical predictions. Finally, we validate our approach across a diverse range of dynamical systems, demonstrating improved performance over existing Koopman learning methods.

---

## 论文详细总结（自动生成）

## 0. 材料说明

- 提供的 PDF 提取文本实际为 OpenReview 浏览器验证页，未包含论文正文。
- 以下总结主要基于元数据与摘要信息；凡摘要未明确说明的实验细节、算力、数据集与基线，均标注为“未说明/无法确认”。
- 元数据表明该论文题为 **Information Shapes Koopman Representation**，中文可译为“信息塑造 Koopman 表征”，来源为 **ICLR-2026-Accepted**。

## 1. 核心问题与整体含义

- **研究背景**：Koopman 算子为动态系统建模提供了强有力框架，可将非线性动力学提升到线性算子视角，因此受到机器学习社区关注。
- **核心问题**：Koopman 算子本质上是无限维的，如何识别合适的有限维子空间仍是难题，尤其在深度架构中更突出。
- **作者判断**：这些困难来自**次优表征学习**，即潜变量未能平衡“表达性”与“简洁性”。
- **理论视角**：该张力与**信息瓶颈困境**密切相关——需要构造既紧凑又具有预测能力的压缩表示。
- **整体含义**：论文试图从信息论角度重新审视 Koopman 学习，解释潜空间为何坍缩或失效，并给出兼顾简洁性与表达性的表征学习方案。

## 2. 方法论

- **核心思想**：从信息瓶颈视角研究 Koopman 表征学习，认为潜在互信息促进简洁性，但过度强调简洁会导致潜空间坍缩到少数主导模态。
- **表达性机制**：表达性由 **von Neumann 熵**维持，可防止潜空间坍缩，并鼓励模态多样性。
- **关键权衡**：简洁性对应压缩与低维主导模态，表达性对应模态多样性与动态可区分性；二者需要显式平衡。
- **理论形式**：论文提出一种**信息论拉格朗日形式**，用拉格朗日乘子思想显式平衡简洁性与表达性之间的权衡。
- **算法思路**：进一步提出基于该拉格朗日形式的新算法，鼓励简洁性与表达性共存，从而得到稳定且可解释的 Koopman 表征。
- **公式细节**：提供的摘要未给出显式目标函数或算法伪代码；只能概括为“预测/动态一致性 + 简洁性正则 + 表达性/熵正则”的联合优化框架。

## 3. 实验设计

- **实验场景**：摘要称在“多样范围的动态系统”上验证方法。
- **评估方式**：包括定量评估，以及对学习到的流形进行可视化，观察经验结果是否与理论预测一致。
- **Benchmark**：未说明具体 benchmark 名称。
- **对比方法**：仅笼统提到“现有 Koopman 学习方法”，未列出具体基线。
- **数据集/系统名称**：未说明具体数据集、物理系统或合成系统名称。

## 4. 资源与算力

- 提供的文本中**未提及** GPU 型号、数量、训练时长、参数量或计算资源。
- 因此无法总结算力开销，也无法判断方法在大规模场景下的计算可行性。

## 5. 实验数量与充分性

- 摘要仅表明在“多样动态系统”上进行了验证，并包含定量评估与流形可视化。
- 具体实验组数、消融实验数量、不同随机种子、统计显著性检验等均未说明。
- 因此**无法客观判断实验是否充分**。
- 对比公平性也无法评估，因为缺少基线方法、数据集划分、评价指标与超参搜索协议等细节。

## 6. 主要结论与发现

- 潜在互信息有助于提升简洁性，但过度强调简洁性会导致潜空间坍缩到少数主导模态。
- von Neumann 熵有助于维持表达性，防止坍缩并鼓励模态多样性。
- 通过信息论拉格朗日形式可以显式平衡简洁性与表达性。
- 基于该形式的算法能得到更稳定、更可解释的 Koopman 表征。
- 可视化学习流形与理论预测一致。
- 在多种动态系统上，方法声称优于现有 Koopman 学习方法。

## 7. 优点

- **理论视角新颖**：将 Koopman 表征学习与信息瓶颈、互信息、von Neumann 熵联系起来，解释潜空间坍缩与模态多样性问题。
- **问题定位清晰**：指出深度 Koopman 学习的核心困难是表达性与简洁性的失衡，而非单纯优化困难。
- **方法具有原则性**：提出信息论拉格朗日形式，使简洁性与表达性的权衡显式化。
- **兼顾理论与实证**：不仅有理论分析，还通过流形可视化与多动态系统验证。
- **可解释性导向**：强调稳定且可解释的 Koopman 表征，符合动态系统建模需求。

## 8. 不足与局限

- **正文信息缺失**：当前提供的 PDF 文本为验证页，无法评估完整方法、公式推导与实验细节。
- **实验覆盖不明确**：具体数据集、动态系统类型、评价指标、基线方法均未说明。
- **算力与复现性未报告**：未提及计算资源、训练时长、代码或超参设置。
- **公平性无法判断**：缺少基线调参、数据划分与统计检验信息。
- **应用限制未讨论**：如高维系统、噪声观测、非平稳动力学、长期预测、实时控制等场景下的表现未知。
- **潜在风险**：信息论目标可能引入额外超参数，实际训练中是否对拉格朗日乘子敏感尚不清楚。

（完）
