---
title: Robust Optimization for Mitigating Reward Hacking with Correlated Proxies
title_zh: 利用相关代理奖励的鲁棒优化缓解奖励黑客攻击
authors: "Zixuan Liu, Xiaolin Sun, Zizhan Zheng"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=O3shkBWM2s"
tags: ["query:rl-control"]
score: 7.0
evidence: 基于相关代理奖励的鲁棒强化学习策略优化
tldr: 强化学习常用代理奖励近似真实目标，却易被智能体利用产生奖励黑客行为。本文将该问题建模为对全体相关代理奖励的鲁棒策略优化，而非固定一条代理奖励，推导出相应的鲁棒优化目标与算法。与现有ORPO等方法相比，方法能覆盖更广的相关代理类别并提供更强的鲁棒性保证。这为构建抵御奖励黑客的可靠强化学习智能体提供了新思路。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 代理奖励与真实目标存在偏差时，智能体通过开发意外行为获取高回报，即奖励黑客，现有方法仅针对固定代理奖励。
method: 将奖励黑客问题转化为对一族相关代理奖励的鲁棒策略优化问题，并推导相应的优化算法。
result: 与仅优化固定代理奖励的方法相比，所提方法对更广的代理奖励类别具有鲁棒性保证。
conclusion: 通过鲁棒优化可以系统性地缓解奖励黑客，提升强化学习智能体的安全性。
---

## Abstract
Designing robust reinforcement learning (RL) agents in the presence of imperfect reward signals remains a core challenge. In practice, agents are often trained with proxy rewards that only approximate the true objective, leaving them vulnerable to reward hacking, where high proxy returns arise from unintended or exploitative behaviors. Recent work formalizes this issue using 
r-correlation between proxy and true rewards, but existing methods like occupancy-regularized policy optimization (ORPO) optimize against a fixed proxy and do not provide strong guarantees against broader classes of correlated proxies. In this work, we formulate reward hacking as a robust policy optimization problem over the space of all 
r-correlated proxy rewards. We derive a tractable max-min formulation, where the agent maximizes performance under the worst-case proxy consistent with the correlation constraint. We further show that when the reward is a linear function of known features, our approach can be adapted to incorporate this prior knowledge, yielding both improved policies and interpretable worst-case rewards. Experiments across several environments show that our algorithms consistently outperform ORPO in worst-case returns, and offer improved robustness and stability across different levels of proxy–true reward correlation. These results show that our approach provides both robustness and transparency in settings where reward design is inherently uncertain.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题背景**：在强化学习（RL）中，真实目标往往难以直接形式化，因此实践中智能体常使用**代理奖励（proxy reward）** 来近似真实目标。然而代理奖励与真实目标之间存在偏差，会导致**奖励黑客（reward hacking）** 现象——智能体通过开发非预期或剥削性的行为获取高代理回报，而非真正完成目标任务。
- **现有方法局限**：近期工作使用**r-相关性（r-correlation）** 来刻画代理奖励与真实奖励之间的关系，但现有方法如**ORPO（Occupancy-Regularized Policy Optimization）** 只针对**固定的一个代理奖励**进行优化，无法针对更广泛的、满足相关性约束的代理奖励类别提供强鲁棒性保证。
- **核心研究问题**：如何系统性地设计策略优化方法，使智能体在面对一类代理奖励时，其最坏情况下的真实性能仍有保障，从而缓解奖励黑客风险。
- **整体含义**：该工作将奖励黑客问题重新定义为**在全体满足r-相关性约束的代理奖励空间上的鲁棒策略优化问题**，为构建安全性更高、对奖励设计误差更不敏感的强化学习智能体提供了新视角。

## 2. 方法论：核心思想、关键技术细节与公式流程

- **核心思路**：不再针对单一固定代理奖励进行优化，而是考虑**一族代理奖励**——即所有与真实奖励的r-相关性不低于某阈值τ的代理奖励——并在其中寻找最坏情况（worst-case）下最大化策略真实性能。
- **形式化建模**：
  - 将奖励黑客问题建模为**max-min 鲁棒优化问题**：外层对策略求最大化，内层在满足相关性约束的代理奖励空间中求最小化。
  - 内层最坏情况代理奖励即为“最能诱导策略走上歧途”的奖励函数。
- **可解性推导**：
  - 作者将该 max-min 问题转化为**可计算的（tractable）形式**，在理论上给出了能够直接用于策略更新的鲁棒目标函数。
- **结合特征先验的扩展**：
  - 当奖励函数可以表示为**已知特征的线性函数**时，该方法可进一步整合先验知识，转化为一个增强版本，不仅能得到**更优的策略**，还能输出**可解释的最坏情况奖励（interpretable worst-case rewards）**，帮助研究人员理解策略在何种奖励假设下会失效。
- **算法流程（文字描述）**：
  - 输入：真实奖励相关性约束参数τ、潜在的特征映射（若已知）等；
  - 构造所有满足r-相关约束的代理奖励集合；
  - 求解 max-min 优化问题，得到鲁棒策略；
  - 在含特征线性结构的场景中，同时输出最坏情况下对应的奖励形式，供分析使用。

## 3. 实验设计：数据集/场景、Benchmark 与对比方法

- **实验场景**：论文使用**多个强化学习环境（several environments）** 进行验证，但摘要中未给出具体环境名称（如 MuJoCo、Atari、GridWorld 等）。
- **Benchmark 设定**：实验围绕不同**代理奖励与真实奖励的相关性水平（不同τ值）** 展开，评估方法在各相关性档位下的表现。
- **对比方法**：主要对比的是**ORPO（Occupancy-Regularized Policy Optimization）**——即现有的针对固定代理奖励的代表性方法。
- **评估指标**：核心指标是**最坏情况回报（worst-case returns）**，同时考察鲁棒性与稳定性。

## 4. 资源与算力

- **文中未明确说明**：提供的摘要中**没有**披露任何关于计算资源的信息，例如 GPU 型号与数量、训练时长、使用多少 CPU 节点等。
- 仅有“实验结果来自多个环境”的表述，但没有给出训练成本或基础设施的相关描述。

## 5. 实验数量与充分性

- **实验组数**：摘要提到“several environments”和“across different levels of proxy–true reward correlation”，表明进行了**多环境、多相关性水平**的对比实验，但对具体实验数量（例如多少个环境、多少个相关性档位）未给出细节。
- **消融实验**：未提及消融实验或其他补充实验。
- **充分性与客观性评估**：
  - 优点：多环境、多相关性水平的设计具有一定覆盖面，且对比 ORPO 这一直接相关的方法，具有明确参照。
  - 不足：由于缺少具体环境名称、实验数量、方差/统计数据信息，以及消融实验，**实验充分性难以从摘要层面完全确认**；同时，未提及与更多其他方法（如基于约束的RL、奖励修正方法等）的对比，对比面相对较窄。

## 6. 主要结论与发现

- **方法有效性**：在所有测试环境中，所提出的鲁棒优化方法在**最坏情况回报**上**一致优于 ORPO**。
- **鲁棒性与稳定性**：在**不同类型和不同程度的相关性水平**下，方法均表现出更强的鲁棒性和训练稳定性。
- **可解释性收益**：在线性奖励结构场景中，方法不仅提升了策略性能，还产生了**可解释的最坏情况奖励**，增强了奖励设计的透明度。
- **方法论贡献**：证明了将奖励黑客问题建模为对一族相关代理奖励的鲁棒优化，是缓和奖励黑客的一般且系统性路径。

## 7. 优点与亮点

- **方法层面**：
  - 将鲁棒优化的思想引入奖励黑客问题，从“单一代理”拓展到“一族代理奖励”，理论框架更一般化。
  - 给出可计算的 max-min 优化推导，兼顾理论保证与实际可行性。
  - 支持利用特征先验知识，实现策略优化与可解释性分析的双重收益。
- **实验层面**：
  - 在所有测试环境下相对于 ORPO 均取得更优的 worst-case 指标，结果一致性较强；
  - 在不同相关性水平下考察鲁棒性，体现出一定的系统性。
- **实际意义**：为奖励设计不确定性较强的场景（如大模型 RLHF、自动驾驶、推荐系统等）提供了安全性更高的训练范式。

## 8. 不足与局限

- **实验公开细节不足**：摘要中未提供具体环境名称、实验规模、随机种子数与方差范围等，难以充分评估方法在不同复杂度任务上的泛化能力。
- **对比方法单一**：仅提及与 ORPO 对比，未能看到与更多奖励黑客防御方法（如保守估计、对抗奖励学习、奖励修正等）的比较，可能限制对其相对优势的全面判断。
- **相关性指标假设及其限制**：所有保证均建立在 r-相关性约束这一数学假设上，真实世界代理奖励是否总能被这种约束很好地刻画，尚需讨论。
- **线性特征假设的场景限制**：可解释性增强需要奖励具有线性特征结构，这是一种较强的先验限制，在其他复杂奖励结构（如非线性、神经奖励模型）下未必适用。
- **计算开销未知**：未报告鲁棒优化相对普通优化带来的额外计算成本，可能影响实际部署意愿。
- **缺失消融分析**：未说明各组件（如相关性约束强度、特征先验的使用与否）对最终性能的贡献，方法设计的必要性论证尚有提升空间。

（完）
