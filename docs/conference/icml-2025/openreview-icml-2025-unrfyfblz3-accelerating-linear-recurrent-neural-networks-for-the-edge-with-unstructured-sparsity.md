---
title: Accelerating Linear Recurrent Neural Networks for the Edge with Unstructured Sparsity
title_zh: 使用非结构化稀疏加速线性递归神经网络在边缘端的推理
authors: "Alessandro Pierro, Steven Abreu, Jonathan Timcheck, Philipp Stratmann, Andreas Wild, Sumit Bam Shrestha"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=UNrfYfbLZ3"
tags: ["query:neural-arch"]
score: 5.0
evidence: 线性RNN推理的高效稀疏化
tldr: 线性RNN虽适合边缘推理，但需要硬件感知优化。本文系统研究非结构化稀疏在多种线性RNN上的表现，发现高稀疏度可一致改善效率-性能权衡，为边缘部署提供指导。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 754, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1609, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1761, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1714, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 848, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 853, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1748, \"height\": 953, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 846, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1658, \"height\": 674, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-unrfyfblz3/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1405, \"height\": 766, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-unrfyfblz3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1604, \"height\": 558, \"label\": \"Table\"}]"
motivation: 线性RNN在资源受限环境下部署需要优化。
method: 通过非结构化稀疏性降低计算和内存，进行缩放研究找到最优稀疏度。
result: 高稀疏线性RNN在效率-性能Pareto前沿上持续优于稠密模型。
conclusion: 非结构化稀疏是加速线性RNN边缘推理的有效手段。
---

## Abstract
Linear recurrent neural networks enable powerful long-range sequence modeling with constant memory usage and time-per-token during inference. These architectures hold promise for streaming applications at the edge, but deployment in resource-constrained environments requires hardware-aware optimizations to minimize latency and energy consumption. 
Unstructured sparsity offers a compelling solution, enabling substantial reductions in compute and memory requirements--when accelerated by compatible hardware platforms. 
In this paper, we conduct a scaling study to investigate the Pareto front of performance and efficiency across inference compute budgets.
We find that highly sparse linear RNNs *consistently* achieve better efficiency-performance trade-offs than dense baselines, with $2\times$ less compute and $36$\% less memory at iso-accuracy.
Our models achieve state-of-the-art results on a real-time streaming task for audio denoising.
By quantizing our sparse models to fixed-point arithmetic and deploying them on the Intel Loihi 2 neuromorphic chip for real-time processing, we translate model compression into tangible gains of $42\times$ lower latency and $149\times$ lower energy consumption compared to a dense model on an edge GPU.
Our findings showcase the transformative potential of unstructured sparsity, paving the way for highly efficient recurrent neural networks in real-world, resource-constrained environments.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：线性递归神经网络（Linear RNNs，如S5架构）在长序列建模中具有内存消耗恒定、推理时每token时间线性的优势，非常适合流式边缘应用（如音频去噪、关键词检测）。但在资源受限的边缘设备上部署，需要减少延迟和能耗，而传统GPU难以高效利用非结构化稀疏性。
- **核心问题**：本文系统探究非结构化稀疏性（权重和激活）能否为线性RNN带来效率-性能的帕累托改进，并最终在神经形态硬件（Intel Loihi 2）上实现实际加速。
- **整体含义**：通过结合权重剪枝、激活稀疏化（ReLU替换GELU）和定点量化，高稀疏度线性RNN可在保持精度的前提下大幅降低计算量和内存占用，并在支持非结构化稀疏的硬件上获得数十倍的延迟和能耗收益，为边缘AI部署提供了可行路径。

## 2. 提出的方法论：核心思想、关键技术细节

### 核心思想
- **模型压缩与加速流水线**：先对预训练稠密S5模型进行**非结构化权重剪枝**（迭代幅度剪枝IMP）和**激活稀疏化**（ReLU替换GELU，并插入额外ReLU），再结合**量化感知训练（QAT）** 将模型转换为W8A16定点算术，最后部署到Intel Loihi 2神经形态芯片上，利用其事件驱动架构高效利用稀疏性。

### 关键技术细节

#### a. 权重剪枝（Iterative Magnitude Pruning, IMP）
- 使用三次多项式调度逐步增加稀疏度（从0%到目标水平，在总训练步数的75%时达到目标）。
- 采用Erdős–Rényi–Kernel (ERK)策略为各层分配不同的稀疏度，保留梯度更新（Straight-Through Estimator）。
- 最终所有实验的权重稀疏度设为90%。

#### b. 激活稀疏化（ReLU-fication）
- 将原始S5中的GELU替换为ReLU（产生更多零激活）。
- 在GLU块的残差加法后、以及S5隐藏层实部之后插入额外ReLU，进一步增加预激活稀疏性。
- 权重复活与激活稀疏化在训练开始前即应用，然后联合训练。

#### c. 量化与定点计算
- 采用**量化感知训练（QAT）** 进行8位权重、16位激活的定点量化（W8A16），对角线递归权重采用16位。
- 使用静态（static）量化策略，预计算所有缩放因子，使得模型可完全使用定点（整数）算术在Loihi 2上运行。

#### d. 硬件适配（映射到Loihi 2）
- 复数矩阵拆分为实部/虚部，通过多个突触层实现。
- 将逐元素操作（BatchNorm、Hadamard积、残差加、对角乘等）融合到可编程神经元层中，减少层数和通信开销。
- 整个S5架构在Loihi 2上只需1个编码器神经元组、1个解码器神经元组和每个S5块3个神经元组。

## 3. 实验设计

### 数据集 / 场景
- **主要任务**：Intel Neuromorphic Deep Noise Suppression (N-DNS) Challenge 音频去噪任务。
  - 数据来源：Microsoft DNS Challenge，包括干净语音和噪声样本。
  - 训练/验证集各60,000个30秒样本，测试集12,000个样本。
  - 采用STFT（32ms窗口，8ms跳步），实时推理延迟预算为8ms。
  - 评价指标：尺度不变信噪比（SI-SNR）。
- **辅助任务**：Speech Commands V2-35 关键词识别（见附录A.3.1），验证方法迁移性。

### Benchmark
- 对比方法：
  - 本工作的稠密S5基线（不同宽度缩放因子）。
  - 先前SOTA：Spiking-FullSubNet XL（15.2 dB SI-SNR，N-DNS挑战赛Track 1获胜者）。
- 硬件对比：在Intel Loihi 2与NVIDIA Jetson Orin Nano上分别部署稀疏量化模型和等效精度的稠密FP32模型，测量延迟、能耗、吞吐量。

### 对比方法
- 自身对比：不同宽度缩放的稠密模型（缩放因子0.25~1.0） vs. 稀疏模型（缩放因子0.5~3.0），在90%权重稀疏度和ReLU激活下。
- 量化对比：PTQ（后训练量化） vs. QAT（量化感知训练） vs. 全精度FP32。
- 硬件模式对比：Loihi 2的fall-through（低延迟）与pipelined（高吞吐）模式；Jetson Orin Nano的不同批大小和扫描模式。

## 4. 资源与算力

文中没有明确说明训练所需的GPU型号、数量或具体训练时长。
- 软件环境：JAX 0.4.30，使用JaxPruner做剪枝，AQT库做量化感知训练。
- 推测训练规模：在50个epoch内完成，使用Adam优化器，学习率余弦退火。所有实验（包括多次缩放、消融）可能使用单卡或少量GPU，但作者未披露。
- 硬件测试：Jetson Orin Nano 8GB（Jetpack 6.2，CUDA 12.4，MAXN SUPER电源模式）；Loihi 2使用Oheo Gulch系统（N3C1修订版芯片，NxCore 2.5.8，NxKernel 0.2.0）。
- 备注：缺少显式的训练算力报告是该文的一个小不足。

## 5. 实验数量与充分性

### 实验数量
- **主要帕累托前沿实验**：测试了12种不同宽度的稀疏模型和4种稠密模型在N-DNS任务上的SI-SNR与有效MACs/内存占用。
- **消融实验**：
  - 权重稀疏度 vs. 激活稀疏度交互分析（图5）。
  - 量化方法对比：PTQ vs. QAT vs. 全精度（图6）。
  - 定点模拟与Loihi 2实际部署的精度对比（图6）。
  - 定点误差逐层分析（附录A.3.3，图11）。
  - Loihi 2不同执行模式（fall-through vs. pipelined）性能对比（附录A.3.2）。
  - 批处理对延迟和能耗的影响（图7）。
- **辅助任务**：Speech Commands关键词识别（附录A.3.1，图9），验证了稀疏模型Pareto优势的泛化性。

### 充分性评价
- **充分**：覆盖了从算法设计（剪枝、激活稀疏化、量化）到硬件部署（多种模式、批处理）的完整链路，消融实验全面，结果一致性强。
- **客观公平**：硬件对比采用了等精度模型（稀疏-8 vs. 稠密-3），并考虑了多种执行模式下公平比较（实时约束、离线吞吐等）。未刻意选择有利于Loihi 2的模式。
- **潜在偏倚**：只用了S5一种线性RNN架构，未扩展到Mamba或其他变体；主要任务为音频去噪，任务多样性有限；硬件对比中Jetson运行的是FP32（而非定点优化版），可能未完全发挥Jetson潜力，但作者已指出这一点有限制。

## 6. 主要结论与发现

1. **高稀疏线性RNN一致优于稠密基线**：在相同推理计算预算下，稀疏模型构成效率-性能的帕累托前沿。例如，稀疏-8模型相比等精度稠密-3模型**减少2×计算量**和**36%内存占用**。
2. **达到SOTA音频去噪效果**：稀疏-11模型SI-SNR达到15.2 dB（与Spiking-FullSubNet XL持平），但**计算量减少3.2×，内存减少5.37×**。
3. **固定点量化可有效压缩**：QAT显著优于PTQ，使模型从FP32转换到W8A16定点后性能损失极小；定点模拟与Loihi 2部署之间有额外少量退化（主要由累积舍入误差和溢出处理方式不同导致）。
4. **硬件实测增益巨大**：在实时逐token处理模式下，Loihi 2比Jetson Orin Nano**延迟低42倍**，**能耗低149倍**（符合8ms实时预算时仍低3倍以上）。在线下批量模式（单序列）下，Loihi 2吞吐量高3.7倍，能耗低8倍。
5. **权重稀疏与激活稀疏存在交互**：权重稀疏模型会降低激活稀疏度（模型补偿信息流），且激活稀疏度随深度递减；未来需设计更高效的控制性激活函数（如近似top-k）。

## 7. 优点

- **方法创新**：系统结合了权重非结构化剪枝、激活稀疏化（ReLU-fying）和定点量化，首次在神经形态芯片上完整验证了线性RNN的压缩-加速流水线。
- **实验设计完备**：从算法帕累托分析到硬件实测，覆盖多个维度（计算、内存、延迟、能耗），消融实验充分，对比公平。
- **硬件适配深入**：针对Loihi 2的特性（事件驱动、本地状态更新、低精度等）进行了细致映射和优化，并分析了不同执行模式的权衡。
- **开源与可复现**：提供了代码仓库（github.com/IntelLabs/SparseRNNs），实验设置详细。
- **实际应用价值**：音频去噪是典型的流式边缘任务，结果直接表明稀疏线性RNN在资源受限设备上的可行性和高效性。

## 8. 不足与局限

- **架构单一**：仅对S5（一种对角线性RNN）进行了实验，未推广到其他线性RNN变体（如Mamba、RWKV等），泛化性待验证。
- **任务多样性有限**：主要实验基于音频去噪；仅在附录中增加了关键词识别单任务，标准长序列基准（如LRA）未涉及。
- **硬件对比不完全公平**：Jetson Orin Nano上仅运行FP32模型（而非定点优化版本），这可能高估了其能耗/延迟优势；作者已承认此局限。
- **定点转换精度损失**：从FP32到定点QAT损失很小，但Loihi 2实际部署仍有1-2 dB SI-SNR下降，且误差随深度线性累积，对于更深的模型可能成为问题。
- **未探索极端稀疏度与更宽模型**：权重稀疏度固定为90%，未对比其他稀疏水平（如95%、99%）；稀疏模型宽度范围（缩放因子0.5~3.0）仍有限，更高缩放可能进一步改善帕累托前沿。
- **训练算力未报告**：缺乏训练时间、GPU型号与数量信息，不利于复现和成本估计。
- **批处理可扩展性受限**：Loihi 2上批处理通过物理复制模型实现，对芯片面积需求线性增长，不适用于大模型或大批次。

（完）
