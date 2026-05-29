---
title: One-dimensional Path Convolution
title_zh: 一维路径卷积
authors: "Xuanshu Luo, Martin Werner"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=9aEYGpSV6v"
tags: ["query:neural-arch"]
score: 9.0
evidence: 新颖的一维CNN架构达到ResNet级精度
tldr: 现有2D卷积在参数效率上存在瓶颈。本文提出PathConv，通过路径卷积和路径移位技术，仅用1D操作实现保局域的图像遍历，在ImageNet上以1/3参数达到ResNet精度，极大降低了计算开销。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 836, \"height\": 577, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 518, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 838, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1733, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 413, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 543, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1630, \"height\": 1702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9aeygpsv6v/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1353, \"height\": 618, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 738, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 1334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 1028, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 682, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1539, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1645, \"height\": 592, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1351, \"height\": 627, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1233, \"height\": 627, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9aeygpsv6v/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1181, \"height\": 532, \"label\": \"Table\"}]"
motivation: 2D卷积参数多，1D卷积破坏图像局部性。
method: 提出PathConv，使用希尔伯特/ Z阶路径和一维卷积，并引入路径移位修复牺牲像素。
result: 在ImageNet上以1/3参数达到ResNet-50级别精度。
conclusion: PathConv证明纯1D卷积可在图像分类中获得竞争力。
---

## Abstract
Two-dimensional (2D) convolutional kernels have dominated convolutional neural networks (CNNs) in image processing. While linearly scaling 1D convolution provides parameter efficiency, its naive integration into CNNs disrupts image locality, thereby degrading performance. This paper presents path convolution (PathConv), a novel CNN design exclusively with 1D operations, achieving ResNet-level accuracy using only 1/3 parameters. To obtain locality-preserving image traversal paths, we analyze Hilbert/Z-order paths and expose a fundamental trade-off: improved proximity for most pixels comes at the cost of excessive distances for other sacrificed ones to their neighbors. We resolve this issue by proposing path shifting, a succinct method to reposition sacrificed pixels. Using the randomized rounding algorithm, we show that three shifted paths are sufficient to offer better locality preservation than trivial raster scanning. To mitigate potential convergence issues caused by multiple paths, we design a lightweight path-aware channel attention mechanism to capture local intra-path and global inter-path dependencies. Experimental results further validate the efficacy of our method, establishing the proposed 1D PathConv as a viable backbone for efficient vision models.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：传统的2D卷积在图像处理中占主导地位，但其参数数量随核大小二次增长，效率较低。1D卷积虽然参数线性增长，但直接用于图像会破坏像素间的空间局部性，导致性能下降。
- **核心问题**：如何利用纯1D卷积构建视觉模型，在保持参数高效的同时克服局部性丧失的问题，使性能媲美2D CNN。
- **整体含义**：论文提出了一种全新的1D卷积神经网络架构——PathConv，通过使用希尔伯特曲线或Z阶曲线等空间填充曲线来遍历图像，并设计路径移位方法修复被牺牲的像素，最终仅用ResNet约1/3的参数即可达到同等精度，为高效视觉模型提供了新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：用1D卷积替代2D卷积，但利用空间填充曲线（希尔伯特曲线、Z阶曲线）将2D图像映射为1D像素流，以保留局部性；并通过路径移位（Path Shifting）来解决曲线本身存在的“牺牲像素”问题（即某些像素与其邻居在1D序列中距离过长）。
- **关键技术细节**：
  - **路径移位（Path Shifting）**：对于给定尺寸s×s的图像，从扩大的空间填充曲线（大小为s+p）中采样一个s×s的窗口，通过调整填充大小p、窗口位置[i,j]和旋转角度r来生成多个移位路径。每个配置c={p, [i,j], r}对应一个移位路径。
  - **最小路径集确定**：将寻找满足“每个像素都比光栅扫描路径更靠近邻居”的最小路径集问题归约为NP难集合覆盖问题。使用随机舍入算法（Randomized Rounding）求解，实验表明3条移位路径即可满足条件（记为C*）。
  - **PathConv模型架构**：
    - **路径遍历层**：将输入图像按多条路径分别展平为1D像素流，并使用CUDA kernel加速（加速比可达73倍）。
    - **主干网络**：采用类似ResNet的四阶段设计，包含stem层（点卷积+深度卷积+位置编码）、PathConv块（含路径感知通道注意力PACA和倒置瓶颈结构）、下采样层。
    - **路径感知通道注意力（PACA）**：先按路径分组计算双尺度通道内注意力，再通过MLP计算路径间注意力，最终融合以动态调整特征。仅引入对数级参数，有效缓解多路径带来的收敛困难。
- **算法流程**（文字说明）：
  1. 对输入图像，为每条路径生成像素坐标序列（通过预计算的移位配置）。
  2. 图像遍历层并行地将图像按多条路径展平成1D序列。
  3. 经过stem层（点卷积+深度卷积+位置编码）后，进入四个阶段：每个阶段由若干个PathConv块组成，块内先做深度可分离1D卷积（核大小11），然后经过PACA模块，最后通过倒置瓶颈。
  4. 下采样层使用步长为2的深度卷积（核大小9），最后用全连接分类头输出。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：CIFAR-10 (32×32)、SVHN (32×32)、ImageNet-64 (64×64，1000类，完整ImageNet-1K的下采样版本)。
- **基准**：主基准为ResNet-18/50（与PathConvS/B的FLOPs相近），另外在ImageNet-64上还对比了Wide ResNet（WRN-40-2和WRN-40-5）。
- **对比方法**：PathConv模型提供了三种路径选择：光栅扫描（Rs）、希尔伯特路径C*（HC*_s）、Z阶路径C*（ZC*_s）。另外还对比了单路径（Hs/Zs）和六路径（C+）的影响。通过消融实验验证位置编码和PACA的必要性。

## 4. 资源与算力

- 论文在附录E中提及CUDA kernel实现，并报告了在**1块NVIDIA A100 GPU**上的测试结果（加速比最高73.7倍）。
- 训练设置（附录F）中未明确说明具体使用的GPU数量，但从batch size（CIFAR/SVHN为512，ImageNet-64为384）推测可能使用单卡或多卡，但未明确。
- 训练轮数：所有模型训练300个epoch。
- 未给出总训练时长，但给出了求解最小路径集C*的时间（例如对s=64的希尔伯特路径，随机舍入算法平均7134.6秒；贪心算法平均634.6秒）。

## 5. 实验数量与充分性

- **主要实验**：在三个数据集上对比了PathConvS/B与ResNet-18/50以及WRN，每组实验报告了参数量、FLOPs和Top-1准确率。
- **路径选择分析**：评估了不同路径类型（Hs vs Zs vs C* vs C+）在不同分辨率下的表现，以及不同路径数量（1、3、6）的影响。
- **消融实验**：单独移除位置编码和PACA模块，验证其重要性；共4组（有/无两者）。
- **充分性评价**：实验设计较为全面，覆盖了不同数据集、不同模型规模、不同路径策略，并进行了算法复杂度分析和替代贪心算法的比较。但仅使用低分辨率数据集（最高64×64），未在ImageNet-1K原始分辨率（224×224）上验证，可能影响结论的泛化性。实验数量在常见顶会论文中属于中等偏上。

## 6. 论文的主要结论与发现

- PathConv模型（使用C*路径）在三个数据集上均以约1/3的参数量达到了与ResNet相当的Top-1精度，部分情况下甚至略优（如CIFAR-10下PathConvB-HC*_s 93.97% vs ResNet-50 93.95%；ImageNet-64下PathConvB-ZC*_s 68.83% vs ResNet-50 68.43%）。
- 光栅扫描路径导致性能严重下降（例如ImageNet-64下降8%以上），证明局部性保留至关重要。
- 3条移位路径（C*）是最优选择：少于3条无法满足所有像素的局部性约束，多于3条（如6条）会因多路径导致收敛困难而性能下降。
- 路径感知通道注意力（PACA）和位置编码是PathConv模型中不可或缺的组件，移除后性能显著下降（尤其在ImageNet-64上降幅达15%以上）。
- 路径移位方法不仅适用于方形图像，也适用于矩形图像，且能扩展Z阶曲线对非2^n尺寸的支持。

## 7. 优点：方法或实验设计上的亮点

- **方法创新性**：首次系统性提出纯1D卷积视觉模型并达到现代CNN水平，打破了2D卷积的垄断。路径移位策略简洁有效，将集合覆盖理论应用于路径选择。
- **参数效率极高**：仅用1/3参数达到同等性能，有利于移动端和边缘设备部署。
- **计算效率**：1D卷积的线性缩放特性使其硬件实现更高效，且CUDA kernel设计使图像遍历开销可忽略。
- **实验设计严谨**：不仅对比主流ResNet，还对比了Wide ResNet；分析了路径选择、路径数量对性能的影响；消融实验完整；附录中提供了求解C*的算法细节和计算时间。
- **通用性**：方法支持任意分辨率的矩形图像，且对路径类型不敏感（希尔伯特和Z阶均可），鲁棒性好。

## 8. 不足与局限

- **实验覆盖不足**：仅测试了低分辨率数据集（最高64×64），未在标准ImageNet-1K（224×224）上评估，而高分辨率下局部性问题可能减弱（原文表1显示Psd随分辨率增加），实际性能是否仍保持竞争力未知。
- **模型规模有限**：PathConvS/B对应ResNet-18/50的复杂度，未尝试更大模型（如ResNet-101/152）或更高FLOPs的设置。
- **多路径开销**：虽然仅3条路径，但每条路径需要单独遍历图像，在批处理中可能增加内存带宽压力，文章仅报告了遍历层的加速比，未提供端到端训练/推理速度对比。
- **路径选择依赖求解**：C*的求解需预先运行随机舍入算法，对s=64的希尔伯特路径耗时约2小时（7134秒），虽然只需一次，但在实际应用中对不同尺寸需要重新计算。
- **缺乏与其他高效架构的比较**：未与MobileNet、EfficientNet等顶级轻量级模型对比，仅与ResNet这类标准模型比较，说服力有限。
- **理论上未证明3条路径的全局最优性**：虽然通过随机舍入算法得到|C|=3，且贪心算法有时需要4条，但论文承认可能不是严格最优，且对希尔伯特和Z阶分别给出不同配置，缺乏统一理论支撑。

（完）
