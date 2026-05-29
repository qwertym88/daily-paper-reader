---
title: The Quest for Universal Master Key Filters in DS-CNNs
title_zh: DS-CNN中通用主密钥滤波器的探索
authors: "Zahra Babaiee, Peyman Kiasari, Daniela Rus, Radu Grosu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=lYnNzmFt7r"
tags: ["query:neural-arch"]
score: 8.0
evidence: 深度可分离卷积的通用主密钥过滤器，实现高效初始化
tldr: "深度可分离卷积网络（DS-CNN）通常使用数千个滤波器。本文发现所有DS-CNN收敛到一组仅有8个通用滤波器（主密钥），且其他滤波器是它们的仿射变换。通过无监督搜索提取这些滤波器，并用其冻结初始化网络，在ImageNet上达到80%以上准确率，甚至超过可训练模型。该发现为设计极高效DS-CNN提供了基础。"
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1130, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 733, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 205, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1446, \"height\": 208, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1440, \"height\": 859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1186, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lynnzmft7r/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1449, \"height\": 529, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1470, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1458, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1424, \"height\": 637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 769, \"height\": 708, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 763, \"height\": 709, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1033, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 703, \"height\": 787, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 691, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 690, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 669, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 686, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 689, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 689, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 689, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lynnzmft7r/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 682, \"height\": 224, \"label\": \"Table\"}]"
motivation: 探索深度可分离卷积网络滤波器的通用性，以实现极简初始化。
method: 通过无监督搜索跨不同架构和数据集提取8个通用滤波器。
result: "冻结初始化这8个滤波器即可在ImageNet上获得80%以上准确率。"
conclusion: 验证了DS-CNN滤波器的高度冗余性，为实现高效网络提供新方向。
---

## Abstract
A recent study has proposed the ``Master Key Filters Hypothesis" for convolutional neural network filters. This paper extends this hypothesis by radically constraining its scope to a single set of just 8 universal filters that depthwise separable convolutional networks inherently converge to. While conventional DS-CNNs employ thousands of distinct trained filters, our analysis reveals these filters are predominantly linear shifts (ax+b) of our discovered universal set. Through systematic unsupervised search, we extracted these fundamental patterns across different architectures and datasets. Remarkably, networks initialized with these 8 unique frozen filters achieve over 80\% ImageNet accuracy, and even outperform models with thousands of trainable parameters when applied to smaller datasets. The identified master key filters closely match Difference of Gaussians (DoGs), Gaussians, and their derivatives, structures that are not only fundamental to classical image processing but also strikingly similar to receptive fields in mammalian visual systems. Our findings provide compelling evidence that depthwise convolutional layers naturally gravitate toward this fundamental set of spatial operators regardless of task or architecture. This work offers new insights for understanding generalization and transfer learning through the universal language of these master key filters.

---

## 论文详细总结（自动生成）

### 论文总结：《The Quest for Universal Master Key Filters in DS-CNNs》

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：深度可分离卷积网络（DS-CNN）通常使用数千个经过训练的空间滤波器（例如 ConvNeXt v2 Huge 模型有约 5 万个滤波器）。先前研究（“Master Key Filters Hypothesis”）提出存在一组通用的“主密钥滤波器”，但未限定其数量或形式。
- **核心问题**：DS-CNN 中这些数以千计的滤波器是否真正需要如此多的多样性？是否存在一组极少的通用滤波器，能够通过线性变换（ax+b）近似绝大多数训练好的滤波器，并足以维持甚至提升网络性能？
- **整体含义**：论文发现所有 DS-CNN 在训练后收敛到仅 **8 个通用滤波器**（称为“万能主密钥滤波器”），其他滤波器几乎都是这些滤波器的仿射变换。这一发现极大压缩了滤波器的理论空间，揭示了 DS-CNN 内部的高度冗余性，并为设计极高效的网络初始化方法提供了理论基础。

#### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：通过无监督方法从预训练模型中提取最小的通用滤波器集合。主要步骤：
  1. **自动编码器降维**：
     - 收集多种 DS-CNN 架构（ConvNeXt v2、ConvNeXt、MogaNet、HorNet、ConvMixer）中所有 7×7 的深度卷积滤波器，归一化后使用一个将每个滤波器压缩为 **1 维编码**（通过 sigmoid 映射到 [0,1]）的自动编码器。
     - 解码器重建滤波器，形成连续的一维潜在空间。
  2. **候选滤波器采样**：
     - 从编码器的 1 维潜在空间中均匀采样（例如 50 个点），通过解码器生成候选滤波器。
  3. **线性近似替换**：
     - 对每个原始滤波器 \( \mathbf{f}_c \)，找到最佳标量系数 \( a, b \)（通过线性回归）使得 \( \mathbf{f}_c \approx a \mathbf{f}'_k + b \)，其中 \( \mathbf{f}'_k \) 是候选滤波器。利用归一化技巧简化计算：\( a = \langle \hat{\mathbf{x}}, \mathbf{y} \rangle, \ b = \bar{y} \)。
  4. **贪婪搜索确定最小滤波器集**：
     - 基于 ConvNeXt v2 Tiny 模型，从 50 个候选滤波器开始，逐步移除对模型精度影响最小的滤波器，直到精度显著下降（曲线出现“肘部”）。搜索收敛到 **8 个关键滤波器**（图 4）。
     - 第二轮回合：在 10 个最佳滤波器周围局部采样扩展搜索空间，再次贪婪搜索，最终确认 8 个滤波器。
  5. **数学形式**：这 8 个滤波器对应经典图像处理算子：
     - 滤波器 1-4：中心差分算子（近似高斯导数）；
     - 滤波器 5-6：一阶高斯导数（x 和 y 方向）；
     - 滤波器 7：高斯差分（DoG，类似拉普拉斯-高斯）；
     - 滤波器 8：高斯平滑核。
- **训练策略**：利用这 8 个固定滤波器初始化网络，仅允许偏置项（bias）可学习。由于 depthwise 卷积的线性性质，缩放系数 \( a \) 可吸收到后续的点卷积层，因此滤波器形式简化为 \( \mathbf{f} + b \)，bias 可学习。

#### 3. 实验设计：数据集、基准、对比方法
- **数据集**：
  - ImageNet (1.2M 训练样本，1000 类)
  - CIFAR-10 (50k 样本)
  - STL-10 (5k 样本)
  - Oxford 102 Flowers (2,040 训练样本)
  - Oxford-IIIT Pets (3,680 训练样本)
- **基准模型**：
  - ConvNeXt v2 系列：Pico, Tiny, Base, Large, Huge
  - HorNet 系列：Tiny, Small
- **对比方法**：
  - **原始模型**（全训练）及其带有 FCMAE 预训练的版本。
  - **候选滤波器替换**：使用不同数量（50、25、10 个）的均匀采样候选滤波器的线性近似替换所有原始滤波器（无微调）。
  - **随机 8 个滤波器替换**（作为对照）：性能几乎崩溃，证明 8 个发现滤波器的非随机性。
  - **ImageNet 迁移学习**：在小型数据集上将预训练权重迁移并微调，与使用 8 个固定滤波器从头训练的模型对比。
  - **多模型尺寸验证**：ConvNeXt Atto、Femto、Pico、Tiny 在 Flowers 和 Pets 上测试。

#### 4. 资源与算力
- **ImageNet 训练与微调**：使用 8 块 NVIDIA TITAN RTX GPU。
- **其他数据集实验**：使用 2 块 NVIDIA TITAN RTX GPU。
- **训练时间**：遵循原始论文的 300 周期训练历程（ImageNet）或相应微调周期。
- **注**：论文未提供确切 GPU 小时数，但明确说明硬件和数量。

#### 5. 实验数量与充分性
- **实验组数**：
  - 表 1：5 种 ConvNeXt v2 模型 + 2 种 HorNet 模型，在 3 种候选滤波器数量下替换精度。
  - 表 2：ConvNeXt v2 4 种模型 + HorNet 1 种模型，使用 8 个固定滤波器从头训练 vs 原始训练 vs FCMAE 预训练。
  - 表 3：4 种数据集、多种模型大小（Atto, Femto, Pico, Tiny）的完整比较：基线、ImageNet 迁移、8 滤波器从头训练。
  - 附加分析：滤波器类型分布（图 6）、近似质量（图 7）、训练曲线（图 8）、消融实验（贪婪搜索过程）。
- **充分性评价**：实验覆盖了多种架构（ConvNeXt v2系列、HorNet）、多种规模（从 Pico 到 Huge）、多个数据集（从 ImageNet 到小型数据集），并包含充分的消融（不同候选数量、随机对照、交叉架构泛化）。实验设计较为全面，对比公平（使用相同超参数）。

#### 6. 论文的主要结论与发现
1. **DS-CNN 滤波器高度冗余**：训练好的数千个滤波器绝大多数可以表示为极少数（8 个）基础滤波器的仿射变换。
2. **8 个通用滤波器的存在性**：通过贪婪搜索，跨模型和数据集找到了相同的 8 个滤波器，且它们在架构间（ConvNeXt↔HorNet）可迁移。
3. **冻结 8 滤波器训练的卓越性能**：
   - ImageNet 上，ConvNeXt v2 Tiny 达 82.7%（仅比全训练低 0.2%）；Huge 达 85.4%（仅低 0.4%）。
   - 在小型数据集上（Flowers, Pets），冻结 8 滤波器甚至显著优于 ImageNet 迁移学习（最高提升 34.5%）。
4. **与经典理论的联系**：这些滤波器对应高斯族函数（DoG、高斯导数等），与尺度空间理论及哺乳动物视觉感受野一致。
5. **实践意义**：提供了一种极简的初始化方法，可用于高效网络设计/迁移学习，挑战了“滤波器随着深度加深必须多样化”的传统观点。

#### 7. 优点
- **方法简洁有力**：仅用 8 个固定滤波器实现高性能，揭示了深度学习中的惊人规律性。
- **系统性的验证**：跨架构、跨数据集、多尺寸消融，结果一致且可靠。
- **实验客观公平**：所有对比使用原文超参数，避免调优偏差；包含随机对照排除偶然性。
- **理论与实验结合**：将经验发现的滤波器与经典图像处理算子对应，增强了解释性。
- **实用价值**：为资源受限场景（小型数据集、边缘设备）提供有效的初始化策略。

#### 8. 不足与局限
- **仅限于 DS-CNN**：方法直接针对深度可分离卷积，未在传统密集卷积网络（如 ResNet、VGG）上验证，适用性有限。
- **滤波器尺寸限定**：所有实验仅使用 7×7 滤波器，未测试其他尺寸（如 3×3、5×5）的通用性。
- **搜索过程需预训练模型**：8 个滤波器的发现依赖于已有预训练模型，并非完全从零设计。
- **精度轻微下降**：在大模型上仍有 0.2%~1% 的精度损失，尽管较小，但在高精度任务中可能不可忽略。
- **未深入探究理论原因**：为何 8 个滤波器足够、它们的最优性（是否可减少或替换）缺乏理论保证。
- **计算资源较大**：ImageNet 训练需 8 张 TITAN RTX，但相比于原训练成本并未显著降低。

（完）
