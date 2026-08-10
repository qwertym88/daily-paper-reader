---
title: Off-Policy Safe Reinforcement Learning with Cost-Constrained Optimistic Exploration
title_zh: 带代价约束乐观探索的离策略安全强化学习
authors: "Guopeng Li, Matthijs T. J. Spaan, Julian F. P. Kooij"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=EHs3tSukHC"
tags: ["query:rl-control"]
score: 9.0
evidence: 离策略安全RL，代价受限探索与保守值学习
tldr: 本文针对离策略安全强化学习在代价约束下探索导致约束违反、累积代价估计有偏的问题，提出COX-Q算法。算法引入代价受限的乐观探索策略，解决奖励与代价的梯度冲突，并结合保守的离线分布价值学习，在保持样本效率的同时降低训练和部署中的安全违规。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 离策略安全RL在探索中常忽略代价约束，且累积代价估计存在偏差。
method: 提出COX-Q，结合代价受限乐观探索与保守离线分布值学习。
result: 在保持样本效率的同时减少训练和部署中的安全违规。
conclusion: 为离策略安全RL提供了避免代价-奖励冲突的乐观探索新方法。
---

## Abstract
When safety is formulated as a limit of cumulative cost, safe reinforcement learning (RL) aims to learn policies that maximize return subject to the cost constraint in data collection and deployment. Off-policy safe RL methods, although offering high sample efficiency, suffer from constraint violations due to cost-agnostic exploration and estimation bias in cumulative cost. To address this issue, we propose Constrained Optimistic eXploration Q-learning (COX-Q), an off-policy safe RL algorithm that integrates cost-bounded online exploration and conservative offline distributional value learning. First, we introduce a novel cost-constrained optimistic exploration strategy that resolves gradient conflicts between reward and cost in the action space and adaptively adjusts the trust region to control the training cost. Second, we adopt truncated quantile critics to stabilize the cost value learning. Quantile critics also quantify epistemic uncertainty to guide exploration. Experiments on safe velocity, safe navigation, and autonomous driving tasks demonstrate that COX-Q achieves high sample efficiency, competitive test safety performance, and controlled data collection cost. The results highlight COX-Q as a promising RL method for safety-critical applications.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机与背景）

- **问题背景**：在安全强化学习（Safe RL）中，安全约束通常被定义为累积代价的阈值限制，算法需要学习在最大化奖励回报的同时满足该代价约束，且该约束在**数据采集（训练）与部署（测试）**两个阶段都要成立。
- **现有方法的痛点**：离策略（off-policy）安全RL虽然样本效率高，但存在两大致命缺陷：
  - **代价无关的探索**：探索过程中只顾收集高奖励样本，忽略对代价约束的控制，导致训练阶段频繁违反安全约束；
  - **累积代价的估计偏差**：对累积代价的估计存在系统性偏差，导致最终学到的策略在部署时难以保证安全性。
- **研究意义**：本文针对上述两个缺口提出新算法，目标是在维持离策略RL高样本效率的同时，做到“训练时安全”和“部署时安全”两头兼顾，适用于安全关键型应用。

## 2. 论文提出的方法论：COX-Q 算法

- **核心思想**：将“乐观探索”与“保守估计”结合起来——在**动作空间**上探索时主动避免代价-奖励冲突，在**价值学习**上对代价做偏保守的估计，二者共同压低训练与部署中的约束违反率。
- **关键技术细节**：
  1. **代价受限的乐观探索（Cost-Constrained Optimistic Exploration）**
     - 在动作空间中显式求解奖励梯度方向与代价梯度方向，识别二者冲突；
     - 当冲突出现时，策略更新会优先满足代价约束，而非盲目追逐奖励；
     - 采用**自适应信任域（adaptive trust region）**机制，根据当前代价水平动态调整探索幅度，从而把训练过程的累积代价控制在预算内。
  2. **保守的离线分布价值学习（Conservative Offline Distributional Value Learning）**
     - 使用**截断的分位数评论家（truncated quantile critics）**来学习累积代价的分布，稳定代价价值学习；
     - 分位数形式不仅能刻画代价分布，还能**量化认知不确定性（epistemic uncertainty）**，并将该不确定性作为探索方向的引导信号，实现“不确定性高的地方谨慎探索”。
- **算法流程**：COX-Q 属于典型的 actor-critic + off-policy（如Q-learning式）框架：critic 用分位数估计回报与代价分布，actor 在每步更新前先判断奖励/代价梯度冲突并决定是否退回到安全区域，再以自适应步长执行探索。全文未给出完整伪代码，但流程可概括为“评估代价风险 → 决定探索方向 → 保守更新价值 → 安全部署”。

## 3. 实验设计

- **实验任务与场景**（均来自摘要明确提及）：
  - **Safe Velocity（安全速度控制）**
  - **Safe Navigation（安全导航）**
  - **Autonomous Driving（自动驾驶）**
- **Benchmark 定位**：上述任务是安全RL领域的常用基准，属于连续控制 + 代价约束的场景。
- **对比方法**：论文摘要未列出具体的基线算法名称；仅从表述推断，应对比了典型离策略安全RL方法（对比是否安全、样本效率、训练代价等指标），但具体基线不明。

## 4. 资源与算力

- **论文未明确说明**使用了多少 GPU（型号、数量）以及训练时长等计算资源信息。提供的提取文本中完全不包含算力配置相关内容，因此无法总结。若需复现或评估算力成本，需要查阅完整论文的实验设置部分。

## 5. 实验数量与充分性

- **实验数量**：从摘要可知至少包含 **3 个任务场景**（安全速度、安全导航、自动驾驶）。但未提供：
  - 是否做了消融实验（如去掉乐观探索 / 去掉保守分位数学习的变体对比）；
  - 每个任务下跑了多少个 random seeds、是否报告方差；
  - 训练曲线、代价曲线等细节。
- **充分性评估**：三个连续控制任务是标准安全RL基准，覆盖面中等。但由于缺乏消融、基线列表和随机种子数等信息，**无法从目前文本判断实验的完整度与统计充分性**。摘要声称“高样本效率、有竞争力的测试安全表现、受控的数据采集代价”，结论方向积极，但证据细节不足。

## 6. 论文的主要结论与发现

- **主要成果**：提出的 COX-Q 算法在安全速度、安全导航、自动驾驶三个任务上：
  - **保持高样本效率**（继承了离策略RL的优点）；
  - **测试阶段安全表现有竞争力**（部署时约束违反率低）；
  - **数据采集代价得到有效控制**（训练过程中的累积代价也受限）。
- **总体判断**：COX-Q 提供了一种新的离策略安全RL范式——在探索阶段就显式考虑代价约束，而非事后修正，为安全关键场景提供了一种有效的实用方法。

## 7. 优点（方法或实验设计的亮点）

- **针对性强**：同时解决离策略安全RL的两大顽疾——探索期的代价失控与累积代价的估计偏差，问题定位准确。
- **机制新颖**：在**动作空间解析奖励-代价梯度冲突**的做法比单纯在目标函数上加拉格朗日乘子更精细，能从根本上避免“为奖励牺牲安全”的更新方向。
- **探索与安全解耦**：用“自适应信任域”控制探索范围，用“分位数不确定性”引导探索方向，两个机制配合既高效又谨慎。
- **价值学习稳健**：截断分位数评论家比传统期望值估计更稳健，还能附带不确定性估计，一石二鸟。
- **应用价值**：自动驾驶、导航等实验场景贴近真实安全关键系统，结论有落地潜力。

## 8. 不足与局限

- **信息不完整**：提取文本仅包含摘要与元数据，缺少方法细节、公式、伪代码、完整实验设置，因此对算法内部机制和实验严谨性的判断受限。
- **实验覆盖有限**：
  - 只有3个连续控制任务，缺少高维视觉输入、真实硬件或仿真到现实的迁移验证；
  - 未在多智能体、部分可观测等复杂场景下检验。
- **对比基线不明**：摘要未列出对比算法名称，无法判断相较最新SOTA（如基于拉格朗日、基于Lyapunov、基于模型的方法）的优势幅度。
- **应用限制**：算法依赖代价信号可分解为动作梯度，若环境代价函数不可微/不明朗，梯度冲突求解可能失效；分位数评论家在极高维动作空间中的计算成本也可能较高。

**（完）**
