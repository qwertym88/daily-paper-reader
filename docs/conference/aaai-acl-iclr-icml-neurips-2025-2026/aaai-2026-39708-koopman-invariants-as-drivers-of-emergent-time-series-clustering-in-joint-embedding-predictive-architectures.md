---
title: Koopman Invariants as Drivers of Emergent Time-Series Clustering in Joint-Embedding Predictive Architectures
title_zh: Koopman不变量作为联合嵌入预测架构中时间序列聚类涌现的驱动因素
authors: "Pablo Ruiz-Morales, Dries Vanoost, Davy Pissoort, Mathias Verbeke"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39708/43669"
tags: ["query:koopman-rl"]
score: 8.0
evidence: JEPA隐式学习系统Koopman算子的不变子空间
tldr: 联合嵌入预测架构（JEPA）能按动力学机制聚类时间序列，但这一现象缺乏理论解释。本文提出新解释，假设JEPA的预测目标隐式驱动其学习系统Koopman算子的不变子空间，并证明理想化JEPA损失在编码器表示机制指示函数（即Koopman特征函数）时被最小化。作者在已知动力学的合成数据上验证该理论，指出将线性预测器约束为近恒等算子是关键归纳偏置。该工作将表示学习与Koopman理论联系起来，深化了对自监督模型的理解。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39708/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 880, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39708/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 1147, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39708/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1836, \"height\": 717, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39708/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39708/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 865, \"height\": 554, \"label\": \"Figure\"}]"
motivation: JEPA能按动力学机制聚类时间序列，但缺乏理论解释。
method: 提出理论假设并证明理想JEPA损失在编码器表示Koopman特征函数时最小化，合成数据验证。
result: 证实线性预测器近恒等约束是关键归纳偏置。
conclusion: 将自监督表示学习与Koopman理论联系起来。
---

## Abstract
Joint-Embedding Predictive Architectures (JEPAs), a powerful class of self-supervised models, exhibit an unexplained ability to cluster time-series data by their underlying dynamical regimes. We propose a novel theoretical explanation for this phenomenon, hypothesizing that JEPA's predictive objective implicitly drives it to learn the invariant subspace of the system's Koopman operator. We prove that an idealized JEPA loss is minimized when the encoder represents the system's regime indicator functions, which are Koopman eigenfunctions. This theory was validated on synthetic data with known dynamics, demonstrating that constraining the JEPA's linear predictor to be a near-identity operator is the key inductive bias that forces the encoder to learn these invariants. We further discuss that this constraint is critical for selecting this interpretable solution from a class of mathematically equivalent but entangled optima, revealing the predictor's role in representation disentanglement. This work demystifies a key behavior of JEPAs, provides a principled connection between modern self-supervised learning and dynamical systems theory, and informs the design of more robust and interpretable time-series models.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
JEPA隐式学习系统Koopman算子的不变子空间。

### 2. 核心内容
联合嵌入预测架构（JEPA）能按动力学机制聚类时间序列，但这一现象缺乏理论解释。本文提出新解释，假设JEPA的预测目标隐式驱动其学习系统Koopman算子的不变子空间，并证明理想化JEPA损失在编码器表示机制指示函数（即Koopman特征函数）时被最小化。作者在已知动力学的合成数据上验证该理论，指出将线性预测器约束为近恒等算子是关键归纳偏置。该工作将表示学习与Koopman理论联系起来，深化了对自监督模型的理解。

### 3. 对应检索需求
representation learning with Koopman operators for control。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/39708](https://ojs.aaai.org/index.php/AAAI/article/view/39708)
