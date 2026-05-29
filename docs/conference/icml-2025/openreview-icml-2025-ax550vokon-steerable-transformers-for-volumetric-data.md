---
title: Steerable Transformers for Volumetric Data
title_zh: 用于体积数据的可操控Transformer
authors: "Soumyabrata Kundu, Risi Kondor"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Ax550Vokon"
tags: ["query:neural-arch"]
score: 7.0
evidence: 针对体积数据的等变Transformer扩展
tldr: 本文提出Steerable Transformers，将Vision Transformer扩展为对SE(d)群等变的架构，通过傅里叶空间非线性操作实现等变注意力，实验表明在2D和3D任务上，添加该层能提升可操控卷积网络的性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ax550vokon/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1306, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ax550vokon/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1006, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ax550vokon/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1130, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ax550vokon/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1078, \"height\": 861, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ax550vokon/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 481, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ax550vokon/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1022, \"height\": 811, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ax550vokon/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1464, \"height\": 924, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ax550vokon/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1277, \"height\": 637, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ax550vokon/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1026, \"height\": 546, \"label\": \"Table\"}]"
motivation: 现有ViT缺乏对旋转平移等变的保证。
method: 提出等变注意力机制，基于可操控卷积特征和傅里叶空间非线性。
result: 在2D和3D任务上提升了可操控卷积网络的性能。
conclusion: 为几何保持的Transformer设计提供了新思路。
---

## Abstract
We introduce Steerable Transformers, an extension of the Vision Transformer mechanism that maintains equivariance to the special Euclidean group $\mathrm{SE}(d)$. We propose an equivariant attention mechanism that operates on features extracted by steerable convolutions. Operating in Fourier space, our network utilizes Fourier space non-linearities. Our experiments in both two and three dimensions show that adding steerable transformer layers to steerable convolutional networks enhances performance.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：现有的 Vision Transformer（ViT）不具备对旋转和平移的等变性，而许多视觉任务（尤其是医学影像、三维体积数据）要求模型对刚性变换具有对称性。虽然可操控卷积（steerable convolutions）能实现 $\mathrm{SE}(d)$ 等变，但其局部感受野限制了捕捉全局依赖的能力。
- **动机**：结合可操控卷积的局部等变能力与 Transformer 的全局注意力机制，设计一种同时保持 $\mathrm{SE}(d)$ 等变性、又能捕获长程关系的混合架构。
- **整体含义**：首次提出针对体积数据（d 维）的等变 Transformer 变体，在傅里叶空间操作，利用群表示理论和相对位置编码实现旋转平移等变性。

## 2. 方法论：核心思想与关键技术细节
- **核心思想**：将可操控卷积的输出特征（已在傅里叶空间按不可约表示/irrep 分解）作为 Transformer 的输入，设计可操控自注意力机制（Steerable Self-Attention），并通过可操控位置编码保证等变性。
- **关键技术细节**：
  - **输入表示**：输入为 $\mathrm{SE}(d)$ 等变的特征图 $f^{\mathrm{in}}(x,\rho) \in \mathbb{C}^{d_\rho \times d_{\text{model}}}$，其中 $\rho$ 为群不可约表示（SO(2) 中用整数 $k$，SO(3) 中用非负整数 $\ell$）。
  - **可操控自注意力**：
    - 查询 $q^{(\rho)}(x) = f^{\mathrm{in}}(x,\rho) W_Q^{(\rho)}$
    - 键 $k^{(\rho)}(x,y) = f^{\mathrm{in}}(x,\rho) W_K^{(\rho)} + P^{(\rho)}(x,y)$
    - 值 $v^{(\rho)}(x,y) = f^{\mathrm{in}}(x,\rho) W_V^{(\rho)} + P^{(\rho)}(x,y)$
    - 位置编码 $P^{(\rho)}$ 满足定理1的等变条件：$P^{(\rho)}(Rx+t, Ry+t) = \rho(R) P^{(\rho)}(x,y)$。具体实现为球谐函数基（2D：$e^{ik\theta}$；3D：球谐函数 $Y^{(\ell)}$）乘以可学习的径向衰减因子 $\phi(r,\rho) = w_\rho r^{-2} \mathbf{1}_{r>0}$。
    - 注意力得分 $s(x,y) = \sum_\rho \text{vec}(q^{(\rho)}(y))^\dagger \text{vec}(k^{(\rho)}(x,y)) / \sqrt{d_K}$，输出 $f^{\text{out}}(x,\rho) = \int \alpha(x,y) v^{(\rho)}(x,y) dy$。
  - **等变非线性**：采用范数ReLU $\sigma(f(x,\rho)) = \text{ReLU}(\|f\|_2 + b) \cdot f / \|f\|_2$，保持等变。
  - **层归一化**：$\text{LN}(f)(x,\rho) = f(x,\rho) / \sqrt{\sum_\rho \|f(x,\rho)\|_2^2}$。
  - **整体架构**：混合架构——可操控卷积编码器 + 可操控 Transformer 块（2个块）+ 分类/分割头。对于分割任务，使用 U-Net 结构，Transformer 置于瓶颈层。

## 3. 实验设计：数据集、Benchmark 与对比方法
- **数据集**：
  - **Rotated MNIST**（2D 分类）：随机旋转的 MNIST，28×28，12000训练/50000测试。
  - **ModelNet10**（3D 分类）：10类 CAD 模型，3991训练/908测试，点云体素化（2048点），包括 z 旋转和 SO(3) 旋转两个变种。
  - **PH2**（2D 分割）：200张皮肤镜图像，分割二值掩膜，100训练/50验证/50测试。
  - **BraTS**（3D 分割）：脑肿瘤 MRI，240×240×155，4模态，分割三种肿瘤区域，243训练/96验证/145测试。
- **Benchmark**：与纯可操控卷积基线（相同编码器，无 Transformer）对比。在 Rotated MNIST 上还与其他等变注意力方法（α-R4 CNN、GSA-Nets、GE-ViT）及等变卷积方法（P4CNN、Harmonic Net、RotEqNet、E2CNN 等）比较。
- **对比方法**：主要对比对象为自身基线（无 Transformer 的 steerable convolution），以及表2/3中的外部方法。

## 4. 资源与算力
- **明确给出的信息**：
  - 所有实验使用单个16GB GPU（型号未说明，可能为 NVIDIA V100 或 RTX 2080 Ti 等）。
  - 训练时间：Rotated MNIST 最大模型4小时；ModelNet10 最大模型12小时；PH2 最大模型2小时；BraTS 最大模型40小时。
  - 批大小：分类任务25（MNIST）、5（ModelNet10）；分割任务1（PH2、BraTS）。
- **未说明**：GPU 具体型号、CPU、内存、是否使用分布式训练等超参数细节（如训练种子数仅5次平均，标准差报告）。

## 5. 实验数量与充分性
- **实验组数**：
  - 2D分类：Rotated MNIST，两种切趾频率（k=4,8），各5次运行。
  - 3D分类：ModelNet10，频率 ℓ=3，两种旋转条件，各5次运行。
  - 2D分割：PH2，两种频率（k=4,8），各5次运行。
  - 3D分割：BraTS，频率 ℓ=2，5次运行。
  - 附录表2/3提供了与外部方法的对比（但外部方法结果引自原论文，未复现）。
- **充分性**：
  - 优点：每个实验5次独立重复，报告均值±标准差，统计可靠。
  - 不足：未做消融实验（如去掉位置编码、不同非线性、不同Transformer层数、不同切趾频率对比等）；未比较其他等变Transformer方法在同一设置下的性能（仅与纯卷积基线对比）；外部对比中，方法、参数量、数据增强策略不同（如ModelNet10对比的方法均使用训练时数据增强，而本文未使用训练增强）。
- **公平性**：基线为相同可操控卷积编码器，仅插入 Transformer 与否，对比公平；但外部对比存在不一致性。

## 6. 主要结论与发现
- **性能提升**：在所有任务上，添加可操控 Transformer 后，性能一致优于纯可操控卷积基线（Rotated MNIST 准确率提升约0.1-0.2%；ModelNet10 提升约0.3-0.7%；PH2 Dice 提升约1.3-1.1%；BraTS 三个肿瘤区域 Dice 提升约1.7-3.8%）。
- **等变验证**：注意力分数可视化显示，不同注意力头捕捉了物体边界或内部，表明学习到有意义的空间模式。
- **复杂度相当**：在典型设置（通道数较大、核大小较小）下，可操控自注意力的复杂度与可操控卷积相当，未引入不成比例开销。

## 7. 优点
- **创新性**：首个针对体积数据的 $\mathrm{SE}(d)$ 等变 Transformer，统一了2D和3D框架。
- **理论严谨**：定理1给出位置编码的充分必要条件，设计基于球谐函数和径向衰减，严格保证等变性。
- **实用价值**：在医学影像（BraTS、PH2）上验证有效，对高精度应用（如肿瘤分割）有潜在价值。
- **实验一致性**：在4个不同数据集、2种任务（分类/分割）、2D/3D上均观察到提升，结论可靠。

## 8. 不足与局限
- **计算资源限制**：论文明确承认受限于GPU内存，未探索更高切趾频率（如 k=16 或 ℓ=4+），导致性能天花板可能未达最优。
- **缺乏消融研究**：未分析各组件贡献（如位置编码设计、非线性选择、Transfomer层数、注意力头数等），难以确定改进来源。
- **外部对比不充分**：与SOTA方法的对比中，数据增强策略、频率设置不一致，且未复现代码验证公平性。
- **可复现性**：代码已公开，但超参数搜索细节不足（如学习率衰减策略、优化器选择理由）。
- **泛化性**：仅测试了旋转/平移等变，未测试其他对称群（如反射、缩放）；模型在无训练增强下与有增强的SOTA相比仍有差距。
- **应用限制**：体积数据的高分辨率导致注意力机制内存消耗大，批大小只能为1，限制了规模扩展。

（完）
