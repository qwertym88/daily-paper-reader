---
title: "HashAttention: Semantic Sparsity for Faster Inference"
title_zh: HashAttention：面向更快推理的语义稀疏性
authors: "Aditya Desai, Shuo Yang, Alejandro Cuadron, Matei Zaharia, Joseph E. Gonzalez, Ion Stoica"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Em2oaXd8Dc"
tags: ["query:neural-arch"]
score: 6.0
evidence: 通过语义稀疏性的高效注意力机制
tldr: 注意力计算中的 token 稀疏性未被有效利用。本文提出 HashAttention，将关键 token 识别建模为推荐问题，利用哈希方法实现高效 MIPS，显著加速 Transformer 推理而几乎不损失质量。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 826, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1363, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1780, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 805, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1420, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 681, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 682, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-em2oaxd8dc/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 679, \"height\": 371, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1773, \"height\": 701, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1758, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1604, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1768, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 897, \"height\": 124, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1181, \"height\": 501, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1298, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1801, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-em2oaxd8dc/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 918, \"height\": 195, \"label\": \"Table\"}]"
motivation: 注意力计算成为长上下文处理的瓶颈，现有稀疏方法质量或效率欠佳。
method: 将关键 token 识别构造为 MIPS 问题，采用哈希推荐方法实现 GPU 友好的稀疏注意力。
result: 在多种长序列任务上实现显著加速且保持高质量。
conclusion: HashAttention 是一种高效且实用的注意力加速方案。
---

## Abstract
Leveraging long contexts is crucial for advanced AI systems, but attention computation poses a scalability challenge. While scaled dot-product attention (SDPA) exhibits token sparsity, i.e. only a few pivotal tokens significantly contribute to output, exploiting this sparsity remains challenging. Existing methods either suffer from quality degradation or require substantial additional resources. We show that identifying pivotal tokens is a Maximum Inner Product Search (MIPS) problem. However, existing MIPS solutions are not well-suited for SDPA, as they are not GPU-friendly and often underperform due to the separated query and key distributions. This paper introduces HashAttention, framing pivotal token identification as a recommendation problem. Given a query, HashAttention encodes keys and queries in Hamming space, capturing the required semantic similarity, using learned mapping functions. HashAttention efficiently identifies pivotal tokens for a given query using bitwise operations and computes attention using only these tokens, improving the overall attention efficiency. Trained on generic data, HashAttention reduces tokens used by up to $16\times$ with minimal quality loss, requiring only 32 bits of auxiliary memory per token. Sparsity can be further improved to $32\times$ through task-specific fine-tuning. 
On A100 GPU, at $32\times$ sparsity, incorporating HashAttention reduces attention latency by up to $4.3\times$ in GPT-FAST and $2.54\times$ in FlashDecode, and achieves up to $3.12\times$ higher throughput for GPT-FAST.

---

## 论文详细总结（自动生成）

好的，遵照您的要求，以下是对论文“HashAttention: Semantic Sparsity for Faster Inference”的详细中文总结。

# 论文总结：HashAttention：面向更快推理的语义稀疏性

## 1. 论文的核心问题与整体含义（研究动机和背景）

-   **研究背景**：现代AI系统（特别是大型语言模型，LLM）在处理长上下文（如长文档、多轮对话）时，性能受限于缩放点积注意力（SDPA）机制的计算复杂度。SDPA的计算量和内存占用随上下文长度线性增长，成为严重瓶颈。
-   **核心问题**：尽管SDPA天然存在**token稀疏性**，即只有少数关键token对最终注意力输出有显著贡献，但如何高效地识别并利用这些关键token是一个挑战。现有方法要么质量损失严重（如启发式丢弃），要么需要大量额外资源（如高内存带宽或计算量）。
-   **核心思想**：本文提出将关键token识别问题重构为一种**推荐系统问题**。给定一个查询（query），目标是找到与之最相关的少量键值对（key-value pairs）。作者证明，这等价于一个**最大内积搜索（MIPS）**问题。

## 2. 论文提出的方法论：核心思想、关键技术细节

-   **核心思想**：将关键token的识别转化为一个**基于哈希的推荐问题**。通过学习两个独立的映射函数，将查询和键值对分别映射到**汉明空间（Hamming space）**中的紧凑比特签名（bit signatures）。然后，通过计算查询签名与所有键签名之间的汉明距离（即比特异或操作），来快速找到最相似的“关键”token。

-   **关键技术细节**：
    1.  **问题形式化**：
        - 稀疏注意力可以看作三个子程序的组合：`SCORE`（打分）、`TOPK`（取top-k）、`GATHER-ATT`（基于top-k索引计算注意力）。
        - 论文通过理论证明（Lemma 4.1和4.2），在忽略值向量间相关性的假设下，token的重要性排序等价于一个MIPS问题，具体表现为查询向量 `q` 与 `[key, log(||value||_2)]` 的内积。
    2.  **HashAttention的SCORE函数**：
        - 使用两个独立的**可学习的映射函数** `ϕ_q` 和 `ϕ_kv`，将原始查询 `q` 和键 `k`（及值 `v`）分别编码为 `b` 维的比特签名。映射函数由一个前馈网络和一个符号函数（`sign`）组成。
        - 在训练时，用 `tanh` 代替 `sign` 进行软分区；在推理时，将签名打包成整数，通过 `bitcount(xor(...))` 快速计算汉明距离作为相似度分数。
        - 键值对的签名可以预先计算并缓存，作为KV Cache的辅助元数据。
    3.  **训练方法**：
        - **目标**：使生成的签名能够准确预测每个注意力头的top-k关键token。
        - **损失函数**：采用多标签分类中的**二元交叉熵损失（BCE Loss）**。
        - **类别不平衡**：针对长上下文中正样本（关键token）远少于负样本的问题，使用**动态类别权重**（`class1-weight = α + β * context_length`）进行修正。
        - **训练数据**：在通用数据集（如OpenWebText）上进行预训练，然后可根据特定任务进行微调。在推理模式下，以分块方式处理LLM，并对每个注意力模块进行独立训练。

## 3. 实验设计：数据集、基准与对比方法

-   **数据集**：
    - **质量评估**：**LongBench** (双语长文本理解基准)、**RULER** (长上下文语言模型能力评估基准)。
    - **训练数据**：**OpenWebText**（通用数据）。
-   **评估框架**：**GPT-FAST** 和 **FlashDecode**（用于效率测试）。
-   **对比方法（Baselines）**：
    - 固定稀疏性：**StreamingLLM**
    - KV Cache丢弃策略：**H2O**
    - 基于块的动态稀疏性：**InfLLM**, **Quest**
    - 基于通道选择的稀疏性：**Double Sparsity (DS)**
-   **实验设置**：
    - **模型**：Llama-3.1-8B-Instruct 和 Mistral-7B-v0.3-Instruct。
    - **评估方式**：在固定辅助内存预算（32 bits per token per head，PTPA）下比较，并引入“prompt-offset”（只对提示的末尾部分和后续生成应用稀疏注意力）来模拟预处理长上下文场景。

## 4. 资源与算力

-   论文**未明确说明**训练HashAttention模块所需的具体算力（如GPU型号、数量、训练时长）。实验部分提到了使用A100 GPU进行推理效率测试。
-   论文提到HashAttention的训练是在LLM模型推理模式下进行的，这意味着需要访问KV缓存并离线训练映射函数，但没有给出具体的资源消耗数据。

## 5. 实验数量与充分性

-   **实验丰富度**：实验数量较为充分，涵盖了质量对比（Table 1, 2, 3, 图3）、效率对比（图4）、消融研究（表6-9, 图5）和帕累托分析（图3, 6）。
-   **质量对比**：
    - **表1**：在LongBench上，与所有基线方法在相同辅助内存和token预算下进行详细对比。
    - **图3**：在LongBench和RULER上绘制了稀疏率与模型质量之间的帕累托曲线，与Quest和DS进行了系统比较。
    - **表2, 3**：展示了在固定16x稀疏率下，HashAttention在完整LongBench和RULER上的性能。
-   **效率对比**：分别在GPT-FAST和FlashDecode框架下，测量了不同上下文长度下的延迟和吞吐量。
-   **消融实验**：
    - **Hash签名 vs. LSH签名**（表8）：证明学习到的签名远优于数据无关的LSH签名。
    - **嵌入对分布的影响**（表7）：证明HashAttention的映射函数缓解了查询与键分布分离的问题。
    - **比特宽度影响**（表9）：研究了不同比特数对预测质量的影响。
    - **SCORE计算延迟**（表6）：展示了比特宽度的可扩展性。
-   **公平性与客观性**：实验设计较为客观。在资源受限的情况下（如固定辅助内存），与同类方法（DS, Quest）进行了公平比较，并指出了某些基线（如StreamingLLM, H2O）的固有限制。对实验结果也进行了合理的解释（如稀疏性有时会提升性能可能是排除了干扰token）。

## 6. 论文的主要结论与发现

1.  **性能优越**：HashAttention在保持模型质量的同时，实现了显著的稀疏化。在16x稀疏率下，质量损失微小（LongBench上下降不到1个点）；在32x稀疏率下，通过任务微调可接近全注意力质量。
2.  **效率提升显著**：在长上下文中，HashAttention能有效降低注意力计算延迟并提高吞吐量。在32x稀疏率下，GPT-FAST的注意力延迟最高可提升4.3倍，端到端吞吐量最高可提升3.12倍。
3.  **资源高效**：仅需训练一个独立的、低参数的哈希映射函数。推理时只需额外存储32 bits/key的辅助内存，远低于许多竞争方法。
4.  **通用性强**：训练于通用数据（OpenWebText）的HashAttention可在多种下游任务上泛化，表现出良好的迁移能力。

## 7. 优点：方法或实验设计上的亮点

-   **理论扎实**：将关键token识别问题明确定义为MIPS问题，并给出了理论证明（Lemma 4.1, 4.2），使得方法有坚实的理论基础，而非纯启发式。
-   **设计精巧**：巧妙地将推荐系统中的学习过程与注意力机制的稀疏性结合起来。使用独立的查询和键映射函数，解决了MIPS中查询与键分布不同的问题。
-   **GPU友好**：核心操作是快速的比特运算（XOR, POPCOUNT），完美适配GPU的并行计算能力，避免了CPU-GPU数据搬运或图搜索等不规则操作。
-   **内存高效**：辅助元数据（比特签名）非常紧凑（32 bits/key），几乎不增加KV Cache的存储压力。
-   **实验全面**：实验覆盖了多种主流模型、多种长文本基准、多种竞争方法，并有充分的消融研究支撑结论。

## 8. 不足与局限

-   **需要训练**：与一些无需训练的方法（如Quest, DS）相比，HashAttention需要至少一次训练（或校准）来学习映射函数。每更换一个新的LLM模型，都需要为它重新训练HashAttention模块。
-   **扩展至超长上下文的验证不足**：论文主要在LLaMA 3.1 8B模型（支持128K上下文）上进行了测试，但没有充分探讨在极其长（如1M+ token）的上下文中，HashAttention的检索效率和性能表现如何。
-   **对训练数据分布的依赖**：虽然可以泛化，但质量仍可能受限于训练数据的分布。例如，在中文任务上的表现略微逊于在英文任务上的表现。
-   **未评估CPU offloading场景**：论文实验前提是KV Cache完全在GPU上。对于需要将KV Cache存储在CPU RAM中的超长上下文场景（这是FlashDecode等系统的设计目标），论文没有评估HashAttention的有效性，这是未来工作的重要方向。
-   **计算瓶颈转移**：虽然减少了注意力计算，但引入了新的“SCORE”计算（即求汉明距离）。实验显示，在短上下文（<8K tokens）中，SCORE计算的开销可能超过其带来的收益，导致延迟反而增加。

（完）
