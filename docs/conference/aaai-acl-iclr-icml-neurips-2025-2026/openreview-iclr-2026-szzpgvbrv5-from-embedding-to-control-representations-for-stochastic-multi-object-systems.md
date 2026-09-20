---
title: "From Embedding to Control: Representations for Stochastic Multi-Object Systems"
title_zh: 从嵌入到控制：随机多物体系统的表示学习
authors: "Xiaoyuan Cheng, Yiming Yang, Wei Jiang, Chenyang Yuan, Zhuo Sun, Yukun Hu"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=SZzpGvBRv5"
tags: ["query:koopman-rl"]
score: 7.0
evidence: 用希尔伯特空间嵌入实现随机非线性动力学的线性控制
tldr: 多物体随机非线性动力学中交互非均匀、拓扑随机，给精确建模与有效控制带来困难。本文提出图可控嵌入GCE，将受控随机动力学的概率分布直接嵌入再生核希尔伯特空间，从而在RKHS中实现线性运算，同时保留非线性表达能力。方法给出存在性、收敛性与适用性的理论保证，使线性控制技术可应用于复杂随机多物体系统。该思路与Koopman式提升为控制提供线性化表示的理念相通。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 随机多物体系统交互非均匀、拓扑随机，难以精确建模与有效控制。
method: 提出图可控嵌入GCE，将受控随机动力学分布嵌入RKHS以支持线性运算。
result: 给出存在性、收敛性与适用性理论保证，并保留非线性表达能力。
conclusion: 为复杂随机多物体系统的线性控制提供了表示学习框架。
---

## Abstract
This paper studies how to achieve accurate modeling and effective control in stochastic nonlinear dynamics with multiple interacting objects. However, non-uniform interactions and random topologies make this task challenging. We address these challenges by proposing Graph Controllable Embeddings (GCE), a general framework to learn stochastic multi-object dynamics for linear control. Specifically, GCE is built on Hilbert space embeddings, allowing direct embedding of probability distributions of controlled stochastic dynamics into a reproducing kernel Hilbert space (RKHS), which enables linear operations in its RKHS while retaining nonlinear expressiveness. We provide theoretical guarantees on the existence, convergence, and applicability of GCE. Notably, a mean field approximation technique is adopted to efficiently capture inter-object dependencies and achieves provably low sample complexity. By integrating graph neural networks, we construct data-dependent kernel features which are capable of adapting to dynamic interaction patterns and generalizing to even unseen topologies with only limited training instances. GCE scales seamlessly to multi-object systems of varying sizes and topologies. Leveraging the linearity of Hilbert spaces, GCE also supports simple yet effective control algorithms for synthesizing optimal sequences. Experiments on physical systems, robotics, and power grids validate GCE and demonstrate consistent performance improvement over various competitive embedding methods in both in-distribution and few-shot tests.

---

## 论文详细总结（自动生成）

# 论文总结：从嵌入到控制：随机多物体系统的表示学习

> 说明：可获取的 PDF 文本仅为 OpenReview 验证页面，未包含论文正文；以下总结主要依据论文摘要与 Markdown 元数据，因此实验细节、算力与消融等信息可能不完整。

## 1. 核心问题与整体含义

- **研究问题**：如何在具有多个交互物体的随机非线性动力学系统中，实现准确建模与有效控制。
- **核心挑战**：
  - 物体间交互非均匀；
  - 系统拓扑具有随机性；
  - 传统建模与控制方法难以同时兼顾非线性表达能力与可计算性。
- **整体含义**：论文提出 Graph Controllable Embeddings（GCE，图可控嵌入），试图把受控随机动力学的概率分布直接嵌入再生核希尔伯特空间（RKHS），从而在嵌入空间中用线性运算完成控制，同时保留原系统的非线性表达能力。
- **理念关联**：该思路与 Koopman 式提升为控制提供线性化表示的理念相通，即为复杂随机多物体系统寻找一个“可线性控制”的表示空间。

## 2. 方法论

- **核心思想**：
  - 使用 Hilbert 空间嵌入，将受控随机动力学的概率分布直接嵌入 RKHS；
  - 在 RKHS 中进行线性操作，同时借助核方法保留非线性表达能力；
  - 通过图结构建模多物体之间的交互关系，使表示能够适应动态交互模式。

- **关键技术细节**：
  - **Graph Controllable Embeddings（GCE）**：一个学习随机多物体动力学以支持线性控制的通用框架。
  - **RKHS 嵌入**：将概率分布映射到再生核希尔伯特空间，使分布层面的运算线性化。
  - **Mean field 近似**：用于高效捕捉物体间依赖关系，并据称具有可证明的低样本复杂度。
  - **图神经网络（GNN）集成**：构造数据依赖的核特征，使其能够适应动态交互模式，并泛化到未见拓扑。
  - **可扩展性**：GCE 声称可无缝扩展到不同规模和拓扑的多物体系统。
  - **控制算法**：利用 Hilbert 空间的线性性质，支持简单而有效的控制算法，用于合成最优控制序列。

- **理论保证**：
  - 论文提供关于 GCE 的**存在性**、**收敛性**与**适用性**的理论保证。
  - 通过 mean field 近似给出低样本复杂度的理论支撑。

- **算法流程（文字概括）**：
  1. 将随机多物体系统的受控动力学表示为概率分布；
  2. 通过 Hilbert 空间嵌入把分布映射到 RKHS；
  3. 利用 GNN 构造与图结构、交互模式相关的核特征；
  4. 在 RKHS 中进行线性运算与控制优化；
  5. 合成控制序列，并映射回原系统执行控制。

## 3. 实验设计

- **实验场景**：
  - 物理系统；
  - 机器人；
  - 电网。

- **测试设置**：
  - 分布内测试（in-distribution）；
  - 少样本测试（few-shot）。

- **对比方法**：
  - 与多种竞争性嵌入方法（various competitive embedding methods）进行比较。

- **主要实验结果**：
  - 摘要声称 GCE 在分布内和少样本测试中均取得一致性的性能提升。

- **基准与数据集细节**：
  - 提供材料中未明确给出具体数据集名称、基准环境、评价指标、训练/测试划分等细节。

## 4. 资源与算力

- 提供材料中**未明确说明**使用的 GPU 型号、数量、训练时长、参数量或计算资源规模。
- 因此无法从现有信息总结算力开销，也无法判断其训练成本与可复现性。

## 5. 实验数量与充分性

- 从摘要可知，实验覆盖三类场景：物理系统、机器人、电网。
- 测试包含分布内与少样本两类设置，并对比多种嵌入方法。
- 但提供材料中**未给出**：
  - 具体实验组数；
  - 数据集数量与规模；
  - 消融实验数量；
  - 超参数敏感性分析；
  - 统计显著性检验；
  - 具体基线方法与实现细节。
- 因此，无法客观判断实验是否充分、公平。仅从摘要描述看，实验覆盖具有一定广度，但缺乏细节支撑深入评估。

## 6. 主要结论与发现

- GCE 能够将随机多物体系统的受控动力学分布嵌入 RKHS，并在其中进行线性控制。
- 方法在理论上具备存在性、收敛性与适用性保证。
- 借助 mean field 近似和 GNN 构造的核特征，GCE 能适应动态交互模式，并泛化到未见拓扑。
- GCE 可扩展到不同规模和拓扑的多物体系统。
- 在物理系统、机器人和电网实验中，GCE 相比多种嵌入方法在分布内与少样本测试中表现出一致提升。

## 7. 优点

- **理论驱动**：提供存在性、收敛性与适用性保证，并声称低样本复杂度。
- **表示学习与控制结合**：通过 RKHS 嵌入把非线性随机动力学转化为线性可操作表示，兼顾表达力与可控性。
- **图结构建模**：利用 GNN 构造数据依赖核特征，适应非均匀交互与随机拓扑。
- **泛化能力**：声称可泛化到未见拓扑，并支持少样本学习。
- **可扩展性**：面向不同规模和拓扑的多物体系统设计。
- **跨领域验证**：在物理、机器人和电网等场景中验证，具有一定应用广度。

## 8. 不足与局限

- **正文信息缺失**：当前可获取文本为验证页面，无法全面核查方法细节、实验设置与理论证明。
- **实验细节不足**：未提供具体数据集、基准、基线方法、评价指标、消融实验与统计检验，难以判断公平性与充分性。
- **算力未报告**：缺少 GPU 型号、数量、训练时长等信息，影响可复现性与成本评估。
- **潜在近似误差**：mean field 近似可能忽略高阶交互或引入偏差，文中未在现有材料中说明其适用边界。
- **核方法扩展性**：RKHS 方法在大规模系统上的计算与存储开销可能成为限制，现有材料未展开讨论。
- **控制安全性与最优性**：虽然支持合成最优序列，但在真实随机环境中的安全性、鲁棒性和约束满足情况未明确。
- **应用限制**：方法面向随机多物体系统，可能对图结构、交互建模和核函数选择有较强假设，实际部署条件尚不清晰。
- **偏差风险**：论文为 ICLR 2026 Accepted，元数据评分为 7.0，可能存在一定的正面选择偏差；需结合正文与独立复现进一步判断。

（完）
