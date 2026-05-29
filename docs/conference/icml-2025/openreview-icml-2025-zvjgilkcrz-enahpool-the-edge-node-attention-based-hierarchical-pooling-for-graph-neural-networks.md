---
title: "ENAHPool: The Edge-Node Attention-based Hierarchical Pooling for Graph Neural Networks"
title_zh: ENAHPool：基于边-节点注意力的图神经网络分层池化
authors: "Zhehan Zhao, Lu Bai, Lixin Cui, Ming Li, Ziyu Lyu, Lixiang Xu, Yue Wang, Edwin Hancock"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=zVJGILkCRZ"
tags: ["query:neural-arch"]
score: 4.0
evidence: 基于注意力的图神经网络分层池化
tldr: 针对图神经网络中池化操作面临的节点分配模糊和信息聚合不充分问题，提出基于边-节点注意力的分层池化方法。该方法将每个节点唯一分配给一个簇，并用注意力机制对簇内节点特征和簇间边强度进行加权聚合，从而获得更富有信息量的层次表示。实验证明该设计提升了图分类等下游任务性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1681, \"height\": 769, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 846, \"height\": 164, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1644, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1425, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 820, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 809, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 851, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zvjgilkcrz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 796, \"height\": 392, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-zvjgilkcrz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1812, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zvjgilkcrz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1752, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zvjgilkcrz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 594, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zvjgilkcrz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1699, \"height\": 152, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zvjgilkcrz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1739, \"height\": 199, \"label\": \"Table\"}]"
motivation: 现有聚类池化方法节点分配模糊且边-节点信息聚合方式单一。
method: 提出边-节点注意力分层池化，通过注意力机制实现加权聚合。
result: 在图分类等任务上，该方法优于现有池化方法，表征更有效。
conclusion: 为图神经网络提供了一种新颖且有效的池化机制。
---

## Abstract
Graph Neural Networks (GNNs) have emerged as powerful tools for graph learning, and one key challenge arising in GNNs is the development of effective pooling operations for learning meaningful graph representations. In this paper, we propose a novel Edge-Node Attention-based Hierarchical Pooling (ENAHPool) operation for GNNs. Unlike existing cluster-based pooling methods that suffer from ambiguous node assignments and uniform edge-node information aggregation, ENAHPool assigns each node exclusively to a cluster and employs attention mechanisms to perform weighted aggregation of both node features within clusters and edge connectivity strengths between clusters, resulting in more informative hierarchical representations. To further enhance the model performance, we introduce a Multi-Distance Message Passing Neural Network (MD-MPNN) that utilizes edge connectivity strength information to enable direct and selective message propagation across multiple distances, effectively mitigating the over-squashing problem in classical MPNNs. Experimental results demonstrate the effectiveness of the proposed method.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与研究动机

- **研究背景**：图神经网络（GNN）在处理非欧几里得结构数据（如社交网络、分子结构）中表现出色，但如何从图中提取有意义的层级表示（graph-level任务）仍是一个关键挑战。
- **核心问题**：
  - 现有基于聚类的池化方法存在两大缺陷：① 节点分配模糊（soft assignment），导致重要节点被拆分到多个簇，而次要节点可能主导簇表示；② 对簇内节点特征和簇间边连接强度采用简单求和（uniform aggregation），忽略了节点和边的不同重要性。
  - 传统的消息传递神经网络（MPNN）存在过压缩（over-squashing）问题，即随着层数增加，远端信息被压缩到固定大小表示，限制了长距离信息捕获能力。
- **整体意义**：提出一种新的基于边-节点注意力的分层池化操作（ENAHPool），结合多距离消息传递神经网络（MD-MPNN），同时解决上述两个问题，提升图分类等下游任务的性能。

## 2. 方法论

### 2.1 ENAHPool操作（核心创新）

- **硬节点分配**：首先使用MD-MPNN生成软分配矩阵 \( S^{(l)} \)，然后通过STE算法将其转化为硬分配矩阵 \( S^{(l)}_H \)，确保每个节点唯一属于一个簇（即最大概率的簇）。
- **基于节点的注意力机制**：
  - 对每个节点计算全局重要性得分（通过一个线性变换+LeakyReLU+自注意力层）。
  - 对同一簇内的节点重要性进行softmax归一化，得到注意力系数 \( \alpha_i^{(l)} \)。
  - 用注意力系数加权求和簇内节点特征，得到新簇的特征向量 \( \vec{z}_p^{(l+1)} \)。
- **基于边的注意力机制**：
  - 对每条边计算注意力系数 \( e_{ij}^{(l)} \)，反映该边的重要性。
  - 对属于同一簇对的边注意力系数进行softmax归一化，得到权重 \( E_{ij}^{(l)} \)。
  - 用这些权重加权聚合簇间连接强度，得到粗化图的邻接矩阵 \( A^{(l+1)} \)。
  - 注意：第一层池化不使用边注意力，以避免所有边强度恒为1导致信息丢失。

### 2.2 MD-MPNN架构（辅助创新）

- **目的**：缓解MPNN的过压缩问题，并利用粗化图中的边连接强度信息。
- **方法**：
  - 计算邻接矩阵的h次幂 \( A^{(l)h} \)，表示h步随机游走的路径数。
  - 通过掩码机制提取最短距离恰好为h的节点对，得到新拓扑 \( T_h^{(l)} \)。
  - 对每个 \( h \)（0至H）分别用MPNN（如GCN）进行消息传递，然后将所有输出拼接。
  - 这样每个节点可以直接与不同最短距离的节点通信，且连接强度由路径数决定（路径越多，影响力越强）。

### 2.3 整体框架

- 输入图 \( G^{(0)} \)，经过多层ENAHPool操作，每层先由MD-MPNN生成嵌入和分配矩阵，然后执行硬分配+节点注意力+边注意力，得到粗化图。
- 最终使用读出函数（readout）得到图级表示。

## 3. 实验设计

### 3.1 数据集

- **8个基准数据集**，涵盖生化和社会领域：
  - D&D、PROTEINS、NCI1、FRANKENSTEIN（生化，有节点标签或属性）
  - IMDB-B、IMDB-M、COLLAB、REDDIT-B（社交，无标签/属性时用节点度作为标签）

### 3.2 对比方法

- **全局池化方法**：Set2Set、SortPool、SAGPool(G)、GMT
- **分层池化方法**：DiffPool、SAGPool(H)、TopKPool、ASAP、StructPool、MinCutPool、SEP-G、ABDPool

### 3.3 评价指标

- 10折交叉验证，平均准确率±标准差（10次运行）

### 3.4 超参数设置

- 网格搜索范围：
  - 池化比率：0.125, 0.25, 0.5
  - 池化层数：1, 2, 3
  - MPNN层数：3, 4, 5, 6, 7
  - MPNN骨干使用GCN

## 4. 资源与算力

- **论文未明确提及**使用的GPU型号、数量或训练时长。仅在复杂度分析中指出计算复杂度为 \( O(N^3) \)，与现有基于聚类的方法相当。

## 5. 实验数量与充分性

- **实验充分性**：
  - 在8个数据集上进行了主实验（表2），覆盖了多种图规模和类型。
  - 进行了消融实验（表4：硬分配 vs 软分配；表5：节点注意力、边注意力各组件贡献）。
  - 进行了超参数敏感性分析（图7：池化层数、池化比率；图8：MD-MPNN层数）。
  - 使用了10折交叉验证且重复10次，保证了统计可靠性。
- **客观公平性**：
  - 对比了多种SOTA方法，包括全局和分层池化。
  - 超参数通过网格搜索调优，且与baseline设置一致（MPNN骨干为GCN）。
  - 但未在更大规模数据集（如OGBN/PascalVOC-SP）上验证，泛化性可能有限。

## 6. 主要结论与发现

- ENAHPool + MD-MPNN在8个数据集中7个上达到了最优或次优结果，特别在REDDIT-B上提升显著（88.56% vs 次优85.12%）。
- 即使仅使用ENAHPool（不含MD-MPNN），性能仍优于大多数方法（表2中ENAHPool(-MD)列）。
- 消融实验证明：硬分配、节点注意力、边注意力均为有效组件，且组合效果最佳。
- 超参数分析表明：2层池化、0.25池化比率、5-6层MD-MPNN层数通常效果较好；MD-MPNN层数增加可缓解过压缩，但过多会导致过拟合。

## 7. 优点

- **创新性**：首次在聚类池化中同时引入节点注意力和边注意力，解决了均匀聚合的问题。
- **硬分配策略**：避免了模糊分配，并通过STE保留梯度。
- **MD-MPNN**：利用图最短路径信息实现多距离直接消息传递，有效缓解过压缩，且能利用边连接强度（路径数）进行选择性聚合。
- **实验全面**：在多个领域、多种图类型上验证，并做了详尽的消融和敏感性分析。
- **代码可复现**：论文对算法描述清晰，未来可复现。

## 8. 不足与局限

- **算力未报告**：未说明实验所用GPU型号和训练时间，不利于复现和公平比较。
- **计算复杂度**：\( O(N^3) \) 可能对大规模图（如百万节点）带来瓶颈，论文未讨论可扩展性。
- **未在最新图Transformer或大规模数据集（如ZINC、OGBN）上对比**：部分SOTA方法（如Graphormer、GPS）未被包含，对比范围仍有扩展空间。
- **超参数调优空间**：网格搜索范围有限，可能无法找到全局最优。
- **应用场景局限**：仅在图分类任务验证，未涉及节点分类、链接预测等任务，泛化性未知。
- **第一层池化不使用边注意力的解释**：论文称避免所有边强度变为1，但未提供理论分析或实验证明此设计的必要性。

（完）
