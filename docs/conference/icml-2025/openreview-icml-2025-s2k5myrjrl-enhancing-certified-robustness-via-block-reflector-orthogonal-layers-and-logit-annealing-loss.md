---
title: Enhancing Certified Robustness via Block Reflector Orthogonal Layers and Logit Annealing Loss
title_zh: 通过块反射正交层和对数退火损失增强认证鲁棒性
authors: "Bo-Han Lai, Pin-Han Huang, Bo-Han Kung, Shang-Tse Chen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=S2K5MyRjrL"
tags: ["query:neural-arch"]
score: 6.0
evidence: 用于利普希茨网络的新型块反射正交层
tldr: 为了提升利普希茨神经网络的表现力，本文提出了一种高效的块反射正交层（BRO），能构造更富有表达力的利普希茨架构。同时引入一种对数退火损失函数，增大数据点的间隔。结合两者设计的BRONet在多个基准上达到了最先进的认证鲁棒性，证明了正交层设计的有效性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 790, \"height\": 661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1078, \"height\": 995, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1483, \"height\": 2155, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1484, \"height\": 832, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 805, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1260, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1047, \"height\": 1042, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1758, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1623, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1737, \"height\": 865, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-s2k5myrjrl/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1700, \"height\": 690, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1284, \"height\": 1356, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1354, \"height\": 593, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1465, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1439, \"height\": 591, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 817, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 713, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 663, \"height\": 365, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 989, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1403, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1048, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1225, \"height\": 463, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1389, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 853, \"height\": 408, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 685, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1535, \"height\": 1096, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-s2k5myrjrl/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1318, \"height\": 744, \"label\": \"Table\"}]"
motivation: 现有正交层在构建利普希茨网络时表达能力有限。
method: 提出块反射正交层，并设计对数退火损失以增大分类间隔。
result: BRONet在认证鲁棒性上达到最先进水平，性能显著提升。
conclusion: 提供了一种构建高表达力利普希茨网络的新方法。
---

## Abstract
Lipschitz neural networks are well-known for providing certified robustness in deep learning. In this paper, we present a novel, efficient Block Reflector Orthogonal (BRO) layer that enhances the capability of orthogonal layers on constructing more expressive Lipschitz neural architectures. In addition, by theoretically analyzing the nature of Lipschitz neural networks, we introduce a new loss function that employs an annealing mechanism to increase margin for most data points. This enables Lipschitz models to provide better certified robustness. By employing our BRO layer and loss function, we design BRONet — a simple yet effective Lipschitz neural network that achieves state-of-the-art certified robustness. Extensive experiments and empirical analysis on CIFAR-10/100, Tiny-ImageNet, and ImageNet validate that our method outperforms existing baselines. The implementation is available at [GitHub Link](https://github.com/ntuaislab/BRONet).

---

## 论文详细总结（自动生成）

# 论文总结：通过块反射正交层和对数退火损失增强认证鲁棒性

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：深度神经网络在图像分类等任务中广泛使用，但容易受到微小的对抗性扰动（ℓ₂范数）影响，导致错误分类。现有的防御方法可分为经验防御（如对抗训练）和认证防御。认证防御提供可证的鲁棒性保证，其中 Lipschitz 神经网络因其高效（单次前向传播即可计算认证半径）而受到关注。
- **问题**：构造 Lipschitz 网络的关键在于正交层的设计。现有正交层（如 BCOP、Cayley、SOC、LOT）在计算效率、数值稳定性或表达能力上存在不足（例如需要迭代近似、内存/时间开销大、可能出现非正交性）。
- **目标**：提出一种高效、稳定的正交层（BRO），并设计一种新的损失函数（Logit Annealing loss）来提升 Lipschitz 网络的认证鲁棒性，最终构建 BRONet 网络架构，在多个基准上达到最优性能。

## 2. 方法论

### 2.1 块反射正交层（BRO）

- **核心思想**：利用块反射（Block Reflector）矩阵的低秩参数化来构造正交矩阵。给定低秩参数矩阵 \(V \in \mathbb{R}^{m \times n}\)（\(m \ge n\)，秩为 \(n\)），定义：
  \[
  W = I - 2 V (V^T V)^{-1} V^T
  \]
  该矩阵是对称的正交矩阵（称为块反射器）。具有 \(n\) 个特征值 \(-1\) 和 \(m-n\) 个特征值 \(1\)。
- **卷积版本**：将 2D 卷积通过傅里叶变换（FFT）转化为频域中的逐点矩阵乘法。对频域中每个像素位置的矩阵应用上述 BRO 参数化，再通过逆 FFT 得到实值输出，从而构造正交卷积。算法流程（Algorithm 1）包括：输入零填充、FFT、逐像素正交化、逆FFT、去除填充。这种参数化无需迭代逼近（对比 SOC 的泰勒展开和 LOT 的牛顿法），且通过低秩参数减少计算量和内存。
- **优点**：时间/内存效率高；数值稳定；不依赖迭代近似，保证严格正交性。

### 2.2 对数退火损失（Logit Annealing Loss, LA Loss）

- **理论动机**：利用 Rademacher 复杂度分析表明，Lipschitz 网络的模型容量有限（上界受 Lipschitz 常数限制），导致经验间隔损失风险存在较高下界。现有 CR（Certificate Regularization）项存在梯度不连续、梯度主导、无法合理分配容量等问题。
- **损失函数**：
  \[
  L_{LA}(z, y) = -T\,(1 - p_t)^{\beta} \log(p_t), \quad p_t = \text{softmax}\left(\frac{z - \xi y}{T}\right)
  \]
  其中 \(T\) 为温度，\(\xi\) 为偏移量，\(\beta\) 为退火系数。核心是 \((1-p_t)^{\beta}\) 因子，当 \(p_t\) 接近 1（即该样本的大间隔）时，梯度逐渐退火到零，从而避免过度优化已大间隔的样本，将模型容量分配给其他样本。
- **特性**：梯度连续可导；避免梯度无限增大；平衡准确率与鲁棒性。

### 2.3 BRONet 网络架构

- 由 Stem（Lipschitz 正则化的卷积层）、Backbone（多个 BRO 卷积块）、Neck（下采样+密集层）、Dense（正交密集层）和 Head（LLN 层）组成。激活函数使用 MaxMin。支持调整宽度 \(W\)、深度 \(L\)、密集块数 \(D\) 来控制模型大小。

## 3. 实验设计

### 3.1 数据集
- CIFAR-10, CIFAR-100, Tiny-ImageNet, ImageNet。
- 部分实验使用扩散模型生成的额外合成数据（EDM）：CIFAR-10 4M、CIFAR-100 1M、ImageNet 2M。

### 3.2 基准方法
- 正交层：Cayley、SOC、LOT、Cholesky。
- 其他 Lipschitz 层：AOL、CPL、SLL、Sandwich、Lipschitz-regularized（Lip-reg）。
- 完整网络：LiResNet（Hu et al. 2024）作为强基线。

### 3.3 对比实验
- **主结果（表1）**：在 CIFAR-10/100、ImageNet 上比较 clean accuracy 和 certified accuracy（扰动预算 ε = 36/255, 72/255, 108/255）。
- **扩散数据增强（表2）**：使用额外合成数据训练，对比 LiResNet、LiResNet+LA、BRONet+LA。
- **主干比较（表3）**：固定 LiResNet 架构，替换不同正交层的卷积主干，公平比较（CIFAR-10/100 + EDM）。
- **LipConvNet 基准（表4）**：在轻量级 LipConvNet 上比较 SOC、LOT、BRO 在不同深度-宽度配置下的性能（CIFAR-100、Tiny-ImageNet）。
- **消融实验（表5）**：在 ImageNet 上逐步添加 LA、架构调整、BRO 层，分析每个组件贡献。
- **LA 损失有效性（表6、图3）**：展示认证半径分布的中位数、方差、偏度，以及训练/测试集的 certified accuracy vs. radius 曲线。
- **额外消融**：BRO 秩 n（表12）、LA 超参数（表14）、LOT 数值稳定性实验（图13）。

## 4. 资源与算力

- **硬件**：多数实验使用 Intel Xeon Gold 6226R CPU，192 GB RAM，NVIDIA RTX A6000 GPU（48 GB）。
  - CIFAR-10/100：单张 A6000。
  - Tiny-ImageNet、扩散增强 CIFAR-10/100：两张 A6000（DDP）。
  - ImageNet 实验：8 × NVIDIA H100。
- **训练配置**：CIFAR-10/100 训练 800 epochs，ImageNet 400 epochs；学习率余弦衰减 + 线性 warmup 20 epochs；优化器 NAdam + LookAhead；batch size 256（CIFAR），1024（ImageNet）。
- **时间与内存对比**：图2显示 BRO 在运行时和内存上均优于 SOC 和 LOT，尤其在大深度下优势显著。

## 5. 实验数量与充分性

- **实验充分性评价**：
  - 覆盖了四个不同规模的数据集（CIFAR-10/100, Tiny-ImageNet, ImageNet），从低分辨率到高分辨率。
  - 与当前最优的多个 Lipschitz 方法进行横向比较。
  - 进行了详尽的消融实验：分离 BRO 层、LA 损失、架构改动的影响；在不同网络架构（LiResNet、LipConvNet）上验证 BRO 层的通用效果。
  - 分析了 BRO 的低秩参数（rank-n）影响、LA 损失超参数敏感性、LOT 数值不稳定性。
  - 实验结果客观：多次运行取平均，基线方法或直接引用原文数据或复现；扩散增强实验控制变量一致。
- **局限性**：部分实验（如大扰动 ε=108/255）性能提升不明显；LA 损失的超参数仅在 LipConvNet 上调参，可能未充分优化于所有场景；未在更大规模（如完整 ImageNet）上与其他方法（如随机平滑）直接对比（但论文聚焦于确定性 Lipschitz 方法）。

## 6. 主要结论与发现

1. **BRO 层**：提出的块反射正交层在构建 Lipschitz 网络时，相比 SOC、LOT、Cayley 等现有正交层，具有更低的计算开销、更高的内存效率、更好的数值稳定性，同时在干净精度和认证鲁棒性上达到或超越现有最优水平。
2. **LA 损失**：基于理论分析提出的对数退火损失，有效缓解了 Lipschitz 网络容量有限导致的过调制问题，使得模型能够为更多数据点学习到合适的间隔，从而提升认证鲁棒性，且不牺牲干净精度。
3. **BRONet 网络**：结合 BRO 层和 LA 损失设计的 BRONet，在 CIFAR-10、CIFAR-100、ImageNet 上均取得了当前最优的认证鲁棒性能（尤其在中等扰动预算下）。额外使用扩散合成数据可进一步提升性能。
4. **理论贡献**：从 Rademacher 复杂度角度揭示了 Lipschitz 网络容量与间隔损失风险下界的关系，为 LA 损失的设计提供了理论依据。

## 7. 优点

- **方法创新**：BRO 层利用低秩块反射参数化，避免了迭代近似，是一个简洁而高效的正交化方法。LA 损失基于理论分析，引入退火机制，解决了 CR 项的实际问题。
- **实验全面**：覆盖多个数据集、多种架构、多种对比方法，消融实验系统全面，验证了各组件的有效性。
- **公平性**：主干比较实验严格控制变量（仅换卷积层），保证了比较的公正性。
- **实用价值**：BRO 层的低资源消耗使其易于嵌入复杂网络，LA 损失与多种正交层兼容；所有代码开源，便于复现和应用。
- **清晰的理论支撑**：对正交性、Rademacher 复杂度、损失函数性质均给出了严谨的证明或推导。

## 8. 不足与局限

- **大扰动性能**：在较大扰动预算（如 ε = 108/255）下，BRONet 的提升并不总是显著，有时甚至略低于部分基线，需进一步改进。
- **超参数调优**：LA 损失引入了温度 T、偏移 ξ、退火系数 β 三个超参数，文中仅在特定配置下调优，不同数据集/模型可能需要重新调整，增加了使用成本。
- **适用范围**：方法主要针对 ℓ₂ 范数攻击的认证鲁棒性，对于 ℓ∞ 等其他范数不一定直接适用，且论文未进行深入对比。
- **训练成本**：尽管 BRO 层本身高效，但训练 Lipschitz 网络（尤其结合扩散数据）仍需较大算力（ImageNet 需要 8×H100 且训练 400 epochs），大规模应用仍有门槛。
- **仅限卷积网络**：BRO 层目前实现限于卷积层，对于 Transformer 等架构的扩展未讨论。
- **理论局限**：LA 损失的理论分析主要基于 Rademacher 复杂度的上界，但实际最优间隔与容量关系可能更复杂，退火机制在极端情况下的行为缺乏深入分析。

（完）
