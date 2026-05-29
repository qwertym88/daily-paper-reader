---
title: "Revolutionizing Training-Free NAS: Towards Efficient Automatic Proxy Discovery via Large Language Models"
title_zh: 革命性训练-free神经架构搜索：利用大语言模型高效自动发现代理
authors: "Haidong Kang, Lihong Lin, Hanling Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=3naHyE5klE"
tags: ["query:neural-arch"]
score: 9.0
evidence: 利用大语言模型自动发现零代价代理的训练-free神经架构搜索
tldr: 本文提出利用大语言模型自动发现零代价代理的训练-free神经架构搜索方法，解决手工设计代理耗时且相关性差的问题。该方法加速了搜索过程，提升了代理与模型性能的关联度，在计算机视觉任务上展现出高效性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1019, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 616, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1112, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1451, \"height\": 1327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1455, \"height\": 1284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1457, \"height\": 1071, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1447, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1448, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1447, \"height\": 726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1430, \"height\": 828, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1446, \"height\": 762, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1449, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1170, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1165, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1455, \"height\": 1226, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3nahye5kle/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1454, \"height\": 1288, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 733, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 785, \"height\": 414, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1449, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 665, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1017, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1155, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 822, \"height\": 311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 817, \"height\": 124, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 871, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 870, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1163, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 726, \"height\": 777, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 523, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 568, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 552, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 890, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1171, \"height\": 662, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3nahye5kle/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1447, \"height\": 882, \"label\": \"Table\"}]"
motivation: 现有训练-free NAS依赖手工设计的零代价代理，费力且与性能相关性差。
method: 利用大语言模型自动生成和评估零代价代理，无需人工专家知识。
result: 自动发现的代理与模型性能相关性更高，搜索效率显著提升。
conclusion: 为训练-free NAS提供了自动化代理设计的新范式。
---

## Abstract
The success of computer vision tasks is mainly attributed to the architectural design of neural networks. This highlights the need to automatically design high-performance architectures via Neural Architecture Search (NAS). To accelerate the search process, training-free NAS is proposed, which aims to search high-performance architectures at initialization via zero-cost proxies (ZCPs). However, existing zero-cost proxies heavily rely on manual design, which is often labor-intensive and requires extensive expert knowledge. In addition, these crafted proxies often suffer from poor correlation with final model performance and high computational complexity, severely limiting NAS efficiency in real-world applications. To address those issues, this paper proposes a novel Large Language Models (LLMs)-driven $\underline{A}$utomatic $\underline{P}$roxy $\underline{D}$iscovery ($\textbf{APD}$) framework, which revolutionizes the design paradigm of ZCPs by leveraging LLMs to automatically discover optimal ZCPs for Training-Free NAS. Moreover, we utilize actor-critic based reinforcement learning to optimize prompts, enabling to generate better ZCPs in the next generation. We conduct extensive experiments on mainstream NAS benchmarks, demonstrating APD excels in both performance and efficiency. Besides, we firmly believe that our APD will dramatically benefit the deep learning community through providing novel paradigm of design algorithms via LLMs.

---

## 论文详细总结（自动生成）

# 论文《Revolutionizing Training-Free NAS: Towards Efficient Automatic Proxy Discovery via Large Language Models》详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：神经架构搜索（NAS）旨在自动设计高性能神经网络，但传统NAS计算开销巨大。训练‑free NAS通过零代价代理（ZCPs）在初始化阶段评估架构性能，从而加速搜索。然而，现有的ZCPs主要依赖手工设计，需要大量专家知识和试错，且与最终模型性能的相关性较差，限制了实际应用效率。
- **整体含义**：本文提出一种由大语言模型（LLM）驱动的自动代理发现（APD）框架，首次将LLM用于自动生成ZCPs，革新了训练‑free NAS中代理的设计范式，有望推动自动化机器学习的发展。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用LLM的生成能力自动产生ZCPs，通过actor‑critic强化学习优化提示（prompt），使LLM逐步生成与模型性能相关性更强的代理，从而实现无需人工设计的自动代理发现。
- **关键技术细节**：
  - **Proxy Candidate Generator**：LLM接收结构化提示（初始化、变异、交叉）及已有代理的上下文窗口，生成新的代理代码及其自然语言描述。
  - **Fitness Evaluator**：评估候选代理的Spearman秩相关与计算成本的加权组合，作为适应度函数。
  - **RL Evolution Scheduler**：基于actor‑critic的强化学习控制器，观察种群状态并选择操作（初始化/变异/交叉），根据适应度计算奖励，更新策略和价值函数。
  - **进化框架**：初始化种群→采样动作→生成候选→评估→更新策略→替换，迭代直到收敛。约30代即可在NAS‑Bench‑201上达到0.80以上的Spearman相关。

## 3. 实验设计：数据集、场景、基准与对比方法

- **数据集与场景**：
  - 图像识别：CIFAR‑10/100，ImageNet16‑120，ImageNet‑1k
  - 自动编码、场景分类、自监督拼图（TransNAS‑Bench‑101）
  - 分布外泛化（OoD‑ViT‑NAS‑Ti，包含ImageNet‑A/R/D等）
- **搜索空间（benchmark）**：
  - NAS‑Bench‑201（CIFAR‑10/100，ImageNet16‑120）
  - NAS‑Bench‑101（CIFAR‑10）
  - DARTS搜索空间（CIFAR‑10/100，ImageNet‑1k）
  - TransNAS‑Bench‑101‑Micro
  - OoD‑ViT‑NAS‑Ti
- **对比方法**：包括Params、FLOPs、SNIP、GraSP、SynFlow、NWOT、ZenNAS、ZiCo、AZ‑NAS、SWAP等手工ZCPs，以及多个训练‑free NAS方法。此外还对比了不同LLM（GPT‑4o、Claude 3.7等）和消融变体。

## 4. 资源与算力

- 文中未明确给出完整算力清单，但指出：
  - 在NAS‑Bench‑201上，APD约在30代（约1 GPU‑hour）内达到0.80以上Spearman相关。
  - 所有搜索在单个RTX 4090 GPU上完成。
  - DARTS搜索成本：0.004 GPU‑days（远低于现有方法）。
  - 评估时使用5次重复，每次16个随机样本。
- 总体算力：中等规模，单GPU即可高效运行。

## 5. 实验数量与充分性

- **实验组数**：涵盖了5种搜索空间、多个数据集（CIFAR‑10/100、ImageNet16‑120、ImageNet‑1k等）、3种下游任务（分类、自动编码、拼图）、分布外场景，以及7种LLM骨干的对比。
- **消融实验**：包括组件消融（有无进化、有无actor‑critic）、种群大小、折扣因子、历史窗口、actor‑critic隐藏层深度等。
- **充分性**：实验设计较为全面，覆盖了主流NAS基准和多种训练‑free NAS方法，且报告了多次独立运行的平均值和标准差（部分结果有误差条）。结论可信度高。
- **公平性**：作者尽量使用公开基准和官方代码复现对比方法，超参数设定明确，对比标准一致。

## 6. 论文的主要结论与发现

- APD在所有基准上均取得**最优或次优**的Spearman相关性与测试准确率，且计算开销显著低于现有手工ZCPs。
- 使用LLM自动发现的代理相关性远高于手工设计，尤其通过actor‑critic RL引导后，性能提升明显（比naive方法提升21.26%）。
- APD对不同LLM骨干具有鲁棒性，在多LLM上都表现出稳定的高相关。
- 在分布外场景（OoD‑ViT‑NAS）上同样表现优异，证明了泛化能力。
- APD在DARTS空间仅用0.004 GPU‑days即可超越许多需训练的NAS方法。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将LLM应用于训练‑free NAS的ZCP自动发现，改变了手工设计范式。
- **自动化**：无需专家知识，通过LLM+RL实现了代理的端到端自动生成与优化。
- **效率**：搜索成本极低（单GPU数小时），代理评估仅需一次前向传播。
- **可解释性**：代理以自然语言+代码形式输出，便于理解和复现。
- **广泛验证**：在CNN和ViT等多种搜索空间及多个数据集上进行了充分实验，包括分布外泛化测试。

## 8. 不足与局限

- **黑盒问题**：LLM内部推理过程不可见，但外层优化回路可监控和调试。
- **需要小规模真实性能数据**：适应度评估需抽样约2‑3%的架构真实精度，并非完全零标签，但成本较低。
- **上下文长度限制**：在搜索空间极大时，prompt+上下文可能超过LLM窗口，需降采样。
- **代码执行安全性**：LLM生成的代码需在沙箱中运行以防恶意或资源滥用。
- **未探讨跨架构类型泛化**：目前仅针对CNN和ViT，未覆盖RNN、GNN等。
- **消融实验细节可进一步丰富**：例如不同LLM温度或更多超参数的影响。

（完）
