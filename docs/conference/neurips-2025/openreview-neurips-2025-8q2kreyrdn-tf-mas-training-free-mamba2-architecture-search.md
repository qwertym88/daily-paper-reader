---
title: "TF-MAS: Training-free Mamba2 Architecture Search"
title_zh: TF-MAS：无训练Mamba2架构搜索
authors: "Yi Fan, Yu-Bin Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=8q2kReYRDn"
tags: ["query:neural-arch"]
score: 9.0
evidence: 提出针对Mamba2的无训练神经架构搜索方法
tldr: 针对Mamba2架构，现有NAS方法需要大量训练，计算开销大。本文提出无训练NAS方法TF-MAS，利用SSD块中的秩崩溃现象设计代理指标，仅需计算变换矩阵及其梯度，无需训练即可高效搜索架构。实验验证了该方法在Mamba2上的有效性，显著降低了搜索成本。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-8q2kreyrdn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1142, \"height\": 793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8q2kreyrdn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 589, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8q2kreyrdn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1162, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8q2kreyrdn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1156, \"height\": 651, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1319, \"height\": 705, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1377, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1488, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1499, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1165, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1400, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1404, \"height\": 706, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1398, \"height\": 705, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1404, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1399, \"height\": 706, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1404, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1404, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1402, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1397, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-8q2kreyrdn/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1209, \"height\": 276, \"label\": \"Table\"}]"
motivation: 现有Mamba的NAS方法需大量训练资源，效率低。
method: 基于SSD块秩崩溃设计无训练代理指标，仅需计算变换矩阵及其梯度。
result: 实现无训练架构搜索，降低计算开销。
conclusion: 提出首个无训练Mamba2 NAS方法，高效实用。
---

## Abstract
The Mamba-type neural networks have gained significant popularity recently. To effectively and efficiently establish model architectures of Mamba, it is natural to introduce Neural Architecture Search (NAS) methods into Mamba. However, existing NAS methods tailored for Mamba are training-based, leading to substantial time and computational resource expenditure. To address this issue, and considering that Mamba2 is an improved version of the original Mamba, we propose a training-free NAS method specifically designed for Mamba2. Based on rank collapse in stacked State Space Duality (SSD) blocks, we design a proxy that only requires the computation of the transformation matrix and its gradient between two tensors within the network. Additionally, we develop a corresponding search space and introduce a novel approach for determining adjustable hyperparameter ranges. Experimental results show that our method outperforms all existing training-free NAS approaches in terms of both ranking correlation and the performance of search results for Mamba2 architecture. To the best of our knowledge, this is the first training-free NAS method designed for Mamba-type architectures. Our codes are available at https://github.com/fanyi-plus/tf-nas.

---

## 论文详细总结（自动生成）

# 论文详细中文总结：TF-MAS: Training-free Mamba2 Architecture Search

## 1. 核心问题与整体含义（研究动机和背景）

- **研究背景**：Mamba系列（尤其是Mamba2）作为状态空间模型（SSM）的代表，在序列建模中展现出接近Transformer的性能，但手动配置其超参数（如深度、宽度、状态维度、头数等）耗时且依赖经验。
- **核心问题**：现有针对Mamba的神经架构搜索（NAS）方法均为训练驱动（training-based），需要大量计算资源和时间；而训练无关（training-free）的NAS（零代理NAS）尚未被引入Mamba领域。
- **论文目标**：提出首个针对Mamba2（Mamba的改进版）的无训练NAS方法 **TF-MAS**，通过设计计算高效的代理（proxy）直接评估架构性能，避免完整训练，从而大幅降低搜索开销。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

### 核心思想
- **理论基础**：堆叠的注意力模块会出现秩崩溃（rank collapse）[18]，而Mamba2的核心模块——状态空间对偶（SSD）在堆叠时同样存在秩崩溃现象（论文给出理论证明和实验验证）。
- **代理设计**：借鉴ZeroLM[69]中基于核范数乘积的代理公式，但需适配SSD结构。代理值由每个Mamba2块中变换矩阵的核范数与其梯度的核范数的乘积求和得到：
  \[
  \text{TF-MAS} = \sum_{l} \left( \sum_{x \in \{X,B,C,\text{out}\}} \left\| \frac{\partial L}{\partial W_x} \right\|_{\text{nuc}} \cdot \|W_x\|_{\text{nuc}} \right)
  \]

### 关键技术细节
1. **变换矩阵的求解**：在Mamba2块内部，从输入U到X、B、C的映射包含卷积和SiLU，需近似求解变换矩阵 \(W_X, W_B, W_C\)。根据序列长度T与特征维度W的关系分为三种情况：
   - **T = W**：直接求逆。
   - **T < W**：无穷多解，取最小2-范数解（Moore-Penrose伪逆）。
   - **T > W**：无精确解，取最小二乘近似解（伪逆）。
2. **梯度计算**：由于 \(W_X, W_B, W_C\) 并非直接参数，通过链式法则利用 \(\partial L/\partial X\) 等计算其梯度。
3. **搜索空间设计**：
   - **SSMamba2**：固定超参数（深度D、宽度W、状态维度N、头数H）；**VWSSMamba2**：允许N和H逐层可变。
   - 超参数范围由预期计算开销（如参数量上限）决定：通过参考模型和缩放常数k（解三次方程）确定基准模型，然后取0.6倍至1.6倍作为范围，步长因子 \(I_D=1, I_W=32, I_N=8, I_H=1\)。
4. **算法流程**（见附录伪代码）：初始化网络 → 前向传播获取U、X、B、C → 反向传播获取梯度 → 根据T和W关系求解各变换矩阵 → 计算核范数乘积 → 求和得代理值。

## 3. 实验设计：数据集/场景、benchmark、对比方法

### 数据集与Benchmark
- **语言理解任务**：LAMBADA（PPL和ACC）、HellaSwag（HS）、PIQA、Arc-Easy/Challenge、WinoGrande（WG）、OpenbookQA（OBQA）。
- **NASBench构建**：基于5个公开预训练Mamba2模型（130M/370M/780M/1.3B/2.7B），从SSMamba2和VWSSMamba2搜索空间中各采样500个架构，共10个NASBench。性能通过权重继承+微调10个epoch（使用Pile数据集）获得。
- **搜索设置**：以130M模型为参考，参数量上限130M，使用进化算法（种群50，代数300）在两种搜索空间搜索最优架构。另有块进化变种（block-wise evolution）。

### 对比方法
- **无训练NAS代理**：参数数量（baseline）、Gradnorm、Synflow、GraSP、Fisher、Snip、Zen-NAS、ZiCo、MeCo、Auto-Prox（CNN方向）；Attention Confidence（AC）、Head Importance（HI）、Head Confidence（HC）、DSS++、AttnNAS（Transformer方向）。
- **基线模型**：原始Mamba2-130M。

## 4. 资源与算力

- **GPU类型**：4块NVIDIA Tesla V100 GPU。
- **搜索时间**：
  - SSMamba2搜索：0.7天
  - VWSSMamba2搜索：0.6天
- **训练测试**：搜索到的最优架构从零训练并测试，论文未明确给出训练时长及GPU数量细节（推测使用与搜索相同或相当的算力）。
- **NASBench构建**：需微调500个架构，每个10 epoch，总计算量较大但可接受。

## 5. 实验数量与充分性

- **排名相关性实验**：在10个NASBench（5个规模×2种搜索空间）上对比了14种无训练代理，涵盖8个数据集，结果稳定。
- **搜索性能实验**：在130M限制下进行了3种设置（SSMamba2、VWSSMamba2、VWSSMamba2 w/ bwe），报告了模型的参数量、FLOPs、延迟及8个任务的准确率/困惑度。
- **消融与讨论实验**：
  - 验证变换矩阵计算方式（替换为全连接权重导致相关性显著下降）。
  - 验证每个超参数的必要性（单变量变化仍保持正相关性）。
  - 验证三种T与W关系下的有效性（Case 1和Case 3同样有效）。
  - 验证代理复杂度（随W/N/H/P线性增长）。
  - 验证搜索空间范围选取的合理性（通过参数落在[0.9c0,c0]区间内的分布指标）。
  - 验证秩崩溃现象在SSD中的存在性（与Attention、Transformer、Mamba2对比）。
  - 验证测试性能的稳定性（对最优模型进行3次独立训练测试，波动很小）。
- **充分性评价**：实验设计全面，覆盖代理评价、实际搜索、消融分析，结论可靠。不足之处是仅针对语言建模任务，未扩展到视觉或更多模态。

## 6. 主要结论与发现

1. **TF-MAS作为首个Mamba2无训练NAS方法**，在所有NASBench上排名相关系数（Kendall's Tau）均远高于现有无训练代理，且显著超过参数数量基线（例如在VMSSMamba2Bench_2.7B上，TF-MAS在LAMBADA ACC上达到0.661，而基线仅0.437）。
2. **搜索得到的最优架构**（opt Mamba2、opt VWMamba2、opt VWMamba2 w/ bwe）在参数量、FLOPs、延迟均不超过130M模型的前提下，在多个任务上超越原始Mamba2-130M（如HS ACC从31.0%提升至40.5%）。
3. **块进化（block-wise evolution）** 进一步提升了搜索质量。
4. **代理的设计合理**：基于秩崩溃的理论基础、变换矩阵的精确求解、核范数乘积的使用均在实验中验证其必要性。

## 7. 优点：方法或实验设计上的亮点

- **首创性**：首个为Mamba类型网络设计无训练NAS的方法，填补空白。
- **理论支撑强**：从秩崩溃现象出发，严格证明SSD堆叠也会出现秩崩溃，代理设计有据可依。
- **搜索空间灵活**：提出基于计算开销自动确定超参数范围的方法，避免人工设定，并支持逐层可变宽度（VWSSMamba2）。
- **效率高**：代理计算仅需一次前向和反向传播（初始化状态），复杂度随主要参数线性增长；搜索时间仅0.6~0.7天。
- **对比公平**：对比方法包括CNN和Transformer方向的无训练代理，且针对Mamba2特殊结构（如将CB^T视为注意力图）进行了适配。
- **实验全面**：从相关性、搜索性能、消融、稳定性、范围合理性等角度充分验证。

## 8. 不足与局限

- **应用范围有限**：目前只针对Mamba2，未测试其他Mamba变体（如Vision Mamba等），也未涉及多模态或图像任务。
- **代理相关性仍有提升空间**：尽管优于现有方法，但部分数据集上的Kendall's Tau未超过0.7（如HS 0.38），可能存在搜索时的排序噪声。
- **计算资源说明不完整**：训练搜索结果的GPU详细信息（数量、时长）未提供，复现成本较高。
- **潜在的数据偏见**：NASBench构建使用了权重继承+微调，虽然证明噪声会降低Kendall's Tau（是保守估计），但实际无噪声环境下的性能可能更高，实验未完全消除这种偏差。
- **未讨论搜索空间复杂度极高的情况**：VWSSMamba2在深度较大时搜索空间天文数字（约5.68×10^50），进化搜索可能无法充分探索。

（完）
