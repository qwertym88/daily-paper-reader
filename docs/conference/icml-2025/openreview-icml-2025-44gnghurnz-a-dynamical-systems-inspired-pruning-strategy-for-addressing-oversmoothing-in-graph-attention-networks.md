---
title: A Dynamical Systems-Inspired Pruning Strategy for Addressing Oversmoothing in Graph Attention Networks
title_zh: 受动力系统启发的图注意力网络过平滑剪枝策略
authors: "Biswadeep Chakraborty, Harshit Kumar, Saibal Mukhopadhyay"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=44gnGhurnZ"
tags: ["query:neural-arch"]
score: 7.0
evidence: 针对GAT过平滑的新型剪枝策略
tldr: 本文针对图注意力网络深层过平滑问题，从动力系统视角揭示其本质，提出DYNAMO-GAT方法，结合噪声协方差分析和反赫布学习动态剪枝注意力权重，有效保持节点区分性，实验在多个基准数据集上取得一致优越性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-44gnghurnz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-44gnghurnz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1512, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-44gnghurnz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 946, \"height\": 642, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-44gnghurnz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 590, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-44gnghurnz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1429, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-44gnghurnz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-44gnghurnz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 879, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-44gnghurnz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1287, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-44gnghurnz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 762, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-44gnghurnz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1135, \"height\": 295, \"label\": \"Table\"}]"
motivation: 图注意力网络深层存在过平滑，降低表达力。
method: 提出DYNAMO-GAT，结合噪声协方差分析与反赫布学习动态剪枝注意力权重。
result: 在基准数据集上一致优于现有方法。
conclusion: 为图网络深层设计提供新视角。
---

## Abstract
Graph Neural Networks (GNNs) face a critical limitation known as oversmoothing, where increasing network depth leads to homogenized node representations, severely compromising their expressiveness. We present a novel dynamical systems perspective on this challenge, revealing oversmoothing as an emergent property of GNNs' convergence to low-dimensional attractor states. Based on this insight, we introduce **DYNAMO-GAT**, which combines noise-driven covariance analysis with Anti-Hebbian learning to dynamically prune attention weights, effectively preserving distinct attractor states. We provide theoretical guarantees for DYNAMO-GAT's effectiveness and demonstrate its superior performance on benchmark datasets, consistently outperforming existing methods while requiring fewer computational resources. This work establishes a fundamental connection between dynamical systems theory and GNN behavior, providing both theoretical insights and practical solutions for deep graph learning.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：图神经网络（GNN）在深层结构中存在严重的**过平滑（oversmoothing）** 现象——随着层数增加，节点表示趋于同质化，丧失区分性，导致模型表达能力严重下降。
- **研究动机**：现有缓解过平滑的方法（如跳跃连接、归一化、注意力机制）多为经验性结构调整，缺乏对过平滑内在动力学的根本理解。作者从**动力系统**视角重新审视该问题，将GNN消息传递过程视为一个动力系统，过平滑实质上是系统收敛到低维吸引子（attractor）的结果。
- **核心含义**：通过改变系统的吸引子结构，而非简单地增加网络复杂性，可以从原理上抑制过平滑。

### 2. 方法论：核心思想、关键技术细节

- **核心思想**：结合**噪声驱动的协方差分析**与**反赫布学习（Anti-Hebbian learning）**，动态地剪枝注意力权重，破坏导致过平滑的低维吸引子，维持节点表示的多样性。
- **技术细节**：
    1. **噪声注入**：向每层节点特征注入独立高斯噪声，扰动系统状态，从而揭示节点特征间的相关性。
    2. **协方差矩阵计算**：计算节点特征之间的协方差矩阵，量化特征相关性；高相关性表示系统正趋近过平滑固定点。
    3. **反赫布剪枝准则**：基于协方差信息，对高度相关的节点之间的连接给予更高的剪枝概率，削弱这些加强同质化的连接。剪枝概率公式为：
       \[
       p_{ij}^{(l)} = r(t) \cdot \frac{|\alpha_{ij}^{(l)}|}{\tau(t)} \cdot (C_{ii} + C_{jj} \mp 2C_{ij})
       \]
       其中 \(r(t)\) 为逐层剪枝率（随层数增大），\(\tau(t) = \mu(|w_{ij}|) + \beta \cdot \sigma(|w_{ij}|)\) 为动态阈值。
    4. **渐进剪枝与权重更新**：权重逐步乘以 \(1-p_{ij}\)，而非直接置零，使系统平滑过渡。
    5. **注意力权重重校准**：剪枝后对剩余注意力进行归一化，保持信息流平衡。
- **理论支撑**：论文通过4个引理（固定点存在性、谱分析、吸引子维数、稳定性）系统证明了过平滑的数学本质，并证明所提剪枝策略在谱半径降低、谱间隙增大、秩保持等方面的理论保证（引理5-6）。

### 3. 实验设计：数据集、场景与对比方法

- **数据集**：
    - 真实世界：Cora（2708节点）、Citeseer（3327节点）、Cornell（183节点）。
    - 合成数据集：Syn_Products（可调节点度、同质性）。
    - 大规模图：OGB 数据集（ogbn-arxiv、ogbn-products）。
- **基准（Benchmark）**：对比方法包括 GCN、GAT 以及基于注意力门控的 G2GAT。
- **评估指标**：准确率、过平滑系数（μ）、GFLOPS、准确率/GFLOPS比值。
- **实验场景**：
    - 深度网络（最多128层）下的过平滑与准确率变化；
    - 不同节点度（稀疏/密集）与不同同质性（homophily）水平；
    - OGB 大规模图上的可扩展性；
    - 消融实验（去除噪声、协方差剪枝、自适应阈值、渐进剪枝、注意力重校准等）；
    - 超参数敏感度分析（噪声水平 σ、剪枝阈值参数 β）；
    - 剪枝统计与余弦相似度分析（保留边与剪掉边的特征相似性对比）；
    - 将 DYNAMO 机制推广到其他注意力模型（Graphormer、SAN）。

### 4. 资源与算力

- **明确说明**：论文**未明确提及** GPU 型号、数量或训练时长。仅提到 GFLOPS 作为计算成本度量。
- **推断**：实验在标准深度学习环境（如单个GPU）上完成，论文强调 DYNAMO-GAT 在较低 GFLOPS 下取得高准确率，表明其计算效率优于对比方法。

### 5. 实验数量与充分性

- **实验数量**：共涉及约 **7组主要实验**（真实数据集3个、合成数据集2个变体、OGB 2个、消融研究、超参数敏感度、剪枝分析、模型推广）。消融部分包含5个变体。此外还有延伸实验（OGB、Graphormer/SAN）。
- **充分性与公平性**：
    - **充分**：涵盖多种深度、同质性、图密度、模型结构、规模，验证了方法的鲁棒性和泛化性。
    - **客观公平**：与三类代表性基线（GCN、GAT、G2GAT）比较，采用统一评估指标，并报告了 GFLOPS 和准确率/GFLOPS 比值，避免仅看准确率。
    - 论文理论分析与实验设计高度一致，消融实验强有力地证实了每个组件的必要性。

### 6. 主要结论与发现

1. **过平滑本质是低维吸引子收敛**，动力系统视角提供了全新理论解释。
2. **DYNAMO-GAT 有效维持节点多样性**：在所有层数下过平滑系数保持恒定，而 GCN/GAT 急剧下降。
3. **性能最优**：在 Cora、Citeseer、Cornell 及 OGB 数据集上，DYNAMO-GAT 准确率最高，且计算效率（GFLOPS）低于或接近最优，准确率/GFLOPS 比值显著领先。
4. **对异质性图友好**：在低同质性、密集/稀疏图上均优于基线。
5. **组件不可或缺**：消融表明，去除任一组件（噪声、协方差剪枝、自适应阈值等）均导致性能下降，其中移除协方差剪枝影响最大。
6. **可推广**：该剪枝思想可应用于其他注意力模型（Graphormer、SAN），提升性能并降低计算量。

### 7. 优点

- **理论贡献**：首次从动力系统角度严格建模过平滑，给出固定点、吸引子、谱间隙等理论保证，并证明剪枝策略的优劣。
- **方法新颖**：将反赫布学习与协方差分析结合于 GNN，通过噪声探知系统状态，实现动态自适应剪枝。
- **实验全面**：多维度（深度、同质性、规模、稀疏/密集）验证，包含消融、超参敏感性、推广实验，说服力强。
- **效率高**：在保持高精度的同时，显著降低 GFLOPS，具有实用潜力。
- **可解释性**：剪枝更可能移除特征相似度低的边（实验结果支持），减少冗余噪声连接。

### 8. 不足与局限

- **资源信息缺失**：未报告 GPU 型号、数量、训练时间，不利于复现和成本评估。
- **基线问题**：对比的 GCN、GAT 为较浅模型（2–4层），在深层比较时可能未公平调参。虽然论文强调深层优势，但应进一步说明浅层基线的参数优化情况。
- **理论假设较强**：论证中假设激活函数 Lipschitz 常数 ≤1、权重矩阵谱范数约束等，在实际训练中可能难以严格满足。
- **局限性声明**：作者在结论中提及“在极稀疏图上可能存在局限”，但未进行针对性实验。
- **缺乏显式超参敏感范围讨论**：虽然给出了 β、σ 的敏感度结果，但未探索极端取值下的失效边界。
- **模型范围**：仅在注意力机制 GNN 上验证，未与其它过平滑缓解方法（如 JK-Net、DAGNN、DropEdge）对比。

（完）
