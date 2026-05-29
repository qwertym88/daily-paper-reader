---
title: Hardware-aligned Hierarchical Sparse Attention for Efficient Long-term Memory Access
title_zh: 面向高效长程记忆的硬件对齐层次稀疏注意力
authors: "Xiang Hu, Jiaqi Leng, Jun Zhao, Kewei Tu, Wei Wu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dIHSZTx9Lu"
tags: ["query:neural-arch"]
score: 7.0
evidence: 新颖的层次稀疏注意力机制实现高效长程记忆
tldr: 本文针对RNN无法随机访问长程历史的问题，提出层次稀疏注意力（HSA），将输入分块并选取top-k块进行层次化聚合，在学习可跳过令牌后实现高效长程访问。HSA保持了RNN的线性复杂度，同时赋予其灵活的长程记忆能力，是一种创新的注意力机制架构改进。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 695, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1311, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 574, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1405, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1153, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 713, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 711, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dihsztx9lu/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1150, \"height\": 387, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1296, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 308, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 793, \"height\": 299, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1446, \"height\": 132, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 698, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 697, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dihsztx9lu/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1563, \"height\": 421, \"label\": \"Table\"}]"
motivation: RNN线性复杂度但无法随机访问历史，简单添加注意力会破坏效率。
method: 将输入分块，选取top-k块并层次化聚合，学习可跳过的令牌。
result: HSA在长序列任务上达到与注意力相当的性能，但计算复杂度更低，长度泛化更好。
conclusion: 为RNN引入高效的长程随机访问能力，拓展了注意力机制的设计空间。
---

## Abstract
A key advantage of Recurrent Neural Networks (RNNs) over Transformers is their linear computational and space complexity enables faster training and inference for long sequences. However, RNNs are fundamentally unable to randomly access historical context, and simply integrating attention mechanisms may undermine their efficiency advantages.
To overcome this limitation, we propose \textbf{H}ierarchical \textbf{S}parse \textbf{A}ttention (HSA), a novel attention mechanism that enhances RNNs with long-range random access flexibility while preserving their merits in efficiency and length generalization. HSA divides inputs into chunks, selecting the top-$k$ chunks and hierarchically aggregates information.
The core innovation lies in learning token-to-chunk relevance based on fine-grained token-level information inside each chunk. This approach enhances the precision of chunk selection across both in-domain and out-of-domain context lengths.
To make HSA efficient, we further introduce a hardware-aligned kernel design.
By combining HSA with Mamba, we introduce RAMba, which achieves perfect accuracy in passkey retrieval across 64 million contexts despite pre-training on only 4K-length contexts, and significant improvements on various downstream tasks, with nearly constant memory footprint. These results show RAMba's huge potential in long-context modeling.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：递归神经网络（RNN）具有线性计算和空间复杂度，在长序列训练和推理上比 Transformer 更高效。然而，RNN 本质上是将可变长度上下文压缩为固定维度的隐状态，**缺乏对历史信息的随机访问能力**，因此在需要精确召回长距离信息（如 passkey retrieval）的任务中性能严重下降。
- **现有方案局限**：简单地给 RNN 加上注意力机制虽能缓解随机访问问题，但会引入平方复杂度、差的外推能力和大的 KV cache 内存开销，从而破坏 RNN 的效率优势。因此，此前缺乏一种同时具备**长度泛化、随机访问灵活性和高效率**的 RNN 方案。
- **整体含义**：本文提出**层次稀疏注意力（HSA）**，并将其集成到 Mamba 中得到 **RAMba**，在保持 RNN 线性效率和长度泛化的同时，赋予 RNN 强大的长程随机访问能力，为构建具有永久记忆的语言模型提供了新基础。

## 2. 论文提出的方法论

### 2.1 核心思想
- 受心理学中工作记忆和长时记忆的启发：用 Mamba 模拟工作记忆（压缩上下文为有限隐状态），用 HSA 模拟长时记忆（可扩展的 KV cache，通过分块稀疏检索实现高效随机访问）。
- **HSA 的关键创新**：**两阶段层次注意力机制**——先对每个 chunk 内部 token 做注意力（获取 chunk 级信息），再对选出的 top‑k 个 chunk 做加权求和（融合 chunk 级信息）。这实现了端到端的 token‑to‑chunk 相关性学习，使 chunk 选择更精准，尤其在外推长上下文时优势明显。

### 2.2 关键技术细节
1. **分块与 Chunk 编码**：
   - 输入序列按固定大小 S（如 64）划分为多个 chunk。
   - 通过一个 Transformer 双向编码器对每个 chunk 独立编码，得到 chunk memory。
2. **Chunk 选择**：
   - 对每个 token，计算其与各 chunk 编码（mean‑pooling）的点积相似度，选取 top‑K 个 chunk。
   - 查询分组（GQA），每组独立选择 K 个 chunk。
3. **层次注意力**：
   - **第一阶段**：对每个选中的 chunk，token 的 query 与该 chunk 内所有 key 做 softmax 注意力，得到 chunk 内部信息（token‑level attention）。
   - **第二阶段**：用 stick‑breaking 方法（基于距离的递减权重）计算各 chunk 的权重，加权融合第一阶段的输出。
4. **硬件对齐的核设计**：
   - 基于 Triton 实现自定义 kernel，每个 GPU 线程加载单个 token 的 query 和对应 chunk 的 KV，并行计算。支持高效前向和反向传播。
5. **推理优化**：
   - 将 token‑level KV cache 卸载到 CPU，GPU 只保留紧凑的 chunk 级表示。每个时间步只加载选中 chunk 的 KV cache，内存占用接近常数。
   - 所有 HSA 层共享同一个 chunk 选择结果，减少 CPU‑GPU 交换开销。

### 2.3 公式/算法流程（文字说明）
- 分块：序列 → chunk i (长度 S)，编码 → E_i。
- 对 token t：Q_slc_t = W_slc_Q * norm(H_t)；K_slc_i = W_slc_K * mean(E_i)。
- 每组计算相似度 s_{t,i} = (Q_slc_t^T K_slc_i)/√d_g，取 top‑K。
- 对每个选中 chunk：softmax(Q_t * K_chunk^T) * V_chunk → O_{t,k}。
- 计算 stick‑breaking 权重 w_{t,k} = σ(s_{t,k}) * Π_{i<k}(1‑σ(s_{t,i}))。
- 最终输出：O_t = Σ_k w_{t,k} * O_{t,k}。

## 3. 实验设计

### 3.1 数据集/场景
- **长程语言建模**：PG19（书籍）、ArXiv‑math、Code（代码）。
- **下游任务**：
  - Passkey Retrieval（在长文本中插入随机 token 作为密码），长度从 4K 到 64M。
  - RULER 子任务：Single NIAH (S‑N)、Multi‑queries NIAH (MQ‑N)、Variable Tracking (VT)、Frequent Words Extraction (FWE)。
  - LongBench V2（零样本长文本理解）。
  - 摘要（XSUM、CNN）和 QA（SQuaD、HotpotQA、QuALITY）。
- **外推测试**：模型仅在 **4K 上下文**上预训练，然后在 16K、64K、甚至 64M 上评估。

### 3.2 Benchmark 与方法
- **基线模型**：
  - Transformer（全注意力 + YaRN 位置编码）。
  - Mamba‑2（纯 RNN）。
  - Mamba + 滑动窗口注意力（SWA，窗口 512，分别用 ALiBi 和 RoPE）。
  - Mamba + Native Sparse Attention（NSA）。
- **本文方法**：RAMba（HSA + Mamba），包含带 memory reset 和不带 memory reset 的变体。

### 3.3 实验设置
- 模型规模：主要 370M 参数（从零预训练），2.7B 参数（额外验证）。
- 预训练数据：Pile 数据集的 60B tokens 子集。
- 训练超参数：4K 上下文，AdamW，峰值 lr 2e‑3，余弦衰减。
- 消融组件：memory reset（记忆重置）、stick‑breaking 权重、chunk encoder 等。

## 4. 资源与算力

- **硬件**：16 个 **PPU**（文中说明每个 PPU 约相当于 A100 GPU 计算能力的一半）。
- **训练时间**：
  - 370M 模型预训练 60B tokens 约 60 小时。
  - 2.7B 模型后训练（含 warmup 和 LoRA 微调）总计约 72 小时（32 PPUs）。
- **推理效率分析**：在 4K–64K 长度上比较 FlashAttention‑2、NSA、HSA 的运行时和内存占用；HSA 比 NSA 快约 3×，比全注意力快 5–25×。

## 5. 实验数量与充分性

- **实验组数**：涵盖 3 个长程语言建模 PPL、5 个下游任务/benchmark（passkey retrieval、RULER 4 子任务、LongBench V2、5 个 SFT 任务），以及多组消融实验（memory reset、stick‑breaking、chunk encoder）和不同模型规模（370M、2.7B）。
- **充分性与客观性**：
  - 基线对比全面，覆盖纯 RNN、混合注意力、稀疏注意力等主流方案。
  - 外推测试长度远超预训练长度（最大 64M），挑战性足够。
  - 统计方式采用多次评估（如 PPL 取单次结果，但多个数据集验证趋势），整体较为客观。
  - 但未提供误差棒或置信区间；论文指出由于只有一个 checkpoint，无法评估统计显著性，但仍通过多任务交叉验证结论稳健性。

## 6. 论文的主要结论与发现

1. **HSA 实现高效精确的 chunk 选择**：在 passkey retrieval 中，RAMba 达到 **64M 上下文的完美准确率**（预训练仅 4K），而基线在 64K 时基本失效。
2. **长度泛化能力强**：在 16K/64K 的 PPL 上，RAMba 普遍优于 Mamba 和 Mamba+SWA/NSA；RULER 任务中可外推 **256×** 预训练长度。
3. **Memory reset 有助于长度外推**：在超过 4K 时，带 memory reset 的变体性能更稳定，防止 RNN 隐状态为注意力提供学习捷径。
4. **与现有稀疏注意力（NSA）相比**：HSA 的 chunk 选择更准确（基于层级反馈而非未归一化的注意力近似），且因共享选择而计算更快。
5. **接近常数的推理内存**：通过 CPU 卸载和分组共享，RAMba 的 GPU 内存占用几乎不随序列长度增长。

## 7. 优点

- **方法新颖**：首次提出**端到端学习的 token‑to‑chunk 相关性**，而非用未归一化得分近似，显著提升 chunk 准确度。
- **硬件高效**：Triton 自定义 kernel，利用 GPU 并行，保持接近 Mamba 的训练吞吐率。
- **强长度泛化**：在未见到长序列的情况下，仍能完美检索 64M 上下文中的密钥，外推能力出色。
- **推理内存可控**：CPU 卸载设计使长序列推理成为实际可能。
- **统一的架构**：HSA 原则上可适用于各种 RNN 骨干，论文以 Mamba 为例展示了通用性。

## 8. 不足与局限

- **实验仅限 Mamba 骨干**：虽声称通用，但未在 RWKV、xLSTM 等其他 RNN 上验证。
- **模型规模不大**：主要实验在 370M 规模，2.7B 实验较少（且使用了后训练而非完全从零预训练），未测试 3B+ 的参数规模。
- **额外参数开销**：HSA 需要 Transformer 编码器（约占 5.4% 参数），在公平性对比中需注意。
- **模板敏感性**：Passkey retrieval 和 Single NIAH 任务表现差异大，说明模型对输入格式敏感，实际泛化可能受限于模式简单性。
- **缺乏统计误差分析**：仅报告单次结果，未提供复现性验证；对随机种子等因素的影响未讨论。
- **长上下文复杂性**：在超过 1M 长度的复杂检索任务（如多查询 NIAH）中性能下降明显，精准 chunk 选择仍为开放挑战。
- **推理时 CPU‑GPU 交换开销**：虽被论证可接受，但在极低延迟场景下可能仍是瓶颈。

（完）
