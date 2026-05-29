---
title: Transformative or Conservative? Conservation laws for ResNets and Transformers
title_zh: 变革还是保守？ResNet和Transformer的守恒定律
authors: "Sibylle Marcotte, Rémi Gribonval, Gabriel Peyré"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=aTBwCSkPxv"
tags: ["query:neural-arch"]
score: 6.0
evidence: 残差块和跳跃连接的守恒定律分析
tldr: 本文研究ResNet和Transformer中梯度流训练的守恒定律，发现残差块与无跳跃连接块具有相同的守恒律，并完整刻画了单注意力层的所有守恒律。理论结果揭示了跳跃连接对训练动力学的影响，为理解残差架构提供了新见解。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-atbwcskpxv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 834, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-atbwcskpxv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 675, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-atbwcskpxv/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 786, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-atbwcskpxv/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 1047, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-atbwcskpxv/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1241, \"height\": 1413, \"label\": \"Figure\"}]"
motivation: 深层架构的守恒定律尚未被充分研究，本文旨在探索ResNet和Transformer中梯度流的守恒特性。
method: 通过理论推导，系统分析ReLU/线性网络、注意力层及残差块的守恒定律，并提出部分参数守恒概念。
result: 证明残差块不改变原有守恒律，并完整描述了注意力层的守恒律。
conclusion: 加深了对流行架构训练动力学的理解，为设计新架构提供了理论指导。
---

## Abstract
While conservation laws in gradient flow training dynamics are well understood for (mostly shallow) ReLU and linear networks, their study remains largely unexplored for more practical architectures. For this, we first show that basic building blocks such as ReLU (or linear) shallow networks, with or without convolution, have easily expressed conservation laws, and no more than the known ones. In the case of a single attention layer, we also completely describe all conservation laws, and we show that residual blocks have the same conservation laws as the same block without a skip connection. We then introduce the notion of conservation laws that depend only on *a subset* of parameters (corresponding e.g. to a pair of consecutive layers, to a residual block, or to an attention layer). We demonstrate that the characterization of such laws can be reduced to the analysis of the corresponding building block in isolation. Finally, we examine how these newly discovered conservation principles, initially established in the continuous gradient flow regime, persist under discrete optimization dynamics, particularly in the context of Stochastic Gradient Descent (SGD).

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- 论文聚焦于深度学习领域一个基本但未充分探索的问题：在梯度流（Gradient Flow）训练动力学中，**现代深层神经网络架构（尤其是带有跳跃连接（skip connections）的 ResNet 和 Transformer）是否具有守恒定律（conservation laws）**。
- 此前，守恒定律主要被用于分析浅层 ReLU 和线性网络，揭示了训练过程中参数间隐含的平衡条件（balancedness conditions），这类分析有助于理解算法的隐式偏置（implicit bias）并用于设计加速收敛的优化方案。
- 然而，对于更复杂的架构（如残差网络、多头注意力机制），守恒定律的存在性、形式和完整性始终未知。本文旨在填补这一空缺，系统性推导并分析 ResNet 和 Transformer 中梯度流下的守恒定律，并检验其在离散 SGD 优化下的近似保持情况。

### 2. 论文提出的方法论：核心思想、关键技术细节

**核心思想**：
- 利用微分几何中的 **Lie 代数** 工具，将守恒定律的刻画转化为对梯度流向量场张成的 Lie 代数轨迹维度的分析。
- 引入 **部分参数守恒** 的概念，将深度网络的全局守恒律分解为对单个构件（如一个残差块、一个注意力层）的孤立分析，从而大幅简化问题。

**关键技术细节**：
- 首先建立结构定理（Theorem 2.1）：说明带权重衰减的梯度流守恒律与无权重衰减的情况之间存在一个简单变换（通过指数重缩放），因此后续可只分析无权重衰减的情形。
- 利用 **Frobenius 定理** 与 Lie 括号性质（Proposition 2.9），给出守恒律的等价条件：函数梯度必须正交于由损失梯度生成的向量空间及其 Lie 括号生成的子空间。
- 对 **浅层** 构件：
    - 证明残差块与无跳跃连接的块具有**相同**的守恒律（Proposition 3.2）。
    - 完整刻画了单通道/多通道卷积 ReLU 网络的守恒律（Theorem 3.6），给出 c₁ 个独立守恒量：\( h_j = \sum_k \|u_{k,j}\|^2 - \sum_i \|v_{j,i}\|^2 \)。
    - 对单头注意力层，证明其全部守恒律等价于 \( QQ^\top - KK^\top \) 和 \( VV^\top - OO^\top \) 的函数（Corollary 3.9）。对多头情况（Corollary 3.10）给出了至少这些守恒量，但未证明完备性。
    - 对交叉熵分类层（softmax），给出 m 个独立守恒律：\( h_j(\theta) = \sum_i \theta_{i,j} \)（Proposition 3.11）。
- 对 **深层网络**（残差网络、Transformer）：
    - 提出 **“局部参数守恒”** 概念（Proposition 4.3），通过定义 \( R_{\theta_T}(W^{g,\ell}) \) 空间，将全局守恒律中仅依赖某个子块（如第 l 个残差块）的条件转化为该子块自身的守恒律。
    - 证明：对于自然残差块，全局网络守恒律中仅依赖于该块参数的部分，**恰好等于**该块孤立时的守恒律（Theorem 4.6）。
    - 对跨越残差连接的连续两层参数（如 \( V^{l+1}, U^l \)），证明不存在非平凡的局部守恒律（Theorem 4.7）。
- 最后，在离散 SGD 下（Proposition 5.1），证明守恒误差以 O(步长²) 控制，并受梯度方差影响。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- 实验部分相对简洁，主要用作理论结果的数值验证，而非追求 SOTA 性能。
- **ResNet 实验**：在 CIFAR-10 上训练 **ResNet-18**，使用 SGD（无动量、无权重衰减），跟踪第一个残差块内各卷积层之间的平方 Frobenius 范数差（即 Theorem 3.6 定义的守恒量）。变换学习率（1e-3 到 5e-3），每个配置 10 个随机种子，训练 50 步。
- **Transformer 实验**：在 IMDb 情感分析数据集上训练一个 Transformer 模型，同样使用 SGD，跟踪第一层中第一个注意力头的 query/key 矩阵的 Frobenius 范数差（即 Corollary 3.10 的守恒量）。同样变化学习率，训练 50 步。
- 两者均统计守恒误差随步数的变化，并与理论斜率 \( O(\tau^2) \) 对比。
- 没有与其它方法对比，因为论文目标不是提出新算法，而是验证理论发现的守恒律在实际训练中是否近似保持。

### 4. 资源与算力

- **未明确说明**使用的 GPU 型号、数量或训练时长。
- 仅提到代码在 GitHub 上公开，实验规模较小（50 步训练），因此推测算力需求不高，在常规 GPU（如单卡 V100 或 RTX 系列）上即可完成。

### 5. 实验数量与充分性：大概做了多少组实验，是否充分、客观、公平

- 实验数量有限：两个主要实验（ResNet-18 + CIFAR-10；Transformer + IMDb），每个实验包含 4 种学习率，每种学习率下 10 个随机种子（因此共约 40 次训练），均只训练 50 步。
- **充分性**：作为对理论结果（Proposition 5.1）的验证，这些实验足以展示守恒误差随步长二次增长的趋势，并表明在真实训练中守恒律近似保持。但未进行更大规模（如完整训练 100+ epoch）或更多数据集的测试，也未包括消融实验（如改变网络深度、头数等）。
- **客观性**：固定种子、多次运行，结果统计可靠；与理论预测 O(τ²) 斜率吻合。
- **局限性**：实验覆盖较窄，未验证 Theorem 4.6/4.7 中关于深层网络局部守恒的完备性，也未检验 Adam 流下的守恒律（仅提及数值计算了 Lie 代数维度）。

### 6. 论文的主要结论与发现

- 残差块（或带有跳跃连接）的网络与对应的无跳跃连接网络具有**完全相同**的守恒律，跳跃连接不创造新的守恒量。
- 对单头注意力层，所有守恒律可由 \( QQ^\top - KK^\top \) 和 \( VV^\top - OO^\top \) 的函数给出（并给出了相关矩阵的秩条件）。
- 深层网络中，仅依赖单个残差块参数的守恒律与该块孤立时的守恒律完全一致；而跨越残差连接的两层参数（如 \( V^{l+1}, U^l \)）无额外非平凡守恒量。
- 离散 SGD 训练下，守恒误差与控制学习率的二次方成正比，且在实验中可观察到该缩放关系。
- 对于 Adam 流的简化版本（符号梯度下降），发现除一维特殊情况外，通常没有非平凡的守恒律。

### 7. 优点：方法或实验设计上有哪些亮点

- **理论贡献强烈**：将微分几何的 Lie 代数方法系统引入现代架构（残差网络、注意力机制）的守恒律分析，提供了完备刻画，且证明了部分参数守恒的“分解定理”，极大简化了复杂网络的分析。
- **结论清晰实用**：揭示了跳跃连接不改变守恒性质这一反直觉结果，以及注意力层特有的守恒量，对理解这类架构的隐式偏置和平衡行为具有指导意义。
- **实验设计简洁高效**：虽然实验数量少，但直接验证了关键理论预测（O(τ²) 规律），并给出了可复现的开源代码。
- **对实际优化有启示**：指出权重衰减会消除无正则化时的守恒量（Theorem 2.1），这一现象可能影响参数平衡性和最终泛化。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **实验覆盖不足**：
  - 仅测试了一个小型 ResNet（ResNet-18）和一个小型 Transformer（单头、单层），未考虑更深或更宽的架构，也未在更大基准（如 ImageNet、语言建模）上验证。
  - 训练仅 50 步，远未收敛，无法反映完整训练过程中守恒量的演化（虽然理论上在整条轨迹上守恒）。
  - 未对多头注意力机制验证完备性（仅给出部分守恒量，未证明是全部），也未包含层归一化、Dropout 等常见组件。
- **理论假设限制**：
  - 主要分析基于 **梯度流** 连续模型，离散优化仅有上界保证（Proposition 5.1），且假设梯度平方期望有界，这在非凸、非平滑网络中未必总成立。
  - 对卷积网络要求 \( n_v = p \) 才能得到 Theorem 4.7 的结论，且假设阵 None 的耦合结构（如注入性）限制了解释的一般性。
- **应用风险**：守恒律揭示的隐式偏置可能在某些情况下导致不良平衡（如训练陷入某个子空间），但论文未讨论如何利用或规避。
- **可读性**：部分证明（如 Theorem 4.7）高度技术化，结构复杂，可能对非数学背景读者不友好。

（完）
