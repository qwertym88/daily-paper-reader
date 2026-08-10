---
title: Safe Reinforcement Learning with Preference-based Constraint Inference
title_zh: 基于偏好约束推断的安全强化学习
authors: "Chenglin Li, Grant Ruan, Hua Geng"
date: 2026-04-30
pdf: "https://openreview.net/pdf/5d4f28d4cb0372aeece0299d4c48ce40e8cd9624.pdf"
tags: ["query:rl-control"]
score: 7.0
evidence: 从人类偏好中推断安全约束，在无显式约束下实现安全强化学习。
tldr: 本文针对现实场景中安全约束难以显式指定的问题，提出从人类偏好中推断约束的强化学习方法。作者指出现有Bradley-Terry模型无法刻画安全成本的非对称重尾特性，导致风险低估，因此设计了适配安全成本分布的推断机制。实验表明该方法能更可靠地恢复约束并提升安全性能。这项工作为隐式安全约束的强化学习提供了数据高效的实用途径。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现实中的安全约束常常复杂且难以显式指定，现有约束推断方法依赖严格假设或大量专家示范，难以适用。
method: 提出从人类偏好中推断约束的方法，并引入非对称重尾模型以改进风险估计。
result: 在实验中验证了该方法能更准确地学习安全约束并降低风险低估，相较于基线显著提升安全性。
conclusion: 偏好式约束推断为难以显式建模的安全约束提供了一种数据高效的解决方案，是安全强化学习的实用补充。
---

## Abstract
Safe reinforcement learning (RL) is a standard paradigm for safety-critical decision making. However, real-world safety constraints can be complex, subjective, and even hard to explicitly specify. Existing works on constraint inference rely on restrictive assumptions or extensive expert demonstrations, which are not realistic in many real-world applications. How to cheaply and reliably learn these constraints is the major challenge we focus on in this study. While inferring constraints from human preferences offers a data-efficient alternative, we identify popular Bradley-Terry (BT) models fail to capture the asymmetric, heavy-tailed nature of safety costs, resulting in risk underestimation. It is still rare in the literature to understand the impacts of BT models on the downstream policy learning. To address the above knowledge gaps, we propose a novel approach namely Preference-based Constrained Reinforcement Learning (PbCRL). We introduce a novel dead zone mechanism into preference modeling and theoretically prove that it encourages heavy-tailed cost distributions, thereby achieving better constraint alignment. Additionally, we incorporate a Signal-to-Noise Ratio (SNR) loss to encourage exploration by cost variances, which is found to benefit policy learning. Further, two-stage training strategy is deployed to lower online labeling burdens while adaptively enhancing constraint satisfaction. Empirical results demonstrate that PbCRL achieves superior alignment with true safety requirements and outperforms state-of-the-art baselines in terms of safety and reward. Our work explores a promising and effective way for constraint inference in Safe RL, with great potential in various safety-critical applications.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究背景**：安全强化学习（Safe RL）是安全关键决策中的标准范式，但真实世界中的安全约束往往复杂、主观，甚至难以显式指定。
- **现有方法的不足**：已有约束推断方法通常依赖较强的假设或大量专家示范，这在许多实际应用中并不现实，成本高且难以扩展。
- **核心问题**：如何低成本、可靠地从人类反馈中学习隐式安全约束？
- **整体含义**：论文提出基于人类偏好推断约束的强化学习方法，为“无法显式建模的安全约束”提供了一种数据高效的实用解决思路，是对安全强化学习的重要补充。

## 2. 论文提出的方法论

- **核心思想**：从人类偏好中推断安全约束，避免依赖显式约束函数或专家示范。
- **针对问题**：作者指出现有 Bradley-Terry（BT）偏好模型无法刻画安全成本的非对称、重尾分布特性，容易导致风险被低估，影响下游策略的安全性。
- **方法名称**：Preference-based Constrained Reinforcement Learning（PbCRL），即“基于偏好的约束强化学习”。

### 关键技术细节

- **死区机制（Dead Zone Mechanism）**：
  - 在偏好建模中引入死区，即对偏好差异较小、难以判断的样本不做强区分。
  - 作者从理论上证明该机制能够促使学习到的成本分布呈现重尾特性，从而更好地与真实安全约束对齐，降低风险低估问题。

- **信噪比损失（Signal-to-Noise Ratio Loss）**：
  - 将成本方差作为探索信号，引入 SNR 损失以鼓励策略探索，进而提升策略学习效果。

- **两阶段训练策略（Two-stage Training）**：
  - 通过分阶段训练降低在线人工标注负担，同时自适应地增强约束满足能力。

### 算法流程（文字描述）

1. 收集人类对轨迹或行为偏好的成对比较反馈。
2. 使用带有死区机制的偏好模型从反馈中推断隐式安全成本分布。
3. 利用 SNR 损失引导策略在成本方差较大的区域进行探索。
4. 在两阶段训练框架下，先学习成本模型，再结合安全约束更新策略，最终实现具备安全性的强化学习策略。

## 3. 实验设计

- **数据集 / 场景**：从提供的摘要中未明确指出具体数据集或环境名称。
- **Benchmark**：摘要仅提到“安全强化学习基准”，未列出具体任务；从论文定位推断，可能涉及常见的 Safe RL 控制任务或仿真环境，但需要查看原文确认。
- **对比方法**：摘要提到与“state-of-the-art baselines”进行比较，但未给出具体基线名称（如 CPO、PPO-Safe、Lagrangian 方法等）。
- **实验结论概述**：PbCRL 在安全对齐、安全性和奖励回报方面优于现有基线。

## 4. 资源与算力

- 在提供的文本（摘要和元数据）中，**没有明确提及 GPU 型号、数量、训练时长或算力规模**。
- 因此无法评估该方法的计算成本与复现资源需求；如需了解，需要查阅论文全文或附录。

## 5. 实验数量与充分性

- 从摘要来看，论文进行了**一组主要实验**，表明 PbCRL 优于 SOTA 基线，并包含一定程度的理论证明。
- 但提供的文本不足以判断实验的完整性与充分性，例如：
  - 是否有多个不同环境或任务？
  - 是否有消融实验（如去掉死区机制、去掉 SNR 损失、两阶段训练 vs 单阶段）？
  - 是否采用真实人类偏好还是合成偏好？
  - 是否验证了对偏好噪声、标签不一致的鲁棒性？
- 因此，**从当前信息看，实验充分性无法完全评估**。摘要结论客观性尚可，但更严格的公平性判断需依赖论文全文。

## 6. 论文的主要结论与发现

- 现有 Bradley-Terry 偏好模型在安全成本推断中会低估风险，不适合直接用于安全约束学习。
- PbCRL 通过死区机制产生重尾成本分布，能够更准确地恢复并匹配真实安全约束。
- SNR 损失有助于策略探索，进一步提升策略学习效果。
- 两阶段训练降低标注负担，同时提升约束满足能力。
- 实验结果显示，PbCRL 在安全性与奖励之间取得更优平衡，并优于当前 SOTA 基线。

## 7. 优点

- **问题选择有现实意义**：关注“约束难以显式指定”的实际痛点，而非理想化假设。
- **理论贡献明确**：对死区机制与重尾分布之间的关系进行了理论证明，而不只是经验式改进。
- **方法上有针对性**：精准指出 BT 模型在安全成本建模中的缺陷，并提出可操作的改进方案。
- **数据高效**：利用偏好反馈而非大量专家示范，降低标注成本。
- **模块设计合理**：SNR 损失和两阶段训练分别从探索效率和实用部署角度提升了系统性能。

## 8. 不足与局限

- **信息不完整**：当前提供的文本仅为摘要，缺乏实验环境、基线选择、消融实验和具体数值等细节，难以独立复现或评估。
- **偏好标注依赖**：尽管比专家示范更便宜，但仍需人类偏好数据；在实际系统中，偏好标注也可能存在噪声、主观偏差和不一致性。
- **重尾假设的适用范围**：死区机制鼓励重尾成本分布，但并非所有安全风险都适合用重尾分布建模，在某些场景下可能引入偏差。
- **安全性保障程度**：基于偏好推断的约束本质上是概率性、估计性的，可能不如显式约束那样提供严格的安全保证。
- **算力与部署成本未知**：未提供算力信息，无法评估大规模应用时的资源需求。
- **实验充分性存疑**：是否涵盖多领域、多任务、真实人类偏好以及对抗性噪声测试，仍需在论文全文中确认。

（完）
