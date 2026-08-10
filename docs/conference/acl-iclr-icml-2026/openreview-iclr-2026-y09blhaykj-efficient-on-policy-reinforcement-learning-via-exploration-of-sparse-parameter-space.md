---
title: Efficient On-Policy Reinforcement Learning via Exploration of Sparse Parameter Space
title_zh: 通过稀疏参数空间探索实现高效同策略强化学习
authors: "Xinyu Zhang, Aishik Deb, Klaus Mueller"
date: 2025-09-16
pdf: "https://openreview.net/pdf?id=y09blHAYKj"
tags: ["query:rl-control"]
score: 7.0
evidence: 利用稀疏参数空间探索提升同策略强化学习策略优化效率
tldr: 以PPO为代表的同策略强化学习每次只沿单个随机梯度方向更新，忽视了参数空间中丰富的局部结构。本文发现同一迭代内策略checkpoint周围的邻近区域存在性能更高的解，据此提出可插拔流水线ExploRLer。ExploRLer系统地探索代理梯度更新未覆盖的邻域，与PPO、TRPO等算法结合后显著提升样本效率和最终性能。该方法为同策略强化学习提供了即插即用的性能增强工具。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 同策略策略梯度方法一次只沿单一随机梯度方向更新，未充分利用参数空间局部结构，且代理梯度与真实奖励景观相关性差。
method: 提出ExploRLer插件式流水线，在每次更新时系统探测同策略代理梯度更新周围的未探索邻域。
result: 在多个连续控制任务上，ExploRLer显著提升PPO和TRPO的样本效率与最终回报。
conclusion: 通过稀疏参数空间探索，可以低成本提升现有同策略强化学习算法的性能。
---

## Abstract
Policy-gradient methods such as Proximal Policy Optimization (PPO) are typically updated along a single stochastic gradient direction, leaving the rich local structure of the parameter space unexplored. Prior work has shown that the surrogate gradient is often poorly correlated with the true reward landscape. Building on this insight, we visualize the parameter space spanned by policy checkpoints within an iteration and reveal that higher-performing solutions often lie in nearby unexplored regions. To exploit this opportunity, we introduce ExploRLer, a pluggable pipeline that seamlessly integrates with on-policy algorithms such as PPO and TRPO, systematically probing the unexplored neighborhoods of surrogate on-policy gradient updates. Without increasing the number of gradient updates, ExploRLer achieves significant improvements over the baselines in complex continuous control environments. Our results demonstrate that iteration-level exploration provides a practical and effective way to strengthen on-policy reinforcement learning and offer a fresh perspective on the limitations of the surrogate objective.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：以 PPO 为代表的同策略强化学习算法，每一轮更新时只沿着单一的随机梯度方向进行参数优化，完全忽略了参数空间中丰富的局部结构。这导致算法无法充分利用参数空间中可能存在的更高性能区域。
- **关键洞察**：已有研究表明，代理梯度（surrogate gradient）与真实奖励景观（true reward landscape）之间的相关性往往很差。作者进一步通过可视化同一迭代内策略 checkpoint 张成的参数空间，发现**性能更高的解往往就位于当前策略附近的未探索邻域中**，但常规的梯度更新并不会访问这些区域。
- **研究意义**：这一观察表明，单纯依赖梯度方向更新在策略优化中存在根本性局限，**迭代级别的参数空间探索**可以作为现有同策略算法的一种有效且低成本的补充手段。

## 2. 方法论：核心思想、技术细节与算法流程
- **核心思想**：提出一种名为 **ExploRLer** 的可插拔（pluggable）流水线，无需修改底层强化学习算法本身，即可系统性地探测代理同策略梯度更新周围未被探索的邻域，寻找性能更优的策略参数。该过程**不增加梯度更新的次数**。
- **关键技术细节**（基于元数据可提取的信息）：
  - 采用稀疏参数空间探索策略，即不是在完整参数空间中做全维度的搜索，而是针对性地、稀疏地探测梯度更新附近的局部区域。
  - 该流水线设计为“即插即用”，可以无缝集成到 PPO、TRPO 等同策略算法中。
- **算法流程**（文字说明）：
  1. 基础算法（如 PPO、TRPO）照常计算代理梯度并生成候选更新方向；
  2. ExploRLer 在该候选更新方向周围的未探索邻域中，进行系统性的稀疏采样与探测；
  3. 经过评估后，选择邻域中性能更优的参数点作为实际更新结果；
  4. 整个过程在迭代级别完成，不改变基础算法的梯度计算次数。
- **注意**：论文元数据信息中未提供具体的数学公式或伪代码，核心方法以流水线架构描述为主。

## 3. 实验设计
- **实验场景/Benchmark**：采用**多个复杂的连续控制环境**作为测试基准（元数据未列出具体环境名称，如 MuJoCo、Robosuite 等未明确说明）。
- **对比方法**：以 **PPO 和 TRPO** 作为基线算法，分别对比“原生算法”与“集成 ExploRLer 后”的版本。其核心指标是**样本效率**和**最终回报**。

## 4. 资源与算力
- **未明确说明**：论文元数据及摘要中**未提及**使用了多少 GPU（型号、数量）、训练时长、计算资源总量等具体算力信息。因此无法评估该方法在算力成本上的具体开销。

## 5. 实验数量与充分性
- **实验数量**：元数据只提到“多个连续控制任务”，并强调在复杂环境上取得“显著改进”。但**未给出具体实验数量**（如多少个环境、多少个随机种子、是否包含消融实验等）。
- **充分性评估**：由于缺乏详细的实验清单和消融分析信息，我们无法完全判断实验的充分性。从已有信息看：
  - **客观性**：以 PPO 和 TRPO 为基线相对公平，因为 ExploRLer 未修改基线的梯度计算次数。
  - **不足之处**：缺少关于超参数敏感性、不同探索策略选择、以及与其他探索方法的对比分析，这些都会影响对方法普适性的判断。

## 6. 主要结论与发现
- ExploRLer 在**不增加梯度更新次数**的前提下，能够显著提升 PPO、TRPO 在复杂连续控制环境中的**样本效率和最终回报**。
- 迭代级别的参数空间探索是**实用且有效**的，可以作为增强现有同策略强化学习算法的通用手段。
- 该工作揭示了代理目标（surrogate objective）在策略优化中的局限性，为理解同策略强化学习的性能瓶颈提供了**新的视角**。

## 7. 优点
- **即插即用设计**：无需改动底层算法，可以低成本地集成到主流同策略算法中，工程实用性强。
- **洞察新颖**：通过可视化揭示“更高性能的解位于未探索的附近邻域”这一现象，为改进同策略算法提供了全新思路。
- **效率提升显著**：在不增加梯度更新次数的前提下获得实质性性能提升，说明该方法并非简单地增加计算量，而是通过更聪明的探索策略获取额外收益。

## 8. 不足与局限
- **实验细节披露不足**：元数据中未列出具体环境名称、实验种子数量、消融实验详情，难以完全客观评估方法的稳健性和泛化能力。
- **算力信息缺失**：未报告训练所需的计算资源，无法判断该方法在算力上是否真的“便宜”。
- **理论分析不足**：缺乏对所提出探索策略的收敛性保证或理论边界分析，更多依赖实验验证。
- **应用范围有限**：仅在连续控制任务上验证，未涉及离散动作空间、多智能体、真实机器人等更广泛场景。
- **被拒稿状态**：该论文为 ICLR-2026 Rejected Public，意味着评审人可能认为其中存在某些不足，虽然元数据未给出具体评审意见，但需谨慎对待其结论的稳健性。

（完）
