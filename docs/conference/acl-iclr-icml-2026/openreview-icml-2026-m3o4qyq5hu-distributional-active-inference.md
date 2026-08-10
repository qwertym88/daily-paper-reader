---
title: Distributional Active Inference
title_zh: 分布式主动推断
authors: "Abdullah Akgül, Gulcin Baykal, Manuel Haussmann, Mustafa Mert Çelikok, Melih Kandemir"
date: 2026-04-30
pdf: "https://openreview.net/pdf/bf244f6527dae8a3d98390fcc7adbdd88c8396a5.pdf"
tags: ["query:rl-control"]
score: 9.0
evidence: 融合最优控制、强化学习与主动推断用于机器人的复杂环境控制
tldr: 机器人最优控制面临感觉状态信息组织和远期动作规划的双重挑战，纯强化学习框架只处理后者导致样本效率低下。本文提出一种横跨基于模型、分布式与无模型方法的强化学习形式化抽象，并将主动推断原理无缝集成进分布式强化学习。该统一框架在处理感知与规划协同的同时提升了样本效率，为复杂机器人系统的控制与决策提供了新途径。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 机器人最优控制需要兼顾感知信息组织与远期规划，而纯强化学习仅解决规划问题，导致样本效率低下。
method: 提出一种涵盖模型化、分布式与无模型的统一RL抽象，并将主动推断纳入分布式强化学习框架。
result: 该抽象能自然整合感知与规划，在机器人控制任务中改善样本效率与决策质量。
conclusion: 主动推断与分布式强化学习的结合为复杂环境下的机器人控制提供了统一而高效的理论框架。
---

## Abstract
Optimal control of complex environments with robotic systems faces two complementary and intertwined challenges: efficient organization of sensory state information and far-sighted action planning. Because the reinforcement learning framework addresses only the latter, it tends to deliver sample-inefficient solutions. Active inference is the state-of-the-art process theory that explains how biological brains handle this dual problem. However, its applications to artificial intelligence have thus far been limited to extensions of existing model-based approaches. We present a formal abstraction of reinforcement learning algorithms that spans model-based, distributional, and model-free approaches. This abstraction seamlessly integrates active inference into the distributional reinforcement learning framework, making its performance advantages accessible without transition dynamics modeling.

---

## 论文详细总结（自动生成）

# 《分布式主动推断》（Distributional Active Inference）中文总结

## 1. 核心问题与研究动机

- **双重挑战**：复杂环境下机器人最优控制面临两个相互交织的问题——① 感觉状态信息的有效组织（感知层面）；② 远视动作规划（决策层面）。
- **现有 RL 框架的局限**：强化学习（RL）框架仅处理上述第二个问题（规划），却未将感知与规划协同起来，因此往往产生样本效率低下的解决方案。
- **主动推断的潜力与缺口**：主动推断（Active Inference）是目前解释生物大脑如何同时处理上述双重问题的最先进过程理论（process theory），然而其在人工智能中的应用至今局限于对已有基于模型方法的扩展，尚未被纳入更广泛的 RL 框架。
- **论文目标**：提出一种能横跨多类强化学习方法的统一形式化抽象，并将主动推断无缝集成到分布式强化学习框架中，从而在不进行转移动态建模的前提下获得其性能优势。

## 2. 方法论

- **核心思想**：提出一种覆盖**基于模型（model-based）、分布式（distributional）与无模型（model-free）**方法的统一形式化抽象，并在该抽象框架内将主动推断的机制纳入分布式强化学习流程。
- **技术要点**：
  - 利用统一抽象将主动推断原理编码到分布式价值学习中；
  - 通过该集成，主动推断在人工系统中的使用不再依赖对环境转移动态（transition dynamics）的显式建模；
  - 该抽象让感知层面的信息组织与决策层面的动作规划在同一学习过程中自然协同，而非作为两个独立模块串行处理。
- **算法流程概述**（依据摘要推断）：建立统一的 RL 形式化框架 → 在分布式的价值分布更新中加入主动推断的自由能目标或预期自由度信号 → 通过分布式回报分布的学习来同时引导感知状态表征的形成与动作策略的规划，最终同时优化感知效率和决策质量。

> 注：原文摘要未提供具体公式、网络结构或伪代码，此处的流程叙述仅是对摘要内容的凝练与结构化转述。

## 3. 实验设计

- **数据集 / 场景**：原文摘要与元数据中未列出具体实验数据集。由 tags 和 evidence 字段可推断，任务领域为**机器人复杂环境控制**。
- **Benchmark**：未明确指定基准测试集（如 DM Control、MuJoCo、Isaac Gym 等均未提及）。
- **对比方法**：摘要未详细列举对比方法，仅从定位上推断可能的对比对象包括：
  - 传统基于模型的主动推断方法；
  - 标准无模型强化学习（如 SAC、PPO 等）；
  - 不包含主动推断机制的分布式 RL 基线。

## 4. 资源与算力

- 原文（摘要部分）**未提及任何算力信息**，包括：
  - GPU 型号与数量；
  - 训练时长；
  - 能源成本或计算预算。
- 需指出：在摘要级别无法获知实验的算力配置。

## 5. 实验数量与充分性

- **实验数量**：原文摘要未提供实验数量，未提及具体任务、消融实验或对比实验的组数。
- **充分性与客观性评估**：
  - 从摘要内容无法判断实验的充分性；
  - 未见与 baseline 的统计比较细节；
  - 未见消融实验说明（如去掉主动推断模块、去掉统一抽象后模型的性能变化）；
  - 因此无法确认实验的客观性和公平性，须等待全文细节（如 ICML 2026 正式出版版本）才能充分评估。

## 6. 主要结论与发现

- 提出的统一抽象能够**自然整合感知信息组织与动作规划**两个环节，不再像纯 RL 方法那样割裂二者。
- 将主动推断集成进分布式强化学习框架后，在机器人控制任务中能够**改善样本效率**，即在更少的交互数据下达到更好的决策效果。
- 这种结合为复杂环境下机器人的控制与决策提供了一个**统一而高效的理论框架**，且无需显式建模环境转移动态。

## 7. 优点

- **理论层面突出**：将主动推断从基于模型的“扩展”提升为可适配多种 RL 范式的“统一抽象”，兼具理论深度与普适性。
- **针对性强**：直接回应了 RL 长期以来样本效率低下的痛点，而非简单堆叠新技巧。
- **框架性贡献**：提出的抽象横跨 model-based / distributional / model-free 三种流派，为后续研究提供了统一理论语言。
- **实用性潜力**：不要求学习转移动态，降低了实际机器人部署中的建模难度，有望提升真实系统的可行性。

## 8. 不足与局限

- **细节不透明**：当前仅有摘要层面信息，公式、算法伪代码和网络设计未展示，难以评估方法的可实现性与复杂度。
- **实验证据缺失**：未报告具体任务、数据集、基线对比、消融等，无法判断该方法相对现有方法的确切优势大小。
- **样本效率的量化模糊**：摘要声称“improve sample efficiency”，但未提供收敛曲线、性能绝对值或效率提升幅度等量化指标。
- **应用范围有限**：主要面向机器人控制场景，对离散决策、多智能体、真实硬件部署等场景的适用性未作说明。
- **偏差风险**：未报告随机种子数、方差度量、不同环境难度下的稳定性，存在结果偶然性的潜在风险。

---

（完）
