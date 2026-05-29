---
title: "UMoE: Unifying Attention and FFN with Shared Experts"
title_zh: UMoE：通过共享专家统一注意力与前馈网络
authors: "Yuanhang Yang, Chaozheng Wang, Jing Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=2Z0OFReqkT"
tags: ["query:neural-arch"]
score: 7.0
evidence: 提出统一注意力与前馈网络的共享专家架构，属于新颖设计
tldr: 本文提出UMoE架构，通过共享专家统一注意力机制和前馈网络，解决了现有注意力MoE层实现复杂且性能不佳的问题。该方法揭示了注意力模块中的FFN-like结构，在多个任务上取得更优表现，为高效Transformer架构设计提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 577, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 651, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1433, \"height\": 807, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 582, \"height\": 235, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 514, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 991, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1376, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1080, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1308, \"height\": 1006, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2z0ofreqkt/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1310, \"height\": 942, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 713, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 684, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 568, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 655, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 573, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1434, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 604, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1187, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1442, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1181, \"height\": 653, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1182, \"height\": 655, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2z0ofreqkt/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 739, \"height\": 343, \"label\": \"Table\"}]"
motivation: 现有注意力MoE层实现复杂且性能不及FFN-MoE，需要统一设计。
method: 重新表述注意力机制，发现其内在FFN结构，并采用共享专家实现统一MoE。
result: UMoE在语言建模等任务上超越现有方法，同时无需特殊实现。
conclusion: 为Transformer中MoE的统一设计提供了有效方案。
---

## Abstract
Sparse Mixture of Experts (MoE) architectures have emerged as a promising approach for scaling Transformer models. While initial works primarily incorporated MoE into feed-forward network (FFN) layers, recent studies have explored extending the MoE paradigm to attention layers to enhance model performance. However, existing attention-based MoE layers require specialized implementations and demonstrate suboptimal performance compared to their FFN-based counterparts. In this paper, we aim to unify MoE designs in attention and FFN layers by introducing a novel reformulation of the attention mechanism, that reveals an underlying FFN-like structure within attention modules. Our proposed architecture, UMoE, achieves superior performance through attention-based MoE layers while enabling efficient parameter sharing between FFN and attention components.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **研究动机**：稀疏混合专家（MoE）架构在扩展Transformer模型方面极具前景，早期工作主要将MoE应用于前馈网络（FFN）层，近期的研究开始探索将MoE扩展到注意力层以提升性能。然而，现有的注意力MoE层实现复杂，且性能明显不如FFN-MoE。
- **核心问题**：如何设计一种统一的MoE架构，使得注意力和FFN层可以采用相同的专家设计，既保留注意力机制的表达能力，又能实现参数共享，从而在不增加参数的前提下提升模型性能。

### 论文提出的方法论

- **核心思想**：通过重新表述多头注意力机制，揭示其内部的“预混合（pre-mixing）”结构，从而将注意力层中的值投影（Wv）和输出投影（Wo）合并为两级矩阵乘法，形成与FFN层类似的专家结构。
- **关键技术细节**：
  - **预混合注意力**：将标准注意力的计算顺序改为先对token隐状态进行加权求和（token mixing），再通过组合的WvWo矩阵进行处理，这使得注意力层可以视为一组“专家”对上下文化输入的处理。
  - **统一架构（UMoE）**：将Transformer层抽象为三个基本组件：共享专家（两层MLP）、token混合操作和路由器。FFN层与注意力层的区别仅在于专家输入：FFN专家处理独立token，注意力专家处理加权求和后的token。这种设计使得FFN-MoE可以被视为注意力MoE的一个特例（注意力矩阵退化为单位矩阵）。
  - **低秩查询投影**：为避免查詢投影矩阵参数过多，为每个专家引入低秩矩阵（Wia, Wib）产生专家特异性的查询向量，同时保留共享查询。
- **算法流程（文字说明）**：
  1. 输入序列X和当前token x。
  2. 通过TopK路由器为x选择k个专家（注意力MoE和FFN MoE共用路由器或独立）。
  3. 注意力MoE分支：使用共享键值（K/X），结合专家特异性查询计算注意力权重，对X进行加权求和得到上下文化表示，再经选中的专家处理，加权合并。
  4. FFN MoE分支：直接将x输入选中的专家处理，加权合并。
  5. 残差连接后输出。

### 实验设计

- **数据集**：
  - 预训练：FineWeb-Edu 100B（高质量教育文本）和 Wikitext-103（约100M token）。
  - 零样本评估：HellaSwag、PIQA、ARC-E、ARC-C、RACE、Lambada、MMLU、Winogrande。
- **基准（Benchmark）**：密集模型（Dense）、细粒度FFN-MoE、MoA（Mixture of Attention Heads）、SwitchHead。所有对比方法在相似激活参数量和MACs条件下进行。
- **模型规模**：
  - Base：12层，隐藏维度768，总参约134M（Dense）～547M（UMoE-Att）。
  - Large：24层，隐藏维度2048，总参约1.1B（Dense）～3.8B（对比方法）。
- **评估指标**：语言建模困惑度（PPL）、训练/验证损失、零样本准确率、MACs（乘法累加操作数）。

### 资源与算力

- **硬件**：NVIDIA H100 GPU（未明确数量，但训练Base模型时采用batch size 1024，预计使用多卡）。
- **训练时长**：Base模型在FineWeb-Edu上预训练约需一周；Wikitext-103上训练100k步，实际20k步内过拟合。Large模型未明确时长，但从规模推断使用更多算力。
- **注**：论文未提供精确GPU数量或总FLOPs，但给出了MACs作为计算开销指标。

### 实验数量与充分性

- **实验组数**：
  - 主要困惑度对比：Base和Large两种规模，在FineWeb-Edu和Wikitext-103两个数据集上，共4组核心结果（表1）。
  - MAC-matched对比：调整激活专家数后比较（表2）。
  - 零样本下游任务：8个任务，Base和Large两套结果（表4）。
  - 消融实验：参数共享策略（表3）、专家分配（表5）、激活函数（表6）。
  - 收敛曲线（图5）、训练损失曲线、专家路由分析（表7、图9-10）、注意力可视化。
- **充分性**：实验设计全面，覆盖了不同规模、不同数据集、计算量匹配、消融分析及可解释性分析。对比方法（Dense、FFN-MoE、MoA、SwitchHead）均为近期主流，控制了参数量和MACs，比较公平。但不足在于未涵盖代码/数学任务，且零样本评估任务数量有限（8个）。

### 论文的主要结论与发现

- UMoE在语言建模困惑度和零样本准确率上一致优于所有对比方法，尤其在Base模型下优势显著。
- 通过预混合注意力实现的注意力MoE（UMoE-Att）首次匹配甚至超越了FFN-MoE的性能，解决了以往注意力MoE性能欠佳的问题。
- 参数共享（注意力与FFN共用专家）在相同总参数量下进一步提升了效果。
- 专家分配实验中，将更多专家分配给注意力层比给FFN层能取得更低的困惑度，验证了注意力机制比FFN更具表达力的理论推断。
- 专家路由分析显示，高阶专家（路由器分数高）表现出更聚焦的任务相关注意模式，且共享专家在注意力和FFN模块中可发展出不同但互补的专门化。

### 优点

1. **方法新颖**：首次揭示注意力机制内在的FFN-like结构，实现了统一的MoE专家设计，避免了以往注意力MoE需要特殊实现的缺点。
2. **性能优越**：在困惑度和零样本任务上全面领先，且参数效率高（总参数量接近FFN-MoE但性能更好）。
3. **理论洞察**：将FFN-MoE解释为注意力MoE的特例，提供了对Transformer层内在统一的视角。
4. **实验充分**：从多个维度（规模、数据集、计算量匹配、消融、可视化）验证了方法有效性，对比基线选取全面。
5. **开放可复现**：代码开源，超参数详细，易于复现。

### 不足与局限

1. **计算开销**：预混合注意力的加权求和操作在隐藏维度上执行，带来一定额外计算（小模型约1.17x MACs，大模型约1.03x），虽然随规模增加可忽略，但对小模型仍不可忽视。
2. **下游任务覆盖不全**：零样本评估仅8个任务，未包含数学推理（如GSM8K）、代码生成（如HumanEval）等关键领域，通用性验证不够充分。
3. **硬件效率未匹配理论**：尽管MACs相近，实际吞吐量和延迟仍高于密集模型（表9），说明现有GPU内核未针对MoE路由和稀疏执行充分优化，实际部署中效率优势可能被抵消。
4. **专家共享的潜在冲突**：同一专家在注意力和FFN模块中可能发展出不同的专门化，存在知识冲突风险，论文未深入研究该问题的影响及缓解策略。
5. **训练数据有限**：仅使用FineWeb-Edu和Wikitext-103，未在大规模、多样化的语料（如Pile、C4）上验证，泛化性有待考察。

（完）
