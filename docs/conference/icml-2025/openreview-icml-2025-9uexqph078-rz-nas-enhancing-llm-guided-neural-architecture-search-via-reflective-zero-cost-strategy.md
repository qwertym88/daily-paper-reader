---
title: "RZ-NAS: Enhancing LLM-guided Neural Architecture Search via Reflective Zero-Cost Strategy"
title_zh: RZ-NAS：通过反射零成本策略增强LLM引导的神经架构搜索
authors: "Zipeng Ji, Guanghui Zhu, Chunfeng Yuan, Yihua Huang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=9UExQpH078"
tags: ["query:neural-arch"]
score: 9.0
evidence: 基于反射零成本策略的LLM引导神经架构搜索
tldr: 针对现有LLM引导的神经架构搜索存在搜索空间有限、效率低、性能不理想等问题，本文提出RZ-NAS方法，通过引入反射机制和零成本指标，使LLM能更高效地搜索高性能架构。在多个NAS基准和下游任务上，RZ-NAS取得了竞争力强的性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-9uexqph078/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1756, \"height\": 870, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9uexqph078/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1514, \"height\": 1398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9uexqph078/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 834, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9uexqph078/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9uexqph078/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1720, \"height\": 1338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9uexqph078/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1666, \"height\": 422, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1619, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1448, \"height\": 726, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 751, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 844, \"height\": 685, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1337, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1614, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1781, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-9uexqph078/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1773, \"height\": 304, \"label\": \"Table\"}]"
motivation: LLM-to-NAS方法受限于搜索空间和效率问题。
method: 提出RZ-NAS，结合反思提示和训练无关指标，利用LLM生成架构。
result: 在标准NAS基准上取得更优或相当性能，提升搜索效率。
conclusion: 反射零成本策略有效增强LLM在NAS中的能力。
---

## Abstract
LLM-to-NAS is a promising field at the intersection of Large Language Models (LLMs) and Neural Architecture Search (NAS), as recent research has explored the potential of architecture generation leveraging LLMs on multiple search spaces. However, the existing LLM-to-NAS methods face the challenges of limited search spaces, time-cost search efficiency, and uncompetitive performance across standard NAS benchmarks and multiple downstream tasks. In this work, we propose the Reflective Zero-cost NAS (RZ-NAS) method that can search NAS architectures with humanoid reflections and training-free metrics to elicit the power of LLMs. We rethink LLMs’ roles in NAS in current work and design a structured, prompt-based to comprehensively understand the search tasks and architectures from both text and code levels. By integrating LLM reflection modules, we use LLM-generated feedback to provide linguistic guidance within architecture optimization. RZ-NAS enables effective search within both micro and macro search spaces without extensive time cost, achieving SOTA performance across multiple downstream tasks.

---

## 论文详细总结（自动生成）

### 论文总结：RZ-NAS: Enhancing LLM-guided Neural Architecture Search via Reflective Zero-Cost Strategy

#### 1. 核心问题与整体含义（研究动机和背景）
- 神经架构搜索（NAS）对高性能神经网络设计至关重要，但传统NAS计算开销大。
- 近期利用大语言模型（LLM）引导NAS（LLM-to-NAS）的方法面临三大挑战：
  - 搜索空间有限（多为微搜索空间）
  - 搜索效率低（需全训练评估架构）
  - 在标准NAS基准和下游任务上性能不具竞争力
- 现有方法主要依赖文本提示直接生成架构，存在**可重复性差**（LLM随机输出）和**可解释性弱**（缺乏设计依据）的问题。
- 本文旨在设计一种新型LLM-to-NAS算法，使LLM能同时理解文本和代码层面的架构信息，利用零成本代理加速评估，并通过反射机制实现自适应优化。

#### 2. 方法论
- **核心思想**：将零成本（Zero-Cost）代理与LLM的反射机制耦合，实现智能、高效的架构变异与搜索。
- **关键技术细节**：
  - **结构化提示模板**：
    - 系统提示：定义LLM角色、搜索空间描述、网络构建描述、零成本代理计算代码及反射模块提示。
    - 上下文示例：提供一次完整变异及推理步骤。
    - 用户提示：以JSON格式输入当前架构、代理类型和得分。
    - 同时提供文本级和代码级描述，增强LLM对架构的理解。
  - **LLM引导变异**：
    - 从种群中随机选择架构，LLM根据提示替换操作符（文本级变异），生成新架构基因型。
    - 支持微搜索空间（DARTS风格）和宏搜索空间（MobileNet风格）。
  - **架构验证与零成本评估**：
    - 检查架构有效性（层数限制、FLOPs预算等），无效架构跳过并反馈异常。
    - 使用预定义的零成本代理（如Gradnorm、Synflow、Zen-Score、ZiCo等）计算得分，避免完整训练。
  - **LLM反射模块**：
    - 内反射模块（系统提示中内置“思考如何生成更好变异”）
    - 外反射模块：输入变异前后架构、得分及异常信息，LLM生成结构化建议用于后续迭代。
  - **种群更新**：按零成本得分排序，保留前N个架构，淘汰最差。
- **算法流程**（Algorithm 1）：初始化种群 → 迭代T次（每次：随机选择、LLM变异、验证、计算得分、加入种群并淘汰最低分、反射）→ 返回最高分架构。

#### 3. 实验设计
- **数据集**：CIFAR-10/100、ImageNet-16-120、ImageNet（分类）、COCO（目标检测）
- **搜索空间**：
  - NAS-Bench-201（微细胞搜索空间）
  - DARTS搜索空间（CIFAR-10/100）
  - MobileNetV2搜索空间（ImageNet，不同FLOPs预算：450M/600M/1000M）
  - 宏搜索空间（COCO目标检测）
- **基准对比方法**：
  - 传统NAS：DARTS、SNAS、PC-DARTS、DrNAS等
  - LLM-to-NAS：GPT-NAS、GENIUS、LLMatic、EvoPrompting、FL-NAS
  - 零成本NAS：GraSP、Gradnorm、Synflow、Zen-NAS、ZiCo、MAE-DET
- **评估指标**：测试/验证准确率、零成本代理与真实精度的相关性（Kendall τ、Spearman φ）、mAP（目标检测）

#### 4. 资源与算力
- 论文未明确指定GPU型号及数量，但给出了搜索成本：
  - 在CIFAR-10上，RZ-NAS搜索成本约**0.03 GPU天**，而传统NAS需1~225 GPU天。
  - 在ImageNet（450M FLOPs预算）下，搜索成本约**0.4 GPU天**（ZiCo），远低于多阶段NAS（3800 GPU天）。
  - 每个代理（每搜索空间）总API调用成本约**75美元**（1500次迭代，GPT-4o模型，温度采样自[0.2,1.0]）。
- 预训练/训练阶段未说明具体硬件配置（如V100/A100），但强调搜索阶段无需完整训练。

#### 5. 实验数量与充分性
- 实验充分且系统：覆盖**5个数据集**、**4种搜索空间**、**5类零成本代理**、**3种下游任务**（分类+检测）。
- **消融实验**（Ablation）：
  - 去除不同提示组件（上下文示例、反射模块、代码描述、文本描述）
  - 不同架构选择策略（随机 vs 最高分）
  - 不同LLM（GPT-4o、LLaMA 3.1、Claude 3.5）
  - 不同温度策略（固定 vs 均匀采样）
  - 时间对比：可视化测试准确率随时间变化
- 实验设置公平：与现有方法采用完全相同搜索空间和训练配置，每种方法重复3次取均值±标准差。
- 客观性：零成本得分由代码计算（非LLM预测），避免幻觉。

#### 6. 主要结论与发现
- RZ-NAS在所有零成本代理上显著提升性能（测试准确率、相关性系数），**超越现有所有LLM-to-NAS方法**，并在**多个基准上达到SOTA**（如NAS-Bench-201 CIFAR-10：93.47% vs Synflow原始93.48%，但方差更优；ImageNet 450M FLOPs：79.0% Top-1 vs DONNA 78.0%）。
- 搜索成本极低（0.03~0.4 GPU天），比传统NAS快数十至数千倍。
- 反射模块可降低异常率（从7%降至2%），提升搜索稳定性。
- 结构化提示（代码+文本）不可或缺，仅代码或仅文本均导致性能下降。
- 随机选择策略与最高分选择策略性能相当，且能维持种群多样性。

#### 7. 优点
- **创新框架**：首次将零成本代理与LLM反射机制有机结合，实现免训练高效搜索。
- **通用灵活**：支持微/宏搜索空间、多种零成本代理、不同下游任务，易于扩展。
- **提示设计精巧**：同时利用文本和代码级理解，使LLM深入理解NAS任务。
- **反射闭环**：内外反射模块形成反馈机制，动态优化变异策略。
- **实验全面**：横跨多基准、多任务、多代理，消融实验覆盖主要设计选择，结论可靠。
- **效率极高**：在保持或超越SOTA性能的前提下，搜索成本降低1~3个数量级。

#### 8. 不足与局限
- **LLM依赖性与成本**：当前基于GPT-4o，虽然搜索成本低，但API调用仍产生费用（~$75/代理）；未充分探索更廉价的本地模型（但消融实验中提及LLaMA 3.1和Claude 3.5，性能略逊）。
- **未涵盖大型搜索空间**：论文测试空间最大为MobileNetV2级别，未涉及Transformer或更大模型（如ViT、GPT）的搜索。
- **消融实验细节**：反射模块的具体提示内容仅附录给出一个示例，未分析不同反射策略的影响（如反馈长度、温度）。
- **跨领域验证有限**：目标检测仅基于COCO的ResNet风格骨干，未涉及语义分割、NLP等任务。
- **零成本代理选择**：评估仍依赖预定义代理，不同代理对任务敏感性未知，可能需人工调参。
- **可复现性**：依赖LLM的非确定性输出，虽采用温度采样和随机种子，但完全复现搜索结果仍具挑战。
- **隐私与安全**：提示工程涉及搜索空间代码，若敏感场景可能引发提示泄露风险（论文虽提及限制，但未深入讨论）。

（完）
