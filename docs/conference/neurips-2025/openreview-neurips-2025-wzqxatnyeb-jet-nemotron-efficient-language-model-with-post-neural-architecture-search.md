---
title: "Jet-Nemotron: Efficient Language Model with Post Neural Architecture Search"
title_zh: Jet-Nemotron：基于后神经架构搜索的高效语言模型
authors: "Yuxian Gu, Qinghao Hu, Haocheng Xi, Junyu Chen, Shang Yang, Song Han, Han Cai"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=WZQXaTNYEB"
tags: ["query:neural-arch"]
score: 9.0
evidence: 提出后神经架构搜索（PostNAS）用于高效模型设计
tldr: 语言模型架构搜索通常从头开始，成本高。本文提出后神经架构搜索（PostNAS），从预训练全注意力模型出发，冻结MLP权重，高效探索注意力块设计。生成的Jet-Nemotron混合架构在准确率上媲美全注意力模型，同时显著提升生成吞吐量。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-wzqxatnyeb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wzqxatnyeb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wzqxatnyeb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wzqxatnyeb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1310, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wzqxatnyeb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1301, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wzqxatnyeb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1316, \"height\": 357, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1363, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1426, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1454, \"height\": 776, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1428, \"height\": 667, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1431, \"height\": 703, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1078, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 927, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 992, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 708, \"height\": 671, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1086, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1470, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1206, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1432, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1379, \"height\": 668, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wzqxatnyeb/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1471, \"height\": 669, \"label\": \"Table\"}]"
motivation: 现有NAS从头训练成本高，难以高效探索注意力设计。
method: 提出PostNAS，从预训练模型出发，冻结MLP层，搜索注意力块结构。
result: Jet-Nemotron模型准确率与全注意力模型相当，吞吐量大幅提升。
conclusion: PostNAS实现了高效、硬件感知的注意力架构搜索。
---

## Abstract
We present Jet-Nemotron, a new family of hybrid-architecture language models, which matches or exceeds the accuracy of leading full-attention models while significantly improving generation throughput. Jet-Nemotron is developed using Post Neural Architecture Search (PostNAS), a novel neural architecture exploration pipeline that enables efficient model design. Unlike prior approaches, PostNAS begins with a pre-trained full-attention model and freezes its MLP weights, allowing efficient exploration of attention block designs. The pipeline includes four key components: (1) learning optimal full-attention layer placement and elimination, (2) linear attention block selection, (3) designing new attention blocks, and (4) performing hardware-aware hyperparameter search. Our Jet-Nemotron-2B model achieves comparable or superior accuracy to Qwen3, Qwen2.5, Gemma3, and Llama3.2 across a comprehensive suite of benchmarks while delivering up to 53.6× generation throughput speedup and 6.1× prefilling speedup. It also achieves higher accuracy on MMLU and MMLU-Pro than recent advanced MoE full-attention models, such as DeepSeek-V3-Small and Moonlight, despite their larger scale with 15B total and 2.2B activated parameters.

---

## 论文详细总结（自动生成）

# 论文总结：Jet-Nemotron: Efficient Language Model with Post Neural Architecture Search

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有大型语言模型（LLM）主要基于全注意力（full attention）机制，计算复杂度为 O(n²) 且生成时产生大量键值（KV）缓存，导致长上下文场景下推理效率极低。尽管已有高效线性注意力架构（如 Mamba2、RWKV7）和混合架构（如 Hymba、Zamba2）被提出，但其准确率仍显著落后于最先进的全注意力模型（如 Qwen3、Llama3.2），尤其在 MMLU、数学推理、检索、编程等复杂任务上。
- **整体含义**：本文试图在不牺牲准确率的前提下大幅提升生成吞吐量，提出了一种新的架构探索范式——后神经架构搜索（PostNAS），通过复用预训练全注意力模型来降低架构探索成本，最终推出 Jet-Nemotron 系列模型，使得高效模型在准确率上匹敌甚至超越同等规模的全注意力模型，同时实现数十倍的吞吐量提升。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
PostNAS 从一个预训练的全注意力模型出发，冻结其 MLP 权重，仅探索注意力模块的设计空间。通过粗到细的四步搜索，找到最优的注意力块组合和超参数配置。

### 关键技术细节（四步流程）

1. **全注意力层放置与消除（Step 1）**  
   - 构建一个“一次为所有”（once-for-all）超网络，在原模型基础上添加线性注意力路径，训练时随机采样子网络并使用特征蒸馏损失。
   - 训练后采用束搜索确定在给定约束（如保留 2 个全注意力层）下最优的层放置策略。
   - 发现：不同任务对注意力层的依赖不同（检索任务仅需少数层，MMLU 也如此），且放置策略显著优于均匀放置。

2. **线性注意力块选择（Step 2）**  
   - 在全注意力层放置固定后，评估多种线性注意力块（RWKV7、RetNet、Mamba2、GLA、Deltanet、Gated DeltaNet）的准确率和效率。
   - Gated DeltaNet 因其数据依赖门控和 Delta 规则两项机制在准确率上表现最佳，被选为基准。

3. **新注意力块设计（Step 3）**  
   - 提出 JetBlock：在 Gated DeltaNet 基础上引入动态卷积（Dynamic Convolution）。利用一个核生成器（kernel generator）根据输入特征动态生成卷积核，仅应用于值（V）令牌；去除查询（Q）和键（K）上的静态卷积。
   - JetBlock 相比 Gated DeltaNet 在数学、检索等任务上准确率更高，且效率相近。

4. **硬件感知架构搜索（Step 4）**  
   - 固定 KV 缓存大小，在键/值维度、注意力头数等超参数上进行网格搜索，以生成吞吐量为优化目标。
   - 发现：KV 缓存大小是影响生成吞吐量的最关键因素，而非参数量。搜索出的配置可在保持吞吐量不变的同时增加参数量以提升准确率。

## 3. 实验设计：数据集 / 场景、benchmark、对比方法

- **评估基准**：涵盖 6 大类任务：
  - 多任务语言理解：MMLU、MMLU-Pro
  - 数学推理：GSM8K、MATH、MathQA、GPQA
  - 常识推理：ARC-c、ARC-e、PIQA、WinoGrande、OBQA、BoolQ、TruthfulQA
  - 检索：FDA、SWDE、SQuAD
  - 编程：EvalPlus、CRUXEval（含 I-cot、O-cot）
  - 长上下文：LongBench（Few-Shot、Code、Sum、Single-Doc、Multi-Doc）
- **对比方法**：
  - 全注意力模型：Qwen2.5-1.5B、Qwen3-1.7B-Base、Llama3.2-3B、MiniCPM-2B-128K、Smollm2-1.7B、DeepSeek-V3-Small（MoE）、Moonlight（MoE）
  - 线性注意力模型：Mamba2-2.7B、RWKV7-1.5B、RecurrentGemma-2B
  - 混合模型：Gemma3n-E2B、Hymba-1.5B、Zamba2-1.2B、Falcon-H1
- **训练数据**：第一阶段使用 Nemotron-CC + Redstone-QA（50B tokens），第二阶段加入数学、编程高质量数据（共 350B tokens）。

## 4. 资源与算力

- **GPU 型号**：NVIDIA H100（DGX H100 服务器，8 卡）。
- **训练时长与 GPU 小时数**：
  - PostNAS 各步骤合计约 10,392 GPU hours（见表 10）。
  - 最终训练：阶段 1（50B tokens）624 GPU hours，阶段 2（350B tokens）7,536 GPU hours，总计约 **8,160 GPU hours**（32 卡并行）。
- **推理测试**：单卡 H100，上下文长度 64K（部分实验至 256K），使用 FlashAttention 和 Flash-Linear-Attention 库。

## 5. 实验数量与充分性

- **实验数量**：大量比较实验：
  - 表 3-6、表 14-16 给出了多个基准上的详细结果。
  - 图 3 展示了 PostNAS 各步骤的准确率提升消融。
  - 表 1 对比了 7 种线性注意力块。
  - 表 2 展示了硬件感知搜索的网格结果。
  - 图 6 给出了不同上下文长度下吞吐量加速比。
  - 附录中还包括不同硬件（Jetson Orin、RTX 3090）的对比、训练数据控制实验、与 Falcon-H1 的对比等。
- **充分性与公平性**：
  - 对比了同参数量级下的最先进模型，并报告了吞吐量（batch size 优化后）。
  - 进行了训练数据控制实验（表 12），排除数据差异影响。
  - 吞吐量测试使用统一环境（PyTorch 2.7.0, Triton 3.3.0, FlashAttention 2.7.4），并调整 chunk size 以最大化 batch size。
  - 实验覆盖了学术基准和长上下文场景，较为全面。

## 6. 论文的主要结论与发现

- **PostNAS 是一种高效的架构探索方法**：通过复用预训练模型冻结 MLP，显著降低架构搜索成本，且搜索出的设计直接迁移至最终模型。
- **非均匀全注意力层放置优于均匀放置**：不同任务依赖不同注意力层，自动搜索可提升准确率。
- **KV 缓存大小比参数量更影响生成吞吐**：硬件感知搜索可在不牺牲吞吐的前提下增加参数量提升准确率。
- **Jet-Nemotron-2B 和 4B 在多项基准上匹配或超越全注意力模型**：
  - MMLU-Pro 准确率高于 Qwen3-1.7B-Base，且吞吐量提升 47×（64K 上下文时）。
  - 在长上下文 256K 下，解码加速达 53.6×，预填充加速 6.14×。
  - 在数学、编程、检索等任务上显著优于其他高效模型（Mamba2、RWKV7、RecurrentGemma）。
- **动态卷积（JetBlock）优于静态卷积线性注意力**：提升数学和检索准确率，且开销可忽略。

## 7. 优点

- **方法学创新**：PostNAS 提出了一种低成本的架构探索范式，可应用于任何预训练 Transformer，降低了架构创新门槛。
- **硬件感知设计**：将实际推理吞吐量而不是参数量作为优化目标，更贴近部署需求。
- **实验全面且公平**：覆盖多种任务、对比多种模型、控制训练数据、公布详细资源消耗。
- **实际效率提升显著**：在保持高准确率的同时，长上下文吞吐量数倍至数十倍提升，有实用价值。
- **新增注意力块 JetBlock**：简单有效，可即插即用。

## 8. 不足与局限

- **架构依赖预训练起点**：PostNAS 搜索出的架构在从头训练时未必最优，论文也承认此局限。
- **训练成本仍然不低**：虽然相比从头训练已降低，但 PostNAS 各步骤仍需约 1 万 GPU hours，第二阶段训练另需 7500+ GPU hours，对资源要求仍较高。
- **线性注意力块选择缺乏理论分析**：仅凭实验选择 Gated DeltaNet，未深入分析其为何优于其他。
- **长上下文评估仅覆盖 64K/256K**：未测试更长上下文（如 1M）下的表现和稳定性。
- **缺少错误分析与鲁棒性讨论**：未评估模型对输入扰动的鲁棒性或 bias 风险。
- **代码与模型未开源**：论文称将在发表后开源，目前无法完全复现。

（完）
