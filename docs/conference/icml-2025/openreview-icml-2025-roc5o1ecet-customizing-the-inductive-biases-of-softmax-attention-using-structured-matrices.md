---
title: Customizing the Inductive Biases of Softmax Attention using Structured Matrices
title_zh: 使用结构化矩阵定制Softmax注意力的归纳偏置
authors: "Yilun Kuang, Noah Amsel, Sanae Lotfi, Shikai Qiu, Andres Potapczynski, Andrew Gordon Wilson"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Roc5O1ECEt"
tags: ["query:neural-arch"]
score: 7.0
evidence: 使用结构化矩阵的新型注意力评分函数
tldr: 本文针对标准softmax注意力在高维输入时信息损失和缺乏距离偏差的问题，提出了基于块张量列（BTT）和多层低秩（MLR）结构化矩阵的新型评分函数。这些函数计算高效且秩高，能更好地处理高维输入。在高维上下文回归任务中，新方法显著提升了性能。该工作为定制注意力机制的归纳偏置提供了灵活且高效的方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1706, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 850, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1565, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1568, \"height\": 764, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1034, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1057, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1775, \"height\": 1794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1776, \"height\": 1798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1773, \"height\": 1803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1774, \"height\": 1800, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1487, \"height\": 1297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1480, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1479, \"height\": 770, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1475, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-roc5o1ecet/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 857, \"height\": 420, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-roc5o1ecet/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1413, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-roc5o1ecet/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1194, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-roc5o1ecet/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1000, \"height\": 260, \"label\": \"Table\"}]"
motivation: 标准注意力评分函数在处理高维输入时信息损失严重。
method: 提出基于BTT和MLR矩阵的新评分函数，具有高秩和高效计算。
result: 在高维上下文回归任务中表现出更优性能。
conclusion: 提供了一种灵活定制注意力机制的方法。
---

## Abstract
The core component of attention is the scoring function, which transforms the inputs into low-dimensional queries and keys and takes the dot product of each pair. While the low-dimensional projection improves efficiency, it causes information loss for certain tasks that have intrinsically high-dimensional inputs. Additionally, attention uses the same scoring function for all input pairs, without imposing a distance-dependent compute bias for neighboring tokens in the sequence. In this work, we address these shortcomings by proposing new scoring functions based on computationally efficient structured matrices with high ranks, including Block Tensor-Train (BTT) and Multi-Level Low Rank (MLR) matrices. On in-context regression tasks with high-dimensional inputs, our proposed scoring functions outperform standard attention for any fixed compute budget. On language modeling, a task that exhibits locality patterns, our MLR-based attention method achieves improved scaling laws compared to both standard attention and variants of sliding window attention.
Additionally, we show that both BTT and MLR fall under a broader family of efficient structured matrices capable of encoding either full-rank or distance-dependent compute biases, thereby addressing significant shortcomings of standard attention.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的中文总结：

# 论文总结：使用结构化矩阵定制Softmax注意力的归纳偏置

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：标准Softmax注意力机制存在两个关键局限：
    1. **低秩瓶颈**：评分函数将输入映射为低维查询和键，导致在高维输入任务中信息丢失严重，表达能力受限。
    2. **缺乏距离依赖计算偏置**：所有位置对使用相同的评分函数，未利用数据中的局部性（locality）结构，导致长序列计算浪费且难以高效利用局部依赖。
- **整体含义**：本文旨在通过引入结构化矩阵（如块张量列BTT和多层低秩MLR），定制注意力机制的归纳偏置，使其更适配特定任务，同时保持计算效率。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将标准注意力中的低秩评分矩阵 \(W_Q W_K^\top\) 替换为高效结构化矩阵（BTT或MLR），从而在不增加过多计算开销的情况下提高秩或引入结构先验。
- **关键技术细节**：
    - **BTT（块张量列）评分函数**：\(s_{\text{BTT}}(x_j, x_{j'}) = x_j^\top \left( P_L \bigoplus_{k'=1}^b L_{k'} P_R \bigoplus_{k=1}^c R_k^\top \right) x_{j'}\)，其中 \(P_L,P_R\) 为固定置换矩阵，\(L_{k'},R_k\) 为低秩因子。BTT矩阵具有高秩，参数复杂度为 \(O(D^{3/2})\)（当 \(a=b=c=d=\sqrt{D}\))。
    - **MLR（多层低秩）评分函数**：\(s_{\text{MLR}}(x_j, x_{j'}) = x_j^\top \left( \sum_{l=1}^L \bigoplus_{k=1}^{p_l} L_{l,k} R_{l,k}^\top \right) x_{j'}\)，其中每层低秩分块对角矩阵对应不同尺度（如局部、全局交互）。通过设置 \(p_l=2^{l-1}\) 实现层次化结构。
    - **距离依赖计算偏置的编码**：通过MLR矩阵的分层结构，使得近距离的token对使用更多计算资源（高秩），远距离使用较少资源（低秩），从而在保持全局视野的同时优先处理局部交互。在自回归生成中还能减少KV缓存大小。
    - **MLBTC统一框架**：作者提出Multi-Level Block Tensor Contraction (MLBTC) 通用类，涵盖了BTT、MLR、Monarch、Butterfly、Kronecker等矩阵，为未来探索提供统一视角。
    - **实践考虑**：采用最优张量缩并顺序（如式(32)）实现高效计算；使用最大更新参数化（μP）进行稳定特征学习，并适配结构化矩阵的初始化和学习率。

## 3. 实验设计：使用的数据集/场景、基准与对比方法

- **场景一：高维上下文回归（In-Context Linear Regression）**
    - **数据集**：合成数据，输入维度 \(d_{\text{input}} \in \{16,32,64,128\}\)，序列长度 \(N=2 d_{\text{input}}\)，每个prompt采样不同的线性函数 \(f(x)=w^\top x\)。
    - **基准**：标准多头注意力（1头、8头）。
    - **对比方法**：Bilinearn BTT（8头）、Bilinearn MLR（8头）。
    - **评价指标**：平方误差（Squared Error），控制计算量（FLOPs）或模型宽度。

- **场景二：语言建模**
    - **数据集**：OpenWebText（字符级分词），序列长度 \(T=1024\)。
    - **基准**：标准多头注意力。
    - **对比方法**：滑动窗口注意力（SWA）、全局+滑动窗口混合（Global+SWA）、MLR注意力（8层，秩分配 32|8|6|4|4|4|4|2）。
    - **模型架构**：6层Transformer，宽度 \(D \in \{256,384,512,768\}\)，头维度 \(r=64\)，优化器AdamW。
    - **评价指标**：验证损失（Validation Loss），控制非嵌入计算量。

- **场景三：时间序列预测**
    - **数据集**：ETTh1（电力变压器温度数据），预测时间范围 \(\{96,192,336\}\) 小时。
    - **基准**：标准注意力Transformer（2层编码器，\(D=512\)，8头）。
    - **对比方法**：MLR注意力（2层和4层变体）。
    - **评价指标**：平均绝对误差（MAE）的相对改善。

- **额外实验**：在Chronos（基础时间序列模型）中替换注意力，验证计算成本减少；μP学习率迁移验证（图5）。

## 4. 资源与算力

- 论文中**未明确说明**所使用的具体GPU型号、数量或总训练时长。
- 仅在In-Context Regression实验中提到训练了500,000步（见图12壁钟时间约140-190分钟），但未说明硬件。
- 语言建模实验提及“训练6层Transformer”且“batch size为4”，但未提供显式算力明细。
- 因此，无法精确量化算力投入。

## 5. 实验数量与充分性

- **实验数量**：共涵盖4个主要场景（回归、语言建模、时间序列、Chronos基础模型），每个场景包含不同模型宽度、输入维度或对比方法。例如：
    - 回归实验：4种输入维度 × 6种模型宽度 × 3种打分函数（标准1头、8头、BTT）及部分MLR，总计大量组合。
    - 语言建模：4种宽度 × 4种注意力变体（标准、SWA、Global+SWA、MLR）。
    - 时间序列：2种MLR结构 × 3种时间范围。
    - 消融实验：μP学习率稳定性、不同张量缩并顺序分析、壁钟时间对比等。
- **充分性与公平性**：
    - 实验设计较为全面：对比了标准注意力、滑动窗口、混合结构，并控制计算量（FLOPs）与模型宽度。
    - 采用μP确保超参数迁移公平；实现细节（层归一化、初始化）均有说明。
    - 但也存在局限：时间序列部分仅用单数据集ETTh1，且语言建模使用字符级分词而非子词，可能影响通用性。

## 6. 论文的主要结论与发现

- **结论一**：Bilinearn BTT和MLR评分函数在高维上下文回归任务中显著优于标准多头注意力，且在全计算量/模型宽度范围内保持优势，证明克服低秩瓶颈的有效性。
- **结论二**：MLR注意力在语言建模中实现比标准注意力和SWA更好的缩放定律，即在相同计算量下获得更低验证损失。
- **结论三**：MLR注意力在时间序列预测中随序列长度增长逐渐优于标准注意力，尤其在长范围预测时改善更明显。
- **结论四**：BTT和MLR均可统一于MLBTC框架，为设计高效结构化注意力提供统一视角。

## 7. 优点

- **方法创新**：首次将BTT和MLR（高秩结构化矩阵）引入注意力评分函数，同时解决低秩瓶颈和缺乏局部偏置两个问题。
- **理论清晰**：揭示标准化力与结构化矩阵的关系，并通过MLBTC统一多种已有结构。
- **实验扎实**：多个场景、多种宽度/维度、消融实验，且采用μP确保公平比较。
- **实际可用**：方法兼容GQA、RoPE等常见技术，且在语言建模中展示更好的缩放定律（实际部署潜力大）。
- **高效性**：MLR注意力在保存视觉的前提下减少计算量和KV缓存。

## 8. 不足与局限

- **实验覆盖不足**：时间序列仅测试单数据集ETTh1；语言建模使用字符级分词（较少见），可能无法直接类比普遍的子词分词实验。
- **算力信息缺失**：未提供详细GPU型号、数量、训练时长，影响可复现性及效率评估。
- **应用局限**：作者指出对科学数据、PDE等高维输入可能有更大价值，但当前仅验证了合成回归任务；语言任务中标准注意力本身未受低秩瓶颈影响，MLR带来的收益可能主要来自局部偏置，而非秩提升。
- **实现优化**：当前壁钟时间比标准注意力慢（1.35x），作者认为可通过优化批量矩阵乘积提升，但未展示优化后结果。
- **探索范围**：仅尝试了MLR和BTT两种结构化矩阵，未深入评估MLBTC类中的其他结构（如Monarch、Butterfly）在注意力上的表现。

（完）
