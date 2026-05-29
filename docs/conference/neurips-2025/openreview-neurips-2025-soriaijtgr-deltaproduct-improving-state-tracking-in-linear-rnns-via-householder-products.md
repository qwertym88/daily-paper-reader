---
title: "DeltaProduct: Improving State-Tracking in Linear RNNs via Householder Products"
title_zh: DeltaProduct：通过Householder乘积改进线性RNN中的状态追踪
authors: "Julien Siems, Timur Carstensen, Arber Zela, Frank Hutter, Massimiliano Pontil, Riccardo Grazzi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=SoRiaijTGr"
tags: ["query:neural-arch"]
score: 6.0
evidence: 通过Householder乘积改进线性RNN状态追踪的新架构
tldr: 针对线性RNN中状态转移矩阵表达能力与效率的权衡问题，提出DeltaProduct架构，利用Householder乘积构造非对角但高效的转移矩阵。该设计在保持线性推理速度的同时显著提升了状态追踪能力。实验表明在关联记忆和状态追踪任务上优于对角线变体。为序列建模提供了新的结构设计思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 839, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1351, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 304, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1454, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 479, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 635, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 632, \"height\": 262, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1345, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1448, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 324, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1455, \"height\": 218, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1439, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1025, \"height\": 641, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 553, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 816, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1447, \"height\": 902, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1448, \"height\": 1154, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1448, \"height\": 1157, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1408, \"height\": 1794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1408, \"height\": 1793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-soriaijtgr/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 524, \"height\": 774, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-soriaijtgr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1456, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-soriaijtgr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 799, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-soriaijtgr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1423, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-soriaijtgr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1422, \"height\": 452, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-soriaijtgr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1418, \"height\": 473, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-soriaijtgr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 883, \"height\": 502, \"label\": \"Table\"}]"
motivation: 现有线性RNN的状态转移矩阵多为对角阵，表达力有限，难以实现复杂状态追踪。
method: 提出基于Householder乘积的状态转移矩阵结构，实现高效且表达力强的线性RNN。
result: 在关联记忆和状态追踪任务上性能优于DeltaNet等基线。
conclusion: Householder乘积结构是提升线性RNN表达力的有效途径。
---

## Abstract
Linear Recurrent Neural Networks (linear RNNs) have emerged as competitive alternatives to Transformers for sequence modeling, offering efficient training and linear-time inference. However, existing architectures face a fundamental trade-off between expressivity and efficiency, dictated by the structure of their state-transition matrices. Diagonal matrices, used in models such as Mamba, GLA, or mLSTM, yield fast runtime but have limited expressivity. To address this, recent architectures such as DeltaNet and RWKV-7 adopted a diagonal plus rank-1 structure, which allows simultaneous token and channel mixing, 
improving associative recall and, as recently shown, state-tracking when
allowing negative eigenvalues in the state-transition matrices.
Building on the interpretation of DeltaNet's recurrence as performing one step of online gradient descent per token on an associative recall loss, we introduce DeltaProduct, which instead takes multiple ($n_h$) steps per token. This naturally leads to diagonal plus rank-$n_h$ state-transition matrices, formed as products of $n_h$ generalized Householder transformations, providing a tunable mechanism to balance expressivity and efficiency. 
We provide a detailed theoretical characterization of the state-tracking capability of DeltaProduct in finite precision and how it improves by increasing $n_h$.
Our extensive experiments demonstrate that DeltaProduct outperforms DeltaNet in both state-tracking and language modeling, while also showing significantly improved length extrapolation capabilities.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：线性递归神经网络（Linear RNNs）在序列建模中成为 Transformer 的有力竞争者，兼具高效训练和线性时间推理的优点。然而，现有架构面临表达能力与效率之间的根本性权衡，这一权衡由状态转移矩阵的结构决定。
- **背景问题**：
  - 对角状态转移矩阵（如 Mamba、GLA、mLSTM）运行快但表达力有限，例如无法在有限精度下完成任意长度序列上的模3加法。
  - 近期模型（如 DeltaNet、RWKV-7）采用对角加秩1结构，可同时进行 token 和 channel 混合，但 DeltaNet 受限于单个 Householder 变换，对复杂状态追踪（如高阶置换群）需要多层；RWKV-7 则缺乏稳定性保证。
- 本文旨在**设计一种可调节表达力与效率之间平衡的线性 RNN 结构**，通过将 DeltaNet 的单步梯度下降扩展为多步，自然导出状态转移矩阵为多个广义 Householder 变换的乘积，从而提升状态追踪能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：
  - DeltaNet 的每个 token 的更新可视为对关联召回损失的**单步在线梯度下降**：  
    $$H_i = H_{i-1} - \beta_i \nabla L_i(H_{i-1}) = (I - \beta_i k_i k_i^\top)H_{i-1} + \beta_i k_i v_i^\top$$
  - **DeltaProduct** 在每个 token 上执行 **$n_h$ 步梯度下降**，从而得到状态转移矩阵为**多个广义 Householder 变换的乘积**：  
    $$A(x_i) = \prod_{j=1}^{n_h} (I - \beta_{i,j} k_{i,j} k_{i,j}^\top), \quad B(x_i) = \sum_{j=1}^{n_h} \left( \prod_{k=j+1}^{n_h} (I - \beta_{i,k} k_{i,k} k_{i,k}^\top) \right) \beta_{i,j} k_{i,j} v_{i,j}^\top$$
  - 参数 $n_h$ 是可调节的**表达力-效率旋钮**：$n_h=1$ 退化为 DeltaNet，$n_h$ 增大可逼近任意正交矩阵（由 Cartan-Dieudonné 定理保证），且谱范数恒≤1，保证稳定性。

- **关键技术细节**：
  - 为每个 token 生成 $n_h$ 组键 $k_{i,j}$、值 $v_{i,j}$ 和 $\beta_{i,j}$（通过可学习的投影矩阵）。
  - 支持扩展至**门控版本**（Gated DeltaProduct）：添加一个标量门控 $g_i \in [0,1]$ 乘以整个乘积，用以插值恒等映射和遗忘。
  - 实现上复用 Flash Linear Attention 库的 Triton 内核，通过扩展序列（将每个 token 的 $n_h$ 个步长拼接）并行计算。
  - **理论贡献**：
    - 定理1：对于任意 $n$，存在 DeltaProduct 模型在 $n_h=n-1$（单层）、$n_h>1$（3层）或 $n_h=1$（4层）下可解对称群 $S_n$ 的词问题。
    - 定理2：对于任意 $n_h \ge 1$ 和任意正则语言，存在 Gated DeltaProduct 模型（有限层数）可识别它。
    - 定理4：对于正交群 $O(n)$ 或特殊正交群 $SO(n+1)$（$n$ 为偶数）的子群，单层 $n_h=n$ 可解。
    - 通过分析展示了 $n_h=2$ 时可通过两个反射组合实现二维旋转，从而解 $S_4$ 和 $A_5$（利用与 $SO(3)$ 的同构）。

## 3. 实验设计

- **状态追踪实验**：
  - 任务：置换群词问题 $S_3, S_4, A_5, S_5$（如壳牌游戏：追踪隐藏物体位置）。
  - 训练序列长度 128，测试扩展到 512；使用 $[-1,1]$ 特征值范围。
  - 对比：DeltaNet（$n_h=1$）在不同层数下的表现；DeltaProduct 在不同 $n_h$ 下单层表现。
  - 数据集：合成数据（Merrill et al. 2024 的代码），200万训练样本，50万测试样本。
  - 结果：$n_h$ 增大显著提升长序列外推能力；$S_4$ 和 $A_5$ 仅需 $n_h=2$ 即可完美外推，验证了与 $SO(3)$ 的同构性。

- **形式语言（Chomsky 层次）实验**：
  - 任务：Parity、Modular Arithmetic（无括号/有括号）。
  - 训练长度 3~40，测试 40~256；对比 Transformer、mLSTM、sLSTM、Mamba、DeltaNet。
  - 结果：DeltaProduct 在 $n_h\ge2$ 且使用 $[-1,1]$ 特征值范围时平均准确率最高。

- **语言建模实验**：
  - 训练数据：FineWeb；外推测试：CodeParrot、OpenThoughts-114K-Math、TriviaQA。
  - 模型规模：213M/392M/805M 参数；训练 token 数 19B/35B/55B；上下文长度 4096。
  - 对比：DeltaNet（$n_h=1$）与 DeltaProduct（$n_h=2,3$），包括门控版本。
  - 评估：FineWeb 困惑度、LAMBADA、PIQA、HellaSwag、Winogrande、ARC-e/ARC-c 等（来自 lm-eval-harness）。
  - 结果：
    - DeltaProduct 在长序列外推上显著优于 DeltaNet，$n_h=3$ 时性能退化极小。
    - 在 805M 规模下，DeltaProduct 在 lm-eval 平均准确率上最高（49.95% vs DeltaNet 48.55%）。
    - 有效秩分析显示 DeltaProduct 的隐藏状态信息密度更可控，有利于遗忘和泛化。

- **吞吐量实验**：在 H100 上测量，参数匹配下 $n_h=2$ 吞吐量约为 DeltaNet 的 70%，$n_h=3$ 约为 50%（通过缩放头数或头维度匹配参数）。

- **消融与扩展**：
  - 验证了特征值范围 $[0,1]$ 无法学习状态追踪（无论 $n_h$ 多大）。
  - 对比了 gated 和 non-gated 版本，门控进一步改善外推。
  - 通过 PCA 分析了 $S_4$ 任务中学到的键向量，证实了三维子空间假设。

## 4. 资源与算力

- **明确说明**：
  - 训练使用 NVIDIA L40s、A100 40GB 或 H100 94GB GPU，共 16~32 块 GPU（2~8 节点）。
  - 总 GPU 时长约 10,500 小时（约 437.5 天·卡）。
  - 使用 DeepSpeed ZeRO-2 分布式训练。
- 论文未给出单个实验的具体 GPU 时间分布，但提供了上述总量。

## 5. 实验数量与充分性

- **实验组数**：共进行了以下主要实验：
  - 状态追踪：4 种群 × (2 种变量：$n_h$ 和层数) × 3 seeds → 约 24+ 组实验。
  - 形式语言：3 种任务 × (多个 $n_h$, DeltaNet, 其他基线) × 3 seeds → 约 30+ 组。
  - 语言建模：3 种模型大小 × 3 个 $n_h$ 值 × 2 种匹配参数方式（缩头维/缩头数）+ 门控版本 → 约 18 组主实验，外加外推和有效秩分析。
  - 吞吐量实验：1 组比较。
- **充分性评价**：
  - **状态追踪**：覆盖了从简单到极难的组问题，并验证了理论预测（$S_4$ 同构 $SO(3)$），实验设计有理论指导，充分且客观。
  - **语言建模**：在多个数据集和评估基准上进行，规模从 200M 到 800M，对比了最相关的基线 DeltaNet 和 Mamba 等，结果一致。但缺少与 RWKV-7 的直接对比（后者也是重要相关模型）。
  - **消融**：对门控、特征值范围、参数匹配方式做了分析，较完整。
  - **局限性**：缺少对 $n_h$ 更大时的性能趋势（如 $n_h=4$ 以上）以及与其他非对角模型（如 TTT-Linear、Titans）的直接对比。

## 6. 论文的主要结论与发现

1. **DeltaProduct 在状态追踪任务上优于 DeltaNet**：增加 $n_h$ 可解更难的置换群问题（如 $S_5$），而 DeltaNet 即使加深层数也难做到。
2. **语言建模中 DeltaProduct 在困惑度和下游任务上普遍优于 DeltaNet**，且长序列外推性能大幅提升（$n_h=3$ 时几乎不退化）。
3. **$n_h$ 可作为可调参数**，以可控的计算成本换取表达能力，且状态转移矩阵的谱范数恒 ≤1，保证了训练稳定性。
4. **隐含的旋转能力**：通过两个反射组合可实现二维旋转，从而解决与 $SO(3)$ 同构的组问题。
5. **理论分析**：给出了 DeltaProduct 识别正则语言和对称群词问题的上界，证明了其表达能力在 $n_h$ 增大时增强。

## 7. 优点

- **理论深度**：不仅提供实验结果，还给出了严谨的定理（如 Cartan-Dieudonné 定理的应用、与 $SO(3)$ 同构的物理解释），理论指导实验。
- **方法简洁优雅**：通过多步梯度下降的自然延伸导出新架构，无需复杂改动即可复用 DeltaNet 的实现。
- **可调表达力**：$n_h$ 提供了一个连续光谱，从对角（$n_h=1$）到稠密矩阵（$n_h$ 很大）之间插值。
- **稳定性保证**：所有状态转移矩阵的谱范数 ≤1，避免梯度爆炸/消失，利于长序列训练。
- **实验充分**：覆盖了状态追踪、形式语言、语言建模三大类，验证了理论预测，且对有效秩进行了深入分析解释外推能力。

## 8. 不足与局限

- **计算成本**：训练耗时与 $n_h$ 呈线性增长（因为递归步数倍增），尽管推理可通过并行化部分缓解；参数匹配时吞吐量下降明显。
- **实验覆盖不足**：
  - 缺少与 **RWKV-7** 的直接比较（后者也是非对角更新的代表作，且号称可单层解正则语言）。
  - 未探索 $n_h$ 大于 3 的情况（理论上应继续提升但成本过高）。
  - 未在更大规模（如 >1B）模型上验证。
- **需要宽 MLP**：理论构造（如解 $S_n$ 需 3 或 4 层）要求第二层 MLP 计算巨大的查找表（大小 $2^m \times (n!)^{2m}$），实际中可能不可行或难以优化。
- **门控的作用**：虽实验显示门控有益，但论文未深入分析与 $n_h$ 的联合影响。
- **有限精度下的理论**：虽然定理证明在有限精度下成立，但实际训练的数值行为可能受限于表示能力（如 β 值接近 2 时敏感）。
- **与其他方法的正交性**：论文提到可与固定点 RNN 结合，但未做实验验证。

（完）
