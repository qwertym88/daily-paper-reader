---
title: "FFN Fusion: Rethinking Sequential Computation in Large Language Models"
title_zh: FFN融合：重新思考大型语言模型中的顺序计算
authors: "Akhiad Bercovich, Mohammed Dabbah, Omri Puny, Ido Galil, Amnon Geifman, Yonatan Geifman, Izhak Golan, Ehud Dov Karpas, Itay Levy, Zach Moshe, Najeeb Nabwani, Tomer Ronen, Itamar Schen, Ido Shahaf, Oren Tropp, Ran Zilberstein, Ran El-Yaniv"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=XUmGMBRv4M"
tags: ["query:neural-arch"]
score: 7.0
evidence: 通过FFN融合实现并行计算的架构优化
tldr: 针对大型语言模型中顺序计算导致的推理延迟问题，提出FFN融合技术，通过识别并融合可并行化的前馈网络层，将顺序计算转化为并行操作。在Llama-3.1-405B上应用后，模型参数从405B降至253B，推理速度显著提升且准确率基本保持不变。为LLM部署提供了一种有效的优化方法。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 740, \"height\": 894, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 476, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1167, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1063, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1164, \"height\": 1035, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1276, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1348, \"height\": 1013, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 745, \"height\": 778, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xumgmbrv4m/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1141, \"height\": 1109, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1374, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 660, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 598, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 728, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 588, \"height\": 467, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 586, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 590, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xumgmbrv4m/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 840, \"height\": 364, \"label\": \"Table\"}]"
motivation: LLM中顺序FFN层限制了推理并行性，增加延迟。
method: 开发识别和融合可并行化FFN序列的方法，转换为并行操作。
result: 在405B模型上创建253B高效模型，延迟降低且性能保持。
conclusion: FFN融合是优化LLM推理效率的有效手段。
---

## Abstract
We introduce \textit{FFN Fusion}, an architectural optimization technique that reduces sequential computation in large language models by identifying and exploiting natural opportunities for parallelization. Our key insight is that sequences of Feed-Forward Network (FFN) layers, particularly those remaining after the removal of specific attention layers, can often be parallelized with minimal accuracy impact. We develop a principled methodology for identifying and fusing such sequences, transforming them into parallel operations that significantly reduce inference latency while preserving model behavior. Applying these techniques to Llama-3.1-405B-Instruct, we create a 253B model (253B-Base), an efficient and soon-to-be publicly available model that achieves a 1.71$\times$ speedup in inference latency and 35$\times$ lower per-token cost while maintaining strong performance across benchmarks. Most intriguingly, we find that even full transformer blocks containing both attention and FFN layers can sometimes be parallelized, suggesting new directions for neural architecture design.

---

## 论文详细总结（自动生成）

以下是根据论文内容生成的中文总结：

---

## 论文核心问题与整体含义（研究动机和背景）

- 大型语言模型（LLM）在规模不断增长的同时，推理计算成本成为瓶颈。传统的顺序 Transformer 架构中，每个 Transformer 块包含注意力层和前馈网络（FFN）层，依次执行，导致推理延迟高。
- 已有优化方法如量化、剪枝、混合专家（MoE）各有局限：量化在低位宽时精度下降；剪枝难以找到额外冗余；MoE 在小批量下计算资源利用率低且同步开销大。
- 作者发现，在剪除部分注意力层后，模型会留下连续的长 FFN 序列，且这些 FFN 层之间依赖度很低，可以被并行化。据此提出 **FFN Fusion**，将顺序计算转化为并行，显著降低延迟并保持性能。

## 方法论：核心思想、关键技术细节

### 核心思想
- 利用 Puzzle 框架（一种基于蒸馏的神经架构搜索）先对预训练 LLM 进行注意力层剪枝，得到多个连续的 FFN-only 层序列。
- 将这些序列中的多个 FFN 层融合成一个更宽的 FFN 层，从而实现并行执行——所有被融合的 FFN 共享相同输入，输出求和，计算互相独立。
- 融合后的宽 FFN 在数学上等价于原多个 FFN 的求和（定理3.1），权重通过拼接获得（W1, W2 沿隐藏维拼接，W3 沿嵌入维拼接）。

### 关键技术细节
- **融合公式**：对于连续序列 `[FFN_i, ..., FFN_{i+c}]`，并行版本为 `X + Σ_{j=0}^{c} FFN_{i+j}(η2(X))`，其中η2取最后一个层的归一化。
- **效率动机**：在张量并行（TP）环境下，融合减少了同步点（all-reduce），并增大了每个 GPU 上矩阵乘法（GEMM）的尺寸，提高硬件利用率。
- **依赖度分析**：通过余弦距离衡量块之间依赖度，选择低依赖区域进行融合。实验表明，注意力移除区域呈现低依赖。
- **最终层敏感性**：每个 FFN 序列中的最后一个 FFN 对融合更敏感，通常跳过不融合以避免精度损失。

### 无额外公式或算法流程（文字说明已足够）

## 实验设计

### 数据集
- 蒸馏数据混合（Distillation Mix）：包含 FineWeb、Dolma、Buzz-V1.2 共 224B tokens。
- 额外生成数据：使用 Llama-405B 按 Magpie 方法生成合成数据，用于对齐。

### Benchmark 评测
- **知识/理解**：MMLU Instruct、MMLU-Pro
- **推理/编程**：HumanEval、MATH
- **对话/综合**：MT-Bench、Arena Hard（基于 GPT-4 评判）
- **长上下文**：RULER-128K

### 对比方法
- 原模型 Llama-3.1-405B-Instruct（父模型）
- 未融合的 253B 模型（Pre-Fusion）
- 去除 FFN 的基线（与融合对比）
- 不同融合强度/步骤的消融
- 在其他规模模型（70B、8B）上验证泛化性

## 资源与算力

- 论文未明确提及训练所使用的具体 GPU 数量和训练时长。
- 提及在单个 NVIDIA 8×H100 节点（640 GB 总显存）上进行推理延迟测试，训练过程使用相同架构。
- 对于 Ultra-253B-Base，知识蒸馏阶段使用 54B tokens（8k 上下文）+ 5B（16k）+ 5B（32k）+ 0.8B（128k），后续连续预训练（CPT）使用 73B tokens（8k）+ 15B（258k）。但未说明训练时并行策略（如 TP/PP 大小）和 GPU 数。

## 实验数量与充分性

- **主要实验组**：
  1. 405B 尺度下的完整流程（剪枝 + 融合 + 蒸馏 + 对齐），并对比延迟、吞吐、精度。
  2. 70B 模型上 4 步融合强度消融。
  3. 融合 vs. 去除 FFN 的对比（70B 规模）。
  4. 最终层敏感性分析（多种组合测试）。
  5. 额外模型泛化：Mistral Large 2 和 Llama-3.1-8B-Instruct。
  6. 融合可解释性实验（输入余弦距离、输出/输入比、逆序融合等）。
  7. 全块并行化的初步探索（附录 B）。

- **充分性判断**：实验设计较为全面，覆盖不同尺度、不同模型族、多种消融（融合程度、是否保留最终层、融合 vs. 删除），并且有额外训练恢复精度验证。但缺失与其他方法（如 MoE、量化）的直接公平对比；仅在性能曲线上与 Llama-70B 和原 405B 比较。整体充分但非穷尽。

## 主要结论与发现

- FFN Fusion 能有效降低推理延迟（405B→253B 模型 speedup 1.71×，per-token 成本降低 35×），同时精度基本保持，甚至超过父模型（如 Arena Hard 提升 12%）。
- 融合后经过蒸馏和额外连续预训练，模型性能可恢复甚至提升（尤其在长上下文任务上）。
- 连续 FFN 序列中的最终 FFN 对融合最为敏感，通常应排除在外。
- 融合后的模型在 TP 设置下因减少同步点和增大计算粒度，具有更好的硬件利用率。
- 初步发现：完整 Transformer 块（含注意力）有时也可并行化，但挑战更大，依赖度更高。

## 优点（方法或实验设计亮点）

- **创新性**：挑战了 Transformer 顺序执行的必要性，提出利用剪枝后自然形成的 FFN 序列进行并行融合，思路新颖。
- **理论支撑**：给出融合的数学等价性证明（定理3.1），操作简单可靠。
- **实用效果显著**：在业界最强模型 405B 上成功应用，产出 253B 高效模型，同时保持竞争力。
- **实验设计系统**：多尺度、多模型、多消融，并通过依赖度分析提供可解释性。
- **开源承诺**：模型将在接收后公开，促进可复现性。

## 不足与局限

- **适用前提**：FFN Fusion 依赖于先通过 Puzzle 等方式剪除部分注意力层以形成长 FFN 序列。对于原始未剪枝模型或注意力保留较多的模型，无法直接应用。
- **实验缺失**：未与 MoE 模型（如 DeepSeek-V3）或量化模型进行直接延迟-精度对比（仅泛化提及 MoE 在小批量下的劣势，未做实验）。
- **全块并行化探索有限**：仅做初步实验（仅 4 个块并行，且精度下降明显），缺乏实际性能评测和与 FFN Fusion 的结合可能性。
- **训练资源不透明**：未说明整体训练成本（GPU 小时数），不利于其他团队复现。
- **风险**：可能受限于特定剪枝框架（Puzzle），泛化性需进一步验证；模型释放后的安全性（safeguard）未讨论。
- **偏差**：未报告多次实验的误差棒，依赖单次结果；所有数据基于 NVIDIA GPU，其他硬件架构未测试。

---

（完）
