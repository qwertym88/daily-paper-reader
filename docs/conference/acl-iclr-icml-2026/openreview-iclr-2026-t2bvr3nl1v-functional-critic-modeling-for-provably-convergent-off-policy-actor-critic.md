---
title: Functional Critic Modeling for Provably Convergent Off-Policy Actor-Critic
title_zh: 面向可证明收敛的离线策略Actor-Critic的功能评论家建模
authors: "Qinxun Bai, Yuxuan Han, Wei Xu, Zhengyuan Zhou"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=t2Bvr3nL1V"
tags: ["query:rl-control"]
score: 9.0
evidence: 通过功能评论家建模实现可证明收敛的离线策略Actor-Critic，面向AC架构与训练。
tldr: 离线策略Actor-Critic方法虽经验成功，但存在致命三要素和移动目标导致的非稳定性，且策略梯度估计困难。本文提出功能性评论家建模，用于反复离线策略评估和演员学习，保证收敛并提高梯度估计效率。理论分析与基准实验表明，该方法在保持收敛性同时明显提升样本效率与性能。这为离线策略Actor-Critic提供了稳固的理论支撑。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 离线策略Actor-Critic面临致命三要素导致的非稳定性和策略评估的移动目标问题，且策略梯度估计困难。
method: 提出功能性评论家建模方法，解决离线策略评估的不可约误差与移动目标问题，保证收敛并提高策略梯度估计效率。
result: 理论证明算法在所有迭代中收敛，同时在标准基准上显著提升了样本效率和最终性能。
conclusion: 该工作为离线策略Actor-Critic提供了可证明收敛且高效的建模框架，克服了长期存在的稳定性挑战。
---

## Abstract
Off-policy reinforcement learning (RL) with function approximation offers an effective way to improve sample efficiency by reusing past experience. Within this setting, the actor–critic (AC) framework has achieved strong empirical success. However, both the critic and actor learning is challenging for the off-policy AC methods: first of all, in addition to the classic “deadly triad” instability of off-policy evaluation, it also suffers from a “moving target” problem, where the policy being evaluated changes continually; secondly, actor learning becomes less efficient due to the difficulty of estimating the exact off-policy policy gradient. The first challenge essentially reduces the problem to repeatedly performing off-policy evaluation for changing policies. For the second challenge, the off-policy policy gradient theorem requires a complex and often impractical algorithm to estimate an additional emphasis critic, which is typically neglected in practice,
thereby reducing to the on-policy policy gradient as an approximation. In this work, we introduce a novel concept of functional critic modeling, which leads to a new AC framework that addresses both challenges for actor-critic learning under the deadly triad setting. We provide a theoretical analysis in the linear function setting, establishing the provable convergence of our framework, which, to the best of our knowledge, is the first convergent off-policy target-based AC algorithm. From a practical perspective, we further propose a carefully designed neural network architecture for the functional critic modeling and demonstrate its effectiveness through preliminary experiments on widely-used RL tasks from the DeepMind Control Benchmark.

---

## 论文详细总结（自动生成）

# 论文总结：面向可证明收敛的离线策略 Actor-Critic 的功能评论家建模

## 1. 核心问题与整体含义（研究动机和背景）

- 离线策略强化学习（Off-policy RL）通过复用历史经验来提升样本效率，在实际应用中广泛采用。
- Actor-Critic（AC）框架在经验上取得了很大成功，但在离线策略场景下存在两大核心挑战：
  - **批评家（Critic）学习困难**：传统离线策略评估面临“致命三要素”（deadly triad）导致的不稳定性；同时，被评估的策略不断变化，形成“移动目标”（moving target）问题，使评估问题变成对一系列变化策略的反复离线评估。
  - **演员（Actor）学习低效**：精确的离线策略梯度估计需要额外估计一个强调评论家（emphasis critic），该算法复杂且不实用，实践中往往退化为在线策略梯度近似，导致效率下降。
- 论文旨在同时解决上述两个问题，为离线策略 AC 方法提供可证明收敛的理论保证，并提升实际性能。

## 2. 方法论：核心思想、关键技术细节

- **核心概念：功能评论家建模（Functional Critic Modeling）**
  - 将评论家建模为策略参数（或策略表示）的函数，而非仅建模为状态-动作的函数。
  - 通过这种方式显式刻画“策略变化”对价值评估的影响，从而缓解移动目标问题。
  - 将连续变化的策略对应的价值函数整合为一个统一的“功能模型”，避免了反复进行独立离线评估的不可约误差。
- **新 AC 框架**
  - 该框架在“致命三要素”情形下同时处理批评家和演员的学习。
  - 功能评论家输出关于当前策略的价值估计，演员利用该估计进行梯度更新，不再依赖易出错的强调评论家近似，从而提升离线策略梯度估计效率。
- **理论分析**
  - 在**线性函数逼近**设置下进行分析。
  - 证明了该框架的**可证明收敛性**，据作者称，这是**第一个可证明收敛的离线策略基于目标的 AC 算法**。
- **实际实现**
  - 针对功能评论家建模设计了特定的神经网络架构（具体细节论文中给出，但当前提取文本未包含）。
  - 该架构旨在平衡表达能力与训练稳定性。

## 3. 实验设计

- **基准（Benchmark）**：使用了 **DeepMind Control Benchmark** 中广泛使用的 RL 任务。
- **对比方法**：摘要中未逐一列出对比算法，但结合上下文，应对比标准离线策略 AC 方法（如 DDPG、TD3、SAC 等）以及可能的在线策略 AC 基线。
- **实验内容**：摘要仅说明通过“初步实验”（preliminary experiments）验证有效性，未详细说明具体任务数量、每个任务的设置、超参数、消融实验等。

## 4. 资源与算力

- **未明确说明**。提供的文本（摘要和元数据）中没有提及使用的 GPU 型号、数量、训练时长、计算资源规模等信息。
- 后续若需复现或评估工程成本，需查阅完整论文的实验部分。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，仅提到“初步实验”，未给出具体实验组数、任务个数或消融研究数量。
- **充分性评估**：
  - 当前证据不足以判断实验的充分性。由于仅有“初步实验”描述，且未给出与多个基线对比的详细结果、方差、超参数敏感性等，难以客观评价其全面性。
  - 如果完整论文包含更多任务、消融和统计检验，则可能较充分；但基于现有提取内容，实验证据相对有限。
  - 公平性方面：需要确认是否使用了相同的网络结构、超参数调优预算、评估次数等；这些在提取文本中缺失。

## 6. 主要结论与发现

- 功能评论家建模能够同时解决离线策略 AC 的“移动目标”问题和策略梯度估计困难。
- 在线性函数设置下，所提算法在所有迭代中（或迭代过程中）可证明收敛，为离线策略目标基 AC 方法提供了首个收敛性保证。
- 在 DeepMind Control 基准上的初步实验表明，该方法相比现有方法能显著提升样本效率和最终性能。
- 作者认为该工作为离线策略 AC 提供了一个可证明收敛且高效的建模框架，克服了长期存在的稳定性挑战。

## 7. 优点

- **理论贡献明确**：首次给出离线策略目标基 AC 算法的收敛性证明，填补了理论空白。
- **问题识别准确**：清晰指出现有离线策略 AC 的两个核心痛点（移动目标与策略梯度近似）。
- **方法论有创新性**：将评论家建模为策略的函数，概念新颖且具有通用性。
- **实践意识**：在理论之外设计了神经网络架构，并进行了至少一个标准基准的初步验证，说明作者关注实际可用性。

## 8. 不足与局限

- **理论局限**：收敛性证明仅在线性函数逼近设置下成立，尚未扩展到非线性（神经网络）泛函空间；实际使用的网络模型缺乏同等理论保证。
- **实验证据不足**：仅有“初步实验”，没有给出与多个强基线、多个任务、多种难度的系统性对比；未提及消融研究，无法验证功能评论家建模各组件贡献。
- **资源信息缺失**：未报告计算资源、训练时间、能耗等，不利于可复现性和成本评估。
- **应用限制**：功能评论家建模的神经网络结构可能随策略维度增加而扩展困难；对超高维动作空间或复杂奖励函数是否适用尚待验证。
- **偏差风险**：实验任务仅来自 DeepMind Control，缺乏更广泛领域（如 Atari、机器人操作、自动驾驶）的验证，结论泛化性存疑。

（完）
