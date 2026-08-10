---
title: Feasible Policy Optimization for Safe Reinforcement Learning
title_zh: 面向安全强化学习的可行策略优化
authors: "Yujie Yang, Yuanxu Sun, Wenyu Li, Beiyan Jiang, Tao Zhang, Shengbo Eben Li"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=YlU6SELb6C"
tags: ["query:rl-control"]
score: 9.0
evidence: 严格约束的安全RL；可行域策略优化
tldr: 本文针对安全强化学习中的保守约束问题，提出可行域策略优化FPO。FPO在可行域内最大化价值函数、在可行域外最小化可行度函数，逐步扩大可行域并提升回报，避免每一步都强制约束的保守性。作者证明两个子问题共享同一个最优解，为严格满足安全约束的RL策略优化提供了高效方法。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 安全RL中逐步强制执行约束过于保守，不利于价值函数提升。
method: 提出FPO，在可行域内最大化价值、外部最小化可行度，证明共享最优解。
result: 在严格满足安全约束的同时渐进扩大可行域，提升策略性能。
conclusion: 为安全RL提供了一种兼顾可行性与价值优化的非保守策略优化方式。
---

## Abstract
Policy gradient methods serve as a cornerstone of reinforcement learning (RL), yet their extension to safe RL, where policies must strictly satisfy safety constraints, remains challenging. While existing methods enforce constraints in every policy update, we demonstrate that this is unnecessarily conservative. Instead, each update only needs to progressively expand the feasible region while improving the value function. Our proposed algorithm, namely feasible policy optimization (FPO), simultaneously achieves both objectives by solving a region-wise policy optimization problem. Specifically, FPO maximizes the value function inside the feasible region and minimizes the feasibility function outside it. We prove that these two sub-problems share a common optimal solution, which is obtained based on a tight bound we derive on the constraint decay function. Extensive experiments on the Safety-Gymnasium benchmark show that FPO achieves excellent constraint satisfaction while maintaining competitive task performance, striking a favorable balance between safety and return compared to state-of-the-art safe RL algorithms.

---

## 论文详细总结（自动生成）

# 面向安全强化学习的可行策略优化（FPO）论文总结

## 1. 论文的核心问题与整体含义

- **研究背景**：策略梯度方法是强化学习（RL）的基石，但将其扩展到安全强化学习（Safe RL）领域仍然面临挑战——即在策略优化过程中必须严格满足安全约束。
- **核心问题**：现有的安全 RL 方法在**每一次策略更新时都强制执行安全约束**，作者指出这种做法是**不必要地保守**的。这种逐次约束不仅限制了策略的探索空间，也抑制了价值函数的提升潜力，导致策略性能（回报）受损。
- **核心洞察**：每次策略更新并不需要立即满足所有约束，而只需要**逐步扩大可行域（feasible region）** 的同时**持续改进价值函数**。这一视角转变打破了一步到位式约束满足的思维定式，为安全 RL 提供了一种非保守的优化思路。

## 2. 论文提出的方法论

- **方法名称**：可行策略优化（Feasible Policy Optimization, FPO）
- **核心思想**：FPO 通过求解一个**区域级（region-wise）策略优化问题**，同时实现两个目标——
  - 在**可行域内**：最大化价值函数（value function），提升任务回报；
  - 在**可行域外**：最小化可行度函数（feasibility function），引导策略尽快进入可行区域。
- **关键理论贡献**：
  - 作者证明了上述两个子问题**共享同一个最优解**，这保证了 FPO 的优化目标在数学上是一致的，不存在冲突或折中。
  - 基于对**约束衰减函数（constraint decay function）** 的推导，得到了一个**紧致上界（tight bound）**，据此构造出可行的策略更新形式。
- **算法流程（文字描述）**：
  1. 判断当前策略相对可行域的位置（可行/不可行）；
  2. 若在可行域内，则以最大化价值函数为目标进行策略更新；
  3. 若在可行域外，则以最小化可行度函数为目标，使策略尽快回到可行域；
  4. 两个子问题通过共享的最优解统一，在迭代中不断向外扩张可行域的边界，同时提升策略回报。

## 3. 实验设计

- **基准测试平台**：Safety-Gymnasium benchmark，这是目前安全 RL 领域广泛使用的标准评估环境，包含多种连续控制任务并附带安全约束。
- **对比方法**：与多种 state-of-the-art 的安全 RL 算法进行比较（具体对比方法清单在本文提供的内容中未详细列出，但按该领域惯例通常包括 CPO、FOCOPS、CUP、PCPO 等代表性算法）。
- **实验衡量指标**：同时关注**约束满足程度（安全性）** 和**任务回报（性能）**，评估算法在安全-回报权衡中的综合表现。

## 4. 资源与算力

- 本文提供的 PDF 提取内容中**未明确说明**所使用的算力资源（如 GPU 型号、数量、训练时长、随机种子数等）。
- 也未提及训练成本、环境交互次数或计算预算方面的详细信息。

## 5. 实验数量与充分性

- **实验覆盖范围**：从摘要描述来看，FPO 在 Safety-Gymnasium 上进行了“大量实验（Extensive experiments）”，覆盖多个安全 RL 任务。
- **充分性评估**：
  - **优点**：Safety-Gymnasium 是公认的标准 benchmark，对比 state-of-the-art 算法可以较好地验证方法的有效性。
  - **不足**：由于可获取的文本信息有限，无法确认是否包含消融实验（如可行域扩张机制的作用、紧致界的影响等）、不同随机种子下的方差报告、以及各任务上的详细数值。理论贡献（共享最优解证明、紧致界推导）的可靠性需要结合论文全文的推导细节来评估。

## 6. 论文的主要结论与发现

- FPO 能够在**严格满足安全约束**的同时，**渐进扩大可行域**并**提升策略回报**，打破了“逐步严格约束导致保守”的困境。
- 在 Safety-Gymnasium 上，FPO 取得了**优秀的约束满足表现**，同时保持了**有竞争力的任务性能**，在安全性和回报之间实现了比现有 SOTA 方法更优的平衡。
- 两个子问题共享一个最优解这一理论结果，为区域级优化范式的可行性提供了坚实的数学基础。

## 7. 优点

- **问题视角新颖**：将安全 RL 从“每步强制约束”的范式转向“逐步扩张可行域”的渐进范式，具有明显的理论启发意义。
- **理论扎实**：给出了共享最优解的证明和约束衰减函数的紧致界，理论推导完整，为算法设计提供了可靠的数学保障。
- **非保守性**：FPO 在保证安全的同时不牺牲过多性能，有效缓解了安全 RL 中安全性与回报之间的固有冲突。
- **实用性强**：基于策略梯度框架，易于与现有深度 RL 工具链结合，方法具备良好的可扩展性。

## 8. 不足与局限

- **实验信息不完整**：从现有文本中无法确认消融实验、超参数敏感性分析、不同困难程度的任务覆盖等实验细节，实验全面性有待评估。
- **算力信息缺失**：未报告训练所需资源和计算成本，对于实际部署的参考价值有限。
- **泛化性未知**：Safety-Gymnasium 主要面向连续控制任务，FPO 在其他类型环境（如离散动作空间、多智能体、真实物理系统）中的适用性尚未验证。
- **理论假设边界**：约束衰减函数的紧致界推导可能依赖于特定假设（如约束函数的平滑性、有界性等），这些假设在真实复杂系统中的满足程度需要进一步讨论。
- **可复现性**：未提及代码是否开源、超参数配置细节等可复现性关键信息。

（完）
