---
title: "SHAPO: Sharpness-Aware Policy Optimization for Safe Exploration"
title_zh: SHAPO：面向安全探索的锐度感知策略优化
authors: "Kaustubh Mani, Yann Pequignot, Vincent Mai, Liam Paull"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=7cUxi8LbKD"
tags: ["query:rl-control"]
score: 7.0
evidence: 利用认知不确定性和锐度感知悲观更新实现安全强化学习探索，属于不确定性下的概率决策。
tldr: 在安全关键强化学习中，探索需要避开高不确定性区域。本文提出SHAPO，一种锐度感知策略更新规则：在扰动参数处计算梯度，使更新对认知不确定性保持悲观。该方法隐式地为策略梯度重新加权，放大少量危险动作的影响并抑制安全动作，从而将学习偏向保守行为。实验显示SHAPO在保障性能的同时显著提升安全探索质量。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 安全探索是安全关键强化学习的前提，但代理对参数扰动的敏感度可作为未知区域的有效代理。
method: 提出SHAPO更新规则，在扰动参数处评估梯度，使策略更新对认知不确定性保持悲观，隐式重加权策略梯度。
result: 实验证明SHAPO能减少危险动作的影响，提高安全探索的效率，并保持任务性能。
conclusion: 锐度感知更新为安全强化学习提供了一种基于不确定性规避的通用手段。
---

## Abstract
Safe exploration is a prerequisite for deploying reinforcement learning (RL) agents in safety-critical domains. In this paper, we approach safe exploration through the lens of epistemic uncertainty, where the actor’s sensitivity to parameter perturbations serves as a practical proxy for regions of high uncertainty. We propose Sharpness-Aware Policy Optimization (SHAPO), a sharpness-aware policy
update rule that evaluates gradients at perturbed parameters, making policy updates pessimistic with respect to the actor’s epistemic uncertainty. Analytically we show that this adjustment implicitly reweighs policy gradients, amplifying the
influence of rare unsafe actions while tempering contributions from already safe ones, thereby biasing learning toward conservative behavior in under-explored regions. Across several continuous-control tasks, our method consistently improves both safety and task performance over existing baselines, significantly expanding their Pareto frontiers.

---

## 论文详细总结（自动生成）

## SHAPO：面向安全探索的锐度感知策略优化

### 1. 核心问题与整体含义

- **研究背景**：安全关键领域（如自动驾驶、机器人操控）要求强化学习（RL）智能体在部署前必须具备**安全探索**能力，即在学习过程中不能仅追求任务性能，还必须避免危险状态或动作。
- **核心问题**：如何在探索未知环境时，使策略更新对高不确定性区域保持**保守和悲观**，从而有效规避潜在风险？
- **关键洞察**：本文提出，**智能体策略对参数扰动的敏感度**可以作为认知不确定性（epistemic uncertainty）的实用代理。若策略参数的微小扰动会导致输出剧变，说明该区域策略欠拟合、不确定性高，应避免前往。
- **整体意义**：将安全探索问题转化为一个**参数空间中的锐度-悲观化**问题，为安全 RL 提供了一种与模型无关、基于不确定性规避的通用手段，而不需要显式建模风险或不确定性。

### 2. 方法论

- **核心思想**：提出 **Sharpness-Aware Policy Optimization (SHAPO)**，一种锐度感知的更新规则，使策略更新对自身的认知不确定性保持悲观。
- **关键技术细节**：
  - 标准策略梯度在当前位置 θ 处计算梯度；SHAPO 则在**经过扰动的参数 θ + ε(θ)** 处计算梯度，模仿 SAM（Sharpness-Aware Minimization）的思路，但目标是安全而非泛化。
  - 该扰动方向是使策略损失最大化的方向，因此在扰动点评估梯度，等于在“最坏情况”的策略行为下进行更新。
  - 分析表明，这一调整**隐式地对策略梯度重新加权**：
    - **放大**那些数量少但危险的（会导致高不确定性/高风险的）动作对梯度的贡献；
    - **抑制**已经安全、探索充分的动作的贡献；
    - 最终使学习过程在未探索区域偏向保守行为。
- **算法流程概要**（用文字表述）：
  1. 计算当前策略参数下的损失；
  2. 求解一个内部最大化问题，得到使损失上升的扰动方向；
  3. 将参数向该方向扰动；
  4. 在扰动后的参数处反向传播，计算梯度并更新策略；
  5. 重复上述步骤直至收敛。

### 3. 实验设计

- **任务场景**：多个**连续控制任务**（continuous-control tasks），来自标准 RL 安全基准。
- **Benchmark**：属于安全 RL 的典型评估框架，具体任务名称（如 Safety Gym、mujoco 安全变体等）在摘要中未逐一列出。
- **对比方法**：与现有安全 RL 基线进行对比，但原文摘要未列出基线具体名称（如 CPO、PPO-Safe、Lagrangian 方法等），仅说明在安全和任务性能上均超过现有基线。
- **评估指标**：同时衡量**安全性**（危险动作/违规次数）与**任务性能**（累计回报），重点观察两者之间的 Pareto 前沿扩展情况。

### 4. 资源与算力

- **未明确说明**：原文提供的信息中**没有**提及使用的 GPU 型号、数量、训练时长、运行次数等算力细节。
- 若需要了解具体算力开销，需查阅论文全文的实验设置或附录。

### 5. 实验数量与充分性

- **实验规模**：涵盖“多个连续控制任务”，属于多场景验证，并报告了与基线的 Pareto 前沿对比，表明实验设计具有基本的横向对比能力。
- **充分性评估**（基于有限摘要信息）：
  - **覆盖范围**：目前只明确了连续控制任务，未明确包含离散动作、高维视觉输入、真实物理平台等场景，覆盖广度有限。
  - **消融实验**：摘要未提及是否对锐度扰动的幅度、更新频率等关键超参数做了消融分析。
  - **公平性**：是否与最先进的安全 RL 方法（如 CPO、FOCOPS、CUP 等）进行了系统性对比，尚待全文确认。
  - **总体判断**：从摘要看，实验初步证明了方法的有效性，但**充分性尚不能完全下定论**，需要查看全文的详细实验设置。

### 6. 主要结论与发现

- SHAPO 通过锐度感知的扰动梯度更新，能够自然地让策略对高认知不确定性区域保持悲观。
- 这种更新方式的本质是对策略梯度进行**隐式重加权**：放大危险动作影响、压制安全动作，从而在探索不足的区域自动偏向保守。
- 在多个连续控制任务中，SHAPO **同时改善了安全性和任务性能**，有效拓展了安全-性能的 Pareto 前沿，表明安全性与性能并非必然冲突。
- 该方法是一种通用、轻量的策略更新规则，可集成到现有策略梯度框架中。

### 7. 优点

- **思想新颖**：将锐度感知最小化（SAM）的思想引入安全 RL，用参数扰动敏感度替代显式的风险建模，方法简洁而直觉清晰。
- **无需额外结构**：不需要学习不确定性模型、不需要集成网络、不需要显式约束优化，可方便地嵌入策略梯度算法。
- **理论分析**：提供了对梯度重加权效应的解析分析，解释了“为什么锐度感知会带来保守行为”，具有理论支撑。
- **带来双赢**：实验表明安全与性能可以同时提升，而不是简单的安全-性能折中。
- **通用性强**：适用于连续控制任务，有潜力扩展到其他 RL 范式。

### 8. 不足与局限

- **实验范围有限**：仅报告了连续控制任务，缺少离散控制、真实机器人、高维图像输入等场景的验证。
- **缺乏消融与敏感性分析**：摘要未提及对扰动幅度、更新频率、损失函数选择等超参数的消融实验。
- **基线覆盖待确认**：未列出具体对比算法，无法判断是否覆盖了当前最先进的安全 RL 方法。
- **理论假设依赖**：锐度作为不确定性代理的有效性依赖于策略欠拟合区域与真实风险区域的耦合程度，在个别场景下这种耦合可能不成立。
- **算力信息缺失**：无训练成本报告，难以评估方法在实际部署中的计算开销。
- **开放问题**：如何选择扰动步长、如何处理连续动作空间中的高维锐度计算，仍需要进一步探讨。

（完）
