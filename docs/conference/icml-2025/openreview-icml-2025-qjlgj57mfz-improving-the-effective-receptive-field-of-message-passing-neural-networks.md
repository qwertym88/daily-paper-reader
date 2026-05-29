---
title: Improving the Effective Receptive Field of Message-Passing Neural Networks
title_zh: 改进消息传递神经网络的有效感受野
authors: "Shahaf E. Finder, Ron Shapira Weber, Moshe Eliasof, Oren Freifeld, Eran Treister"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=QJLGj57MfZ"
tags: ["query:neural-arch"]
score: 7.0
evidence: 改进有效感受野的新型MPNN架构
tldr: 针对消息传递神经网络（MPNN）有效感受野受限的问题，本文提出交错多尺度消息传递神经网络（IM-MPNN），通过多尺度信息融合缓解过压缩现象，显著提升长程依赖捕获能力。实验证明该方法在图任务上优于基线。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 824, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1549, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 798, \"height\": 106, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 750, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 767, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 744, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1557, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-qjlgj57mfz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1642, \"height\": 263, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 712, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1398, \"height\": 1051, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1127, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1391, \"height\": 1776, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 834, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 738, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 608, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-qjlgj57mfz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 438, \"height\": 321, \"label\": \"Table\"}]"
motivation: MPNN的有效感受野受限，影响长程依赖建模。
method: 提出IM-MPNN架构，交错多尺度消息传递以扩大有效感受野。
result: 在图任务上有效提升性能，缓解过压缩问题。
conclusion: IM-MPNN为改善MPNN感受野提供有效方案。
---

## Abstract
Message-Passing Neural Networks (MPNNs) have become a cornerstone for processing and analyzing graph-structured data. However, their effectiveness is often hindered by phenomena such as over-squashing, where long-range dependencies or interactions are inadequately captured and expressed in the MPNN output. This limitation mirrors the challenges of the Effective Receptive Field (ERF) in Convolutional Neural Networks (CNNs), where the theoretical receptive field is underutilized in practice. In this work, we show and theoretically explain the limited ERF problem in MPNNs. Furthermore, inspired by recent advances in ERF augmentation for CNNs, we propose an Interleaved Multiscale Message-Passing Neural Networks (IM-MPNN) architecture to address these problems in MPNNs. Our method incorporates a hierarchical coarsening of the graph, enabling message-passing across multiscale representations and facilitating long-range interactions without excessive depth or parameterization. Through extensive evaluations on benchmarks such as the Long-Range Graph Benchmark (LRGB), we demonstrate substantial improvements over baseline MPNNs in capturing long-range dependencies while maintaining computational efficiency.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：消息传递神经网络（MPNN）在处理图结构数据时，常因“过压缩”（over-squashing）现象而难以有效捕获长程依赖关系。这与卷积神经网络（CNN）中“有效感受野（ERF）”小于理论感受野的问题类似——深层的MPNN中，远处节点对中心节点的贡献呈指数级衰减。
- **研究动机**：受CNN中通过增大卷积核或使用多尺度特征图扩展ERF的启发，作者希望将类似思想引入MPNN，在不显著增加深度和参数量的前提下，提升模型对长程信息的捕获能力。
- **整体含义**：提出一种通用的多尺度消息传递架构IM-MPNN，可插拔至多种现有MPNN骨干，在保持线性计算复杂度的同时显著改善ERF，从而缓解过压缩。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过对输入图进行层次化粗化（coarsening），构建多个不同分辨率（尺度）的图表示；在每个尺度上独立执行消息传递，并通过“尺度混合”（scale-mix）操作在相邻尺度间交换信息，从而在不增加深度的情况下扩大有效感受野。
- **关键技术细节**：
  1. **多尺度构建**：使用Graclus算法对原始图G⁰反复进行二节点配对池化（每步节点数约减半），得到S个尺度图{G⁰, G¹, …, Gˢ}。池化时取两个子节点的特征均值作为父节点特征，并更新邻接矩阵。
  2. **消息传递骨干**：每个尺度使用相同的MPNN协议（如GCN、GINE、GatedGCN），但各有独立权重。更新公式为：`x̃^{(s,ℓ)} = MPNN^{(s,ℓ)}(x^{(s,ℓ)}, Aˢ)`。
  3. **尺度混合**：对相邻尺度间的父子节点进行信息融合。例如，尺度s的节点q（由尺度s-1的节点i,j合并而成）同时接收来自子节点(i,j)的聚合信息（低到高）和来自父节点p（尺度s+1）的信息（高到低），通过可学习的线性变换相加：`x^{(s,ℓ+1)}_q = x̃^{(s,ℓ)}_q + W^{(s,ℓ)}_{l2h}·(x̃^{(s-1,ℓ)}_i + x̃^{(s-1,ℓ)}_j)/2 + W^{(s,ℓ)}_{h2l}·x̃^{(s+1,ℓ)}_p`。
  4. **上池化与拼接**：最后将各尺度的特征通过UNPOOL逐层恢复至原始图分辨率，并沿通道维度拼接，送入任务头（分类/回归）。
- **复杂度**：所有尺度上的MPNN总复杂度为O(|V|+|E|)，尺度混合为O(|V|)，整体仍为线性。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - **长程图基准（LRGB）**：PascalVOC-SP、COCO-SP、Peptides-func、Peptides-struct。前两者为超像素节点分类，后两者为多标签图分类/回归。
  - **图传输任务**（Di Giovanni等人提出）：三种图结构（ring, crossed-ring, cliquepath），评价网络在不同距离k下转移源节点标签到目标节点的准确率。
  - **城市网络（City-Networks）**：四个真实城市道路图（巴黎、上海、洛杉矶、伦敦），节点数10万-57万，直径>100，衡量远程通信能力。
  - **异质性节点分类**（Platonov等人提出）：Roman-empire、Amazon-ratings、Minesweeper、Tolokers、Questions，覆盖弱同质性、大数据集。
- **基准方法**：对比了多种MPNN（GCN、GINE、GatedGCN、GAT、GAT-sep、CO-GNN等）、图Transformer（Exphormer、GPS、GOAT等）、异质性专门GNN（FSGNN、GBK-GNN、JacobiConv等）以及高阶扩散/重连方法（DRew、Graph U-Net）。所有比较均保证参数预算约500K。
- **评价指标**：分类任务用Accuracy或F1，回归任务用MAE/AUC。

### 4. 资源与算力

- **文中明确信息**：运行时测量使用**Nvidia RTX A6000 GPU**。给出了每epoch训练/推理时间（如PascalVOC-SP上GCN为8.00s/epoch，IM-GCN 4尺度为21.86s/epoch）。但未说明总训练epoch数、多卡并行设置或总GPU耗时。整体上，IM-MPNN的额外开销可接受（约2-3倍基线，与尺度数成正比）。

### 5. 实验数量与充分性

- **实验数量**：共计在**5大类任务、约20个不同数据集/场景**上进行了实验。此外包含：
  - 消融实验：改变尺度数（S=1~4）对性能影响（表1、2、3）。
  - 不同MPNN骨干的扩展（GCN、GINE、GatedGCN、GAT、CO-GNN等）。
  - 在异质性数据集上与其他14种方法对比（表4、表6）。
  - 图传输任务中对比GCN与IM-GCN在不同距离下的行为（图7）。
- **充分性与客观性**：
  - 所有对比均控制参数量在500K左右（通过调整通道数），确保公平。
  - 使用官方划分和多次随机种子（3~5次），报告均值±标准差。
  - 在长程图基准上与改进后的Tönshoff等人设置对齐，避免评估漏洞。
  - 论文也提供了与Graph U-Net和DRew的额外对比（表9）。
- **结论**：实验设计较为充分，覆盖了多种图特性（同质/异质、小/大直径、小/大图），且与主流方法直接对比，说服力强。

### 6. 论文的主要结论与发现

- IM-MPNN能**有效扩大MPNN的有效感受野**：图传输任务中，在长距离下（如cliquepath k~37）仍保持100%准确率，而普通GCN在k≈7即失败。
- 在**长程图基准**上，IM-MPNN取得显著提升：PascalVOC-SP F1从0.2078提升至0.2929（+41%），COCO-SP从0.1338提升至0.1960（+46%）。
- 在**城市网络**大规模图上，IM-GCN比GCN准确率提高10%~16.5%。
- 在**异质性节点分类**中，IM-MPNN（尤其是IM-GatedGCN和IM-CO-GNN）达到或超过当前最优图Transformer和异质性专门模型，且保持线性复杂度。
- 多尺度数量增加通常带来性能提升，但超过某个点后收益递减（如S=4时部分任务性能稳定甚至略降）。

### 7. 优点（方法或实验设计上的亮点）

1. **通用性**：IM-MPNN可即插即用于任意MPNN骨干（GCN、GINE、GatedGCN、GAT、CO-GNN等），无需改动核心更新规则。
2. **保复杂度**：所有操作保持O(|V|+|E|)，与标准MPNN同级，适合大规模图。
3. **理论动机清晰**：从线性图分析（帕斯卡三角）和连续扩散方程（PDE）两个角度严格论证了ERF指数衰减，并说明粗化可放大扩散系数κ从而扩展ERF。
4. **全面实验评估**：覆盖多种任务类型（节点分类、图分类、回归、传输）、多种图特性（同质、异质、超大直径），且与大量先进方法对比，结果具有说服力。
5. **代码开源**：提供GitHub仓库，便于复现和扩展。

### 8. 不足与局限

1. **实验覆盖仍有限**：缺少对极端大图（如千万节点）的测试；虽然在City-Networks上测试了最大57万节点，但可比方法较少。另外未在分子/蛋白质等典型GNN基准（如ZINC、OGBG）上测试。
2. **可解释性不足**：虽理论分析ERF，但未直接可视化或量化IM-MPNN在各尺度上的实际感受野分布（仅在图1展示了GCN和IM-GCN的贡献热力图，但缺乏与理论的定量对照）。
3. **尺度选择依赖经验**：最佳尺度数需根据图直径、同质性等特征手动调节（文中附录B给出了启发式规则，但缺乏自动选择机制）。
4. **未考虑图动态变化**：池化与上池化基于固定配对（Graclus），不适用于动态图或需要保留精细边结构的任务。
5. **计算开销虽线性但实际倍数**：如使用4个尺度，每epoch时间约为基线3倍（表7），在极大规模图上可能仍显昂贵。
6. **异质性数据集对比中**：部分较新的方法（如Graph Mamba）未包含对比，结果并非全面领先所有方法（如IM-GCN在Roman-empire上低于CO-GNN基线）。

（完）
