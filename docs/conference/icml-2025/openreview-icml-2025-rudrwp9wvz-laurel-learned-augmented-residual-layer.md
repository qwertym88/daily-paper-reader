---
title: "LAuReL: Learned Augmented Residual Layer"
title_zh: LAuReL：学习增强残差层
authors: "Gaurav Menghani, Ravi Kumar, Sanjiv Kumar"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=rUDRWP9WvZ"
tags: ["query:neural-arch"]
score: 9.0
evidence: 泛化跳跃连接的新型可学习残差连接
tldr: 针对标准残差连接性能进一步提升空间有限的问题，本文提出学习增强残差层（LAuReL），作为残差连接的泛化形式。LAuReL可作为即插即用模块替换现有残差连接，在增加极少参数的情况下提升模型质量，同时降低延迟和内存占用。在视觉和语言模型上的实验表明，LAuReL在多个指标上优于标准残差连接。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-rudrwp9wvz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 675, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rudrwp9wvz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rudrwp9wvz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 765, \"height\": 544, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-rudrwp9wvz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 420, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rudrwp9wvz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 843, \"height\": 874, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rudrwp9wvz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 815, \"height\": 908, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rudrwp9wvz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 897, \"height\": 349, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rudrwp9wvz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 879, \"height\": 506, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rudrwp9wvz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 808, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rudrwp9wvz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1883, \"height\": 497, \"label\": \"Table\"}]"
motivation: 残差连接虽有效，但仍有改进余地，本文希望设计一种更强的可学习残差连接替代方案。
method: 提出一种可学习的残差连接泛化，通过小规模参数增强残差路径以提升信息流。
result: 在视觉和语言模型上，LAuReL以更少参数和更低开销实现了比标准残差连接更好的质量。
conclusion: 为深层网络提供了一种更优的残差连接方案，有望广泛替代现有设计。
---

## Abstract
One of the core pillars of efficient deep learning methods are architectural improvements, such as residual/skip connections, which have led to significantly better model convergence and quality. Since their introduction, residual connections have become ubiquitous not only in convolutional neural networks but also in transformer-based architectures, the backbone of LLMs.

In this paper, we introduce the Learned Augmented Residual Layer (LAuReL) --- a novel generalization of the canonical residual connection --- designed to serve as an in-situ replacement while outperforming it in both model quality and footprint metrics.  Our experiments show that LAuReL can enhance quality for both vision and language models while adding fewer parameters and incurring less latency and memory overhead than naively increasing parameter count.

For example, on the ImageNet-1K task, LAuReL achieves the same model quality improvements as naively adding an extra layer while using $2.6 \times$ fewer parameters. Similarly, when pre-training 1B and 4B parameter LLMs, LAuReL improves performance on a variety of challenging downstream evaluation tasks by 2.54\% to 20.05\%, while adding only 0.012\% and 0.1\% additional parameters, respectively.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：残差连接（Residual/Skip Connection）是高效深度学习的关键架构创新，显著改善了模型收敛与质量，广泛应用于 CNN 和 Transformer（包括 LLM）。然而，标准残差连接 `x_{i+1} = f(x_i) + x_i` 仅为简单的恒等跳跃，仍有进一步提升空间。
- **动机**：作者受“残差流”（Residual Stream）概念启发，认为残差路径可以承载更丰富的线性信息。因此提出一种可学习的泛化形式，在不显著增加参数和延迟的前提下，提升模型质量与效率。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：将标准残差连接推广为：
  \[
  x_{i+1} = \alpha \cdot f(x_i) + g(x_i, x_{i-1}, \ldots, x_0)
  \]
  其中 \(\alpha\) 是可学习标量，\(g\) 是学习到的线性函数，可考虑多个历史输入。

- **三种变体（可混合组合）**：
  1. **LAuReL-RW（残差权重）**：`x_{i+1} = \alpha f(x_i) + \beta x_i`（\(\alpha,\beta\) 用 softmax/sigmoid 归一化），仅增加 1–2 个参数。
  2. **LAuReL-LR（低秩）**：`x_{i+1} = f(x_i) + (BA + I)x_i`，其中 \(A \in \mathbb{R}^{D\times r}, B \in \mathbb{R}^{r\times D}, r\ll D\)，增加 \(2rD\) 参数。
  3. **LAuReL-PA（历史激活）**：使用前 \(k\) 个历史激活，加权并经过低秩映射后再累加，增加 \(2rkD + k\) 参数。
  4. **组合变体**：如 RW+LR、RW+LR+PA 等，可灵活混用。

- **轻量设计**：通过标量学习或低秩分解，确保新增参数极少（如 LLM-1B 仅增加 0.012% 参数），且不影响训练稳定性。

## 3. 实验设计

- **视觉任务**：
  - 数据集：ImageNet-1K（分类）。
  - 模型：ResNet-50。
  - 基准：标准 ResNet-50 + 数据增强，额外对比“加一层”的朴素缩放（Naive Scaling）。
  - 评估指标：Top-1 准确率（5 次平均）。

- **语言任务**：
  - 两个自训练的 LLM：
    - **LLM-1B**：1B 参数 decoder-only Transformer，仅文本预训练（约 0.5T tokens）。
    - **LLM-4B**：4B 参数 decoder-only Transformer，多模态+多语言预训练（约 0.5T tokens）。
  - 评估任务多样：MATH、GSM8K、MMLU、BoolQ、HellaSwag、HumanEval、MBPP、翻译（WMT23）、多模态（MMMU、COCO Caption、DocVQA、TextVQA）等。
  - 对比方法：同结构无 LAuReL 的基线模型，以及增加一层（Naive Scaling）的模型。

- **消融实验**：
  - 在 C4 语料库（~10B tokens）上训练小 LLM（24 层 vs 28 层），比较所有 LAuReL 变体在参数量、测试损失、峰值内存、步时间上的表现（见表 5）。
  - 对 LAuReL-LR 中的秩 r 取不同值（4,8,16,32,64,128）测试准确率趋势（图 3）。

## 4. 资源与算力

- **ResNet-50/ImageNet**：使用 **16 块 Google Cloud TPU v5e**，训练 1 个 epoch。
- **LLM-1B**：使用 **256 块 Google Cloud TPU v5e**，训练约 **2 周**。
- **LLM-4B**：使用 **1024 块 Google Cloud TPU v4**，训练稍多于 **2 天**。
- 消融实验（小 LLM）用 **4×4 Google Cloud TPU v6e Trillium** 拓扑。
- 论文明确说明硬件配置，但未提供具体训练成本（美元等）。

## 5. 实验数量与充分性

- **实验数量充足**：
  - 视觉：1 个主要实验（ResNet-50/ImageNet），包含 5 次重复取平均。
  - 语言：两个不同规模（1B/4B）的 LLM，各对比多个下游任务（1B 有 8 个任务，4B 有 10 个任务）。
  - 消融：在独立的小 LLM 上对所有 6 个变体/组合进行完整测试（表 5），并单独分析秩 r 的影响（图 3）。
  - 与朴素缩放对比：在 LLM-4B 上单独对比“加一层”的参数量、步时间、任务性能（表 6、7）。
- **公平性和客观性**：每个实验均使用相同训练设置（优化器、学习率调度等），基线经过调优。LAuReL 作为即插即用替换，未额外调超参；消融实验中控制了层数、参数量等变量。结论具有统计显著性（标注了改进百分比和方差）。

## 6. 主要结论与发现

- 在 **ResNet-50** 上：LAuReL-RW 以仅 0.003% 额外参数提升 0.15% 准确率；RW+LR 达到“加一层”相同的效果，但参数少 2.6 倍；RW+LR+PA 进一步超越。
- 在 **LLM-1B** 上：RW+LR 以 0.012% 额外参数，在所有评估任务（除 MBPP 持平）上提升 0.03%–13.07%。
- 在 **LLM-4B** 上：RW+LR 以 0.1% 额外参数，在 8/10 个任务上提升 2.54%–20.05%，翻译和 DocVQA 持平。
- 与“加一层”的朴素缩放相比，LAuReL 以远少参数、相近延迟取得更好或相当的质量，表现出帕累托效率。
- 低秩变体中，秩 r 存在最优范围（16–32），过小或过大性能均下降。

## 7. 优点

- **轻量即插即用**：可作为标准残差连接的“in-situ”替换，无需修改模型整体结构。
- **显著质量提升**：以极低额外成本（参数、内存、延迟）带来可衡量的模型改善。
- **通用性强**：适用于 CNN（ResNet）和 Transformer（LLM），包括多模态与多语言场景。
- **变体灵活**：提供了多种选择（RW、LR、PA 及组合），允许根据预算选择最佳折衷。
- **效率分析清晰**：给出了每个变体的参数、内存、延迟的理论界（表 4），并附实际测量（表 5）。

## 8. 不足与局限

- **变体较多，选择需调优**：虽然论文推荐顺序（RW→LR→RW+LR→RW+LR+PA），但实际效果可能依赖模型规模和任务，需要少量实验确定最优 r 和 k。
- **低秩初始化敏感**：作者指出初始化对 LAuReL-LR 性能影响显著（如 LLM 实验中使用列正交初始化），但未提供系统性的初始化敏感性分析。
- **PA 变体增加内存开销**：存储 k 个历史激活需 \(\Theta(kD)\) 额外内存，在大模型或长序列下可能不忽略。
- **未在更大模型（如 100B+）上验证**：论文仅测试到 4B，更大模型的表现尚不明确。
- **实验场景有限**：未在其他视觉架构（如 ViT）或更多 NLP 任务（如对话、指令微调）上验证；消融实验（小 LLM）仅使用测试损失而非完整下游评估，可能不完全反映实际收益。
- **未与其他参数高效方法对比**：如 LoRA 微调、Adapter 等，论文仅与朴素缩放对比，缺少与同类轻量架构改进（如 AltUp）的直接比较。

（完）
