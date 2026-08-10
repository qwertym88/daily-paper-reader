---
title: "RN-D: Discretized Categorical Actors for On-Policy Reinforcement Learning"
title_zh: RN-D：用于在线策略强化学习的离散分类动作器
authors: "Yuexin Bian, Jie Feng, Tao Wang, Yijiang Li, Sicun Gao, Yuanyuan Shi"
date: 2026-04-30
pdf: "https://openreview.net/pdf/ef60a31fcf6a1563c2e4d1fc94b079eeaf94c2f3.pdf"
tags: ["query:rl-control"]
score: 8.0
evidence: 在线策略强化学习中的策略优化，离散化分类动作表示
tldr: 标准on-policy强化学习通常使用高斯动作与浅层MLP，导致优化脆弱。论文提出将动作表示为离散化分类分布，并联合正则化网络，形成RN-D策略。该策略目标类似于分类交叉熵，在多种连续控制任务上验证了其有效性，为在线策略学习提供了新的actor设计方向。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 标准on-policy强化学习使用高斯actor和浅层MLP，梯度噪声大且更新保守，优化脆弱。
method: 将每个动作维度表示为离散分类分布以构建分类actor，并引入正则化网络形成RN-D策略。
result: 在多个连续控制任务上优于基线，表现出更稳定的优化与更好的策略性能。
conclusion: 离散分类actor结合正则化网络是on-policy RL中高效且稳健的策略表示选择。
---

## Abstract
On-policy Reinforcement Learning (RL) remains a dominant paradigm for continuous control, yet standard implementations rely on Gaussian actors and relatively shallow MLP policies, often leading to brittle optimization when gradients are noisy, and policy updates must be conservative. In this paper, we revisit actor policy representation as a first-class design choice for on-policy RL. We study discretized categorical actors, which represent each action dimension as a distribution over discrete bins and induce a policy objective analogous to classification cross-entropy loss. Building on architectural advances from supervised learning, we further pair discretized categorical actors with regularized networks, yielding RN-D. Across diverse continuous-control benchmarks, we show that simply replacing the standard Gaussian actor with our proposed actor substantially improves performance, achieving state-of-the-art results within on-policy RL. We release our code at https://github.com/alwaysbyx/RND-RL.

---

## 论文详细总结（自动生成）

# 论文总结：RN-D——用于在线策略强化学习的离散分类动作器

## 1. 核心问题与整体含义

- **研究背景**：在线策略（On-policy）强化学习（RL）是连续控制任务中占主导地位的训练范式（如PPO、TRPO等）。然而，**标准实现通常依赖高斯动作分布与较浅的MLP策略网络**，这种组合在梯度噪声较大时极易导致优化过程脆弱，策略更新不得不保持保守，从而限制了学习效率与最终性能。
- **核心问题**：论文将**策略表示（policy representation）**视为在线策略RL中一个被忽视的“一等设计选择”，试图回答：能否通过改变actor的策略表示方式，从本质上改善在线策略RL的优化稳定性与性能？
- **整体意义**：论文通过提出一种新的actor设计——**离散分类动作器与正则化网络的结合（RN-D）**，为在线策略RL的策略表示选择提供了新的视角和强有力的实证支持，表明简单的表示替换即可带来显著的性能提升。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：放弃标准高斯actor，改为将**每个动作维度表示为离散化分类分布**。这一转换将策略优化目标类比为**分类交叉熵损失**，使策略学习在形式上更接近监督学习中的分类任务，从而可以利用在监督学习中已被验证有效的架构与训练技术。
- **关键技术细节**：
  - **离散化分类actor**：每个动作维度不再用连续的均值/方差参数化高斯分布，而是将动作空间划分为离散bin，每个bin上定义一个概率分布，动作采样从该分类分布中进行。
  - **正则化网络（Regularized Network）**：借鉴监督学习中深层残差网络与正则化设计的架构进展，将分类actor与正则化网络结构配对，形成完整策略体系 **RN-D（Regularized Network + Discretized actor）**。
  - **训练目标**：策略优化目标与分类交叉熵形式类似，使得梯度信号更平稳、更新方向更明确，缓解了高斯actor下梯度噪声大和更新保守的问题。
- **算法流程**（文字描述）：
  1. 将连续动作空间按维度离散化为若干个固定bin区间。
  2. 每个状态输入经正则化网络编码，输出每个动作维度在各个bin上的概率logits。
  3. 通过softmax获得分类分布，从中采样动作。
  4. 基于在线策略RL框架（如PPO）进行策略更新，策略损失与分类交叉熵形式一致。

## 3. 实验设计：数据集、场景与对比方法

- **Benchmark**：采用了多样化的连续控制基准任务（continuous-control benchmarks），涵盖不同的机器人控制与环境动力学复杂度。
- **对比方法**：主要对照**标准在线策略RL实现**，即以高斯actor + 浅层MLP为策略的标准baseline，并以在线策略RL框架下的现有最优方法为参照，评估RN-D是否达到**state-of-the-art**水平。
- **说明**：具体任务名称、环境列表（如MuJoCo、Isaac Gym等）在提供的元数据中未逐一列出。

## 4. 资源与算力

- 论文提供的材料中**未明确说明**使用的GPU型号、数量、训练时长、并行环境数量等算力相关信息。
- 也未提及与baseline方法之间的训练成本对比（如参数量、推理开销等）。

## 5. 实验数量与充分性

- 根据元数据，实验覆盖了多个连续控制基准任务，同时验证了**替换actor这一核心改动**带来的性能提升，并以“state-of-the-art within on-policy RL”进行总结。
- **充分性评估**：
  - **积极方面**：跨多个连续控制任务的验证为结论提供了有力支撑；“直接替换Gaussian actor”这一简洁的实验设计能清晰归因性能提升来源。
  - **信息缺口**：提供的元数据中未包含具体的消融实验细节，例如：
    - 是否有对离散bin数量、网络深度、正则化方式等超参数的消融分析？
    - 是否与离策略方法或其他actor家族（如扩散策略、Transformer策略）进行对比？
    - 是否报告了多次随机种子的方差与统计显著性检验？
  - 因此，从元数据来看，实验设计具有方向上的说服力，但具体实验规模与严谨性程度尚需阅读论文全文确认。

## 6. 主要结论与发现

- **简单替换，效果显著**：在多样化的连续控制任务中，仅将标准高斯actor替换为离散分类actor，即可显著提升性能。
- **RN-D达到最新最优水平**：离散分类actor + 正则化网络的组合在在线策略RL框架内达到了state-of-the-art结果。
- **优化稳定性改善**：分类交叉熵式目标有效缓解了高斯actor下的梯度噪声问题，策略更新更加稳健。
- **核心结论**：离散分类actor配合正则化网络，是在线策略RL中一种高效且稳健的策略表示选择。

## 7. 优点

- **视角独特**：将策略表示问题提升为在线策略RL的核心设计维度，挑战了“高斯actor是默认选择”这一隐含假设。
- **方法简洁有效**：不改变RL算法框架（如PPO），仅替换actor表示，即带来显著性能提升，工程成本低，可推广性强。
- **与监督学习前沿进展衔接**：将监督学习中成熟的正则化网络架构迁移到RL策略网络设计中，利用跨领域经验，思路新颖且合理。
- **代码开源**：公开了实现代码，有助于后续工作复现与进一步探索。

## 8. 不足与局限

- **环境覆盖范围与公开细节不够明确**：元数据中未列出具体任务名称与数量，需阅读全文确认是否覆盖了高维、稀疏奖励、视觉输入等更具挑战性的场景。
- **算力与成本信息缺失**：未说明训练所需的资源规模与时间成本，无法评估该方法在实际部署中的资源可行性。
- **消融实验细节未见**：缺少对bin数量、网络规模、正则化方式等关键超参数的消融分析，以及多次运行下的稳定性报告，结论的稳健性需进一步验证。
- **与更广泛方法家族的对比不明确**：是否与离散动作领域的已有工作、或更先进的actor表示（如扩散模型、Transformer策略）进行了对比尚不清楚，这会影响“state-of-the-art”结论的可信度。
- **潜在偏差风险**：在线策略RL框架本身受超参数（如PPO的clip系数、学习率）影响较大，文中若未明确这些超参在不同方法间如何调优，可能存在比较不公平的风险。

---

（完）
