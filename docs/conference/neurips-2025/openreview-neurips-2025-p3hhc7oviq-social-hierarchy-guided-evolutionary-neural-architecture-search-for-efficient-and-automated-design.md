---
title: Social Hierarchy-Guided Evolutionary Neural Architecture Search for Efficient and Automated Design
title_zh: 社会等级引导的进化神经架构搜索实现高效自动设计
authors: "Fang Su, YuChen Jing, Yance Wang, Jiajun Yao"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=p3hhC7OvIq"
tags: ["query:neural-arch"]
score: 9.0
evidence: 社会等级引导的进化神经架构搜索，实现高效自动设计
tldr: 进化神经架构搜索（ENAS）计算成本高。本文提出社会等级引导的ENAS（SH-ENAS），受社会层级启发设计种群组织结构，并基于此优化搜索过程。在多个基准上，SH-ENAS以更低计算量搜索到精度更高的架构，显著优于现有ENAS方法。该工作为低成本的自动架构设计提供了有效解决方案。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-p3hhc7oviq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p3hhc7oviq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p3hhc7oviq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 657, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p3hhc7oviq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 938, \"height\": 159, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p3hhc7oviq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 940, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-p3hhc7oviq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1175, \"height\": 822, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1129, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 140, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1440, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1307, \"height\": 872, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1328, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1220, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 933, \"height\": 780, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-p3hhc7oviq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 985, \"height\": 459, \"label\": \"Table\"}]"
motivation: 降低进化神经架构搜索的计算成本，同时保持高精度。
method: 提出社会等级引导的种群组织结构和相应的搜索策略。
result: 在多个基准上以更低计算成本获得更高精度架构。
conclusion: 社会等级机制有效提升ENAS的效率与效果。
---

## Abstract
Neural Architecture Search (NAS) serves as an important component in Automated Machine Learning. Compared with reinforcement learning and gradient-based NAS approaches, evolutionary computation-based NAS (ENAS) has gained prominence due to its lower dependence on domain expertise and superior adaptability across diverse problem domains. However, despite a lot of research, how to significantly reduce the computational cost while pursuing high accuracy is still a huge challenge for ENAS. To address this issue, we propose a Social Hierarchy-guided Evolutionary Neural Architecture Search algorithm (SH-ENAS). In this algorithm, inspired by the social hierarchy, a novel population organization structure is designed, and based on it, effective guidance operations are designed for the subsequent evolutionary search process. Additionally, to further reduce computational overhead, a progressive evaluation search method is proposed, which introduces weight inheritance and validation-loss-guided early stopping operation to prevent unnecessary evaluations of the architecture. The experimental results demonstrate that SH-ENAS achieves test errors of $2.50\%$ and $16.24\%$ on CIFAR-10 and CIFAR-100, respectively, outperforming existing state-of-the-art methods. In particular, SH-ENAS requires only $10$ population individuals and $12$ iterations to complete the search, with computational costs as low as $0.69$ GPU days and $0.83$ GPU days, validating the significant advantages of the new algorithm in terms of accuracy, computational efficiency, and automation.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：进化神经架构搜索（ENAS）因不依赖领域知识和强适应性而备受关注，但其计算成本依然高昂，如何在追求高精度的同时显著降低计算开销是当前ENAS面临的核心挑战。
- **背景**：现有ENAS方法存在两大不足：一是遗传算法中固定概率的交叉/变异缺乏有效引导，导致搜索能力弱，需要大种群和多次迭代；二是搜索过程中大量冗余的性能评估（如对后期贡献很小的个体仍进行完整训练）造成严重计算浪费。本文旨在通过改进搜索过程和减少冗余评估来提升ENAS效率。

### 2. 论文提出的方法论
- **核心思想**：受社会等级制度启发，设计了三层次种群组织结构，并为每个子种群赋予差异化的交叉/变异策略，以此引导搜索；同时提出渐进式评估搜索方法（含权重继承和早停）进一步降低计算开销。
- **关键技术细节**：
  - **社会等级种群组织**：将每代种群按适应度分为上层、中层、下层三个子种群。上层负责保留最优个体（交叉/变异率为0）；中层采用自适应交叉率 \(c_m = \lambda_m e^{-k_c \delta^2_t} (1 - t/T)\) 和变异率 \(m_m = \mu_m e^{-k_m \delta^2_t} (1 - t/T)\)，兼顾探索与开发；下层采用随迭代递减的高交叉/变异率（\(c_l = \lambda_l (1 - t/T)\), \(m_l = \mu_l (1 - t/T)\)），以增强多样性并跳出局部最优。
  - **社会等级引导的变异**：
    - **变异算子选择**：根据上层子种群节点数的众数 \(\bar{n}_{top}\) 动态调整添加、修改、删除三种算子的概率。例如，当个体节点数 \(n < \bar{n}_{top}\) 时，优先添加节点；当 \(n > \bar{n}_{top}\) 时，优先删除节点；当 \(n = \bar{n}_{top}\) 时，仅允许修改。
    - **操作类型选择**：统计上层子种群中各类操作的出现频率，形成高质量操作集 \(L_{good}\)（频率最高的两种）和低质量操作集 \(L_{bad}\)（频率最低的两种）。在添加操作时从 \(L_{good}\) 中轮盘赌选择；修改操作时若当前存在 \(L_{bad}\) 中的操作，则将其替换为 \(L_{good}\) 中的操作。
  - **种群缩减**：在下层子种群中，根据迭代次数和适应度变化率 \(v = (f_t - f_{t-1})/f_{t-1}\) 动态计算缩减概率 \(P(t)\)。当迭代前期或适应度变化较快时不缩减，否则逐渐增加缩减概率，从而避免对低性能个体的无效评估。
  - **渐进式评估搜索**：设置最大训练轮次上限 \(n\)，并引入基于验证损失的早停机制：若验证损失连续 \(m\) 个轮次低于阈值 \(\delta\) 则提前终止训练。同时，通过权重继承（交叉和变异中保留未改动部分的参数）减少重复训练。
- **公式**：
  - 适应度函数：\( \text{Fitness}(x) = \lambda \cdot \frac{acc(x)-acc_{min}}{acc_{max}-acc_{min}} + (1-\lambda) \cdot \left(1 - \frac{parm(x)-parm_{min}}{parm_{max}-parm_{min}}\right) \)，其中 \(\lambda=0.95\) 平衡精度与参数量。
- **算法流程**（文字描述）：
  1. 初始化种群（编码为NASNet-style序列）。
  2. 逐代进行：评估个体适应度 → 按适应度分为上、中、下子种群（比例1:2:2）。
  3. 对上层个体不进行交叉/变异，直接保留。
  4. 对中层个体，根据其适应度方差和当前迭代计算自适应交叉/变异率；根据上层节点分布选择变异算子（添加/修改/删除）和操作类型。
  5. 对下层个体，使用高交叉/变异率（随时间递减）并同样受上层引导；同时动态缩减下层规模。
  6. 采用渐进式评估：权重继承 + 早停。
  7. 重复迭代12次，最终输出最优架构。

### 3. 实验设计
- **数据集**：CIFAR-10 和 CIFAR-100（均为图像分类基准）。
- **Benchmark（对比方法）**：
  - **手动设计网络**：DenseNet-BC、MobileNet-V2、ShuffleNet。
  - **RL-NAS**：NASNet-A、Efficient NAS、MetaQNN。
  - **梯度NAS**：DARTS、DARTS-PT。
  - **进化NAS**：Genetic CNN、CNN-GA、AmoebaNet-A、pEvoNAS-c10c、MOGIG-Net、CARS、ESENet-P。
- **对比指标**：分类测试错误率、参数量（Params）、GPU天数（计算成本）。
- **消融实验**：在CIFAR-10上依次移除每个核心组件（社会等级种群组织、引导变异、种群缩减、渐进式评估），观察精度、GPU天数和参数量的变化。
- **参数敏感性实验**（附录）：测试了不同子种群划分比例（1:4:5, 1:2:2, 1:1:3, 3:3:4）和不同自适应交叉/变异系数组合，以确定最优配置。

### 4. 资源与算力
- **硬件**：Intel® Xeon Gold 5218R CPU，NVIDIA Tesla V100 GPU。
- **软件**：Ubuntu 18.04.2, Python 3.11.8, PyTorch 2.2.2。
- **计算成本**：
  - CIFAR-10：0.69 GPU days。
  - CIFAR-100：0.83 GPU days。
- **搜索设置**：种群大小10，迭代次数12，早停阈值0.001，patience=5等（详见附录表7）。

### 5. 实验数量与充分性
- **实验数量**：
  - 主要对比实验（表3）：在CIFAR-10和CIFAR-100上对比15种方法，报告了平均和最佳结果（含多次运行的均值和标准差）。
  - 消融实验（表4）：5个组件逐一移除，共6组实验。
  - 子种群划分比例实验（附录表5）：4组对比。
  - 自适应系数实验（附录表6）：3组对比。
- **充分性与公平性**：
  - 对比方法结果均来自原论文，设置一致，具有可比性。
  - 消融实验完整，验证了每个组件的必要性。
  - 超参数调优通过单独实验确定（如比例、系数），减少了主观偏差。
  - 但仅测试了图像分类（CIFAR-10/100），未覆盖其他领域（如NLP、目标检测），也未与更大型数据集（如ImageNet）上的NAS方法直接对比。实验充分性中等。

### 6. 论文的主要结论与发现
- SH-ENAS在CIFAR-10上达到2.50%测试错误率，在CIFAR-100上达到16.24%，均优于所有对比的手动设计和NAS方法。
- 计算成本极低：仅需0.69~0.83 GPU days，远低于大多数ENAS方法（如AmoebaNet需3150 GPU days）。
- 使用极小的搜索规模（10个体，12次迭代）就能获得高质量架构，验证了社会等级引导机制在提升搜索效率方面的有效性。
- 消融实验表明，每个核心组件（社会等级组织、引导变异、种群缩减、渐进式评估）都对最终性能有贡献，特别是渐进式评估大幅降低了GPU天（从8.10降至0.69）。

### 7. 优点
- **方法创新**：
  - 首次将社会等级思想融入ENAS，设计了三子种群差异化策略，有效平衡探索与利用。
  - 动态变异算子选择和操作类型引导，使得搜索朝着高性能方向高效进行。
  - 种群缩减机制避免了后期低价值个体的评估浪费。
  - 渐进式评估结合权重继承和早停，显著降低训练开销。
- **效率突出**：仅需10个体和12次迭代，计算成本低于绝大多数NAS方法，同时保持甚至超越了SOTA精度。
- **自动化程度高**：无需专家设计超网络或复杂代理模型，适合资源受限场景。
- **实验完整**：提供了消融实验和参数敏感性分析，验证了设计合理性。

### 8. 不足与局限
- **应用范围有限**：仅验证了CNN图像分类任务（CIFAR-10/100），未在ImageNet大规模图像分类、目标检测、语义分割或NLP任务上测试，泛化能力未充分证明。
- **搜索空间限制**：采用NASNet-style编码（固定细胞结构），未探索更灵活或复杂的搜索空间（如Transformer架构）。
- **超参数敏感性**：虽进行了部分调优，但关键参数（如子群比例、交叉/变异系数）仍需手动设定，未讨论在更大搜索空间下的自适应能力。
- **与最新大规模方法对比不足**：未与EfficientNet、RegNet等基于手动/自动设计的极高效模型对比，也未与最新的大语言模型NAS方法（如基于Transformer的）对比。
- **消融实验仅报告一次运行结果**（表4只显示单次值，未提供标准差），可能缺少统计显著性分析。
- **收敛性分析缺失**：未从理论上分析社会等级引导的收敛性保证，也未讨论早停可能带来的有偏评估问题（论文参考文献[33]提及）。

（完）
