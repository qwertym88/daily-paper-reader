---
title: Learning to Flow from Generative Pretext Tasks for Neural Architecture Encoding
title_zh: 从生成式预训练任务学习流式神经架构编码
authors: "Sunwoo Kim, Hyunjin Hwang, Kijung Shin"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=z2vJpjopJk"
tags: ["query:neural-arch"]
score: 9.0
evidence: 用于性能预测的神经架构编码方法
tldr: 针对神经架构搜索中快速准确评估架构性能的需求，提出基于生成式预训练任务的流式架构编码器。该编码器通过学习信息流模式来表征架构，相比现有流式编码器处理速度更快。实验表明在多个NAS基准上预测准确性更高。该方法加速了架构搜索过程，提升了NAS效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1356, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 783, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1446, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 590, \"height\": 207, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 638, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 803, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1446, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 512, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z2vjpjopjk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1426, \"height\": 349, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1469, \"height\": 785, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 789, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1021, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1368, \"height\": 524, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 607, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1123, \"height\": 372, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1251, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1192, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1141, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1446, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1377, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 870, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 730, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1205, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1346, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z2vjpjopjk/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1285, \"height\": 181, \"label\": \"Table\"}]"
motivation: 现有神经架构编码器计算速度慢，限制了其在NAS中的实用性。
method: 利用生成式预训练任务学习架构信息流，设计高效流式编码器。
result: 在NAS基准上预测性能更准且处理速度更快。
conclusion: 生成式预训练能有效提升架构编码器的效率与准确性。
---

## Abstract
The performance of a deep learning model on a specific task and dataset depends heavily on its neural architecture, motivating considerable efforts to rapidly and accurately identify architectures suited to the target task and dataset. To achieve this, researchers use machine learning models—typically neural architecture encoders—to predict the performance of a neural architecture. Many state-of-the-art encoders aim to capture information flow within a neural architecture, which reflects how information moves through the forward pass and backpropagation, via a specialized model structure. However, due to their complicated structures, these flow-based encoders are significantly slower to process neural architectures compared to simpler encoders, presenting a notable practical challenge. To address this, we propose FGP, a novel pre-training method for neural architecture encoding that trains an encoder to capture the information flow without requiring specialized model structures. FGP trains an encoder to reconstruct a flow surrogate, our proposed representation of the neural architecture's information flow. Our experiments show that FGP boosts encoder performance by up to 106\% in Precision@1\%, compared to the same encoder trained solely with supervised learning.

---

## 论文详细总结（自动生成）

# 论文《Learning to Flow from Generative Pretext Tasks for Neural Architecture Encoding》详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **研究动机**：深度学习模型性能严重依赖其神经架构，而传统暴力训练和评估每个架构成本极高。因此研究者使用神经架构编码器来预测架构性能，加速神经架构搜索（NAS）。
- **现有挑战**：
  - 现有的流式编码器（如FlowerFormer）虽能有效捕获架构内部的信息流（前向传播和反向传播），但由于其复杂的模型结构（异步消息传递），处理速度极慢（比非流式编码器慢最多57倍），成为实际应用中的瓶颈。
  - 已有的生成式预训练方法（如Arch2vec、GMAE）大多从其他领域直接迁移，针对神经架构缺乏明确的训练引导：例如预测被掩码的操作时，由于架构不存在类似化学规则的约束，模型难以学到有意义的模式。
- **核心目标**：提出一种无需专用模型结构即可捕获信息流的预训练方法，兼顾效率和性能。

## 2. 方法论核心思想与关键技术细节
### 核心思想：流代理（Flow Surrogate）
- 定义一种称为“流代理”的向量，代表给定神经架构的信息流，作为预训练目标。
- 流代理通过将随机向量沿架构的有向无环图（DAG）模拟前向传播和反向传播获得，无需任何学习过程，且计算一次即可复用。

### 关键技术步骤
1. **拓扑排序**：为架构图节点分配拓扑顺序（$V^{(1)}, V^{(2)}, ..., V^{(T)}$）。
2. **模拟前向传播**：
   - 初始化顺序-1节点的前向消息（随机向量）。
   - 按拓扑顺序传播，每个节点汇总邻居消息（求和池化），并根据自身操作类型（通过操作嵌入矩阵$P$）进行消息转换：$f_i = \alpha m_i + (1-\alpha)\text{ReLU}([h_i\|m_i]W)$。
3. **模拟反向传播**：
   - 顺序-T节点的反向消息初始化为其前向消息。
   - 按逆拓扑顺序传播，转换公式同前向。
4. **生成流代理**：将所有顺序-1节点的反向消息求和，得到向量$s \in \mathbb{R}^k$。
5. **预训练**：将编码器输出的架构嵌入$z$通过MLP解码器重建流代理$\hat{s}$，最小化$\mathcal{L}_{rec} = \|s - \hat{s}\|_2^2$。可选辅以零成本代理预测损失（排序损失）。

### 关键特性
- 流代理对节点排列保持不变性（理论证明基于异步消息传递的排列不变性）。
- 无需专用模型结构，适用于任意非流式编码器（如ResGatedGCN、GIN）。

## 3. 实验设计
### 数据集
- **主要数据**：NAS-Bench-101、NAS-Bench-201、NAS-Bench-301（均为CIFAR-10图像分类任务）。
- **额外域**：NAS-Bench-NLP（自然语言处理）、NAS-Bench-Graph（图表示学习），以及自建的迁移学习数据集（TinyImageNet→DTD/OxfordPet）。

### 骨干编码器
- 非流式：ResGatedGCN、GIN、DiGCN
- 流式：FlowerFormer
- 非图编码器：MLP、Transformer

### 对比方法
- 无预训练（N/A）
- GraphCL（图对比学习）
- Arch2vec（变分图自编码器）
- GMAE（掩码自编码器）
- ZC-Proxy（零成本代理预测）

### 评价指标
- Kendall's tau、Precision@1%、Precision@5%（性能预测）
- NAS任务中比较搜索得到的最佳架构测试误差

## 4. 资源与算力
- **硬件**：NVIDIA RTX 8000 D6 GPU（48GB内存） + Intel Xeon Silver 4214R CPU。
- **训练配置**：预训练epochs=200，batch size=256，优化器AdamW。
- **流代理计算时间**：每个架构约0.002~0.005秒（表2）。
- **备注**：论文未单独报告总预训练时长，但在图8中显示FGP的预训练总时间仅次于ZC-Proxy，在NAS-Bench-201上约4.3秒（对比其他方法更长）。

## 5. 实验数量与充分性
- **性能预测实验**（表1）：3个数据集 × 3种编码器 × 6种预训练方法 = 54个设置（文中报告了27个主要设置，包括标准差），FGP在23/27中最佳。
- **不同训练集比例**（表3）：1%、5%、10%三种比例，FGP在14/18中最佳。
- **仅用训练集预训练**（表5）：6个设置全胜。
- **不同预训练数据比例**（图9）：20%~100%，FGP始终优于基线。
- **不同域**（表6）：NLP和图，FGP在5/6中最佳。
- **其他任务（迁移学习）**（表7）：4个设置全胜。
- **其他编码器**（表8、13）：DiGCN、MLP、Transformer，全胜。
- **消融实验**（表7）：4种变体（无重建、无辅助、无前向、无反向），FGP在5/6中最佳。
- **统计检验**（图11）：不同随机初始化下的流代理性能无显著差异（Wilcoxon检验）。
- **补充分析**：编码时间对比、替代设计（多轮传播、池化函数）、理论性质等。
- **充分性评价**：覆盖了多种数据集、骨干、任务、数据量、消融交叉验证，实验设计全面且公平。所有实验均报告多次运行的均值和标准差，并进行了统计检验。

## 6. 主要结论与发现
- **效率与性能兼得**：FGP使非流式编码器（ResGatedGCN）在性能预测上超越流式编码器（FlowerFormer），同时处理速度快57倍。
- **性能增益显著**：相比无预训练，FGP在Precision@1%上最高提升106%（NB-101/ResGatedGCN）。
- **超越所有基线的预训练方法**：在23/27个设置中取得最佳，包括流式编码器自身（FlowerFormer）也能受益于FGP（通过暴露更广泛无标签架构的流模式）。
- **流代理具有良好的性能表征能力**：PCA可视化显示高/低性能架构的流代理分布分离。
- **鲁棒性**：对不同随机初始化、超参数、预训练数据量均表现稳定。

## 7. 优点
1. **新颖性**：首次提出以随机向量模拟信息流作为预训练目标，无需专用模型结构。
2. **高效性**：流代理计算成本极低（毫秒级），预训练速度仅次于ZC-Proxy，但性能远超之。
3. **通用性**：适用于多种编码器（GNN、MLP、Transformer）和多个领域（CV、NLP、图）。
4. **可解释性**：流代理可鉴别架构中是否包含特定操作（分类准确率>92%）。
5. **理论基础**：证明了流代理的排列不变性，与信息流的本质一致。
6. **实验充分**：涵盖大量消融、统计检验、跨域验证、公平对比。

## 8. 不足与局限
1. **理论深度有限**：虽然提供了初步的排列不变性证明，但对流代理能捕获何种程度的信息流缺乏严格理论刻画（作者在附录E中承认这一点）。
2. **随机向量依赖性**：流代理依赖随机向量和随机矩阵，论文通过统计检验证明不同初始化结果无显著差异，但未解释为何随机性有效，也未与确定性选择（如训练好的流式编码器输出）进行足够对比（附录B.9.2只对比了TA-GATEs且性能更差，但未与其他确定性方案比较）。
3. **应用局限于搜索空间内**：实验均在NAS基准的预定义搜索空间内进行，对跨空间或生成式架构的泛化能力未验证。
4. **零成本代理的依赖**：FGP的辅助损失（Laux）需使用零成本代理，这些代理本身可能带有一定偏差，且并非所有场景都有现成的零成本代理（如NB-Graph数据集无法使用ZC-Proxy基线）。
5. **消融实验仅涵盖核心组件**：未分析消息转换公式中不同激活函数、不同α取值、不同嵌入维度k的敏感性（虽然附录B.15对λ进行了分析）。
6. **算力报告不完整**：未报告总预训练时长（仅给相对比较），也未报告微调阶段的详细时间。

（完）
