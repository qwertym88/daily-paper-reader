---
title: "DeepCrossAttention: Supercharging Transformer Residual Connections"
title_zh: DeepCrossAttention：增强变换器残差连接
authors: "Mike Heddes, Adel Javanmard, Kyriakos Axiotis, Gang Fu, Mohammadhossein Bateni, Vahab Mirrokni"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=j3JBfFnGYh"
tags: ["query:neural-arch"]
score: 9.0
evidence: 通过可学习的交叉注意力增强变换器残差连接
tldr: 传统变换器的残差连接通过简单求和可能稀释关键信息。本文提出DeepCrossAttention（DCA），利用可学习的输入依赖权重动态组合各层输出，并引入深度方向交叉注意力增强层间交互。语言建模实验表明DCA优于标准残差连接，显著提升了模型性能。该方法为改进变换器中的跳跃连接设计提供了新思路，是残差连接变体的重要进展。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 669, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 673, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 727, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 514, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 572, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1542, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 698, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 704, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 675, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 687, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-j3jbffngyh/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1586, \"height\": 1579, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 815, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 775, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 834, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 847, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 757, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 781, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 656, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 691, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-j3jbffngyh/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 825, \"height\": 204, \"label\": \"Table\"}]"
motivation: 传统残差连接简单求和可能稀释关键信息。
method: 提出DCA，使用可学习权重和深度交叉注意力动态融合层输出。
result: 语言建模实验表明DCA优于标准残差连接。
conclusion: DCA为变换器提供了更有效的残差学习机制。
---

## Abstract
Transformer networks have achieved remarkable success across diverse domains, leveraging a variety of architectural innovations, including residual connections. However, traditional residual connections, which simply sum the outputs of previous layers, can dilute crucial information. This work introduces DeepCrossAttention (DCA), an approach that enhances residual learning in transformers. DCA employs learnable, input-dependent weights to dynamically combine layer outputs, enabling the model to selectively focus on the most relevant information in any of the previous layers. Furthermore, DCA incorporates depth-wise cross-attention, allowing for richer interactions between layers at different depths. Our language modeling experiments show that DCA achieves improved perplexity for a given training time. Moreover, DCA obtains the same model quality up to 3x faster while adding a negligible number of parameters (e.g., 0.2\%). Theoretical analysis confirms that DCA provides an improved trade-off between accuracy and model size when the ratio of collective layer ranks to the ambient dimension falls below a critical threshold.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，以下是对论文《DeepCrossAttention: Supercharging Transformer Residual Connections》的详细中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统的Transformer网络依赖于残差连接（Residual Connections）来稳定训练和促进信息流动。然而，标准残差连接只是简单地将各层输出相加，这隐含地假设了所有前层信息同等重要。这种“一视同仁”的求和方式会**稀释**（dilute）关键层携带的有用信息，导致信息瓶颈问题，限制了模型的表示能力和训练效率。
- **研究动机**：作者通过一个简单的实验（让低秩线性网络学习恒等映射）证实了信息稀释现象的存在：即使网络具有完整秩，传统ResNet也难以完美恢复输入，而具有可学习残差权重的模型则能轻松做到。这证明了标准残差连接并非最优，为改进提供了空间。
- **整体含义**：本文旨在解决传统残差连接的信息稀释问题，提出一种更智能、更动态的残差学习机制，以提高Transformer模型的性能、训练速度和参数效率。

### 2. 论文提出的方法论：核心思想、关键技术细节

论文提出了**DeepCrossAttention (DCA)**，其核心思想是通过引入**可学习、依赖于输入的权重**来动态组合各层的输出，并融入**深度方向交叉注意力**以增强层间交互。

**方法论建立在三个递进式的广义残差网络（GRN）上：**

- **GRN-v1 (维度独立权重)**：不再简单求和，而是为每个前层输出学习一个标量权重（\( b_t \)），对层输出进行线性加权组合。权重 \( b_t \) 对所有特征维度共享。这本质上与DenseFormer类似。
- **GRN-v2 (维度相关权重)**：将权重扩展为矩阵（\( b_t \in \mathbb{R}^{d \times t} \)），允许每个特征维度对不同的前层输出拥有不同的权重，增强了特征级别的选择能力。
- **GRN-v3 (输入依赖权重)**：这是最关键的变体。除了维度相关的权重 \( b_t \) 外，还增加了一个由输入 \( x \) 非线性映射得到的权重 \( \bar{w}_t \)（通过 \( \bar{w}_t = \mathbf{1}\sigma(w_t^T G_t) \) 计算）。这使得最终的组合权重可以**根据输入样本动态调整**，实现完全自适应的信息聚合。

**DeepCrossAttention (DCA) 的具体实现：**

- DCA将GRN-v3集成到Transformer的每个解码器块中。
- **三个独立的GRN实例**：在每个DCA块中，为注意力模块的**查询（Query）、键（Key）、值（Value）**分别配备一个独立的GRN-v3实例。这三个GRN接收的是相同的、由所有前层输出构成的“栈”（stack）作为输入，但各自学习不同的权重来生成Q、K、V。这实现了“深度方向交叉注意力”（depth-wise cross-attention），允许模型在不同深度和不同“角色”（Q/K/V）上以不同方式关注前层信息。
- **效率优化**：为减少计算和内存开销，DCA提出了“**首层+最后k层**”策略。在构建“层输出栈” \( \mathbf{G}_t \) 时，只显式包含模型输入和最后k个层的输出，中间的层仍然使用标准的残差求和。实验表明取 \( k = 2 \) 效果很好。

### 3. 实验设计：数据集、Benchmark和对比方法

- **数据集**：
    - **语言建模 (Language Modeling)**：
        - **LM1B** (One Billion Word Benchmark)
        - **C4** (Colossal Clean Crawled Corpus)
    - **图像分类 (Image Classification)**：
        - **ImageNet-1K**
- **Benchmark**：标准Transformer架构（Vaswani, 2017）作为主要的基准模型。
- **对比方法**：
    - DenseFormer (Pagliardini et al., 2024)
    - LAuReL (Menghani et al., 2024)
    - Hyper-Connections (Zhu et al., 2024)
- **评估指标**：
    - **主要指标**：**困惑度 (Perplexity, PPL)**（语言模型）
    - **辅助指标**：准确率 (Accuracy)、训练时间 (Training Time)、Loss峰值 (Loss Spikes)

### 4. 资源与算力

- **未明确说明GPU型号和总数**，但论文提到在 **64个TPU (张量处理单元)** 上进行训练。
- **训练时长**：主要实验训练 **500k步**，总处理 **131B tokens**，批处理大小 (batch size)为 **2048**，序列长度 (sequence length)为 **128**。使用的是 AdamW 优化器。

### 5. 实验数量与充分性

- **实验数量**：论文进行了相当全面和系统的实验，具体包括：
    1.  **模型深度缩放实验**：在LM1B上，模型深度从6层增至42层，展示了DCA在不同深度下的优势。
    2.  **效率优化实验（首/末k层）**：对比不同k值对训练速度、推理速度和最终困惑度的影响。
    3.  **训练时间对比实验**：绘制了不同深度（24, 36, 42层）的Transformer和2-DCA模型的训练时间 vs. 困惑度曲线。
    4.  **模型宽度缩放实验**：在LM1B上，保持12层，将嵌入维度从64增至1024，验证DCA的收益与宽度关系。
    5.  **模型规模缩放实验**：在C4数据集上，训练了从75M到449M参数不等的模型。
    6.  **预训练模型改造实验 (Retrofitting)**：将DCA添加到已预训练好的标准Transformer模型中，观察性能提升。
    7.  **训练稳定性分析**：观察并对比训练过程中的Loss曲线。
    8.  **与相关工作的对比实验**：在同一基准下与DenseFormer、LAuReL、Hyper-Connections进行公平对比。
    9.  **消融实验 (Ablation Study)**：分离GRN-v1, v2, v3和完整DCA的贡献。
    10. **图像分类实验**：将DCA应用于ViT模型进行ImageNet分类。
- **充分性与公平性**：
    - **充分性**：实验覆盖了不同的模型规模（深度/宽度/总参数）、不同数据集（LM1B/C4/ImageNet）、多种架构变体，并做了消融和对比，非常全面。
    - **公平性**：几乎所有对比实验都严格控制了**参数数量**或**训练时间**等变量，确保比较的公平性。例如，在消融研究中，DCA仅比标准Transformer多0.2%的参数。对比不同方法时也控制了参数量。

### 6. 论文的主要结论与发现

1.  **DCA性能显著优于标准Transformer**：在**同等参数预算**和**同等训练时间**下，DCA模型均能取得更低的困惑度（PPL）。例如，30层的DCA比42层的Transformer性能更好，更参数高效。
2.  **训练效率极高**：DCA可以**快达3倍**地达到与标准Transformer相同的模型质量。
3.  **参数效率高**：实现显著性能提升的同时，仅增加了**可忽略不计的参数**（约0.2%）。
4.  **训练更稳定**：DCA能有效缓解大模型训练中常见的 **Loss 尖峰（Loss Spikes）** 问题，训练过程更平滑。
5.  **适用于多种模态**：在语言建模和图像分类（ViT）任务上均验证了其有效性，表明其通用性。
6.  **收益与模型宽度成反比**：实验证实了理论分析——模型宽度越大（rank越高），DCA带来的相对收益越小；但对于更深（而非更宽）的模型，收益依然显著。
7.  **可改造预训练模型**：由于初始化时DCA等价于标准残差网络，可以无缝添加到已预训练的模型中，并进一步提升性能。

### 7. 优点：方法或实验设计上的亮点

- **方法新颖且优雅**：从“信息稀释”这一直观问题出发，通过引入**学习权重 + 输入依赖 + 深度交叉注意力**，逐步构建出一个强大且易于实现的变体。设计思路清晰，逻辑链条完整。
- **理论分析扎实**：作者通过一个线性低秩模型，在理论上证明了DCA（GRN）相比ResNet在测试误差-模型复杂度权衡上的优势，并精确给出了收益的条件和界限。理论与实验结果高度一致，增强了方法的说服力。
- **实验设计严谨且全面**：如上所述，实验覆盖了几乎所有关键维度，变量控制良好。特别是“预训练模型改造”实验，极具实用价值，展示了DCA可以直接“嫁接”到现有强大模型上的潜力。
- **关注实际应用**：提出了“首层+最后k层”的效率优化策略，有效降低了计算和内存成本，提高了实用性。

### 8. 不足与局限

- **实验规模限制**：虽然进行了多规模的实验，但最大模型参数为449M，没有在更大的模型（>1B参数）上进行验证。对于更大模型，DCA的有效性和收益是否还能保持，有待进一步验证。
- **理论分析的近似性**：理论分析主要基于线性低秩模型和特定假设（如 \( A - I \succ 0 \)），虽然能揭示关键趋势，但与真实Transformer的非线性、复杂交互机制存在差距。文中的扩展（如使用瓶颈秩）也只是一个上界分析。
- **效率优化的局限性**：“首层+最后k层”策略虽然提高了效率，但其最优的k值可能依赖于模型深度和任务。此外，即使有优化，DCA的**推理速度**仍然比标准Transformer慢（论文表1显示，即使k=2，推理速度也约为Transformer的66%），这在某些对延迟要求极高的场景下可能是个问题。
- **未探索的方面**：作者没有探讨DCA在不同**注意力头数**下的表现，也没有探讨GRN权重在整个训练过程中的**动态变化**。此外，虽然提到了稳定训练，但未对**Loss尖峰的成因和DCA如何缓解**进行深入分析。
- **对比范围**：虽然对比了三种最新的相关方法，但并未与同样旨在改善信息流动的架构如 **Mixer**、**MLP-Mixer** 或 **状态空间模型 (SSMs)** 等进行对比。

（完）
