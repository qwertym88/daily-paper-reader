---
title: "Deep Linear Network Training Dynamics from Random Initialization: Data, Width, Depth, and Hyperparameter Transfer"
title_zh: 随机初始化下深度线性网络训练动力学：数据、宽度、深度和超参数迁移
authors: "Blake Bordelon, Cengiz Pehlevan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=SEj9uopOWP"
tags: ["query:neural-arch"]
score: 4.0
evidence: 对残差网络深度的理论分析
tldr: 本文理论刻画了深层线性残差网络在随机初始化和大宽度下的梯度下降动力学。研究表明，将残差分支按1/sqrt(深度)缩放可实现无限深度极限，并揭示超参数迁移效应。该理论同时涵盖非残差和残差网络，为深层网络设计提供了理论指导。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1744, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 647, \"height\": 1112, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1501, \"height\": 1032, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1721, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 649, \"height\": 1105, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1712, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 648, \"height\": 1099, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 793, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1610, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-sej9uopowp/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 882, \"height\": 634, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-sej9uopowp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 158, \"label\": \"Table\"}]"
motivation: 深层线性网络训练动力学的理论理解不足，特别是残差结构的影响。
method: 对残差和非残差线性网络进行渐近分析，推导深度缩放规则。
result: 揭示了1/sqrt(深度)缩放可实现无限深度极限，并解释超参数迁移现象。
conclusion: 为设计可扩展的深层网络提供了理论依据。
---

## Abstract
We theoretically characterize gradient descent dynamics in deep linear networks trained at large width from random initialization and on large quantities of random data. Our theory captures the ``wider is better" effect of mean-field/maximum-update parameterized networks as well as hyperparameter transfer effects, which can be contrasted with the neural-tangent parameterization where optimal learning rates shift with model width. We provide asymptotic descriptions of both non-residual and residual neural networks, the latter of which enables an infinite depth limit when branches are scaled as $1/\sqrt{\text{depth}}$. We also compare training with one-pass stochastic gradient descent to the dynamics when training data are repeated at each iteration. Lastly, we show that this model recovers the accelerated power law training dynamics for power law structured data in the rich regime observed in recent works.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：理解深度网络训练动力学及其缩放特性对于推导能跨模型规模保持稳定动力学的参数化和优化器至关重要，从而通过超参数迁移显著节省计算成本。然而，由于非线性动力学依赖于参数化、初始化、优化器和数据结构，其表征非常复杂。现有理论缺乏能同时捕捉宽度、深度、丰富度（richness）和数据量对随机初始化网络学习动力学影响的统一模型，特别是无法理论刻画成功超参数迁移所需的两点：性能随宽度/深度单调提升，以及适当参数化下最优学习率近似一致。

- **核心问题**：是否存在一个简单的深度网络理论模型，能够捕捉随机初始化、网络参数化、宽度和深度的影响，从而表征超参数迁移效应？

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：作者针对**深度线性网络**（deep linear networks）开发了一种**动态平均场理论（DMFT）**，在随机初始化和大量随机数据的联合大系统极限下（宽度N、数据量P、输入维度D成比例增长），对训练和测试损失的典型轨迹进行封闭形式的刻画。该理论同时适用于全批梯度下降和在线随机梯度下降（SGD），并能处理残差网络结构。

- **关键技术细节**：
  - **模型定义**：网络为前馈线性MLP（含L个隐藏层，每层宽度N），输入x ∈ R^D，输出f(x)为线性变换，采用μP参数化（输出缩放因子γ0）。初始权重服从标准正态分布。目标函数为线性模型加噪声。
  - **动力学方程**：权重更新采用梯度下降（μP缩放），引入误差向量∆(t)和预测误差v(t)等。通过引入层间变量hℓ(t)和gℓ(t)，将动力学表示为关于初始化噪声的随机过程。
  - **DMFT方程**：在D→∞的极限下，系统的统计行为由一组**关联函数**（如C_h^ℓ, C_g^ℓ, C_∆, C_v）和**响应函数**（如R_hr^ℓ, R_gu^ℓ, R_vu, R_∆）的封闭方程决定。这些函数可通过数值积分求解，进而计算任意时刻的训练损失Ŷ(t)和测试损失L(t)。公式如(11)、(13)等。
  - **残差网络扩展**：对残差网络（残差分支缩放因子β），DMFT需要引入跨层关联和响应函数。当β = β₀/√L时，可得到无限深度极限，其中残差流服从含布朗运动的随机微分方程（SDE）(17)。
  - **结构化数据**：对幂律协方差数据（特征值λ_k ~ k^{-α}，目标权重平方乘λ_k ~ k^{-αβ-1}），推导出近似平均场理论，得到每个特征模态的传递函数H_k(t,t')，并分析出训练损失的幂律缩放指数。

### 3. 实验设计：使用的数据集/场景、基准、对比方法

- **数据集/场景**：
  - ** isotropic 随机数据**：输入x ~ N(0, I)，目标y为线性函数加噪声。用于验证DMFT对宽度、深度、参数化、数据量的预测。
  - **在线SGD场景**：每次迭代采样新批数据，比较全批GD与在线SGD的动力学差异。
  - **幂律结构数据**：采用λ_k ~ k^{-α}的协方差矩阵，目标权重按(20)生成，用于分析缩放定律。
- **基准**：论文以**数值模拟（finite-width network training）** 作为基准，将DMFT预测（虚线）与模拟结果（实线）直接对比。
- **对比方法**：
  - **NTK参数化**（γ0 ~ 1/√ν） vs **μP参数化**（γ0 = Θ(1)），展示宽度ν对训练速度和超参数迁移的影响。
  - **深度L的不同缩放**：对比常数β与β = β₀/√L，验证深度迁移效应。
  - **不同批次大小、数据集大小**：展示有限数据/小批次导致过拟合峰值及SGD噪声的影响。

### 4. 资源与算力

论文未明确说明使用的GPU型号、数量或训练时长。作为理论性工作，数值模拟主要用于验证理论预测，规模通常较小（如宽度N=64, 128等，时间步T=几百）。文中提到的计算复杂度对比（表1）指出DMFT求解成本为O(LT²)，远小于直接训练大型网络（O(N²LPT)），但未提及实际硬件资源。

### 5. 实验数量与充分性

- **实验数量**：论文共展示了约7个主图（Fig.1-7）及若干附录图，覆盖以下场景：
  - 不同宽度ν下的NTK和μP测试损失动力学（Fig.1a-b）。
  - 不同深度L的MLP损失（Fig.1c）。
  - 不同学习率η的宽度迁移（Fig.2）。
  - 不同数据集大小α的影响及过拟合峰（Fig.3a-b）。
  - 在线SGD不同批次大小α_B和宽度ν (Fig.3c-d)。
  - 残差网络不同γ₀, β₀, L下训练动力学（Fig.4）。
  - 深度迁移实验中β是否缩放的对比（Fig.5）。
  - 幂律数据下SGD噪声、宽度和任务难度（β>1 vs β<1）的缩放定律（Fig.6）。
  - 幂律特征下NTK vs μP的学习率迁移（Fig.7）。
- **充分性**：实验设计比较全面，系统验证了理论对不同参数化、宽度、深度、数据量、批次大小、数据结构的预测能力。所有模拟与DMFT预测高度吻合，说明理论是准确且充分的。
- **客观与公平**：直接对比理论预测与数值模拟，无主观调整；方法上未涉及与其他竞争方法的比较（因为本文主要是理论工作），但理论自身的一致性验证是客观的。

### 6. 论文的主要结论与发现

1. **DMFT提供了深度线性网络的精确封闭描述**，能同时捕捉宽度、深度、数据量、参数化对训练动力学的影响。
2. **μP参数化实现超参数迁移**：最优学习率在不同宽度下近似保持不变（Fig.2b），而NTK参数化下最优学习率随宽度右移（Fig.2a）。
3. **残差网络需要β ∝ 1/√L缩放才能得到稳定的无限深度极限**，此时超参数（学习率）可跨深度迁移（Fig.5b）；否则随着深度增加，最优学习率变化几个数量级（Fig.5a）。
4. **在线SGD的训练损失单调改善**，而全批GD中重复使用有限数据会导致过拟合峰（Fig.3）。
5. **在幂律数据上，深层线性网络的特征学习（rich regime）能够加速硬任务（β<1）的缩放定律**：从懒学习（lazy）的L(t) ~ t^{-β}提升至L(t) ~ t^{-2β/(1+β)}（Fig.6c, Fig.10），且该加速指数与层数L无关（至少对于深度线性网络）。
6. **有限宽度和有限数据带来的方差项**（如式(13)中的最后两项）会导致学习曲线偏离无限极限。

### 7. 优点

- **理论完整性**：第一次在可处理的理论框架内同时考虑了宽度、深度、数据量、参数化、随机初始化、SGD噪声等多种因素对训练动力学的影响。
- **可计算性**：DMFT方程复杂度为O(LT²)，远小于直接仿真大型网络（O(N²LPT)），提供了高效的理论计算工具。
- **对超参数迁移的解释**：清晰区分了NTK和μP参数化下学习率迁移行为的差异，并推广到深度（残差分支缩放）。
- **对缩放定律的洞察**：揭示了深层线性网络在硬任务上的加速幂律缩放，且指出这一效应与深度无关（至少在模型内如此）。
- **方法普适性**：框架可扩展至非等宽隐藏层（附录F）、多输出（附录G）和结构化数据（附录E）。

### 8. 不足与局限

- **模型局限**：只分析了深度线性网络，缺乏非线性激活函数。许多非线性效应（如表示学习、特征融合）可能无法被捕捉，因此结论向非线性网络的推广需谨慎。
- **计算成本**：DMFT求解器虽然比直接训练大网络高效，但对于非常深的网络（L>>1）和长时间步（T>>1），其O(LT²)复杂度仍然较高（表1）。残差网络因需要O(L²)响应函数，成本更高。
- **离散时间效应**：论文在分析幂律缩放时使用了连续时间梯度流，但离散梯度下降可能引入边缘稳定性（Edge of Stability）效应，改变长时间行为，文中指出这需要进一步分析。
- **实验覆盖有限**：数值模拟限于较短的训练步数（T~200）和中等网络规模（N≤1024），没有验证极大规模或超长训练时间下的理论准确性。此外，所有模拟基于合成数据，未在真实图像/文本数据集上测试。
- **优化器扩展**：只考虑了（S）GD，未涉及Adam、动量等更常用优化器的动力学。
- **缺乏与非线性网络经验的对比**：虽提到相关工作，但未直接展示理论预测与真实非线性网络训练行为的对比（如GPT-4等），因此实际应用价值尚需验证。

（完）
