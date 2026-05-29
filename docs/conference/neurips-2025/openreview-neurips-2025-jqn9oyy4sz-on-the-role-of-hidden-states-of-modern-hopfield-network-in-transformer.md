---
title: On the Role of Hidden States of Modern Hopfield Network in Transformer
title_zh: 现代Hopfield网络隐藏状态在Transformer中的作用
authors: "Tsubasa Masumura, Masato Taki"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=jQn9oYY4sz"
tags: ["query:neural-arch"]
score: 7.0
evidence: 提出现代Hopfield注意力，一种新的注意力变体
tldr: 现代Hopfield网络与Transformer注意力已被证明有联系，但现有近似忽略隐藏状态。本文超越近似，引入MHN隐藏状态到注意力中，提出现代Hopfield注意力（MHA）。该机制增强了记忆能力，在长序列任务上表现更优，为注意力架构创新提供理论依据。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqn9oyy4sz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1238, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jqn9oyy4sz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1403, \"height\": 726, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqn9oyy4sz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1038, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqn9oyy4sz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 639, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqn9oyy4sz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 979, \"height\": 545, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqn9oyy4sz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1028, \"height\": 114, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqn9oyy4sz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 642, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqn9oyy4sz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1378, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jqn9oyy4sz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 911, \"height\": 309, \"label\": \"Table\"}]"
motivation: 现有研究仅近似关联Hopfield网络与注意力，忽略了隐藏状态的作用。
method: 将现代Hopfield网络的隐藏状态融入自注意力，提出MHA机制。
result: MHA在长序列任务上提升记忆能力和性能。
conclusion: 揭示了隐藏状态的重要性，提出更通用的注意力变体。
---

## Abstract
Associative memory models based on Hopfield networks and self-attention based on key-value mechanisms have been popular approaches in the study of memory mechanisms in deep learning. It has been pointed out that the state update rule of the modern Hopfield network (MHN) in the adiabatic approximation is in agreement with the self-attention layer of Transformer. In this paper, we go beyond this approximation and investigate the relationship between MHN and self-attention. Our results show that the correspondence between Hopfield networks and Transformers can be established in a more generalized form by adding a new variable, the hidden state derived from the MHN, to self-attention. This new attention mechanism, modern Hopfield attention (MHA), allows the inheritance of attention scores from the input layer of the Transformer to the output layer, which greatly improves the nature of attention weights. In particular, we show both theoretically and empirically that MHA hidden states significantly improve serious problem of deep Transformers known as rank collapse and token uniformity. We also confirm that MHA can systematically improve accuracy without adding training parameters to the Vision Transformer or GPT. Our results provide a new case in which Hopfield networks can be a useful perspective for improving the Transformer architecture.

---

## 论文详细总结（自动生成）

# 现代Hopfield网络隐藏状态在Transformer中的作用——论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：已有研究表明，现代Hopfield网络（MHN）在绝热近似下的状态更新规则与Transformer的自注意力机制完全一致。然而，这种近似忽略了MHN中隐藏状态的动力学过程。
- **核心问题**：超越绝热近似，将MHN的隐藏状态引入Transformer，能否建立更一般化的对应关系，并改善Transformer的性能？
- **整体含义**：维持隐藏状态动力学可以衍生出一种新的注意力机制——现代Hopfield注意力（MHA），它能跨层传递注意力分数信息，从而显著缓解深度Transformer中的秩坍塌（rank collapse）和令牌均匀性问题（token uniformity），并提升多种任务表现。

## 2. 论文提出的方法论
- **核心思想**：从MHN的离散化时间演化方程出发，不取绝热极限，保留隐藏状态h的动态，并将其映射到Transformer的自注意力层中，形成带有隐藏状态的新注意力变体MHA。
- **关键技术细节**：
  - MHN的离散化更新规则（式4）：  
    \( x_{n+1} = \alpha x_n + (1-\alpha) f(h_n) W_1^\top \)  
    \( h_{n+1} = \alpha' h_n + (1-\alpha') g(x_n) W_2 \)
  - 选用合适的拉格朗日函数（模型B）得到f=softmax，g=identity。
  - 翻译为Transformer符号后得到MHA核心公式（式10）：  
    \( x_{n+1} = \alpha x_n + (1-\alpha) \text{softmax}(h_n) V_n \)  
    \( h_n = \alpha' h_{n-1} + (1-\alpha') q_n K_n^\top \)
  - 隐藏状态h是注意力得分\( QK^\top \)的指数移动平均，并直接用于计算softmax权重；α和α'是超参数（论文中通常取α=α'，并设为0.5或0.7）。
- **算法流程**：每一层先更新隐藏状态h（累积历史注意力得分），然后用该隐藏状态计算注意力输出，再与输入x进行残差连接（权重由α控制）。MHA不引入额外可训练参数，仅增加少量计算（\( O(T^2) \) vs 原始\( O(dT^2) \)）。

## 3. 实验设计
- **数据集与场景**：
  - 文本生成：WikiText103、CNN DailyMail、BookCorpus（用于GPT-2和LLaMA架构）。
  - 图像分类：CIFAR10、CIFAR100、ImageNet-1k（用于ViT系列）。
  - 下游任务迁移（线性探测）：Oxford Flowers 102、Food-101、Stanford Dogs、Stanford Cars。
- **基准模型**：标准Transformer自注意力（Self-Attention）作为基线，与替换为MHA的对应架构在完全相同设置下从零训练比较。
- **对比方法**：仅对比自身基线，未与其他高级注意力变体（如Reformer、Linformer等）对比，但重点在于证明MHA相对于标准自注意力的系统性提升。

## 4. 资源与算力
- 文中明确提及使用最多8张A100 GPU进行实验。
- 未报告具体训练时长或总计算量，但指出训练成本较高（因此未提供误差棒）。

## 5. 实验数量与充分性
- **实验组数量**：
  - GPT-2 Small/Medium共2组（perplexity对比）。
  - LLaMA在3个数据集上对比（3组）。
  - ViT-Tiny/Small/Base/Large在CIFAR10/100共8组（含α=0.5和0.7两个版本）。
  - ViT-B在ImageNet-1k上1组。
  - 下游迁移4组。
  - 超参数α/α'消融实验（变动α或α'的网格搜索）1组。
  - 无skip-connection网络的深度影响实验（不同深度对比）1组。
  - 秩坍塌可视化（余弦相似度小提琴图）2组。
- **充分性**：覆盖多种模型规模（从5.5M到303M参数）、多种任务（文本生成、图像分类、迁移学习）、关键消融（α/α'影响、深度影响）。实验设置公平（相同超参数、训练配置）。但缺乏与已有注意力改进方法的直接对比，也缺乏在更大规模模型（如GPT-3）上的验证。

## 6. 论文的主要结论与发现
- MHA在不增加参数的情况下，显著提升了GPT-2、LLaMA、ViT在多个数据集上的性能（如GPT-2 Medium在WikiText-103上perplexity从20.85降至19.61）。
- 理论分析和实验均证明，MHA的隐藏状态能有效抑制深度Transformer的秩坍塌——证明了在无skip-connection网络中由指数衰减变为线性衰减；在有skip-connection的完整模型中，令牌余弦相似度峰值从1.0大幅降低，令牌多样性得到保留。
- 隐藏状态的两个超参数α和α'协同作用，缺一不可；简单选择α=α'=0.5或0.7即可取得稳定改善。

## 7. 优点
- **理论创新**：从MHN动力学出发，自然导出一种新的注意力机制，为注意力架构设计提供了新的理论视角。
- **实用性**：无需额外参数，计算开销极小，可无缝替换现有自注意力层，便于在已有模型上应用。
- **实验扎实**：覆盖多种任务、模型尺寸、消融实验，且可视化验证了秩坍塌的缓解。
- **效果突出**：在几乎所有对比中均优于基线，且提升幅度在合理范围内（非微调噪声）。

## 8. 不足与局限
- **实验范围限制**：仅在中型模型（最大303M参数）上验证，未在百亿/千亿参数规模的LLM上测试，其可扩展性存疑。
- **缺乏与先进注意力变体的对比**：未与已有的改进如RealFormer、RevViT、DeepViT等比较，难以评估MHA的相对优势。
- **超参数敏感性**：α和α'需要手动设定，论文仅在有限网格搜索中尝试，未提供自动选择策略。
- **主要关注文本和图像**：仅在文本生成和图像分类上评估，未涉及语音、多模态等其他领域。
- **理论假设**：理论分析基于简化模型（无FFN、无残差连接等），实际架构中效果可能受其他组件影响。
- **社会影响**：未讨论潜在负面应用，但作为基础研究影响较小。

（完）
