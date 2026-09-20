---
title: Making Offline Model-Based Reinforcement Learning Work on Real Robots
title_zh: 让离线基于模型的强化学习在真实机器人上奏效
authors: "Chenhao Li, Andreas Krause, Marco Hutter"
date: 2025-09-11
pdf: "https://openreview.net/pdf?id=rbNOhbdQ0v"
tags: ["query:koopman-rl"]
score: 5.0
evidence: 面向真实机器人的离线基于模型强化学习与世界模型
tldr: 离线模型强化学习虽数据高效，但在真实机器人上受复合误差与分布偏移困扰，难以应对噪声、有偏与部分可观测数据。本文提出使离线MBRL在真实机器人上有效的流程RWM-O，为自回归世界模型引入认知不确定性估计，以支持长时程想象rollout与稳健控制。结果表明该流程提升了在物理机器人上的鲁棒性，推动了离线基于模型强化学习的实际落地。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 离线基于模型强化学习在真实机器人上受复合误差与分布偏移影响，难以稳健应用。
method: 提出RWM-O，为自回归世界模型加入认知不确定性估计，支持长时程想象rollout。
result: 提升在物理机器人上的稳健性与数据效率。
conclusion: 推动离线基于模型强化学习从仿真走向真实机器人。
---

## Abstract
Reinforcement Learning (RL) has achieved impressive results in robotics, yet high-performing pipelines remain highly task-specific, with little reuse of prior data. Offline Model-based RL (MBRL) offers greater data efficiency by training policies entirely from existing datasets, but suffers from compounding errors and distribution shift in long-horizon rollouts. Although existing methods have shown success in controlled simulation benchmarks, robustly applying them to the noisy, biased, and partially observed datasets typical of real-world robotics remains challenging. We present a principled pipeline for making offline MBRL effective on physical robots. Our RWM-O extends autoregressive world models with epistemic uncertainty estimation, enabling temporally consistent multi-step rollouts with uncertainty effectively propagated over long horizons. We combine RWM-O with MOPO-PPO, which adapts uncertainty-penalized policy optimization to the stable, on-policy PPO framework for real-world control. We evaluate our approach on diverse manipulation and locomotion tasks in simulation and on a real quadruped, training policies entirely from offline datasets. The resulting policies consistently outperform model-free and uncertainty-unaware model-based baselines, and fusing real-world data in model learning further yields robust policies that surpass online model-free baselines trained solely in simulation.

---

## 论文详细总结（自动生成）

> 说明：当前提供的“论文 PDF 提取文本”实际为 OpenReview 的 CAPTCHA 验证页面，未包含论文正文。因此以下总结主要依据摘要、元数据与 tldr 信息；凡正文未提供的细节，均标注为“未提供/无法核实”。

# 论文总结：Making Offline Model-Based Reinforcement Learning Work on Real Robots

## 1. 核心问题与整体含义
- **研究动机**：强化学习在机器人领域已有显著成果，但高性能流程通常高度任务特定，难以复用先验数据。
- **核心问题**：离线基于模型的强化学习（Offline MBRL）虽能完全从已有数据集中训练策略，具有较高数据效率，但在长时程 rollout 中面临**复合误差**与**分布偏移**。
- **现实挑战**：真实机器人数据通常带有噪声、偏差且部分可观测，现有方法虽在受控仿真基准中成功，但难以稳健迁移到真实机器人。
- **整体含义**：论文试图提出一套原则性流程，使离线 MBRL 能在物理机器人上真正有效，推动其从仿真走向真实应用。

## 2. 方法论：核心思想与关键技术
- **核心方法 RWM-O**：在自回归世界模型中加入**认知不确定性估计**，使模型能够进行时间一致的多步 rollout，并在长时程中有效传播不确定性。
- **策略优化组合**：将 RWM-O 与 **MOPO-PPO** 结合，把不确定性惩罚策略优化适配到稳定、on-policy 的 PPO 框架中，以服务真实机器人控制。
- **算法流程（文字描述）**：
  - 使用离线数据集训练自回归世界模型；
  - 对模型预测引入认知不确定性估计；
  - 在想象 rollout 中传播不确定性，支持长时程多步预测；
  - 在策略优化中对不确定性进行惩罚，降低模型偏差带来的风险；
  - 使用 PPO 进行稳定 on-policy 策略更新，得到可用于真实机器人的控制策略。
- **公式与损失函数**：正文未提供，无法总结具体数学形式。

## 3. 实验设计
- **场景**：仿真中的多种操作任务与运动任务，以及真实四足机器人。
- **数据设置**：策略完全从离线数据集训练；此外，在模型学习中融合真实世界数据。
- **Benchmark**：摘要未给出具体 benchmark 名称，仅说明覆盖仿真操作/运动和真实四足任务。
- **对比方法**：
  - model-free 基线；
  - 不考虑不确定性的 model-based 基线；
  - 仅在仿真中训练的 online model-free 基线，用于比较融合真实数据后的模型学习效果。
- **评价指标**：未提供具体指标、成功率或回报数值。

## 4. 资源与算力
- 论文摘要与元数据中**未提及** GPU 型号、数量、训练时长、参数量、计算预算或仿真环境算力开销。
- 因此无法总结资源与算力使用情况。

## 5. 实验数量与充分性
- 摘要仅说明在“多种操作与运动任务”和“真实四足”上评估，**未给出具体任务数、随机种子数、消融实验数量或统计检验信息**。
- 可识别出的实验维度包括：
  - 仿真 vs. 真实四足；
  - 离线 MBRL vs. model-free；
  - 考虑不确定性 vs. 不考虑不确定性；
  - 纯离线训练 vs. 融合真实数据。
- **充分性判断**：从摘要看，实验覆盖仿真与真实机器人，具备一定广度；但由于正文缺失，无法核实任务数量、基线调参公平性、显著性检验和消融充分性。
- **客观公平性**：作者声称方法“一致优于”基线，但缺少细节，无法独立判断实验是否完全公平。

## 6. 主要结论与发现
- RWM-O 结合 MOPO-PPO 后，训练出的策略在仿真和真实四足机器人上**一致优于** model-free 与不考虑不确定性的 model-based 基线。
- 在模型学习中融合真实世界数据，可得到更稳健的策略，并超过仅在仿真中训练的 online model-free 基线。
- 结果表明，该流程能提升离线 MBRL 在物理机器人上的鲁棒性与数据效率，推动其从仿真走向真实机器人。

## 7. 优点
- **问题定位准确**：直面真实机器人离线数据中的噪声、偏差、部分可观测与长时程复合误差问题。
- **方法针对性强**：将认知不确定性估计引入自回归世界模型，并在长时程 rollout 中传播，直接缓解模型偏差累积。
- **策略优化稳定**：使用 MOPO-PPO，把不确定性惩罚与稳定 on-policy PPO 结合，更适合真实机器人控制。
- **实验设置实用**：完全离线训练，并在真实四足上验证，还探索融合真实数据，具有较强的落地导向。
- **任务覆盖较广**：仿真中同时涉及操作与运动任务。

## 8. 不足与局限
- **正文不可得**：当前提取文本为验证页面，无法核实方法公式、实验细节、超参数、算力与实现细节。
- **实验细节不足**：未说明具体任务数量、数据集名称、基线配置、随机种子、统计显著性和消融规模。
- **真实机器人覆盖有限**：真实实验明确提到四足机器人，真实操作任务是否验证未说明；sim-to-real 泛化范围可能有限。
- **不确定性估计可靠性未知**：摘要未说明认知不确定性在分布外数据上的校准质量与失效模式。
- **安全与部署限制**：真实机器人控制中的安全约束、实时性、计算成本和恢复机制未提及。
- **元数据背景**：该论文在元数据中标注为 ICLR-2026-Rejected-Public，评分为 5.0；这不直接等同于方法质量，但提示其学术评价存在争议，需结合正文进一步判断。

（完）
