---
title: Blending Complementary Memory Systems in Hybrid Quadratic-Linear Transformers
title_zh: 混合二次-线性Transformer中的互补记忆系统融合
authors: "Kazuki Irie, Morris Yau, Samuel J. Gershman"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Q8m0TkIpJZ"
tags: ["query:neural-arch"]
score: 6.0
evidence: 混合记忆架构的神经网络设计，提升序列处理性能
tldr: 本文混合了二次Transformer的键值记忆与线性Transformer的快权重记忆，提出三种融合方法。混合模型兼顾了精确检索和长序列处理能力，在多个序列任务上表现出更优的泛化性能。该架构创新属于神经网络结构改进范畴。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-q8m0tkipjz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-q8m0tkipjz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-q8m0tkipjz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 817, \"height\": 567, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 944, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 989, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 661, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 875, \"height\": 767, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 738, \"height\": 595, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 793, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1184, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-q8m0tkipjz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 697, \"height\": 553, \"label\": \"Table\"}]"
motivation: 二次和线性Transformer的记忆系统各有优劣，希望融合以取长补短。
method: 提出三种融合方式，在不同阶段和方式上结合键值记忆与快权重记忆。
result: 混合架构在长序列和精确回忆任务上均优于单一记忆系统，泛化能力更强。
conclusion: 该工作为设计兼具高效与精准记忆的神经网络架构提供了新思路。
---

## Abstract
We develop hybrid memory architectures for general-purpose sequence processing neural networks, that combine key-value memory using softmax attention (KV-memory) with fast weight memory through dynamic synaptic modulation (FW-memory)---the core principles of quadratic and linear transformers, respectively. These two memory systems have complementary but individually limited properties: KV-memory offers precise retrieval but is constrained by quadratic complexity in sequence length, while FW-memory supports arbitrarily long sequences and enables more expressive computation but sacrifices precise recall. We propose and compare three methods to blend these two systems into a single memory system, differing in how and when input information is delivered to each system, to leverage the strengths of both. We conduct experiments on general language modeling and retrieval tasks by training 340M- and 1.3B-parameter models from scratch, as well as on synthetic algorithmic tasks designed to precisely illustrate the benefits of certain hybrid methods over others. We also evaluate our hybrid memory systems on reinforcement learning in partially observable environments. Overall, we demonstrate how a well-designed hybrid can overcome the limitations of its individual components, offering new insights into the design principle of neural memory systems.

---

## 论文详细总结（自动生成）

## 论文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

现代 Transformer 存在两种互补但各有局限的记忆系统：

- **二次 Transformer（KV-memory）**：通过 softmax 注意力实现精确检索，但计算复杂度随序列长度二次增长，实际使用时需限定上下文窗口大小。
- **线性 Transformer（FW-memory）**：通过快权重编程实现线性复杂度，支持任意长序列，且具有更强的状态追踪（如 DeltaNet）能力，但牺牲了精确回忆。

理想通用记忆系统应同时具备精确性、长程处理和表达力，但单一模型无法兼得。受大脑中互补学习系统（CLS）的启发，本文提出将两种记忆系统融合到一个混合架构中，取长补短。

### 2. 论文提出的方法论

#### 核心思想
将 KV-memory（精确检索）与 FW-memory（长程处理+表达力）结合在一个层内，共享键、值、查询向量，并在输出时融合两者结果。

#### 三种混合方法（HQLT: Hybrid Quadratic-Linear Transformers）

1. **Delayed-Streaming HQLT**  
   - KV-memory 维护最近 S 个 token 的滑动窗口。  
   - 当旧 token 被移出窗口时，将其送入 FW-memory（使用 DeltaNet 的 delta 规则更新）。  
   - 输出 = FW-memory 输出 + KV-memory 输出（可加权混合）。  
   - 分工：FW-memory 负责窗口外所有历史，KV-memory 负责窗口内精确检索。

2. **Delayed-Chunk HQLT**  
   - 基于分块并行训练思路：块内使用 softmax 注意力，块间使用 FW-memory 的循环形式。  
   - FW-memory 只在块边界更新，块内 KV-memory 只容纳当前块内容。  
   - 与 Munkhdalai et al. (2024) 的 Infini-attention 类似。

3. **Synchronous HQLT**  
   - 每个时间步输入同时进入 KV-memory 和 FW-memory。  
   - 无延迟，FW-memory 实时处理最新输入。  
   - 公式与 Delayed-Stream 类似，但 FW-memory 更新使用 (k_t, v_t) 而非 (k_{t-S}, v_{t-S})。

#### 关键技术细节
- FW-memory 基于 **DeltaNet**（带 delta 规则和动态学习率 β_t，激活函数为 SiLU + L2 归一化）。  
- 输出混合策略：sum mixing、dynamic scalar mixing、dynamic vector mixing（学习权重 γ_t）。  
- 训练兼容 flash-attention 和 flash-linear-attention，支持高效分块并行训练。

### 3. 实验设计

| 实验类型 | 数据集/场景 | 基线方法 | 对比模型 |
|----------|-------------|----------|----------|
| 通用语言建模 | FineWeb-Edu 15B tokens, 评估 WikiText-2, LAMBADA, PiQA, HellaSwag, WinoGrande, ARC-easy, ARC-challenge | Transformer++ (二次), DeltaNet (线性) | 三种 HQLT 变体 |
| 检索密集任务 | SWDE, SQuAD, FDA | 同上 | HQLT Synchronous (含消融混合策略和窗口大小) |
| 表达力/算法任务 | Parity (奇偶性), Modular Arithmetic (模运算) | 同上 + Mamba | 三种 HQLT + vanilla linear attention |
| 强化学习 (POMDP) | Passive visual match (3阶段导航任务, 780步) | Transformer (全上下文), DeltaNet | HQLT Synchronous (窗口64) |

### 4. 资源与算力

- **硬件**：4 张 H100-80GB GPU。  
- **训练时长**：  
  - 340M 参数模型：基础 Transformer ~8小时，DeltaNet ~10小时，HQLT ~10小时。  
  - 1.3B 参数模型：基础 Transformer/DeltaNet ~26小时，HQLT ~30小时。  
- **数据量**：15B tokens（340M 用 2048 长度，1.3B 用 2240 长度）。  
- 所有模型训练吞吐量约 170K tokens/s（基线）和 148K tokens/s（HQLT）。  
- 合成任务单次训练约 70分钟（单 H100）。

### 5. 实验数量与充分性

- **充分性**：覆盖多种任务类别（语言建模、检索、算法、RL），两种模型规模（340M 和 1.3B），并进行了大量消融实验。  
- **消融实验**：  
  - 窗口大小（64→1024）。  
  - 混合策略（sum / scalar / vector）。  
  - FW-memory 类型（DeltaNet vs vanilla linear attention）。  
  - 位置编码（RoPE vs No Pos）。  
- **公平性**：所有模型采用相同的训练数据、优化器、调度策略，baseline 采用公开的最强配置（Transformer++、DeltaNet 最新实现）。  
- **可重复性**：代码已开源，基于 fla 和 flame 框架，使用标准评估工具 lm-evaluation-harness。

### 6. 论文的主要结论与发现

1. **同步混合（Synchronous HQLT）最优**：  
   - 在通用语言建模上略优于或持平基线。  
   - 在 LAMBADA 困惑度上比 Transformer 和 DeltaNet 降低约 15%。  
   - 在算法任务上（Parity、Modular Arithmetic）达到 100% 准确率，而延迟混合完全失败。  
   - 在 RL 任务上显著缩小与 Transformer 的差距（仅用窗口 64）。  

2. **延迟混合（Delayed-Stream/Chunk）的局限**：  
   - FW-memory 因延迟无法实时处理输入，丧失表达力优势，无法解决状态追踪任务。  
   - 在检索任务上表现也不如同步混合（尤其在 SWDE 和 FDA）。  

3. **窗口大小的重要性**：  
   - 对于检索任务，增大窗口（如 1024）可大幅提升性能，但仍低于全上下文 Transformer。  
   - FW-memory 无法完全替代大上下文窗口进行精确检索。  

4. **FW-memory 类型至关重要**：  
   - 用 vanilla linear attention 替代 DeltaNet 会导致性能严重下降（基因语言模型丢失 5.6% 平均准确率，算法任务失败）。  

### 7. 优点

- **理论动机清晰**：基于神经科学中互补学习系统概念，提出四种互补性维度（复杂度、上下文长度、检索精度、表达力）。  
- **架构设计合理**：三种混合策略各有逻辑，实验系统比较后得出明确推荐（同步混合）。  
- **实验充分全面**：涵盖语言、算法、强化学习三大领域，两个模型规模，严格的消融和对比。  
- **工程友好**：完全兼容现有高效实现（flash-attention, flash-linear-attention），代码开源并基于成熟框架。  
- **对最新进展敏感**：采用 DeltaNet（含动态学习率、SiLU 激活）而非旧版线性注意力，确保结论的时效性。

### 8. 不足与局限

- **检索任务仍不理想**：即使同步混合，也需要较大窗口（如 1024）才能接近全上下文 Transformer，说明 FW-memory 无法完全替代 KV-memory 的精确回忆。  
- **延迟混合的排除合理但缺少更细致分析**：论文仅测试了窗口=8/16 的延迟混合，未探索更大延迟窗口或自适应延迟是否可能改善。  
- **计算开销未完全量化**：虽提及训练时间，但未详细对比不同窗口大小下的推理内存/速度。  
- **仅测试一种 FW-memory 变体（DeltaNet）**：虽然作者指出可扩展至其他线性模型，但未实验如 GLA、Mamba2 等。  
- **RL 实验仅一个任务**：结论泛化性有限。  
- **窗口大小超参数敏感**：在检索任务上存在非单调行为（如增大窗口有时反而下降），缺乏深入解释。

（完）
