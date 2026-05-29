---
title: "LV-XAttn: Distributed Cross-Attention for Long Visual Inputs in Multimodal Large Language Models"
title_zh: LV-XAttn：多模态大语言模型中长视觉输入的分布式交叉注意力
authors: "Tzu-Tao Chang, Shivaram Venkataraman"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=kuIwMEHXMT"
tags: ["query:neural-arch"]
score: 6.0
evidence: 面向长视觉输入的高效分布式交叉注意力
tldr: 多模态大模型在处理长视觉输入时，交叉注意力层内存需求高且分布式通信开销大。本文提出LV-XAttn，一种低通信开销的精确分布式交叉注意力机制。通过优化通信模式，该方法显著降低了训练和推理时的瓶颈。实验表明LV-XAttn在视频理解等长输入场景中效率大幅提升。该工作有助于实现高效的神经网络结构优化。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-kuiwmehxmt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 770, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kuiwmehxmt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 842, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kuiwmehxmt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1766, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kuiwmehxmt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 688, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kuiwmehxmt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 353, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kuiwmehxmt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 833, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-kuiwmehxmt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 968, \"height\": 785, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-kuiwmehxmt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kuiwmehxmt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 739, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kuiwmehxmt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1771, \"height\": 895, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kuiwmehxmt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1649, \"height\": 896, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kuiwmehxmt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-kuiwmehxmt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 850, \"height\": 502, \"label\": \"Table\"}]"
motivation: 长视觉输入下交叉注意力层内存和通信开销大。
method: 提出LV-XAttn，实现低通信开销的精确分布式交叉注意力。
result: 实验证明通信开销大幅降低，训练和推理更高效。
conclusion: LV-XAttn有效解决了长视觉输入下的效率瓶颈。
---

## Abstract
Cross-attention is commonly adopted in multimodal large language models (MLLMs) for integrating visual information into the language backbone. However, in applications with large visual inputs, such as video understanding, processing a large number of visual tokens in cross-attention layers leads to high memory demands and often necessitates distributed computation across multiple GPUs. Existing distributed attention mechanisms face significant communication overheads, making cross-attention layers a critical bottleneck for efficient training and inference of MLLMs. To address this, we propose LV-XAttn, a distributed, exact cross-attention mechanism with minimal communication overhead. We observe that in applications involving large visual inputs, the size of the query block is typically much smaller than that of the key-value blocks.  Thus, in LV-XAttn we keep the large key-value blocks locally on each GPU and exchange smaller query blocks across GPUs. We also introduce an efficient activation recomputation technique to support longer visual context. We theoretically analyze the communication benefits of LV-XAttn and show that it can achieve speedups for a wide range of models. Our evaluations with Llama 3-V, mPLUG-Owl3 and OpenFlamingo models find that LV-XAttn achieves up to 10.62$\times$ end-to-end speedup compared to existing approaches.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：多模态大语言模型（MLLMs）常采用交叉注意力（cross-attention）来融合视觉信息与语言表示。但在长视频理解等场景中，视觉输入产生的大量键值（Key-Value）token 导致交叉注意力层的内存需求极高（例如，Llama 3-V 处理 20 分钟视频时单层交叉注意力需超过 234 GB），必须借助多 GPU 分布式计算。
- **现有方法的瓶颈**：已有的分布式注意力机制（如序列并行的 Ring Attention）在处理长视觉输入时，键值块（KV blocks）的通信开销巨大，即使重叠计算和通信，交叉注意力仍可占据迭代总时间的 88%（尽管其参数量仅占 3%）。头并行方法（如 DeepSpeed-Ulysses）受限于注意力头数，可扩展性不足。
- **本文目标**：提出一种**低通信开销的精确分布式交叉注意力机制**，使交叉注意力层不再是训练和推理的效率瓶颈。

## 2. 论文提出的方法论

**核心思想**：利用 MLLMs 中长视觉输入时查询（Query）序列长度远小于键值序列长度的特点，将大的键值块保持本地，仅交换小的查询块、输出块和 softmax 统计量，大幅减少通信量。

**关键技术细节**：
- **分布式交叉注意力（LV-XAttn）**：
  - 每个 worker 存储本地的键值块 \(K_i, V_i\)（大小 \(S_{KV}/n \times d\)）。
  - 查询块 \(Q_i\)、输出块 \(O_i\) 和 softmax 统计量 \(L_i\) 在多个 worker 之间以环形方式轮转。
  - 每一轮中，worker 使用本地键值块与收到的查询块计算部分注意力输出 \(\Delta O\) 和部分统计量 \(\Delta L\)，然后 rescale 更新 \(O_j, L_j\)。
  - 通过重叠计算与通信（在计算当前轮注意力时，同时发送/接收下一轮所需的数据），进一步隐藏通信开销。
- **激活重计算（Activation Recomputation）**：
  - 观察：所有交叉注意力层共享相同的视觉特征 \(y\)（投影前）。因此不在前向时保存每层的键值激活，而是仅保存一份视觉特征 \(y\) 以及各层的 \(x, O_j, L_j\)，反向时重新计算 \(K_i, V_i\)。
  - 内存节省：单个交叉注意力层可减少存储大键值块的需求，从而支持多处理 1.6× 更长的视觉输入，运行时开销仅增加 <8%。

**算法流程（文字描述）**：
1. 将查询、键值、输出按 worker 数量 \(n\) 分块。
2. 每一轮，worker \(i\) 接收来自前一个 worker 的查询块 \(Q_j\)、输出块 \(O_j\) 和统计量 \(L_j\)。
3. 用本地键值块 \(K_i, V_i\) 对 \(Q_j\) 执行 FlashAttention，得到 \(\Delta O, \Delta L\)。
4. 更新 \(O_j, L_j\)（rescale）。
5. 同时，发送本轮的 \(O_j, L_j\) 和下一个查询块到下一个 worker。
6. 经过 \(n\) 轮后，原始 worker 获得完整的注意力输出。

## 3. 实验设计

- **数据集/场景**：非真实数据集，使用**随机生成的输入**（遵循 FlashAttention 等工作的 benchmark 方法），模拟不同文本长度（\(S_Q\)）和帧数（对应 \(S_{KV}\)），覆盖模型典型应用场景（如视频理解）。
- **对比方法**：
  - **Ring Attention**（序列并行）：将键值块在 workers 间轮转。
  - **DeepSpeed-Ulysses**（头并行）。
  - 所有方法均使用 FlashAttention 实现。
- **模型**：6 种 MLLMs：Llama 3-V-11b（8 个交叉注意力层）、mPLUG-Owl3（7b/2b/1b）、OpenFlamingo（9b/3b）。
- **集群配置**：
  - 16 台 A100 80GB（4×NVLink 节点内，节点间 25 GB/s）。
  - 8 台 A30 24GB（节点间 1.25 GB/s）。
  - 12 台 A100 40GB（PCIe 64 GB/s 节点内，节点间 25 GB/s，用于消融实验）。
- **评估指标**：每轮迭代的 wall-clock 时间（前向+反向），单独报告交叉注意力时间（CA）和总时间。

## 4. 资源与算力

- **硬件**：
  - 主要实验使用 16 块 A100 80GB GPU（4 节点 × 4 GPU）。
  - 资源受限场景使用 8 块 A30 24GB GPU（8 节点 × 1 GPU）。
  - 消融实验使用 12 块 A100 40GB GPU（4 节点 × 3 GPU）。
- **训练时长**：论文未报告完整训练时长，仅报告单次迭代时间（秒级）。所有实验为**前向+反向的 benchmark**，非完整训练。
- **其他资源**：使用了 TACC、NERSC、CloudLab 等计算设施。

## 5. 实验数量与充分性

- **实验组数**：
  - 主要对比（表 3、表 4）：每种模型在 3 种不同 \(S_Q\) / \(S_{KV}\) 设置下与 Ring Attention 对比，共 6 模型 × 3 场景 × 2 集群 = 36 组。
  - 与 DeepSpeed-Ulysses 对比（表 5、表 6）：2 种模型，多种 worker 数和输入规模。
  - 消融实验：
    - **通信与计算重叠效果**（图 5）：OpenFlamingo-3b，6 GPU，3 种文本长度。
    - **激活重计算**（图 6）：mPLUG-Owl-7b 和 OpenFlamingo-3b，3 GPU，不同帧数。
- **充分性评估**：
  - 覆盖了不同模型规模（1b~11b）、不同帧编码效率（每个帧产生的视觉 token 数差异大，如 64 vs 6404）、不同集群配置（高带宽 A100 vs 低带宽 A30）。
  - 对比方法考虑了最相关且最强力的基线（Ring Attention 和 DeepSpeed-Ulysses）。
  - 消融实验验证了关键设计（重叠、重计算）的有效性。
  - **公平性**：所有方法使用相同 FlashAttention 内核，输入随机生成避免数据依赖，报告平均 5 次运行结果（含 2 次预热）。
  - **不足**：未在真实视频数据集上测试端到端精度（因方法为精确注意力，输出与标准实现一致，但可能忽略了视觉编码器等其他部分的实际开销）。未与更早的近似方法对比。

## 6. 论文的主要结论与发现

1. **LV-XAttn 大幅降低通信开销**：在典型长视频场景下，通信量仅为 Ring Attention 的 0.04%（Query 块 vs KV 块）。
2. **显著加速**：
   - 在 16×A100 上，交叉注意力层加速 1.47×~27.59×（取决于 \(S_Q\) 和 \(S_{KV}\)），端到端迭代加速 1.16×~10.62×。
   - 在 8×A30 上，交叉注意力层加速 3.97×~45.85×，端到端加速 1.04×~3.45×。
3. **通信可完全隐藏**：由于通信量极小，重叠后运行时开销低于理论无通信基线的 0.42%。
4. **激活重计算提升可处理长度**：可支持多处理 1.6× 的帧数，额外开销 <8%。
5. **与 DeepSpeed-Ulysses 对比**：LV-XAttn 不仅速度更快（1.34×~1.55×），而且不受注意力头数限制，可处理更长序列。

## 7. 优点

- **方法巧妙**：利用交叉注意力中 Q/KV 长度不对称的特性，设计了极低通信的分布式方案，而非通用序列并行。
- **精确无近似**：输出与标准注意力完全一致，不影响模型精度。
- **工程实用**：支持与 FlashAttention 等优化内核结合，提供开源代码。
- **全面的实验验证**：覆盖多种模型、多种集群、多种输入规模，消融实验充分。
- **理论分析与实际结果吻合**：从 FLOPs 和通信量推导出理论加速比，与实际测量一致。

## 8. 不足与局限

- **适用范围有限**：仅适用于**交叉注意力**（query 远小于 key-value）的场景；对于自注意力或相等序列长度，LV-XAttn 无优势甚至更慢（论文明确指出自注意力仍用 Ring Attention）。
- **未在真实训练/推理任务中评估**：所有实验基于随机输入的“benchmark”，缺少真实视频-文本数据上的端到端时间（包含视觉编码、投影等）测量。
- **未与更新方法对比**：如 DistFlashAttn、Striped Attention 等变体，仅对比了原始 Ring Attention 和 DeepSpeed-Ulysses。
- **资源获取门槛**：需要多 GPU 集群（至少 8 块），对小规模实验者可能不友好。
- **激活重计算增加反向计算量**：虽然仅增加 8% 时间，但可能在某些场景下 (如超大 batch) 仍成为瓶颈。
- **未讨论负载均衡与故障容错**：分布式注意力在 worker 数非 n 的因子时可能不平衡（虽然论文未提及，但可通过补齐处理）。

（完）
