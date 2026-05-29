---
title: Attention-Only Transformers via Unrolled Subspace Denoising
title_zh: 通过展开子空间去噪的纯注意力Transformer
authors: "Peng Wang, Yifu Lu, Yaodong Yu, Druv Pai, Qing Qu, Yi Ma"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ITMu1pZTFo"
tags: ["query:neural-arch"]
score: 7.0
evidence: 新颖的纯注意力Transformer架构，提升模型准确性
tldr: 针对Transformer架构冗余且缺乏可解释性的问题，本文提出通过展开子空间去噪操作得到纯注意力的紧凑Transformer架构。该方法将表示学习视为低维子空间压缩，使自注意力成为自然的去噪操作。实验表明该架构在保持性能的同时大幅减少组件数量，为设计更简洁有效的Transformer提供了理论基础。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-itmu1pztfo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 250, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-itmu1pztfo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1612, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-itmu1pztfo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1263, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-itmu1pztfo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1553, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-itmu1pztfo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1531, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-itmu1pztfo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1520, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-itmu1pztfo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1362, \"height\": 1241, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-itmu1pztfo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 802, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-itmu1pztfo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 806, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-itmu1pztfo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1600, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-itmu1pztfo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1730, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-itmu1pztfo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1622, \"height\": 206, \"label\": \"Table\"}]"
motivation: 现有Transformer架构经验设计且存在冗余，本文旨在推导出完全可解释且仅含必要组件的注意力架构。
method: 将表示学习解释为向低维子空间混合的压缩过程，通过展开迭代去噪操作得到仅含多头自注意力的深度网络。
result: 得到高度紧凑的纯注意力架构，在多项任务上验证了其有效性与可解释性。
conclusion: 从第一性原理出发设计出了更简洁、更具解释性的Transformer变体，为架构设计提供了新视角。
---

## Abstract
Despite the popularity of transformers in practice, their architectures are empirically designed and neither mathematically justified nor interpretable. Moreover, as indicated by many empirical studies, some components of transformer architectures may be redundant. To derive a fully interpretable transformer architecture with only necessary components, we contend that the goal of representation learning is to compress a set of noisy initial token representations towards a mixture of low-dimensional subspaces. To compress these noisy token representations, an associated denoising operation naturally takes the form of a multi-head (subspace) self-attention. By unrolling such iterative denoising operations into a deep network, we arrive at a highly compact architecture that consists of \textit{only} self-attention operators with skip connections at each layer. Moreover, we show that each layer performs highly efficient denoising: it improves the signal-to-noise ratio of token representations \textit{at a linear rate} with respect to the number of layers. Despite its simplicity, extensive experiments on vision and language tasks demonstrate that such a transformer achieves performance close to that of standard transformer architectures such as GPT-2 and CRATE.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：标准Transformer架构（如GPT、ViT）由多头自注意力、MLP、层归一化、残差连接等多个组件堆叠而成，但很多经验设计缺乏数学解释，且已有实证表明MLP等组件并非必不可少。作者希望从第一性原理出发，设计一个**仅包含必要组件**、**完全可解释**的最小化Transformer架构。
- **整体含义**：论文提出将表示学习的目标理解为“将一组带噪声的初始token表示压缩到混合低维子空间”，而多头自注意力正是这一去噪操作的自然形式。通过展开迭代去噪步骤，得到了一个**仅由自注意力层和跳跃连接构成的紧凑架构**（Attention-Only Transformer, AoT），并从理论上证明每层以线性速率提升信噪比（SNR）。实验表明，尽管结构极简，AoT在视觉和语言任务上性能接近标准Transformer（如GPT-2、CRATE）。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：
  - 假设token表示来自**混合低秩高斯分布**（即不同语义对应不同低维子空间，且存在噪声），则去噪操作等价于将每个token投影到其所属子空间。
  - 设计**多头子空间自注意力（Multi-Head Subspace Self-Attention, MSSA）** 作为去噪算子：每个头对应一个子空间，通过计算投影后token的相似度（softmax）获得注意力权重，再加权聚合去噪。
  - 通过**展开迭代去噪步骤**，将单步去噪操作堆叠为深度网络，得到AoT架构：每一层为 `Z^{(l+1)} = Z^{(l)} + η · MSSA(Z^{(l)})`，其中η为步长。
- **关键技术细节**：
  - MSSA公式：`MSSA(Z) = Σ_k U_k U_k^T Z φ(Z^T U_k U_k^T Z)`，其中`U_k`是第k个子空间的正交基，φ为softmax+硬阈值函数（理论分析中使用）。
  - 该算子可视为标准MHSA的特殊情况（令W_Q=W_K=W_V=U_k, W_O=[U_1,...,U_K]），从而与标准Transformer对齐。
  - 实际训练时，`U_k^{(l)}`通过反向传播学习，在不同层可以不同。
- **理论保证**（定理3.1）：在混合低秩高斯模型下，若噪声水平满足`δ ≤ O(√(log N)/√p)`，则每层以`(1+ητ)`倍线性提升SNR。

### 3. 实验设计：数据集、基准、对比方法

- **视觉任务**：监督图像分类（ImageNet）。
  - 对比方法：CRATE（基于MSSA的白盒Transformer）、ViT（标准MHSA+MLP模型）。
  - 使用AoT-MSSA-V（仅MSSA）和AoT-MHSA-V（仅MHSA，去掉MLP）两种变体。
- **语言任务**：因果语言建模（预训练+零样本评估）及上下文学习（ICL）。
  - **语言建模**：在OpenWebText上预训练，在WikiText、LAMBADA、PTB、Children's Book Test (CBT)等数据集上评估零样本困惑度和准确率。对比GPT-2 Base/Medium等。
  - **上下文学习**：线性回归和稀疏线性回归任务，对比GPT-2风格Transformer。
- **消融/分析**：通过合成数据验证理论SNR提升曲线（图4）；可视化注意力热图（图7）展示语义解释性。

### 4. 资源与算力

- 论文**未明确说明**使用的GPU型号、数量及训练总时长。仅提到在视觉任务中使用Lion优化器、特定学习率、batch size等，在语言任务中使用AdamW优化器、1024-token上下文等，但未披露硬件配置。

### 5. 实验数量与充分性

- **实验数量**：视觉任务（ImageNet上对比CRATE和ViT，两种设置）；语言任务（预训练损失/验证损失曲线、零样本4个数据集、3种模型规模、上下文学习2种任务）。总共约**6组核心实验**，每组包含不同规模或变体。
- **充分性**：
  - 正面：覆盖了视觉和语言两大领域，理论预测（线性SNR提升）在合成数据上得到验证；对比方法为标准基线；零样本评估覆盖多个经典数据集。
  - 不足：视觉任务仅做了ImageNet分类，未涉及检测/分割；语言模型规模较小（最大182M参数），未与更大规模（如GPT-2 Large）对比；缺少对不同噪声水平、子空间维度的系统消融实验；未分析注意力头数的敏感性等。

### 6. 论文的主要结论与发现

- **理论结论**：所提AoT每层以线性速率提高token表示的SNR，证明了自注意力作为子空间去噪算子的高效性。
- **实验结论**：
  - AoT-MSSA-V在ImageNet上达到71.7%准确率（22M参数），CRATE为79.5%（39M参数），AoT-MHSA-V达69.5%（15M参数），ViT为72.4%（22M参数）。表明去掉MLP后性能略有下降但参数减半。
  - 在语言建模中，AoT-MHSA-L（122M参数）的零样本性能接近GPT-2 Base（124M参数）；AoT-MSSA-L略低但仍在可比范围。
  - 在ICL任务上，AoT表现与GPT-2相近，说明自注意力本身足以实现上下文学习。
  - 注意力热图显示不同头捕获不同语义区域，增强了可解释性。

### 7. 优点

- **理论驱动**：从底层数据模型出发，推导出最小化架构，并提供严格的收敛保证（线性SNR提升），使架构设计具备数学可解释性。
- **架构极简**：仅保留自注意力+跳跃连接，去除MLP、层归一化（可选）、值矩阵等，参数效率高。
- **实验全面**：涵盖视觉和语言两大领域，包括零样本评估和上下文学习，结果与标准方法可比。
- **可解释性**：注意力头可视化显示语义聚类，有助于理解Transformer内部机制。

### 8. 不足与局限

- **实验覆盖有限**：
  - 视觉任务仅做ImageNet分类，缺少检测、分割、自监督学习等常见benchmark。
  - 语言模型规模较小（最大182M），未验证在大规模（如1B+）上的行为。
  - 未与同等参数量的完全Transformer做精细对比（如去掉MLP后增加宽度/深度的影响）。
- **偏差风险**：理论模型（混合低秩高斯）假设子空间正交、噪声独立同分布，与真实数据（文本、图像）的结构复杂性有差距，理论结论可能无法直接推广。
- **应用限制**：AoT在视觉任务上准确率明显低于ViT/CRATE（约7-8%差距），在实际高精度场景中可能不可接受；语言任务上训练损失下降较慢（图5），收敛速度可能不及带MLP的模型。
- **消融不充分**：未系统研究不同层数、头数、步长η、阈值τ等超参数的影响；未分析训练过程中SNR的实际变化曲线（仅做了合成数据验证）。
- **算力信息缺失**：无法复现训练成本。

（完）
