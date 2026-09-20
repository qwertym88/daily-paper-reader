---
title: Efficient Parametric SVD of Koopman Operator for Stochastic Dynamical Systems
title_zh: 面向随机动力系统的Koopman算子高效参数化SVD
authors: "Minchan Jeong, Jongha Jon Ryu, Se-Young Yun, Gregory W. Wornell"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=kL2pnzClyD"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 面向非线性随机动力系统的Koopman算子
tldr: Koopman算子通过线性算子理论分析非线性动力系统，但现有深度学习辨识方法在目标计算中需对经验二阶矩矩阵做SVD与求逆等数值不稳定操作的反向传播，导致梯度有偏且难以扩展到大系统。本文提出面向随机动力系统的Koopman算子高效参数化SVD方法，避免不稳定运算，从而获得更可靠的梯度估计并提升可扩展性。该工作为数据驱动Koopman谱分析提供了更稳定的计算途径。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有学习Koopman奇异子空间的方法需对二阶矩矩阵做不稳定SVD与求逆，梯度有偏且难扩展。
method: 提出面向随机动力系统的Koopman算子高效参数化SVD方法，避免数值不稳定的反向传播。
result: 获得更可靠的梯度估计并提升对大系统的可扩展性。
conclusion: 为数据驱动Koopman谱分析提供更稳定的计算途径。
---

## Abstract
The Koopman operator provides a principled framework for analyzing nonlinear dynamical systems through linear operator theory. Recent advances in dynamic mode decomposition (DMD) have shown that trajectory data can be used to identify dominant modes of a system in a data-driven manner. Building on this idea, deep learning methods such as VAMPnet and DPNet have been proposed to learn the leading singular subspaces of the Koopman operator. 
However, these methods require backpropagation through potentially numerically unstable operations on empirical second moment matrices, such as singular value decomposition and matrix inversion, during objective computation, which can introduce biased gradient estimates and hinder scalability to large systems.
In this work, we propose a scalable and conceptually simple method for learning the top-$k$ singular functions of the Koopman operator for stochastic dynamical systems based on the idea of low-rank approximation. Our approach eliminates the need for unstable linear-algebraic operations and integrates easily into modern deep learning pipelines. Empirical results demonstrate that the learned singular subspaces are both reliable and effective for downstream tasks such as eigen-analysis and multi-step prediction.

---

## 论文详细总结（自动生成）

# 论文总结：Efficient Parametric SVD of Koopman Operator for Stochastic Dynamical Systems

> 说明：提供的 PDF 提取文本实际为 OpenReview 浏览器验证页面，未包含论文正文；以下总结主要依据论文摘要与 Markdown 元数据。凡正文未披露的信息，均标注为“未说明/无法确认”，不做臆测。
>
> - 论文标题：Efficient Parametric SVD of Koopman Operator for Stochastic Dynamical Systems
> - 中文标题：面向随机动力系统的 Koopman 算子高效参数化 SVD
> - 作者：Minchan Jeong, Jongha Jon Ryu, Se-Young Yun, Gregory W. Wornell
> - 来源：NeurIPS-2025-Accepted，OpenReview 元数据评分 8.0
> - 日期：2025-09-18

## 1. 核心问题与整体含义

- **研究背景**：Koopman 算子提供了一种用线性算子理论分析非线性动力系统的框架。近年来，动态模式分解（DMD）及相关数据驱动方法表明，可以利用轨迹数据识别系统的主导模态。
- **现有方法**：VAMPnet、DPNet 等深度学习方法被用于学习 Koopman 算子的主导奇异子空间。
- **核心问题**：这些方法在目标函数计算中，需要对经验二阶矩矩阵执行潜在数值不稳定的线性代数操作，例如奇异值分解（SVD）和矩阵求逆，并通过这些操作反向传播。这会导致：
  - 梯度估计有偏；
  - 难以扩展到大规模系统；
  - 训练稳定性和可靠性受限。
- **整体含义**：本文旨在为随机动力系统提供一种可扩展、概念简单的方法，学习 Koopman 算子的 top-k 奇异函数，避免不稳定的线性代数反向传播，从而为数据驱动 Koopman 谱分析提供更稳定的计算途径。

## 2. 方法论

- **核心思想**：基于低秩近似思想，直接参数化并学习 Koopman 算子的 top-k 奇异函数，避免在目标计算中显式执行 SVD 与矩阵求逆等不稳定操作。
- **关键技术要点**：
  - 面向随机动力系统；
  - 学习 Koopman 算子的前 k 个奇异函数/主导奇异子空间；
  - 消除对经验二阶矩矩阵进行 SVD 和求逆的需求；
  - 使目标计算更容易嵌入现代深度学习管线，并支持稳定反向传播；
  - 目标是获得更可靠的梯度估计，并提升对大系统的可扩展性。
- **算法流程（摘要级推断）**：
  1. 输入随机动力系统的轨迹数据；
  2. 参数化 Koopman 算子的 top-k 奇异函数或奇异子空间；
  3. 通过低秩近似构造目标函数，避免显式 SVD/矩阵求逆；
  4. 利用深度学习优化方法反向传播训练；
  5. 将学到的奇异子空间用于特征分析、多步预测等下游任务。
- **未披露内容**：具体损失函数、参数化形式、低秩分解公式、优化细节、理论推导等在提供的摘要中未给出，无法展开。

## 3. 实验设计

- **使用场景**：摘要指出方法面向随机动力系统，并利用轨迹数据进行数据驱动学习。
- **下游任务**：摘要明确提到两类下游任务：
  - 特征分析（eigen-analysis）；
  - 多步预测（multi-step prediction）。
- **Benchmark**：未说明具体 benchmark。
- **数据集**：未说明使用了哪些数据集或具体动力系统。
- **对比方法**：摘要背景提到 VAMPnet 和 DPNet，但未明确说明实验中是否将它们作为基线进行对比。
- **评价指标**：未说明。

## 4. 资源与算力

- 提供的摘要和元数据中未提及 GPU 型号、数量、训练时长、参数量、计算资源等任何算力信息。
- 因此无法总结资源与算力使用情况。

## 5. 实验数量与充分性

- 从摘要看，至少包含两类下游任务评估：特征分析和多步预测。
- 但具体实验组数、数据集数量、消融实验、不同随机种子、统计显著性检验、超参数敏感性分析等均未说明。
- 因此无法判断实验是否充分、客观、公平。需要论文正文才能进一步评估。

## 6. 主要结论与发现

- 提出了一种可扩展且概念简单的方法，用于学习随机动力系统中 Koopman 算子的 top-k 奇异函数。
- 方法基于低秩近似，避免了对经验二阶矩矩阵执行 SVD 和矩阵求逆等不稳定线性代数操作。
- 该方法可以较容易地集成到现代深度学习管线中。
- 实证结果表明，学到的奇异子空间在特征分析和多步预测等下游任务中可靠且有效。
- 元数据进一步总结：该方法可获得更可靠的梯度估计，并提升对大系统的可扩展性，为数据驱动 Koopman 谱分析提供更稳定的计算途径。

## 7. 优点

- **数值稳定性**：避免在反向传播中经过 SVD、矩阵求逆等不稳定操作，有望减少有偏梯度。
- **可扩展性**：方法设计目标之一是可扩展到较大系统。
- **概念简单**：基于低秩近似，思路相对直接，易于集成到深度学习框架。
- **任务相关性**：学习到的奇异子空间直接用于特征分析和多步预测，具有实际下游价值。
- **问题定位明确**：针对现有 VAMPnet、DPNet 等方法在数值稳定性和扩展性上的痛点。

## 8. 不足与局限

- **正文信息缺失**：由于提供的 PDF 文本是验证页面，无法核实论文的完整方法、公式、理论保证和实验细节。
- **实验覆盖未知**：未说明数据集、benchmark、基线方法、评价指标和实验组数，无法判断泛化性与公平性。
- **算力未披露**：没有 GPU 型号、数量、训练时长等信息。
- **理论保证未说明**：摘要未提及收敛性、误差界或低秩近似的理论分析。
- **应用限制**：方法面向随机动力系统；对确定性系统、非平稳系统或高维实际系统的适用性需正文验证。
- **超参数与规模敏感性**：top-k 中 k 的选择、秩选择、模型容量等对性能的影响未说明。
- **比较公平性无法评估**：虽然背景提到 VAMPnet 和 DPNet，但摘要未明确是否进行系统对比，因此难以判断相对优势的实证强度。

（完）
