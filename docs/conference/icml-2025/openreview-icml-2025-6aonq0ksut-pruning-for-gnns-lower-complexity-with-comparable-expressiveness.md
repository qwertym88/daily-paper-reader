---
title: "Pruning for GNNs: Lower Complexity with Comparable Expressiveness"
title_zh: 图神经网络剪枝：低复杂度与可比的表达能力
authors: "Dun Ma, Jianguo Chen, Wenguo Yang, Suixiang Gao, Shengminjie Chen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=6AOnQ0KSUT"
tags: ["query:neural-arch"]
score: 6.0
evidence: 剪枝GNN中冗余结构以降低复杂度同时保持表达能力
tldr: 针对图神经网络（GNN）追求高表达能力导致复杂度过高的问题，本文识别出GNN中的冗余结构并加以剪枝，提出Pruned MP-GNN、K-Path GNN和K-Hop GNN三种变体。理论和实验证明，剪枝后的GNN在保持甚至提升表达能力的同时大幅降低了复杂度，在多个图任务上取得更优效率。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-6aonq0ksut/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 841, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6aonq0ksut/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 831, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6aonq0ksut/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 760, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6aonq0ksut/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1520, \"height\": 1197, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6aonq0ksut/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1347, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6aonq0ksut/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1349, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-6aonq0ksut/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1585, \"height\": 482, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1227, \"height\": 561, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1866, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1548, \"height\": 617, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 951, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 732, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 661, \"height\": 487, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1335, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1569, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 558, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1649, \"height\": 1241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1768, \"height\": 751, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1764, \"height\": 1015, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1766, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-6aonq0ksut/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1764, \"height\": 674, \"label\": \"Table\"}]"
motivation: 高表达能力的GNN往往结构复杂，本文旨在通过剪枝冗余部分降低复杂度而不损失表达能力。
method: 系统识别MP-GNN等架构中的冗余结构，提出对应的剪枝模型。
result: 剪枝后的GNN具有更低的复杂度，但在表达能力和实验性能上与原模型相当甚至更优。
conclusion: 为高效GNN设计提供了剪枝策略，平衡了表达能力和计算开销。
---

## Abstract
In recent years, the pursuit of higher expressive power in graph neural networks (GNNs) has often led to more complex aggregation mechanisms and deeper architectures. To address these issues, we have identified redundant structures in GNNs, and by pruning them, we propose Pruned MP-GNNs, K-Path GNNs, and K-Hop GNNs based on their original architectures. We show that 1) Although some structures are pruned in Pruned MP-GNNs and Pruned K-Path GNNs, their expressive power has not been compromised. 2) K-Hop MP-GNNs and their pruned architecture exhibit equivalent expressiveness on regular and strongly regular graphs. 3) The complexity of pruned K-Path GNNs and pruned K-Hop GNNs is lower than that of MP-GNNs, yet their expressive power is higher. Experimental results validate our refinements, demonstrating competitive performance across benchmark datasets with improved efficiency.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：当前图神经网络（GNN）为了提升表达能力，往往采用更复杂的聚合机制和更深的网络层数，导致计算复杂度急剧上升。同时，这些架构中存在冗余结构，不仅浪费计算资源，还可能因过度非线性导致性能退化。
- **研究动机**：系统性地识别GNN（包括标准消息传递MP-GNN、K-Path GNN和K-Hop GNN）中的冗余结构，并通过剪枝在保持甚至提升表达能力的同时显著降低复杂度。
- **整体含义**：提出三种剪枝框架（Pruned MP-GNN、Pruned K-Path GNN、Pruned K-Hop GNN），理论证明其与原框架表达能力等价（或对正则/强正则图等价），且复杂度更低。实验验证了它们在多个基准任务上的竞争性表现和效率提升。

## 2. 提出的方法论

### 2.1 核心思想
- **冗余识别**：在标准MP-GNN中，不同层重复聚合相似邻域信息（如1-WL邻居多次被聚合）；在K-Path/K-Hop框架中，早期层聚合的路径/跳数信息会在后续层被再次聚合，形成冗余。
- **剪枝策略**：
  - **Pruned MP-GNN**：第 \(k\) 层只聚合 \(2^{k-1}\)-walk邻居（而非1-hop邻居），使得感受野指数增长，减少所需层数。
  - **Pruned K-Path GNN**：当层数 \(l \le K\) 时，只聚合从 \(l\)-path到 \(K\)-path的邻居（而非从1-path到K-path），消除低层重复聚合。
  - **Pruned K-Hop GNN**：类似地，当 \(l \le K\) 时只聚合从 \(l\)-hop到 \(K\)-hop的邻居。

### 2.2 关键技术细节
- **理论工具**：利用矩阵语言（MATLANG）将表达能力问题转化为代数问题，证明剪枝框架与原框架在 \(L_1 = \{ \cdot, \top, 1, \text{diag} \}\) 语言下等价。
- **关键定理**：
  - **Theorem 4.1**：若步长序列 \(\{a_k\}\) 是可视的（viewable），则 \(a_k\)-walk消息传递框架至少与1-WL测试同等强大。
  - **Lemma 4.2**：当 \(a_k = 2^{k-1}\) 时满足可视性，且是唯一使 \(S_k = 2k-1\) 的序列，从而最大化每层感受野。
  - **Theorem 4.4**：Pruned K-Path框架与K-Path框架表达能力完全等价（ \(\forall L, \text{GI}_{L}^{PR K-P} = \text{GI}_{L}^{K-P}\) ）。
  - **Theorem 4.5**：对于正则图（时 \(K=2\)）和强正则图（任意 \(K\)），Pruned K-Hop框架与K-Hop框架表达能力等价。

### 2.3 算法流程（文字说明）
- **Pruned MP-GNN**：第 \(l\) 层，节点 \(v\) 聚合其 \(2^{l-1}\)-walk邻居的特征（可通过 \(2^{l-1}\) 次1-hop消息传递实现），然后与自身特征组合。
- **Pruned K-Path/K-Hop**：当层数 \(l \le K\) 时，仅聚合从 \(l\)-path/hop到 \(K\)-path/hop的邻居；当 \(l > K\) 时，退化为仅聚合 \(K\)-path/hop邻居。

## 3. 实验设计

### 3.1 数据集与场景
- **合成数据集**：EXP（80对非正则图）、SR25（25个强正则图）、CSL（循环图），用于验证表达能力等价性。
- **真实数据集**：
  - **TU数据库**：MUTAG、D&D、PROTEINS、PTC-MR、IMDB-B（图分类任务）。
  - **分子性质预测**：QM9（12个目标）、ZINC（分子图回归）。
  - **节点/图属性与子结构计数**：模拟任务（单源最短路径、偏心距、连通性、直径、三角形计数等）。

### 3.2 基准方法
- 对比方法包括：WL子树核、GraphSAGE、GraphSNN、GIN、K-Hop、K-Path（均为原始版本）。所有剪枝框架均以GIN作为基础编码器。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长。仅在附录G.3提供了训练时间对比（如每个epoch的秒数），例如在COLLAB数据集上，GIN(3)训练时间为1.104秒/epoch，PR GIN(1)为1.060秒/epoch。但未报告总体训练时长或硬件配置。

## 5. 实验数量与充分性

- **实验组数**：共涵盖6个合成数据集/任务（表达能力验证）、5个TU数据集、1个QM9（12目标）、1个ZINC，以及额外的节点/图属性任务和子结构计数任务。
- **消融实验**：包括不同层数（3、7、10层）和不同K值（2、3、4）的对比，以及参数数量、运行时间、聚合时间等效率比较。
- **充分性与公平性**：
  - 表达能力验证中，分别测试了KEXP、SR、CSL的准确率，并与原始框架对比，结果一致。
  - 真实数据集上报告了多次运行的平均值和标准差（如Table 2中的“±”），重复次数未明确说明。
  - 对比方法均为经典或近期代表性工作，对比设置较为公平。
  - **不足**：所有实验均使用GIN作为基础编码器，未验证在其他骨干网络（如GAT、GraphSAGE）上的剪枝效果；未在超大规模图（如ogbn-arxiv）上测试；合成数据集的多样性可能有限。

## 6. 主要结论与发现

1. **表达能力等价性**：Pruned MP-GNN与1-WL等价；Pruned K-Path与K-Path完全等价；Pruned K-Hop在正则图和强正则图上与K-Hop等价。
2. **复杂度降低**：MP-GNN的复杂度从 \(O(nL)\) 降低到 \(O(n\log L)\)；K-Path/K-Hop框架在深度较大时复杂度从 \(O(nL)\) 降低到 \(O(nL/K)\)（当 \(L \gg K\)）。
3. **性能提升**：在多数真实数据集上，剪枝框架达到了与原始框架相当或更优的准确率，且训练时间更短、参数量更少。
4. **冗余消除**：通过剪枝，GNN的搜索空间减小，更容易优化，且非线性退化问题得到缓解。

## 7. 优点

- **理论扎实**：利用MATLANG语言严格证明了剪枝前后表达能力的等价性，数学工具新颖且严谨。
- **方法通用**：提出了三种剪枝策略，覆盖了主流GNN框架（MP、K-Path、K-Hop），具有较好的可推广性。
- **实验全面**：不仅验证了表达能力，还进行了节点/图属性预测、子结构计数、分类回归等多种任务，并对比了效率指标。
- **实际效益显著**：在保持性能的同时明显降低计算开销，参数量和训练时间均减少，有利于大规模图应用。

## 8. 不足与局限

- **实验硬件未披露**：未说明使用的GPU型号、数量等，影响可重复性评估。
- **骨干网络单一**：仅使用GIN作为基础编码器，未验证在GAT、GraphSAGE等其他架构上的普适性。
- **大规模图验证缺失**：未在ogbg或大型社交网络数据集上测试，实际可扩展性存疑。
- **K-Hop在非正则图上的等价性未证明**：Theorem 4.5仅覆盖正则图和强正则图，对于一般图，Pruned K-Hop可能损失非最短路径信息，表达能力弱于原始K-Hop（文中也指出这一点）。
- **剪枝策略的自动选择**：文中手动设定剪枝参数（如 \(a_k = 2^{k-1}\)），未探讨自适应或学习剪枝率的方法。
- **实验重复次数和方差报告不完整**：部分表格仅给出平均值，部分给出标准差，但未说明重复试验的具体次数。

（完）
