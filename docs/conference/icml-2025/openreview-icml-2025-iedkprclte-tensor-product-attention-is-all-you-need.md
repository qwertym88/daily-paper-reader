---
title: Tensor Product Attention Is All You Need
title_zh: 张量积注意力：你需要的全部注意力
authors: "Yifan Zhang, Yifeng Liu, Huizhuo Yuan, Zhen Qin, Yang Yuan, Quanquan Gu, Andrew C Yao"
date: 2025-01-17
pdf: "https://openreview.net/pdf?id=IEDkPrCLtE"
tags: ["query:neural-arch"]
score: 8.0
evidence: 新型注意力机制与架构提升模型质量
tldr: 本文针对长序列推理中KV缓存占用大内存的问题，提出张量积注意力（TPA），通过张量分解紧凑表示查询、键、值，大幅缩小缓存并提升模型质量；基于TPA构建T6架构，实验证明其在多个任务上达到更优性能，为高效序列建模提供了新范式。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-iedkprclte/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 785, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iedkprclte/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1563, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iedkprclte/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1560, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iedkprclte/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1745, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iedkprclte/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1743, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iedkprclte/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1711, \"height\": 512, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1770, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1625, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1570, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1285, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 885, \"height\": 401, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1772, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1773, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1772, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1773, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1773, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1768, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1774, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iedkprclte/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1769, \"height\": 365, \"label\": \"Table\"}]"
motivation: 长序列推理中KV缓存过大，导致内存开销高。
method: 提出张量积注意力，将查询、键、值分解为低秩分量，结合RoPE，压缩缓存。
result: 在多个序列建模任务上，模型质量提升且内存效率更高。
conclusion: TPA和T6架构在长序列场景下兼顾效率与性能。
---

## Abstract
Scaling language models to handle longer input sequences typically necessitates large key-value (KV) caches, resulting in substantial memory overhead during inference. In this paper, we propose **T**ensor **P**roduct **A**ttention (TPA), a novel attention mechanism that uses tensor decompositions to represent queries, keys, and values compactly, significantly shrinking KV cache size at inference time. By factorizing these representations into contextual low-rank components (contextual factorization) and seamlessly integrating with RoPE, TPA achieves improved model quality alongside memory efficiency. Based on TPA, we introduce the **T**ensor Produc**T** A**TT**en**T**ion **T**ransformer (T6), a new model architecture for sequence modeling. Through extensive empirical evaluation of language modeling tasks, we demonstrate that T6 exceeds the performance of standard Transformer baselines including MHA, MQA, GQA, and MLA across various metrics, including perplexity and a range of renowned evaluation benchmarks. Notably, TPAs memory efficiency enables the processing of significantly longer sequences under fixed resource constraints, addressing a critical scalability challenge in modern language models.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大型语言模型（LLM）在处理长输入序列时，推理阶段需要存储巨大的键值（KV）缓存，内存开销随序列长度线性增长，严重限制了上下文窗口的最大长度。
- **整体含义**：现有方法（如MQA、GQA、MLA、稀疏注意力、KV缓存卸载等）在减少缓存的同时往往牺牲模型灵活性或引入额外延迟。论文旨在提出一种新的注意力机制，在**大幅压缩KV缓存**的同时**提升模型质量**，从而在固定资源下支持更长的序列处理。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用**张量分解**（Tensor Decomposition）对查询（Q）、键（K）、值（V）的激活进行**上下文相关的低秩因子分解**。每个token的Q、K、V被表示为若干个张量积（a ⊗ b）之和，其中a ∈ R^h（头维度），b ∈ R^{dh}（头内维度）。
- **关键技术细节**：
  - **上下文因子分解**：对于token t，Q_t = (1/R_Q) Σ_{r=1}^{R_Q} a^Q_r(x_t) ⊗ b^Q_r(x_t)，K_t和V_t类似。a和b均通过对隐藏状态x_t的线性变换得到（例如a^Q_r(x_t)=W^a_Q_r x_t）。
  - **兼容RoPE**：RoPE旋转操作可施加于b因子（b^Q、b^K）上，保持旋转后的Q、K仍然具有相对位置编码特性（定理1），且支持预旋转键缓存以加速推理。
  - **KV缓存压缩**：传统缓存大小为2 h dh，TPA仅需存储两个低秩因子矩阵，每个token缓存大小为 (R_K+R_V)(h+dh)，当R_K,R_V ≪ h时，可达到10倍以上压缩。
  - **统一已有注意机制**：当a因子为非上下文（固定）且秩等于头数h时，TPA退化为MHA；当秩为1且a为全1向量时，退化为MQA；分组共享时等价于GQA。
- **算法流程（文字说明）**：
  1. 对每个token的隐藏状态x_t，通过线性层生成A_Q, B_Q, A_K, B_K, A_V, B_V（合并所有秩维度）。
  2. 对B_Q和B_K施加RoPE（或预旋转）。
  3. 通过张量积重建Q_t, K_t, V_t（或使用优化的非显式实现以降低计算量）。
  4. 按标准多头注意力计算注意力输出（缩放点积、Softmax、加权V），最后投影输出。

### 3. 实验设计：数据集、基准、对比方法

- **数据集**：FineWeb-Edu 100B（100B训练token + 0.1B验证token）。
- **基准**：LLaMA架构（SwiGLU + RoPE）作为基础，对比以下注意力机制：
  - **MHA**（标准多头）
  - **MQA**（多查询）
  - **GQA**（分组查询，组数固定为2）
  - **MLA**（多潜在头注意力，来自DeepSeek-V2）
- **评估**：
  - **训练/验证损失和困惑度曲线**（在训练过程中记录）。
  - **下游零样本与两样本性能**：ARC-Easy、ARC-Challenge、BoolQ、HellaSwag、OBQA、PIQA、WinoGrande、MMLU、SciQ（使用lm-evaluation-harness）。
- **模型规模**：四种（Small 124M、Medium 353M、Large 773M、XL 1.5B），确保参数量与标准MHA一致（通过调整头数实现）。

### 4. 资源与算力

- 文中明确提及的硬件配置：
  - Small (124M)：4× A100 GPU
  - Medium (353M)、Large (773M)、XL (1.5B)：8× A100 GPU
- 训练设置：全球批量大小480，余弦学习率调度，预热2,000步。总训练token约49B。
- 未明确给出每轮时长或总训练时间。

### 5. 实验数量与充分性

- **实验数量**：覆盖4种模型规模、7种注意力变体（MHA、MQA、GQA、MLA、TPA、TPA-KVonly、TPA non-ctx-A）、零样本和两样本评估共9个下游任务、消融实验（不同rank、不同学习率）。还展示了训练/验证损失及困惑度曲线。
- **充分性与公平性**：
  - 所有注意力机制在相同参数量下公平比较（调整头数）。
  - 消融实验验证了不同rank（R_K,R_V）和学习率的影响。
  - 使用一致训练框架（nanoGPT）和数据。
  - **不足**：仅在单一数据集（FineWeb-Edu）上训练，未在其他多源大规模数据集上验证（如C4、Pile等），可能影响泛化性结论。

### 6. 论文的主要结论与发现

- TPA在各种规模下**持续优于或持平MHA、MQA、GQA、MLA**（在验证损失、困惑度和下游准确率上）。
- TPA可实现**KV缓存压缩5–10倍**，同时模型质量不降反升。
- TPA与RoPE**天然兼容**，可无缝替换现有架构中的MHA层。
- 变体TPA-KVonly（仅对K和V分解）在较大规模上表现最佳，说明对Q的分解并非必需。
- MLA在训练中收敛较慢且最终性能多数不及TPA。

### 7. 优点：方法或实验设计上的亮点

- **方法亮点**：
  - 提出统一的张量分解视角，将MHA、MQA、GQA纳入同一框架，清晰揭示其关系。
  - 理论上证明与RoPE兼容，实际应用简便。
  - 支持多种变体（KV-only、非上下文因子等），灵活适应不同效率/精度需求。
- **实验亮点**：
  - 在多个模型规模下进行公平对比，参数量一致。
  - 评估涵盖零样本和两样本，任务多样。
  - 提供了详细的训练曲线和消融实验。

### 8. 不足与局限

- **实验覆盖**：仅在单一数据集（FineWeb-Edu）上训练，未验证在其他预训练数据（如Pile、C4）或更大规模模型（≥7B）上的表现。模型最高仅1.5B，难以推断在业界级大模型上的效果。
- **偏差风险**：所有实验基于nanoGPT框架，可能引入实现偏差；未与文献中更高效的变体（如基于flash attention的实现）对比实际推理速度。
- **应用限制**：
  - 虽然在FLOPs分析中指出TPA可降低计算量，但未提供实际的端到端推理速度提升数据（wall-clock time）。
  - 变体TPA-KVonly在较大规模上超过全TPA，表明全分解不一定最优，最优配置需调参。
  - 对于极长上下文（如>32k token），实际内存节省效果未被直接测量。
- **消融实验深度**：未系统分析不同秩的组合（R_Q, R_K, R_V）对性能和压缩比的影响（仅给出默认值R_Q=6, R_K=R_V=2及少量变化）。

（完）
