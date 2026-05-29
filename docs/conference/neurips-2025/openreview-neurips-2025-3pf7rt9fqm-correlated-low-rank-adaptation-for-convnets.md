---
title: Correlated Low-Rank Adaptation for ConvNets
title_zh: 用于卷积网络的相关低秩适应
authors: "Wu Ran, Weijia Zhang, ShuYang Pang, Qi Zhu, Jinfan Liu, JingSheng Liu, Xin Cao, Qiang Li, Yichao Yan, Chao Ma"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=3pF7rt9fQM"
tags: ["query:neural-arch"]
score: 6.0
evidence: 利用相关低秩适应的卷积网络参数高效微调
tldr: 针对现有低秩适应方法在卷积网络上效果不佳的问题，提出相关低秩适应(CoLoRA)，通过建模卷积层间依赖关系，使用相关低秩矩阵进行参数高效微调。同时提出无参数过滤方法提升调优效率。实验表明在多个卷积网络微调任务上优于独立低秩适应方法。为ConvNet的PEFT提供了有效解决方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1394, \"height\": 151, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1425, \"height\": 179, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1302, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 526, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 506, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 470, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1381, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1449, \"height\": 1428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3pf7rt9fqm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1440, \"height\": 1422, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1236, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1132, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1156, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 727, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 419, \"height\": 123, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 727, \"height\": 159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1427, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1076, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1044, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1444, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1445, \"height\": 468, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1447, \"height\": 315, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3pf7rt9fqm/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1302, \"height\": 200, \"label\": \"Table\"}]"
motivation: 现有LoRA方法假设层间独立，不适用于卷积网络的层间高相关性。
method: 提出CoLoRA框架，利用相关低秩矩阵建模层间依赖，并引入无参数过滤。
result: 在多个ConvNet微调任务上取得更优性能。
conclusion: 考虑层间相关性是提升ConvNet微调效果的关键。
---

## Abstract
Low-Rank Adaptation (LoRA) methods have demonstrated considerable success in achieving parameter-efficient fine-tuning (PEFT) for Transformer-based foundation models. These methods typically fine-tune individual Transformer layers using independent LoRA adaptations. However, directly applying existing LoRA techniques to convolutional networks (ConvNets) yields unsatisfactory results due to the high correlation between the stacked sequential layers of ConvNets. To overcome this challenge, we introduce a novel framework called Correlated Low-Rank Adaptation (CoLoRA), which explicitly utilizes correlated low-rank matrices to model the inter-layer dependencies among convolutional layers. Additionally, to enhance tuning efficiency, we propose a parameter-free filtering method that enlarges the receptive field of LoRA, thus minimizing interference from non-informative local regions. Comprehensive experiments conducted across various mainstream vision tasks, including image classification, semantic segmentation, and object detection, illustrate that CoLoRA significantly advances the state-of-the-art PEFT approaches. Notably, our CoLoRA achieves superior performance with only 5\% of trainable parameters, surpassing full fine-tuning in the image classification task on the VTAB-1k dataset using ConvNeXt-S. Code is available at [https://github.com/VISION-SJTU/CoLoRA](https://github.com/VISION-SJTU/CoLoRA).

---

## 论文详细总结（自动生成）

# 论文《Correlated Low-Rank Adaptation for ConvNets (CoLoRA)》中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题背景**：参数高效微调（PEFT）方法，尤其是低秩适应（LoRA），在 Transformer 模型中取得了巨大成功，但直接应用于卷积网络（ConvNets）时效果不佳。
- **核心发现**：
  - 卷积网络层间存在高度相关性（Adjacent layers have high correlation），而现有 LoRA 为每层独立引入低秩矩阵，忽略了层间依赖。
  - 全量微调卷积网络时，权重更新矩阵 ∆W 的秩接近全秩（full-rank），低秩近似难以有效捕获更新。
- **研究动机**：提出一种专为卷积网络设计的 LoRA 变体，通过建模相邻卷积层间的相关性来实现高效、低参数的微调，同时保留卷积网络的层次特征提取能力。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想：Correlated Low-Rank Adaptation (CoLoRA)
- 利用相邻全连接层（或 1×1 卷积）的反向传播梯度公式，发现 ∆W₁ 和 ∆W₂ 存在共享项（`Xᵀ ∂L/∂Y₂`），即它们高度相关。
- 提出将权重更新分解为**相关部分**与**独立部分**：
  - `∆W₁ = S·W₂ᵀ + P₁`
  - `∆W₂ = W₁ᵀ·S + P₂`
  - 其中 `S` 为相邻层共享的低秩矩阵，`P₁`、`P₂` 为各层独立的低秩矩阵。
- 进一步参数化：`S = s·Aₛ·Bₛ`，`P₁ = s₁·A₁·B₁`，`P₂ = s₂·A₂·B₂`，其中 A、B 为低秩矩阵，s 为缩放因子。

### 2.2 关键技术细节

1. **相关低秩更新**：
   - 更新方程：`Y₁ = X(W₁ + s₁A₁B₁ + s Aₛ Bₛ W₂ᵀ)`，`Y₂ = Y₁(W₂ + s₂A₂B₂ + s W₁ᵀ Aₛ Bₛ)`。
   - 共享矩阵 `Aₛ, Bₛ` 秩为 `rₛ`，独立矩阵秩为 `rₗ`，总秩 `r = rₛ + rₗ`。
   - 相比独立 LoRA，CoLoRA 参数更少（节省 `2 rₛ d′` 参数）。

2. **缩放因子设计**：
   - 独立更新部分使用 `s_expect = 1/√(r σ_A)`。
   - 共享更新部分使用方差匹配的缩放因子 `s_var = 1/(⁴√(r d) σ_A)`，以稳定训练。

3. **参数无关滤波（Filtering）**：
   - 解决卷积核空间局部性导致的有害梯度问题：LoRA 接收来自局部区域所有位置的梯度，非信息区域可能干扰适应。
   - 提出**边缘保持滤波**（基于双边滤波的快速实现）：
     - 使用高斯空间核 `k_s` 和余弦范围核 `k_r(x,y) = cos(γ_c(x-y))`，可在 `O(1)` 时间内通过四次深度可分离卷积完成。
     - 滤波应用于低秩矩阵 A 压缩后的特征，以扩大感受野并抑制噪声，无额外可训练参数。

4. **集成位置**：
   - 在 ConvNet 的每个残差块内，将相邻两层（如 pwconv1 和 pwconv2）配对使用 CoLoRA，其余层使用常规 LoRA。

5. **周期性合并（Merging）**：
   - 借鉴 ReLoRA，每隔一定步数将更新矩阵合并回预训练权重，并重新初始化 LoRA 矩阵，以提高更新矩阵的实际秩。

## 3. 实验设计：数据集、Benchmark、对比方法

- **数据集与任务**：
  - **图像分类**：VTAB-1k 基准（19 个子任务，含 NATURAL、SPECIALIZED、STRUCTURED 三类）。
  - **语义分割**：ADE20K，使用 UPerNet 架构，分辨率 512×512，160k 迭代。
  - **目标检测**：MS-COCO，使用 Faster R-CNN，标准 1x 计划（12 epoch）。
  - **细粒度分类**（额外实验）：CUB-200-2011、FGVC-Aircraft，使用 ViT-B（MAE 预训练）。
- **Backbones**：ResNet-50、ConvNeXt-S、ConvNeXt-B 等（ImageNet-22K 预训练）。
- **对比方法**：
  - 全量微调（FT）
  - Conv-Adapter（CVPRW'24，专为 ConvNet 设计的适配器）
  - PiSSA（NeurIPS'24，改进的 LoRA 初始化）
  - HiRA（ICLR'25，高阶 Hadamard 低秩适应）
- **公平性设置**：所有对比方法的可训练参数数量对齐（通过调整压缩因子 γ 和秩 r），采用相同基本配置（AdamW 优化器、学习率 1e-4、权重衰减 0.05、混合精度训练等）。

## 4. 资源与算力

- 论文中明确提及**计算资源**：
  - 所有实验在 **NVIDIA A800 GPU** 上进行。
  - VTAB-1k：单卡，每子任务 100 epoch，batch size 32。
  - ADE20K：单卡，160k 迭代（约 2 天）。
  - MS-COCO：**两张 A800 GPU**，batch size 16，12 epoch（约 2.5 天）。
- **内存与时间**（表 5）：
  - 训练 GPU 内存：CoLoRA 约 15042 MiB（ConvNeXt-S on COCO），低于全量微调的 18418 MiB。
  - 每步训练时间：CoLoRA 约 1.527s，略高于 PiSSA（1.426s）但远低于全量微调（1.747s），过滤模块引入额外开销可忽略。
  - 推理时间：所有 LoRA 变体相同（0.108s），因权重可合并。
- **未说明部分**：未提及总 GPU 小时数或完整实验的总功耗。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验（表 1、2）：覆盖 3 种任务、2～3 个 backbone、4～5 种对比方法，每个设置多次运行（VTAB-1k 报告 3 次均值和 std，ADE20K/COCO 未重复但提及单次运行）。
  - 消融实验（表 3、6、图 6）：分析过滤、相关更新、合并、秩分配、压缩因子等。
  - 额外实验（表 4）：ViT-B 上细粒度分类。
  - 附录更多结果（表 7～15）：包括不同 γ 的缩放分析、CKA 分析、复杂度对比等。
- **充分性与公平性**：
  - **积极方面**：对比方法参数数量对齐，超参数保持一致，多次运行报告误差棒（VTAB-1k），消融实验较全面，覆盖核心设计维度。
  - **潜在不足**：
    - ADE20K 和 COCO 仅报告单次结果，未提供统计显著性。
    - 部分超参数（如滤波窗口大小、γ 选择）未做系统敏感性分析。
    - 对比方法（Conv-Adapter、PiSSA、HiRA）的官方实现可能针对 Transformer 优化，在 ConvNet 上未做最优适配，可能未达到其最佳性能。
  - 总体而言，实验设计较充分，结论较可靠，但统计重复性可进一步提升。

## 6. 主要结论与发现

1. **核心结论**：卷积网络微调是一个**近似全秩学习**过程，独立 LoRA 无法有效捕获相邻层的高相关性，导致性能下降。
2. **CoLoRA 显著优于现有 PEFT 方法**：
   - VTAB-1k 上，ConvNeXt-S 平均准确率 76.39%（仅 2.6M 可训练参数），超过全量微调（76.15%），比 PiSSA（76.09%）高 0.3%。
   - ADE20K 上，CoLoRA 以 4.6M 参数达 49.55 mIoU，接近全量微调 50.99；更强配置（5.7M 参数）达 50.65 mIoU，接近全量微调。
   - COCO 上，CoLoRA 在 AP_box 和 AP_mask 上均超越所有对比方法，特别是 CoLoRA†（5.7M 参数）达 47.5 AP_box，优于 Conv-Adapter（44.9）。
3. **过滤技术与周期性合并**能进一步提升性能（表 3 中分别提升 0.74 和 0.28 mIoU）。
4. 共享秩 `rₛ` 与独立秩 `rₗ` 的合理分配（如 `rₛ=rₗ`）可达到最优性能。

## 7. 优点

- **方法创新性**：首次从梯度相关角度提出为卷积网络定制 LoRA，突破 Transformer 独立假设的局限。
- **参数效率高**：比已有方法参数更少（如相比 PiSSA 节省 0.2M～0.4M），性能却大幅提升。
- **理论支撑**：通过梯度形式化（式 3-4）严格推导层间相关更新结构，并分析缩放因子对梯度方差的影响（Lemma 3.1）。
- **实现简洁高效**：滤波基于双边滤波的快速近似，无需额外可训练参数；推理时可合并权重，无额外开销。
- **实验全面**：涵盖图像分类、语义分割、目标检测三大主流任务，并验证了在 ViT 上的泛化能力。
- **开源代码**：提供完整实现，可复现。

## 8. 不足与局限

1. **应用范围有限**：仅针对 2D 视觉 ConvNet，未探索 3D 场景（如视频理解、点云）或视觉语言任务（如 VQA、视觉定位）。
2. **实验统计严谨性可提升**：ADE20K/COCO 未提供多次运行误差棒；VTAB-1k 虽报告标准差，但未进行显著性检验。
3. **超参数敏感性未充分分析**：滤波窗口大小、σ、γ_c 等固定；压缩因子 γ 与秩分配 `rₛ/(rₛ+rₗ)` 的选择对性能有影响（图 6、表 6），但缺乏系统性网格搜索。
4. **泛化至其他 ConvNet 架构验证不足**：仅测试 ResNet 和 ConvNeXt，未涉及 MobileNet、EfficientNet 等高效架构。
5. **计算开销**：训练时过滤模块引入少量额外计算（表 5 显示 COCO 上每步多 0.018s），但对长训练可能仍有一定累积成本。
6. **与全量微调对比的公平性**：全量微调通常需要更多迭代和不同的学习率调度，本文使用相同配置，可能未完全挖掘全量微调潜力。
7. **局限性声明**：作者在 Section 6 中明确指出了上述限制，并对未来工作提出方向（如扩展至视觉语言模型、3D 领域）。

（完）
