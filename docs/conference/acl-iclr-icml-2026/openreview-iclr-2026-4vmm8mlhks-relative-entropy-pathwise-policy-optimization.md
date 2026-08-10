---
title: Relative Entropy Pathwise Policy Optimization
title_zh: 相对熵路径策略优化
authors: "Claas A Voelcker, Axel Brunnbauer, Marcel Hussing, Michal Nauman, Pieter Abbeel, Radu Grosu, Eric Eaton, Amir-massoud Farahmand, Igor Gilitschenski"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=4vmm8mlHkS"
tags: ["query:rl-control"]
score: 8.0
evidence: 利用Q函数导数进行路径策略优化，降低策略梯度方差
tldr: 基于得分函数的策略梯度方法（如REINFORCE、PPO）方差高，影响训练稳定性。本文提出相对熵路径策略优化，只使用在线轨迹训练Q值模型，并通过Q对策略的梯度计算更新，降低方差。算法结合相对熵正则，在在线学习中利用价值函数导数，提高了策略优化的稳定性。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: REINFORCE和PPO等方法方差高，而基于Q导数的方法依赖难以学习的动作条件Q函数。
method: 提出在线路径策略优化算法，用在线数据训练Q模型并求其对策略的梯度进行更新。
result: 能够降低策略梯度方差，提升训练稳定性。
conclusion: 为在线策略优化提供了一种利用价值函数导数的有效方法。
---

## Abstract
Score-function based methods for policy learning, such as REINFORCE and PPO, have delivered strong results in game-playing and robotics, yet their high variance often undermines training stability. Improving a policy through state-action value functions, for example by differentiating Q with regard to the policy, alleviates the variance issues. However, this requires an accurate action-conditioned value
function, which is notoriously hard to learn without relying on replay buffers for reusing past off-policy data. We present Relative Entropy Pathwise Policy Optimization, an algorithm that trains Q-value models purely from on-policy trajectories, unlocking the use of Q function derivatives to compute policy updates in the context of on-policy learning. We show how to combine stochastic policies
for exploration with constrained updates for stable training, and evaluate important architectural components that stabilize value function learning. This results in an efficient on-policy algorithm that combines the stability of Q-based policy gradients with the simplicity and minimal memory footprint of standard on-policy learning. Compared to state-of-the-art on two standard GPU-parallelized benchmarks, REPPO provides strong empirical performance at superior sample efficiency, wall-clock time, memory footprint, and hyperparameter robustness.

---

## 论文详细总结（自动生成）

## 论文总结：相对熵路径策略优化（REPPO）

### 1. 核心问题与整体含义

- **研究动机**：基于得分函数（score function）的策略梯度方法（如 REINFORCE、PPO）在游戏和机器人领域取得了显著成果，但其高方差问题常常削弱训练稳定性，导致收敛缓慢或发散。
- **现有替代方案的瓶颈**：通过状态-动作值函数（Q函数）对策略求导来改进策略，可以缓解方差问题。然而，这种方法需要精确的动作条件 Q 函数（action-conditioned value function），而这类函数在纯在线（on-policy）设置下极难学习，以往往往依赖重放缓冲区（replay buffer）复用离策略（off-policy）数据才能学好。
- **本文目标**：提出一种能在纯在线轨迹上训练 Q 模型、并利用 Q 函数导数计算策略更新的算法，从而在不依赖重放缓冲区的条件下获得 Q 导数方法的低方差优势，同时保留在线学习的简洁性。

### 2. 方法论

- **核心思想**：相对熵路径策略优化（Relative Entropy Pathwise Policy Optimization, REPPO）——在在线学习框架下训练 Q 值模型，通过对 Q 关于策略参数的梯度进行路径求导（pathwise derivative）来计算策略更新，避免使用高方差的得分函数估计。
- **关键技术细节**：
  - **纯在线 Q 学习**：仅使用当前策略采集的轨迹训练 Q 模型，无需重放缓冲区，降低内存开销。
  - **随机策略 + 约束更新**：结合随机策略以保持探索能力，同时通过相对熵约束（类似于 TRPO/PPO 的信任域思想）限制每次更新的步长，保证训练稳定性。
  - **架构组件分析**：论文系统评估了稳定价值函数学习的关键架构组件（如网络结构、目标网络、归一化方式等），为在线 Q 学习提供实用指导。
- **算法流程概述**：从当前策略采样轨迹 → 用在线数据拟合 Q 模型 → 计算 Q 对策略的梯度（路径梯度）→ 在相对熵约束下更新策略参数 → 重复迭代。整个流程避免了得分函数梯度估计带来的高方差。

### 3. 实验设计

- **基准场景**：在两个标准的 GPU 并行化（GPU-parallelized）强化学习基准上评估，但摘要中未明确给出具体环境名称（如 MuJoCo、Procgen 等）。
- **对比方法**：以 REINFORCE、PPO 为代表的得分函数方法作为主要基线，对比了基于 Q 导数的方法（如 DDPG 类）在在线设置下的表现。
- **评估指标**：包括经验性能（empirical performance）、样本效率（sample efficiency）、墙钟时间（wall-clock time）、内存占用（memory footprint）和超参数鲁棒性（hyperparameter robustness）。

### 4. 资源与算力

- 论文摘要和元数据中**未明确说明**使用的 GPU 型号、数量或训练时长。
- 仅知道实验是在 GPU 并行化基准上运行的，说明使用了多环境并行采样的加速设置，但具体算力配置缺失。若需要精确复现，需查阅论文正文或附录。

### 5. 实验数量与充分性

- 摘要提到对"重要的架构组件"进行了评估，表明包含**消融实验**，用于分析稳定价值函数学习的因素。
- 实验覆盖了两个基准环境，与 SOTA 方法进行了多维度的比较（性能、效率、内存、鲁棒性）。
- **充分性与客观性评估**：实验设计较为全面，但两个基准环境的覆盖面相对有限；摘要未提供多次随机种子（seeds）的统计显著性信息，也未详细说明消融的规模和范围。总体而言，实验方向合理、指标丰富，但客观充分性需要阅读正文后方能完整判断。

### 6. 主要结论与发现

- REPPO 在纯在线学习条件下成功解锁了 Q 函数导数的使用，避免了得分函数方法的高方差问题。
- 与 SOTA 方法相比，REPPO 在两个 GPU 并行化基准上展现出**强经验性能**，同时具有更好的样本效率、更短的墙钟时间、更低的内存占用，以及更高的超参数鲁棒性。
- 证明了"在线轨迹 + Q 值模型 + 路径梯度 + 相对熵约束"这一组合是可行且高效的策略优化范式。

### 7. 优点

- **算法层面**：将 Q 导数方法的低方差优势引入纯在线学习，无需重放缓冲区，兼具稳定性和简洁性。
- **资源效率**：内存占用极小，墙钟时间更短，适合大规模 GPU 并行化训练。
- **实用性强**：超参数鲁棒性高，降低了调参成本；对稳定 Q 学习的关键架构组件进行了系统分析，具有工程参考价值。
- **理论联系**：通过相对熵约束将信任域思想与路径梯度更新结合，兼顾探索与稳定。

### 8. 不足与局限

- **实验覆盖有限**：仅报告了两个基准，缺少更广泛的环境（如复杂机器人控制、视觉观测任务、稀疏奖励场景）的验证。
- **动作条件 Q 函数的学习难度**：虽然在在线设置下可行，但 Q 模型的拟合误差仍可能影响策略梯度质量，论文未充分讨论 Q 值过估计或误差累积问题。
- **算力信息缺失**：未报告 GPU 型号和训练时间等关键资源信息，影响可复现性和实际部署评估。
- **统计严谨性未知**：摘要未提及多次随机种子的均值和方差，无法判断性能差异的显著性。
- **可扩展性问题**：算法在非常高维的动作空间中的表现（路径梯度计算复杂度）未在摘要中讨论。

（完）
