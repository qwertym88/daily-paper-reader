---
title: Flow Actor-Critic for Offline Reinforcement Learning
title_zh: 面向离线强化学习的流式演员-评论家方法
authors: "Jongseong Chae, Jongeui Park, Yongjae Shin, Gyeongmin Kim, Seungyul Han, Youngchul Sung"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=wuncwN7iZN"
tags: ["query:rl-control"]
score: 9.0
evidence: 提出Flow Actor-Critic，用流模型同时构造演员与保守评论家，是新的actor-critic架构与训练方法
tldr: 离线强化学习的数据集常呈现复杂多模态分布，传统高斯策略表达不足且批评家易在分布外发生Q值爆炸。该文提出Flow Actor-Critic，将流模型同时用于演员和评论家获取：用流行为代理模型构造新的评论家正则项，抑制数据外区域的Q值高估。该方法保留了流策略对多模态分布的建模能力，并借助流模型副产品实现保守评论家训练。实验表明其在离线RL基准上表现更稳健。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 离线RL数据分布多模态，高斯策略表达能力有限，且分布外Q值可能爆炸。
method: 提出Flow Actor-Critic，利用流模型构建演员，并用流行为代理模型设计保守评论家正则项。
result: 有效抑制Q值爆炸，更好拟合多模态行为，离线策略学习性能提升。
conclusion: 流模型与保守评论家结合为离线RL提供了新的actor-critic设计范式。
---

## Abstract
The dataset distributions in offline reinforcement learning (RL) often exhibit complex and multi-modal distributions, necessitating expressive policies to capture such distributions beyond widely-used Gaussian policies. To handle such complex and multi-modal datasets, in this paper, we propose Flow Actor-Critic, a new actor-critic method for offline RL, based on recent flow policies. The proposed method not only uses the flow model for actor as in previous flow policies but also exploits the expressive flow model for conservative critic acquisition to prevent Q-value explosion in out-of-data regions. To this end, we propose a new form of critic regularizer based on the flow behavior proxy model obtained as a byproduct of flow-based actor design. Leveraging the flow model in this joint way, we achieve new state-of-the-art performance for test datasets of offline RL including the D4RL and recent OGBench benchmarks.

---

## 论文详细总结（自动生成）

# 面向离线强化学习的流式演员-评论家方法：论文总结

## 1. 核心问题与整体含义

- **研究背景**：离线强化学习（Offline RL）不使用在线交互，而是从预先收集的静态数据集中学习策略。这类数据集的行为分布往往具有**复杂、多模态**的特性。
- **现有瓶颈**：
  - 广泛采用的高斯策略表达能力有限，难以拟合真实数据集中的多模态分布。
  - 在离线设置下，批评家（Critic）容易对**分布外（out-of-distribution）区域**产生过高的Q值估计（Q-value explosion），导致策略学习不稳定。
- **整体含义**：需要一种既能表达复杂多模态行为，又能在训练中抑制Q值高估的新演员-评论家架构。

## 2. 方法论

- **核心思想**：提出 **Flow Actor-Critic**，将流模型（flow model）同时用于演员与评论家两条路径，形成联合利用。
  - **演员侧**：使用流模型作为策略，保留对多模态分布的强大建模能力（类似已有 flow policy 做法）。
  - **评论家侧**：利用流模型在构建演员过程中**副产品**——流行为代理模型（flow behavior proxy model），设计一种新型评论家正则项。
- **关键技术细节**：
  - 基于流行为代理模型构造的评论家正则项，用于惩罚流出数据分布区域的Q值，从而避免Q值爆炸。
  - 演员与评论家共享同一流模型框架，实现“一种模型、两种用途”的协同设计。
- **算法流程（文字说明）**：
  1. 从离线数据集学习一个流行为代理模型，用于刻画行为分布。
  2. 以该流模型为基底构建流策略（演员）。
  3. 在评论家训练中，使用流行为代理模型计算正则项，对分布外Q值施加惩罚。
  4. 交替更新演员与评论家，直至收敛。

## 3. 实验设计

- **数据集 / 基准**：
  - **D4RL**：离线RL最常用的标准基准，覆盖多种任务（如机器人控制、导航等）。
  - **OGBench**：较新的离线RL基准，用于测试泛化性与鲁棒性。
- **对比方法**：论文未在摘要中列出具体对比方法名称，但声明达到了“新最先进性能”（new state-of-the-art），暗示与已有的离线RL方法（如基于高斯策略的保守方法、现有流策略方法等）进行了比较。

## 4. 资源与算力

- **未明确说明**：摘要与元数据中**没有提及**任何关于GPU型号、数量、训练时长或算力资源的信息。
- 因此无法评估其计算成本或可复现性中的资源需求。

## 5. 实验数量与充分性

- **实验数量**：摘要仅概括性地说明在 D4RL 和 OGBench 的测试数据集上进行了实验，并报告了性能提升。具体实验组数（例如任务数量、独立种子数、消融实验）**未在提供内容中详述**。
- **充分性评估**：
  - 覆盖了两个主流基准，跨任务类型较广，增加了结果的**可信度**。
  - 但缺少对消融实验（如不同正则化强度、流模型结构选择）的说明，也未见对**超参数敏感性**和**失败案例**的分析。
  - 从可获取信息看，实验设计相对**有限但合理**，具体充分性需依赖论文全文判断。

## 6. 主要结论与发现

- 将流模型同时用于演员与评论家获取，能够**有效抑制分布外区域Q值爆炸**。
- 流策略能够更好地拟合离线数据中的**多模态行为分布**。
- 在 D4RL 与 OGBench 测试集上取得了**新的最先进性能**，证明了联合使用流模型的演员-评论家设计范式的有效性。

## 7. 优点

- **创新性**：首次将流模型同时用作演员和评论家正则项来源，形成统一的actor-critic架构，不同于仅将流用于策略的先前工作。
- **优雅性**：评论家正则项所需的流行为代理模型是流演员设计的天然副产品，无需额外复杂模型，结构紧凑。
- **针对性**：直击离线RL两大痛点（多模态拟合与Q值高估），问题意识强。
- **基准权威性**：使用D4RL和OGBench两大公认基准，结论具有较强说服力。

## 8. 不足与局限

- **信息缺失**：提供的文本中缺少对方法公式、具体正则项形式、超参数设置、网络结构等细节的公开，难以直接复现。
- **算力成本未知**：未报告资源消耗，无法评估其实际应用成本。
- **实验覆盖有限**：未见对更广任务（如视觉、多智能体）或真实世界数据集的评估；缺少消融实验细节，正则项贡献度不清晰。
- **潜在偏差风险**：若仅报告“最佳性能”而未提供方差、失败模式，可能高估方法稳定性；未说明与具体基线相比的统计显著性。
- **应用限制**：流模型通常推理成本较高，可能不适用于对实时性要求极高的部署场景；且依赖高质量离线数据集，在数据质量差时有效性未知。

（完）
