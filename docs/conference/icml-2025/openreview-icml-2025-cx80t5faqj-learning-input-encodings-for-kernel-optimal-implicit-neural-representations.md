---
title: Learning Input Encodings for Kernel-Optimal Implicit Neural Representations
title_zh: 学习核最优隐式神经表示的输入编码
authors: "Zhemin Li, Liyuan Ma, Hongxia Wang, Yaoyun Zeng, Xiaolong Han"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Cx80t5FAQJ"
tags: ["query:neural-arch"]
score: 7.0
evidence: 基于核对齐的隐式神经表示架构设计理论
tldr: 本文通过核对齐理论分析隐式神经表示（INR）的泛化性能。提出了最优核的概念，并证明通过调整输入特征映射，INR的神经切线核可逼近任意点积核。基于此提出核对齐正则化器（KAR），自然融入INR训练，提升了图像表示等任务的重建质量。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 720, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 735, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1418, \"height\": 879, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1391, \"height\": 849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 833, \"height\": 749, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 748, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 748, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 853, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1025, \"height\": 616, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-cx80t5faqj/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 854, \"height\": 507, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-cx80t5faqj/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 773, \"height\": 721, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cx80t5faqj/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 772, \"height\": 714, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-cx80t5faqj/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 744, \"height\": 720, \"label\": \"Table\"}]"
motivation: INR的泛化性能高度依赖架构选择，缺乏理论指导。
method: 通过无限宽极限理论分析，提出核对齐正则化器（KAR）来优化输入编码。
result: 在图像表示等任务上，KAR提升了INR的重建质量和泛化能力。
conclusion: 为INR的架构设计提供了理论支撑，并提出有效正则化方法。
---

## Abstract
Implicit Neural Representations (INRs) rely heavily on architectural choices for good generalization. Developing theoretically grounded approaches for architecture design remains an active area of research. Via theoretical analysis of the infinite-width limit, we establish a methodology that characterizes INR's generalization by means of kernel alignment. We first formulate the optimal kernel that minimizes pointwise expected squared error, then demonstrate that the Neural Tangent Kernel of the composed function (INR with input encoding) can approximate any positive semidefinite dot-product kernels through input feature mapping adjustments. Building upon these insights, we propose a Kernel Alignment Regularizer (KAR) that naturally integrates with existing INR systems to enhance kernel alignment. We further develop Plug-in Encoding for Aligned Kernels (PEAK) to refine INR models with KAR using learnable input encoding. This work contributes to the ongoing research efforts in bridging theory and practice for principled INR architecture design. Code is available at https://github.com/lizhemin15/KAR.

---

## 论文详细总结（自动生成）

## 论文中文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

隐式神经表示（Implicit Neural Representation, INR）通过神经网络将低维坐标映射到输出值，在连续信号建模中展现出强大潜力，但其泛化性能高度依赖架构选择（激活函数、网络结构、输入编码等）。当前缺乏理论指导的架构设计方法。本文旨在通过无限宽极限下的神经切线核（Neural Tangent Kernel, NTK）理论，建立INR泛化性能与核对齐之间的桥梁，从而提出理论驱动的架构优化策略。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：在无限宽极限下，INR的训练动力学等价于核回归，其泛化误差可通过点态期望平方误差衡量。论文先形式化了最小化该误差的**最优核** \(K^*\)，并证明通过调整输入特征映射，INR的NTK可以逼近任意正半定点积核。据此提出**核对齐正则化器（Kernel Alignment Regularizer, KAR）**，引导INR的核与最优核对齐；进一步设计**可插拔核对齐编码（PEAK）**，结合可学习输入编码与KAR实现自适应对齐。
- **关键技术细节**：
  - **最优核公式**：\(K^*(x,x') = \mathbb{E}_{f^*\sim\mu_{f|D}}[f^*(x)f^*(x')]\)，其中\(\mu_{f|D}\)是给定训练数据后的目标函数后验分布。
  - **定理3.3**：对任意连续点积核\(K^*\)，存在编码器\(\gamma\)使得INR的NTK\(K_\gamma\)可以任意逼近\(K^*\)。构造采用幂级数展开及张量积。
  - **KAR正则项**：使INR输出满足\(f_\theta(\gamma(x)) \approx \sum_i A(x,x_i) f_\theta(\gamma(x_i))\)，其中\(A\)是软最大参数化的相似度函数。
  - **PEAK算法**：联合优化INR参数\(\theta\)、多项式编码系数\(\{a_j\}\)、注意力网络参数\(\theta'\)，损失函数为数据保真项 + λ * KAR（在网格上离散化）。
- **算法流程（文字说明）**：初始化INR、注意力网络、多项式系数；循环T轮：计算总损失\(L_{all}\)（包含数据项和KAR项），对\(\theta, \theta', a_j\)分别进行梯度下降；返回优化后的INR。

### 3. 实验设计

- **数据集/场景**：
  - **1D信号拟合**：验证核对齐性质。
  - **图像重建（线性逆问题）**：6张标准测试图像（Baboon, Boat, Cameraman, Jetplane, Lake, Livingroom）；三种缺失模式：Random（50%随机缺失）、Patch（结构化缺失）、Textural（纹理复杂缺失）。
  - **相位恢复（非线性逆问题）**：Fourier相位恢复（FPR）和Gaussian相位恢复（GPR）；使用House, Boston, Boat图像；采样比s取1.9,1.8,1.7（FPR）和1.0,0.9,0.8（GPR）。
  - **神经辐射场（NeRF）**：NeRF合成数据集（chair, hotdog, lego, drums, ficus, mic）；视图数25/50/100。
- **基准方法**：
  - Vanilla MLP（ReLU激活）、Fourier特征网络、Hash编码（Instant-NGP）。
  - 相位恢复中与Net-GD和Net-ADM结合，替换原始深度解码器。
- **指标**：PSNR（dB）。

### 4. 资源与算力

论文正文及附录均**未明确说明**使用的GPU型号、数量、训练时长等算力信息。仅在实验中提及“训练时间”对比图（Figure 7），显示PEAK收敛速度较快，但未提供具体硬件配置。

### 5. 实验数量与充分性

- **实验数量**：涵盖**三类任务**（线性/非线性逆问题、NeRF）、多数据集（6种图像+6种NeRF物体）、多基线方法，并包含**三组消融实验**：多项式阶数、正则化系数λ、注意力网络输出维度r、激活函数选择。
- **充分性**：
  - **正面**：任务覆盖面较广，从简单1D到复杂3D场景；消融实验探索关键超参数；结果统计了均值/最值（如Figure 3、Figure 9），显示稳定性。
  - **不足**：缺少在更大规模数据（如高分辨率图像、真实场景NeRF）上的验证；仅使用PSNR单一指标；未与更多先近INR架构（如SIREN、WIRE、BACON）对比；相位恢复实验场景较简单（图像尺寸未被提及）。

### 6. 论文的主要结论与发现

- 通过理论证明了INR的NTK可以通过可学习输入编码逼近任意点积核，从而实现了理论指导的架构设计。
- 提出的KAR正则项能有效促进INR核与最优核对齐，提升泛化能力。
- PEAK在图像重建（最高提升约13dB）、相位恢复（最高提升约12dB）和NeRF稀疏视图任务上均显著优于MLP、Fourier和Hash等基线方法。
- 多项式阶数Nγ=1即可取得良好效果，兼顾性能与复杂度；正则化系数λ在10^{-2}~10^{-1}最优；注意力网络输出维度r=100最佳。
- 消融实验显示激活函数选择对性能影响不大（23-24dB），鲁棒性强。

### 7. 优点

- **理论驱动**：从无限宽NTK理论出发，严格推导最优核及可逼近性，使方法具有坚实数学基础。
- **可插拔性**：PEAK作为插件可无缝集成到任意现有INR系统，无需修改骨干网络结构或初始化。
- **高效性**：仅需额外少量参数（多项式系数+注意力网络），训练速度快于Hash等方法，参数效率高（Figure 7-8）。
- **广泛适用**：在线性和非线性逆问题、NeRF等多种任务上均验证有效。

### 8. 不足与局限

- **理论假设限制**：无限宽极限在实际有限宽网络中仅为近似；最优核构造依赖对后验分布μ_f的离散近似，可能引入偏差。
- **计算复杂性**：KAR项需要在网格点采样计算，网格密度影响效果与效率，未探讨自适应采样。
- **实验覆盖**：缺乏在高分辨率/高维（如3D体积渲染）上的测试；未与近期先进INR（如SIREN、Multiplicative Filter Networks、WIRE）进行彻底对比；缺少真实世界NeRF场景（如NeRF-W）验证。
- **消融深度**：未系统分析注意力网络结构（如层数、宽度）的影响。
- **算法收敛性**：未分析PEAK训练的理论收敛保证，仅依赖实验观测。
- **代码可复现性**：虽开源，但未在附录提供完整超参数设置（如学习率调度、训练轮数、网格尺寸等），可能影响复现。

（完）
