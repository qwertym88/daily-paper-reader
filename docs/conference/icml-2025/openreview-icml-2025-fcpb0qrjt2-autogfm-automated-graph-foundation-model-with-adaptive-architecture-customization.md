---
title: "AutoGFM: Automated Graph Foundation Model with Adaptive Architecture Customization"
title_zh: AutoGFM：自适应架构定制的自动化图基础模型
authors: "Haibo Chen, Xin Wang, Zeyang Zhang, Haoyang Li, Ling Feng, Wenwu Zhu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=fCPB0qRJT2"
tags: ["query:neural-arch"]
score: 8.0
evidence: 面向基础模型的图神经架构搜索
tldr: 现有图基础模型采用固定架构，无法适应不同任务。本文首次将图神经架构搜索引入基础模型，发现跨任务不变的图-架构关系，并据此自适应定制架构，显著提升下游性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fcpb0qrjt2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 478, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fcpb0qrjt2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1775, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fcpb0qrjt2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fcpb0qrjt2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1786, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fcpb0qrjt2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1088, \"height\": 436, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fcpb0qrjt2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 580, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fcpb0qrjt2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1772, \"height\": 896, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fcpb0qrjt2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1768, \"height\": 656, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fcpb0qrjt2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1768, \"height\": 675, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fcpb0qrjt2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1766, \"height\": 684, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fcpb0qrjt2/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1417, \"height\": 494, \"label\": \"Table\"}]"
motivation: 固定GNN架构导致图基础模型性能次优。
method: 设计图神经架构搜索方法，学习不变图-架构关系以自适应定制。
result: 在多种图任务上性能优于固定架构基线。
conclusion: 自动架构搜索可显著增强图基础模型的泛化能力。
---

## Abstract
Graph foundation models (GFMs) aim to share graph knowledge across diverse domains and tasks to boost graph machine learning. 
However, existing GFMs rely on hand-designed and fixed graph neural network (GNN) architectures, failing to utilize optimal architectures *w.r.t.* specific domains and tasks, inevitably leading to suboptimal performance in diverse graph domains and tasks. 
In this paper, we explore graph neural architecture search (GNAS) for GFMs for the first time, which suffers from the problem of *architecture inconsistency*, i.e., the optimal architectures for different tasks and domains vary. We tackle this problem by discovering an invariant graph-architecture relationship across domains and tasks, which imposes three challenges: i) how to capture invariant and variant patterns; ii) how to customize architectures to adapt to diverse domains and tasks; iii) how to mitigate the data domination phenomenon during the architecture search process.
To address these challenges, we propose **Auto**mated **G**raph **F**oundation **M**odel with Adaptive Architecture Customization (**AutoGFM**), providing a theoretical analysis to demonstrate the limitations of existing GNAS. Specifically, we first propose a disentangled contrastive graph encoder to learn invariant and variant patterns. Then, we design an invariant-guided architecture customization strategy to customize architectures for data from diverse domains and tasks. Finally, we propose a curriculum architecture customization mechanism to mitigate the phenomenon of particular data dominating the search process. 
Extensive experiments demonstrate that **AutoGFM** outperforms baselines, achieving state-of-the-art performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：图基础模型（GFM）旨在跨不同领域和任务共享图知识，提升图机器学习性能。现有GFM（如OFA、GFT）依赖手工设计的固定GNN架构，但不同领域和任务对架构需求不同（如GCN在OGBN-arxiv上表现好，但在OGBN-proteins上差）。这种“架构不一致性”导致固定架构无法达到最优性能。
- **核心问题**：首次将图神经架构搜索（GNAS）引入GFM，但面临**架构不一致性**问题——不同任务和领域的最优架构差异大。现有可微GNAS方法（如DARTS）在GFM场景下会产生操作优化冲突，导致次优架构。
- **解决思路**：发现跨领域和任务的**不变图-架构关系**，即存在与任务无关的图模式（不变模式）可以稳定预测最优架构，而可变模式则带来干扰。需要解决三个挑战：①如何捕捉不变和可变模式；②如何基于这些模式为不同数据定制架构；③如何缓解特定数据在搜索过程中主导的现象。

## 2. 方法论：核心思想、关键技术细节
### 2.1 核心思想
- 训练一个映射函数 π: G → A，为每个数据集定制架构，同时通过权重共享超网络实现跨领域知识共享。
- 从**不变性视角**出发：将图数据分解为不变模式（ZI）和可变模式（ZV）。目标是最小化I(ZI, ZV)并最大化I(ZI, A)，同时使A在给定ZI下与ZV独立。

### 2.2 关键技术模块
1. **解耦对比图编码器（Disentangled Contrastive Graph Encoder）**
   - 使用两个独立的GNN通道分别提取不变模式和可变模式。
   - 提出**NOI图级对比学习**：通过实例判别任务促使相同来源的图具有相似的ZI，不同来源的图具有不同的ZI；同时最小化ZI与ZV之间的互信息。
   - 损失函数为 \( \mathcal{L}_{\text{dis}} \)（公式10）。

2. **不变引导的架构定制（Invariant-guided Architecture Customization）**
   - 建立权重共享超网络，每层操作通过连续参数化混合（公式11）。
   - 设计**架构预测器ψI**：利用原型向量计算操作选择概率（公式12），将图表示与原型相似度映射为架构选择。
   - 使用**辅助预测器ψE**，将不变模式与可变模式（包括来自其他数据的可变模式）融合后预测架构，并通过最小化 ψI 和 ψE 预测的差异来实现条件互信息最小化（Loss: \( \mathcal{L}_{\text{inv}} \)，公式14）。

3. **课程架构定制机制（Curriculum Architecture Customization Mechanism）**
   - 计算每层各操作的平均选择概率的变异系数（CV），作为多样性损失 \( \mathcal{L}_{\text{cur}} \)（公式18）。
   - 采用**课程学习**策略：训练早期鼓励多样性（γ=1-t/te），后期逐渐放松约束。

### 2.3 总体优化目标
- 损失函数：\( \mathcal{L} = \mathcal{L}_{\text{task}} + \lambda \mathcal{L}_{\text{dis}} + \beta \mathcal{L}_{\text{inv}} + \mathcal{L}_{\text{cur}} \)
  - \( \mathcal{L}_{\text{task}} \)：GFM任务损失（最大化I(ZI, A)）
  - \( \mathcal{L}_{\text{dis}} \)：解耦损失（最小化I(ZI, ZV)）
  - \( \mathcal{L}_{\text{inv}} \)：不变引导损失（最小化I(A, ZV|ZI)）
  - \( \mathcal{L}_{\text{cur}} \)：课程多样性损失（缓解数据主导）

### 2.4 算法流程（文字描述）
- 训练循环T步：从每个数据集中采样NOI子图；提取ZI和ZV；计算解耦损失；用ψI和ψE预测架构；计算不变引导损失；计算课程损失和任务损失；更新编码器θ、预测器ψI和ψE。推理时，直接使用ψI基于ZI输出定制架构。

## 3. 实验设计
- **数据集**：8个数据集，涵盖节点分类（Cora、PubMed、WikiCS、Arxiv）、链路预测（WN18RR、FB15K237）、图分类（HIV、PCBA）。遵循OFA/GFT预处理，使用Sentence Transformer统一节点特征为768维。
- **Benchmark**：
  - 基线分为五类：①普通GNN（GCN、GAT、GIN）；②自监督方法（DGI、BGRL、GraphMAE、GIANT）；③GFM（OFA、GFT）；④手工GNN（GraphSAGE、GraphConv）；⑤GNAS方法（DARTS、GraphNAS、GASSO、Graces）。
  - 公平性设置：所有手工GNN和GNAS方法均以GFT为基础模型，使用相同搜索空间（5种操作，2层网络）。
- **实验场景**：
  - 预训练-微调（表1）：在8个数据集上报告准确率。
  - 少样本学习（表2、附录B.3）：在Cora、WN18RR、ChemHIV上设置不同N-way K-shot（1-shot、3-shot、5-shot等）。
  - 消融实验（图3）：在5个数据集上移除非必需模块（w/o D、w/o I、w/o C）。
  - 超参数敏感性（附录B.2）：分析λ和β在WikiCS上的影响。
  - 架构可视化（附录B.1）：展示不同数据集各层操作选择热图。

## 4. 资源与算力
- 论文附录D.4给出硬件配置：
  - 操作系统：Ubuntu 20.04.5 LTS
  - CPU：Intel Xeon Gold 5218R @ 2.10GHz
  - GPU：NVIDIA A100-SXM4-40GB 和 A100-SXM4-80GB（具体数量未说明）
  - 软件：Python 3.9, CUDA 12.2, PyTorch 1.13.1
- **未明确说明训练时长、GPU数量、总计算量**，但指出每个实验重复10次取平均值。

## 5. 实验数量与充分性
- **实验数量**：
  - 主表1：8个数据集×16种方法，共128组对比。
  - 少样本表2：3个数据集×10种方法×多个shot，约90组。
  - 消融图3：5个数据集×4种变体，20组。
  - 超参数分析、架构可视化、更多少样本结果等补充实验。
- **充分性与公平性**：
  - 基线覆盖全面，且对手工GNN和GNAS进行了统一基座控制。
  - 重复10次报告均值和标准差，统计可靠。
  - 消融实验验证了每个模块的贡献。
  - 不足：未与最新的LLM-based GFM（如GraphGPT、InstructGLM）对比，主要聚焦GNN-based GFM；数据集规模中等（除Arxiv外，其他节点数较少）。

## 6. 主要结论与发现
- 固定GNN架构在跨领域任务中性能不佳，验证了“架构不一致性”的存在。
- 现有可微GNAS方法在GFM场景下因操作优化冲突导致性能下降（理论证明见附录A.1）。
- AutoGFM通过自适应架构定制，在预训练-微调设置下平均准确率80.86%，优于所有基线（第二名GraphSAGE 79.84%）。
- 少样本学习场景中，AutoGFM在大部分设置下表现最佳，表明定制架构具有快速适应能力。
- 消融实验表明，三个模块（解耦编码器、不变引导定制、课程机制）均不可或缺，其中不变引导定制模块影响最大。
- 课程机制有效缓解数据主导现象，提高架构多样性。

## 7. 优点
- **首创性**：首次将GNAS引入GNN-based GFM，解决架构固定导致性能次优的问题。
- **理论贡献**：对架构不一致性进行了形式化定义，并证明了现有可微GNAS方法在该场景下的优化冲突（Proposition 3.2）。
- **方法论创新**：
  - 提出解耦对比学习同时捕捉不变和可变模式，设计NOI图级对比损失。
  - 利用原型向量实现数据到架构的映射，避免了逐数据搜索的高成本。
  - 引入课程学习机制促进早期搜索多样性，创新性地应用在架构搜索过程。
- **实验全面**：覆盖节点、边、图三类任务，数据集多样化，基线广泛。
- **代码开源**（隐含，论文未明确提及但基于ICML惯例）。

## 8. 不足与局限
- **应用范围有限**：仅聚焦GNN-based GFMs，未探索LLM-based GFMs（如GraphGPT）中的架构搜索问题。
- **复杂度较高**：虽然给出了时间复杂度分析（O(|E|d + |V|d² + |O|²d + |O|(|E|d + |V|d²))），但未与基线方法进行实际训练时间对比，可能实际开销较大。
- **超参数敏感**：λ和β需要手动调参（在1e-1～1e-4间选择），且在WikiCS上观察到取值不当会导致性能下降。
- **数据集偏差**：实验集中在学术/分子/知识图谱领域，缺少社交网络、推荐系统等大规模图数据。
- **理论假设强度**：Assumption 3.3假设完全解耦，但在真实数据中不变和可变模式可能难以彻底分离。
- **未见大规模部署验证**：仅在中等规模数据集（最大Arxiv约16万节点）上测试，未在超大规模图（如亿级节点）上评估。

（完）
