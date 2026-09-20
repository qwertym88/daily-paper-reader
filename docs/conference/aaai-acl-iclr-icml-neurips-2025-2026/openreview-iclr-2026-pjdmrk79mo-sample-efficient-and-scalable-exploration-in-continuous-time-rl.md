---
title: Sample-efficient and Scalable Exploration in Continuous-Time RL
title_zh: 连续时间强化学习中样本高效且可扩展的探索
authors: "Klemens Iten, Lenart Treven, Bhavya Sukhija, Florian Dorfler, Andreas Krause"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=PJdMrK79Mo"
tags: ["query:koopman-rl"]
score: 4.0
evidence: 基于ODE动力学的连续时间基于模型强化学习
tldr: 现实控制系统本质上是连续时间的，而多数强化学习算法却按离散时间动力学设计。本文研究连续时间强化学习，用高斯过程与贝叶斯神经网络学习未知非线性ODE的不确定性模型，并提出COMBRL算法贪婪最大化外在奖励与模型认知不确定性的加权和。该算法实现了可扩展且样本高效的连续时间基于模型强化学习，并获得次线性遗憾，为连续时间控制中的探索提供了理论保障。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现实控制系统本质连续时间，而多数强化学习算法按离散时间设计。
method: 用高斯过程与贝叶斯神经网络学习ODE不确定模型，提出COMBRL最大化奖励与不确定性。
result: 实现可扩展且样本高效的连续时间基于模型RL，并获得次线性遗憾。
conclusion: 为连续时间控制中的探索提供了具理论保障的框架。
---

## Abstract
Reinforcement learning algorithms are typically designed for discrete-time dynamics, even though the underlying real-world control systems are often continuous in time. In this paper, we study the problem of continuous-time reinforcement learning, where the unknown system dynamics are represented using nonlinear ordinary differential equations (ODEs). We leverage probabilistic models, such as Gaussian processes and Bayesian neural networks, to learn an uncertainty-aware model of the underlying ODE. Our algorithm, COMBRL, greedily maximizes a weighted sum of the extrinsic reward and model epistemic uncertainty. This yields a scalable and sample-efficient approach to continuous-time model-based RL. We show that COMBRL achieves sublinear regret in the reward-driven setting, and in the unsupervised RL setting (i.e., without extrinsic rewards), we provide a sample complexity bound. In our experiments, we evaluate COMBRL in both standard and unsupervised RL settings and demonstrate that it scales better, is more sample-efficient than prior methods, and outperforms baselines across several deep RL tasks.

---

## 论文详细总结（自动生成）

# 论文总结：连续时间强化学习中样本高效且可扩展的探索

> 说明：可获取的 PDF 文本仅为 OpenReview 的验证页面，未包含论文正文；以下总结主要依据论文摘要与元数据。涉及具体公式、实验清单、算力等正文细节时，凡材料未说明之处均标注为“未说明/无法确认”。

## 1. 核心问题与整体含义
- **研究动机**：现实世界中的控制系统本质上通常是连续时间的，但多数强化学习算法按离散时间动力学设计，二者之间存在建模与算法假设的不匹配。
- **核心问题**：如何在未知非线性常微分方程（ODE）描述的连续时间系统中，进行可扩展且样本高效的探索，并给出理论保障。
- **整体含义**：论文试图推动连续时间基于模型的强化学习，使其不仅能处理连续时间动力学，还能在奖励驱动和无监督探索两种场景下具备样本效率与可扩展性。

## 2. 方法论
- **核心思想**：将未知系统动力学建模为非线性 ODE，并使用概率模型学习一个“不确定性感知”的 ODE 模型。
- **关键技术细节**：
  - 使用**高斯过程（GP）**与**贝叶斯神经网络（BNN）**来学习未知 ODE 的不确定性模型。
  - 提出算法 **COMBRL**，其探索策略是贪婪最大化“外在奖励”与“模型认知不确定性”的加权和。
  - 可概念化理解为：在选择控制/动作时，同时追求高奖励和高认知不确定性，以促进探索。
- **算法流程概述**：基于连续时间 ODE 模型进行基于模型的 RL；利用概率模型给出认知不确定性；COMBRL 将奖励与不确定性加权组合作为贪婪优化目标。
- **理论结果**：
  - 在奖励驱动设置下，COMBRL 可实现**次线性遗憾（sublinear regret）**。
  - 在无监督 RL 设置下，即没有外在奖励时，论文提供了**样本复杂度界（sample complexity bound）**。
- **注意**：具体公式、推导、算法伪代码及假设条件未在可获取材料中给出，无法进一步展开。

## 3. 实验设计
- **场景/任务**：论文在**标准强化学习设置**和**无监督强化学习设置**中评估 COMBRL，并在多个**深度强化学习任务**上进行实验。
- **数据集/环境**：摘要与元数据未明确列出具体数据集或环境名称；只能确认是若干 deep RL 任务。
- **Benchmark**：未明确说明具体 benchmark 名称或评价指标细节。
- **对比方法**：论文声称与**先前方法（prior methods）**和**基线（baselines）**进行比较，但可获取材料未列出具体对比算法名称。

## 4. 资源与算力
- 可获取材料中**未提及** GPU 型号、GPU 数量、训练时长、参数量或总体算力开销。
- 因此无法评估该方法的计算成本、可复现性所需资源，以及“可扩展性”在硬件层面的具体表现。

## 5. 实验数量与充分性
- 从摘要可确认的实验范围：
  - 至少覆盖**标准 RL**与**无监督 RL**两类设置；
  - 在**多个深度 RL 任务**上评估；
  - 与 prior methods 和 baselines 对比。
- **无法确认**的内容：
  - 具体任务数量、数据集数量；
  - 是否包含消融实验；
  - 是否报告随机种子、置信区间、统计显著性；
  - 基线是否经过充分调参、比较是否公平。
- **充分性判断**：仅凭摘要看，实验覆盖了两种重要设置和多个任务，方向较完整；但由于缺少实验细节，无法客观判断其充分性、公平性和可复现性。

## 6. 主要结论与发现
- COMBRL 为连续时间基于模型的强化学习提供了一种**可扩展且样本高效**的方法。
- 在奖励驱动设置中，算法获得**次线性遗憾**，说明探索策略具有理论上的长期效率保障。
- 在无监督 RL 设置中，论文给出**样本复杂度界**，扩展了无外在奖励场景下的理论分析。
- 实验结果表明：COMBRL 相比先前方法**扩展性更好、样本效率更高**，并在多个深度 RL 任务上**优于基线**。

## 7. 优点
- **问题选择重要**：针对连续时间控制与离散时间 RL 算法之间的根本错配，具有现实意义。
- **方法结合理论**：将 GP/BNN 的不确定性建模与基于模型的连续时间 RL 结合，并给出遗憾界和样本复杂度界。
- **探索机制清晰**：通过奖励与认知不确定性的加权和进行贪婪探索，思路简洁且与乐观探索原则一致。
- **场景覆盖较广**：同时考虑奖励驱动和无监督 RL，提升框架的一般性。
- **实验宣称有优势**：在多个深度 RL 任务上声称优于先前方法和基线，并强调可扩展性与样本效率。

## 8. 不足与局限
- **正文信息缺失导致验证受限**：由于 PDF 正文未成功提取，无法核实公式、假设、实验细节、超参数和统计结果。
- **实验细节不透明**：未列出具体数据集、任务、基线名称、消融实验、重复次数和计算资源，难以判断公平性与可复现性。
- **模型与计算限制**：GP 和 BNN 在连续时间 ODE 建模中可能面临计算复杂度、数值求解和高维扩展性问题；摘要虽声称可扩展，但缺少证据细节。
- **理论条件未知**：次线性遗憾与样本复杂度界所依赖的假设、模型类别、正则性和探索条件未说明。
- **应用限制未讨论**：未涉及安全约束、部分可观测、非平稳环境、真实物理系统部署等实际问题。
- **偏差风险**：当前总结完全依赖摘要和元数据，可能受到作者摘要表述的乐观倾向影响，不能替代全文审读。

（完）
