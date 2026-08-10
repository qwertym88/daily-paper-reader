---
title: What Makes Value Learning Efficient in Residual Reinforcement Learning?
title_zh: 残差强化学习中价值学习高效性的关键因素
authors: "Guozheng Ma, Lu Li, Haoyu Wang, Zixuan Liu, Pierre-Luc Bacon, Dacheng Tao"
date: 2026-04-30
pdf: "https://openreview.net/pdf/ebd90c4553944cff7ac36ef3d715054e374d9d7a.pdf"
tags: ["query:rl-control"]
score: 6.0
evidence: 分析残差RL中价值学习面临的瓶颈并提出解决办法
tldr: 残差强化学习通过冻结基础策略并学习有界修正来实现稳定在线改进，但其价值学习面临独特困难。本文识别出冷启动病理和结构尺度失配两个关键瓶颈，并验证简单方案即可解决：利用基础策略转移隐式预热价值模型，配合评论家归一化。这为残差RL的稳定训练提供了实用指导。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 残差RL中价值学习存在冷启动与尺度失配问题，影响稳定改进。
method: 系统性分析价值学习瓶颈，提出基础策略转移作为价值锚点并进行评论家归一化。
result: 识别出两个核心瓶颈并验证了简单有效的解决方案。
conclusion: 为残差RL的价值学习设计提供了可操作的改进准则。
---

## Abstract
Residual reinforcement learning (RL) enables stable online refinement of expressive pretrained policies by freezing the base and learning only bounded corrections. However, value learning in residual RL poses unique challenges that remain poorly understood. In this work, we identify two key bottlenecks: cold start pathology, where the critic lacks knowledge of the value landscape around the base policy, and structural scale mismatch, where the residual contribution is dwarfed by the base action. Through systematic investigation, we uncover the mechanisms underlying these bottlenecks, revealing that simple yet principled solutions suffice: base-policy transitions serve as an essential value anchor for implicit warmup, and critic normalization effectively restores representation sensitivity for discerning value differences. Based on these insights, we propose DAWN (Data-Anchored Warmup and Normalization), a minimal approach targeting efficient value learning in residual RL. By addressing these bottlenecks, DAWN demonstrates substantial efficiency gains across diverse benchmarks, policy architectures, and observation modalities.

---

## 论文详细总结（自动生成）

# 残差强化学习中价值学习高效性的关键因素：详细总结

## 1. 核心问题与整体含义（研究动机与背景）
- **背景**：残差强化学习（Residual RL）是一种面向已预训练策略的在线优化范式，其核心思想是冻结基础策略（base policy）保持不变，仅学习一个有界的修正项（residual correction），从而在利用预训练知识的同时保证在线更新的稳定性。
- **核心问题**：尽管残差RL在策略优化层面具有优势，但其中的**价值学习**（value learning）存在独有的难点，此前研究对此理解不足。作者识别出两个关键瓶颈：
  - **冷启动病理（cold start pathology）**：评论家（critic）在训练初期对基础策略附近的价值景观（value landscape）缺乏知识，导致价值估计不准确，进而干扰残差策略的学习。
  - **结构尺度失配（structural scale mismatch）**：残差动作的贡献在数值尺度上远小于基础动作，在价值函数表示中容易被“淹没”，使得评论家难以分辨不同残差动作带来的价值差异。
- **整体含义**：这两大瓶颈会阻碍残差RL的稳定改进和样本效率。本文通过系统分析揭示其机制，并提出简单有效的解决方案，为残差RL中价值学习的设计提供了实用性指导原则。

## 2. 方法论：核心思想、关键技术细节
- **方法论核心思想**：作者不引入复杂的新架构，而是基于对瓶颈机制的理解，提出最小化干预方法 **DAWN（Data-Anchored Warmup and Normalization）**。
- **两个关键技术措施**（结合摘要与元数据描述）：
  - **基础策略转移作为价值锚点（Base-policy transitions as value anchor）**：
    - 利用基础策略产生的转移数据（transitions）对评论家进行**隐式预热（implicit warmup）**，使价值模型在训练早期就能获得关于基础策略附近状态-动作价值的基本认识。这相当于给价值学习一个“锚”，缓解冷启动病理。
  - **评论家归一化（Critic normalization）**：
    - 对评论家网络或其特征表示进行归一化处理，恢复其表示敏感性（representation sensitivity），使其能够有效区分被基础动作“掩盖”的微小残差差异，从而解决结构尺度失配问题。
- **关于公式与算法流程**：由于提供的文本仅为论文摘要与元数据，未包含具体公式或算法伪代码。但根据描述，DAWN应当是在标准残差RL框架（如TD3/SAC的残差变体）基础上，增加数据锚定预热阶段和评论家归一化层，而无需改变基础策略或损失函数的基本形式。

## 3. 实验设计
- **Benchmark与场景**：摘要明确指出实验覆盖了“多样化基准、策略架构和观察模态”（diverse benchmarks, policy architectures, and observation modalities），暗示至少包含多种连续控制任务（如MuJoCo/DM Control类）以及不同输入类型（如状态输入、图像输入）。
- **对比方法**：文本未具体列出基线对比对象。通常这类工作会与标准RL算法（如TD3、SAC）、不带残差的微调方法、未做DAWN处理的残差RL变体等进行对比。
- **评测指标**：未在摘要中详细说明，推测以累积奖励（return）或训练效率（如达到特定分数所需的环境交互步数）为主。
- **注意**：由于无法获取全文，具体的任务列表、环境版本和对比基线均无法确认。

## 4. 资源与算力
- **原文未明确说明**：在提供的摘要与元数据中，没有关于GPU型号、数量、训练时长、参数量等算力资源的信息。
- **推断**：相关实验可能使用常规深度学习训练配置，但无法证实，需查阅全文才能获知。

## 5. 实验数量与充分性
- **实验数量**：从摘要看，实验覆盖面较广（多样化基准、架构、模态），但无法得知具体组数（如任务数量、种子数、消融实验数量）。
- **充分性与公平性分析**：
  - 由于未提供详细实验设置，无法客观评估其对比是否公平（如超参数调优程度、计算预算是否对齐等）。
  - 论文属于ICML 2026接收论文，通常审稿要求一定程度的多任务验证与消融，因此大概率存在针对两个瓶颈的消融实验（如去除预热、去除归一化的效果对比）。
  - 但当前证据不足以做出全面判断。

## 6. 主要结论与发现
- **识别瓶颈**：明确残差RL价值学习中存在冷启动病理和结构尺度失配两大核心困难。
- **机制理解**：通过系统研究揭示了上述瓶颈产生的内在原因：基础策略附近价值信息缺失，以及基础动作对残差信号的尺度压制。
- **解决方案有效**：简单而有原则的方法（基础策略转移锚定预热 + 评论家归一化）即可显著改善价值学习效率。
- **性能提升**：DAWN在多种基准、策略架构和观察模态下均表现出明显效率优势，验证了方法的通用性。
- **实践准则**：总结出可操作的设计原则——残差RL应利用基础策略数据预热价值网络，并对评论家表示进行归一化处理。

## 7. 优点
- **问题定义清晰**：首次系统性地分析残差RL中价值学习面临的独有困难，精准指出两个可复现的病理现象。
- **方案简洁有效**：避免了复杂的结构性创新，用数据选择与归一化等基础手段解决问题，易于实现和集成到现有系统。
- **洞察力强**：将尺度失配与表示敏感性联系起来，为理解价值学习在残差设定下的失效模式提供了新视角。
- **实验覆盖面广**：验证了方法在多种策略架构和观测模态上的有效性，增强了结论可靠性。
- **实用价值高**：给出的准则可以直接应用于实际残差RL工程中，有助于稳定在线微调。

## 8. 不足与局限
- **信息不完整风险**：当前文献来源仅有摘要，无法评估方法在数学推导、算法稳定性证明等方面的细节，以及是否所有实验均严格对齐标准协议。
- **应用边界未明**：摘要未说明DAWN在不具备基础策略数据的场景（如完全在线从头训练）是否有效，对基础策略质量不同（差/好）的敏感性也未讨论。
- **理论深度可能有限**：评分6.0暗示审稿人可能认为其贡献属于“验证了简单有效技巧”，而非重大理论突破；归一化与预热的作用机制仍可能缺乏严格的理论保证。
- **泛化担忧**：虽然测试了多样化基准，但未提及真实世界任务或大规模图像环境；在复杂高维观察下的表现未知。
- **算力透明度不足**：未报告训练成本，难以判断效率提升是否包含额外计算开销（如生成基础策略转移数据的成本）。

（完）
