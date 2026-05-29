---
title: Prior Knowledge Guided Neural Architecture Generation
title_zh: 先验知识引导的神经架构生成
authors: "Jingrong Xie, Han Ji, Yanan Sun"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=5QU8dAnLgO"
tags: ["query:neural-arch"]
score: 9.0
evidence: 无需搜索和评估的神经架构生成方法
tldr: 针对神经架构搜索需要大量评估候选架构导致耗时的问题，本文提出先验知识引导的架构生成方法。首先量化架构各组件对性能的贡献度，然后利用扩散模型在先验知识指导下直接生成高性能架构。该方法完全避免了搜索与评估过程，在多个基准上取得了与搜索方法相当甚至更好的性能，极大提升了架构设计效率。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-5qu8danlgo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 825, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5qu8danlgo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1754, \"height\": 846, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5qu8danlgo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 780, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5qu8danlgo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1616, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5qu8danlgo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1066, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5qu8danlgo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1465, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5qu8danlgo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1509, \"height\": 592, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1593, \"height\": 950, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1611, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1418, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 856, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 856, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1112, \"height\": 586, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5qu8danlgo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 763, \"height\": 568, \"label\": \"Table\"}]"
motivation: 神经架构搜索计算开销巨大，本文希望无需搜索和评估即可直接生成高性能架构。
method: 量化架构组件贡献度，结合先验知识训练扩散模型以生成高性能架构。
result: 生成的架构在多个数据集上达到或超过搜索方法的性能，且计算量大幅降低。
conclusion: 验证了先验知识在架构生成中的有效性，为高效架构设计开辟了新路径。
---

## Abstract
Automated architecture design methods, especially neural architecture search, have attracted increasing attention. However, these methods naturally need to evaluate numerous candidate architectures during the search process, thus computationally extensive and time-consuming. In this paper, we propose a prior knowledge guided neural architecture generation method to generate high-performance architectures without any search and evaluation process. Specifically, in order to identify valuable prior knowledge for architecture generation, we first quantify the contribution of each component within an architecture to its overall performance. Subsequently, a diffusion model guided by prior knowledge is presented, which can easily generate high-performance architectures for different computation tasks. Extensive experiments on new search spaces demonstrate that our method achieves superior accuracy over state-of-the-art methods. For example, we only need $0.004$ GPU Days to generate architecture with $76.1\%$ top-1 accuracy on ImageNet and $97.56\%$ on CIFAR-10. Furthermore, we can find competitive architecture for more unseen search spaces, such as TransNAS-Bench-101 and NATS-Bench, which demonstrates the broad applicability of the proposed method.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

神经架构搜索（NAS）是自动设计高性能神经网络架构的有效方法，但其核心瓶颈在于需要在庞大的搜索空间中评估大量候选架构（通常超过10¹⁰种），每次评估需从头训练模型以获得精度，导致极高的计算开销。现有的加速方法（如性能预测器、零样本方法）虽能降低评价成本，但仍需逐个评估架构，计算量依然庞大。为此，本文探索“神经架构生成”（NAG）范式，旨在**完全避免搜索和评估过程**，直接生成高性能架构。作者提出一种名为PG-NAG的方法，利用从基准数据集中高性能架构提取的先验知识，指导扩散模型生成新架构，从而在极低计算成本下获得与甚至超越传统NAS方法的性能。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **先验知识提取**：从NAS基准数据集（NAS-Bench-101、NAS-Bench-201、NAS-Bench-301）中选取排名前20的高性能架构，利用**Shapley值**量化每个操作（operation）和一跳子图（one-hop subgraph）对架构整体性能的边际贡献，形成先验知识K。
- **扩散模型引导生成**：设计一个条件扩散模型，将先验知识作为条件，使生成过程朝向高性能区域。扩散模型包括前向扩散过程（逐步加噪）和反向生成过程（去噪恢复），其中先验知识影响噪声分布和去噪步骤，使模型更倾向于生成含有关键操作和连接的架构。

### 关键技术细节
1. **架构表示**：每个架构表示为图GR = ⟨O, C⟩，O为操作节点，C为边（连接）。采用统一编码表示不同搜索空间的架构。
2. **Shapley值计算**：将操作和一跳子图视为合作博弈中的玩家，性能函数V(S)为子集S对应架构的验证精度。计算每个操作oᵢ和子图gⱼ的Shapley值：
   - φᵢᵒ(P) = (1/|N_O|) Σ_{S⊆N_{oᵢ}} [V(S∪{oᵢ})−V(S)] / C(|N_O|−1, |S|)
   - φⱼᵍ(P) = (1/|N_G|) Σ_{S⊆N_{gⱼ}} [V(S∪{gⱼ})−V(S)] / C(|N_G|−1, |S|)
   其中N_O和N_G分别表示操作和子图集合。整个架构性能等于所有组件Shapley值之和。
3. **条件扩散模型**：
   - 前向过程：q(A_t|A_{t-1}, K) = Πᵢ Πₙ N(A_{t,n}; A_{t-1,n}, β_t Xₙ)
   - 反向过程：p_θ(A_{t-1}|A_t, K) = Πᵢ Πₙ N(A_{t-1,n}; μ̃_t(A_{t,n}, A_{0,n}|K), β̃_t Xₙ)
   - 最终先验分布：p(A_T|K) = Πᵢ Πₙ N(A_T; μ_n, Xₙ)
   利用图卷积网络（GCN）提取操作特征，多层感知机（MLP）提取连接特征，使模型能学习先验知识并概率性地选择关键组件。

## 3. 实验设计

### 使用的数据集与搜索空间
- **搜索空间**：DARTS（包含约10¹⁸种架构）、NAS-Bench-201（15,625种）、TransNAS-Bench-101（51,464种，覆盖7个视觉任务）、NAS-Bench-101（423,624种）、NAS-Bench-ASR（8,242种，语音识别）、NAS-Bench-NLP（14,000种，语言建模）。
- **验证数据集**：
  - 图像分类：CIFAR-10、CIFAR-100、ImageNet（含ImageNet16-120）
  - 语音识别：TIMIT（音素错误率PER）
  - 语言建模：Penn Tree Bank（测试困惑度）

### 对比方法
- **NAS方法**：DARTS、SNAS、P-DARTS、GDAS、PC-DARTS、ISTA-NAS、SDARTS-ADV、FairDARTS、DARTS+PT、TE-NAS、EOI NAS、BALENAS-TF、PRE-NAS、EAEPSO、MOEA-PS、ANGLE LOSS、PIANT-T、SWD-NAS、EG-NAS、IS-DARTS等。
- **NAG方法**：DiffusionNAG（An et al., 2024）、AutoBuild等。
- **加速方法**：BANANAS、NPENAS、NASBOT、REA等。
- 所有对比结果均直接引用原论文报告的数据。

## 4. 资源与算力

- 文中明确提到：生成架构仅需要**0.004 GPU天**（约5.76分钟），使用**Nvidia 3090 GPU**，操作系统为Linux Ubuntu 18.04。
- 训练扩散模型的算力未单独报告，但整体成本极低（因无需训练大量候选架构）。
- 此外，在NAS-Bench-201上的搜索成本（生成5个架构并验证）为**4,147秒**（约1.15小时），远低于对比方法（例如DARTS需29,902秒）。

## 5. 实验数量与充分性

### 实验数量
- **主要基准测试**：在DARTS、NAS-Bench-201、TransNAS-Bench-101、NAS-Bench-ASR、NAS-Bench-NLP、NAS-Bench-101共**6个不同搜索空间**上进行了实验。
- **数据集覆盖**：涉及图像分类（CIFAR-10/100、ImageNet）、语音识别（TIMIT）、语言建模（PTB）、以及7个跨域视觉任务（场景分类、目标分类、自编码、表面法线、语义分割、房间布局、拼图）。
- **消融实验**：3组（组件消融、扩散模型配置消融、先验知识质量与数量消融）。
- **分布分析**：生成1,000个架构与随机采样1,000个架构对比精度分布。
- **稳定性分析**：在DARTS搜索空间上重复5次实验，计算方差。

### 充分性与公平性
- 实验覆盖了多个未见过的新搜索空间，验证了方法的**泛化性**。
- 对比方法均为已发表的最先进方法，且性能数据直接引用原论文，避免二次训练差异。
- 消融实验系统性地分析了先验知识、特征提取方式、扩散模型参数的影响，结果逻辑一致。
- 但存在一定局限：未在同一硬件和软件环境下复现所有对比方法，可能存在实现细节差异；部分对比方法（如DiffusionNAG）仅报告了部分数据集的结果，导致直接比较不完全。

## 6. 论文的主要结论与发现

1. **高效性**：PG-NAG仅需0.004 GPU天即可生成高性能架构，计算成本比传统NAS低2~3个数量级。
2. **高精度**：在ImageNet上达到76.1% top-1准确率（best架构），CIFAR-10上97.56%，均超越或持平现有SOTA方法。
3. **泛化能力强**：在未见过的搜索空间（如TransNAS-Bench-101、NAS-Bench-ASR、NAS-Bench-NLP）中同样取得有竞争力的性能，表明先验知识具有跨空间迁移性。
4. **生成稳定性**：生成的架构精度分布集中，最低性能和平均性能均优于随机采样和DiffusionNAG。
5. **先验知识的重要性**：消融实验表明，去除先验知识后性能下降最明显，且高质量先验（前20高性能架构）远优于随机挑选的架构。

## 7. 优点

- **创新性**：提出“无需搜索和评估”的架构生成范式，区别于传统NAS的迭代搜索，大幅降低计算开销。
- **方法简洁有效**：利用Shapley值量化组件贡献，将先验知识直接嵌入扩散模型的条件分布，避免了额外训练预测器。
- **实验全面**：在6个不同领域（图像、语音、语言、多视觉任务）的搜索空间上进行验证，跨任务泛化性证据充分。
- **资源需求极低**：0.004 GPU天的生成成本在实用场景中极具吸引力。
- **可解释性**：通过Shapley值可视化操作重要性（如3x3卷积贡献最大），为架构设计提供洞察。

## 8. 不足与局限

- **先验知识依赖性**：方法严重依赖从基准数据集提取的先验知识质量。若基准数据集本身存在偏差（如仅覆盖特定类型架构），可能导致生成的架构偏置。
- **实验对比公平性**：未在新硬件环境下复现所有对比方法，性能数据直接引用原论文，可能因训练策略、超参数、设备差异导致比较不完全公平。
- **生成架构的多样性**：生成1,000个架构的分布显示集中于高性能区域，但可能存在模式崩塌风险，生成架构的多样性可能不足。
- **搜索空间覆盖**：虽然测试了多个空间，但均为基准搜索空间（如DARTS、NAS-Bench系列），未在更现实的工业级搜索空间（如MobileNet-like空间、EfficientNet空间）上验证。
- **缺乏理论分析**：未对先验知识引导的有效性提供理论保证，仅通过经验实验证明。
- **应用限制**：方法需要高性能架构作为“种子”，对于全新任务（无任何先验架构可用）可能不适用。

（完）
