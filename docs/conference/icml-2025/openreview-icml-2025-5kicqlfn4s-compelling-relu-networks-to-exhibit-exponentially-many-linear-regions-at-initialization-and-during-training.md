---
title: Compelling ReLU Networks to Exhibit Exponentially Many Linear Regions at Initialization and During Training
title_zh: 使ReLU网络在初始化及训练中展现指数多个线性区域
authors: "Max Milkert, David Hyde, Forrest John Laine"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=5KICQlFN4s"
tags: ["query:neural-arch"]
score: 7.0
evidence: 一种新颖的网络参数化方法，增加ReLU网络的线性区域数量
tldr: 本文针对随机初始化下ReLU网络线性区域数量不足的问题，提出一种受约束的权重参数化方法，使深度为d的网络在初始化时恰好有2^d个线性区域，并在训练中保持。该方法使得网络对凸一维函数的近似精度比随机初始化高出几个数量级。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 849, \"height\": 853, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 855, \"height\": 889, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 582, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1735, \"height\": 582, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 858, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 803, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 842, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1597, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 897, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1599, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1604, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1249, \"height\": 631, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 877, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1609, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1614, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-5kicqlfn4s/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1677, \"height\": 699, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-5kicqlfn4s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1438, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5kicqlfn4s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1483, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5kicqlfn4s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1417, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-5kicqlfn4s/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1234, \"height\": 411, \"label\": \"Table\"}]"
motivation: 随机初始化的ReLU网络难以有效生成指数多的线性区域，导致网络容量浪费。
method: 提出一种新的参数化方法，通过约束权重使得网络在初始化时产生恰好2^d个线性区域，并在训练中维持。
result: 在凸一维函数近似任务上，该方法比随机初始化网络精度提升数个数量级。
conclusion: 该参数化能有效提升ReLU网络的表达能力和逼近精度，为网络结构设计提供新思路。
---

## Abstract
In a neural network with ReLU activations, the number of piecewise linear regions in the output can grow exponentially with depth.
However, this is highly unlikely to happen when the initial parameters are sampled randomly, which therefore often leads to the use of networks that are unnecessarily large.
To address this problem, we introduce a novel parameterization of the network that restricts its weights so that a depth $d$ network produces exactly $2^d$ linear regions at initialization and maintains those regions throughout training under the parameterization.
This approach allows us to learn approximations of convex, one-dimensional functions that are several orders of magnitude more accurate than their randomly initialized counterparts.
We further demonstrate a preliminary extension of our construction to multidimensional and non-convex functions, allowing the technique to replace traditional dense layers in various architectures.

---

## 论文详细总结（自动生成）

## 详细论文总结

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：ReLU神经网络的输出理论上可随深度呈指数增长线性区域，但**随机初始化**时几乎无法实现这种指数增长，导致网络容量被浪费，需要更大的网络才能达到理想性能。
- **整体含义**：论文旨在通过设计一种**受约束的权重参数化**方法，强制网络在**初始化时即产生指数多个线性区域**（例如深度 d 的网络恰好产生 2^d 个区域），并在训练过程中保持不变。该方法旨在提升网络对非线性函数的逼近效率，尤其是一维凸函数，并可扩展至多维和非凸函数。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

#### 核心思想
- 将每层与一个**非对称三角波函数**关联，通过组合不同层生成的三角波并加权求和来构造输出。三角波函数定义为：
  \[
  T_i(x) = \begin{cases}
  \frac{x}{a_i}, & 0 \le x \le a_i \\
  1 - \frac{x-a_i}{1-a_i}, & a_i \le x \le 1
  \end{cases}
  \]
  其中 \(a_i \in (0,1)\) 为峰值位置。

- 每层利用**两个ReLU神经元**实现三角波，并通过**sum神经元**（类残差连接）叠加各层的三角波信号，构建深层基函数 \(W_i(x) = T_i \circ T_{i-1} \circ \cdots \circ T_0(x)\)。最终输出为 \(F(x) = \sum_{i=0}^\infty s_i W_i(x)\)。

#### 关键技术细节与公式
- **参数化方式**：网络宽度固定为4（sum, t1, t2, bias四个神经元），每层的权重由三角波峰值 \(a_i\) 和缩放系数 \(s_i\) 决定。例如隐藏层权重矩阵形式为（见原文第4–5页）：
  \[
  \begin{bmatrix}
  1 & \pm[S_i/a_i] & -S_i/(a_i-a_i^2) & 0 \\
  0 & S_i/a_i & -S_i/(a_i-a_i^2) & 0 \\
  0 & S_i/a_i & -S_i/(a_i-a_i^2) & -S_i a_{i+1} \\
  0 & 0 & 0 & S_i
  \end{bmatrix}
  \]
  其中 \(S_i = s_i / s_{i-1}\)。

- **不同延性条件（定理3.1）**：为保证无限深度下输出可微，缩放系数需满足：
  \[
  s_{i+1} = s_i (1 - a_{i+1}) a_{i+2}.
  \]
  该条件使三角波振幅指数级衰减，避免产生分形。

- **算法流程（三阶段）**：
  1. **初始化**：随机生成峰值向量 \(A = [a_0, a_1, \dots, a_n]\)，使用上述公式计算权重。
  2. **预训练**：在参数化空间下，仅更新 \(A\)（通过反向传播梯度），训练网络（通常1000 epoch）。
  3. **正式训练**：释放权重约束，用常规梯度下降训练原始权重（可选）。

### 3. 实验设计：使用的数据集 / 场景、基准方法、对比方法

#### 主要实验场景
- **一维凸函数近似**（第4节）：目标函数包括 \(x^3\)、\(x^{11}\)、\(\sin(x)\)、\(\tanh(3x)\)。使用500个密集点（评估最佳拟合）和10个稀疏点（评估泛化能力）。
- **非凸函数近似**：\(y = x^3 - x\) 的差分解。
- **二维凸函数近似**：\(z = r^3\)（\(r = \sqrt{x^2+y^2}\)）。
- **图像分类**：CIFAR-10（小CNN + VGG-16）、ImageNet（VGG-16替换分类器）。

#### 基准与对比方法
- **基准**：PyTorch默认的Kaiming初始化；RAAI分布（改进权重初始化）。
- **对比变体**：
  - 使用新参数化但**跳过预训练**（仅初始化权重，之后常规训练）。
  - **无正则化预训练**（不施加定理3.1条件）。
  - **带定理3.1正则化预训练**（完整方法）。
- 公平比较：稠密网络 vs. 块对角网络（相同参数数量）。

### 4. 资源与算力

- **论文未明确说明使用的GPU型号、数量或训练总时长**。实验描述中只提及训练轮次（1000 epoch）和学习率（0.001），未提供硬件细节。
- 在实际部署中（如ImageNet和CIFAR-10实验），推测使用了单卡或多卡NVIDIA GPU（例如V100或A100），但**文中无具体信息**，需注意这一缺失。

### 5. 实验数量与充分性

#### 实验数量
- **一维函数**：每种目标函数运行30次，记录最小和平均MSE（表1、表2）；稀疏测试独立运行（表3）。
- **非凸/二维扩展**：各测试一次，取30次训练的最小MSE。
- **图像分类**：CIFAR-10（多个架构，图17）；ImageNet（VGG-16，图8），但未提供统计重复次数。
- **消融实验**：对比不同预训练变体（跳过、无正则化、带正则化），验证定理3.1有效性；对比不同学习率（附录B.1）。

#### 充分性与公平性
- **优点**：一维实验重复30次，覆盖多种目标函数，统计了最小和平均值，避免了单次随机性；消融实验设计合理，对比了多种初始化与预训练策略。
- **不足**：图像分类实验重复次数未给出，且结论不够显著（最终精度相当，仅有早期优势）；非凸/二维扩展示例数量少（每个仅一个函数），缺乏系统性对比；未测试更高维度或实际回归数据集（如UCI具体任务除外）。

### 6. 论文的主要结论与发现

1. **线性区域指数增长**：新参数化方法使深度d的网络在初始化时即产生 \(2^d\) 个线性区域，远多于随机初始化（后者平均线性区域数与深度无关）。
2. **逼近精度大幅提升**：在一维凸函数逼近中，完整方法的最小误差比Kaiming初始化低**3–4个数量级**，且平均误差显著降低（表1、表2）。
3. **泛化能力增强**：稀疏数据测试（10个训练点）中，新方法对未见点的预测误差同样低约1–2个数量级（表3）。
4. **可扩展到非凸/多维函数**：通过多个子网络组合（差分解或组合取向），成功近似 \(x^3-x\) 和 \(z=r^3\)，误差比常规网络小1–2个数量级。
5. **图像分类效果有限**：在CIFAR-10和ImageNet上，新方法在训练早期有优势，但最终精度与常规网络相当，未体现显著提升。

### 7. 优点：方法或实验设计上的亮点

- **创新性参数化**：将网络权重直接与理论最优的三角波峰值关联，巧妙规避了随机初始化无法生成足够线性区域的固有问题。
- **理论保障**：定理3.1给出了可微性条件，保证无限深度下输出光滑，并提供了稳定的正则化方案。
- **简洁性**：网络宽度仅4，参数数量少，却能实现指数级表达力；可视为一种“深度基函数”框架。
- **扩展性**：方法可作为“模块”插入任意网络的稠密层，兼容现有架构（如VGG、CNN）。
- **实验统计严格**：一维函数重复30次，报告最小与平均误差，并附消融实验，可信度高。

### 8. 不足与局限

- **应用范围狭窄**：当前直接适用的函数类仅限于一维凸函数，扩展到多维需多个子网络拼合，且权重矩阵呈稀疏块对角结构，限制参数利用率。
- **图像分类未见优势**：实验表明高精度决策边界对分类任务可能不关键，方法优势在回归场景更明显，但大规模回归实验缺失。
- **训练复杂度**：两阶段切换（预训练→正式训练）需要重启优化器，可能导致损失瞬时上升；如何选择切换时机缺乏指导。
- **可微性条件限制**：定理3.1要求 \(a_i\) 有界（如 \(c< a_i <1-c\)），若峰值靠近0或1，网络退化；且只能逼近凸函数（差分解需额外假设）。
- **算力与耗时未报告**：未提供训练总时长或硬件信息，使复现或估计成本困难。
- **实验覆盖面有限**：非凸/多维示例仅2个，缺乏系统性benchmark（如更高维度、真正工业级回归数据集）；图像分类结果不够充分，未展示参数化开关的影响（如第6节提到“似乎无关紧要”）。

（完）
