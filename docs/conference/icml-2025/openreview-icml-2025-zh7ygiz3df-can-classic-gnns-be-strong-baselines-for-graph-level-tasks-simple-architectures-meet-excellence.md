---
title: Can Classic GNNs Be Strong Baselines for Graph-level Tasks? Simple Architectures Meet Excellence
title_zh: 经典GNN能否成为图级别任务的强基线？简单架构实现卓越性能
authors: "Yuankai Luo, Lei Shi, Xiao-Ming Wu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=ZH7YgIZ3DF"
tags: ["query:neural-arch"]
score: 8.0
evidence: GNN+框架中集成残差连接
tldr: 本文探讨经典图神经网络的潜力，通过集成残差连接、归一化、dropout等六种技术，提出GNN+框架。实验表明，在多个图分类和回归基准上，增强的GNN性能与图Transformer相当甚至更优，挑战了图Transformer必然优于GNN的观点。残差连接在防止过平滑中发挥了关键作用。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-zh7ygiz3df/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 792, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zh7ygiz3df/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 772, \"height\": 664, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zh7ygiz3df/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1770, \"height\": 769, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zh7ygiz3df/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1505, \"height\": 970, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zh7ygiz3df/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1552, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-zh7ygiz3df/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1578, \"height\": 1293, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 516, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1784, \"height\": 1171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1784, \"height\": 1071, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1603, \"height\": 978, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 749, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1766, \"height\": 835, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1694, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1216, \"height\": 706, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1769, \"height\": 604, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1213, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1770, \"height\": 603, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1226, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1770, \"height\": 603, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1765, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 937, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1168, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-zh7ygiz3df/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 657, \"height\": 202, \"label\": \"Table\"}]"
motivation: 图Transformer常被认为优于GNN，但GNN的潜力可能未被充分利用。
method: 在经典GNN基础上集成残差连接、归一化、dropout等六种技术，构建GNN+框架。
result: 在多个图级别任务上，GNN+性能超越图Transformer，成为强有力的基线。
conclusion: 证明了经典GNN配合适当技巧足以在图级别任务上取得一流性能。
---

## Abstract
Message-passing Graph Neural Networks (GNNs) are often criticized for their limited expressiveness, issues like over-smoothing and over-squashing, and challenges in capturing long-range dependencies. Conversely, Graph Transformers (GTs) are regarded as superior due to their employment of global attention mechanisms, which potentially mitigate these challenges. Literature frequently suggests that GTs outperform GNNs in graph-level tasks, especially for graph classification and regression on small molecular graphs. In this study, we explore the untapped potential of GNNs through an enhanced framework, GNN+, which integrates six widely used techniques: edge feature integration, normalization, dropout, residual connections, feed-forward networks, and positional encoding, to effectively tackle graph-level tasks. We conduct a systematic re-evaluation of three classic GNNs—GCN, GIN, and GatedGCN—enhanced by the GNN+ framework across 14 well-known graph-level datasets. Our results reveal that, contrary to prevailing beliefs, these classic GNNs consistently match or surpass the performance of GTs, securing top-three rankings across all datasets and achieving first place in eight. Furthermore, they demonstrate greater efficiency, running several times faster than GTs on many datasets. This highlights the potential of simple GNN architectures, challenging the notion that complex mechanisms in GTs are essential for superior graph-level performance. Our source code is available at https://github.com/LUOyk1999/GNNPlus.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，以下是对该论文的详细、结构化中文总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

-   **研究动机**：图神经网络（GNN）通常被认为存在表达能力有限、过平滑、过挤压以及难以捕捉长距离依赖等问题。而图Transformer（GTs）由于采用了全局注意力机制，被认为能有效缓解这些问题，因此在图级别任务（如图分类、回归）中常被视为更优的选择。本文的核心动机是**挑战这一普遍认知**，探究经典GNN在图级别任务中被低估的潜力。
-   **核心问题**：通过系统性地集成一些广泛使用的技术，简单的经典GNN（如GCN、GIN、GatedGCN）能否在图级别任务上达到甚至超越当前最先进的图Transformer的性能？
-   **整体含义**：本文试图证明，图分析领域的“冠军”可能并非总是需要复杂架构。通过恰当的增强和调优，简单、高效的传统方法足以与甚至超越那些设计精妙的复杂模型成为强有力的基线，这有助于引导社区重新审视模型设计的复杂性与性能之间的平衡。

### 2. 论文提出的方法论：核心思想、关键技术细节

-   **核心思想**：提出了一个名为**GNN+**的增强框架，该框架在不改变经典GNN核心消息传递机制的前提下，系统地集成了6种被广泛验证有效的技术。该框架旨在“解锁”经典GNN的潜力，使其能有效应对图级别任务。
-   **关键技术细节**：
    -   **边特征集成 (Edge Feature Integration)**：将边特征直接融入消息传递过程，例如在GCN的聚合中加上边特征的线性变换（如公式6所示）。
    -   **归一化 (Normalization)**：采用批归一化（Batch Normalization）来稳定训练过程，缓解内部协变量偏移。
    -   **Dropout**：在激活函数后应用Dropout，以减少过拟合，防止神经元之间的共适应。
    -   **残差连接 (Residual Connections)**：将每一层的输入直接加到输出上，公式化为 `hlv = ... + hl-1v`，旨在缓解深层网络中的梯度消失和过平滑问题，使模型可以训练得更深。
    -   **前馈网络 (Feed-Forward Network, FFN)**：在每个GNN层的末尾附加一个全连接的前馈网络，以增强模型的非线性变换能力和表达能力。其结构为 `FFN(h) = BN(σ(hW1)W2 + h)`。
    -   **位置编码 (Positional Encoding, PE)**：使用随机游走结构编码（如RWSE）为节点添加位置或结构信息，然后将其与原始节点特征拼接后作为模型输入，以弥补消息传递机制在捕捉全局结构信息上的不足。

### 3. 实验设计：数据集、基准与对比方法

-   **数据集与基准**：在**14个广泛使用的图级别基准数据集**上进行评估，涵盖3个不同的基准平台：
    -   **GNN Benchmark**：包括ZINC（图回归）、MNIST/CIFAR10（超像素图分类）、PATTERN/CLUSTER（归纳式节点分类）。
    -   **Long-Range Graph Benchmark (LRGB)**：包括Peptides-func/struct（图分类/回归）、PascalVOC-SP/COCO-SP（节点分类）、MalNet-Tiny（图分类）。
    -   **Open Graph Benchmark (OGB)**：包括ogbg-molhiv/pcba（分子性质预测）、ogbg-ppa（蛋白关联网络分类）、ogbg-code2（代码图预测）。
-   **对比方法**：与大量最先进的图Transformer（GTs）和某些图状态空间模型（GSSMs）进行了全面对比，包括GT (2020), SAN, Graphorsmer, SAT, EGT, GraphGPS, GRIT, Exphormer, GRED, Graph-Mamba等。同时，也与未经增强的原始GCN、GIN、GatedGCN进行了对比。

### 4. 资源与算力

-   **计算环境**：论文明确提到，实验是在一台配备**8块NVIDIA RTX 3090 GPU**的工作站上进行的。
-   **训练时长**：论文在多个结果表（表2、3、4）中提供了每个epoch的训练耗时作为效率参考。例如，GraphGPS在某些数据集上耗时数倍于GNN+。但**并未提供完整的、针对每个实验的总体训练时间**（例如，跑完全部2000个epoch所需的总小时数）。这算是信息的一个小缺失，但通过每个epoch的时间已经可以清晰地比较效率。

### 5. 实验数量与充分性

-   **实验数量**：实验非常丰富，涵盖了14个数据集，对3种经典GNN（GCN, GIN, GatedGCN）进行了增强和测试。此外，还进行了详尽的**消融研究**（表5、6），系统地移除GNN+框架中的每一个组件，以验证其贡献。还包括了超参数敏感性分析（深度、Dropout率）。
-   **充分性与公平性**：实验设计总体上是**充分和公平**的。
    -   **充分性**：数据集覆盖了分子图、超像素图、社会网络、蛋白质网络等多种类型和规模的图级别任务，范围广泛。
    -   **公平性**：作者强调，他们遵循了与GraphGPS等主流GT相同的超参数搜索空间和训练设置，确保了对比的公平性。但需要指出，基线GT的结果多来自原论文，可能存在实现细节和环境差异。
    -   **客观性**：对比的基线模型列表非常全面，涵盖了该领域绝大多数知名的SOTA模型。结论稳健，所有结果都报告了多次运行（5次）的均值和标准差。

### 6. 论文的主要结论与发现

-   **主要结论**：**增强了经典GNN（GNN+）可以在一系列图级别任务上匹配甚至超越最先进的图Transformer**。在14个数据集中，GNN+在8个上取得了第一，且在所有数据集上都稳定地排在前三名。
-   **关键发现**：
    1.  **效率优势**：GNN+的运行速度通常比GT快数倍，体现了其高效性。
    2.  **组件重要性**：通过消融研究，明确了各组件的作用：
        -   边特征在分子和超像素图中至关重要。
        -   归一化在大规模数据集上更为关键。
        -   Dropout对多数图级别任务有益，且最优率很低（≤0.2）。
        -   残差连接是构建深层GNN的基础，对防止过平滑至关重要。
        -   前馈网络（FFN）对GCN和GIN这类能力较弱的模型提升显著。
        -   位置编码（PE）在较小的数据集上作用更明显，在大型数据集上作用相对减弱。
    -   **挑战主流认知**：该研究有力地证明了，GT并非图级别任务的唯一最优解，经过恰当增强的简单GNN架构同样可以取得卓越性能。

### 7. 优点（方法/实验设计的亮点）

-   **高度的简洁性与实用性**：方法本身不复杂，只是将现成技术进行了有机组合，这使得GNN+易于理解和复现，对实际应用具有很高的指导价值。
-   **系统且严谨的实证研究**：实验覆盖范围广，对比基线全面，消融研究深入，结论稳固。特别是对超参数的敏感性分析，为社区提供了非常有价值的实践指导。
-   **挑战了领域内根深蒂固的假设**：有力地反驳了“GT必定优于GNN”的观点，其发现可能改变未来图学习领域的模型选择和设计思路，促使研究者更关注基础组件的有效整合。
-   **揭示了关键组件在不同场景下的差异化贡献**：消融实验不仅验证了各组件的作用，更揭示了它们作用的边界条件（如PE对小规模数据更有用），见解深刻。

### 8. 不足与局限

-   **缺乏理论解释**：作者明确指出，本文是**纯粹基于大量实验的实证研究**，缺乏对GNN+为何能超越GT的理论分析，例如，为什么这些组件组合就能有效解决机制瓶颈（如过平滑）？这留给了未来工作。
-   **数据集局限性**：文末也提到，当前的图数据集可能不足以完全反映真实世界图问题的复杂性。GNN+的优势可能仅限于现有的基准测试上，在更复杂、更具挑战性的真实应用场景中，其竞争力尚存疑问。
-   **超参数搜索空间**：尽管采用了与GT相同的搜索空间，但并未进行“穷举”搜索。不同的超参数搜索范围可能导致不同的最优性能，存在偏差风险。
-   **计算资源报告**：虽然报告了单Epoch时间，但**未提供总训练时长**，这对于希望复现或者评估整体计算成本的读者来说，信息不够完整。
-   **应用范围**：结论主要基于“图分类/回归”等全局性任务，对于需要精细节点关系理解的底层任务，其结论可能不能直接外推。

（完）
