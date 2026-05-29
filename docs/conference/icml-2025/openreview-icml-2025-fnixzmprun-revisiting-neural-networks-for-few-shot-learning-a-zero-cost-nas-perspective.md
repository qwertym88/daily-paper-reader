---
title: "Revisiting Neural Networks for Few-Shot Learning: A Zero-Cost NAS Perspective"
title_zh: 重新审视少样本学习的神经网络：零代价NAS视角
authors: Haidong Kang
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=fNixzmprun"
tags: ["query:neural-arch"]
score: 9.0
evidence: 针对少样本学习的零代价神经网络架构搜索
tldr: 针对少样本学习中架构搜索效率低和迁移次优的问题，本文提出IBFS框架，基于信息瓶颈理论实现零训练成本的架构选择。该方法在无需任何训练的情况下为给定少样本任务选出最优网络，大幅降低搜索开销并提升任务适应性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 812, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1639, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 768, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 576, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 785, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 697, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 863, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fnixzmprun/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 862, \"height\": 300, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fnixzmprun/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1772, \"height\": 806, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnixzmprun/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1132, \"height\": 851, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnixzmprun/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1774, \"height\": 767, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fnixzmprun/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 171, \"label\": \"Table\"}]"
motivation: 现有NAS在少样本场景下需要从头搜索或借用架构，既低效又可能次优。
method: 提出信息瓶颈驱动的零代价NAS框架IBFS，无需训练即可评估和选择架构。
result: 在少样本学习基准上，选出的架构性能优于从其他任务迁移的架构，且搜索成本极低。
conclusion: 零代价NAS能有效适应新任务，为少样本学习提供高效灵活的架构选择方案。
---

## Abstract
Neural Architecture Search (NAS) has recently outperformed hand-designed networks in various artificial intelligence areas. However, previous works only target a pre-defined task. For a new task in few-shot learning (FSL) scenarios, the architecture is either searched from scratch, which is neither efficient nor flexible, or borrowed architecture from the ones obtained on other tasks, which may lead to sub-optimal. Can we select the best neural architectures without involving any training and eliminate a significant portion of the search cost for new tasks in FSL? In this work, we provide an affirmative answer by proposing a novel information bottleneck (IB) theory driven \textit{Few-shot Neural Architecture Search} (dubbed, IBFS) framework to address this issue. We first derive that the global convergence of Model-agnostic meta-learning (MAML) can be guaranteed by only considering the first-order loss landscape. Moreover, motivated by the observation that IB provides a unified view toward understanding machine learning models, we propose a novel Zero-Cost method tailored for FSL to rank and select architectures based on their \textit{expressivity} obtained by IB mechanisms. Extensive experiments show that IBFS achieves state-of-the-art performance in FSL without training, which demonstrates the effectiveness of our IBFS.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：在少样本学习（FSL）场景中，传统 Neural Architecture Search（NAS）方法存在两个根本局限：
  1. 常规 NAS 仅针对单一预定义任务，当面对新任务时，要么从头开始搜索（效率低、计算开销大），要么直接借用其他任务搜索得到的架构（可能导致次优性能）。
  2. 基于元学习的自适应 NAS（如 AutoMeta）虽能提升泛化能力，但搜索过程极其耗时（超过 100 GPU 天）。
- **整体含义**：本文旨在回答：能否在不涉及任何训练的情况下，为 FSL 新任务选择最佳神经网络架构，从而消除大部分搜索成本？作者给予肯定答案，提出 **IBFS（Information Bottleneck-driven Few-shot Neural Architecture Search）** 框架。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法
- **核心思想**：
  - 利用信息瓶颈（IB）理论，在无需训练的条件下评估架构的“表达力”（expressivity），并据此对候选架构进行排序和选择。
  - 理论前提：证明 MAML 的全局收敛只需考虑一阶损失景观（Theorem 4.1），从而将设计专用架构的问题转化为寻找合适的零代价代理指标。
- **关键技术细节**：
  1. **全局收敛性分析**：定理 4.1 指出，对于宽度足够大的网络，以足够小的学习率进行梯度下降时，损失函数满足上界 \(\ell(W^t) \le (1 - \tau \cdot \eta_0 \sigma_{\min}(\Phi))^{2t}\)，其中 \(\sigma_{\min}(\Phi)\) 是雅可比矩阵的最小奇异值，说明 MAML 的全局收敛可以通过一阶信息保证。
  2. **零代价代理指标**：基于 IB 理论，提出使用**信息熵**作为衡量架构表达力的指标。具体地，对未训练架构 \(F_i\)，通过输入数据计算其雅可比矩阵的特征值 \(\varsigma_k\)，然后构造熵：\(\text{expressivity} = -\sum_{k=1}^N p \log p \le H^* \exp(-\beta \mathbb{E}[-\log p(\varsigma_k)])\)。该指标无需任何训练，且与最终测试精度呈正相关。
  3. **搜索流程**：在搜索空间中随机采样部分架构，计算其信息熵值，选取熵值最高的架构作为最终候选。整个过程仅需一次前向传播计算熵，无梯度更新。
- **算法流程（文字描述）**：
  1. 定义搜索空间（如 DAG 图）。
  2. 采样一批候选架构（如 500 个）。
  3. 对每个架构，随机输入一批数据，计算雅可比矩阵，求特征值，计算信息熵。
  4. 按熵值降序排列，选择熵值最高的架构。
  5. 对所选架构进行常规的 FSL 训练（如使用 RFS 方法），得到最终模型。

### 3. 实验设计
- **使用的数据集**：
  - **NAS 基准测试**：NAS-Bench-201（CIFAR-10、CIFAR-100、ImageNet-16-120）。
  - **少样本学习（FSL）基准**：mini-ImageNet、tiered-ImageNet（均为 5-way 分类）。
  - **大规模图像分类**：ImageNet1k（验证零代价代理的迁移能力）。
  - **Transformer 架构**：AutoFormer 基准。
- **对比方法**：
  - **NAS 方法**：REA、BOHB、REINFORCE、DARTS、PC-DARTS、GDAS、SNAS、PC-DARTS、iDARTS、IS-DARTS、NASWOT、GradSign、ZiCo、AZ-NAS、SWAP 等。
  - **FSL 方法**：MAML、ANIL、COMLN、Meta-AdaM、GAP、MetaDiff、MetaOptNet、CTM、RFS、MAML+ALFA、Sparse-MAML、MeTAL、ClassifierBaseline、MetaQDA、MAML+SiMT 等。
  - **NAS 与 FSL 结合的方法**：AutoMeta、T-NAS++、MetaNAS、H-Meta-NAS、MetaNTK-NAS。
  - **Transformer 设计**：ViT-Ti、AutoFormer-T、TF-TAS-T、ViTAS-C、Auto-Prox。
- **评价指标**：
  - 分类准确率（Top-1、Top-5）。
  - 搜索成本（秒、GPU 天数）。
  - Kendall's Tau 相关系数（衡量代理指标与真实准确率的排序一致性）。

### 4. 资源与算力
- **主要硬件**：NVIDIA RTX 2080Ti 和 NVIDIA RTX A100 80G GPU。
- **搜索成本示例**：
  - NAS-Bench-201 搜索仅需 **3.82 秒**（单 GPU）。
  - 在 DARTS 搜索空间（ImageNet1k 目标）上仅需 **0.0042 GPU-days**（约 6 分钟）。
  - FSL 任务（mini-ImageNet）搜索成本约 **0.1 小时**（约 6 分钟）。
- **训练阶段**：使用单 GPU 运行，所有实验独立执行。

### 5. 实验数量与充分性
- **实验数量**：
  - NAS-Bench-201 上三个数据集，对比 15+ 种方法（含随机、训练免费、权重共享等），报告多次运行的平均值和标准差。
  - 在 DARTS 搜索空间（ImageNet1k）上对比 20+ 种方法。
  - 在 mini-ImageNet 和 tiered-ImageNet 上对比 16+ 种 FSL 方法，包括 1-shot 和 5-shot 设置。
  - 额外在 AutoFormer 上验证 Transformer 设计场景，对比 5 种方法。
  - 消融实验：超参数 θ 对 Kendall's Tau 的影响（图6）。
  - 可视化：搜索到的正常细胞和还原细胞结构（图7、8）。
- **充分性评价**：
  - 覆盖了多种搜索空间（NAS-Bench-201、DARTS、AutoFormer）和多种任务（分类、FSL）。
  - 对比方法类型丰富（手动设计、NAS、元学习、零代价）。
  - 结果报告了多次实验的均值和标准差，具有统计意义。
  - **客观公平**：该文明确指出与 Transformer 方法比较时仅限 CNN 方法，避免不公平比较。总体实验设计合理，结论可靠。

### 6. 论文的主要结论与发现
- **主要结论**：IBFS 在 **零训练成本** 的条件下，能够选出 FSL 友好的架构，在多个基准上达到**最优**或**第二优**的表现，同时搜索成本极低（如比 MetaNTK-NAS 快 19.2 倍，比 MetaNAS 快 1680 倍）。
- **重要发现**：
  - 信息熵作为代理指标，与真实精度之间的 Kendall's Tau 在不同训练轮次下保持稳定，且方差小（图4）。
  - MAML 的全局收敛仅需一阶信息，这为使用零代价代理提供了理论支撑。
  - 在 ImageNet1k 上，仅在小数据集（CIFAR-10）上搜索的架构能直接迁移到 Large-scale 任务，且取得更高准确率（76.7% Top-1）。

### 7. 优点（方法或实验设计上的亮点）
- **零代价搜索**：完全不需要在搜索阶段进行任何训练（甚至无需计算梯度以外的额外信息），搜索时间仅为秒级。
- **理论支撑**：基于 IB 理论，从信息论角度解释了架构表达力的评价方法，并给出了 MAML 全局收敛的理论保障。
- **强泛化能力**：在 CIFAR 上搜索的架构可直接迁移至 ImageNet 等大规模数据集，无需重新搜索。
- **实验广泛全面**：覆盖了 NAS 基准、FSL 基准、大规模分类、Transformer 设计等多个场景，对比方法全面。
- **高效与高性能兼顾**：在 mini-ImageNet 5-shot 上达到 81.52% 准确率，同时搜索成本不足 0.1 小时。

### 8. 不足与局限
- **实验覆盖的局限性**：
  - FSL 实验仅使用 Conv4 和 ResNet-12 作为基线，未测试 Transformer 作为 FSL 主干的情况（尽管在 AutoFormer 上验证了方法对 Transformer 的有效性，但 FSL 场景下未与 Transformer 对比）。
  - 跨域 FSL、varying-way/varying-shot 等更复杂场景（如 10-way 或 1-shot 之外）尚未验证。
- **潜在偏差风险**：代理指标基于雅可比矩阵的特征值，可能只适用于特定类型的搜索空间或激活函数，对于极深或极窄网络的鲁棒性未知。
- **应用限制**：论文提及未来计划部署到边缘设备，但当前方法仍需在 GPU 上运行一次前向传播以计算雅可比矩阵，若搜索空间极大，采样数量增加可能仍有一定成本。且边缘设备资源受限，需进一步压缩搜索开销。
- **对比方法的时间差异**：部分对比方法（如 MetaNAS）搜索成本为数百 GPU 天，而 IBFS 仅数十分钟，作者虽然展示了优势，但未深入分析在不同搜索策略下是否会出现反直觉情况（比如某些任务可能需要更复杂的架构筛选）。

（完）
