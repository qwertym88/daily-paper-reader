---
title: "ESPFormer: Doubly-Stochastic Attention with Expected Sliced Transport Plans"
title_zh: ESPFormer：基于期望切片传输计划的双随机注意力
authors: "Ashkan Shahbazi, Elaheh Akbari, Darian Salehi, Xinran Liu, Navid NaderiAlizadeh, Soheil Kolouri"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Uq70mJuUB8"
tags: ["query:neural-arch"]
score: 7.0
evidence: 无需迭代归一化的高效双随机注意力机制
tldr: 针对自注意力过度集中导致信息流次优的问题，本文提出基于切片最优传输的双随机注意力机制ESPFormer。该方法利用期望切片传输计划直接强制双随机性，避免了传统Sinkhorn迭代的高计算成本。理论分析和实验表明，ESPFormer在保持注意力分布平衡的同时显著提升效率，并易于并行化。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-uq70mjuub8/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1758, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uq70mjuub8/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1775, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uq70mjuub8/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 820, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uq70mjuub8/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1118, \"height\": 749, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-uq70mjuub8/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 887, \"height\": 511, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1776, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 866, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 875, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1784, \"height\": 547, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1121, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 994, \"height\": 130, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 991, \"height\": 131, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 989, \"height\": 127, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 989, \"height\": 128, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 989, \"height\": 130, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 944, \"height\": 131, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-uq70mjuub8/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1038, \"height\": 130, \"label\": \"Table\"}]"
motivation: 现有双随机注意力依赖迭代Sinkhorn归一化，计算成本高，本文旨在设计无需迭代的高效双随机注意力。
method: 提出基于切片最优传输的期望传输计划，以完全并行方式强制注意力矩阵双随机性。
result: 消除了迭代归一化步骤，在保持注意力分布质量的同时大幅提升计算效率。
conclusion: 为Transformer提供了高效且结构化的注意力机制，促进了信息流动的平衡。
---

## Abstract
While self-attention has been instrumental in the success of Transformers, it can lead to over-concentration on a few tokens during training, resulting in suboptimal information flow. Enforcing doubly-stochastic constraints in attention matrices has been shown to improve structure and balance in attention distributions. However, existing methods rely on iterative Sinkhorn normalization, which is computationally costly. In this paper, we introduce a novel, fully parallelizable doubly-stochastic attention mechanism based on sliced optimal transport, leveraging Expected Sliced Transport Plans (ESP). Unlike prior approaches, our method enforces doubly stochasticity without iterative Sinkhorn normalization, significantly enhancing efficiency. To ensure differentiability, we incorporate a temperature-based soft sorting technique, enabling seamless integration into deep learning models. Experiments across multiple benchmark datasets, including image classification, point cloud classification, sentiment analysis, and neural machine translation, demonstrate that our enhanced attention regularization consistently improves performance across diverse applications. Our implementation code can be found at \url{https://github.com/dariansal/ESPFormer}.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：标准 Transformer 的自注意力机制通过 softmax 产生**行随机**注意力矩阵，容易导致注意力过度集中在少数 token 上，使信息流不平衡，影响模型表达能力。
- **已有的解决方案**：强制注意力矩阵满足**双随机**（行和列和均为1）可以改善分布平衡性，但现有方法（如 Sinkformer）依赖**迭代 Sinkhorn 归一化**，计算复杂度高（O(S·N²)），且难以并行化。
- **研究动机**：设计一种无需迭代、可完全并行化的双随机注意力机制，在保证注意力平衡的同时大幅提升计算效率，并保持可微分以兼容深度学习训练。
- **整体含义**：通过引入**切片最优传输（Sliced Optimal Transport）** 和**期望切片传输计划（Expected Sliced Transport Plan，ESP）**，首次建立了从一维最优传输到注意力矩阵的高效桥梁，为 Transformer 提供了一种结构化、可扩展的注意力正则化方法。

### 2. 论文提出的方法论

- **核心思想**：将查询（Q）和键（K）视为均匀离散概率分布，利用 ESP 框架直接构造一个双随机的传输计划（transport plan）作为注意力矩阵，从而避免迭代归一化。
- **关键技术细节**：
  - 使用**轴对齐切片**（即 Θ = Iₘ×ₘ，每个维度作为一个切片），不引入额外可学习参数。
  - 对每个切片，将 Q 和 K 投影到一维，使用 **SoftSort**（可微软排序）得到排序置换矩阵 A_l 和 B_l。
  - 计算每切片的传输计划：**U_l = (1/N) A_l^T B_l**。
  - 计算每切片的传输成本：**D_l = Σᵢⱼ ||q_i - k_j||² · [U_l]ᵢⱼ**。
  - 通过逆温度参数 τ 对各切片计划加权聚合：**G = Σ_l σ_l^τ U_l**，其中 σ_l^τ = softmax(-τ D_l)。
  - 最终注意力输出：**Attention(Q,K,V) = V G**。
- **算法流程**（文字说明）：
  1. 计算 Q、K、V 投影。
  2. 对每个维度 l（共 m 个切片）：
     - 用 SoftSort 对 Q 和 K 的第 l 行分别排序得到 A_l、B_l。
     - 计算传输计划 U_l 和成本 D_l。
  3. 用 softmax 计算权重 σ_l^τ，加权平均所有 U_l 得到 G。
  4. 返回 V G。
- **可微分性**：SoftSort 使用温度参数 t 实现连续松弛，使整个流程可端到端训练。训练时可退火温度至接近硬排序，推理时切换为硬排序以获得精确双随机矩阵，并降低复杂度至 O(m N log N)。
- **复杂度**：训练时 O(m N (N+d))，可并行；推理时使用硬排序可降至 O(m N log N)，优于 Sinkformer 的 O((S+m)N²)。

### 3. 实验设计

- **使用数据集与场景**：
  - **图像分类**：Cats vs. Dogs（Kaggle，使用不同比例训练数据 1%/10%/25%/100%）、MNIST（研究 patch size 影响）。
  - **点云分类**：ModelNet40（40 类 3D 物体）。
  - **情感分析**：IMDB（电影评论）、TweetEval（推文）。
  - **神经机器翻译**：IWSLT’14（德英翻译）。
- **Benchmark**：对比方法包括 **Vanilla Transformer**、**Sinkformer**（迭代 Sinkhorn 归一化）、**DiffTransformer**（差分注意力）。在 ModelNet40 上还对比了 Set Transformer 和 Point Cloud Transformer 架构。
- **评估指标**：分类准确率（Accuracy）、BLEU 分数（机器翻译）。

### 4. 资源与算力

- **论文未明确说明**所用的 GPU 型号、数量、具体训练时长。只在附录中给出了部分超参数（如学习率、批次大小等），但未提及硬件配置。

### 5. 实验数量与充分性

- **实验数量**：涵盖四大类任务共 7 个数据集/场景。每项实验均报告多次运行（通常 3~4 次）的平均值、标准差或最佳/中位/最差值，统计可靠。
- **消融实验**：
  - 切片类型（可学习、冻结、轴对齐）对精度的影响（表 6）。
  - 切片数 L 和逆温度 τ 的敏感性。
  - 软排序温度退火后切换硬排序的增益（表 1）。
  - 即插即用（Plug-and-Play）与微调（Fine-Tune Boost）效果（表 5）。
- **充分性与公平性**：
  - 所有对比方法使用相同架构与超参数（除注意力机制外）。
  - 在 Cats vs. Dogs 上使用相同随机种子和数据子集，确保比较公平。
  - 在机器翻译中，先在相同条件下预训练基线，再替换注意力模块进行微调，避免预训练偏差。
  - **结论**：实验设计充分、客观，验证了方法的有效性。

### 6. 论文的主要结论与发现

- **主要结论**：
  - ESPFormer 在**所有任务上一致优于或持平** Vanilla Transformer、Sinkformer、DiffTransformer，尤其在**数据稀缺**场景（如仅 1% 训练数据）下优势显著（Cats vs. Dogs 上比 Transformer 高约 6%）。
  - 计算效率：ESPFormer 的软排序版本在序列长度较大时（N≥500）显著快于 Sinkformer（S>3 的迭代数），硬排序版本在所有长度下均最快。
  - **即插即用**：在预训练 Transformer 中替换注意力模块并微调少量 epoch，即可获得性能提升（机器翻译 BLEU 提高 0.2~0.3 点）。
  - **兼容性**：可无缝集成到差分注意力（DiffTransformer）中进一步改善性能。
  - **硬排序转换**：通过温度退火 + 推理时硬排序，可得到精确双随机矩阵，降低推理复杂度并小幅提升精度。

### 7. 优点

1. **高效性**：无需迭代 Sinkhorn，完全可并行化，训练和推理效率均优于 Sinkformer。
2. **可微性**：利用 SoftSort 实现端到端训练，且可通过温度退火自然过渡到硬排序。
3. **无额外参数**：轴对齐切片避免了引入可学习切片方向参数，与基线公平对比。
4. **即插即用**：可轻松替换现有 Transformer 中的注意力模块，只需少量微调即可提升性能。
5. **广泛适用性**：在图像、点云、文本、翻译任务上均验证有效，并兼容差分注意力架构。
6. **理论联系**：通过最优传输理论为注意力提供结构化解释，开辟了新研究方向。

### 8. 不足与局限

1. **不兼容因果注意力**：由于要求同时满足下三角性和双随机性会退化为恒等映射，因此不适用于**自回归 Transformer**（如 GPT 类架构），限制了在语言生成任务中的应用。
2. **内存开销**：训练时需要为每个切片存储置换矩阵（大小为 N×N），内存占用与切片数 m 线性增长，可能限制在极大模型或极长序列上的使用（推理时可通过硬排序丢弃这些矩阵）。
3. **未报告计算资源**：缺乏 GPU 型号、数量、训练时长的详细信息，不利于复现和评估实际成本。
4. **规模验证不足**：实验主要在中等规模数据集上（ModelNet40、IMDB、IWSLT’14），未在超大规模（如 ImageNet-1K/21K、WMT 大语种）或超长序列（如文档级别）上验证，泛化性有待进一步确认。
5. **切片方向选择**：虽然轴对齐切片简单有效，但理论上最优切片方向可能随数据变化，方法未提供自适应选择策略（消融显示可学习切片在较少切片数时略优，但增加参数）。

（完）
