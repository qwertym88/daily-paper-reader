---
title: "Convolution Goes Higher-Order:  A Biologically Inspired Mechanism Empowers Image Classification"
title_zh: 卷积迈向高阶：生物启发机制赋能图像分类
authors: "Simone Azeglio, Olivier Marre, Peter Neri, Ulisse Ferrari"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=u3aRwVkBv1"
tags: ["query:neural-arch"]
score: 8.0
evidence: 高阶卷积提升CNN图像分类准确率
tldr: 传统卷积无法捕捉生物视觉中的非线性交互。本文提出可学习的高阶卷积算子，通过Volterra展开模拟生物视觉处理。实验表明，三阶或四阶展开在多个标准基准上持续优于传统CNN基线。系统分析揭示不同阶数处理不同视觉信息，解释模型优势。该工作引入了一种增强CNN表征能力的通用机制。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 861, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 971, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1411, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1427, \"height\": 908, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 393, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1379, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1366, \"height\": 1113, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1441, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1317, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1439, \"height\": 1321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1438, \"height\": 1035, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1465, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1465, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-u3arwvkbv1/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1465, \"height\": 434, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1167, \"height\": 306, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 642, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1453, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 945, \"height\": 736, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 943, \"height\": 736, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 729, \"height\": 143, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 728, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1489, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-u3arwvkbv1/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1511, \"height\": 464, \"label\": \"Table\"}]"
motivation: 受生物视觉非线性处理启发，增强CNN对复杂视觉模式的建模能力。
method: 使用Volterra级数扩展传统卷积，引入可学习的高阶交互项。
result: 在多个图像分类基准上超越传统CNN，最优为三至四阶展开。
conclusion: 高阶卷积有效提升CNN性能，且具有生物学可解释性。
---

## Abstract
We propose a novel enhancement to Convolutional Neural Networks (CNNs) by incorporating learnable higher-order convolutions inspired by nonlinear biological visual processing. Our model extends the classical convolution operator using a Volterra-like expansion to capture multiplicative interactions observed in biological vision. Through extensive evaluation on standard benchmarks and synthetic datasets, we demonstrate that our architecture consistently outperforms traditional CNN baselines, achieving optimal performance with 3rd/4th order expansions. Systematic perturbation analysis and Representational Similarity Analysis reveal that different orders of convolution process distinct aspects of visual information, aligning with the statistical properties of natural images. This biologically-inspired approach offers both improved performance and deeper insights into visual information processing.

---

## 论文详细总结（自动生成）

### 论文核心问题与研究动机

- **研究动机**：传统卷积神经网络（CNN）依赖线性卷积加逐点非线性激活函数，难以有效捕捉自然图像中广泛存在的高阶统计相关性（如纹理、边缘交互、几何结构）。尽管深层网络可通过多层组合逼近复杂函数，但计算成本高且需要大量数据。生物视觉系统（如视网膜、视觉皮层）则通过非线性的非逐点交互（乘法性相互作用）高效处理空间信息。
- **整体含义**：本文提出一种受生物启发的可学习高阶卷积算子，扩展经典卷积操作，使网络能够在较浅架构中直接建模像素间的乘法交互，从而更有效地利用图像中的高阶相关性，提升分类性能并揭示视觉信息处理的深层机制。

### 方法论：高阶卷积

- **核心思想**：将标准卷积扩展为Volterra级数形式，在卷积核中显式包含二阶、三阶乃至更高阶的输入像素乘积项。这使得网络可以学习独立的权重来建模不同阶数的交互，避免了传统点状非线性激活函数所固有的权重耦合问题（即泰勒展开中不同阶次项共享权重）。
- **关键技术细节**：
  - 对输入图像块（展平为向量 x），高阶卷积输出定义为：
    y(x) = b + Σ w_i x_i + Σ Σ w_ij x_i x_j + Σ Σ Σ w_ijk x_i x_j x_k + ...
  - 实际实现时，每个阶数对应一组独立的可学习卷积核（参数数量随阶数增长，利用对称性缩减参数：3×3核二阶从81减至45，三阶从729减至165）。
  - 不同阶数的特征图在逐点非线性（如ReLU）之前求和，形成完整的高阶卷积层。
  - 引入缩放因子 s = 1/√nV 平衡高阶项量级，其中 nV 为对应阶数的参数数量。
- **算法流程**（文字说明）：
  1. 输入图像块展平为向量。
  2. 分别计算一阶（标准卷积）、二阶（外积后点乘权重）、三阶（两次外积后点乘权重）等特征。
  3. 将所有阶特征图相加。
  4. 通过批量归一化、ReLU激活、池化等标准操作。
- **与点状非线性的区别**：高阶卷积直接解耦了不同阶次项的权重，使得网络可以独立学习线性、二次、三次等交互模式，避免了传统CNN中因权重绑定而无法有效捕捉高阶相关性的缺陷。PCA分析证实高阶卷积层产生的激活具有更高的有效维度（解释95%方差所需主成分更多）。

### 实验设计

- **数据集**：
  - **合成纹理数据集**：基于Victor & Conte方法生成包含1-4点相关性的二值纹理（10类，每类对应不同阶数和朝向的glider）。
  - **标准图像分类基准**：MNIST、FashionMNIST、CIFAR-10、CIFAR-100、Imagenette、ImageNet。
  - **细粒度分类**：CUB-200-2011（鸟类，200类）。
  - **鲁棒性测试**：CIFAR-10-C / CIFAR-100-C。
- **对比方法**：
  - 标准CNN基线（相同架构但使用普通卷积）。
  - 更深层的CNN（增加层数/通道数，对比参数量相近或FLOPs相近）。
  - 对于ImageNet等：标准ResNet-18/34/50 vs 高阶ResNet-18/34/50（HoResNet）。
  - 额外对比VOneNet（另一种生物启发模型）。
- **训练设置**：AdamW优化器、学习率0.001、权重衰减5e-4、批次64、交叉熵损失、早停；ImageNet使用SGD动量0.9；无数据增强（MNIST/CIFAR等），ImageNet使用标准增强。

### 资源与算力

- **硬件**：
  - MNIST/FashionMNIST/CIFAR-10/CIFAR-100：NVIDIA RTX 4080 Ti GPU。
  - ImageNet：NVIDIA A100 GPU。
- **训练时长**：
  - MNIST/FashionMNIST：约10-15分钟（HoCNN耗时1.5-2倍）。
  - CIFAR-10/100：约20-30分钟（HoCNN耗时1.5-2倍）。
  - Imagenette：约4-5小时。
  - ImageNet：约2-3天（每个运行）。
- **参数和FLOPs**：
  - HoCNN 3×3核三阶参数约80k（低于基线CNN的82k）。
  - FLOPs：二阶约5倍于标准卷积，三阶约18倍；HoResNet-18整体仅增加1.45-1.65倍FLOPs（因仅在首层使用高阶）。

### 实验数量与充分性

- **实验数量**：
  - MNIST/FashionMNIST/CIFAR-10/100：每个模型50次随机初始化，报告平均值和标准差（统计鲁棒）。
  - ImageNet：5次独立运行。
  - 合成纹理：单次（但四个模型对比）。
  - 鲁棒性测试：17种腐败，5个严重级别。
  - 消融实验：高阶层放置位置（第1/2/3层）、核大小（2×2 vs 5×5 vs 7×7）、不同非线性函数下的PCA分析。
  - ResNet深度缩放实验（R18/R34/R50）。
  - 细粒度分类CUB-200-2011。
- **充分性与公平性**：
  - 实验覆盖了从简单到复杂、从合成到真实、从标准分类到鲁棒性测试等多维度，具有全面性。
  - 公平性：基线CNN与HoCNN参数量相近或略多，确保对比公平；FLOPs控制实验也排除了计算量优势。
  - 但部分实验（Imagenette、CUB-200-2011）仅单次运行，未报告方差，统计可靠性略逊于主实验。

### 主要结论与发现

1. **性能提升**：高阶CNN在所有测试数据集上一致超越标准CNN基线，尤其对复杂数据集（CIFAR-10提升3.1%，CIFAR-100提升3.5%，ImageNet提升0.85%，CUB-200-2011提升4.07%）。
2. **最优阶数**：3阶或4阶展开达到最优，与自然图像中像素强度高阶相关性分布规律一致（Koenderink等人发现三次/四次项分别占约35%/2%）。
3. **表征差异**：Representational Similarity Analysis（RSA）显示高阶CNN的内部表征具有更分散的类特异性结构，2阶和3阶分量分别捕捉不同尺度的模式。
4. **鲁棒性**：对非结构性扰动（CIFAR-10-C/100-C）鲁棒性更好，但对特定高阶统计扰动更敏感，验证了模型确实利用了高阶信息。
5. **权重独立性**：PCA分析证实高阶卷积有效缓解了传统CNN中的权重耦合问题，增加了表征空间的维度。

### 优点

- **生物启发明确**：直接引用视网膜和视觉皮层中乘法性交互的神经机制，算法设计有坚实的神经科学基础。
- **数学框架清晰**：Volterra展开形式简洁，易于理解和实现；在理论上解释了与点状非线性的本质区别（权重解耦）。
- **实验设计全面**：从合成纹理到真实大规模数据集，从分类性能到内部机制分析，从参数量控制到FLOPs控制，实验严谨、对比公平。
- **消融深入**：系统分析了高阶层位置、核大小、不同阶数贡献、不同非线性函数等影响因素。
- **跨架构有效**：不仅适用于浅层CNN，也兼容ResNet等深层结构，在ImageNet上验证了可扩展性。
- **提供可解释性**：通过扰动分析和RSA揭示了不同阶数处理不同视觉特征，与自然图像统计对齐，增强了模型可解释性。

### 不足与局限

- **计算复杂度**：2阶和3阶卷积分别增加5倍和18倍FLOPs，虽然通过仅首层使用部分缓解，但对资源受限场景仍是显著开销。
- **参数量增长**：高阶项参数数量随阶数快速增长（尽管利用对称性缩减），限制了实际应用超过4阶的可能性。
- **部分实验统计性不足**：Imagenette和CUB-200-2011仅单次运行，未报告方差，降低了结论的稳健性。
- **鲁棒性双刃剑**：对高阶统计扰动更敏感，可能在某些对抗场景下更脆弱。
- **缺乏低秩近似**：当前实现未采用低秩分解等加速技术，未来可进一步优化。
- **未与Transformer对比**：虽然讨论中提到可能与ViT互补，但未进行实验对比，尚不清楚在同等FLOPs下高阶卷积与注意力机制的相对优势。

（完）
