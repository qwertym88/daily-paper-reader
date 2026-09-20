---
title: Thompson Sampling in Function Spaces via Neural Operators
title_zh: 基于神经算子的函数空间Thompson采样
authors: "Rafael Oliveira, Xuesong Wang, Kian Ming A. Chai, Edwin V. Bonilla"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=F54u4NkFvS"
tags: ["query:koopman-rl"]
score: 4.0
evidence: 用于函数空间优化的神经算子代理模型
tldr: 在函数空间优化中，目标常是未知算子输出的已知泛函，而算子查询（如高保真仿真）代价高昂。本文提出将Thompson采样推广到此类函数空间问题，采用先采样再优化的策略，用神经算子代理模型充当高斯过程后验的近似样本，从而避免显式不确定性量化。作者给出遗憾界及神经算子与高斯过程在无穷维设定下的理论联系，并在实验中与多种贝叶斯方法对比。该工作属于算子学习范畴，与Koopman算子方法有方法论关联但并非同一目标。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 函数空间优化中算子查询代价高昂，需要高效的代理模型与决策策略。
method: 将Thompson采样推广到函数空间，用神经算子代理充当高斯过程近似样本并推导遗憾界。
result: 给出理论保证并在基准上与贝叶斯方法对比。
conclusion: 建立了神经算子与高斯过程在无穷维设定下的理论联系。
---

## Abstract
We propose an extension of Thompson sampling to optimization problems over function spaces where the objective is a known functional of an unknown operator's output. We assume that queries to the operator (such as running a high-fidelity simulator or physical experiment) are costly, while functional evaluations on the operator's output are inexpensive. Our algorithm employs a sample-then-optimize approach using neural operator surrogates. This strategy avoids explicit uncertainty quantification by treating trained neural operators as approximate samples from a Gaussian process (GP) posterior. We derive regret bounds and theoretical results connecting neural operators with GPs in infinite-dimensional settings. Experiments benchmark our method against other Bayesian optimization baselines on functional optimization tasks involving partial differential equations of physical systems, demonstrating better sample efficiency and significant performance gains.

---

## 论文详细总结（自动生成）

> 说明：提供的 PDF 提取文本仅为 OpenReview 浏览器验证页，未包含论文正文。以下总结主要基于论文摘要与元数据；正文未披露之处会明确标注为“未提供”或“无法判断”。

## 1. 核心问题与整体含义

- **研究动机**：在函数空间优化问题中，目标函数通常是某个未知算子输出的已知泛函。对算子的查询（例如运行高保真仿真或物理实验）代价高昂，但对算子输出进行泛函评估相对便宜。
- **核心问题**：如何在此类“算子查询昂贵、泛函评估廉价”的设定下，高效地进行函数空间优化。
- **背景关联**：该工作属于算子学习与贝叶斯优化的交叉方向；与 Koopman 算子方法有方法论关联，但优化目标并不相同。
- **整体含义**：作者将 Thompson 采样从传统参数空间/有限维空间推广到函数空间，并借助神经算子代理模型近似高斯过程后验样本，从而避免显式不确定性量化。

## 2. 方法论：核心思想与算法流程

- **核心思想**：采用“先采样、再优化”（sample-then-optimize）策略，将 Thompson 采样扩展到函数空间优化。
- **关键技术细节**：
  - 目标是一个未知算子输出的已知泛函。
  - 对未知算子的查询昂贵，因此需要代理模型减少真实查询次数。
  - 使用神经算子作为代理模型。
  - 将训练好的神经算子视为高斯过程后验的近似样本，而不是显式建模和量化不确定性。
- **算法流程（文字描述）**：
  1. 初始化或训练神经算子代理模型。
  2. 在每一轮中，将神经算子代理视作 GP 后验的近似样本，从中采样一个候选算子输出或目标函数。
  3. 针对该采样样本优化已知泛函，选择下一个待查询的输入或函数。
  4. 对真实昂贵算子执行查询，获得输出。
  5. 利用新数据更新神经算子代理，进入下一轮。
- **理论部分**：
  - 推导了遗憾界（regret bounds）。
  - 给出了神经算子与高斯过程在无穷维设定下的理论联系。
  - 具体遗憾界形式、假设条件和证明细节未在提供文本中给出。

## 3. 实验设计

- **实验场景**：涉及物理系统偏微分方程（PDE）的功能优化任务。
- **Benchmark**：摘要称在函数优化任务上进行基准测试，但具体 benchmark 名称未提供。
- **对比方法**：与其他贝叶斯优化基线方法比较，元数据提到与多种贝叶斯方法对比；具体基线名称未提供。
- **评价指标**：样本效率和性能增益。摘要称方法表现出更好的样本效率和显著性能提升。

## 4. 资源与算力

- 提供的文本中**未明确提及** GPU 型号、数量、训练时长、显存消耗或计算资源规模。
- 因此无法评估该工作的算力需求和复现成本。

## 5. 实验数量与充分性

- **实验组数**：未提供具体数量，无法判断使用了多少数据集、PDE 任务或消融实验。
- **消融实验**：未提及是否有消融研究。
- **客观性与公平性**：摘要称与贝叶斯优化基线比较，但缺少基线实现、调参策略、重复次数、统计显著性检验等细节，因此无法充分评估公平性。
- **总体判断**：仅从摘要看，实验覆盖了 PDE 功能优化任务，但信息不足以判断实验是否充分。

## 6. 主要结论与发现

- 将 Thompson 采样成功推广到函数空间优化问题。
- 使用神经算子代理作为高斯过程后验的近似样本，可以避免显式不确定性量化。
- 给出了遗憾界以及神经算子与 GP 在无穷维设定下的理论联系。
- 在涉及 PDE 的物理系统功能优化任务中，方法相比其他贝叶斯优化基线具有更好的样本效率和显著性能提升。

## 7. 优点

- **方法创新**：将 Thompson 采样扩展到函数空间，并结合神经算子代理模型。
- **避免显式 UQ**：用训练后的神经算子近似 GP 后验样本，可能降低不确定性量化的计算负担。
- **理论贡献**：提供遗憾界，并建立神经算子与 GP 在无穷维设定下的联系。
- **应用价值**：面向高保真仿真或物理实验等昂贵查询场景，具有实际意义。
- **实验方向合理**：在 PDE 功能优化任务上验证，贴合科学计算与物理系统优化需求。

## 8. 不足与局限

- **正文缺失导致验证困难**：提供的 PDF 文本仅为验证页，无法核对具体算法、公式、实验设置和理论证明。
- **实验细节不足**：未提供具体 PDE 数据集、benchmark、基线方法名称、超参数和评价协议。
- **算力未报告**：缺少 GPU 型号、数量、训练时长等信息，影响复现性评估。
- **理论适用性未知**：无穷维设定下的假设、神经算子近似 GP 后验的误差界等未在提供文本中说明。
- **实验覆盖有限或未知**：无法判断是否覆盖足够多任务、是否有消融实验和统计检验。
- **应用限制**：方法依赖“算子查询昂贵、泛函评估便宜”的设定；若实际场景不满足该条件，优势可能减弱。

（完）
