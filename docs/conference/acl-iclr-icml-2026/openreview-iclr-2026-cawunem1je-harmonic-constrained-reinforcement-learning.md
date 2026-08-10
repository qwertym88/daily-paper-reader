---
title: Harmonic Constrained Reinforcement Learning
title_zh: 谐波约束强化学习
authors: "Guojian Zhan, Feihong Zhang, Maanping Shao, Tianyi Zhang, Jingliang Duan, Shengbo Eben Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=CawuNEM1jE"
tags: ["query:rl-control"]
score: 9.0
evidence: 约束强化学习，安全约束，谐波梯度与置信域极小极大优化
tldr: 约束强化学习需要同时最大化奖励并满足安全约束，但奖励驱动更新容易违反约束，安全驱动更新又损害性能。本文提出谐波约束强化学习HCRL，在梯度层面以最优方式解决奖励与安全之间的冲突。每轮迭代构造置信域极小极大优化问题，计算谐波梯度用于策略更新。该方法在多个基准任务中实现了稳定且均衡的约束满足与奖励性能，为安全RL提供了一种新的梯度级融合思路。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 奖励驱动与安全驱动的更新存在冲突，难以在训练中保持奖励最大化与约束满足的平衡。
method: 每轮构造置信域极小极大问题，用谐波梯度融合奖励与安全信号进行策略更新。
result: 实验表明HCRL有效缓和冲突，兼顾奖励性能与约束满足且训练稳定。
conclusion: 为约束强化学习的梯度层面权衡提供了最优化的新机制。
---

## Abstract
Constrained reinforcement learning (CRL) aims to train agents that maximize rewards while satisfying safety constraints, an essential requirement for real-world application. Despite extensive progress in using various constrained optimization techniques, striking a stable balance between reward maximization and constraint satisfaction remains a challenge. Reward-driven updates often violate constraints, while overly safety-driven updates degrade performance. To address this conflict, we propose harmonic constrained reinforcement learning (HCRL), a framework that resolves reward-safety trade-offs at the gradient level in an optimal manner. At each iteration, HCRL formulates a trust-region minimax optimization problem to compute a harmonic gradient (HG) for the policy update. This gradient has minimal conflict with both the reward and safety objective gradients, thereby enabling more stable and balanced policy learning. In practice, we can equivalently convert this challenging constrained minimax problem for solving HG as an unconstrained single-variable optimization problem, maintaining high time-efficiency. Empirical results on three planar constrained optimization problems and ten Safety Gymnasium tasks demonstrate that HCRL consistently outperforms existing CRL baselines in terms of stability and the ability to find feasible and optimal policies.

---

## 论文详细总结（自动生成）

# 谐波约束强化学习（HCRL）论文总结

> 说明：以下内容基于论文摘要与元数据生成，原始 PDF 文本因访问限制未能获取全文，因此部分细节（如公式、算法实现、具体对比方法）无法展开，将如实标注。

## 1. 核心问题与整体含义

- **背景**：约束强化学习（Constrained Reinforcement Learning, CRL）旨在训练智能体在最大化累积奖励的同时满足安全约束，这对真实世界部署至关重要。
- **核心问题**：奖励驱动与安全驱动的策略更新存在固有冲突——过分追求奖励容易违反安全约束，而过分强调安全又会导致性能严重退化。现有 CRL 方法在“奖励最大化”和“约束满足”之间难以取得稳定平衡。
- **整体含义**：作者提出一种在梯度层面最优协调两者冲突的框架，使策略更新同时尽可能不违背奖励梯度和安全梯度，从而在学习过程中保持性能与安全的均衡。

## 2. 方法论

- **核心思想**：提出**谐波约束强化学习（Harmonic Constrained Reinforcement Learning, HCRL）**，将奖励与安全目标的权衡从“目标函数加权”转移到“梯度方向融合”层面。
- **关键技术**：
  - 每次迭代构造一个**信任域极小极大优化问题（trust-region minimax optimization）**，用于计算**谐波梯度（harmonic gradient, HG）**。
  - 该谐波梯度被定义为与奖励目标梯度、安全约束目标梯度的“总冲突最小”的方向，从而在更新策略时既不严重损害奖励，也不严重违反安全约束。
  - 理论上，该约束极小极大问题可以**等价转换为无约束的单变量优化问题**，因此求解高效，保持了较好的时间效率。
- **算法流程（文字描述）**：
  1. 在当前策略处构建信任域，限制策略更新幅度；
  2. 构造极小极大优化问题，求解谐波梯度；
  3. 利用谐波梯度更新策略，进入下一轮迭代；
  4. 重复直到收敛或达到最大迭代次数。

## 3. 实验设计

- **任务场景**：
  - 3 个平面约束优化问题（planar constrained optimization problems），用于验证方法在低维可控场景中的正确性。
  - 10 个 Safety Gymnasium 任务，用于评估在高维连续控制环境中的泛化性和稳定性。
- **Benchmark**：Safety Gymnasium（常见安全强化学习基准平台）。
- **对比方法**：与“现有 CRL 基线”（existing CRL baselines）进行比较，但摘要中**未列出具体基线名称**（如 CPO、FOCOPS、CUP 等），也未给出性能数值表。此外，未提及是否有消融实验。

## 4. 资源与算力

- **未明确说明**。论文摘要和元数据中均未报告 GPU 型号、数量、训练时长、显存占用等计算资源信息。若要复现，需要查阅全文或联系作者补充。

## 5. 实验数量与充分性

- **实验数量**：至少 13 个任务（3 个平面优化 + 10 个 Gymnasium 任务），每个任务估计有多次随机种子运行，但未在摘要中明确。
- **充分性评价**：
  - 覆盖了从简单优化问题到高维安全任务的多层次场景，具有一定广度；
  - 但缺少具体性能指标（如平均回报、约束违反率）、标准差、训练曲线等细节；
  - 没有提及消融实验，无法单独验证谐波梯度的贡献；
  - 由于对比方法未列出，难以判断实验设置的公平性和全面性。
  - 总体上，实验规模中等偏上，但摘要层面的信息不足以完全评估其充分性。

## 6. 主要结论与发现

- HCRL 在**稳定性**和**找到可行且最优策略**的能力上，持续优于现有 CRL 基线。
- 实验表明，该方法能有效缓和奖励与安全之间的冲突，在保持奖励性能的同时更好地满足安全约束，且训练过程更稳定。
- 作者认为这一结果验证了“梯度级最优权衡”的可行性，为 CRL 提供了一种新的解决思路。

## 7. 优点

- **新颖的梯度级融合机制**：不同于传统加权或约束优化的做法，HCRL 在梯度方向上进行极小极大权衡，理论上能保证更新方向与两目标的最小冲突，具有较强创新性。
- **高效求解**：将复杂的约束极小极大问题等价化简为无约束单变量问题，避免了高开销的迭代优化，有利于实际部署。
- **任务表现均衡**：在多个基准任务上同时兼顾了奖励性能与约束满足，且训练稳定性好。
- **问题定义清晰**：明确指出现有方法的短板（“奖励驱动违反约束，安全驱动损害性能”），并给出对症下药的方案。

## 8. 不足与局限

- **信息不完整**：当前只有摘要，无法获得完整公式、超参数设置、网络结构等关键细节；原始 PDF 无法直接访问也是阅读障碍之一。
- **实验细节缺失**：没有具体基线名称、性能数值表、标准差不汇报，很难定量判断优势幅度。
- **缺乏消融实验**：未说明是否做了谐波梯度与替代梯度（如简单加权梯度、安全梯度）的对比，无法确认方法核心贡献的独立效果。
- **计算资源未报告**：可复现性和工程成本不明。
- **应用限制**：实验仅基于仿真环境（Safety Gymnasium），未涉及真实机器人或其他高风险物理场景；梯度级方法在高维策略网络中是否易于扩展仍需更多验证。
- **潜在偏差风险**：由于对比方法和随机种子信息不清，可能存在选择性报告或基线调参不充分的风险，但这一判断需要全文确认。

（完）
