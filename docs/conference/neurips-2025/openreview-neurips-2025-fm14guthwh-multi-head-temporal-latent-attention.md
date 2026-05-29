---
title: Multi-head Temporal Latent Attention
title_zh: 多头时间潜注意力
authors: "Keqi Deng, Phil Woodland"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=fm14gUThwh"
tags: ["query:neural-arch"]
score: 7.0
evidence: 沿时间维度压缩KV缓存的新型注意力机制
tldr: 针对Transformer推理中KV缓存随序列长度线性增长的问题，提出多头时间潜注意力(MTLA)，通过超网络动态合并时间相邻的KV向量，降低内存占用。同时设计步长感知因果掩码保证训练与推理一致性。实验表明在多个序列任务上以更少内存达到与标准注意力相当的性能。为高效注意力机制提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-fm14guthwh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1433, \"height\": 636, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fm14guthwh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 601, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1455, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1286, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1346, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1456, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1452, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1222, \"height\": 1397, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1435, \"height\": 594, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fm14guthwh/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 599, \"height\": 164, \"label\": \"Table\"}]"
motivation: 标准注意力KV缓存随序列增长，成为推理瓶颈。
method: 提出MTLA，用超网络在时间维度合并邻近KV向量，减少缓存大小。
result: 在多种序列任务上显著降低内存使用，性能与标准注意力持平。
conclusion: 时间维度压缩是提升注意力推理效率的有效方法。
---

## Abstract
While Transformer self-attention offers strong parallelism, the  Key-Value (KV) cache grows linearly with sequence length and becomes a bottleneck for inference efficiency. Multi-head latent attention was recently developed to compress the KV cache into a low-rank latent space. This paper proposes Multi-head Temporal Latent Attention (MTLA), which further reduces the KV cache size along the temporal dimension, greatly lowering the memory footprint of self-attention inference. MTLA employs a hyper-network to dynamically merge temporally adjacent KV cache vectors. To address the mismatch between the compressed KV cache and processed sequence lengths, a stride-aware causal mask is proposed to ensure efficient parallel training and consistency with inference behaviour. Experiments across tasks, including speech translation, speech recognition, speech understanding and text summarisation, demonstrate that MTLA achieves competitive performance compared to standard Multi-Head Attention (MHA), while greatly improving inference speed and GPU memory usage. For example, on a English-German speech translation task, MTLA achieves a 5.3$\times$ speedup and a reduction in GPU memory usage by a factor of 8.3 compared to MHA, while maintaining translation quality.

---

## 论文详细总结（自动生成）

# 论文总结：Multi-head Temporal Latent Attention (MTLA)

## 1. 核心问题与整体含义（研究动机和背景）

- Transformer 自注意力机制在并行计算方面表现优异，但其 **Key-Value (KV) 缓存** 随着序列长度线性增长，成为推理效率的主要瓶颈，尤其是在长序列场景（如语音、文档摘要）中。
- 已有工作尝试压缩 KV 缓存，例如 **Multi-Query Attention (MQA)**、**Grouped-Query Attention (GQA)** 通过减少 KV 头数来降低内存，但存在表达能力下降的问题；**Multi-Head Latent Attention (MLA)** 通过低秩潜在空间压缩 KV 向量，取得了更好的性能，但 **均未探索沿时间维度进行压缩** 的可能性。
- 本文提出 **多头时间潜注意力 (MTLA)**，在 MLA 的基础上进一步沿时间维度压缩 KV 缓存，从而大幅降低内存占用和推理延迟，并保持与标准多头注意力 (MHA) 相当的任务性能。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- MTLA 构建于 MLA 的低秩潜在空间压缩之上，额外利用 **超网络 (hyper-network)** 动态生成权重，将时间上相邻的低秩潜在向量合并为更短的 KV 缓存序列。
- 引入 **步长感知因果掩码 (stride-aware causal mask)**，确保高效并行训练时的注意力行为与增量推理一致，解决了压缩后缓存长度与输入序列长度不匹配的问题。

### 关键技术细节

1. **低秩潜在压缩**  
   沿用 MLA，对输入序列 \(X \in \mathbb{R}^{T \times d}\) 进行低秩投影（维度 \(r\)），得到潜在向量序列 \(C \in \mathbb{R}^{T \times r}\)：  
   \( C = X W^r, \quad W^r \in \mathbb{R}^{d \times r} \)

2. **时间维度合并**  
   设定压缩比 \(s\)（默认 \(s=2\)），将每 \(s\) 个相邻潜在向量通过超网络生成的权重 \(w_i\) 加权求和，得到压缩后的序列 \(\hat{C} \in \mathbb{R}^{t \times r}\)，其中 \(t = \lceil T/s \rceil\)。  
   例如 \(s=2\) 时：\(\hat{c}_1 = w_1 c_1 + w_2 c_2\)。

3. **超网络生成权重**  
   超网络以当前潜在向量 \(c_i\) 和对应的位置编码 \(pe_j\)（\(j = \lceil i/s \rceil\)）为输入，通过线性层和 Sigmoid 激活输出标量权重：  
   \( w_i = \text{Sigmoid}(\text{Linear}(c_i) \cdot \text{Linear}(pe_j)) \)

4. **步长感知因果掩码**  
   训练时，先按公式（14）构造与原始序列等长的压缩序列 \(\hat{C}'\)（包含临时版本），然后使用专用掩码：  
   \( \text{mask}_{m,n} = 0 \text{ if } n=m \text{ or } (n < m \text{ and } n \bmod s = 0), \text{ else } -\infty \)  
   该掩码保证了训练时每个查询只能访问与推理时一致的压缩 KV 缓存，实现并行训练。

5. **解耦旋转位置编码 (Decoupled RoPE)**  
   类似 MLA，采用解耦 RoPE，并将 RoPE 键也沿时间维度压缩，以匹配训练与推理。

6. **计算优化**  
   通过矩阵乘法结合律，将键值投影矩阵吸收到查询和输出投影中，避免显式计算完整 K、V，进一步提升效率。

## 3. 实验设计

### 使用的数据集与场景
- **语音翻译 (ST)**：MuST-C v1.0 En-De（TED Talks 英语-德语）
- **文本摘要 (TS)**：XSum（BBC 新闻数据）
- **自动语音识别 (ASR)**：AMI 会议语料库（100 小时英语会议）
- **口语理解 (SLU)**：SLURP（人机交互指令，意图分类）
- **额外评估**：Long Range Arena (LRA) 基准、WMT14 英德机器翻译

### Benchmark 与对比方法
- 主要对比：标准 **MHA**、**MLA**（同为自注意力机制）
- 相关方法对比：**MQA**、**GQA**（组大小为 2）、**MLA + SnapKV**（令牌压缩方法）、**Mamba-2**（线性时间模型）
- 所有模型在同一 decoder-only 架构下训练，自注意力模块替换为对应机制，其余部分严格一致。

## 4. 资源与算力

- **GPU 型号**：单张 NVidia RTX 6000 Ada（48GB 显存）
- **训练时长**（每 epoch）：  
  - ST：约 13 分钟  
  - 文本摘要：约 20 分钟  
  - ASR：约 50 分钟  
  - SLU：约 15 分钟  
- 总训练步数：ST 最大 100k 步，文本摘要 60k 步，ASR 10k 步，SLU 30k 步。  
- 所有实验均在单卡上完成，未使用多卡并行或大规模预训练。

## 5. 实验数量与充分性

### 实验组数
- 主实验覆盖 4 个任务（ST、TS、ASR、SLU），每个任务报告 MHA、MLA、MTLA 的得分及推理速度/内存。
- 在 ST 任务上进行了更详细的消融：不同压缩比 \(s=2,3,4\)；与 MQA、GQA、MLA+SnapKV、Mamba-2 对比；使用 FlashAttention-2 的扩展实验。
- 额外补充实验：LRA 基准（8 种方法对比）、WMT14 机器翻译（MLA vs MTLA）。
- 实验数量较为充分，覆盖多种长序列场景和典型高效注意力方法。

### 充分性与公平性
- 所有对比模型使用相同的数据预处理、优化策略、批大小和束搜索大小。
- 推理速度测试在同一 GPU 上以相同批大小进行，结果具有可比性。
- 在统计显著性方面，部分结果（如 MTLA s=4 vs MQA）使用了 SacreBLEU 统计检验（p<0.05）。
- 局限性：未在大规模 LLM 上验证（受限于计算资源）；仅测试了 decoder-only 架构；未探索极端长序列（如>100k tokens）但通过压缩比 s=4 展示了进一步潜力。

## 6. 主要结论与发现

- **效率大幅提升**：在 ST 任务上，MTLA 默认 (s=2) 比 MHA 推理速度快 **4.29×**，GPU 内存降低 **6.58×**；s=4 时速度提升 **5.78×**，内存减少 **9.71×**。
- **任务性能持平甚至更优**：在 ST、ASR、SLU、文本摘要上，MTLA 的 BLEU/WER/ROUGE/Accuracy 均与 MHA 和 MLA 相当，部分略优（如 ST 上 23.28 BLEU vs MHA 23.18）。
- **优于同类方法**：相比 MQA、GQA、MLA+SnapKV、Mamba-2，MTLA 在质量与效率两方面均占优。
- **FlashAttention-2 兼容**：结合 FlashAttention-2 后，MTLA 相比 MHA 实现 3.99× 速度提升和 14.81× 内存降低（扩展自定义 CUDA 实现）。
- **在短文本翻译任务上无退化**：WMT14 英德翻译中 MTLA (25.57 BLEU) 与 MLA (25.63) 基本一致，说明时间压缩不会损害短序列性能。

## 7. 优点

- **创新性**：首次提出沿时间维度压缩 KV 缓存的自注意力机制，填补了该方向空白。
- **高效性与兼容性**：在保持 MLA 低秩压缩优势的同时进一步压缩；步长感知掩码使训练保持并行性；与 FlashAttention 等加速技术兼容。
- **通用性**：在语音、文本、多模态任务上均验证有效，且适用于不同长度的序列。
- **实用性**：开源代码（GitHub 链接），实验细节充分，便于复现与扩展。
- **理论清晰**：通过矩阵结合律吸收投影，避免冗余计算；掩码设计推理与训练一致，逻辑严谨。

## 8. 不足与局限

- **计算资源限制**：未能在大型语言模型（如数十亿参数）上验证其效果，这在当前 LLM 时代是重要局限。
- **实验覆盖有限**：仅测试 decoder-only 架构，未在 encoder-decoder 或纯 encoder 模型上评估；未覆盖更长序列（如 100k tokens）但推测有效。
- **对比方法选择**：虽与主流方法对比，但未包括更多新兴的 KV 缓存技术（如 StreamingLLM、H2O、Quest 等），自称“首次”时间压缩，但存在 [32] 相关工作（作者承认），但 MTLA 可实现从头训练，优于 [32] 的 retrofitting 方法。
- **超网络开销**：生成权重的超网络带来额外计算，但总体仍显著节省内存与时间；未详细分析超网络本身的计算成本。
- **应用风险**：主要讨论效率提升，未深入分析潜在负面社会影响（如能源消耗降低是正面影响）。

（完）
