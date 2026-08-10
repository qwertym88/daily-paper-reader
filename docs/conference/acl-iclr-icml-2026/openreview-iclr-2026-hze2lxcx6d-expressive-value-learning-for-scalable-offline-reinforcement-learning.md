---
title: Expressive Value Learning for Scalable Offline Reinforcement Learning
title_zh: 面向可扩展离线强化学习的高表达价值学习
authors: "Nicolas Espinosa-Dice, Kianté Brantley, Wen Sun"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=Hze2lxCX6D"
tags: ["query:rl-control"]
score: 7.0
evidence: 关注离线强化学习中价值函数的高表达学习与可扩展性
tldr: 离线强化学习受限于可扩展性和表达力，现有方法依赖耗时的反向传播或策略蒸馏。本文研究如何利用扩散模型和流匹配等高表达生成模型进行价值学习，以提升离线RL在大规模复杂数据集上的扩展能力。通过对比不同价值学习范式，探索绕过BPTT和蒸馏瓶颈的新途径，为规模化离线决策奠定方法基础。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 离线RL扩展到大规模数据时，现有价值学习方法受限于反向传播和策略蒸馏。
method: 探讨利用扩散与流匹配等生成模型构建高表达能力价值函数，提升可扩展性。
result: 提出类问题并评估不同价值学习范式，显示高表达价值模型的潜力。
conclusion: 为大规模离线RL提供高表达价值学习的新方向，减少计算瓶颈。
---

## Abstract
Reinforcement learning (RL) is a powerful paradigm for learning to make sequences of decisions. However, RL has yet to be fully leveraged in robotics, principally due to its lack of scalability. Offline RL offers a promising avenue by training agents on  large, diverse datasets, avoiding the costly real-world interactions of online RL. Scaling offline RL to increasingly complex datasets requires expressive generative models such as diffusion and flow matching. However, existing methods typically depend on either backpropagation through time (BPTT), which is computationally prohibitive, or policy distillation, which introduces compounding errors and limits scalability to larger base policies. In this paper, we consider the question of how to develop a scalable offline RL approach without relying on distillation or backpropagation through time. We introduce Expressive Value Learning for Offline Reinforcement Learning (EVOR): a scalable offline RL approach that integrates both expressive policies and expressive value functions. EVOR learns an optimal, regularized $Q$-function via flow matching during training. At inference-time, EVOR performs inference-time policy extraction via rejection sampling against the expressive value function, enabling efficient optimization, regularization, and compute-scalable search without retraining. Empirically, we show that EVOR outperforms baselines on a diverse set of offline RL tasks, demonstrating the benefit of integrating expressive value learning into offline RL.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 核心问题与整体含义

论文关注离线强化学习（Offline RL）的可扩展性问题。强化学习在机器人等领域尚未被充分利用，主要原因在于其缺乏可扩展性——在线交互成本高昂。离线 RL 通过在大规模、多样化的数据集上训练智能体，避免了昂贵的在线交互，是一条有前景的路径。然而，将离线 RL 扩展到日益复杂的数据集，需要高表达能力的生成模型（如扩散模型和流匹配）。现有方法要么依赖通过时间反向传播（BPTT），其计算开销巨大；要么依赖策略蒸馏，这会引入复合误差并限制基策略的扩展能力。因此，论文的核心问题是：**如何在不依赖蒸馏或 BPTT 的情况下，构建可扩展的离线 RL 方法？** 整体含义在于，通过引入高表达价值学习，为大规模离线决策提供一种计算上更高效、可扩展性更强的新范式。

## 2. 方法论

论文提出 **EVOR（Expressive Value Learning for Offline Reinforcement Learning）**，一种可扩展的离线 RL 方法，其核心思想是同时集成高表达的策略和高表达的价值函数：

- **价值学习阶段（训练时）**：使用流匹配（flow matching）技术学习一个最优的、正则化的 Q 函数。流匹配是一种高表达生成模型，能够拟合复杂的价值分布，从而摆脱传统价值网络在表达力上的限制。
- **策略提取阶段（推理时）**：EVOR 不进行策略蒸馏或 BPTT，而是对学习到的表达价值函数执行**拒绝采样（rejection sampling）** 来提取策略。这种方式实现了高效的优化、正则化以及计算可扩展的搜索，且无需重新训练。

该方法避免了 BPTT 的巨额计算开销，也避免了策略蒸馏带来的复合误差和扩展瓶颈。

## 3. 实验设计

根据提供的文本（仅包含摘要），**实验设计的具体细节未充分披露**。摘要仅陈述：

- **基准任务**：在“一组多样化的离线 RL 任务”（a diverse set of offline RL tasks）上进行了评估。
- **对比方法**：与若干基线方法进行了比较，但摘要中未列出具体基线名称。
- **数据集**：未说明使用了哪些具体数据集（如 D4RL、Meta-World 等）。
- **评估指标**：未说明具体指标（如归一化得分、成功率等）。

因此，基于当前信息无法详细描述实验场景与基准。

## 4. 资源与算力

文中（至少是提供的摘要和元数据部分）**没有说明**所使用的 GPU 型号、数量、训练时长、计算资源规模等任何算力信息。因此无法对此进行总结。

## 5. 实验数量与充分性

从摘要来看，论文声称在多样任务上超越了基线，但**没有给出实验组数、消融实验、统计显著性检验等信息**。由于缺乏详细实验描述，无法判断实验的充分性、客观性与公平性。仅能确认存在多任务的对比实验，但其覆盖范围和严谨性需要查阅完整论文才能评判。

## 6. 主要结论与发现

论文的主要结论是：**EVOR 在多个离线 RL 任务上优于基线方法**，证明了将高表达价值学习整合到离线 RL 中是有益的。该方法通过流匹配训练正则化 Q 函数，并在推理时使用拒绝采样进行策略提取，成功绕过了 BPTT 和策略蒸馏这两个瓶颈，为大规模离线 RL 提供了新的方向，同时减少了计算负担。

## 7. 优点

- **方法创新性**：将高表达生成模型（流匹配）直接用于价值函数学习，而非仅用于策略表示，扩展了离线 RL 中价值函数的设计空间。
- **计算效率**：摆脱了 BPTT，避免了昂贵的训练时反向传播；同时不使用策略蒸馏，避免了复合误差。
- **推理时可扩展**：采用拒绝采样实现推理时策略提取，允许在价值函数指引下进行可扩展的搜索，无需重新训练。
- **问题动机明确**：针对离线 RL 扩展性的核心挑战，给出了清晰的解决思路。

## 8. 不足与局限

- **信息不完整**：提供的文本仅为摘要，缺少实验细节、数据集、基线、超参数等关键信息，无法全面评估其有效性。
- **实验证据有限**：摘要未报告具体性能数值、任务数量或消融研究，使“优于基线”的结论缺乏可量化的支撑。
- **潜在应用限制**：拒绝采样在生成价值函数空间中的效率与高维动作空间的可扩展性未在摘要中说明，可能在实际复杂任务中面临挑战。
- **论文被拒**：根据元数据，该论文为 ICLR-2026 Rejected，虽然评分 7.0，但表明可能仍存在审稿人指出的重要缺陷（如实验不充分或方法有漏洞），需谨慎看待其声称的结果。

（完）
