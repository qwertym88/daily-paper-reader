---
title: "SeerAttention: Self-distilled Attention Gating for Efficient Long-context Prefilling"
title_zh: SeerAttention：自蒸馏注意力门控实现高效长上下文预填充
authors: "Yizhao Gao, Zhichen Zeng, DaYou Du, Shijie Cao, Peiyuan Zhou, Jiaxing Qi, Junjie Lai, Hayden Kwok-Hay So, Ting Cao, Fan Yang, Mao Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Nf8yfPDFTl"
tags: ["query:neural-arch"]
score: 8.0
evidence: 新颖的注意力门控机制用于高效长上下文处理
tldr: 长上下文注意力计算复杂，现有稀疏方法依赖预定义模式。本文提出SeerAttention，受MoE门控启发，在注意力中增加可学习门控，自适应地选择重要块。该方法自蒸馏自注意力图，无需外部监督，在长上下文预填充任务上大幅降低计算量，同时保持模型质量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1460, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1453, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 767, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1433, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1454, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1172, \"height\": 555, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1267, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-nf8yfpdftl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 528, \"height\": 390, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8yfpdftl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1403, \"height\": 618, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8yfpdftl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1380, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8yfpdftl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 904, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8yfpdftl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1398, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-nf8yfpdftl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1223, \"height\": 385, \"label\": \"Table\"}]"
motivation: 长上下文注意力二次复杂度高，现有稀疏方法适应性差。
method: 借鉴MoE门控机制，在注意力中引入可学习门控，学习块级稀疏模式。
result: 在长上下文预填充中显著降低计算量，保持模型质量。
conclusion: SeerAttention提供了自适应、高效的注意力稀疏化方案。
---

## Abstract
Attention is the cornerstone of modern Large Language Models (LLMs). Yet its quadratic complexity hinders efficiency and scalability, especially for long-context processing. A promising approach is to leverage sparsity in attention.  However, existing sparsity-based solutions predominantly rely on predefined patterns or heuristics at the attention head level, struggling to adapt dynamically to different contexts efficiently. We propose SeerAttention, a simple yet effective attention mechanism that directly learns the block-level attention sparsity from the LLM itself. Inspired by the gating mechanism in Mixture of Experts (MoE), SeerAttention augments the conventional attention with a **learnable gate** that **selectively activates important blocks** within the attention map. Specifically, the gate first pools the query (Q) and key (K) tensors along the sequence dimension and processes them through learnable linear layers. The resulting matrices are then multiplied together to produce the gating scores, which are used to predict block-level attention sparsity. Combined with our block-sparse FlashAttention kernel, SeerAttention can achieve significant speedup on GPUs. When applied to pre-trained LLMs, SeerAttention only requires training the gate parameters in a lightweight self-distillation manner, allowing rapid convergence. Our evaluation results demonstrate that SeerAttention achieves better model accuracy and lower latency for long-context pre-filling compared to prior methods. Code is available at: https://github.com/microsoft/SeerAttention.

---

## 论文详细总结（自动生成）

# 论文《SeerAttention: Self-distilled Attention Gating for Efficient Long-context Prefilling》详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：Transformer中的注意力机制具有二次复杂度（$O(n^2)$），在处理长上下文时计算和内存开销巨大，严重限制了LLM的可扩展性和推理效率。
- **现有方法的不足**：
  - 线性注意力或循环架构（如Mamba）效率高，但性能往往不及全注意力。
  - 已有的稀疏注意力方法（如MoA、MInference）主要依赖**预定义模式**或**启发式规则**，缺乏对不同模型、输入上下文和注意力头的动态适应性，无法充分利用注意力内在的动态稀疏性。
- **研究意义**：提出一种**可学习的、自适应的块级稀疏注意力机制**，能够直接从预训练LLM自身学习稀疏模式，无需预定义模式或从头预训练，从而在保持或提升模型精度的同时大幅加速长上下文预填充阶段。

## 2. 方法论

### 2.1 核心思想
- **借鉴MoE门控机制**：在标准注意力中引入一个轻量级可学习门控模块 **AttnGate**，该模块通过池化操作将Q和K下采样为块级表示，然后通过线性层和矩阵乘法生成每个块的“重要性分数”，从而预测注意力图中的哪些块是重要的（即非稀疏的）。
- **自蒸馏训练**：AttnGate的监督信号来自原始LLM的全注意力输出的**2D-MaxPooled注意力图**（块级真实标签）。仅训练门控参数，其余模型参数冻结，实现快速收敛。

### 2.2 关键技术细节
- **AttnGate结构**（图1）：
  - **池化**：对Q采用平均池化，对K采用最大、最小、平均池化的组合（经实验验证最优）。
  - **可学习线性层**：池化后的Q和K分别经过线性变换（Linear Layer）。
  - **块级RoPE**：为支持长度外推，在AttnGate内部重新施加块级旋转位置编码（$\theta' = \theta / B$，B为块大小），使用不含位置编码的 $Q_{\text{nope}}$ 和 $K_{\text{nope}}$ 作为输入。
  - **输出**：$O = \text{softmax}(Q_c K_c^T / \sqrt{d})$，产出大小为 $[\text{seq}/B, \text{seq}/B]$ 的门控分数矩阵，仅为原注意力图的 $1/4096$（当B=64时），计算开销极低。
- **生成二进制块掩码**：
  - 两种方式：**TopK**（每行选top-k块）或 **阈值法**（分数大于阈值则激活）。
  - 推理时可动态调整稀疏率。
- **块稀疏FlashAttention内核**：将块大小与FlashAttention的tile大小对齐（64或128），根据二进制掩码跳过未激活块的I/O和计算。

### 2.3 训练损失函数
- 使用 **KL散度损失** 蒸馏AttnGate输出 $o$ 与真实标签 $gt$（2D-MaxPooled注意力图）之间的分布，而非MSE。
  - $gt = \text{MaxPool2D}\left(\text{softmax}\left(\frac{Q_{\text{rope}} K_{\text{rope}}^T}{\sqrt{d}}\right)\right)$
  - $o = \text{AttnGate}(Q_{\text{nope}}, K_{\text{nope}})$
  - $\text{loss} = D_{KL}(gt \| o)$

## 3. 实验设计

### 3.1 模型与数据集
- **模型**：
  - Llama-3.1-8B-Instruct、Llama-3.1-70B-Instruct
  - Qwen2.5-7B-Instruct、Qwen2.5-14B-Instruct、Qwen2.5-32B-Instruct
- **基准任务**：
  - **长上下文**：LongBench（bilingual, multitask）、RULER（4k~128k的13个子任务）
  - **短上下文**：Open LLM Leaderboard上的HellaSwag、MMLU、ARC-challenge、GSM8K

### 3.2 对比方法
- **MoA**（Mixture of Sparse Attention）：离线搜索静态稀疏模式。
- **MInference 1.0**：基于预定义“Vertical-Slash”模式动态生成稀疏索引。
- **DuoAttention**：部分头作为streaming head，其余为dense head。

### 3.3 实验设置
- **块大小**：固定为64。
- **蒸馏训练数据**：RedPajama数据集，截断至64k长度，带BOS和EOS。
- **评估方式**：长上下文任务中仅对上下文（非问题）应用稀疏注意力。

## 4. 资源与算力

- **训练硬件**：A100 GPU（未明确具体数量，但使用DeepSpeed stage 2优化）。
- **训练时长**：
  - 对于7B/8B模型，约**40 A100 GPU小时**（500步训练，batch size 16）。
  - 对于70B模型（约503MB门控参数），训练时间按比例增长，但未给出具体数字。
- **参数开销**：
  - 训练参数约1.01亿（约模型总参数的1.3%）。
  - 推理时AttnGate的内存和延迟开销小于5%（在128k长度下几乎可忽略）。

## 5. 实验数量与充分性

- **实验组数**：
  - **长上下文精度**：在LongBench上对5个模型进行测试；在RULER上对Llama-3.1-8B进行全长度（4k~128k）测试。
  - **短上下文精度**：4个数据集（MMLU等）的测试。
  - **效率对比**：内核级（速度 vs 稀疏率曲线）、端到端预填充时间（RULER全序列平均）。
  - **消融实验**：池化方法选择（图2）、块级RoPE效果（图3）、AttnGate开销分解（图4）。
  - **可视化**：展示学习到的多种稀疏模式（A-shape、Vertical、Slash等）。
  - **附录中额外实验**：训练kernel的内存/延迟、YaRN扩展下的联合微调、解码阶段初步结果（DeepSeek-R1-Distill-Qwen-14B）。
- **充分性评价**：
  - 实验覆盖多个模型大小、多种基准类型、多种稀疏率，与最先进方法进行公平比较（使用官方配置）。
  - 消融设计合理（池化组合、位置编码、训练策略）。
  - 但仍存在局限：主要聚焦预填充阶段，解码阶段仅初步探索；在128k超长上下文下的RULER精度略低于全注意力（稀疏率>80%），但速度优势显著。

## 6. 主要结论与发现

- **精度优势**：SeerAttention在LongBench上超越所有对比方法（如相较于全注意力平均提升0.13%），在RULER上平均精度（87.60）仅次于全注意力（88.01），但提升最接近（仅低0.41%），且平均速度提升最高（1.41×）。
- **效率优势**：内核级速度呈线性加速，128k长度、90%稀疏率下实现**7.3×加速**；端到端预填充速度在128k下达到2.43×。
- **自适应能力**：AttnGate无需人工定义模式，能够自动学习A-shape、Vertical、Slash等多种稀疏模式，并能根据输入长度动态调整稀疏率（4k时~10%，128k时~85%）。
- **训练高效**：自蒸馏仅需500步即可收敛，训练开销远小于预训练或全模型微调。
- **解码扩展潜力**：初步实验显示，在DeepSeek-R1-Distill-Qwen-14B上，SeerAttention解码变体在AIME24/MATH500/GPQA-Diamond上优于训练无关方法Quest。

## 7. 优点

- **新颖性**：首次将**可学习门控**与**自蒸馏**结合用于注意力稀疏化，避免了预定义模式的局限性。
- **即插即用**：可直接应用于任何预训练全注意力模型，无需从头训练或修改原模型权重。
- **硬件友好**：块级稀疏设计与FlashAttention tiling对齐，在现代GPU上实现近乎线性的加速。
- **轻量级训练**：仅训练门控参数，收敛快（500步），训练成本低（40 A100小时）。
- **鲁棒性强**：池化组合和块级RoPE设计有效保留关键信息，支持长度外推至不同上下文。

## 8. 不足与局限

- **阶段覆盖不全**：论文主要针对**预填充阶段（prefilling）** 进行优化，解码阶段（decoding）仅给出了初步结果（附录A.3），尚未充分验证其在自回归生成中的有效性。
- **训练数据依赖**：蒸馏需要一定量的训练数据（RedPajama），虽然数据量不大，但仍需额外准备和标注步骤（自动生成ground truth）。
- **超参数敏感**：推理时阈值或TopK比例需要手动调整以平衡精度和速度，不同任务可能需不同设置。
- **极长上下文精度下降**：在128k长度的RULER测试中，由于稀疏率高达85%，精度（73.37）低于全注意力（76.26）和DuoAttention（75.32，但稀疏率<50%），表明高稀疏率下存在精度损失。
- **对比方法覆盖不全面**：未与训练式稀疏注意力（如Native Sparse Attention、MoBA）进行对比，但这些方法需要从头预训练，与本工作设定不同。
- **重复性信息**：代码已开源，但论文中未提供完整的训练配置（如具体GPU数量、训练总时长对于70B模型等），可能影响完全复现。

（完）
