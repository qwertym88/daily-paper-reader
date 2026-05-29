---
title: "Linear Differential Vision Transformer: Learning Visual Contrasts via Pairwise Differentials"
title_zh: 线性差分视觉Transformer：通过成对差分学习视觉对比
authors: "Yifan Pu, Jixuan Ying, Qixiu Li, Tianzhu Ye, Dongchen Han, Xiaochen Wang, Ziyi Wang, Xinyu Shao, Gao Huang, Xiu Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=91GzT22Sef"
tags: ["query:neural-arch"]
score: 7.0
evidence: 新颖的视觉对比注意力机制提升ViT准确性
tldr: 针对Vision Transformer中多头自注意力计算冗余的问题，本文提出视觉对比注意力（VCA），通过将查询场蒸馏为少量视觉对比令牌并区分为正负类，将复杂度从O(N^2C)降至O(NnC)。实验证明VCA在图像识别和生成任务上能提升准确性并降低计算量，是一种高效的新型注意力架构设计。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-91gzt22sef/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 697, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-91gzt22sef/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 718, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-91gzt22sef/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1457, \"height\": 582, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-91gzt22sef/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-91gzt22sef/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1384, \"height\": 278, \"label\": \"Table\"}]"
motivation: 现有Vision Transformer的自注意力层对所有令牌对进行二次交互，计算冗余且忽略视觉对比。
method: 提出视觉对比注意力（VCA），将每个头的密集查询场蒸馏为少量空间池化的视觉对比令牌，并拆分为可学习的正负类。
result: VCA在保持或提升精度的同时，显著降低了计算复杂度，在图像识别与生成任务上验证了有效性。
conclusion: VCA作为MHSA的即插即用替代，为视觉Transformer提供了一种高效且准确的新架构方案。
---

## Abstract
Vision Transformers (ViTs) have become a universal backbone for both image recognition and image generation.  Yet their Multi–Head Self–Attention (MHSA) layer still performs a quadratic query–key interaction for \emph{every} token pair, spending the bulk of computation on visually weak or redundant correlations.  We introduce \emph{Visual–Contrast Attention} (VCA), a drop-in replacement for MHSA that injects an explicit notion of discrimination while reducing the theoretical complexity from $\mathcal{O}(N^{2}C)$ to $\mathcal{O}(N n C)$ with $n\!\ll\!N$.  VCA first distils each head’s dense query field into a handful of spatially pooled \emph{visual–contrast tokens}, then splits them into a learnable \emph{positive} and \emph{negative} stream whose differential interaction highlights what truly separates one region from another.  The module adds fewer than $0.3$\,M parameters to a DeiT-Tiny backbone, requires no extra FLOPs, and is wholly architecture-agnostic.  Empirically, VCA lifts DeiT-Tiny top-1 accuracy on ImageNet-1K from $72.2\%$ to \textbf{$75.6\%$} (+$3.4$) and improves three strong hierarchical ViTs by up to $3.1$\%, while in class-conditional ImageNet generation it lowers FID-50K by $2.1$ to $5.2$ points across both diffusion (DiT) and flow (SiT) models.  Extensive ablations confirm that (i) spatial pooling supplies low-variance global cues, (ii) dual positional embeddings are indispensable for contrastive reasoning, and (iii) combining the two in both stages yields the strongest synergy.  VCA therefore offers a simple path towards faster and sharper Vision Transformers. The source code is available at \href{https://github.com/LeapLabTHU/LinearDiff}{https://github.com/LeapLabTHU/LinearDiff}.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：Vision Transformer（ViT）中多头自注意力（MHSA）层对所有令牌对进行二次复杂度（O(N²C)）的查询-键交互，大量计算消耗在视觉上弱相关或冗余的相似度上，导致计算效率低下，同时模型难以聚焦于真正有区分度的视觉特征。
- **背景**：已有方法试图通过限制感受野（如窗口注意力）或近似注意力图（如低秩投影）来降低复杂度，但前者牺牲了全局上下文，后者则对所有相关性一视同仁，未能突出有判别力的信号。受语言模型中“差分注意力”的启发，本文尝试将差分思想引入视觉，并结合视觉空间的平滑性来压缩查询场。
- **整体含义**：提出一种即插即用的视觉对比注意力（VCA），在保持全局感受野的同时将复杂度降至线性（O(NnC)，n≪N），并通过显式对比正负流来强化判别性，从而在图像分类和生成任务上提升性能。

## 2. 方法论核心思想、关键技术细节

- **核心思想**：利用图像的空间平滑性，将每个注意力头的密集查询场先空间池化为少量“视觉对比令牌”，再将其拆分为正流和负流，通过差分运算突出区域间的真正差异，最后让原始补丁令牌基于对比结果进行线性注意力计算。
- **关键技术细节**：
  - **两阶段结构**：
    - **Stage I（全局对比）**：从查询令牌出发，通过平均池化生成n个视觉对比令牌（h×w网格），并添加两组独立的位置编码分别形成正流和负流。正负流各自对键和值执行注意力，得到中间结果后做差分、RMS归一化并乘以学习标量，得到全局对比表征。
    - **Stage II（补丁级差分注意力）**：原始查询令牌分别与正、负对比令牌计算注意力分数，再次差分得到最终注意力权重，然后与Stage I的对比表征进行值聚合。
  - **视觉对比令牌生成**：对查询特征图进行平均池化（分辨率从H×W降至h×w），添加正负位置编码后展平得到两组令牌。
  - **复杂度分析**：每层复杂度为O(NnC)，相比标准自注意力的O(N²C)降低因子N/n（n≪N），且仅增加少量参数（<0.3M）。
- **公式/算法流程**（文字说明）：  
  输入前层令牌序列→线性投影得到Q、K、V（多头）→对Q池化生成正负对比令牌→Stage I中对比令牌与K、V交互得到对比结果→Stage II中Q与对比令牌交互得到差分注意力权重→加权对比结果→RMSNorm→拼接+输出投影。

## 3. 实验设计

- **数据集**：ImageNet-1K（1.28M训练图像，50K验证图像，1000类），用于图像分类和类条件图像生成（256×256分辨率）。
- **基准与评估指标**：
  - 分类任务：top-1准确率。
  - 生成任务：FID-50K（Fréchet Inception Distance）。
- **对比方法**：
  - 分类：DeiT-T/S、PVT-T/S/M、Swin-T/S/B、CSwin-T/S（均为原版基线）。
  - 生成：DiT-S/B（三种补丁尺寸8/4/2）、SiT-S/B（三种补丁尺寸8/4/2）。
- **实验设置**：
  - 分类：300 epochs，AdamW优化器，余弦学习率衰减，RandAugment、Mixup、CutMix、随机擦除等增强，EMA。
  - 生成：400k迭代，batch size 256，固定学习率1e-4，仅随机水平翻转，EMA decay 0.9999。所有实验从零开始训练，与原作者设置保持一致。

## 4. 资源与算力

- **论文未明确说明**：文中未提及具体GPU型号、数量、训练时长等算力信息，仅指出所有模型均采用标准训练配置，未额外增加FLOPs。因此无法总结算力消耗细节。

## 5. 实验数量与充分性

- **实验数量**：
  - 分类任务：10个模型变体（DeiT、PVT、Swin、CSwin各尺寸）。
  - 生成任务：12个模型变体（DiT和SiT的Small/Base，各三种补丁尺寸）。
  - 消融实验：2组（模型架构消融、视觉对比令牌生成消融），分别评估分类和生成任务。
- **充分性**：实验覆盖了主流ViT架构（plain和hierarchical）以及两种生成范式（扩散和流模型），消融实验验证了各组件的贡献。对比基线均为官方标准，训练设置一致，实验客观公平。但未提供错误条或统计显著性测试。

## 6. 论文的主要结论与发现

- VCA作为MHSA的即插即用替代，在几乎不增加FLOPs和参数的前提下，显著提升分类准确率（DeiT-Tiny +3.4%，PVT-Tiny +3.1%）和生成质量（FID-50K下降2.1~5.2点）。
- 两阶段设计（全局对比+补丁差分）具有累加效应；结合池化和双位置编码的正负流生成方式效果最佳。
- VCA是架构无关的，在plain和hierarchical ViT上均有效，且同时适用于扩散和流模型。

## 7. 优点

- **新颖性**：首次将差分注意力成功扩展到视觉任务并实现线性复杂度，区别于先前线性注意力方法（无显式对比）和语言差分注意力（仍是二次复杂度）。
- **高效性**：参数量极小（<0.3M），无额外FLOPs，即插即用，兼容多种ViT架构和生成范式。
- **泛化性**：在两种不同任务（分类、生成）和多种架构上表现一致提升，表明方法通用性强。
- **消融实验设计清晰**：逐步验证了两阶段结构、池化与位置编码的作用，具有很好的可解释性。

## 8. 不足与局限

- **任务局限性**：提出的平均池化可能丢失边缘等细节信息，对需要精细定位的任务（如目标检测、语义分割）未进行验证。
- **小图像场景**：当图像尺寸较小时，额外引入的微注意力可能削弱速度优势（文中提及）。
- **未扩展的任务**：视频、3D、语言等领域的应用尚未探索。
- **实验细节缺失**：未报告计算资源（GPU型号、数量、训练时间）、统计显著性及多次运行的误差棒，可能影响结果的可重复性。
- **无开源代码**：论文声称代码已提供，但提交时未公开，阻碍复现。

（完）
