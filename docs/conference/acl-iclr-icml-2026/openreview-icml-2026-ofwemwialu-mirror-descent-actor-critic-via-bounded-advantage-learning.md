---
title: Mirror Descent Actor Critic via Bounded Advantage Learning
title_zh: 通过有界优势学习的镜像下降Actor-Critic
authors: Ryo Iwaki
date: 2026-04-30
pdf: "https://openreview.net/pdf/f0142beb317f354de9f7a2dea571e500e62f966f.pdf"
tags: ["query:rl-control"]
score: 9.0
evidence: 基于镜像下降与有界优势学习的Actor-Critic连续动作算法
tldr: 镜像下降值迭代（MDVI）结合KL散度和熵正则化虽有理论保证，但在连续动作域并未超越强熵正则化方法。本文提出镜像下降Actor-Critic（MDAC），将MDVI实例化为连续动作域的actor-critic算法。关键改进是在评论家损失中约束actor对数概率项的范围，相比朴素实例显著提升经验性能。这为连续控制任务中正则化强化学习提供了新的架构选择。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: KL-熵正则化方法在连续动作域不如纯熵正则化方法，现有MDVI缺少有效的actor-critic实现。
method: 提出MDAC，将镜像下降值迭代实现为连续动作域的actor-critic，并限制actor对数概率项以稳定训练。
result: 实验显示，加入对数概率边界后，MDAC在连续动作基准上显著优于朴素实现。
conclusion: 界限化的对数概率能显著提升正则化actor-critic在连续控制中的表现。
---

## Abstract
Regularization is a core component of recent Reinforcement Learning (RL) algorithms. Mirror Descent Value Iteration (MDVI) uses both Kullback-Leibler divergence and entropy as regularizers in its value and policy updates. Despite its empirical success in discrete action domains and strong theoretical guarantees, the performance of KL-entropy-regularized methods does not surpass that of a strong entropy-only-regularized method in continuous action domains. In this study, we propose Mirror Descent Actor Critic (MDAC) as an actor-critic style instantiation of MDVI for continuous action domains, and show that its empirical performance is significantly boosted by bounding the actor's log-probability terms in the critic's loss function, compared to a non-bounded naive instantiation. Further, we relate MDAC to Advantage Learning by recalling that the actor's log-probability is equal to the regularized advantage function in tabular cases, and theoretically discuss when and why bounding the advantage terms is validated and beneficial. We also empirically explore effective choices for the bounding functions, and show that MDAC performs better than strong non-regularized and entropy-only-regularized methods with an appropriate choice of the bounding functions.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- 正则化是近期强化学习（RL）算法的核心组件。MDVI（Mirror Descent Value Iteration，镜像下降值迭代）在价值更新与策略更新中同时使用 **KL 散度**和**熵**作为正则项，并拥有坚实的理论保证。
- MDVI 在**离散动作域**已取得实证成功，但在**连续动作域**中，KL-熵正则化方法的性能未能超越强熵-only 正则化方法（如 SAC 类算法）。
- 现有 MDVI 缺乏针对连续动作域的高效 actor-critic 实现，这是该文要填补的空白。
- 论文整体目标是：为连续动作域提供一个 MDVI 风格的 actor-critic 算法，并解决其在实际应用中的性能短板。

## 2. 论文提出的方法论（核心思想与关键技术）

- **算法名称**：MDAC（Mirror Descent Actor Critic，镜像下降 Actor-Critic）。
- **核心思路**：将 MDVI 实例化为适用于连续动作域的 actor-critic 架构，使 KL-熵正则化的理论优势在连续控制任务中得以落地。
- **关键改进**：在 critic（评论家）的损失函数中，**对 actor（演员）的对数概率项施加边界（bounding）限制**。这一看似简单的约束相比朴素（不加边界）实例化能显著提升经验性能。
- **理论联系**：论文回顾了在表格（tabular）情形下，**actor 的对数概率恰好等于正则化优势函数（regularized advantage function）**，因此“限制 actor 对数概率”本质上等同于“限制优势项（advantage term）”。
- **理论分析**：从 Advantage Learning 的角度出发，论文理论上讨论了**何时以及为何**对优势项施加边界是合理且有帮助的。
- **边界函数选择**：论文还实证探索了多种边界函数（bounding functions）的有效选择，说明不同边界形式对性能有显著影响。

## 3. 实验设计（数据集 / 场景 / 基准 / 对比方法）

- **实验场景**：在**连续动作域基准任务**上进行评估（根据上下文推测为连续控制类标准 benchmark，如 MuJoCo 等，但提供的文本中未列出具体环境名称）。
- **对比方法**：
  - 非正则化（non-regularized）强基线方法；
  - 熵-only 正则化（entropy-only-regularized）强基线方法；
  - 朴素的 MDAC 实例化（未施加对数概率边界）作为自身消融对比。
- **实验目的**：
  - 验证施加边界后的 MDAC 是否优于朴素实例化；
  - 验证 MDAC 在合适的边界函数下能否超过非正则化与熵-only 正则化强基线；
  - 比较不同边界函数设置的性能差异。

## 4. 资源与算力

- 提供的论文文本中**未明确提及**所使用的 GPU 型号、数量、训练时长、随机种子数等资源与算力信息。
- 因此无法从已有材料中给出关于计算资源的具体细节。

## 5. 实验数量与充分性

- 从摘要可识别出的实验类别至少包括：
  - **主实验**：有界 vs. 无界的 MDAC 实例化对比；
  - **基线对比**：MDAC vs. 非正则化 / 熵-only 正则化方法；
  - **消融探索**：不同边界函数的有效性比较。
- 实验设计整体上**结构较完整**，同时覆盖了性能对比、算法自身消融和设计选择探索。
- **不足之处**：由于只能获得摘要层面的信息，无法判断具体的环境数量、每个任务的独立实验次数、统计显著性检验等细节，因此对实验充分性的全面评估受限。
- 从已有证据看，实验结论与论文主张（bound 显著提升性能）是一致的，设计具备基本的客观性和公平性（与强基线对比、自身消融并行）。

## 6. 主要结论与发现

- 对 actor 对数概率项施加边界控制，能够**显著提高** MDAC 在连续动作域中的经验性能，这是论文的核心实证结论。
- 在合适的边界函数选择下，MDAC **优于非正则化方法**和**熵-only 正则化方法**（后者为连续域中此前较强的正则化方案）。
- 论文通过表格情形下的“actor 对数概率 = 正则化优势”这一等价关系，将 MDAC 与 Advantage Learning 建立联系，为边界技巧提供了理论依据。
- 该工作表明：**边界化（bounded）的优势学习结合镜像下降更新，是连续控制任务中一种有前景的正则化 RL 架构选择**。

## 7. 优点（方法与实验设计的亮点）

- **理论与实践的衔接**：巧妙地将 actor 对数概率与正则化优势函数建立等价关系，用 Advantage Learning 的理论框架解释边界技巧的合理性，而不只是经验调参。
- **简洁实用的改进**：只通过在 critic 损失中限制 actor 对数概率范围，就实现了显著的性能提升，方法轻量、易于集成到现有 actor-critic 框架中。
- **填补空白**：首次将 MDVI 有效实例化到连续动作域，为 KL-熵正则化方法提供了可与强熵正则化方法竞争的实现路径。
- **系统性探索**：对不同边界函数进行实证比较，使算法设计具有一定的可迁移性与参考价值。

## 8. 不足与局限

- **实验细节透明度有限**（基于当前可获取的材料）：具体连续动作 benchmark 的名称、环境数量、训练预算和超参数配置均未在提供文本中列出，难以完全复现。
- **理论论证的适用性**：关于“对数概率等于优势函数”的等价关系在表格情形下成立，而连续动作域中该关系的近似程度与边界策略的普适性仍需进一步论证。
- **基线范围**：摘要只提及强非正则化与熵-only 正则化基线，未说明是否与更多主流连续控制算法（如 PPO、TD3 等）进行了系统对比。
- **边界函数的敏感性**：结果显示性能高度依赖边界函数的选择，这意味着算法需要针对任务进行调整，泛化性可能存在隐患。
- **算力与可扩展性评估缺失**：没有提供计算资源使用量、训练成本或大规模任务上的表现，影响了实际部署价值的判断。

（完）
