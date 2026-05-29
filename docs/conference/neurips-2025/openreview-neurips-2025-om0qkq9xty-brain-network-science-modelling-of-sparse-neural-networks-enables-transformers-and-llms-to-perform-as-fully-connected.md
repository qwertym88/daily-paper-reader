---
title: Brain network science modelling of sparse neural networks enables Transformers and LLMs to perform as fully connected
title_zh: 脑网络科学建模稀疏神经网络使Transformer和LLM表现如全连接网络
authors: "Yingtao Zhang, Diego Cerretti, Jialin Zhao, Wenjing Wu, Ziheng Liao, Umberto Michieli, Carlo Vittorio Cannistraci"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=OM0Qkq9xtY"
tags: ["query:neural-arch"]
score: 7.0
evidence: 脑启发的动态稀疏训练方法用于高效网络优化
tldr: 动态稀疏训练可降低计算成本，但高稀疏度下性能下降。本文借鉴脑网络科学，采用Cannistraci-Hebb训练（CHT）进行拓扑驱动的连接生长，在Transformer等模型上实现超稀疏连接且性能不降。该方法有效优化网络结构，兼顾效率与精度。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1411, \"height\": 711, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 726, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1422, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1381, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1309, \"height\": 928, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1320, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1445, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1410, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1413, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1429, \"height\": 590, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 732, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-om0qkq9xty/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1396, \"height\": 568, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 720, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1414, \"height\": 516, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1301, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1182, \"height\": 729, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1409, \"height\": 651, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1216, \"height\": 516, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1442, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 458, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 576, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1220, \"height\": 499, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 608, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1380, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1036, \"height\": 537, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 946, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1104, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 587, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 754, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1473, \"height\": 134, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-om0qkq9xty/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1449, \"height\": 561, \"label\": \"Table\"}]"
motivation: 高稀疏度下动态稀疏训练难以维持性能。
method: 采用Cannistraci-Hebb训练（CHT）进行无梯度、拓扑驱动的连接再生。
result: 在超稀疏连接下达到全连接性能，降低计算开销。
conclusion: 脑启发方法有效优化稀疏网络结构，兼顾效率与精度。
---

## Abstract
This study aims to enlarge our current knowledge on the application of brain-inspired network science principles for training artificial neural networks (ANNs) with sparse connectivity. Dynamic sparse training (DST) emulates the synaptic turnover of real brain networks, reducing the computational demands of training and inference in ANNs. However, existing DST methods face difficulties in maintaining peak performance at high connectivity sparsity levels. The Cannistraci-Hebb training (CHT) is a brain-inspired method that is used in DST for growing synaptic connectivity in sparse neural networks. CHT leverages a gradient-free, topology-driven link regrowth mechanism, which has been shown to achieve ultra-sparse (1\% connectivity or lower) advantage across various tasks compared to fully connected networks. Yet, CHT suffers two main drawbacks: (i) its time complexity is $\mathcal{O}(N\cdot d^3)$- N node network size, d node degree - hence it can be efficiently applied only to ultra-sparse networks. (ii) it rigidly selects top link prediction scores, which is inappropriate for the early training epochs, when the network topology presents many unreliable connections. Here, we design the first brain-inspired network model - termed bipartite receptive field (BRF) - to initialize the connectivity of sparse artificial neural networks. Then, we propose a matrix multiplication GPU-friendly approximation of the CH link predictor, which reduces the computational complexity to $\mathcal{O}(N^3)$, enabling a fast implementation of link prediction in large-scale models. Moreover, we introduce the Cannistraci-Hebb training soft rule (CHTs), which adopts a flexible strategy for sampling connections in both link removal and regrowth, balancing the exploration and exploitation of network topology. Additionally, we propose a sigmoid-based gradual density decay strategy, leading to an advanced framework referred to as CHTss. Empirical results show that BRF offers performance advantages over previous network science models. Using 1\% of connections, CHTs outperforms fully connected networks in MLP architectures on visual classification tasks, compressing some networks to less than 30\% of the nodes. Using 5\% of the connections, CHTss outperforms fully connected networks in two Transformer-based machine translation tasks. Finally, with only 30\% of the connections, both CHTs and CHTss achieve superior performance over other dynamic sparse training methods, and perform on par with—or even surpass—their fully connected counterparts in language modeling across various sparsity levels within the LLaMA model family. The code is available at: https://github.com/biomedical-cybernetics/Cannistraci-Hebb-Training-Soft-Rule-.

---

## 论文详细总结（自动生成）

### 论文中文总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）
- **动机**：深度神经网络（尤其是 Transformer 和 LLM）依赖全连接层，参数随神经元数量平方增长，导致高计算和存储开销。生物大脑具有稀疏连接特性，动态稀疏训练（DST）模拟大脑突触可塑性，但现有 DST 方法在高稀疏度（如 99% 连接）下性能显著下降。
- **背景**：Cannistraci-Hebb 训练（CHT）是一种脑启发的无梯度拓扑驱动连接生长方法，能在超稀疏（≤1% 连接）下取得优势，但有两个主要缺陷：① 时间复杂度为 O(N·d³)，仅适用于超稀疏网络；② 刚性选择最高链接预测分数，在早期训练中易陷入“表位拓扑局部极小值”（ELM），即移除和再生的链接高度重叠。
- **目标**：本文旨在克服 CHT 的局限性，提出更高效、灵活的脑启发 DST 框架，使稀疏神经网络在大规模模型（Transformer、LLaMA）上达到或超越全连接性能。

#### 2. 论文提出的方法论：核心思想、关键技术细节
- **核心思想**：融合脑网络科学的拓扑智能与软采样策略，实现高效稀疏训练。
- **关键技术细节**：
  - **二分感受野（BRF）网络初始化模型**：模拟大脑感受野的空间局部性，通过参数 r ∈ [0,1] 控制连接的对角聚集程度（r 小则局部密集，r=1 则随机），并保留输出层度分布的可控性（固定或均匀）。
  - **节点级 CH 链接预测器（CH2-L3n）**：将原路径级（CH3-L3p）复杂度从 O(N·d³) 降至 O(N³)，支持 GPU 矩阵乘法加速。公式为：  
    `CH2-L3n(u,v) = Σ_{z∈L3} (di⁺_z / de⁺_z)`，其中 di⁺_z 和 de⁺_z 分别为节点 z 的内部/外部局部社区链接数。
  - **软规则移除与再生（CHTs）**：移除阶段使用加权幅度（WM）或相对重要性（RI）的软采样（多项式分布，温度 δ 从 0.5 递增至 0.9）；再生阶段基于 CH2-L3n 得分进行软采样，避免 ELM。
  - **Sigmoid 渐进密度衰减（CHTss）**：采用 Sigmoid 函数控制稀疏度从初始值平滑过渡到目标值，比立方衰减更平稳，提升训练稳定性。
  - **网络渗流调整**：移除无连接节点并修复残余链接，适配 Transformer 注意力层结构。
- **算法流程**（以单次迭代为例）：BRF 初始化 → 软移除 → 神经元除杂 → 链接修复 → 软再生 → 重复至训练结束。

#### 3. 实验设计
- **数据集与场景**：
  - **MLP 图像分类**：MNIST、Fashion-MNIST、EMNIST、CIFAR-10（99% 稀疏度）。
  - **Transformer 机器翻译**：Multi30k en-de、IWSLT14 en-de、WMT17 en-de（95% 和 90% 稀疏度）。
  - **LLaMA 语言建模**：OpenWebText（70%、80%、90%、95% 稀疏度），模型规模 60M、130M、1B。
  - **零样本评测**：GLUE 和 SuperGLUE（LLaMA-1B）。
- **Benchmark**：全连接网络作为基线。
- **对比方法**：
  - 固定稀疏度 DST：SET、RigL、CHT、CHTs。
  - 密度衰减 DST：MEST(EM&S)、GMP、GraNet、CHTss。
- **评价指标**：准确率（ACC）、BLEU、困惑度（PPL）、活跃神经元渗透率（ANP）。

#### 4. 资源与算力
- **硬件**：NVIDIA A100 80GB GPU。
  - MLP 和 Transformer：单卡训练。
  - LLaMA 模型：8 卡并行训练。
- **训练时长**：文中仅给出部分示例（如 CHTss 在 Multi30K 上 0.25 小时/epoch，IWSLT 上 1.5 小时/epoch），未提供完整训练总时间。总体算力需求较大，但未详细量化。

#### 5. 实验数量与充分性
- **实验数量**：涵盖 4 个图像分类数据集、3 个机器翻译数据集、1 个语言建模数据集（含 3 种模型规模）、1 个零样本评测；此外包含多种消融实验（BRF 参数 r、移除策略 δ、密度衰减形状、ζ 分数、软/硬采样对比等）。
- **充分性**：充分且客观。多数实验报告 3 次重复的标准误差；对比方法全面（包括 SOTA 的 RigL、GraNet 等）；在 LLaMA-1B 等大模型上进行了验证，证明了可扩展性。

#### 6. 论文的主要结论与发现
- **MLP 上**：CHTs 在 99% 稀疏度下超越全连接网络（CIFAR-10 提升 11%+），ANP 显著降低。
- **Transformer 上**：CHTss 在 5% 密度下超越全连接翻译模型（Multi30K BLEU 32.03 vs 全连 31.38）。
- **LLaMA 上**：
  - CHTs/CHTss 在 30% 连接下达到或超越全连接困惑度（LLaMA-1B 70% 稀疏度 CHTs 14.53 vs 全连 14.62）。
  - 在低精度（bfloat16）下，基于梯度的 RigL/GraNet 性能大幅下降，而 CHTs/CHTss 保持稳健。
  - 零样本 GLUE/SuperGLUE 上，70% 稀疏度模型与全连相当，但高稀疏度下 MCC 下降。
- **算法优势**：脑启发拓扑初始化（BRF）优于 BSW/BSF；软采样平衡探索-利用；Sigmoid 衰减优于立方衰减。

#### 7. 优点
- **高效性**：节点级 CH 预测器将复杂度从 O(N·d³) 降至 O(N³)，使大规模模型稀疏训练可行。
- **鲁棒性**：无梯度再生避免对梯度质量的依赖，在低精度训练中更可靠。
- **灵活性**：移除/再生均采用可调温度的软采样，避免陷于 ELM；BRF 初始化通过 r 控制空间随机性，适用不同场景。
- **广泛验证**：从 MLP 到 Transformers 再到 LLaMA-1B，涵盖多种任务和稀疏度，实验设计严谨（含消融、敏感性、标准误差）。

#### 8. 不足与局限
- **硬件加速**：非结构化稀疏在训练阶段的硬件加速尚未普及，论文未提供实际训练速度对比。
- **自动调参**：软采样温度 δ 手动设定（线性递增），未探索自适应方法。
- **零样本性能**：高稀疏度（95%）下 LLaMA-1B 零样本 MCC 为负，说明极端稀疏影响泛化，训练不足可能是原因。
- **计算资源消耗**：虽降低复杂度，但大规模模型仍需 8×A100，训练成本仍高。
- **局限声明**：作者在附录中指出未来需测试更大模型（如 LLaMA-7B），且当前未实现自动温度调节。

（完）
