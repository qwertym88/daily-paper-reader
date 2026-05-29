---
title: "Mind the Gap: Removing the Discretization Gap in Differentiable Logic Gate Networks"
title_zh: 弥合差距：消除可微分逻辑门网络中的离散化间隙
authors: "Shakir Yousefi, Andreas Plesner, Till Aczel, Roger Wattenhofer"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=chYXaetMmz"
tags: ["query:neural-arch"]
score: 7.0
evidence: 新颖的可微分逻辑门网络设计，使用Gumbel噪声提升效率和精度
tldr: 可微分逻辑门网络（DLGN）在训练和推理之间存在离散化间隙，导致性能下降且大量神经元闲置。本文通过注入Gumbel噪声并使用直通估计器来缩小间隙，使得网络能更高效地学习，训练时间从数天缩短到数小时，同时减少了未使用神经元的比例，提升了部署准确性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 664, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 984, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1425, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 699, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1453, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1456, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1452, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1315, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1421, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1453, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1467, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-chyxaetmmz/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1467, \"height\": 635, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-chyxaetmmz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-chyxaetmmz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1261, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-chyxaetmmz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 957, \"height\": 822, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-chyxaetmmz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1427, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-chyxaetmmz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 635, \"height\": 325, \"label\": \"Table\"}]"
motivation: DLGN训练慢且存在性能下降的离散化间隙，阻碍实际部署。
method: 在训练中注入Gumbel噪声并采用直通估计器，缩小训练与推理间的间隙。
result: 训练速度大幅提升，未使用神经元减少，分类精度接近标准网络。
conclusion: 有效弥合离散化间隙，使DLGN成为可行的效率解决方案。
---

## Abstract
Modern neural networks exhibit state-of-the-art performance on many existing benchmarks, but their high computational requirements and energy usage cause researchers to explore more efficient solutions for real-world deployment.
    Differentiable logic gate networks (DLGNs) learns a large network of logic gates for efficient image classification. However, learning a network that can solve simple problems like CIFAR-10 or CIFAR-100 can take days to weeks to train. Even then, almost half of the neurons remains unused, causing a \emph{discretization gap}. This discretization gap hinders real-world deployment of DLGNs, as the performance drop between training and inference negatively impacts accuracy.
    We inject Gumbel noise with a straight-through estimator during training to significantly speed up training, improve neuron utilization, and decrease the discretization gap. 
    We theoretically show that this results from implicit Hessian regularization, which improves the convergence properties of DLGNs. We train networks $4.5 \times$ faster in wall-clock time, reduce the discretization gap by 98\%, and reduce the number of unused gates by 100\%.

---

## 论文详细总结（自动生成）

# 论文详细总结：Mind the Gap: Removing the Discretization Gap in Differentiable Logic Gate Networks

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：现代神经网络性能优异，但计算和能耗需求高昂。可微分逻辑门网络（DLGN）通过将网络表示为逻辑门组合，旨在利用硬件原生布尔运算实现高效推理。
- **核心问题**：DLGN存在两个关键缺陷：
  - **离散化间隙（Discretization Gap）**：训练时使用连续松弛（soft gates），推理时需离散化为硬门，导致性能下降（约3%准确率损失）。
  - **训练缓慢**：由于依赖连续松弛，损失景观尖锐，梯度信号差，训练CIFAR-10/100需数天至数周。
  - **神经元利用率低**：几乎一半的神经元在训练后“未使用”（即门概率分布未坍缩）。
- **研究动机**：通过平滑损失景观来缩小离散化间隙、加速收敛，并使DLGN在实际部署中可行。

## 2. 方法论

### 核心思想
- 在门选择过程中注入Gumbel噪声，并使用直通估计器（Straight-Through Estimator, STE），使训练过程更接近推理时的离散选择，同时保持可微性。
- 该方法隐式地正则化Hessian迹，促进更平坦的极小值，从而：
  - 降低对参数离散化的敏感性（缩小间隙）
  - 改善梯度信号（加速收敛）
  - 促使神经元门概率坍缩（提高利用率）

### 关键技术细节
1. **Gumbel-Softmax采样**：每个神经元维护16个逻辑门的logits \( z \in \mathbb{R}^{16} \)，采样Gumbel噪声 \( g \sim \text{Gumbel}(0,1) \)，计算：
   \[
   \pi_i^{\text{Gumbel}} = \frac{\exp((\log \pi_i + g_i)/\tau)}{\sum_j \exp((\log \pi_j + g_j)/\tau)}
   \]
   其中 \(\tau\) 为温度参数。
2. **硬门选择（前向）**：在正向传播中，选择最大扰动logit对应的门 \( h_k \)，即：
   \[
   f_{\text{discrete}}(a,b) = h_k(a,b)
   \]
3. **梯度近似（后向）**：使用Soft Gumbel-Softmax的梯度作为硬选择的梯度近似（STE估计器）：
   \[
   \frac{\partial f_{\text{discrete}}}{\partial z_i} := \frac{\partial f_{\text{soft}}}{\partial z_i}
   \]
4. **温度τ的作用**：调节隐式平滑强度，τ越小对Hessian迹的惩罚越大，损失景观越平坦。

### 理论贡献（Lemma 1）
- 注入Gumbel噪声后的期望损失可展开为：
  \[
  J(z) = L(\text{softmax}(z/\tau)) + \frac{\pi^2}{12\tau^2} \text{tr}(H_f(z/\tau)) + O(\tau^{-3})
  \]
  这证明了Gumbel噪声起到了隐式Hessian迹正则化的作用，促使优化器找到曲率更小的平坦极小值。

## 3. 实验设计

### 数据集
- **主要数据集**：CIFAR-10、CIFAR-100
- **辅助数据集（附录）**：MNIST、FashionMNIST、KMNIST、QMNIST、EMNIST（balanced/letters）等，用于验证离散化间隙在不同任务中的表现。

### Benchmark
- **基线方法**：标准DLGN（Petersen et al., 2022），使用相同的网络架构（宽度256k、深度12等，除非特别说明）。
- **对比指标**：
  - 离散化间隙 = |soft准确率 - 离散准确率|
  - 训练收敛速度（迭代次数和墙钟时间）
  - 神经元利用率（通过门熵分布衡量）

### 对比方法
- **Gumbel LGN（本文）**：在DLGN基础上加入Gumbel噪声+STE。
- **消融实验变体**：
  - Gumbel Soft（仅用Gumbel噪声，不使用STE）
  - Gumbel + ST（完整方法）
  - 不同温度τ（0.01, 0.05, 0.1, 0.15, 0.2, 0.25, 0.5, 1, 2）
- **其他对比**：不同深度（6,8,10,12）、不同宽度（256k, 2048k）下的表现。

## 4. 资源与算力

- **GPU型号**：RTX 3090 和 RTX 2080 Ti（内部集群）。
- **总GPU小时**：论文明确记录为 **1284 GPU小时**（包括实验和测试）。
- **单实验限制**：默认训练限制为 **48 GPU小时**（每个实验在48小时内截止）。
- **其他**：作者提到由于计算资源约束，未进行多次种子重复实验（报告误差条）。

## 5. 实验数量与充分性

### 实验组数
- **主要实验**：CIFAR-10和CIFAR-100上的深度/宽度缩放实验（图3、4、5），共约8个对比曲线。
- **消融实验**：
  - STE vs. Gumbel Soft（图6）
  - 温度τ扫描（图7、表1）共9个τ值
  - 深度扫描（4个深度）
  - 宽度扫描（1个宽网络）
- **Hessian迹估计**（图7左）：基于200个Rademacher向量，采样于训练过程中。
- **损失曲面可视化**（图8）：DLGN vs. Gumbel LGN。
- **神经元熵分布**（图9）：DLGN vs. Gumbel LGN，每层分布。
- **门分布分析**（附录C）：按层和按类统计。
- **辅助数据集**（附录I）：7个MNIST类数据集，各5次运行取平均。

### 充分性评价
- **优点**：覆盖了关键的消融（STE、温度、深度/宽度），并提供了理论解释和可视化证据。
- **不足**：
  - **未报告误差条**：所有实验仅展示单次运行（作者因计算约束未进行多种子重复），这降低了统计显著性。
  - **数据集有限**：主要依赖CIFAR-10/100，复杂数据集（如ImageNet）未涉及。
  - **超参数调优**：温度τ需要手动调整，且未使用调度策略。
  - **实验公平性**：基线DLGN的超参数取自原文，但Gumbel LGN与基线共享大部分超参数（学习率等），未针对Gumbel调优可能略有利基线的比较。

## 6. 主要结论与发现

1. **显著加速训练**：Gumbel LGN在墙钟时间上比DLGN快 **4.5倍**（迭代次数快4.75倍，每次迭代开销仅增加约5%）。
2. **几乎消除离散化间隙**：离散化间隙降低 **98%**（从约3%降至几乎为零）。
3. **100%神经元利用率**：Gumbel LGN中所有神经元的门熵近乎零（全部坍缩），而DLGN有约49.81%的神经元未使用。
4. **深度友好**：随着网络加深，DLGN的间隙增大，而Gumbel LGN保持稳定。
5. **理论机制**：Gumbel噪声通过隐式Hessian迹正则化平滑损失景观，验证了Hessian迹随τ减小而下降（图7左），损失曲面更平坦（图8）。
6. **温度存在黄金区间**：τ≈0.25时收敛最快，τ过高(>1)或过低(<0.1)则变慢；τ=1时最终准确率略高但收敛更慢。

## 7. 优点

- **方法简洁有效**：仅需在DLGN训练中注入Gumbel噪声并采用STE，无需改变网络架构，易于集成。
- **理论深度**：提供了Gumbel噪声与Hessian正则化之间的严格数学联系，支撑了实验观察。
- **针对性指标**：提出并量化了“离散化间隙”和“神经元利用率”这两个重要但未被此前工作充分分析的指标。
- **可视化丰富**：损失曲面、Hessian迹、门熵分布等分析增强了说服力。
- **可移植性**：作者指出该方法与卷积DLGN（Petersen et al., 2024）正交，可推广。

## 8. 不足与局限

- **实验覆盖不足**：
  - 仅在CIFAR-10/100上做主要验证，缺乏ImageNet等更大规模数据集的结果。
  - 未进行多次种子实验，无法评估方差和统计显著性。
- **偏差风险**：
  - 温度τ需要手动调优，文中未讨论自动调节策略（如调度），实际应用需额外调参。
  - 训练时间限制为48小时，可能导致DLGN未达到最佳性能，而Gumbel LGN已收敛，比较可能不充分公平。
- **理论限制**：
  - Lemma 1假设损失函数二次可微且Hessian Lipschitz，实际DLGN中softmax的损失函数可能存在非光滑性，但近似成立。
  - 隐式正则化分析仅针对Gumbel噪声，未与显式SAM等其他平滑方法比较。
- **应用限制**：
  - 逻辑门网络本身只适用于二值化输入（如二值化图像），不直接适用于一般连续数据。
  - 推理效率虽高，但训练仍需GPU，且噪声采样带来额外开销（约5%）。
- **未解决问题**：宽度与深度的交互作用、更复杂的网络拓扑（如卷积DLGN）是否继承相同优势未充分探索。

---

（完）
