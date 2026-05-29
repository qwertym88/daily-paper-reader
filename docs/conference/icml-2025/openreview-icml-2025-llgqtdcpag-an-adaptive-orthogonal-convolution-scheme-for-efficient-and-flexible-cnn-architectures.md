---
title: An Adaptive Orthogonal Convolution Scheme for Efficient and Flexible CNN Architectures
title_zh: 一种用于高效灵活CNN架构的自适应正交卷积方案
authors: "Thibaut Boissin, Franck Mamalet, Thomas Fel, Agustin Martin Picard, Thomas Massena, Mathieu Serrurier"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=lLGqtDcPag"
tags: ["query:neural-arch"]
score: 7.0
evidence: 高效的CNN架构正交卷积方案
tldr: 该论文针对正交卷积在大规模应用中计算开销大且缺乏现代特征支持的问题，提出了自适应正交卷积（AOC）方法。AOC扩展了BCOP方法，支持步长、膨胀、分组卷积和转置卷积等现代特性。实验显示AOC能在保持正交性优势的同时实现高效灵活的CNN架构。该工作为高效神经网络结构优化提供了新的正交卷积方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1710, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1689, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 489, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 382, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 763, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1588, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 761, \"height\": 865, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-llgqtdcpag/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 788, \"height\": 290, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1710, \"height\": 683, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 1141, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1582, \"height\": 488, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1777, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1778, \"height\": 517, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 957, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1680, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 804, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 897, \"height\": 864, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-llgqtdcpag/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 976, \"height\": 368, \"label\": \"Table\"}]"
motivation: 正交卷积部署困难，计算开销大且缺乏对现代特征的支持。
method: 提出AOC，扩展BCOP方法以支持步长、膨胀、分组卷积和转置卷积。
result: 实验表明AOC在多种任务上实现高效灵活的CNN架构。
conclusion: AOC为大规模应用正交卷积提供了可行方案。
---

## Abstract
Orthogonal convolutional layers are valuable components in multiple areas of machine learning, such as adversarial robustness, normalizing flows, GANs, and Lipschitz-constrained models. Their ability to preserve norms and ensure stable gradient propagation makes them valuable for a large range of problems. Despite their promise, the deployment of orthogonal convolution in large-scale applications is a significant challenge due to computational overhead and limited support for modern features like strides, dilations, group convolutions, and transposed convolutions. In this paper, we introduce **AOC** (Adaptive Orthogonal Convolution), a scalable method that extends a previous method (BCOP), effectively overcoming existing limitations in the construction of orthogonal convolutions. This advancement unlocks the construction of architectures that were previously considered impractical. We demonstrate through our experiments that our method produces expressive models that become increasingly efficient as they scale. To foster further advancement, we provide an open-source python package implementing this method, called **Orthogonium**.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的结构化、深入且客观的中文总结。

### 论文中文总结：自适应正交卷积方案（AOC）

#### 1. 核心问题与整体含义（研究动机和背景）
*   **核心问题**：正交卷积层因其保持范数、稳定梯度等优良性质，在机器学习许多领域（如图像鲁棒性、标准化流、生成对抗网络、Lipschitz约束模型）中至关重要。然而，现有的正交卷积方法存在显著瓶颈：
    *   **计算开销大**：在大规模应用中部署困难。
    *   **功能受限**：普遍缺乏对现代卷积神经网络（CNN）关键特性的原生支持，如步长（Stride）、膨胀（Dilation）、分组卷积（Group Convolution）和转置卷积（Transposed Convolution）。这些限制严重阻碍了正交卷积在U-Net、ResNeXt、EfficientNet等现代架构中的应用。
*   **研究动机**：为了解决上述问题，实现一个既严格正交、高效，又灵活支持现代CNN特性的卷积层，从而解锁正交卷积在更大规模、更复杂架构中的应用潜力。

#### 2. 方法论：核心思想、关键技术与算法
*   **核心思想**：提出**AOC**方法，该方法巧妙地将两种现有的正交卷积构建方法——**BCOP** (Block Convolution Orthogonal Parameterization) 和 **RKO** (Reshaped Kernel Orthogonalization)——通过一个高效的**块卷积（Block-convolution, ⊛）** 算子进行组合，从而取长补短。
*   **核心技术细节**：
    *   **核心工具：块卷积 (⊛)**：该算子用于计算两个卷积核组合后的等效核。通过此算子，AOC可以利用BCOP构建任意尺寸的标准正交卷积核，并利用RKO实现原生步长卷积。其关键性质是，两个正交卷积的复合结果仍然是正交的。
    *   **构建过程**：AOC通过将RKO核 (KRKO，负责处理步长s) 和BCOP核 (KBCOP，负责定义任意尺寸k) 进行块卷积操作（KAOC = KRKO ⊛ KBCOP），得到一个最终的正交卷积核。这个核的原生尺寸为 `k x k`，步长为 `s`。
    *   **支持现代CNN特性**：
        *   **原生步长**：RKO方法在核尺寸等于步长（`k = s`）时，能保证严格正交。BCOP则可以提供任意大的核尺寸。两者的结合解决了正交卷积缺乏原生步长支持的问题。
        *   **转置卷积**：基于转置卷积的定义和正交矩阵的性质，论文证明，一个正交的直卷积的转置卷积本身就是正交的。AOC首次为**带步长的正交转置卷积**提供了原生支持。
        *   **分组卷积**：AOC利用块卷积的并行化能力，可以独立地构建每一组的正交卷积核，从而原生支持分组卷积。
        *   **膨胀卷积**：论文指出，一个标准卷积如果满足正交性，其对应的膨胀版本（在适当调整填充后）也一定是正交的。
*   **高效实现**：
    *   **并行化块卷积**：通过优化`⊛`算子，利用分组卷积的并行计算能力，大幅提升了其计算效率。
    *   **并行化BCOP**：利用`⊛`算子的结合律，可以将BCOP的序列迭代过程转化为并行关联扫描，将计算复杂度从 `O(k-s)` 降低到 `O(log(k-s))`。
    *   **智能参数化**：根据步长和核大小的不同取值，算法会自适应地选择最简洁的等价参数化形式（例如，直接使用BCOP或RKO），进一步减少冗余计算。

#### 3. 实验设计
*   **数据集/场景**：
    *   **CIFAR-10**：用于评估模型在可证明鲁棒性任务中的表现（验证AOC的表达能力）。
    *   **ImageNet-1K**：用于评估模型在大型数据集上的可扩展性和计算效率。
*   **基准任务**：
    *   **可证明鲁棒性**：训练1-Lipschitz网络（Lipschitz常数为1的神经网络），通过计算“可证明准确率”（Provable Accuracy）来衡量模型在给定L2范数攻击半径下的鲁棒性保证。
*   **对比方法**：
    *   **正交方法**：BCOP, SOC (Skew Orthogonal Convolution), Cayley, LOT, ECO等。
    *   **非正交的Lipschitz方法**：SLL (SDP-based Lipschitz Layer), AOL (Almost-Orthogonal Layer), Sandwich, LiResNets等。
    *   **无约束基准**：标准Conv2d。

#### 4. 资源与算力
*   论文明确提及了所使用的硬件资源，但未提供完整的训练总时长：
    *   CIFAR-10训练：
        *   高精度设置：1块 RTX 3080。
        *   高鲁棒性设置：1块 RTX 4090。
    *   ImageNet-1K训练：
        *   高精度/高鲁棒性设置：2块 RTX 4090。
*   训练周期：实验中的“秦金”（AOC）模型在不同设置下训练了90到3000个周期不等，资源消耗具有可扩展性。

#### 5. 实验数量与充分性
*   **实验数量**：实验覆盖了多个层面，包括：
    *   **核心表达能力验证**：在CIFAR-10和ImageNet-1K上进行了多项鲁棒性训练实验。
    *   **可扩展性验证**：在ResNet-34架构上，系统比较了不同批次大小下，AOC与其他正交方法（BCOP, SOC, Cayley）在训练/测试时间、内存占用上的开销。
    *   **技术深化**：在附录中，AOC被用来改进其他方法（如SOC, SLL, Sandwich），展示了其作为基础框架的潜力。
*   **公平性与客观性**：
    *   论文试图通过Replicating BCOP的基线结果来建立比较基准，并指出AOC的改进在于效率和灵活性，而非模型表达的终极精准度。
    *   实验比较是全面的，包括了对不同尺度、不同模型、不同方法的横向对比。
    *   论文对AOC的局限性（如BCOP参数化空间不完整）进行了公开讨论，并在对比表中明确标注了各种方法的特性支持情况（check mark, cross mark, approximate symbol），展现了较强的客观性。

#### 6. 主要结论与发现
1.  **AOC是有效的**：AOC能够成功构建**严格正交**且支持现代CNN特性的卷积层，并因此训练出具有表达能力的1-Lipschitz网络，在可证明鲁棒性任务上与最先进的方法（如SLL, LiResNets）具有竞争力。
2.  **AOC是可扩展的**：在ImageNet-1K等大型数据集上，AOC的计算开销显著低于现有的正交方法（如SOC, Cayley, BCOP）。随着批量大小增加，其相对于无约束卷积的开销可降低到仅13%（1.13倍），而内存占用几乎不变。这种“随规模扩大而更高效”的特性是AOC的核心优势。
3.  **“旧方法”因规模而受益**：通过AOC的高效实现，原始的BCOP方法在参数量从2.6M扩大到41.3M后，其性能显著提升，变得具有竞争力。
4.  **解锁新架构**：AOC对步长、转置、分组和膨胀卷积的原生支持，首次为这些特性在正交神经网络中的应用打开了大门，特别是在U-Net、VAEs和分组卷积等复杂架构中。

#### 7. 优点
*   **突破性功能**：是首个能够**同时原生支持步长、膨胀、分组卷积和转置卷积**的严格正交卷积方法，填补了领域内的空白。
*   **理论严谨**：建立在严格的正交性数学证明之上，确保了方法的可靠性。
*   **实用性强**：提供开源库**Orthogonium**，且其高效实现使得在大规模应用中使用正交卷积成为可能。方法的计算开销与输入尺寸无关，具有良好的可扩展性。
*   **普适性强**：不仅能独立使用，其框架还可以作为基础技术，用于改进和优化其他现有的正交或Lipschitz约束方法（如SOC, SLL, Sandwich）。

#### 8. 不足与局限
*   **参数化空间不完整**：AOC的核心组件BCOP本身存在参数化空间不完整的问题（即并非所有正交卷积核都能被其参数化空间覆盖）。论文承认，部分“丢失的”正交性可以通过扩大核大小来弥补，但这仍是一个潜在的理论弱点。
*   **对可证明鲁棒性的影响**：在严格的1-Lipschitz网络训练中，“AOC准确”模型虽然干净准确率高（91.5%），但可证明鲁棒性为零，说明它未能充分利用正交性带来的鲁棒性好处。这表明存在准确率-鲁棒性之间的权衡，且AOC本身并不自动解决这一问题。
*   **计算开销**：尽管AOC比现有正交方法快得多，但与无约束的卷积相比，仍然有大约10%~13%的额外开销。对于计算资源极度紧张的场景，这可能仍然是个考虑因素。
*   **对高度专业化场景的适用性**：虽然AOC原理上支持，但论文并未在标准化流、GANs等其他重要应用上进行大规模测试，其在这些领域的实际表现和最优训练策略仍有待探索。

（完）
