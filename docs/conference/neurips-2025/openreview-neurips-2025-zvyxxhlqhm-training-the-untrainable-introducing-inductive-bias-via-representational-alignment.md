---
title: "Training the Untrainable: Introducing Inductive Bias via Representational Alignment"
title_zh: 训练不可训练的：通过表征对齐引入归纳偏置
authors: "Vighnesh Subramaniam, David Mayo, Colin Conwell, Tomaso Poggio, Boris Katz, Brian Cheung, Andrei Barbu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zvYxXhlQHM"
tags: ["query:neural-arch"]
score: 7.0
evidence: 通过表征对齐训练传统上不可训练的架构
tldr: 某些架构（如无残差连接的深卷积网络）难以训练。本文提出“引导”方法，使用指导网络通过层间表征相似性距离来引导目标网络，使其能学习到合适的归纳偏置。实验证明该方法成功训练了传统上不可训练的架构，提升了准确率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1394, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1176, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 847, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1171, \"height\": 874, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1209, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1185, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1184, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1150, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1146, \"height\": 516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1192, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1143, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 724, \"height\": 580, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1193, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1122, \"height\": 864, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1145, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1427, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zvyxxhlqhm/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1428, \"height\": 490, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zvyxxhlqhm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1037, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zvyxxhlqhm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zvyxxhlqhm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1157, \"height\": 679, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zvyxxhlqhm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1277, \"height\": 1335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zvyxxhlqhm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 893, \"height\": 648, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zvyxxhlqhm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 855, \"height\": 555, \"label\": \"Table\"}]"
motivation: 传统架构如无残差连接的网络难以训练，性能差。
method: 引入指导网络，通过层间表征相似性距离引导目标网络训练。
result: 成功训练了不可训练的架构，如深卷积网络，提升准确率。
conclusion: 提供了一种架构无关的归纳偏置注入方法，拓展了可训练架构范围。
---

## Abstract
We demonstrate that architectures which traditionally are considered to be ill-suited for a task can be trained using inductive biases from another architecture.  We call a network untrainable when it overfits, underfits, or converges to poor results even when tuning their hyperparameters. For example, fully connected networks overfit on object recognition while deep convolutional networks without residual connections underfit. The traditional answer is to change the architecture to impose some inductive bias, although the nature of that bias is unknown. We introduce guidance, where a guide network steers a target network using a neural distance function. The target minimizes its task loss plus a layerwise representational similarity against the frozen guide. If the guide is trained, this transfers over the architectural prior and knowledge of the guide to the target. If the guide is untrained, this transfers over only part of the architectural prior of the guide. We show that guidance prevents FCN overfitting on ImageNet, narrows the vanilla RNN–Transformer gap, boosts plain CNNs toward ResNet accuracy, and aids Transformers on RNN-favored tasks. We further identify that guidance-driven initialization alone can mitigate FCN overfitting. Our method provides a mathematical tool to investigate priors and architectures, and in the long term, could automate architecture design.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：许多神经网络架构（如全连接网络FCN、无残差连接的深卷积网络、普通RNN）在特定任务上难以训练，表现为过拟合、欠拟合或收敛到较差结果，即所谓的“不可训练”网络。传统解决方案是修改架构以引入归纳偏置，但偏置的具体性质未知。
- **研究动机**：探究能否通过引入另一个架构（指导网络）的归纳偏置来训练这些不可训练的网络，而无需改变其自身架构。这有助于理解架构与归纳偏置之间的关系，并可能自动化架构设计。
- **整体含义**：论文提出一种名为“引导”（Guidance）的方法，通过层间表征对齐，将指导网络的归纳偏置（包括架构偏置和已学知识）迁移到目标网络，从而使其变得可训练，即使指导网络是随机初始化的。

### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：在目标网络的训练损失中添加一项层间表征相似性损失，使得目标网络在优化任务损失的同时，其各层激活与一个冻结的指导网络对应层激活对齐。通过这种方式，指导网络的归纳偏置（架构偏置和/或已学知识）被迁移到目标网络。
- **关键技术细节**：
  - **表征距离度量**：使用中心核对齐（Centered Kernel Alignment, CKA）作为相似性度量，也可以替换为其他可微度量（如RSA、岭回归）。
  - **损失函数**：`L(θ_T) = L_T(θ_T) + Σ_i (1 - CKA(A_{T,i}, A_{G,i}))`，其中 `θ_T` 为目标网络参数，`L_T` 为任务损失，`A_{T,i}` 和 `A_{G,i}` 分别为目标网络和指导网络第 `i` 层的激活。
  - **层映射**：将指导网络的层均匀地映射到目标网络的层，例如ResNet-18的每个卷积层映射到深FCN的每2~3个全连接层。所有可训练权重的层（卷积、全连接、RNN/Transformer层）都参与对齐。
  - **冻结指导网络**：指导网络的参数在整个训练过程中保持不变。
  - **两种设置**：指导网络可以是预训练好的（传递架构偏置+知识），也可以是随机初始化的（仅传递架构偏置）。
- **算法流程**（文字描述）：每个小批量中，同时前向传播目标网络和指导网络，收集指定层的激活，计算CKA损失并累加到任务损失上，反向传播更新目标网络参数。

### 3. 实验设计：数据集/场景、基准、对比方法
- **序列建模任务**：
  - **Copy-Paste**：生成10以内数字序列（长度20-40），训练集80k，验证/测试各10k。基准：4层RNN（目标），4层Transformer（指导）。
  - **Parity**：比特串奇偶分类（长度2-50）。基准：1层Transformer（目标），1层RNN（指导）。
  - **语言建模**：WikiText-103数据集，上下文长度50。小设置：4层RNN（目标）vs 4层Transformer（指导）；大设置：6层RNN（目标）vs 4层Transformer（指导）。
- **图像分类任务**：
  - **ImageNet-1K**，报告验证集top-5准确率。
  - **目标网络**：深FCN（50块，每块线性+BN+ReLU，2048 units），宽FCN（3块，每块8192 units），深ConvNet（ResNet-50去除残差连接）。
  - **指导网络**：ResNet-18（用于深/宽FCN），ResNet-50（用于深ConvNet）。
  - 额外实验：使用ViT-B-16作为指导进行误差一致性分析。
- **对比方法**：
  - 基础训练（无引导）。
  - 知识蒸馏（与指导网络进行logit匹配）。
  - 不同表征距离函数（RSA、岭回归）的引导。
  - 消融实验（不同层引导、层数影响）。
- **其他分析**：
  - 仅初始化引导（预对齐300步后停止引导）的效果。
  - 噪声引导（指导网络输入高斯噪声而非真实数据）。
  - 内在维度（Intrinsic Dimensionality）测量及正则化实验。

### 4. 资源与算力
论文明确说明：实验在 **4块H100和4块A100 GPU**上进行，总训练时间约**3周**。使用了梯度累积、梯度检查点、混合精度训练等技术以降低显存消耗。

### 5. 实验数量与充分性
- **数量**：涵盖了3个序列建模任务（含大小两种设置）和1个图像分类任务，每个任务包含多种网络组合及引导设置（训练/随机指导）。消融实验包括：不同层引导、不同距离函数、噪声引导、仅初始化引导、内在维度正则化等。总共报告了约20+组主要实验结果，每组训练了5个随机种子以计算标准误差。
- **充分性**：实验设计较为系统，覆盖了“不可训练”的典型场景（过拟合、欠拟合、梯度消失等），对比了蒸馏、不同度量，并进行了误差一致性分析。但作者也承认未对所有超参数进行极致搜索，也未尝试最优收敛，而是聚焦于证明引导的有效性。总体而言，实验足以支撑主要结论，但在性能绝对数值上还有提升空间。

### 6. 论文的主要结论与发现
- **引导有效转移归纳偏置**：无论是训练的还是随机的指导网络，都能显著提升目标网络的性能，甚至随机指导网络有时优于训练指导（如Copy-Paste、深FCN），证明纯架构偏置足以带来收益。
- **跨架构转移**：RNN经Transformer引导后，在Copy-Paste和语言建模上大幅提升；Transformer经RNN引导后在Parity上提升；深FCN经ResNet引导后过拟合得到抑制。
- **引导可仅用于初始化**：对深FCN仅进行300步预对齐，之后停止引导，仍能避免过拟合，表明存在更好的初始化方式。
- **引导优于蒸馏**：在多个设置中，引导的验证损失和准确率均优于知识蒸馏，尤其当教师网络未训练时蒸馏完全失效。
- **误差一致性继承**：引导后的FCN与指导网络的错误模式高度一致，表明不仅准确率提升，功能行为也向指导网络靠拢。
- **内在维度解释**：引导使深FCN的内在维度下降更慢，避免过早低维化导致的过拟合；基于内在维度的正则化能复现部分引导效果。
- **度量选择影响效果**：岭回归作为距离函数比CKA和RSA效果更好，可能因为其自由度更高。

### 7. 优点
- **新颖性**：首次将表征对齐（CKA等）作为归纳偏置迁移工具，用于训练传统上“不可训练”的网络，并区分了架构偏置与知识偏置。
- **通用性**：方法适用于多种架构（CNN、RNN、Transformer）和任务（图像分类、序列建模）。
- **简洁性**：仅需在损失中添加层间对齐项，无需更改网络架构，易于实现。
- **理论启发**：提供了研究架构归纳偏置的新工具，可系统分析不同架构的偏置性质，并有可能引导自动化架构设计。
- **实验多样性**：涵盖了过拟合、欠拟合、梯度消失等多种训练失败场景，分析深入（误差一致性、内在维度、初始化效果等）。

### 8. 不足与局限
- **性能未达最优**：作者明确表示未追求SOTA，而是验证引导的有效性。引导后的FCN在ImageNet上准确率仍远低于标准CNN，RNN性能也低于Transformer。
- **计算开销大**：需要同时前向传播两个网络并存储层激活，显存和计算成本较高，限制了批量大小和层数。
- **层映射简单**：采用均匀映射，可能不够最优；更复杂的映射（如非一对一）在消融中并未显著改善。
- **缺乏理论证明**：虽然提供了直观解释和内在维度分析，但未给出严格的泛化界或收敛保证。
- **仅限于特定训练设置**：未探索不同优化器、学习率调度等对引导的影响；实验以小规模模型为主（<150M参数），可扩展性未知。
- **引导网络依赖**：引导网络的选择（架构、训练与否）对结果影响较大，实际使用时需要针对任务选择合适指导网络，增加了调参成本。

（完）
