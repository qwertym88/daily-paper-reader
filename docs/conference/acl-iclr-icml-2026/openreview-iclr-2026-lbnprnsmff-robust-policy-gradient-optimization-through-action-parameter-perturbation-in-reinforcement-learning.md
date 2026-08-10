---
title: Robust Policy Gradient Optimization through Action Parameter Perturbation in Reinforcement Learning
title_zh: 通过动作参数扰动实现鲁棒策略梯度优化
authors: "Md Masudur Rahman, Juan Wachs, Yexiang Xue"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=lbNPrnSmfF"
tags: ["query:rl-control"]
score: 7.0
evidence: 优化中通过动作参数扰动实现鲁棒策略梯度
tldr: 策略梯度方法容易陷于过早收敛和泛化不佳，尤其在on-policy状态下探索有限。该工作提出鲁棒策略优化（RPO），仅在优化阶段对策略参数施加扰动，从而平滑损失景观并隐式正则化学习。与熵正则化或动作噪声等方法相比，RPO直接作用于优化过程，避免敏感超参，降低对局部不规则性的敏感度，提升策略优化的鲁棒性。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 策略梯度方法容易过早收敛和泛化不佳，现有熵正则化或动作噪声方案需敏感调参或改变交互过程。
method: 提出RPO算法，仅在优化阶段扰动策略参数以平滑损失景观，实现隐式正则化。
result: 降低对局部不规则性的敏感度，改善训练稳定性和泛化能力，且无需修改交互过程。
conclusion: 为策略梯度优化提供轻量鲁棒化增强手段，可推广应用到多种强化学习算法。
---

## Abstract
Policy gradient methods have achieved strong performance in reinforcement learning, yet remain vulnerable to premature convergence and poor generalization, especially in on-policy settings where exploration is limited. Existing solutions typically rely on entropy regularization or action noise, but these approaches either require sensitive hyperparameter tuning or alter the interaction dynamics rather than the optimization process itself. In this paper, we propose Robust Policy Optimization (RPO), a policy gradient method that introduces perturbations to the policy parameters only during optimization. This approach smooths the loss landscape and implicitly regularizes learning, reducing sensitivity to local irregularities while leaving policy behavior during data collection unchanged. We provide a theoretical perspective showing that RPO implicitly biases updates toward flatter and more stable solutions. Empirically, RPO significantly improves upon PPO and entropy-regularized variants across diverse continuous control benchmarks, achieving faster convergence, higher returns, and greater robustness.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题背景**：策略梯度方法（如 PPO）在强化学习中表现优异，但在 on-policy 环境下容易陷入**过早收敛**和**泛化能力差**的问题，根本原因之一是探索受限。
- **现有方案的不足**：
  - **熵正则化**：需要敏感的超参数调优，容易破坏训练稳定性。
  - **动作噪声**：改变了智能体与环境交互的动态过程，而非优化过程本身，可能引入偏差。
- **核心研究问题**：能否通过**只修改优化过程**、不改变数据采集行为的方式，提高策略梯度训练的鲁棒性和泛化能力？

## 2. 提出的方法论（RPO）

- **核心思想**：仅在**优化阶段**对策略参数施加小规模扰动，从而**平滑损失景观**，实现对学习的**隐式正则化**。
- **关键技术细节**：
  - 扰动作用于策略参数，而不是动作空间；训练过程中采集数据时的策略行为保持不变。
  - 通过对损失景观的平滑处理，降低对局部不规则性的敏感性，使梯度更新偏向更“平坦”和更稳定的解。
  - 与手动调熵正则化或添加动作噪声相比，RPO 直接作用于优化过程，避免敏感超参，也无需改变交互过程。
- **理论视角**：论文给出理论解释，表明 RPO 隐式地将更新偏向**平坦且稳定**的局部最优解，从而提升泛化能力。
- **算法流程示意**：
  1. 采样一批状态-动作-回报数据（策略行为不受扰动影响）。
  2. 在计算策略梯度时，对当前策略参数施加随机扰动（如以某种分布采样扰动向量）。
  3. 基于扰动后的参数计算或近似梯度，更新策略参数。
  4. 重复迭代；扰动仅在梯度和参数更新阶段存在，不用于数据采集。
- 注意：原始文本未给出完整公式，以上为基于摘要的可还原描述。

## 3. 实验设计

- **场景与基准**：连续控制基准任务（continuous control benchmarks），但摘要未列出具体任务名（如 MuJoCo、PyBullet 等未明确）。
- **对比方法**：
  - **PPO**（基线策略梯度方法）。
  - **熵正则化变体**（熵正则化的 PPO）。
- **评估指标**：收敛速度、累计回报、鲁棒性。
- **主要结果**：RPO 在多样连续控制基准上显著优于 PPO 和熵正则化变体，实现**更快收敛、更高回报、更强鲁棒性**。

## 4. 资源与算力

- **原文未明确说明**：摘要和元数据中**没有提到 GPU 型号、数量、训练时长、计算资源规模**等信息。
- 若需评估可复现性，该信息缺失是一个局限。

## 5. 实验数量与充分性

- **实验数量**：摘要仅提及“diverse continuous control benchmarks”，但未给出具体环境数量、重复运行次数、随机种子数、消融实验细节。
- **充分性评估**：
  - 从现有信息看，**实验覆盖不够全面**，缺少离散动作空间、真实机器人场景等更广泛验证。
  - 是否进行了消融实验（如扰动幅度、扰动分布类型的影响）未在文本中明确。
  - 公平性：对比了 PPO 和熵正则化变体，但未提及是否对基线进行了同等超参数调优，因此公平性难以完全确认。
- 综合来看，现有摘要提供的信息**不足以证明实验的充分性和公平性**，需要查阅完整论文才能判断。

## 6. 主要结论与发现

- **RPO 有效**：仅扰动策略参数的优化过程即可平滑损失景观，提高策略梯度方法的训练稳定性和泛化能力。
- **优于现有方法**：在连续控制基准上，RPO 比 PPO 和熵正则化变体收敛更快、回报更高、鲁棒性更强。
- **实现轻量**：不改变交互过程，不需要敏感的熵系数调参，可以直接嵌入多种策略梯度算法。

## 7. 优点

- **方法创新**：聚焦于优化过程而非交互或奖励设计，为策略梯度鲁棒化提供新视角。
- **隐式正则化**：概念上简洁，通过参数扰动实现平坦极小值偏好，有理论支撑。
- **实用性强**：轻量、易集成，可推广到 PPO 等多种策略梯度算法。
- **保持交互不变**：避免动作噪声带来的扰动问题，更利于真实系统应用。

## 8. 不足与局限

- **实验信息不完整**：摘要中未给出具体环境、任务数量、运行随机种子、消融实验等详细内容，验证力度有限。
- **理论深度有限**：仅提及“提供理论视角”，未展示具体定理和证明，严谨性待考。
- **超参数引入**：虽然避免熵系数，但扰动幅度等新超参数仍需调优，其敏感性未讨论。
- **适用场景局限**：主要在连续控制上验证，未覆盖离散动作空间、多智能体、真实机器人硬件等。
- **算力缺失**：未报告资源消耗，影响可复现性和工程参考价值。
- **元数据标注为 ICLR-2026-Rejected-Public**：说明该工作可能未被会议接收，需注意其贡献是否被评审认为存在不足。

（完）
