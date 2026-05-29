---
title: Runtime Analysis of Evolutionary NAS for Multiclass Classification
title_zh: 进化NAS在多分类问题上的运行时分析
authors: "Zeqiong Lv, Chao Qian, Yun Liu, Jiahao Fan, Yanan Sun"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=biKDr4cNMQ"
tags: ["query:neural-arch"]
score: 8.0
evidence: 进化神经网络架构搜索的运行时分析
tldr: 本文首次对进化NAS在多分类问题上的运行时进行理论分析。提出了一个基准问题和两级搜索空间，使得搜索空间设置与常见ENAS一致。为ENAS的理论研究奠定了基础。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bikdr4cnmq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1702, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bikdr4cnmq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1776, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bikdr4cnmq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 850, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bikdr4cnmq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1675, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bikdr4cnmq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 672, \"height\": 932, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bikdr4cnmq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1523, \"height\": 1516, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bikdr4cnmq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1515, \"height\": 1513, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bikdr4cnmq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1779, \"height\": 409, \"label\": \"Table\"}]"
motivation: 进化NAS理论分析尚处于初期，缺乏运行时分析。
method: 提出适合多分类的基准和两级搜索空间，进行严格的运行时分析。
result: 建立了ENAS在多分类上的理论分析框架和基准。
conclusion: 为进化NAS的理论发展提供了基础，指导实际算法设计。
---

## Abstract
Evolutionary neural architecture search (ENAS) is a key part of evolutionary machine learning, which commonly utilizes evolutionary algorithms (EAs) to automatically design high-performing deep neural architectures. During past years, various ENAS methods have been proposed with exceptional performance. However, the theory research of ENAS is still in the infant. In this work, we step for the runtime analysis, which is an essential theory aspect of EAs, of ENAS upon multiclass classification problems. Specifically, we first propose a benchmark to lay the groundwork for the analysis. Furthermore, we design a two-level search space, making it suitable for multiclass classification problems and consistent with the common settings of ENAS. Based on both designs, we consider (1+1)-ENAS algorithms with one-bit and bit-wise mutations, and analyze their upper and lower bounds on the expected runtime. We prove that the algorithm using both mutations can find the optimum with the expected runtime upper bound of $O(rM\ln{rM})$ and lower bound of $\Omega(rM\ln{M})$. This suggests that a simple one-bit mutation may be greatly considered, given that most state-of-the-art ENAS methods are laboriously designed with the bit-wise mutation. Empirical studies also support our theoretical proof.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：进化神经网络架构搜索（ENAS）已在实际应用中取得优异性能，但其理论基础十分薄弱，尤其是运行时分析（runtime analysis）这一进化算法的重要理论方面几乎空白。现有理论工作仅局限于二分类问题，且搜索空间与实际ENAS算法存在较大差距。
- **核心问题**：如何为多分类问题建立适合运行时分析的基准问题、搜索空间，并证明(1+1)-ENAS算法在两种常见变异操作（单比特变异、逐比特变异）下的期望运行时上、下界。
- **整体含义**：首次将ENAS的运行时分析从二分类扩展到多分类，给出了与问题规模（类别数M、扇区划分参数r）相关的理论界，并指出简单的单比特变异与复杂的逐比特变异性能相当，为实际ENAS算法设计提供理论指导。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **基准问题MCC**：定义了一个多分类问题，输入是单位圆盘上的点，均匀划分为2rM个扇区，每个扇区可再分为三角形和弓形区域。每个类别包含r个三角形、r个扇区和r个弓形区域，决策区域形状涵盖半空间、无界多面体、有界多面体，反映了真实多分类的复杂性。
- **两级搜索空间**：第一级为细胞（cell），对应M-1个细胞（每个细胞输出0/1）；第二级为块（block），每个细胞包含A、B、C三种类型的块（可分别产生弓形、扇区、三角形决策区域）。架构编码为M-1个三元组（n_A, n_B, n_C），每个分量表示对应类型块的数量。
- **适应度函数**：基于几何面积公式化表达。设I_x为正确分类的三角形数（所有细胞之和），J_x为正确分类的弓形数，ε_x为第M类中被错误分类的弓形数，则适应度F(x) = (Ar_tri·(I_x+2r) + Ar_seg·(J_x+2r-ε_x))/π。该函数类似于OneMax函数，使得优化可逐步增加正确分类区域。
- **(1+1)-ENAS算法**：初始解随机采样块数量（上界s=r）；每代变异分内外两层：外层选择要变异的细胞（单比特：均匀选一个；逐比特：每个细胞以1/(M-1)概率独立选择），内层对选中的细胞执行局部或全局变异（加、删、改一种类型的块）。选择策略：若后代适应度不低于父代则替换。
- **运行时分析上界**：分为两个阶段：第一阶段将I_x提升至最大值（N=2r(M-1)），第二阶段将J_x-ε_x提升至N。利用乘法漂移定理，证明单比特与逐比特变异均可达到O(rM ln(rM))上界。
- **运行时分析下界**：通过分析初始解中“好细胞”的分布以及持续未改进概率，证明下界为Ω(rM ln M)。结合上界，说明两者性能差距仅为常数因子。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集/场景**：使用论文提出的MCC基准问题，不依赖真实图像数据集，完全是合成几何分类任务。
- **Benchmark**：即MCC问题本身，参数M（类别数）从2到24（步长2），r（扇区倍增因子）从2到10（步长2）。每个设置运行1000次独立实验。
- **对比方法**：
  - (1+1)-ENAS的四种变异组合：单比特+局部内变异、单比特+全局内变异、逐比特+局部内变异、逐比特+全局内变异。
  - 扩展到带种群和交叉的ENAS：(λ+λ)-ENAS（λ=2,4,10），带单点交叉和均匀交叉的版本。同样对比四种变异组合。

### 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点。

- **论文未明确说明**：文中未提及使用的GPU型号、数量、训练时长等具体算力信息。所有实验为合成基准上的仿真运行，仅统计进化代数，不涉及真实神经网络的训练，因此计算开销主要来自CPU仿真，但作者未披露硬件配置。

### 5. 实验数量与充分性：大概做了多少组实验，这些实验是否充分、是否客观、公平

- **实验数量**：
  - 主体实验：M从2到24共12个值×r从2到10共5个值=60种参数组合，每种组合四种变异设置，每个设置1000次独立运行，总计60×4×1000=240,000次运行（仅(1+1)-ENAS）。
  - 扩展实验：9种带种群/交叉的ENAS（三种λ×三种交叉类型）×60种参数组合×四种变异设置×1000次，总计9×60×4×1000=2,160,000次运行。数据量充分。
- **充分性与公平性**：
  - 覆盖了多个M和r值，展示了算法性能随问题规模变化的趋势。
  - 对比了四种主要变异组合，且扩展到真实ENAS常用框架（种群、交叉），验证结论普适性。
  - 统计了平均代数，误差估计可靠（1000次重复）。但未报告方差或置信区间，仅展示均值曲线。
  - 所有实验采用相同初始化和随机种子，对比公平。

### 6. 论文的主要结论与发现

- **核心结论**：(1+1)-ENAS使用单比特变异与逐比特变异的期望运行时上界均为O(rM ln(rM))，下界均为Ω(rM ln M)，说明两者性能仅相差常数因子，与理论证明一致。
- **实践启示**：在基于块/细胞的搜索空间中，简单单比特变异即可达到与复杂逐比特变异相近的效率，建议ENAS算法优先考虑单步变异（如AE-CNN所用的单步变异）。
- **理论贡献**：首次为ENAS多分类建立完整的运行时分析框架，包括基准问题、两级搜索空间、公式化适应度函数，为后续ENAS理论研究奠定了基础。

### 7. 优点：方法或实验设计上有哪些亮点

- **理论创新**：克服了将多分类决策区域几何化建模的困难，设计了兼容实际ENAS设置的两级搜索空间，使理论分析能够与常见ENAS算法（如细胞/块结构）对齐。
- **公式化适应度函数**：适应度可分解为I_x和J_x两部分，分别对应三角形和弓形正确分类数，与OneMax函数类似，便于应用乘法漂移和适应度层技术。
- **理论界紧致**：上界与下界仅差对数因子，证明方法严谨。
- **实验扩展充分**：不仅验证(1+1)-ENAS，还扩展到种群、交叉等更实际的进化算子，证明结论的鲁棒性。
- **实用导向**：指出单比特变异优于逐比特变异的实践意义，可能简化ENAS算法设计。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等

- **问题场景局限**：MCC基准是人工合成的几何分类问题，决策区域形状仅限三角形、扇区、弓形，与实际图像等高维多分类任务差异大，结论向真实NAS的推广需谨慎。
- **假设理想化**：假设所有块参数（权重、偏置）可通过优化方法达到最优，且激活函数为硬阈值二进制，不涉及真实神经网络训练中的非凸优化、过拟合等问题。
- **搜索空间限制**：仅考虑三种类型的块，尚未包含更丰富的拓扑结构（如跳跃连接、池化等），实际ENAS搜索空间更为复杂。
- **变异操作定义**：内层变异每次只能加、删、改一种类型的块，且操作均匀随机，与实际ENAS中常见的带概率的多种变异可能不同。
- **未报告方差**：实验仅给出平均代数，缺少标准差或置信区间，无法评估结果稳定性。
- **下界证明依赖初始解分布**：下界Ω(rM ln M)要求初始解块数量上界s=r，且算法无精英保护（(1+1)选择），若s更大或采用其他选择机制，下界可能不同。

（完）
