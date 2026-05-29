---
title: On the Expressive Power of Mixture-of-Experts for Structured Complex Tasks
title_zh: 关于混合专家模型在结构化复杂任务上的表达能力
authors: "Mingze Wang, Weinan E"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zSrb8rtH9M"
tags: ["query:neural-arch"]
score: 5.0
evidence: 混合专家模型表达能力分析，属于新颖架构设计
tldr: 本文系统研究混合专家网络（MoE）在结构化复杂任务上的表达能力。证明浅层MoE可高效逼近低维流形上的函数，深层MoE能以组合稀疏性逼近大量分段函数。该理论为MoE架构设计提供了支撑。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zsrb8rth9m/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 431, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zsrb8rth9m/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 425, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zsrb8rth9m/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 433, \"height\": 390, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zsrb8rth9m/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1223, \"height\": 152, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zsrb8rth9m/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 761, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zsrb8rth9m/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 905, \"height\": 111, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zsrb8rth9m/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1116, \"height\": 151, \"label\": \"Table\"}]"
motivation: MoE在实践中高效，但缺乏理论基础，特别是其建模复杂任务的能力。
method: 通过低维流形和稀疏性假设，分析浅层和深层MoE的逼近能力。
result: 证明浅层MoE克服维度诅咒，深层MoE可表达指数级数量的分段函数。
conclusion: 揭示了MoE高效性的理论根源，指导架构优化。
---

## Abstract
Mixture-of-experts networks (MoEs) have demonstrated remarkable efficiency in modern deep learning. Despite their empirical success, the theoretical foundations underlying their ability to model complex tasks remain poorly understood.
In this work, we conduct a systematic study of the expressive power of MoEs in modeling complex tasks with two common structural priors: low-dimensionality and sparsity.
For shallow MoEs, we prove that they can efficiently approximate functions supported on low-dimensional manifolds, overcoming the curse of dimensionality.
For deep MoEs, we show that $\mathcal{O}(L)$-layer MoEs with $E$ experts per layer can approximate piecewise functions comprising $E^L$ pieces with compositional sparsity, i.e., they can exhibit an exponential number of structured tasks.
Our analysis reveals the roles of critical architectural components and hyperparameters in MoEs, including the gating mechanism, expert networks, the number of experts, and the number of layers, and offers natural suggestions for MoE variants.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：混合专家网络（MoE）在大规模深度学习（如大语言模型）中表现优异，但其理论基础——尤其是处理复杂任务时的表达能力——尚不清晰。现有理论缺乏对MoE如何利用数据的低维结构和稀疏结构来高效建模的系统理解。
- **整体含义**：本文旨在从理论上证明MoE可以利用两种常见结构先验（低维流形和组合稀疏性）克服维度灾难，解释其成功背后的原理，并为MoE架构设计提供指导。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：MoE通过分解复杂任务为多个局部子任务，并由门控机制完成输入到专家的分配，从而在高维数据中利用内在低维或稀疏结构。
- **关键技术细节**：
  - **浅层MoE（深度2）**：
    - 假设目标函数定义在d维光滑紧致流形上，存在正则图集 $\{(U_i, \phi_i)\}_{i\in[E]}$ 和单位分解 $\{\rho_i\}$。
    - 第一层MoE近似单位分解函数 $\rho_i$（使用宽度 $\Omega(E^2)$ 的稠密网络），第二层门控通过线性路由选择专家，专家网络近似低维局部函数 $f|_{U_i} \circ \phi_i^{-1}$ 和坐标映射 $\phi_i$。
    - 误差分解为两个部分：局部函数逼近误差 + 坐标映射逼近误差，最终率随内在维度 $d$ 而非环境维度 $D$ 衰减。
  - **深层MoE（深度 $2L$）**：
    - 目标函数形式 $f(x) = (f_{1,i_1}(x_1), \ldots, f_{L,i_L}(x_L))$，其中 $x_l \in U_{l,i_l}$，每个子函数只依赖单一坐标，且组成乘积流形。
    - 每一对MoE层（第 $2l-1$ 层和第 $2l$ 层）近似一个子函数 $f_{l,i_l}$，通过门控选择专家，最终堆叠 $L$ 对层实现指数级 $E^L$ 个分段函数的逼近。
  - **门控非线性建议**：理论表明线性门控能力不足，需要非线性门控（如两层ReLU路由网络）来近似非线性单位分解，从而简化深度。
- **算法流程**（文字说明）：
  - 浅层：输入 $x$ → 第1层MoE（所有专家输出 $(x, \tau(x))$，其中 $\tau$ 近似 $\rho$）→ 第2层门控计算 $\tau(x)$ 并选择最大值的专家 → 该专家输出 $g_i \circ \psi_i(x)$ 逼近 $f|_{U_i}$。
  - 深层：输入 $(x_1,\ldots,x_L)$，对每个 $l$：第 $2l-1$ 层近似局部指示函数 $\tau^{(l)}(x_l)$，第 $2l$ 层门控选择专家，输出 $g_{l,i} \circ \psi_{l,i}(x_l)$；最后 $L$ 维输出组合为最终函数。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **实验一（验证浅层MoE）**：
  - **场景**：低维流形 $\mathcal{M} = \{x \in \mathbb{R}^D : x_1^2+x_2^2=1; x_i=0\ \forall i>2\}$，目标函数 $f(x)=\sin(5x_1)+\cos(3x_2)$，输入维度 $D\in\{16,32,64,128\}$。
  - **模型**：1-4-MoE（1个路由层，4个专家，每个专家两层ReLU网络，隐藏宽度10）。
  - **对比**：无显式基准，通过变化 $D$ 观察误差是否稳定（证明克服维度诅咒）。
- **实验二（验证深层MoE）**：
  - **场景**：分段函数 $f$ 在 $[0,3]^2$ 上由 $3^2=9$ 个单元立方体上的子函数组合而成（具体形式见图3说明）。
  - **模型**：2-3-MoE（2个MoE层，每层3个专家）与 1-6-MoE（1个MoE层，6个专家，参数量相当）。
  - **对比**：改变专家隐藏宽度 $m\in\{16,32,64,128\}$，比较两种架构的测试误差。
- **Benchmark**：无公开基准，作者自行构造合成函数。

## 4. 资源与算力

- **文中明确说明**：实验在 **1块A100 GPU** 上进行。
- 训练配置：
  - 实验一：2000迭代，batch size 128，平方损失，Adam优化器，学习率1e-3。
  - 实验二：5000迭代，batch size 128，平方损失，Adam优化器，学习率1e-3。
- 未说明总训练时长，但考虑模型规模小、迭代少，算力需求较低。

## 5. 实验数量与充分性

- **实验数量**：
  - 实验一：仅报告了4组不同输入维度的测试误差（单一配置，未做重复或消融）。
  - 实验二：报告了2种架构 × 4种隐藏宽度的测试误差（共8组），无重复实验。
- **充分性评价**：
  - 实验作为理论辅助验证，设计清晰简洁，但数量有限。
  - 优点：直接对应理论结论（克服维度诅咒、深度MoE优于浅层MoE）。
  - 不足：缺乏（1）多次重复以显示统计稳定性；（2）不同流形/函数类型；（3）更复杂的MoE变体对比；（4）消融门控非线性等组件。整体说服力有限。

## 6. 论文的主要结论与发现

- **结论1**：浅层MoE可以高效逼近低维流形上的函数，逼近率 $\tilde{\mathcal{O}}\big(m^{-\frac{\kappa(f|_{U_i})}{d} \wedge \frac12}\big)$，避免维度诅咒；与之对比的稠密网络率为 $\tilde{\mathcal{O}}\big(m^{-\frac{\kappa(f)}{D} \wedge \frac12}\big)$。
- **结论2**：深层MoE（$2L$层，每层$E$个专家）可逼近具有组合稀疏性的分段函数，包含 $E^L$ 个不同片段，实现指数级任务数量。
- **结论3**：门控机制需要非线性才能高效建模；交替MoE-稠密层或共享+路由专家等变体具有等价表达能力。
- **结论4**：MoE通过分解复杂问题为子问题，并利用结构先验，实现高效逼近。

## 7. 优点：方法或实验设计上有哪些亮点

- **理论贡献**：
  - 首次系统证明MoE在低维流形和组合稀疏结构下的表达能力，填补空白。
  - 分解专家和门控的角色，提供可解释洞见（专家负责局部逼近，门控负责分配）。
  - 提出非线性门控、低维专家网络（通过自编码器降维）等实用建议。
- **实验设计**：
  - 两个实验分别直接对应浅层和深层理论，验证了克服维度诅咒和深度的指数级优势。
  - 控制参数量相当（实验二中1-6-MoE与2-3-MoE参数可比），比较公平。
- **证明技术**：利用图集、单位分解等流形工具，构建显式MoE网络进行逼近，证明清晰。

## 8. 不足与局限：包括实验覆盖、偏差风险、应用限制

- **实验覆盖不足**：
  - 仅针对双变量人工函数，未使用真实数据集（如图像、文本），与实际MoE应用场景差距大。
  - 未验证非线性门控、自编码专家等建议的有效性，仅停留在理论建议。
  - 无重复实验，无法排除随机性影响。
- **偏差风险**：合成数据完美满足理论假设（低维流形或完美分段），对噪声、非理想条件缺乏鲁棒性分析。
- **应用限制**：
  - 理论假设目标函数具有严格的正则图集和单位分解，实际中可能难以满足。
  - 训练动力学未分析：文中指出虽然存在这样的MoE网络，但SGD能否找到是开放问题。
  - 仅考虑top-1路由（$K=1$），未讨论更一般的top-K路由。
  - 未考虑负载平衡等实际MoE训练中的关键因素。

（完）
