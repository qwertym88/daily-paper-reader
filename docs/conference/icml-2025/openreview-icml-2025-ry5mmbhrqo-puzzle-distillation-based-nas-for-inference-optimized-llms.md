---
title: "Puzzle: Distillation-Based NAS for Inference-Optimized LLMs"
title_zh: Puzzle：面向推理优化的LLM蒸馏NAS框架
authors: "Akhiad Bercovich, Tomer Ronen, Talor Abramovich, Nir Ailon, Nave Assaf, Mohammed Dabbah, Ido Galil, Amnon Geifman, Yonatan Geifman, Izhak Golan, Netanel Haber, Ehud Dov Karpas, Roi Koren, Itay Levy, Pavlo Molchanov, Shahar Mor, Zach Moshe, Najeeb Nabwani, Omri Puny, Ran Rubin, Itamar Schen, Ido Shahaf, Oren Tropp, Omer Ullman Argov, Ran Zilberstein, Ran El-Yaniv"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=RY5MMBHRqo"
tags: ["query:neural-arch"]
score: 9.0
evidence: 结合知识蒸馏的硬件感知NAS，优化大语言模型推理
tldr: 针对大语言模型推理成本高的问题，本文提出Puzzle框架，通过大规模NAS结合块级知识蒸馏和混合整数规划，在数十亿参数模型上自动搜索最优结构。生成的Llama-3.1-Nemotron-51B-Instruct在保持性能的同时显著加速推理。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1328, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 842, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 304, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 692, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 863, \"height\": 255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 835, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ry5mmbhrqo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 865, \"height\": 454, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 882, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 708, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 783, \"height\": 116, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1782, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 883, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 860, \"height\": 152, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 859, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 866, \"height\": 131, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 855, \"height\": 160, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 858, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 859, \"height\": 153, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 860, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 869, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 863, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 862, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ry5mmbhrqo/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1782, \"height\": 481, \"label\": \"Table\"}]"
motivation: 大模型参数增加提升能力但加剧推断成本。
method: 采用块级本地知识蒸馏进行并行架构探索，结合混合整数规划约束优化。
result: 生成Nemotron-51B模型，在推理速度大幅提升的同时保持原有能力。
conclusion: NAS结合蒸馏能有效优化大模型推理，兼顾速度和性能。
---

## Abstract
Large language models (LLMs) offer remarkable capabilities, yet their high inference costs restrict wider adoption.
While increasing parameter counts improves accuracy, it also broadens the gap between state-of-the-art capabilities and practical deployability. We present **Puzzle**, a hardware-aware framework that accelerates the inference of LLMs while preserving their capabilities.
Using neural architecture search (NAS) at a large-scale, Puzzle optimizes models with tens of billions of parameters.
Our approach utilizes blockwise local knowledge distillation (BLD) for parallel architecture exploration and employs mixed-integer programming for precise constraint optimization.

We showcase our framework’s impact via Llama-3.1-Nemotron-51B-Instruct (Nemotron-51B) and Llama-3.3-Nemotron-49B, two publicly available models derived from Llama-70B-Instruct. Both models achieve a 2.17x inference throughput speedup, fitting on a single NVIDIA H100 GPU while retaining 98.4% of the original model's benchmark accuracies. 
These are the most accurate models supporting single H100 GPU inference with large batch sizes, despite training on 45B tokens at most, far fewer than the 15T used to train Llama-70B.
Lastly, we show that lightweight alignment on these derived models allows them to surpass the parent model in specific capabilities.
Our work establishes that powerful LLM models can be optimized for efficient deployment with only negligible loss in quality, underscoring that inference performance, not parameter count alone, should guide model selection.

---

## 论文详细总结（自动生成）

# Puzzle：面向推理优化的大语言模型蒸馏NAS框架

## 核心问题与整体含义

- **研究动机**：大语言模型（LLM）参数规模持续增长，虽然提升了能力，但推理成本急剧上升，阻碍了广泛部署。现有方法（如直接训练小模型、全局知识蒸馏）难以在保持性能的同时高效探索庞大架构空间。
- **核心问题**：如何在保留已有大模型（如Llama-70B）知识的前提下，通过神经网络架构搜索（NAS）自动设计出硬件感知、推理高效的子模型，实现吞吐量与精度的帕累托最优。
- **整体含义**：提出Puzzle框架，首次将分解式NAS成功应用于数十亿参数的LLM，证明通过局部蒸馏与混合整数规划结合，可以在极低训练成本下（相比预训练）获得几乎不损失性能的高效模型，从而改变“模型选择唯参数论”的现状。

## 方法论

- **核心思想**：三阶段流水线（见图1）：
  1. **块库构建（Block Library）**：针对父模型的每一Transformer层，生成多种替代“子块”选项（如不同KV头数的GQA、不同中间维度FFN、线性层、甚至跳过操作）。通过**解耦块级局部蒸馏（Decoupled BLD）**并行训练每个子块（注意力子块与FFN子块独立训练后组合），形成质量分数与硬件成本已知的“拼图块”库。
  2. **架构搜索（MIP）**：将选择问题建模为混合整数线性规划（MIP），以最大化全局质量分数（如KL散度得分之和）为目标，受内存、吞吐量、延迟等硬件约束。搜索空间达10^138量级，但MIP可在秒级求解。
  3. **全局知识蒸馏（GKD）**：对搜索出的异构模型进行端到端训练，使用余弦相似度+KL散度损失（不包含语言建模损失），让子模型对齐父模型输出，弥补块间累积误差。

- **关键技术细节**：
  - 解耦BLD：训练注意力变体时冻结FFN（父版本），训练FFN变体时冻结注意力；训练后组合成全块，将组合数从$m \times n$降至$m+n$。
  - 评分指标：使用KL散度作为替换单块的质量度量，比LM loss或下游准确率更优。
  - 计算资源消耗直接测量：对每个块变体在目标硬件上测量不同批次大小、序列长度下的预填充和生成延迟，作为MIP约束。
  - 搜索后还可加入“多样性约束”生成多种架构。

## 实验设计

- **主要实验**：
  1. **主模型**：以Llama-3.1-70B-Instruct为父模型，通过Puzzle生成Nemotron-51B（约51B参数）和Nemotron-49B。目标：单张NVIDIA H100 GPU，FP8量化，大批次推理。
  2. **基准测试**：
     - 准确率：Winogrande、ARC、MMLU、HellaSwag、GSM8K、TruthfulQA、MT-Bench、HumanEval等。
     - 吞吐量：不同输入/输出长度下的tokens/s（使用TensorRT-LLM，FP8）。
     - 长上下文：RULER benchmark（4K~128K）。
  3. **消融与对比**：
     - 对比方法：Wanda（结构化稀疏）、低秩近似、贪心搜索、随机搜索。
     - 消融：耦合vs解耦BLD、数据集组成（Distillation Mix vs Project Gutenberg）、BLD token预算、评分指标（LM loss vs KL vs 下游准确率）、搜索空间限制（仅no-op）、后训练损失组合等。
  4. **额外衍生产品**：针对Llama-3.1-8B-Instruct生成RTX 4090优化模型；针对Llama-3.1-405B生成253B模型。

- **数据集**：
  - 蒸馏混合数据集：224B tokens，来自FineWeb、Dolma、Buzz-V1.2。
  - BLD阶段使用1B tokens（也可用0.25B~1B消融）。
  - GKD阶段使用45B tokens（主实验），消融中测试3.7B、8.68B等更小预算。

- **公平性**：对比方法在类似吞吐量约束下比较；使用相同推理引擎（TensorRT-LLM）和硬件；人类盲评确认性能接近。

## 资源与算力

- **GPU型号**：NVIDIA H100 SXM（主实验），RTX 4090（8B衍生模型）。
- **训练成本**：
  - 父模型Llama-70B预训练需15T tokens。
  - Puzzle的BLD+GKD合计最多45B tokens（主模型），消融显示3.7B即可恢复98.8%准确率。
  - 长上下文扩展（Nemotron-49B）额外10B tokens。
  - 整体训练量远低于从头训练，但具体GPU型号、数量未明确给出（论文提及“利用管道并行在多个GPU上训练块”，但无精确计数）。
- **推理成本**：优化后的模型在单张H100上即可运行大批次，而父模型需4张（TP=4）。

## 实验数量与充分性

- **实验数量**：非常充分。包含：
  - 主模型的多基准准确率、吞吐量对比（表1、表2）。
  - 人类评估（图4）。
  - 长上下文RULER结果（表3、表19）。
  - 对齐效果（表4）。
  - 8B衍生模型对比（表5）。
  - 多种消融实验（附录F）：
    - 耦合vs解耦BLD（表8）
    - 数据集组成（表9）
    - BLD token预算（表10）
    - 评分指标（图7、表11）
    - 搜索空间多样性（表12）
    - 搜索算法（贪心vs MIP，表13；随机基线，表15）
    - 参数最大化（表14）
    - GKD损失组合（表17）
  - 与Wanda、低秩对比（表18）。
  - 小型预算准确率恢复（表6）。
- **充分性与公平性**：较多实验设计考虑控制变量，对比方法在类似约束下运行。不足：与更前沿的NAS方法（如更复杂的搜索策略）对比略少，但已有基线足够说明优势。所有实验基于公开或自研数据集，推理测量在统一硬件与引擎上进行。

## 主要结论与发现

- **Puzzle能高效生成硬件感知的LLM子模型**：以极低训练成本（<50B tokens，相比预训练的15T）获得吞吐量2.17x提升，同时保留98.4%准确率，部分任务甚至超越父模型。
- **解耦BLD显著降低块库构建开销**，且性能接近耦合版本；结合耦合BLD可进一步提升。
- **KL散度作为评分指标最佳**，优于LM loss和下游准确率。
- **FFN层比注意力层更重要**：即使在严格吞吐约束下，MIP也不会跳过FFN，而注意力可被替换或跳过。
- **全局优化（MIP）远胜贪心局部选择**，表明块间联合决策至关重要。
- **数据多样化有助于鲁棒性**，但即使在窄域数据（Project Gutenberg）上也能保持93%性能。
- **后续对齐（RLHF）可进一步提升子模型能力**，甚至超过父模型（如MT-Bench）。
- **Puzzle具有通用性**：可应用于不同规模（8B、70B、405B）和不同硬件（H100、RTX 4090），并支持长上下文扩展。

## 优点

1. **方法创新**：首创将分解式NAS（blockwise distillation + MIP）扩展到数十亿参数LLM，解决了大规模搜索空间与高昂评估成本的冲突。
2. **效率卓越**：训练成本仅为父模型预训练的0.3%，却产出接近无损的高效模型，且一次块库构建可复用生成多种架构。
3. **硬件感知**：直接测量实际部署中的延迟、内存，而不是依赖FLOPs等理论指标，确保优化结果真实有效。
4. **充分实验验证**：多维度消融和对比实验，定量分析每个设计决策的影响，结果可重复性强。
5. **开源贡献**：提供了代码仓库，并发布了多个可直接使用的模型，促进社区应用。

## 不足与局限

1. **搜索空间限制**：当前仅考虑注意力KV头数变化、FFN中间维度裁剪、线性/跳过等选项，未纳入如滑动窗口注意力、状态空间模型、MoE等更丰富的结构。
2. **依赖父模型质量**：子模型性能受限于父模型上限，如果父模型本身存在偏差或错误，Puzzle无法纠正，只能保留。
3. **长上下文扩展尚不完善**：Nemotron-51B在64K+上下文准确率显著下降（表19），需额外长时间扩展训练才能恢复，而Nemotron-49B通过专门扩展后表现良好，说明框架本身未天然解决长上下文问题。
4. **硬件泛化性未充分验证**：虽然测试了H100和RTX 4090，但对更多GPU类型（如A100、AMD、手机端）的泛化能力未知。
5. **评价基准覆盖有限**：未包含代码生成、多模态、安全/偏见等更广泛能力的评估。
6. **训练数据依赖**：蒸馏数据虽公开，但质量与领域覆盖会影响最终性能；封闭数据场景（如仅使用Gutenberg）仍有显著下降（表9）。
7. **BLD阶段假设输入来自父模型**：导致块间不兼容，需后续GKD弥补；如果GKD预算极小，误差会累积。
8. **MIP求解的近似最优性**：虽然MIP能在秒级给出高质量解，但未保证全局最优解；论文未分析MIP解与真实最优解的差距。

（完）
