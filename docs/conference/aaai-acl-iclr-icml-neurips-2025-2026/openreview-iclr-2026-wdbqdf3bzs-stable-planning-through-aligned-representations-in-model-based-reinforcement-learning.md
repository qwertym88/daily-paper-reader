---
title: Stable Planning through Aligned Representations in Model-Based Reinforcement Learning
title_zh: 基于模型强化学习中通过对齐表示实现稳定规划
authors: "Misagh Soltani, Forest Agostinelli"
date: 2025-09-16
pdf: "https://openreview.net/pdf?id=wdBqDf3BZs"
tags: ["query:koopman-rl"]
score: 4.0
evidence: 基于模型强化学习中的世界模型与规划
tldr: 将规划与强化学习结合能提升稀疏奖励长时程任务的求解能力，但现有离散世界模型在状态变换（如噪声）下会失效，除非重新训练。本文通过对齐表示训练世界模型，使状态在规划过程中可被稳定重新识别。该方法在稀疏奖励长时程任务中实现稳定规划，缓解了世界模型退化问题，提升了世界模型与启发函数在规划中的鲁棒性。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 将规划与RL结合时，世界模型在长时程与状态变换下容易退化失效。
method: 训练具对齐表示的离散世界模型，使状态在规划中可被稳定重新识别。
result: 在稀疏奖励长时程任务中实现稳定规划，缓解模型退化问题。
conclusion: 提升了世界模型与启发函数在规划中的鲁棒性。
---

## Abstract
Integrating planning with reinforcement learning (RL) significantly improves problem-solving capabilities for sequential decision-making problems, particularly in sparse-reward, long-horizon tasks. Recently, it has been shown that discrete world models can be trained such that no model degradation occurs over thousands of time steps and states can be re-identified during planning. As a result, a heuristic function can be trained with data generated from the world model, and the learned world model and heuristic function can be used with planning to solve problems. However, this approach fails to solve problems with state transformations to which the world model and heuristic function should be invariant (i.e., noise), without re-training the world model and heuristic function. In this work, we introduce Stable Planning through Aligned Representations (SPAR), an efficient framework that trains a discrete world model and heuristic function in a clean Markov decision process (MDP) and trains an alignment network to map transformed states to their discrete latent state in the clean MDP. When solving problems, we exploit the underlying discrete latent representation and round the output of the alignment network in hopes that it matches the clean latent state exactly. As a result, adapting to transformations only requires training the adaptation network while the world model and heuristic function remain fixed. We then demonstrate its effectiveness on Rubik's Cube domain, and compare it with applying a similar approach to a world model with continuous latent representations. SPAR successfully solves over 90% of problems with 17 different visual transformations and real-world images. This adaptation process requires no additional world model or heuristic function re-training, and reduces re-training time by at least 95%.

---

## 论文详细总结（自动生成）

# 论文总结：Stable Planning through Aligned Representations in Model-Based Reinforcement Learning（SPAR）

> 说明：由于 PDF 正文未成功提取（OpenReview 页面要求 CAPTCHA），以下总结主要基于论文摘要与元数据，部分方法细节、实验设置和算力信息无法从全文进一步核实。

## 1. 核心问题与整体含义

- **研究背景**：将规划与强化学习（RL）结合，可以显著提升稀疏奖励、长时程序列决策任务的问题求解能力。
- **已有进展**：近期工作表明，离散世界模型可以被训练到在数千个时间步内不发生模型退化，并且状态在规划过程中可以被重新识别。因此，可以利用世界模型生成数据来训练启发函数，再结合规划求解问题。
- **核心问题**：当环境存在状态变换（例如噪声）时，世界模型和启发函数本应保持一定不变性，但现有方法若不重新训练世界模型和启发函数，就会失效。
- **整体含义**：本文提出 SPAR，希望在面对状态变换时，不需要重新训练世界模型和启发函数，只通过轻量适配即可实现稳定规划，从而缓解世界模型退化问题，提高规划鲁棒性。

## 2. 方法论

- **核心思想**：在一个干净的马尔可夫决策过程（clean MDP）中训练离散世界模型和启发函数；另外训练一个对齐网络，将经过变换的状态映射到干净 MDP 中对应的离散潜在状态。
- **关键流程**：
  1. 在干净 MDP 中训练离散世界模型，使其在长时程规划中保持稳定，并支持状态重新识别。
  2. 利用世界模型生成的数据训练启发函数。
  3. 训练对齐网络，使其输入变换后的状态，输出干净 MDP 中的离散潜在状态。
  4. 求解问题时，利用底层离散潜在表示，并对对齐网络输出进行取整，希望其与干净潜在状态精确匹配。
  5. 世界模型和启发函数保持固定，仅训练适配网络即可适应新的状态变换。
- **技术特点**：
  - 强调“对齐表示”，即让变换状态与干净状态在离散潜空间中重新对齐。
  - 利用离散潜在表示的可取整特性，提高状态重识别和规划稳定性。
  - 与连续潜在表示方法相比，SPAR 更依赖离散潜状态匹配，而不是连续表示回归。
- **摘要未给出的内容**：具体损失函数、网络结构、训练目标公式、取整方式和规划算法细节未在提供文本中说明。

## 3. 实验设计

- **实验场景**：主要使用魔方（Rubik's Cube）域。
- **测试变换**：包括 17 种不同的视觉变换，以及真实世界图像。
- **Benchmark / 任务目标**：在稀疏奖励、长时程任务中求解魔方问题；适应视觉变换后仍能完成规划求解。
- **对比方法**：与将类似适配思路应用于连续潜在表示世界模型的方法进行比较。
- **评价指标**：
  - 问题求解成功率。
  - 是否需要额外重新训练世界模型或启发函数。
  - 重新训练时间减少幅度。
- **主要实验结果**：
  - SPAR 在 17 种视觉变换和真实世界图像上成功解决超过 90% 的问题。
  - 适应过程不需要额外重新训练世界模型或启发函数。
  - 重新训练时间至少减少 95%。

## 4. 资源与算力

- 提供的摘要和元数据中**未明确说明**使用的 GPU 型号、GPU 数量、训练时长、参数量或总计算量。
- 因此无法总结具体算力配置。
- 只能确认论文声称其适配过程非常高效，显著减少了重新训练时间。

## 5. 实验数量与充分性

- 根据摘要，实验至少覆盖：
  - 魔方域。
  - 17 种视觉变换。
  - 真实世界图像。
  - 与连续潜在表示世界模型方法的对比。
- 但提供文本中**未说明**：
  - 是否包含消融实验。
  - 是否测试多个随机种子。
  - 是否报告统计显著性或置信区间。
  - 是否在魔方之外的其他任务上验证。
- **充分性评价**：
  - 在单一魔方域内，17 种视觉变换和真实图像提供了一定多样性，能说明方法对视觉扰动的适应性。
  - 但实验域较单一，泛化到其他长时程规划任务、其他类型噪声或其他 MDP 的结论仍需谨慎。
  - 对比公平性取决于连续潜表示方法的实现细节，摘要未提供足够信息判断。

## 6. 主要结论与发现

- SPAR 能够在稀疏奖励、长时程任务中实现稳定规划。
- 通过离散潜在表示对齐，世界模型和启发函数在状态变换下仍可被有效复用。
- 面对多种视觉变换和真实世界图像，SPAR 的问题求解成功率超过 90%。
- 适应新变换只需训练对齐网络，无需重新训练世界模型和启发函数。
- 相比重新训练方案，重训练时间至少减少 95%，显著提升效率。
- 总体上，该方法缓解了世界模型退化问题，并提升了世界模型与启发函数在规划中的鲁棒性。

## 7. 优点

- **高效适配**：世界模型和启发函数固定，只训练轻量对齐网络，避免高成本重训。
- **离散表示优势**：利用离散潜状态和取整操作，有望提高状态重识别稳定性。
- **鲁棒性较强**：在 17 种视觉变换和真实世界图像上仍能保持高求解率。
- **问题设定有价值**：关注规划与 RL 结合中的状态变换不变性问题，切中实际部署中的噪声和视觉扰动挑战。
- **结果指标明确**：超过 90% 成功率、至少 95% 重训时间减少，直观体现效率和效果。

## 8. 不足与局限

- **全文信息不足**：由于只获取到摘要和元数据，无法验证具体算法、公式、网络结构和训练细节。
- **实验域单一**：主要在魔方域验证，是否适用于其他长时程规划任务尚不明确。
- **取整策略风险**：依赖对齐网络输出取整后精确匹配干净潜状态；若对齐误差较大，可能导致匹配失败或规划不稳定。
- **算力信息缺失**：未报告 GPU 型号、数量、训练时长等，影响可复现性和成本评估。
- **对比范围有限**：主要与连续潜表示世界模型的类似方法比较，缺少与其他规划/RL 方法的广泛对比。
- **泛化边界未知**：真实世界图像的具体范围、噪声类型、视觉变换强度等未详细说明。
- **应用限制**：需要预先在干净 MDP 中训练世界模型和启发函数；若干净环境不可得或变换过于复杂，方法可能受限。
- **失败案例分析不足**：摘要未讨论失败情况、规划时间开销、安全性或长期稳定性。

（完）
