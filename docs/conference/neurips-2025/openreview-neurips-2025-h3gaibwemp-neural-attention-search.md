---
title: Neural Attention Search
title_zh: 神经注意力搜索
authors: "Difan Deng, Marius Lindauer"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=h3gaIBwemp"
tags: ["query:neural-arch"]
score: 9.0
evidence: 神经架构搜索自动学习Transformer稀疏注意力模式
tldr: 本文提出神经注意力搜索（NAtS），将单次神经架构搜索方法应用于Transformer，自动学习每个令牌的类型（全局、局部、滑动窗口），从而稀疏化注意力。在从头训练和微调实验中，NAtS在降低计算量的同时保持了模型准确性，是神经网络架构搜索提升性能的直接应用。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1426, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 659, \"height\": 205, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 604, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 587, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 646, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1446, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1449, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1447, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1447, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-h3gaibwemp/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1444, \"height\": 422, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1395, \"height\": 530, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1451, \"height\": 696, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1364, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 697, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1444, \"height\": 695, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1443, \"height\": 692, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1225, \"height\": 742, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-h3gaibwemp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1062, \"height\": 739, \"label\": \"Table\"}]"
motivation: Transformer注意力计算冗余，手动设计稀疏模式繁琐且次优。
method: 设计包含三种令牌类型的搜索空间，通过可学习注意力掩码联合优化架构权重。
result: NAtS在多种Transformer任务上减少计算量并保持或提升精度，搜索高效。
conclusion: 为Transformer的高效架构自动设计提供了NAS新范式。
---

## Abstract
We present Neural Attention Search (NAtS), an end-to-end learnable sparse transformer that automatically evaluates the importance of each token within a sequence and determines if the corresponding token can be dropped after several steps. To this end, we design a search space that contains three token types: (i) Global Tokens will be preserved and queried by all the following tokens. (ii) Local Tokens survive until the next global token appears. (iii) Sliding Window Tokens have an impact on the inference of a fixed size of the next following tokens. Similar to the One-Shot Neural Architecture Search approach, this token-type information can be learned jointly with the architecture weights via a learnable attention mask. Experiments on both training a new transformer from scratch and fine-tuning existing large language models show that NAtS can efficiently reduce the KV cache and the inference costs for the transformer-based models while maintaining the models' performance.

---

## 论文详细总结（自动生成）

# 论文总结：Neural Attention Search (NAtS)

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：Transformer 的注意力计算复杂度为 O(L²)（L 为序列长度），即使使用 KV 缓存降低到 O(L)，随着模型规模和上下文长度增大，KV 缓存的存储和计算仍成为瓶颈。许多 token 是冗余的，但现有方法依赖预定义规则（如 top-k 注意力分数）或启发式来识别重要 token，缺乏灵活性和自适应性。
- **背景**：神经架构搜索（NAS）中的 One-Shot 方法可以联合优化架构和权重。受此启发，NAtS 将 token 角色选择视为搜索问题，自动学习每个 token 应保留多久，从而实现端到端的稀疏注意力。

## 2. 论文提出的方法论
### 核心思想
- 为每个 token 分配三种角色（类型），通过可学习的注意力掩码联合优化 token 类型和模型权重，在保持性能的同时减少 KV 缓存。
### 关键技术细节
- **搜索空间设计**：三种 token 类型：
  - **Global Token**：永久保留，可被所有后续 token 查询。
  - **Local Token**：仅存活到下一个 Global Token 出现，用于局部子序列。
  - **Sliding Window Token**：仅对后续固定窗口大小 W 的 token 可见。
- **可学习注意力掩码**：使用 Gumbel-Softmax 技巧从离散搜索空间中采样 token 类型，并构造乘法注意力掩码 M（值 ∈ {0,1}），替代传统加法掩码。掩码构造规则：
  - Global: M_G(i,j) = 1（始终可见）
  - Sliding Window: M_SW(i,j) = 1 若 j ≤ i+W，否则 0
  - Local: M_L(i,j) = 1 若 j ≤ 下一个 Global Token 索引，否则 0
- **联合优化**：通过反向传播梯度更新 token 类型参数（线性映射层）和模型权重。引入正则化 λ 控制稀疏度，鼓励更多 token 变为 Sliding Window。
- **高效推理**：在预填充和解码阶段动态管理 KV 缓存：Global Tokens 永久保留，Local Tokens 在下一个 Global 出现后移除，Sliding Window Tokens 用队列仅保留最近 W 个。

## 3. 实验设计
- **从头训练**：GPT-2 small（128M 参数）在 PG-19 语言建模数据集上训练 600k 迭代，上下文长度 1024。对比方法：Full Attention（基线）、Streaming LLM、H2O。
- **微调大模型**：Llama-3.1-8B-Instruct 和 Mistral-7B-v0.3-Instruct，在 7000 实例的混合数据集（源于 LongBench 训练集 + Passkey Retrieval 合成数据，最大长度 16k）上微调 One Epoch。对比方法：Full Attention、DuoAttention、MoA、Streaming LLM、H2O、SnapKV、AdaKV、ChunkKV、PyramidKV、CriticalKV。
- **评测基准**：
  - **RULER**：合成基准，评估长上下文能力（4k-128k/32k 长度）。
  - **LongBench**：真实长上下文任务（单/多文档 QA、摘要、少样本学习、代码补全等 18 个子集）。
- **延迟评估**：在单块 H100 PCIe GPU 上测试预填充和解码阶段的显存与延迟。

## 4. 资源与算力
- **从头训练**：4× Nvidia H100 PCIe GPU，约 16–18 小时。
- **微调大模型**：2× Nvidia H100 PCIe GPU，约 8 小时。
- **延迟/显存测试**：单块 Nvidia H100 PCIe GPU，模型以 Bfloat16 存储。
- **注**：文中明确给出了 GPU 型号、数量、训练时长，信息充分。

## 5. 实验数量与充分性
- **实验组数**：
  - PG-19 从头训练：5 个 λ 值（0, 1e-9, 5e-9, 1e-8, 1e-7），每个 3 个随机种子，对比 2 种基线方法。
  - RULER：两种模型（Llama-3.1、Mistral）× 两种预算（25%、50%），每个模型在不同上下文长度（4k-128k/32k）下评估，对比 10+ 种基线。
  - LongBench：两种模型 × 两种预算，每模型覆盖 18 个子任务，对比全部基线。
  - 消融实验：正则化 λ 的 6 个值、滑动窗口 W 的 4 个值，均在 LongBench 上进行。
- **充分性**：实验覆盖了从头训练和微调两种场景，多种预算比例，多种上下文长度，并与大量现有方法公平对比。消融研究验证了关键超参数的影响。实验设计较为充分，结果呈现了均值和标准差（如 Figure 3），但部分表格（如 RULER）未提供误差棒或多次运行结果，统计显著性略欠。

## 6. 主要结论与发现
- **性能保持**：NAtS 在显著减少 KV 缓存（例如仅保留 15–25% 缓存）时，在 RULER 和 LongBench 上仍能保持接近全注意力的性能，远超现有方法。
- **极端稀疏性依然有效**：在 PG-19 上，NAtS 仅用约 3% 的 KV 缓存（约 30 个 token）时，困惑度仍低于 H2O 在 12.5% 缓存下的表现。
- **端到端学习优势**：NAtS 自动学习 token 重要性，无需手工规则；联合优化 token 类型和模型权重，比基于启发式的方法更灵活。
- **延迟和显存效率**：NAtS 可将推理上下文长度扩展至全注意力的 3.5 倍（从 200k 到 700k），预填充速度提升约 3 倍，解码速度提升约 1.4 倍。

## 7. 优点
- **端到端可学习**：无需手工设计稀疏模式或注意力近似，直接从损失函数中学习 token 角色。
- **统一框架**：可同时用于从头训练和微调，适用性强。
- **搜索空间丰富**：包含多种现有稀疏注意力模式（如 StreamingLLM、Local、Sliding Window），可灵活组合。
- **高效实现**：基于 FlashAttention 集成，仅增加少量计算开销；运行时可动态管理 KV 缓存，减少存储和运算。
- **正则化可调**：通过单个参数 λ 精确控制稀疏度，便于平衡效率与性能。

## 8. 不足与局限
- **搜索空间限制**：仅支持列式（垂向）稀疏，未覆盖块稀疏或斜线稀疏模式（如 MInference 中常见的模式），可能限制表达力。
- **梯度近似**：因注意力掩码中零值导致梯度不稳定，文中采用了裁剪策略（Equation 16），可能引入近似误差。
- **实验统计性**：部分实验（如 RULER 表格）仅报告单次结果（fixed seed），未提供多次运行的置信区间或误差棒，结论的稳健性有待加强。
- **数据与语言局限**：微调训练集仅包含英文和中文，未测试其他语言或多模态场景。合成 Passkey 数据可能与实际分布有偏差。
- **计算资源依赖**：虽然推理高效，但训练/微调仍需多块高端 GPU，对资源有限的研究者门槛较高。
- **未讨论公平性/偏见**：未分析稀疏后对模型公平性、鲁棒性或有害输出的影响。

（完）
