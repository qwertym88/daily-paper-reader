---
title: "Deep Edge Filter: Return of the Human-Crafted Layer in Deep Learning"
title_zh: 深度边缘滤波器：深度学习中人造层的回归
authors: "Dongkwan Lee, Junhoo Lee, Nojun Kwak"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QcItn1s1jO"
tags: ["query:neural-arch"]
score: 7.0
evidence: 提出一种新颖的高通滤波层，跨领域提升模型准确率
tldr: 本文提出深度边缘滤波器，通过对深度特征进行高通滤波来提升模型泛化能力。其核心思想是神经网络在深层特征中将任务相关语义信息编码在高频分量，而领域偏差存储在低频分量。通过减去低通滤波输出，该方法隔离出可泛化的表示，同时保持架构完整。在视觉、文本、3D和音频等多个领域的实验表明，该方法能够一致提升性能，并诱导特征稀疏化。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 284, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1156, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1297, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1406, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1407, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1432, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qcitn1s1jo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1430, \"height\": 352, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 603, \"height\": 184, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1159, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 970, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 932, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1449, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1446, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-qcitn1s1jo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 791, \"height\": 221, \"label\": \"Table\"}]"
motivation: 深度学习模型在不同领域泛化能力有限，现有方法未充分利用特征频率特性。
method: 提出Deep Edge Filter，通过对深层特征进行高通滤波，减去低通分量，保留高频语义信息。
result: 在视觉、文本、3D和音频任务上一致提升性能，且与模型架构无关。
conclusion: 高频特征包含可泛化表示，该层可即插即用提升模型泛化性。
---

## Abstract
We introduce the Deep Edge Filter, a novel approach that applies high-pass filtering to deep neural network features to improve model generalizability. Our method is motivated by our hypothesis that neural networks encode task-relevant semantic information in high-frequency components while storing domain-specific biases in low-frequency components of deep features. By subtracting low-pass filtered outputs from original features, our approach isolates generalizable representations while preserving architectural integrity. Experimental results across diverse domains such as Vision, Text, 3D, and Audio demonstrate consistent performance improvements regardless of model architecture and data modality. Analysis reveals that our method induces feature sparsification and effectively isolates high-frequency components, providing empirical validation of our core hypothesis. The code is available at \url{https://github.com/dongkwani/DeepEdgeFilter}.

---

## 论文详细总结（自动生成）

# 论文深度总结：Deep Edge Filter

## 1. 核心问题与整体含义（研究动机和背景）

深度学习模型虽然在多个领域表现出色，但对扰动和领域偏移（domain shift）非常脆弱。传统边缘滤波器（如 Sobel、Canny）虽然能提供鲁棒先验，但直接在输入图像上应用会丢失细粒度信息，且局限于图像模态，难以推广到文本、3D、音频等多样数据。作者的核心假设是：**神经网络在深层特征中将任务相关的语义信息编码在高频分量中，而领域特定的偏差（如光照、纹理、背景）存储在低频分量中**。基于此，他们提出 **Deep Edge Filter**：通过从原始特征中减去低通滤波结果，实现高通滤波，从而分离出可泛化的表示，同时保持架构完整性。该方法是一种可即插即用的轻量化层，不改变模型结构。

## 2. 方法论：核心思想、关键技术细节

*   **核心思想**：将经典的高通边缘滤波思想推广到深层特征上。假设特征可分解为 `h = h_sem + h_dom`，其中 `h_sem` 是高频语义信息，`h_dom` 是低频领域偏差。通过设计 `F_edge(h) = h - LPF(h)`（LPF为低通滤波器，如均值、中值、高斯核），得到近似语义成分的高频输出。
*   **关键技术细节**：
    *   **滤波器实现**：默认使用均值滤波。对于 CNN 架构，使用 2D 核（在空间维度上滑动）；对于 Transformer/MLP 架构，使用 1D 核（沿序列长度维度滑动）。滤波时采用 **reflect padding** 保持尺寸不变，且 **LPF 部分梯度被截断（detach）**，不参与反向传播，仅对高通输出进行训练。
    *   **插入位置**：一般仅在模型某个中间块后插入一个 Edge Filter（而非多层），避免信息过度丢失。通过消融实验确定最佳层位置和核大小。
    *   **实现简单**：无需额外参数学习，仅需指定核大小和滤波器类型。

## 3. 实验设计

*   **覆盖模态与任务**：
    *   **视觉 (Vision)**：测试时适应 (TTA)，使用 CIFAR-10C/100C、ImageNet200-C 基准。模型：WRN-28-10、ResNet18、ViT-B/32。对比方法：无滤波、NORM、TENT。
    *   **语言 (Language)**：GLUE 子任务（SST-2 情感分析、QQP 释义检测、QNLI 推理）。模型：BERT（12层Transformer）。
    *   **3D**：Few-shot Neural Radiance Field (NeRF)，使用 Blender 数据集（8-view设定）。模型：NeRF（MLP结构）。指标：PSNR、SSIM、LPIPS、MAE。
    *   **音频 (Audio)**：UrbanSound8K 分类。模型：3 个卷积块构成的 CNN。
*   **基准对比**：均与不使用任何滤波的基线模型（Vanilla）比较，并在 TTA 中进一步比对了 TENT、NORM 等算法。
*   **消融实验**：
    *   不同滤波器类型（均值、中值、高斯）作为 LPF 时的效果。
    *   直接应用低通滤波（LPF）而非 Edge Filter 造成的性能下降（证明了低频保留领域偏差）。
    *   对插入层位置和核大小进行网格搜索（热图展示）。
    *   额外验证：将 Edge Filter 替换为同等计算量的可训练卷积层，未观测到提升，排除了计算量增加带来的影响。
*   **分析实验**：
    *   激活密度随训练 epoch 的变化（显示 Edge Filter 导致特征稀疏化）。
    *   对深层特征进行 FFT 分析（证实低频分量被有效抑制）。
    *   t-SNE 可视化（在 CIFAR-10C 上显示加了 Edge Filter 的模型类别边界更清晰）。
    *   跨领域小样本分类（在 PACS、DomainNet 上验证了在更大基础模型 ViT-L/14 OpenCLIP 上仍有效）。

## 4. 资源与算力

文中提到：“All experiments were run using a single A6000 GPU.” 此外没有具体说明每个实验的GPU小时数。由于需要从头训练或微调多个模型（WRN/ViT/BERT/NeRF/CNN），算力需求中等，但推理成本极低（滤波器无参）。论文也承认由于计算资源限制，未能在大规模语言模型（LLM）上进行实验。

## 5. 实验数量与充分性

*   **数量充分**：覆盖 4 个模态、多种架构（CNN、Transformer、MLP）、多个数据集（共约10+个标准benchmark）。消融实验包括滤波器类型、核大小、插入层位置、统计显著性测试（重复5次种子）。此外还有额外的跨领域小样本实验和计算量控制实验。
*   **公平性**：对比基线均为官方标准设置或复现代码；TTA任务中使用相同预训练和TTA算法；消融实验严格变量控制。作者也报告了不同随机种子的均值和标准差，并显示性能提升普遍超过2σ统计显著。
*   **潜在不足**：部分实验（如NeRF、音频）仅报告单次结果（未重复）；语言任务仅用了BERT（较小）；未在大规模模型（LLaMA、GPT等）上验证，可能限制了结论的通用性。

## 6. 主要结论与发现

1.  **Edge Filter 能一致提升模型泛化能力**：在所有测试模态和任务上，性能均有改善（0.1%p至10.2%p不等），尤其在领域偏移大的场景（如CIFAR-100C直接测试提升10.2%p）。
2.  **核心假设得到验证**：低通滤波直接应用会显著降低性能（如CIFAR-10C下降9.95%p），而高通滤波提升性能；FFT分析确认了低频分量被抑制；特征稀疏化表明高频成分是关键。
3.  **架构无关**：在CNN、Transformer、MLP上均有效，且1D/2D滤波器适配自然。
4.  **即插即用且轻量**：无需大量调参，单一层即可带来收益，且计算量极小。

## 7. 优点

*   **简洁高效**：仅需一行代码（h - mean_filter(h)），无额外可学习参数，易于集成到现有模型。
*   **跨模态通用性**：首次将边缘滤波思想系统推广到非图像模态（文本、3D、音频），实验设计全面。
*   **理论解释清晰**：从频率分解和稀疏编码角度提供了理论动机，并通过 FFT、密度分析、线性探测等实验验证。
*   **消融彻底**：详细分析了滤波器类型、位置、核大小的影响，并排除了计算量增加混淆因素。
*   **统计显著验证**：在多个条件下报告了重复实验结果并确认显著性。

## 8. 不足与局限

*   **实验覆盖有限**：语言任务仅使用 BERT，未在更大 LLM（如 GPT、LLaMA）上测试；NeRF 和音频实验未报告多次运行结果；视觉 TTA 也未涵盖所有主流算法（如 MEMO、CoTTA）。
*   **性能有时下降**：在部分场景（如 NeRF 中的 ficus 场景、ViT 早期层插入高斯滤波）出现退化，说明超参数敏感，需要网格搜索。
*   **理论支撑偏定性**：虽然提供了假设和实证，但缺少严格的数学证明，例如频率分量与语义/领域信息之间并非严格正交，可能存在混叠。
*   **计算资源限制**：作者自述无法进行更广泛的实验（如 LLM、SOTA 模型），可能导致结论在极大规模模型上是否成立存疑。
*   **局限性讨论**：论文在结尾承认这些限制，并指出未来方向包括应用到多模态和更大模型。

（完）
