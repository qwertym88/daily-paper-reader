---
title: Approximation theory for 1-Lipschitz ResNets
title_zh: 1-Lipschitz残差网络的逼近理论
authors: "Davide Murari, Takashi Furuya, Carola-Bibiane Schönlieb"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rsTWR7z4PB"
tags: ["query:neural-arch"]
score: 4.0
evidence: 1-Lipschitz残差网络的近似理论
tldr: 本文研究1-Lipschitz残差网络的逼近能力，利用限制Stone-Weierstrass定理证明该类网络在紧致域上可稠密逼近标量Lipschitz函数，并能精确表示分段仿射函数。当插入范数约束线性映射后，固定宽度也可保持稠密性。该理论为鲁棒分类器等应用提供了支撑。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rstwr7z4pb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1114, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rstwr7z4pb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1118, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rstwr7z4pb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 765, \"height\": 238, \"label\": \"Table\"}]"
motivation: 1-Lipschitz网络在生成建模、逆问题和鲁棒分类中重要，但ResNet的逼近能力缺乏系统理论。
method: 利用限制Stone-Weierstrass定理，分析1-Lipschitz ResNet的密度和精确表示。
result: 证明可在宽度和深度增长时稠密逼近，以及固定宽度下通过添加线性映射保持稠密性。
conclusion: 为1-Lipschitz ResNet的设计提供了理论依据。
---

## Abstract
$1$-Lipschitz neural networks are fundamental for generative modelling, inverse problems, and robust classifiers. In this paper, we focus on $1$-Lipschitz residual networks (ResNets) based on explicit Euler steps of negative gradient flows and study their approximation capabilities. Leveraging the Restricted Stone–Weierstrass Theorem, we first show that these $1$-Lipschitz ResNets are dense in the set of scalar $1$-Lipschitz functions on any compact domain when width and depth are allowed to grow. We also show that these networks can exactly represent scalar piecewise affine $1$-Lipschitz functions. We then prove a stronger statement: by inserting norm-constrained linear maps between the residual blocks, the same density holds when the hidden width is fixed. Because every layer obeys simple norm constraints, the resulting models can be trained with off-the-shelf optimisers. This paper provides the first universal approximation guarantees for $1$-Lipschitz ResNets, laying a rigorous foundation for their practical use.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：1-Lipschitz 神经网络在水生成对抗网络（WGAN）、逆问题（如 Plug-and-Play）、以及对抗鲁棒分类中具有重要应用。然而，现有约束网络（如谱归一化、正交权重）会显著降低表达力，且缺乏对 1-Lipschitz 残差网络（ResNet）通用逼近能力的理论保证。  
- **核心问题**：能否在保持 1-Lipschitz 约束的前提下，使 ResNet 架构能够稠密逼近任意标量 1-Lipschitz 函数？如果宽度固定，是否仍能实现？  
- **整体含义**：本文首次为 1-Lipschitz ResNet 提供了严格的通用逼近定理，为设计可训练的、具有理论保障的鲁棒网络奠定了基础。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用受限 Stone–Weierstrass 定理（Restricted Stone–Weierstrass Theorem），证明特定结构的 1-Lipschitz ResNet 构成一个格（lattice）且能分离点，从而具有稠密性。  
- **关键技术细节**：
  1. **基础模块**：残差层定义为显式欧拉步：  
     `Φ_θ(x) = x - τ W^T σ(W x + b)`，其中 `σ = ReLU`，`||W||_2 ≤ 1`，`τ ∈ [0,2]`。该层是 1-Lipschitz 的（Proposition 2.1）。  
  2. **第一类网络（G₍d,σ₎）**：由未约束的仿射升维层 Q、多个残差层和一个范数为1的投影向量 v 组成。允许宽度和深度自由增长，证明其在紧致域上稠密于 C¹（X,R）（Theorem 3.1）。  
  3. **第二类网络（Ĝ₍d,σ,h₎）**：在残差块之间插入范数约束的线性映射（块对角、行和为1），且将残差层限制为 `Ẽ₍h,σ₎`（前三个分量执行 max/min 操作）。固定宽度 `h = d+3` 下仍保持稠密性（Theorem 4.1）。  
  4. **构造性证明**：展示两种网络都能精确表示任意 1-Lipschitz 分段仿射函数（Theorem 3.2 和 Theorem 4.2），从而继承该函数类的逼近性质。

### 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集与场景**：
  - **Two-moon 数据集**（含高斯噪声 σ=0.1）：4000 个点，20% 训练，用于二分类。
  - **MNIST 数据集**：标准训练/测试划分，预处理归一化，用于十分类。
- **Benchmark**：论文未设置外部基准方法对比，主要验证自身架构的可行性和训练稳定性。
- **对比方法**：仅对比论文中提出的两类网络（来自 Theorem 3.1 的无仿射层网络 vs. Theorem 4.1 的含仿射层网络）在不同深度和宽度下的测试准确率和约束归一化耗时。

### 4. 资源与算力

- **GPU 型号**：Quadro RTX 6000。
- **训练细节**：
  - 优化器：Adam，余弦退火学习率调度。
  - 批大小：256。
  - 约束归一化：使用幂迭代法（初始多次迭代，之后每步一次）。
- **未明确说明**：总训练轮数、每轮时间、功耗等细节未提供。

### 5. 实验数量与充分性

- **实验数量**：
  - Two-moon：两组实验（固定宽度变化深度 L=2,4,8,16,32,64；固定深度 L=10 变化宽度 h=10,20,30,40），各 6 个配置。
  - MNIST：仅 Theorem 4.1 网络，深度 L=5,10,20 与宽度 h=50,100,200 组合，共 9 个配置。
- **充分性评价**：
  - 实验仅验证训练可行性和测试准确率，缺乏与现有 1-Lipschitz 网络（如 GroupSort 网络、谱归一化 MLP）的公平对比。
  - 未提供误差棒（注：论文明确声明“No” for statistical significance），也未对多轮重复取均值。
  - 实验场景简单（低维 Two-moon 和标准 MNIST），不足以全面论证架构在实际复杂任务中的优势。
  - 总体实验数量偏少，且偏重展示性而非系统性评测。

### 6. 论文的主要结论与发现

1. **稠密逼近性**：1-Lipschitz ResNet（基于负梯度流欧拉步）在宽度和深度允许增长时，可稠密逼近任意标量 1-Lipschitz 函数（Theorem 3.1）。
2. **精确表示**：该类网络可以精确表示所有标量 1-Lipschitz 分段仿射函数（Theorem 3.2）。
3. **固定宽度下的稠密性**：通过在残差块间插入范数约束的线性映射，并调整残差块结构（Ẽ₍h,σ₎），可保持稠密性，网络宽度固定为 d+3（Theorem 4.1）。
4. **参数化简洁**：所有层满足简单的范数约束，可用标准优化器训练。
5. **向量值扩展**：结果可推广至向量值 1-Lipschitz 函数（Lemma 5.1），但需放弃内嵌的 Lipschitz 保证。

### 7. 优点：方法或实验设计上的亮点

- **理论贡献突出**：首次系统建立 1-Lipschitz ResNet 的通用逼近定理，弥补了该领域重要空白。
- **证明手法多样**：同时使用受限 Stone–Weierstrass 定理和构造性证明（分段仿射函数表示），两种视角互补。
- **架构可实用**：提出的第二种网络（Theorem 4.1）具有固定宽度和显式约束，可直接投入训练，具备实际部署潜力。
- **扩展性强**：讨论了对其他激活函数、更一般残差层集合的推广思路，并为未来研究指明方向（如去除中间线性层、与正梯度步结合等）。
- **开源代码**：提供了 PyTorch 实现，有利于复现。

### 8. 不足与局限

- **实验覆盖不足**：仅有两类简单分类任务，缺乏与现有 1-Lipschitz 方法（如 GroupSort、Cayley 正交卷积等）的公平 benchmark 对比；未提供误差棒或显著性分析。
- **训练细节不完整**：未说明学习率、epoch 数、超参调优过程，影响可复现性。
- **应用限制**：
  - 理论主要针对标量输出（c=1），向量值扩展会失去 Lipschitz 保证（Lemma 5.1 中的 G₍c,d,σ₎ 不保证是 1-Lipschitz）。
  - 激活函数仅限 ReLU，虽可推广至其他正齐次函数，但实际实现可能复杂。
  - 固定宽度架构**要求输入维度 d+3**，对高维输入（如图像）宽度会很大，但文中未讨论计算效率。
- **缺乏泛化误差分析**：仅关注逼近能力（表达力），未分析在有限样本下的泛化性能与训练复杂度。

（完）
