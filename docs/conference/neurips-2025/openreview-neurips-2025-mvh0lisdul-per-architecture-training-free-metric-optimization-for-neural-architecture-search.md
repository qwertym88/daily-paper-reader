---
title: Per-Architecture Training-Free Metric Optimization for Neural Architecture Search
title_zh: 逐架构无训练度量优化用于神经架构搜索
authors: "Mingzhuo Lin, Jianping Luo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=mVh0lIsdUl"
tags: ["query:neural-arch"]
score: 9.0
evidence: 提出针对每个架构的无训练度量优化方法用于神经架构搜索
tldr: 神经架构搜索（NAS）中常用的无训练度量通常只捕获部分特征，且不同架构对度量敏感度不同。本文提出逐架构的无训练度量优化方法，为每个候选架构自适应调整度量组合，而不是使用全局固定组合。在多个搜索空间上的实验表明，该方法相比全局优化显著提高了搜索到的架构性能，同时保持了无训练的低成本优势。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1437, \"height\": 966, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1422, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 644, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1456, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1230, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1405, \"height\": 934, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1434, \"height\": 764, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1415, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1030, \"height\": 1398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1441, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1385, \"height\": 768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1440, \"height\": 763, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1439, \"height\": 390, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 754, \"height\": 2133, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 762, \"height\": 2150, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1447, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1458, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mvh0lisdul/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1448, \"height\": 324, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1308, \"height\": 1003, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1240, \"height\": 924, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1503, \"height\": 1008, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1411, \"height\": 706, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1311, \"height\": 558, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1088, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1184, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 953, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1442, \"height\": 790, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1351, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1441, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1439, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1298, \"height\": 1018, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 884, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mvh0lisdul/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1055, \"height\": 612, \"label\": \"Table\"}]"
motivation: 现有无训练度量组合忽略架构对度量敏感度的差异，限制搜索性能。
method: 逐架构优化度量权重，根据每个架构的特性自适应组合多个训练无关度量。
result: 在多个搜索空间中取得更优的架构性能，且未增加计算成本。
conclusion: 考虑架构特异性的度量优化能有效提升NAS效果。
---

## Abstract
Neural Architecture Search (NAS) aims to identify high-performance networks within a defined search space. Training-free metrics have been proposed to estimate network performance without actual training, reducing NAS deployment costs. However, individual training-free metrics often capture only partial architectural features, and their estimation capabilities are different in various tasks. Combining multiple training-free metrics has been explored to enhance scalability across tasks. Yet, these methods typically optimize global metric combinations over the entire search space, overlooking the varying sensitivities of different architectures to specific metrics, which may limit the final architectures' performance. To address these challenges, we propose the Per-Architecture Training-Free Metric Optimization NAS (PO-NAS) algorithm. This algorithm: (a) Integrates multiple training-free metrics as auxiliary scores, dynamically optimizing their combinations using limited real-time training data, without relying on benchmarks; (b) Individually optimizes metric combinations for each architecture; (c) Integrates an evolutionary algorithm that leverages efficient predictions from surrogate models, enhancing search efficiency in large search spaces. Notably, PO-NAS combines the efficiency of training-free search with the robust performance of training-based evaluations. Extensive experiments demonstrate the effectiveness of our approach. Our code has been made publicly available at https://github.com/LMZ-Zhuo/PO-NAS.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：神经架构搜索（NAS）旨在自动设计高性能网络。传统NAS需要大量训练，计算成本高。无训练度量（training-free metrics）可在无训练情况下估计网络性能，大幅降低搜索成本。然而，单个无训练度量仅捕获部分架构特征，且在不同任务上评估能力差异大。已有方法通过组合多个度量提升跨任务泛化性，但通常在整个搜索空间上优化全局度量组合，忽略了不同架构对各个度量敏感度的差异，导致最终搜索到的架构性能受限。
- **核心问题**：如何为每个候选架构自适应地优化无训练度量权重，以提升度量组合的评估能力和搜索性能，同时保持无训练的低成本优势。

## 2. 论文提出的方法论

- **核心思想**：提出逐架构的无训练度量优化方法（PO-NAS）。为每个架构单独分配一组度量权重，通过加权和作为代理评分，并利用少量真实训练数据动态调整权重，而非使用全局固定组合。结合贝叶斯优化和进化算法高效搜索。
- **关键技术细节**：
  - **架构编码器**：使用图注意力网络（GAT）提取架构图嵌入，通过节点特征掩码重建任务和度量预测任务进行预训练，无需真实性能标签。
  - **代理模型**：基于多头交叉注意力的网络，融合架构嵌入和度量嵌入，为每个架构生成个性化度量权重。引入动态门控模块和残差连接，使用对齐损失（alignment loss）、相关性损失和方向对齐损失进行训练。
  - **度量组合**：对每个架构，将多个无训练度量（如grad_norm, snip, grasp, fisher, synflow, jacob_cov）加权求和，权重视架构而异，且可正可负以捕捉正负相关性。
  - **进化算法**：提出最短操作路径交叉和邻域遍历变异，利用代理模型快速评估海量候选架构，平衡探索与利用。
- **算法流程**：初始化大量候选架构并计算无训练度量；选择少量架构进行真实训练；预训练架构编码器；在贝叶斯优化阶段，每次迭代更新代理模型，根据预测分数选择最佳架构进行真实训练；进化阶段使用代理模型预测后代分数，挑选优秀后代更新候选池。

## 3. 实验设计

- **数据集与场景**：
  - NAS-Bench-201：三个图像数据集（CIFAR-10, CIFAR-100, ImageNet-16-120）。
  - TransNAS-Bench-101：七种视觉任务（场景分类、物体检测、拼图、布局、分割、法线估计、自编码），含微搜索空间和宏搜索空间。
  - DARTS搜索空间：CIFAR-10, CIFAR-100, ImageNet的分类任务。
- **基准方法**：对比多种方法，包括随机搜索（RS）、正则化进化算法（REA）、REINFORCE、BOHB、DARTS、DrNAS、Sharply-NAS、β-DARTS、TE-NAS、NASI、GradSign、ZiCo、AZ-NAS、HNAS、RoBoT等。同时报告了无训练度量平均（Avg）和最优单度量（Best）的结果。
- **对比组**：至少包含20种以上不同算法，涵盖随机搜索、强化学习、进化、可微分搜索、无训练搜索、混合搜索等类别。

## 4. 资源与算力

- 论文明确报告了搜索成本：对于DARTS搜索空间，PO-NAS在Nvidia 1080Ti上搜索耗时约0.64 GPU天（ImageNet）或3.9 GPU小时（CIFAR-10/100）。对于NAS-Bench-201，搜索成本约3162 GPU秒（折合不到1小时）。实验中使用单块1080Ti GPU，未提及多卡或集群。
- 训练最终架构时使用了更长的训练周期（如CIFAR-10/100 600 epochs，ImageNet 250 epochs），该部分成本已包含在最终测试性能中，但不计入搜索成本。

## 5. 实验数量与充分性

- **实验数量**：在3个搜索空间、约20种不同训练任务上进行了评估。每个实验重复10次（部分基线重复50次），报告均值和标准差。此外，进行了广泛的消融研究（代理模型组件、进化算法组件、度量数量、阈值参数等），共数十组实验。
- **充分性与公平性**：实验覆盖了不同规模、不同结构的搜索空间（小规模NAS-Bench-201，中等TransNAS-Bench-101，大规模DARTS），对比方法涵盖主流baseline。消融实验系统且全面，验证了逐架构优化、编码器、进化策略等组件的必要性。实验设置（如初始架构选择、训练预算）与基线方法保持一致，结果公平。

## 6. 论文的主要结论与发现

- PO-NAS在多个基准上取得了领先或最优的性能，尤其在NAS-Bench-201的CIFAR-100和ImageNet-16-120上达到或接近最优值，在DARTS搜索空间上Top-1错误率23.9%（ImageNet）和2.52%（CIFAR-10），优于对比方法。
- 逐架构度量权重优化相比全局优化显著提升了搜索到的架构质量。
- 进化算法结合代理模型能在有限真实训练预算下高效探索大规模搜索空间。
- 预训练架构编码器通过无监督方式学习架构特征，无需真实性能标签，有效辅助代理模型。

## 7. 优点

- **创新性**：首次提出为每个架构单独优化无训练度量权重，打破了全局优化的局限。
- **效率与性能兼顾**：结合无训练度量的低成本与训练性能反馈的准确性，仅需少量真实训练即可达到甚至超越需要大量训练的方法。
- **泛化能力**：不依赖预定义的基准测试集，可适应任意新搜索空间和任务。
- **组件可解释性强**：动态门控、正负权重分解使得模型能捕捉度量对架构的正负相关性，代理模型的损失函数设计合理。
- **进化算法设计巧妙**：最短操作路径交叉和邻域变异有效探索架构空间，探索权重自适应调节平衡探索与利用。

## 8. 不足与局限

- **稳定性问题**：逐架构优化增加了代理模型的优化难度，导致在部分任务上性能波动较大（如NAS-Bench-201 CIFAR-10标准差0.22）。
- **短期训练与最终性能的差距**：论文指出存在短周期训练（10 epochs）与最终训练（600 epochs）之间的性能鸿沟，限制了搜索结果的可靠性。
- **评估覆盖有限**：实验主要集中于图像分类任务，未涉及NLP、语音等其他领域；搜索空间仅限于细胞级和链式结构，未验证在更复杂搜索空间（如Transformer NAS）上的表现。
- **度量选择依赖经验**：无训练度量集为固定六种，论文未系统研究最优度量组合在不同任务上的自动选择问题。
- **计算资源细节不足**：仅报告搜索成本，未详细说明预训练编码阶段和进化阶段的具体计算开销，也未与所有基线方法在同一硬件下完全对齐比较。

（完）
