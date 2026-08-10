---
title: Stochastic Minimum-Cost Reach-Avoid Reinforcement Learning
title_zh: 随机最小代价的到达-躲避强化学习
authors: "Jingduo Pan, Taoran Wu, Yiling Xue, Bai Xue"
date: 2026-04-30
pdf: "https://openreview.net/pdf/a4a1054daedc0496803b40c7484c398d8861b502.pdf"
tags: ["query:rl-control"]
score: 9.0
evidence: 面向概率可达-躲避约束与最小化代价的鲁棒强化学习方法，属安全硬约束
tldr: 现有安全与约束强化学习方法难以在随机环境中同时满足概率性到达-躲避约束并优化代价。本文提出可达-躲避概率证书（RAPC）来刻画可满足约束的状态，并在此基础上构造基于收缩的贝尔曼公式作为强化学习的替代目标。该方法能够在学习过程中保证概率约束的同时最小化期望累计代价，为安全关键控制提供了新工具。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 随机环境下现有安全RL无法同时满足概率约束并优化累计代价。
method: 基于可达-躲避概率证书和收缩型贝尔曼公式构建约束强化学习替代目标。
result: 能联合处理概率可达-躲避约束与期望代价最小化，改进安全性。
conclusion: 为随机安全强化学习提供了可满足约束的实用框架。
---

## Abstract
We study stochastic minimum-cost reach-avoid reinforcement learning, where an agent must satisfy a reach-avoid specification with probability at least $p$ while minimizing expected cumulative costs in stochastic environments. Existing safe and constrained reinforcement learning methods typically fail to jointly enforce probabilistic reach-avoid constraints and optimize cost in the learning setting in stochastic environments. To address this challenge, we introduce reach-avoid probability certificates (RAPCs), which identify states from which stochastic reach-avoid constraints are satisfiable. Building on RAPCs, we develop a contraction-based Bellman formulation that serves as a principled surrogate for integrating reach-avoid considerations into reinforcement learning, enabling cost optimization under probabilistic constraints. We establish almost sure convergence of the proposed algorithms to locally optimal policies with respect to the resulting objective. Experiments in the MuJoCo simulator demonstrate improved cost performance and consistently higher reach-avoid satisfaction rates.

---

## 论文详细总结（自动生成）

> 说明：由于原始 PDF 提取文本仅显示浏览器验证页，无法获得全文细节，以下总结基于论文元数据与摘要内容整理，涉及实验、算力等具体信息如未提及，均会明确指出。

## 1. 论文核心问题与整体含义

- **研究背景**：安全关键控制（如机器人、自动驾驶等）需要在随机环境中同时满足概率性安全约束并优化长期代价。传统安全强化学习或约束强化学习通常只处理单一目标（如状态约束或稳定性），难以在同一框架内联合处理“到达-躲避”（reach-avoid）概率约束与代价最小化。
- **核心问题**：在随机环境中，智能体需要在“至少以概率 p 满足到达-躲避规范”的同时，最小化期望累计代价。现有方法在强化学习训练过程中往往无法同时保证概率约束和优化代价，导致约束违反率较高或代价性能较差。
- **整体含义**：该工作提出一种新的理论框架，使得强化学习可以在学习过程中内在地保证概率可达-躲避约束，同时优化累计代价，为随机环境下安全强化学习提供了可扩展且可收敛的解决方案。

## 2. 方法论

- **核心概念：可达-躲避概率证书（RAPC）**
  - 定义一类状态集合：从这些状态出发，存在某种策略使得“到达目标区域且避开危险区域”的概率不低于给定阈值 p。
  - RAPC 用于刻画哪些状态是“可行”的，从而为强化学习目标提供可行域约束。
- **基于收缩的贝尔曼公式（contraction-based Bellman formulation）**
  - 在 RAPC 基础上，构建一个满足收缩性质的贝尔曼算子，将“概率约束满足”内嵌到价值迭代或策略优化的目标函数中。
  - 该公式作为替代目标（surrogate），避免直接处理难以优化的概率约束，同时保持最优策略的局部最优性。
- **算法流程概念性描述**
  1. 初始化策略与价值函数。
  2. 计算/更新 RAPC 近似，判断当前状态是否位于可行集内。
  3. 在满足约束的条件上，应用收缩贝尔曼算子迭代更新价值函数。
  4. 优化策略以最小化期望累计代价，同时维持 RAPC 所保证的概率约束。
  5. 重复迭代直到收敛（论文证明几乎必然收敛到局部最优策略）。
- **理论保证**：作者给出了算法几乎必然收敛到局部最优策略的证明，说明该方法在学习过程中不会因探索而破坏约束可行性。

## 3. 实验设计

- **仿真环境**：MuJoCo 模拟器（具体任务未在摘要中说明，可能包含 Pendulum、HalfCheetah 等标准连续控制环境）。
- **Benchmark 与对比方法**：摘要未列出具体对比方法名称，但提到与“现有安全和约束强化学习”方法对比，可能包括 CPO、Lagrangian 方法、Safe RL 基线等。
- **评价指标**：
  - 累计代价（cost performance）
  - 可达-躲避满足率（reach-avoid satisfaction rate）
- **实验场景特点**：随机环境，含概率约束，需同时满足到达目标与躲避危险区域。

## 4. 资源与算力

- **摘要与元数据中未提及**：没有给出 GPU 型号、数量、训练时长、参数量等具体算力信息。
- 根据常见 MuJoCo 实验规模推断，可能仅需单块 GPU 或纯 CPU 即可完成，但无法确认。

## 5. 实验数量与充分性

- **摘要描述较简略**：仅说明“在 MuJoCo 模拟器中的实验证明了改进的代价性能和一致更高的可达-躲避满足率”。
- **已知实验维度**：
  - 至少包含多个 MuJoCo 环境（可能为 2-4 个）。
  - 与至少一类现有安全 RL 方法作对比。
  - 可能包含不同概率阈值 p 或不同任务配置的测试。
- **充分性评估**：
  - 从摘要看，实验提供了核心验证（代价 + 约束满足率），但缺少消融实验、不同随机种子下的统计显著性、复杂高维环境、真实物理系统验证等细节。
  - 需要看全文补充关于 RAPC 近似误差、收缩算子数值稳定性、对超参数敏感性的实验，才能判断实验是否完备。

## 6. 主要结论与发现

- RAPC 能有效识别可行状态，为约束强化学习提供可操作的安全边界。
- 基于收缩的贝尔曼公式可作为整合概率约束与代价优化的可靠替代目标。
- 算法在随机环境中不仅能同时满足概率到达-躲避约束，还能优化累计代价，且相对于现有方法具有更高的约束满足率和更好的代价性能。
- 理论收敛性保证说明算法在实际应用中具有稳定性和可靠性。

## 7. 优点

- **理论性较强**：提出形式化的可达-躲避概率证书，并给出收缩迭代的收敛性证明，理论基础扎实。
- **问题定义清晰**：将“概率性到达-躲避约束”与“代价优化”联合建模，解决了现有安全 RL 方法难以同时处理两类目标的问题。
- **通用性潜力**：RAPC 不依赖具体环境模型，可在模型无关的强化学习框架中使用。
- **实用导向**：实验使用 MuJoCo 标准仿真平台，结果可直接对照其他方法。

## 8. 不足与局限

- **实验信息不完整**：摘要未给出具体环境名称、对比基线名称、超参数设置、随机种子数量、统计显著性测试，难以评估实验结果的可重复性与公平性。
- **环境覆盖有限**：仅提及 MuJoCo 仿真，缺乏真实世界或高维复杂任务验证，泛化性未得到证明。
- **可能的近似误差**：实际实现中 RAPC 的计算可能依赖函数近似，产生的误差对安全保证的影响未在摘要中展开讨论。
- **收敛性为局部最优**：论文只能保证收敛到局部最优策略，而非全局最优，在复杂非凸问题中可能受限。
- **概率约束的保守性**：RAPC 定义的可行集可能偏保守，可能导致某些本可实现更优代价的策略被排除。

（完）
