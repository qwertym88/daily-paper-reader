---
title: "FADRM: Fast and Accurate Data Residual Matching for Dataset Distillation"
title_zh: FADRM：用于数据集蒸馏的快速准确数据残差匹配
authors: "Jiacheng Cui, Xinyue Bi, Yaxin Luo, Xiaohan Zhao, Jiacheng Liu, Zhiqiang Shen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=UGjWlxU6GY"
tags: ["query:neural-arch"]
score: 4.0
evidence: 数据级残差连接（数据残差匹配）
tldr: 本文将残差连接的概念引入数据层面，首次提出数据残差匹配用于数据集蒸馏。该方法通过数据级跳连在像素空间优化与原始数据局部信息之间取得平衡，显著提升了计算效率和蒸馏质量。虽然应用于数据蒸馏，但其残差连接思想可启发模型架构设计。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 723, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1452, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 730, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 726, \"height\": 716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1424, \"height\": 1429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1424, \"height\": 1432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1423, \"height\": 1428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1423, \"height\": 1429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1424, \"height\": 1430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1423, \"height\": 1432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1423, \"height\": 1431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1423, \"height\": 1430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1423, \"height\": 1431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ugjwlxu6gy/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1423, \"height\": 1429, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 580, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 558, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 641, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 655, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1377, \"height\": 199, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 711, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 732, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 713, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 562, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 585, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 730, \"height\": 134, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 864, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1009, \"height\": 125, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1370, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1157, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 968, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1018, \"height\": 709, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 750, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 513, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 862, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 749, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 865, \"height\": 696, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 839, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 866, \"height\": 503, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 862, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 866, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ugjwlxu6gy/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 868, \"height\": 618, \"label\": \"Table\"}]"
motivation: 残差连接在模型层面广泛使用，但在数据层面尚未探索。
method: 提出数据残差匹配，在像素空间优化中加入数据级跳连以保留核心信息。
result: 方法在数据集蒸馏任务上速度快、精度高，优于现有方法。
conclusion: 探索了残差连接在新领域的应用潜力。
---

## Abstract
Residual connection has been extensively studied and widely applied at the model architecture level. However, its potential in the more challenging data-centric approaches remains unexplored. In this work, we introduce the concept of ***Data Residual Matching*** for the first time, leveraging data-level skip connections to facilitate data generation and mitigate data information vanishing. This approach maintains a balance between newly acquired knowledge through pixel space optimization and existing core local information identification within raw data modalities, specifically for the dataset distillation task. Furthermore, by incorporating training-time refinements, our method significantly improves computational efficiency, achieving superior performance while reducing training time and peak GPU memory usage by 50\%. Consequently, the proposed method **F**ast and  **A**ccurate  **D**ata **R**esidual **M**atching for Dataset Distillation (**FADRM**) establishes a new state-of-the-art, demonstrating substantial improvements over existing methods across multiple dataset benchmarks in both efficiency and effectiveness. For instance, with ResNet-18 as the student model and a 0.8\% compression ratio on ImageNet-1K, the method achieves 48.4\% test accuracy in single-model dataset distillation and 50.9\% in multi-model dataset distillation, surpassing RDED by +6.4\% and outperforming state-of-the-art multi-model approaches, EDC and CV-DD, by +2.3\% and +4.9\%.

---

## 论文详细总结（自动生成）

# FADRM: Fast and Accurate Data Residual Matching for Dataset Distillation 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：残差连接（Residual Connection）在模型架构层面已被广泛研究（如 ResNet、DenseNet），但它在数据驱动方法（data-centric approaches）中的潜力尚未被探索。随着深度学习模型规模增长（如 LLM、MLLM），对高质量、信息密集的数据需求日益迫切，数据集蒸馏（Dataset Distillation / Condensation）成为压缩大规模数据集、保留关键信息、加速训练的重要方向。然而现有蒸馏方法存在两大问题：**信息蒸发（Information Vanishing）**——在单级优化（Uni-level Framework）中，随优化步骤增加，信息密度先升后降，导致特征退化；**计算成本高昂**——生成大规模蒸馏数据集（如ImageNet-1K 50 IPC）耗时可达数十小时，GPU内存占用大。
- **核心问题**：如何将残差连接思想从模型层延伸到数据层，在数据合成过程中平衡“像素空间优化获得的新知识”与“原始数据中的核心局部信息”，同时提升效率和精度。
- **本文贡献**：首次提出**数据残差匹配（Data Residual Matching）**概念，并构建**FADRM**框架，通过数据级跳连缓解信息蒸发，同时引入混合精度训练和多分辨率优化，使训练时间和峰值GPU内存降低约50%，并在多个标准数据集上超越现有方法。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：在数据合成过程中，将中间优化的蒸馏图像与原始数据补丁（Real Patches）进行加权融合，使优化过程持续保留原始信息，避免信息丢失。这一机制模仿模型层面的残差连接，但作用于数据层面。
- **关键技术组件**：
  - **可调残差连接（Adjustable Residual Connection, ARC）**：在每个残差注入阶段，将当前优化图像与重采样至相同尺寸的原始补丁按比例混合： \(\tilde{x}_t = \alpha \tilde{x}_t + (1-\alpha) \text{Resample}(P_s, D_t)\)，其中 α 为融合比例（实验最优 α=0.5）。注入次数由超参数 k 控制（最优 k=3），总优化迭代被分为 k+1 段，前 k 段末尾执行残差注入，最后一段纯优化。
  - **混合精度训练（Mixed Precision Training, MPT）**：将模型参数从 FP32 转换为 FP16 进行前向和损失计算，但保留关键统计量匹配梯度和总损失梯度在 FP32 中计算，以保持数值稳定性。此举显著减少GPU内存和训练时间约50%。
  - **多分辨率优化（Multi-Resolution Optimization, MRO）**：针对大规模数据集（如ImageNet-1K），先对初始化图像下采样至较小分辨率（如200×200）进行部分迭代，再恢复原始分辨率继续优化。通过交替在不同分辨率上训练，在保证质量的同时降低计算开销。下采样尺寸 Dds 需折中选择（实验最优200）。
- **算法流程**（简化文字描述）：
  1. 从原始数据中采样补丁并下采样至 Dds 作为初始蒸馏图像。
  2. 进行 k 个残差阶段：每个阶段先执行 niter 次梯度优化，然后重采样图像至目标分辨率，并与原始补丁以比例 α 融合。
  3. 最后执行剩余迭代（无残差注入），输出最终蒸馏图像。
- **理论支撑**：
  - 定理1：证明在无原始数据参与的单级优化中，蒸馏数据集与原始数据集之间的互信息存在上界（受模型输出熵限制），即信息有限。
  - 定理2（泛化界分析）：证明当合成数据过度拟合时（Rademacher复杂度增加），通过残差注入结合原始数据可以获得更紧的泛化界。
  - 定理3（数据处理不等式分析）：证明FADRM打破了条件独立性假设，使得蒸馏图像与原始数据之间的互信息严格大于纯单级框架。

## 3. 实验设计

- **数据集**：CIFAR-100 (32×32)、Tiny-ImageNet (64×64)、ImageNet-1K (224×224) 及其子集 ImageNette、ImageWoof。覆盖不同分辨率和规模。
- **基准方法**：对比三种SOTA蒸馏方法——RDED（直接选取原始裁剪补丁，高度参与原始数据）、EDC（极小学习率优化选取补丁，高参与度）、CV-DD（对齐全局BN统计量，低参与度）。此外还与SRe²L++、G-VBSM等对比。
- **评估设置**：
  - 使用预训练教师模型（ResNet-18等）生成蒸馏数据，再用蒸馏数据训练学生模型（ResNet-18/50/101等），在对应测试集上评估Top-1准确率。
  - 训练配置严格遵循EDC的设置：普通设置300 epochs（Tiny-ImageNet IPC=10/50、ImageNet-1K及子集），IPC=1时使用1000 epochs。
  - 同时评估单模型版本（FADRM，仅用ResNet-18蒸馏）和集成版本（FADRM+，使用多种学生模型生成并集成）。
  - 跨架构泛化测试：使用EfficientNet-B0、MobileNetV2、ShuffleNetV2、Swin-Tiny、Wide ResNet等不同架构。
  - 连续性学习（Continual Learning）测试：在Tiny-ImageNet IPC=50上做5-step和10-step类增量学习。
- **消融实验**：考察补丁配置（1×1 vs 2×2）、混合精度MPT有无、多分辨率MRO有无（在ImageNet-1K上）、融合比例α不同取值（0.4~1.0）、残差注入次数k（1~6）、下采样尺寸Dds（160/180/200/224）。

## 4. 资源与算力

- **文中明确说明**：所有实验在单个NVIDIA RTX 4090 GPU上执行。
- **效率测量**：
  - 生成单张图像耗时：FADRM为0.47秒，FADRM+为1.09秒（ImageNet-1K）；对比EDC需4.99秒，CV-DD需8.20秒。
  - GPU峰值内存：FADRM仅2.9 GB，FADRM+为11.0 GB；对比EDC为17.9 GB，CV-DD为23.4 GB。
  - 总训练时间节省举例：生成50 IPC ImageNet-1K，相比EDC节省约54小时，相比SRe²L++节省约28.5小时。
- **其他细节**：教师模型使用官方PyTorch预训练模型或自行训练（其他数据集）。未提及多GPU并行或分布式训练。

## 5. 实验数量与充分性

- **实验数量**：涵盖5个数据集（CIFAR-100、Tiny-ImageNet、ImageNet-1K、ImageNette、ImageWoof），每个数据集在多个IPC（1/10/50）和多个学生架构（ResNet-18/50/101及其他）上测试，主干结果表（Table 2）包含大量数值。消融实验有6+组（补丁数、MPT、MRO、α、k、Dds等）。另外有泛化性表、Rademacher复杂度验证、连续学习实验。
- **充分性与公平性**：
  - 对比方法涵盖三种典型参与程度（高/中/低），且所有方法均使用相同训练配置重新运行（RDED、CV-DD按EDC配置），报告的精度为最高结果，确保公平。
  - 交叉架构泛化实验全面，验证了蒸馏数据的通用性。
  - 理论定理（1~3）与实验（信息熵曲线、Rademacher复杂度）相互印证。
  - **未提供误差棒或标准差**，但论文声称性能提升幅度大，统计意义明显。不过若需严格严谨，建议补充多次运行的平均值和方差。
- **总体评价**：实验设计系统、对比充分、消融细致，基本覆盖了关键因素，可信度较高。

## 6. 主要结论与发现

- **性能优势**：FADRM/FADRM+在所有数据集和IPC设置下均超越现有SOTA。例如ImageNet-1K IPC=10，ResNet-18学生：FADRM 48.4%，FADRM+ 50.9%，分别比RDED高+6.4%，比EDC高+2.3%，比CV-DD高+4.9%。跨架构泛化也全面领先。
- **效率优势**：生成速度最快、GPU内存最低，训练时间减少约50%。
- **信息蒸发缓解**：通过ARC机制，蒸馏图像的信息密度随优化步数稳定提升（而非下降），可视化也显示FADRM保留更多细节。
- **理论验证**：证明FADRM可提供更紧的泛化界，且互信息上界严格大于纯单级框架。
- **最佳配置**：融合比例α=0.5、残差注入次数k=3、下采样尺寸Dds=200（ImageNet-1K）、1×1补丁优于2×2。

## 7. 优点（亮点）

- **创新性**：首次将残差连接从模型架构延伸到数据层面，思想新颖，为数据蒸馏提供了新范式。
- **理论与实验紧密结合**：提出定理1-3，分析信息上界、泛化界和互信息改进，并用Rademacher复杂度、信息熵曲线等实验验证，说服力强。
- **高效实用**：MPT + MRO 双项加速，使大规模蒸馏变得可行（单卡RTX 4090即可），大幅降低资源门槛。
- **泛化性**：跨架构、跨数据集、持续学习场景均表现优异，证明蒸馏数据质量高、通用性强。
- **消融全面**：对每个关键组件（α、k、Dds、MPT、MRO）均有仔细分析，结论清晰。

## 8. 不足与局限

- **实验局限**：
  - 未提供多次运行的统计误差（如标准差或置信区间），仅报告单次或最优结果，可能导致结果波动未知。
  - 仅测试了图像分类任务，未涉及目标检测、语义分割或其他模态（文本、时间序列等），通用性需进一步验证。
  - 未与更近期的蒸馏方法（如SRe²L++的变体等）在同等资源下全面对比（EDC等已包含但仍有其他方法）。
- **方法依赖**：
  - ARC依赖于原始数据集补丁的可用性，若原始数据不可访问或隐私受限，则无法直接应用（但论文提到这作为优势而非劣势）。
  - 融合比例α需手动选择（通过实验最优0.5），不同场景可能需要重新调优；自适应方法（附录C.1）仅做了初步尝试，未作为主要部分。
  - MRO中下采样尺寸Dds需人工设定，虽有自适应版本但性能略低，未推广。
- **理论部分**：定理的假设（如Rademacher复杂度关系、Lipschitz连续性）在实际中是否严格成立需要更多实证，但论文已通过实验支持。
- **公平性与社会影响**：论文指出蒸馏数据可能继承原始数据偏差，需谨慎审计；FADRM的高效性可能降低滥用门槛（如用于监控等敏感场景），需伦理监管。
- **应用限制**：当前主要适用于可见数据集，对于域外或长尾分布可能效果下降；未探讨对噪声或对抗扰动的鲁棒性。

（完）
