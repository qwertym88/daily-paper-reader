---
title: Searching Latent Program Spaces
title_zh: 搜索隐式程序空间
authors: "Matthew Macfarlane, Clément Bonnet"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=CsXKGIqZtr"
tags: ["query:neural-arch"]
score: 7.0
evidence: 内置测试时搜索的新型架构，提升泛化能力
tldr: 现有方法在泛化与搜索效率间难以平衡。本文提出隐式程序网络（LPN），将测试时搜索直接融入模型架构，学习隐式程序空间的神经映射。实验表明LPN在少样本学习和分布外泛化上显著优于传统方法，提供了一种可微的架构搜索新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1400, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 734, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 629, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1421, \"height\": 258, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1314, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 860, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1434, \"height\": 748, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1397, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1078, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1405, \"height\": 907, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1369, \"height\": 1492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1338, \"height\": 1414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1353, \"height\": 1468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1313, \"height\": 2251, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1372, \"height\": 1484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1384, \"height\": 1490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1068, \"height\": 1867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 722, \"height\": 1947, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1383, \"height\": 1101, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1027, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-csxkgiqztr/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1420, \"height\": 820, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1314, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 790, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 707, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1154, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1339, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 885, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 855, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 854, \"height\": 430, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 704, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 703, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 704, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 645, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1447, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1060, \"height\": 808, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1063, \"height\": 1031, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1064, \"height\": 1029, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1063, \"height\": 1025, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1062, \"height\": 1106, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1451, \"height\": 670, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1302, \"height\": 697, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-csxkgiqztr/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1366, \"height\": 700, \"label\": \"Table\"}]"
motivation: 程序合成泛化强但搜索空间大，深度学习缺乏结构化测试时适应。
method: 提出隐式程序网络（LPN），将测试时搜索嵌入神经模型中的隐式程序空间。
result: 在少样本和分布外泛化任务上显著优于基线。
conclusion: LPN提供了一种兼具泛化与效率的神经架构新方向。
---

## Abstract
General intelligence requires systems that acquire new skills efficiently and generalize beyond their training distributions.
Although program synthesis approaches have strong generalization power, they face scaling issues due to large combinatorial spaces that quickly make them impractical and require human-generated DSLs or pre-trained priors to narrow this search space.
On the other hand, deep learning methods have had high successes, but they lack structured test-time adaptation and rely on heavy stochastic sampling or expensive gradient updates for fine-tuning.
In this work, we propose the Latent Program Network (LPN), a new architecture that builds in test-time search directly into neural models.
LPN learns a latent space of implicit programs---neurally mapping inputs to outputs---through which it can search using gradients at test time.
LPN combines the adaptability of symbolic approaches and the scalability of neural methods.
It searches through a compact latent space at test time and bypasses the need for pre-defined domain-specific languages.
On a range of programming-by-examples tasks, LPN either outperforms or matches performance compared to in-context learning and test-time training methods.
Tested on the ARC-AGI benchmark, we demonstrate that LPN can both learn a compact program space and search through it at test time to adapt to novel tasks.
LPN doubles its performance on out-of-distribution tasks when test-time search is switched on.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：通用人工智能需要高效获取新技能并泛化到训练分布之外。程序合成方法泛化能力强，但面临巨大组合搜索空间，往往依赖人工设计的领域特定语言（DSL）或预训练先验来缩小搜索空间，导致可扩展性差。深度学习方法虽然成功，但缺乏结构化的测试时适应能力，要么依赖大量随机采样，要么依赖昂贵的梯度更新进行微调。
- **研究意义**：现有方法在泛化性与搜索效率之间存在矛盾。本文旨在融合符号方法的适应性与神经方法的可扩展性，提出一种**将测试时搜索直接嵌入神经网络架构**的新范式。

## 2. 方法论

### 核心思想
- **Latent Program Network (LPN)**：学习一个连续的隐式程序空间，将输入输出对映射为隐式表示，并通过梯度搜索在测试时调整该隐式表示，以更好地拟合新任务的规范，从而绕过对人工DSL的需求。

### 关键技术细节
1. **编码器**：将每个输入输出对 `(x, y)` 映射到隐式空间的分布 `q_ϕ(z|x,y)` （高斯分布，输出均值和协方差）。
2. **解码器**：给定隐式变量 `z` 和输入 `x`，预测输出 `y` 的概率 `p_θ(y|x,z)`（逐像素预测）。
3. **隐式优化**：在测试时，从编码器初始隐式 `z` 出发，通过梯度上升最大化规范中所有给定对的似然和：
   ```
   z' = z + α · ∇_z Σ_i log p_θ(y_i | x_i, z)
   ```
   可进行多步迭代。
4. **训练**：采用留一法（Leave-One-Out）损失：对于每个对 `(x_i, y_i)`，用其他 `n-1` 个对编码并优化隐式，再解码 `y_i` 并计算交叉熵损失，同时加上KL散度正则项 `β · KL(q_ϕ || N(0,I))`。训练时可选择是否将梯度流经隐式更新（stop-gradient可提升效率）。

### 算法流程（文字描述）
- **测试时推理**：对给定n个输入输出对，编码器各自采样隐式，取均值初始化；然后迭代K步梯度上升更新隐式；最后用更新后的隐式解码新输入的输出。
- **训练**：批量采样任务，对每个任务中的每个对，用其余对编码并优化隐式，然后计算该对的解码损失和KL损失，反向传播更新编码器和解码器参数。

## 3. 实验设计

### 数据集与场景
- **Pattern Task**：简化的10×10网格任务，输入为全黑网格加一个蓝色标记点，输出为粘贴一个4×4的程序特定图案。用于分析LPN内部动态和OOD泛化。
- **String Manipulation Task**：合成序列任务，包含超过1亿个唯一程序（由3-5个参数化规则组合），用于验证无空间结构下的泛化。
- **ARC-AGI (2024)**：抽象与推理语料库，评估在分布外任务上的技能获取效率。训练使用re-arc数据集（与ARC训练集同分布），评估集为显著OOD的hidden测试集。

### 对比基线
- **In-Context Learning**：直接编码所有输入输出对并拼接，然后解码新输出，无中间程序表示。
- **Test-Time Training (TTT)**：在测试时对模型全部参数进行梯度微调。
- **CodeIt**：基于预训练CodeT5的离散程序搜索方法。
- **Mirchandani et al.**：使用text-davinci-003（175B参数）的LLM方法。

### 评估指标
- Exact match accuracy（精确匹配准确率），ARC-AGI使用top-2准确率（标准做法）。

## 4. 资源与算力

- **ARC-AGI实验**：训练一个178M参数的LPN（编码器8层、解码器6层，隐式维度256），在**TPU v4-32**上训练2天，共100k步（其中前95k步无隐式梯度，后5k步使用1步梯度微调），批量大小256，总处理约5100万输入输出对。
- **其他实验**：Pattern任务和字符串任务在较小模型（约1M参数）上训练20k步（模式任务）或更少，未明确说明GPU/TPU型号，但可推断在普通GPU或TPU上完成。
- **算力对比**：文中给出不同FLOPs下的性能对比（表4），LPN在2E+11到2E+15 FLOPs区间内测试。

## 5. 实验数量与充分性

- **实验数量**：包含4大类实验（Pattern、String、OOD、ARC-AGI）及大量消融。主要消融包括：
  - 不同训练策略（Grad 0/1/5、Sampling）与不同推理策略（Grad步数、采样）的组合（表1、表5）。
  - 编码器初始化 vs 先验初始化的作用（图2）。
  - OOD泛化（表3、表6）：弱OOD和强OOD。
  - 规格大小（specification size）从1到19的扩展（图3、表7-9）。
  - ARC-AGI上与TTT、CodeIt、Mirchandani的对比（表4）。
  - 隐式空间的t-SNE可视化（图19）。
  - 组合泛化定性分析（图17-18）。
- **充分性与公平性**：
  - 多数实验使用3个随机种子并报告均值和标准差。
  - 基线超参数分别调优（如TTT学习率搜索），确保公平。
  - 对比方法使用了相同或相近的模型容量和训练数据。

## 6. 主要结论与发现

1. **LPN能够通过测试时隐式空间搜索显著提升性能**：在Pattern任务上，仅使用编码器预测（无搜索）准确率仅3.2%，使用100步梯度搜索后达67.5%；若训练时也融入1步梯度（Grad 1），测试时100步搜索可达99.5%。
2. **训练时加入隐式梯度信号至关重要**：使用1步梯度训练比无梯度训练在测试时搜索中性能提升显著（Pattern OOD：88% vs 41%）。
3. **梯度搜索远优于随机采样**：采样250个隐式仅得3.2%，而100步梯度可达67.5%。
4. **编码器初始化对搜索效率至关重要**：从编码器初始化的搜索性能远优于从先验初始化（图2）。
5. **LPN平滑泛化到未见过规格大小**：与ICL和TTT不同，LPN在不同规格大小下保持稳定甚至提升（图3）。
6. **在ARC-AGI上，LPN通过测试时搜索使OOD性能翻倍**（从7.75%到15.5%），在较低FLOPs下优于TTT，但最终TTT在高FLOPs下略优，推测因LPN训练程序多样性有限。
7. **LPN具备一定的组合泛化能力**：隐式搜索可以组合训练中分别见过的操作（如边界框提取+颜色替换），但不够鲁棒（如三操作组合失败）。

## 7. 优点

- **新颖融合**：将符号方法的系统搜索与神经方法的可扩展性统一在连续隐式空间中，无需人工DSL。
- **高效的测试时适应**：仅更新隐式变量（低维），避免全参数微调，计算成本远低于TTT。
- **强泛化性**：在OOD任务和大规格变化下仍能持续提升，展现出对训练分布外任务的良好适应。
- **结构化的隐式空间**：t-SNE可视化显示同类程序在隐式空间聚类，隐式遍历可生成平滑变化的输出。
- **实验全面**：涵盖从简单模式到复杂ARC-AGI的多个层次，消融充分。

## 8. 不足与局限

- **训练程序多样性有限**：仅在re-arc数据集上训练，缺乏LLM和大型预训练模型的先验知识，导致隐式空间的表现力受限，在ARC-AGI上性能低于o3等超大规模方法。
- **梯度搜索可能陷入局部最优**：特别是当初始隐式质量差时，优化可能收敛到次优解。
- **组合泛化不鲁棒**：仅对简单组合有效，复杂组合常失败，离真正系统组合推理仍有差距。
- **计算资源不透明**：Pattern等实验未说明具体GPU型号和训练时长，可重复性信息不足。
- **评估局限**：ARC-AGI的OOD测试集规模有限（400个公开任务），结果可能存在偏差；未在更多元化benchmark（如编程语言合成）上验证。
- **缺乏与最先进LLM的公平对比**：虽然算力低于o3等，但数据集、模型规模和训练策略差异大，不能完全说明方法优越性。

（完）
