---
title: Structured Initialization for Vision Transformers
title_zh: 视觉Transformer的结构化初始化
authors: "Jianqiao Zheng, Xueqian Li, Hemanth Saratchandran, Simon Lucey"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=fmQFCXAe4v"
tags: ["query:neural-arch"]
score: 6.0
evidence: 通过结构化初始化将CNN归纳偏置引入ViT，提升准确率
tldr: 现有Vision Transformer (ViT) 在小规模数据集上泛化能力不足，且缺乏CNN的归纳偏置。本文提出结构化初始化方法，通过精心设计的权重初始值将CNN的归纳偏置引入ViT，无需修改架构。实验表明，该方法在小数据集上能获得类似CNN的性能，同时在大数据集上仍能保持ViT的优势。该工作为初始化策略提升架构性能提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-fmqfcxae4v/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fmqfcxae4v/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fmqfcxae4v/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1217, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fmqfcxae4v/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1220, \"height\": 899, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fmqfcxae4v/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1424, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fmqfcxae4v/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1431, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fmqfcxae4v/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1442, \"height\": 2245, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1265, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1335, \"height\": 309, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1281, \"height\": 248, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1453, \"height\": 764, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1307, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1046, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fmqfcxae4v/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 266, \"label\": \"Table\"}]"
motivation: 旨在通过初始化而非架构修改，将CNN的强归纳偏置引入ViT，改善小规模数据上的性能。
method: 提出结构化初始化方法，利用随机冲击滤波器模拟CNN特征，并设计特定的权重初始化方案。
result: 在小数据集上达到与CNN相当的性能，在大数据集上仍保持ViT优势。
conclusion: 通过初始化实现归纳偏置注入，平衡了小数据和大数据场景下的性能。
---

## Abstract
Convolutional Neural Networks (CNNs) inherently encode strong inductive biases, enabling effective generalization on small-scale datasets. In this paper, we propose integrating this inductive bias into ViTs, not through an architectural intervention but solely through initialization. The motivation here is to have a ViT that can enjoy strong CNN-like performance when data assets are small, but can still scale to ViT-like performance as the data expands. Our approach is motivated by our empirical results that random impulse filters can achieve commensurate performance to learned filters within a CNN. We improve upon current ViT initialization strategies, which typically rely on empirical heuristics such as using attention weights from pretrained models or focusing on the distribution of attention weights without enforcing structures. Empirical results demonstrate that our method significantly outperforms standard ViT initialization across numerous small and medium-scale benchmarks, including Food-101, CIFAR-10, CIFAR-100, STL-10, Flowers, and Pets, while maintaining comparative performance on large-scale datasets such as ImageNet-1K. Moreover, our initialization strategy can be easily integrated into various transformer-based architectures such as Swin Transformer and MLP-Mixer with consistent improvements in performance.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义
- **研究动机**：Vision Transformer (ViT) 在大型数据集上表现出色，但在小规模数据集上性能显著下降，主要原因是其缺乏卷积神经网络 (CNN) 固有的归纳偏置（如局部性、平移不变性）。CNN 凭借这些偏置能在数据量有限时有效泛化，而 ViT 的标准初始化（随机高斯）不包含任何结构信息。
- **核心问题**：如何在**不修改 ViT 架构**的前提下，将 CNN 的归纳偏置引入 ViT，使模型在小数据场景下获得类似 CNN 的性能，同时在大数据场景下保持 ViT 的长程建模优势。
- **整体意义**：提出一种**结构化初始化**方法，通过初始化的方式而非架构修改来平衡局部与全局特征学习，为 Transformer 类模型在小数据训练提供一种轻量、通用的解决方案。

## 2. 方法论
- **核心思想**：受“随机深度卷积核在不训练空间混合层的情况下仍能达到与训练核相当的性能”这一现象启发，作者将注意力映射初始化为具有 CNN 局部结构的**随机脉冲滤波器**（impulse filters），从而在初始阶段注入卷积偏置。
- **关键技术细节**：
  - **理论基石**：Proposition 1 指出，当输入嵌入秩为 \(k\)，且空间混合矩阵能张成 \(f^2\) 维核空间时，仅需训练通道混合层即可逼近任意训练好的空间混合结果。Corollary 2 进一步表明，随机脉冲滤波器同样满足该条件。
  - **初始化目标**：使每个注意力头的注意力映射 \(M_{\text{init}} = \text{softmax}(P Q_{\text{init}} K_{\text{init}}^\top P^\top)\) 近似于卷积脉冲矩阵 \(H_{\text{impulse}}\)，其中 \(P\) 是位置编码（作为伪输入）。
  - **求解 Q 和 K**：
    1. 构造理想映射：\(\alpha H_{\text{impulse}} + \beta Z\)（\(Z\) 为高斯噪声，\(\alpha:\beta=40:1\)）。
    2. 通过伪逆 \(P_{\text{inv}}\) 右乘得到 \(Q_{\text{init}} K_{\text{init}}^\top\) 的目标值。
    3. 对该矩阵进行 SVD 分解，取前 \(d\) 维作为 \(Q_{\text{init}}\) 和 \(K_{\text{init}}\) 的近似。
    4. 对结果进行范数归一化（\(\gamma=2\)）得到最终初始值。
- **说明**：初始化完成后，训练过程中不修改 ViT 结构，注意力机制仍能自由学习长程依赖。

## 3. 实验设计
- **数据集与场景**：
  - 小/中规模（约 5K–75K 训练图像）：STL-10、Flowers、Pets、Food-101、CIFAR-10、CIFAR-100。
  - 大规模（约 1.3M 训练图像）：ImageNet-1K。
  - 还测试了 Swin Transformer 和 MLP-Mixer 架构上的泛化性。
- **对比方法**：
  - **Default**：PyTorch Image Models (timm) 中的标准初始化（截断正态分布）。
  - **Mimetic**：Trockman & Kolter (2023) 提出的模仿预训练注意力权重分布的初始化。
  - **Ours (impulse)**：本文提出的结构化初始化。
- **基准与训练设置**：小/中数据集遵循 Xu et al. (2024) 的训练策略；ImageNet-1K 使用 DeiT (Touvron et al., 2021) 的训练策略；Swin 和 MLP-Mixer 分别按原论文或特定配置训练。

## 4. 资源与算力
- **硬件**：主实验使用单节点 8 块 Tesla V100 SXM3 GPU（32GB 显存）。
- **训练时间**：
  - 小规模数据集：约 **3 小时**/模型。
  - ImageNet-1K：约 **2 天**/模型。
- 额外设置：ViT-Base* 实验使用了 16 块 V100 并增加 0.3 color jittering，以对齐并发论文结果。这些资源信息在论文 Sec.5 中明确给出。

## 5. 实验数量与充分性
- **实验数量**：覆盖 6 个小/中数据集 + 1 个大数据集，包含 ViT-Tiny/Small/Base 三种模型大小，以及 Swin Transformer-Base/Tiny 和 MLP-Mixer 两种扩展架构。还包含预训练（Weight Selection）场景实验。
- **消融与统计**：在附录中提供了 5 次不同随机种子的均值和标准差（图 6），确认结果稳定性。在 ImageNet-1K 上还做了不同学习率缩放和 repeated augmentation 的消融（表 5）。
- **公平性**：所有对比实验均使用相同代码、相同超参数（仅初始化方法不同），且自行重训练所有 baseline，避免了数据污染。
- **总体评价**：实验设计较为全面、客观，充分验证了方法在不同规模数据、不同架构和不同训练条件下的有效性。

## 6. 主要结论与发现
1. **小/中数据集显著提升**：ViT-Tiny 在 CIFAR-10 上相比 Default 提升 2.38%，在 Pets 上提升高达 24.26%，持续优于 Mimetic 初始化。
2. **大规模数据集保持竞争力**：在 ImageNet-1K 上，ViT-Base 达到 81.83%（Default 81.24%），未出现性能退化，表明结构化初始化不限制模型学习长程依赖的能力。
3. **加速收敛**：训练初期准确率上升更快（附录表 7）。
4. **架构泛化性**：在 Swin Transformer 和 MLP-Mixer 上均有 1%–2% 的性能提升，而 Mimetic 在这些架构上无效甚至退化。
5. **预训练兼容**：用 ImageNet-1K 预训练的 ViT-Small 经结构化初始化后，其权重选择在小数据集上的效果可与 ImageNet-21K 预训练模型媲美。

## 7. 优点
- **无需架构修改**：仅更改初始化，保留 ViT 原始 Transformer 结构，具有高度通用性，可即插即用于多种 ViT 变体。
- **理论支撑充分**：从矩阵秩和卷积核张成空间的角度给出了严格证明，解释了随机脉冲滤波器为何有效。
- **简单高效**：初始化计算仅依赖位置编码和 SVD，开销极小，不依赖任何外部预训练模型。
- **平衡性能**：在小数据上获得 CNN 级偏置，在大数据上保持 ViT 灵活性，解决了长期存在的“架构偏置 vs 容量”的权衡问题。

## 8. 不足与局限
- **对位置编码的依赖**：使用 Positional Encoding 作为伪输入，但位置编码只在第一层添加，对深层注意力图的影响可能减弱（图 7 中深层注意力结构不如浅层清晰）。
- **头数限制**：理论要求多个头共同张成核空间（如 3×3 核需至少 9 个头），而 ViT-Tiny 仅 3 个头，Small 仅 6 个头，可能无法完全发挥理论优势。实验也表明模型越大 (Base 12 头) 提升越明显。
- **未覆盖 Value 和投影矩阵**：初始化仅针对 Q 和 K，未考虑 V 权重和输出投影，可能无法完全捕捉注意力机制的完整偏置。
- **实验局限**：小数据集上性能波动较大（尤其在 Pets 上），且未在更多实际低数据场景（如医学影像）中验证。此外，只有 5 次重复，部分结果误差带稍大。

（完）
