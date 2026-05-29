---
title: "MobileODE: An Extra Lightweight Network"
title_zh: MobileODE：一种超轻量级网络
authors: "Le Yu, Jun Wu, Bo Gou, Xiangde Min, Lei Zhang, Zhang Yi, Tao He"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=spjAvoZpVW"
tags: ["query:neural-arch"]
score: 8.0
evidence: 利用常微分方程优化深度可分离卷积实现轻量化网络
tldr: 针对深度可分离卷积中逐点卷积参数仍较多的问题，本文提出MobileODE，通过离散常微分方程求解器（COS）替换逐点卷积，利用欧拉算法实现轻量化。该方法在保持精度的前提下显著减少模型参数量，为高效网络结构设计提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 994, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 665, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1101, \"height\": 202, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 974, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 648, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 655, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1224, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1228, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1208, \"height\": 1985, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-spjavozpvw/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1203, \"height\": 1529, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 703, \"height\": 129, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 659, \"height\": 510, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 735, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 257, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 733, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-spjavozpvw/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 931, \"height\": 701, \"label\": \"Table\"}]"
motivation: 深度可分离卷积虽轻量，但逐点卷积仍有优化空间，期望进一步减少参数。
method: 用离散常微分方程模块（COS）替代逐点卷积，通过可学习增量参数实现通道间交互。
result: MobileODE在多种任务上以更少参数取得与基准相当的精度，验证了其轻量化有效性。
conclusion: 该方法为构建超轻量卷积网络提供了可行的新范式，拓展了深度可分离卷积的优化方向。
---

## Abstract
Depthwise-separable convolution has emerged as a significant milestone in the lightweight development of Convolutional Neural Networks (CNNs) over the past decade. This technique consists of two key components: depthwise convolution, which captures spatial information, and pointwise convolution, which enhances channel interactions. In this paper, we propose a novel method to lightweight CNNs through the discretization of Ordinary Differential Equations (ODEs). Specifically, we optimize depthwise-separable convolution by replacing the pointwise convolution with a discrete ODE module, termed the \emph{\textbf{C}hannelwise \textbf{O}DE \textbf{S}olver (COS)}. The COS module is constructed by a simple yet efficient direct differentiation Euler algorithm, using learnable increment parameters. This replacement reduces parameters by over $98.36$\% compared to conventional pointwise convolution. By integrating COS into MobileNet, we develop a new extra lightweight network called MobileODE. With carefully designed basic and inverse residual blocks, the resulting MobileODEV1 and MobileODEV2 reduce channel interaction parameters by $71.0$\% and $69.2$\%, respectively, compared to MobileNetV1, while achieving higher accuracy across various tasks, including image classification, object detection, and semantic segmentation. The code is available at {\url{https://github.com/cashily/MobileODE}}.

---

## 论文详细总结（自动生成）

# MobileODE: 一种超轻量级网络 —— 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：深度可分离卷积（Depthwise‑separable convolution）是目前轻量化 CNN 的主流范式，它由空间卷积（depthwise）和通道交互卷积（pointwise）组成。然而，逐点卷积（1×1 卷积）的参数数量仍然较大（复杂度为 O(C²)），限制了模型的进一步轻量化。
- **核心问题**：如何在保持甚至提升模型精度的前提下，大幅减少通道交互部分的参数量，从而构建“超轻量级”网络。
- **整体含义**：论文提出利用离散化常微分方程（ODE）来替代逐点卷积，通过一个称为 Channelwise ODE Solver (COS) 的模块，将通道交互建模为 ODE 的求解过程，从而将参数量降低两个数量级以上，并能在多种视觉任务中实现精度与效率的更好平衡。

## 2. 论文提出的方法论

- **核心思想**：将通道间的非线性映射视为一个动态系统，利用神经记忆 ODE（nmODE）的全局吸引子特性，通过离散化的欧拉方法逐步迭代求解，以极少的可学习参数完成通道交互。
- **关键技术细节**：
  - **Direct Differentiation Euler (DDE) 算法**：在传统显式欧拉法中，时间步长 Δt 是固定的（常设为 1/L）。DDE 将 Δt 设为可学习的参数，并通过 ReLU6 激活确保非负且范围受限。梯度下降时，模型可自适应调整时间分辨率，公式：
    \[
    \dot{y}_l(t) = -y_l + f(y_l + g(x_l, \theta_l)), \quad y_{l+1} = y_l + \Delta t_l \cdot \dot{y}_l(t)
    \]
  - **Channelwise ODE Solver (COS) 模块**：对输入特征张量 \(x \in \mathbb{R}^{C \times H \times W}\)，在每个像素位置执行线性变换 \(g(x_{\langle i,j \rangle}) = x_{\langle i,j \rangle} \cdot \Phi\)，其中 \(\Phi \in \mathbb{R}^{\sqrt{C} \times \sqrt{C}}\) 是小型可学矩阵，复杂度从 O(C²) 降至 O(C)。然后利用 DDE 算法迭代 L 层（论文取 L=10）进行非线性映射，最后加入残差连接 \(o = y_L + x\)。
  - **两种基础模块**：
    - **COS‑base**：保留原始 depthwise 卷积，用 COS 替换 pointwise 卷积。
    - **COS‑inv**：基于 MobileNetV2 的反残差结构，先通过 COS 进行通道扩展（扩展因子 e），再经 depthwise 卷积，最后用另一个 COS 恢复通道数；扩展/压缩时使用双线性插值进行上/下采样。
- **架构设计**：基于 MobileNetV1 和 MobileNetV2 的骨干，将大部分 pointwise 卷积替换为 COS，分别得到 MobileODEV1 和 MobileODEV2。参数量对比显示，通道交互参数量分别下降 71.0% 和 69.2%（相对 MobileNetV1）。

## 3. 实验设计

- **数据集与场景**：
  - 图像分类：CIFAR‑10、CIFAR‑100、Tiny ImageNet (IN‑tiny)、ImageNet‑R (IN‑R)、ImageNet‑A (IN‑A)
  - 语义分割：PASCAL VOC 2012、ADE20K（使用 DeepLabV3 作为分割头）
  - 目标检测：BUSI（乳腺超声）、FFE（面部特征提取）（使用 SSDLite 检测头）
- **Benchmark 对比方法**：
  - 经典轻量网络：MobileNetV1/V2/V3/V4、GhostNet、ShuffleNetV1/V2、MobileOne、FastViT‑T8、MobileViT、MobileViTv2、ResNet‑110/353 等。
  - 消融实验对比了固定 Δt 与可学习 Δt，不同离散层数 L，不同扩展因子 e。
- **实验设置公平性**：所有模型均从随机初始化从头训练，不使用预训练权重；采用相同的数据增强、优化器（AdamW/SGD）、学习率调度（余弦退火）、训练周期（200 epochs）等。

## 4. 资源与算力

- 文中明确说明：所有实验在 **单张 NVIDIA RTX 4090 GPU** 上完成，使用 PyTorch 框架，固定随机种子以保证可复现性。
- 未给出具体训练总时长，但提及在 CIFAR 上 batch size = 32，IN‑tiny/IN‑R 上 batch size = 16，语义分割与目标检测使用标准训练配置（200 epochs）。
- 在计算效率分析中（Tab.7），MobileODEV1 的 FLOPs 为 7.09M，推理延迟为 24.54 ms（batch size = 16）。

## 5. 实验数量与充分性

- **实验组数**：涵盖 3 大类任务（分类、分割、检测），共 7 个数据集；消融实验包括 L 的取值（1~15）、Δt 固定 vs 可学习、扩展因子 e 的对比；还测试了将 COS 与 MobileViT 结合（+ViT）的变体。
- **充分性评价**：
  - 对比基线覆盖全面，包括同代 MobileNet 系列、基于 NAS 的 MobileNetV3/V4、基于 reparameterization 的 MobileOne、Transformer 混合的 FastViT/MobileViT 等。
  - 消融实验深入探讨了 L 和 Δt 学习的影响，验证了可学习 Δt 的有效性。
  - 不足之处：未在更大规模数据集（如完整 ImageNet‑1K）上进行验证；检测和分割任务的数据集规模较小（如 BUSI 仅约 780 张图），结论的泛化性需进一步确认。

## 6. 论文的主要结论与发现

1. **COS 模块有效性**：以极低参数（相比 pointwise 卷积减少 98.36%）实现了有效的通道交互，且通过 DDE 可学习 Δt 能自适应调整时间分辨率，在 L 增加时精度持续提升，而固定 Δt 则会出现性能波动甚至下降。
2. **MobileODEV1 和 MobileODEV2 相比基线**：
   - 参数量：MobileODEV1 仅 1.14M（↓66.57% vs MobileNetV1 3.41M），MobileODEV2 仅 1.52M（↓38.7% vs MobileNetV2 2.48M）。
   - 精度：在 CIFAR‑10/100、IN‑tiny、IN‑R 上均超过或持平对应基线，尤其在 IN‑R 上提升显著（MobileODEV2+ViT 达 48.08%）。
   - 在语义分割（PASCAL VOC 2012 / ADE20K）和目标检测（BUSI / FFE）上也以更少参数达到相近或更优性能。
3. **与自注意力机制兼容**：将 COS 与 MobileViT 结合可进一步提升精度，且参数量依然远低于纯 Transformer 模型。
4. **DDE 算法优势**：相比固定 Δt 的 gating 方式，可学习 Δt 能更好地适应不同区域的曲率，实现细粒度学习。

## 7. 优点

- **创新性**：首次将离散 nmODE 系统化地用于构建类似 MobileNet 的轻量骨干网络，替代 pointwise 卷积，思路新颖。
- **轻量化显著**：参数量降低至接近 depthwise 卷积的水平，且精度不降反升，在超轻量网络领域具有竞争力。
- **通用性**：提出 COS‑base 和 COS‑inv 两种模块，可灵活嵌入不同网络结构，并兼容自注意力机制。
- **实验设计规范**：固定随机种子、从头训练、对比方法丰富、消融实验全面。

## 8. 不足与局限

- **大数据集验证缺失**：未在完整 ImageNet‑1K 上评估，该数据集是轻量网络的标准 benchmark，缺少这一结果限制了与主流方法的直接横向比较。
- **计算效率权衡**：COS 的串行计算（L 层迭代）增加了 FLOPs（MobileODEV1 的 FLOPs 比 MobileNetV1 高约 75%），且推理延迟与 L 相关，大 L 会降低速度。论文虽设 L=10 平衡，但并非最优解。
- **扩展因子 e 敏感**：消融显示 e 对精度影响显著，过大或过小均导致性能下降，缺乏自适应选择策略。
- **检测与分割数据集规模小**：BUSI 和 FFE 均为专用小数据集（数百张），结果可能存在偏差，缺乏在 COCO 等大规模检测数据集上的验证。
- **应用局限性**：作者提到在医疗筛查 demo 中部署，但未给出详细公平性、鲁棒性分析；轻量模型可能在某些场景下产生错误预测，需谨慎应用。

（完）
