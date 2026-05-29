---
title: Scaling Value Iteration Networks to 5000 Layers for Extreme Long-Term Planning
title_zh: 将值迭代网络扩展到5000层以进行极端长期规划
authors: "Yuhui Wang, Qingyuan Wu, Dylan R. Ashley, Francesco Faccio, Weida Li, Chao Huang, Jürgen Schmidhuber"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=YwltsnSUFQ"
tags: ["query:neural-arch"]
score: 6.0
evidence: 将VIN扩展到5000层，采用动态转移核
tldr: 针对值迭代网络难以扩展到长期大规模规划的问题，本文通过引入动态转移核增强潜在MDP的表征能力，并解决梯度消失问题，成功将VIN扩展到5000层。实验表明，该方法在100x100迷宫中实现了高效的规划，大幅提升了规划深度和泛化能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1530, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1299, \"height\": 870, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 674, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1838, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1767, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1741, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1634, \"height\": 1527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1634, \"height\": 1528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1619, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ywltsnsufq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 893, \"height\": 939, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 730, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1081, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1215, \"height\": 616, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 784, \"height\": 751, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1272, \"height\": 195, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1067, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 981, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1019, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1020, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1214, \"height\": 571, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1261, \"height\": 493, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1695, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1209, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1216, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1156, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1698, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ywltsnsufq/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 984, \"height\": 231, \"label\": \"Table\"}]"
motivation: 值迭代网络在长期规划任务中受限于潜在MDP表征能力和网络深度不足。
method: 通过动态转移核增强MDP表征，并设计深层规划模块以缓解梯度消失。
result: 在100x100迷宫等任务中，5000层VIN实现了高效规划，性能显著优于现有方法。
conclusion: 该工作为深度规划网络的设计提供了新思路，证明了极深架构在规划任务中的潜力。
---

## Abstract
The Value Iteration Network (VIN) is an end-to-end differentiable neural network architecture for planning. It exhibits strong generalization to unseen domains by incorporating a differentiable planning module that operates on a latent Markov Decision Process (MDP). However, VINs struggle to scale to long-term and large-scale planning tasks, such as navigating a $100\times 100$ maze---a task that typically requires thousands of planning steps to solve. We observe that this deficiency is due to two issues: the representation capacity of the latent MDP and the planning module's depth. We address these by augmenting the latent MDP with a dynamic transition kernel, dramatically improving its representational capacity, and, to mitigate the vanishing gradient problem, introduce an "adaptive highway loss" that constructs skip connections to improve gradient flow. We evaluate our method on 2D/3D maze navigation environments, continuous control, and the real-world Lunar rover navigation task. We find that our new method, named Dynamic Transition VIN (DT-VIN), scales to 5000 layers and solves challenging versions of the above tasks. Altogether, we believe that DT-VIN represents a concrete step forward in performing long-term large-scale planning in complex environments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题**：值迭代网络（VIN）在小型、短时规划任务中表现出色，但无法扩展到大规模（如 $100 \times 100$ 迷宫）和长时（需数千规划步）的任务。例如，在 $100 \times 100$ 迷宫中，原版 VIN 的成功率低于 40%；在 $35 \times 35$ 迷宫中，当规划步数超过 60 时，成功率为 0%。
- **背景**：VIN 通过一个可微分的规划模块（在潜在 MDP 上进行值迭代）实现了跨域泛化，但其潜在 MDP 的表征能力和规划模块的深度限制了其规模扩展。
- **整体含义**：本文旨在系统性修正 VIN 架构的缺陷，使其能够进行大规模长时规划，从而推动可微规划网络在实际复杂环境中的应用。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：同时增强潜在 MDP 的表征能力和规划模块的深度，以解决 VIN 的规模瓶颈。
- **关键技术细节（DT-VIN）**：
  - **动态转移核（Dynamic Transition Kernel）**：
    - 原版 VIN 使用与潜在状态和观测无关的固定转移核 $T_{\text{inv}} \in \mathbb{R}^{|\mathcal{A}| \times F \times F}$。
    - DT-VIN 使用**潜在状态-动态**和**观测-动态**的完全动态转移核 $T_{\text{dyn}} \in \mathbb{R}^{M \times M \times |\mathcal{A}| \times F \times F}$，由可学习的 CNN 模块 $f_T(x)$ 生成，使得每个潜在状态和每个观测都能拥有不同的转移概率。
    - 转移核在每个潜在状态上施加 softmax 归一化，确保梯度稳定。
    - 增强后的值迭代更新公式为：$V^{(n)}_{i,j} = \max_a \sum_{i',j'} T^{\text{dyn}}_{i,j,a,i',j'} \left( R_{i-i',j-j'} + V^{(n-1)}_{i-i',j-j'} \right)$。
  - **自适应高速损失（Adaptive Highway Loss）**：
    - 为缓解深层网络中的梯度消失问题，设计一种跳过连接方式，将中间层的输出直接连接到最终损失。
    - 具体公式：$L(\theta) = \frac{1}{K|\mathcal{D}|} \sum_{(x,y,l)\in\mathcal{D}} \sum_{1 \le n \le N} \mathbb{1}_{\{n \ge l\}} \mathbb{1}_{\{n \bmod J = 0\}} \ell\left( f^\pi(V^{(n)}(x)), y \right)$。其中 $l$ 是专家路径长度，$J$ 是跳跃超参数（默认 10）。
    - 只对层数 $n \ge l$ 施加损失，避免过早监督；只在 $n \bmod J = 0$ 的层上计算，降低计算开销。
    - 推断时移除这些辅助损失，保持值迭代结构完整。
  - **整体架构**：DT-VIN = 动态转移核 + 自适应高速损失，训练深度可达 5000 层，支持 1800 规划步。

## 3. 实验设计：数据集、场景、基准方法

- **数据集与场景**：
  - **2D 迷宫导航**：$15 \times 15$, $35 \times 35$, $100 \times 100$ 大小的随机迷宫，任务是从起点导航到终点。训练集 25000 个迷宫，验证集 5000，测试集 5000。评估指标：**成功率（SR）** 和 **最优率（OR）**（路径是否相对最优）。
  - **3D ViZDoom 导航**：使用第一人称 RGB 视图预测迷宫地图，然后在预测地图上规划。$35 \times 35$ 3D 迷宫。
  - **连续控制**：Point Maze 和 Ant Maze（D4RL 数据集），训练时用固定 $9 \times 12$ 迷宫，测试时面对 $35 \times 35$ 和 $100 \times 100$ 更大更复杂的迷宫（需强泛化）。
  - **月球车导航（Rover Navigation）**：基于 Apollo 17 着陆点的地形图像（0.5m/像素分辨率的正射影像），需在没有高程数据的情况下从图像中规划路径。图像尺寸 $270\times270$, $450\times450$, $630\times630$。
- **基准方法**：
  - VIN（Tamar et al., 2016）
  - GPPN（Lee et al., 2018）
  - Highway VIN（Wang et al., 2024a）
  - 部分场景还对比了 CNN+A*（传统规划基线）。
- **评价指标**：成功率（SR）、最优率（OR）、交叉熵损失、梯度范数等。

## 4. 资源与算力

- 论文附录 G 提供了详细的算力统计，但未明确指定使用的 GPU 总数或集群规模，主要给出单个实验的 GPU 消耗：
  - 在 $100 \times 100$ 迷宫中，使用 **5000 层** DT-VIN 训练 90 个 epoch：GPU 内存约 61.2 GB，训练时间约 97 小时（单卡）。
  - 对比：VIN 5000 层需 35 GB / 36 小时；GPPN 需 710 GB / 31 小时（显存爆炸，需多卡）；Highway VIN 需 111 GB / 112 小时。
  - 所有实验在 **NVIDIA A100 GPU** 上运行。
  - 未明确说明使用的 GPU 数量（推测为单卡或多卡并行，但给出的是单卡 GPU hours）。例如 DT-VIN 5000 层 GPU hours 为 97。

## 5. 实验数量与充分性

- **实验组数**：相当充分，覆盖：
  - 3 种迷宫尺寸 × 多种深度（30/100/300/600/5000）的主实验；
  - 3D 迷宫、连续控制（Point/Ant Maze × 2 种尺寸）、月球车（3 种图像尺寸）；
  - 大量消融实验：动态核变体（完全固定 / 仅观测动态 / 仅状态动态 / 完全动态）、softmax 操作、自适应高速损失变体（无、全连接、单层连接、层间残差连接）、深度影响、不同转移类型（Differential Drive / Moore）、噪声迷宫、数据集大小减半、不同跳跃超参数 J、真实长度 vs 估计长度等。
  - 每个算法通常运行 3 个随机种子取均值和标准差（论文指出低标准差足够可靠）。
- **充分性与公平性**：
  - 在训练测试集划分上保障无重叠（不同障碍布局独立），测试集对基线公平。
  - 每个方法都选取最佳深度（论文明确给出选择方法）。DT-VIN 在所有深度和场景下均优于基线，差异显著。
  - 消融实验完整，证明了每个组件的必要性。
  - 不足：未在更广泛任务（如 Atari、机器人操控）上测试，仅聚焦于迷宫类规划场景；未与最新扩散规划器（如 Diffusion Policy）直接比较（论文在相关工作提及但未实验）。

## 6. 论文的主要结论与发现

- DT-VIN 通过动态转移核和自适应高速损失，成功将 VIN 扩展到 **5000 层**，能够解决 $100 \times 100$ 迷宫中最大 1800 步的规划任务。
- 在 2D/3D 迷宫、连续控制、月球车导航等任务中，DT-VIN 的成功率和最优率均**显著优于所有基线**（VIN、GPPN、Highway VIN、CNN+A*）。
- 深度增加显著提升长期规划能力（消融图 7(c)）。动态核比固定核在长路径和高障碍密度下性能差距加大（图 6）。
- 自适应高速损失比无损失、全损失、单层损失、层间残差连接都更有效，且可使梯度范数更稳定（图 7(b)）。
- 软最大操作对训练稳定性至关重要，否则梯度爆炸（图 7(a)）。
- DT-VIN 在数据集缩减至 50% 时仍保持优异性能（降幅 < 4%），而基线降幅达 12%~45%，表明其更强的样本效率。
- 总体结论：DT-VIN 代表了在复杂环境中执行长期大规模规划的切实步骤。

## 7. 优点：方法或实验设计上的亮点

- **模型设计**：
  - 动态转移核直观且参数高效（仅需 $|\mathcal{A}| F'^2 F^2$ 个额外参数，$F=3, F'=3$ 即可表现优异），显著增强表征能力而不显著增加训练成本。
  - 自适应高速损失简单易实现，无需修改网络主体，且仅在部分层添加辅助损失，计算开销可控。
  - 通过跳步 $J$ 进一步降低复杂度；可自适应任务难度（根据路径长度 $l$ 选择监督深度）。
- **实验设计**：
  - 在多个规模（15/35/100）和多种动作空间（离散/连续）上验证，涵盖了无噪声和噪声输入、3D 感知、真实地形图像等不同复杂度。
  - 消融分析全面，梯度范数和损失曲线提供深入了解训练动态。
  - 与 GPPN、Highway VIN 等强基线公平对比，每方法选择最佳深度。
  - 将离线数据集（D4RL）用于连续控制，并在更大、未见过的迷宫上测试泛化，增加了挑战性。

## 8. 不足与局限

- **计算资源需求高**：虽然比 GPPN 和 Highway VIN 在相同层数下更省显存，但 5000 层 DT-VIN 仍需 61.2 GB 显存和 97 小时训练时间，对一般实验室门槛较高。
- **任务覆盖有限**：仅在迷宫类（2D/3D）、连续控制和月球车导航上验证，未在更通用环境（如室内导航、机器人操控、游戏）或更高维观测（如真实照片）上测试。
- **没有与最新扩散规划器比较**：论文提到扩散规划器（Diffusion Planner）是互补方法，但未在相同设定下对比实验。
- **路径长度 $l$ 要求已知**：自适应高速损失需要 $l$（最短路径长度）。论文实验表明使用启发式估测（L1 距离）或次优轨迹仍可，但可能在实际未知场景中引入额外误差。
- **潜在的偏差风险**：所有实验基于仿真或固定数据集，真实世界噪声分布可能与模拟不同，泛化至动态环境有待验证。
- **与值迭代理论对齐**：尽管 DT-VIN 保持了值迭代的结构，但动态核的引入破坏了严格的理论收敛保证（原 VIN 通过固定卷积核模拟 VI），论文未提供新的收敛证明。

（完）
