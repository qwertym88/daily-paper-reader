---
title: Dynamical Low-Rank Compression of Neural Networks with Robustness under Adversarial Attacks
title_zh: 具有对抗鲁棒性的神经网络动态低秩压缩
authors: "Steffen Schotthöfer, H. Lexie Yang, Stefan Schnake"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=7AwFJzgIUW"
tags: ["query:neural-arch"]
score: 7.0
evidence: 动态低秩压缩结合谱正则化，实现高效且鲁棒的神经网络
tldr: 神经网络压缩常牺牲对抗鲁棒性。本文提出动态低秩训练方案，结合新颖的谱正则化器控制低秩核的条件数，从而在压缩时保持鲁棒性。该方法与模型和数据无关，支持自适应秩选择。在多个架构和数据集上，压缩后的模型在准确率和鲁棒性上均优于现有方法。该工作为高效且鲁棒的模型压缩提供了实用工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-7awfjzgiuw/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 822, \"height\": 261, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7awfjzgiuw/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1407, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7awfjzgiuw/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 596, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7awfjzgiuw/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1243, \"height\": 814, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7awfjzgiuw/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1246, \"height\": 825, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-7awfjzgiuw/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1247, \"height\": 814, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 728, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1447, \"height\": 586, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 729, \"height\": 474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 687, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 570, \"height\": 159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1444, \"height\": 699, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1207, \"height\": 571, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1421, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-7awfjzgiuw/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1441, \"height\": 433, \"label\": \"Table\"}]"
motivation: 解决模型压缩与对抗鲁棒性冲突的问题，实现二者兼顾。
method: 提出动态低秩训练与谱正则化，自动确定层秩并控制条件数以提升鲁棒性。
result: 在多种架构和攻击下，压缩模型保持了高准确率和鲁棒性。
conclusion: 所提方法有效平衡压缩与鲁棒性，且泛化性强。
---

## Abstract
Deployment of neural networks on resource-constrained devices demands models that are both compact and robust to adversarial inputs. However, compression and adversarial robustness often conflict. In this work, we introduce a dynamical low-rank training scheme enhanced with a novel spectral regularizer that controls the condition number of the low-rank core in each layer. This approach mitigates the sensitivity of compressed models to adversarial perturbations without sacrificing clean accuracy. The method is model- and data-agnostic, computationally efficient, and supports rank adaptivity to automatically compress the network at hand. Extensive experiments across standard architectures, datasets, and adversarial attacks show the regularized networks can achieve over 94 compression while recovering or improving adversarial accuracy relative to uncompressed baselines.

---

## 论文详细总结（自动生成）

# 论文《Dynamical Low-Rank Compression of Neural Networks with Robustness under Adversarial Attacks》详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：深度神经网络在资源受限设备（如无人机、监控传感器）上部署时，面临三个相互冲突的目标：**压缩**（降低内存和计算成本）、**高准确率**（保持任务性能）和**对抗鲁棒性**（抵御输入扰动或攻击）。已有研究表明，低秩压缩会降低模型对抗鲁棒性，而提升鲁棒性的技术（如对抗训练）往往增加计算开销并损害干净准确率。如何同时实现高压缩、高精度和高鲁棒性是一个关键挑战。
- **整体含义**：论文旨在打破压缩与鲁棒性之间的矛盾，提出一种既能大幅压缩网络又能保持甚至提升对抗鲁棒性的训练方法，为边缘设备上的可信AI部署提供可行方案。

## 2. 方法论：核心思想、关键技术细节、算法流程

### 核心思想
- 利用**动态低秩训练（DLRT）**将网络层权重矩阵分解为 \( W = U S V^\top \)，其中 \( U, V \) 为正交基，\( S \) 为 \( r \times r \) 核心矩阵。网络的对抗敏感性可由每层条件数 \( \kappa(S) \) 的上界（公式 (1)）控制。
- 提出**谱正则化器 \( \mathcal{R}(S) \)**，惩罚 \( S^\top S \) 与缩放单位矩阵的偏离，从而降低条件数，提升鲁棒性。

### 关键技术细节
- **正则化器定义**：
  \[
  \mathcal{R}(S) = \| S^\top S - \alpha_S^2 I \|, \quad \alpha_S^2 = \frac{1}{r} \|S\|^2
  \]
  该正则化器等于归一化的奇异值方差（公式 (3)），是酉不变的，即只依赖 \( S \) 而非 \( U,V \)。
- **梯度闭合形式**：
  \[
  \nabla \mathcal{R}(S) = \frac{2 S (S^\top S - \alpha_S^2 I)}{\mathcal{R}(S)}
  \]
  计算复杂度为 \( O(r^3) \)，对 \( r \ll n \) 高效。
- **条件数上界**（Proposition 2）：\( \kappa(S) \leq \exp\left( \frac{1}{\sqrt{2}\, \varsigma_r(S)^2} \mathcal{R}(S) \right) \)，说明通过最小化 \( \mathcal{R}(S) \) 可直接控制条件数。
- **稳定性分析**（Proposition 3）：在最小二乘回归场景下，正则化后的梯度流具有长期稳定性，证明正则化不会导致损失发散。

### 算法流程（RobustDLRT，Algorithm 1）
1. **前向计算**：对当前低秩表示 \( U S V^\top \) 计算损失 \( L \)。
2. **基底扩充**：计算梯度 \( \nabla_U L, \nabla_V L \)，将基与梯度拼接并正交化，得到扩大的基底 \( \hat{U}, \hat{V} \)（秩翻倍）。
3. **扩大的核心矩阵**：\( \hat{S} \leftarrow \hat{U}^\top U S V^\top \hat{V} \)。
4. **正则化核心训练**：在缩小的潜在空间中对 \( \hat{S} \) 进行若干步梯度下降（SGD/Adam），梯度包含损失项和正则项 \( -\beta \nabla \mathcal{R}(\hat{S}) \)。
5. **截断**：对更新后的 \( \hat{S} \) 进行截断 SVD，丢弃小于阈值 \( \vartheta \) 的奇异值，更新 \( U, S, V \) 并恢复正交性。
- 扩展至卷积层：通过 Tucker 分解将卷积核压缩，仅对特征模式的核心矩阵进行正则化。

## 3. 实验设计：数据集、基准、对比方法

### 数据集
- **UCM**：遥感土地分类数据集（21类，2100张256×256图像）。
- **CIFAR-10**：10类，60000张32×32彩色图像。
- **ImageNet-1k**：1000类，约120万张图像（用于大模型ViT-32l）。

### 网络架构
- VGG16、VGG11（卷积网络），ViT-16b、ViT-32l（视觉Transformer）。

### 攻击类型（白盒和黑盒）
- ℓ₂-FGSM、ℓ₁-FGSM、Jitter、Mixup、PGD（附录A.2）。覆盖不同扰动度量（ℓ₂、ℓ₁、随机噪声、尺度不变攻击）。

### 对比方法
- **Baseline**：全秩原始网络。
- **未正则化低秩训练（DLRT，β=0）**。
- **LoRA**（同时梯度下降，不保证正交）。
- **文献方法**：Cayley SGD、Projected SGD、CondLR、SVD prune、GeoLoRA等（对比来自原论文[35]）。

### 其他实验设置
- 消融实验：不同正则化强度 β 的影响（Fig.2）。
- 黑盒攻击：攻击者不知道压缩，使用基线生成对抗样本测试压缩网络。
- 对抗训练：将部分对抗样本加入训练。

## 4. 资源与算力

- **硬件**：5块 NVIDIA RTX A6000、3块 RTX 4090、8块 A100 80GB。每项实验使用单GPU。
- **时间**：每项实验（训练+攻击测试）约30分钟。ImageNet ViT-32l：DLRT 26分07秒，RobustDLRT 27分51秒（开销约3%）。
- **未明确说明**：未给出总GPU小时数，但根据配置可以估算。

## 5. 实验数量与充分性

- **实验组数**：至少包含3个数据集 × 3个架构 × 5种攻击类型 × 多种 β（通常5-10个值） × 10次随机运行（部分5次）。此外还有黑盒攻击、对抗训练、与文献对比（Table 4, Table 7）。附录包含大量扩展结果。
- **充分性**：非常充分。覆盖了不同规模的数据集（小规模UCM、中等CIFAR、大规模ImageNet）、不同复杂度架构（CNN、ViT）、多种攻击（单步、迭代、非梯度等）。统计上报告了均值和标准差（多数小于1%），β 通过初步扫描选择，避免了手动调参偏差。
- **公平性**：对比方法均来自官方/已有论文结果（Table 4, Table 7），并注明来源。自己的方法在同一超参数下比较（干净准确率、压缩率等）。

## 6. 主要结论与发现

- **压缩率与鲁棒性兼得**：RobustDLRT 可在高达 **94% 参数缩减**下，干净准确率几乎无损失，且对抗鲁棒性显著优于未正则化的 DLRT，在多数攻击下达到或超过全秩基线水平。
- **理论验证**：条件数上界与正则化器值正相关，训练中条件数随正则化下降（Fig.2）。
- **优于现有文献**：在 CIFAR-10 VGG16 下，ℓ₁-FGSM 攻击中超过所有列出的压缩方法（如 CondLR、LoRA），且压缩率更高（Table 4）。
- **黑盒与对抗训练兼容**：正则化网络在攻击者不知识别时表现极佳；与对抗训练结合进一步提高鲁棒性。
- **秩自适应**：自动调整秩，无需手动设定，且压缩率与未正则化 DLRT 相当。

## 7. 优点（方法或实验设计亮点）

- **高效性**：正则化器仅操作小核心矩阵 \( S \)（\( O(r^3) \)），总计算量与 LoRA 相当。
- **理论与经验双支撑**：给出条件数上界、稳定性分析，并验证了正则化与条件数下降的关联。
- **模型与数据无关**：适用于任意带正交化步骤的低秩训练方法（如 DLRT）。
- **正交性关键**：明确指出正交基的重要性（Remark 1 和 Table 1 验证），避免 LoRA 非正交导致的控制失效。
- **适用范围广**：支持全连接层和卷积层（Tucker 分解），并能在大型模型（ViT-32l, ImageNet）上高效运行。
- **实验全面**：涵盖多种数据集、架构、攻击、消融、黑盒、对抗训练，并提供了可复现的详细设置（Appendix B）。

## 8. 不足与局限

- **正则化器非凸**：虽然证明了稳定性，但收敛性分析仅限于简单平方损失，对神经网络非凸损失的理论保证尚不充分。
- **超参数 β 需调优**：不同攻击和网络需手动选择最佳 β（见 Table 9），虽可通过简单扫描获得，但缺乏自适应选择机制。
- **对某些攻击提升有限**：例如 Jitter 攻击下恢复幅度不如 Mixup 明显（可能因为 Jitter 更依赖其他因素）。
- **依赖正交性**：若基不正交（如 LoRA），正则化无效且精度下降（Table 1），限制了与某些微调方法的兼容性。
- **未在 NLP 或更大模型（LLM）上验证**：论文主要聚焦视觉任务，方法是否适用于语言模型待验证。
- **截断阈值选择**：秩自适应依赖阈值 \( \vartheta \)，该超参数仍需初步扫描（但经验值较小）。

（完）
