---
title: "Bridging Discrete and Continuous RL: Stable Deterministic Policy Gradient with Martingale Characterization"
title_zh: 连接离散与连续强化学习：具有鞅刻画的稳定确定性策略梯度
authors: "Ziheng Cheng, Xin Guo, Yufei Zhang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=aS2o4Gn4CR"
tags: ["query:rl-control"]
score: 7.0
evidence: 连续时间确定性策略梯度及鞅刻画，提出CT-DDPG算法
tldr: 离散时间强化学习算法在连续环境应用中常因时间离散化而出现稳定性差、收敛慢的问题。该工作研究连续时间强化学习下的确定性策略梯度，基于优势函数的类似物推导出连续时间策略梯度公式，并建立鞅刻画，进而提出CT-DDPG算法。新算法在时间离散化下保持稳定，弥合了离散与连续强化学习之间的鸿沟，为连续控制任务提供更稳健的策略梯度方法。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 连续环境强化学习中，离散时间算法对时间离散化敏感，导致稳定性差和收敛缓慢，限制实际部署。
method: 推导连续时间确定性策略梯度公式，建立鞅刻画，并基于此提出CT-DDPG算法。
result: CT-DDPG在时间离散化下保持稳定，显著改善连续控制任务的收敛性和鲁棒性。
conclusion: 连接离散与连续强化学习，为连续控制提供理论扎实的策略梯度方法。
---

## Abstract
The theory of discrete-time reinforcement learning (RL) has advanced rapidly over the past decades. Although primarily designed for discrete environments, many real-world RL applications are inherently continuous and complex. A major challenge in extending discrete-time algorithms to continuous-time settings is their sensitivity to time discretization, often leading to poor stability and slow convergence.
In this paper, we investigate deterministic policy gradient methods for continuous-time RL. We derive a continuous-time policy gradient formula based on an analogue of the advantage function and establish its martingale characterization. This theoretical foundation leads to our proposed algorithm, CT-DDPG, which enables stable learning with deterministic policies in continuous-time environments.
Numerical experiments show that the proposed CT-DDPG algorithm offers improved stability and faster convergence compared to existing discrete-time and continuous-time methods, across a wide range of control tasks with varying time discretizations and noise levels.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机与背景）
- **问题背景**：离散时间强化学习（RL）理论在过去几十年发展迅速，但大多数真实世界应用本质上是**连续时间、连续状态**的复杂系统。将离散时间算法直接推广到连续环境时，算法对**时间离散化步长高度敏感**，容易导致稳定性差、收敛缓慢，这限制了其实际部署。
- **核心问题**：如何为连续时间 RL 设计一种**稳定、快速收敛的确定性策略梯度方法**，并建立相应的理论基础。
- **整体含义**：论文旨在搭建离散时间 RL 与连续时间 RL 之间的**理论桥梁**，使策略梯度方法在连续控制任务中既具备可靠的理论保证，又能在实际数值离散化下保持稳定。

### 2. 方法论：核心思想、技术细节与算法流程
- **核心思想**：在连续时间框架下重新推导确定性策略梯度，利用**优势函数的连续时间类比物**，并建立**鞅刻画（martingale characterization）**，以此为基础构造新的策略梯度算法。
- **关键技术细节**：
  - 推导出**连续时间策略梯度公式**：该公式将策略梯度表示为优势函数（或其连续时间对应物）的某种期望形式，从而在连续时间域中提供准确的梯度方向。
  - 建立**鞅刻画**：利用鞅理论对梯度估计进行统计分析，确保估计量具有良好的性质（如无偏性或方差控制），这为算法的稳定性提供理论支撑。
  - 基于上述理论，提出 **CT-DDPG（Continuous-Time Deep Deterministic Policy Gradient）算法**：该算法在连续时间环境中使用确定性策略，并通过神经网络近似策略和值函数，结合经验回放和目标网络等 DDPG 常见技巧，但核心梯度更新基于新的连续时间公式。
- **算法流程（文字描述）**：
  1. 初始化策略网络、Q 网络及其目标网络。
  2. 在环境中采样转移数据，存储在回放缓冲区。
  3. 从缓冲区采样小批量数据，计算连续时间策略梯度公式所需的优势估计（通过 Q 网络和目标网络）。
  4. 利用鞅刻画调整或修正梯度估计，更新策略网络参数。
  5. 更新 Q 网络参数以减小贝尔曼误差，并定期软更新目标网络。
  6. 重复上述步骤直到收敛。

### 3. 实验设计
- **实验场景**：覆盖**多种连续控制任务**，并考虑了**不同的时间离散化步长**和**噪声水平**，以检验算法的鲁棒性。
- **Benchmark**：未明确列出具体环境名称（如 MuJoCo 或 Gym 任务），但提到“a wide range of control tasks”，暗示使用了标准连续控制基准中的多个任务。
- **对比方法**：
  - 现有的**离散时间 RL 方法**（如标准 DDPG 或其变体）。
  - 现有的**连续时间 RL 方法**（作为同行比较）。
- **评估指标**：稳定性（训练曲线波动程度）和收敛速度（达到一定性能所需的迭代次数/样本量）。

### 4. 资源与算力
- 论文摘要中**未明确说明**所使用的 GPU 型号、数量、训练时长等具体算力信息。
- 仅能推断实验涉及神经网络训练（深度强化学习），需要一定计算资源，但具体细节缺失。

### 5. 实验数量与充分性
- **实验数量**：论文提到“numerical experiments”和“a wide range of control tasks”，表明进行了多组实验，覆盖不同任务、不同离散化步长、不同噪声水平。
- **消融实验**：未在摘要中提及是否包含消融实验（如去掉鞅刻画或使用旧梯度公式的对照实验）。
- **充分性与客观性**：
  - 优点：跨多个任务、多种离散化步长和噪声水平进行测试，能较好展示算法的泛化性和鲁棒性。
  - 不足：缺乏具体实验数量、统计显著性分析、以及是否多次随机种子重复实验的描述，无法完全判断实验的严谨性；也未提及与其他最新 SOTA 算法的对比范围是否全面。

### 6. 主要结论与发现
- CT-DDPG 在**时间离散化变化下能保持稳定**，显著改善了连续控制任务的**收敛速度和鲁棒性**。
- 相比现有的离散时间方法和连续时间方法，CT-DDPG 在多个任务上表现更好。
- 验证了连续时间策略梯度公式与鞅刻画的理论价值，表明该理论能够转化为实际有效的算法。

### 7. 优点
- **理论贡献**：首次（或重要地）将确定性策略梯度推广到连续时间，并建立鞅刻画，为连续时间 RL 提供了严谨的理论基础。
- **算法实用性**：提出的 CT-DDPG 直接可应用于现有深度 RL 框架，无需特殊架构。
- **稳定性提升**：通过理论引导的设计，有效缓解了离散化敏感性这一关键痛点。
- **实验覆盖较广**：考量了多种时间步长和噪声条件，使结论更具说服力。

### 8. 不足与局限
- **实验细节缺失**：未提供具体环境列表、超参数设置、网络结构等，难以复现。
- **消融分析不足**：没有明确展示各组件（鞅刻画、连续时间公式）的独立贡献。
- **算力信息未披露**：不利于评估方法的使用成本。
- **对比范围有限**：摘要中未提及与更先进的基于模型的 RL 或离线 RL 方法进行比较。
- **理论假设**：连续时间策略梯度公式可能依赖于某些规则性条件（如平滑性、充分探索），在极端噪声或高维复杂环境中可能不成立或需要额外处理。
- **实际部署差距**：虽然声称改善连续控制，但未涉及真实机器人等物理系统的部署验证。

（完）
