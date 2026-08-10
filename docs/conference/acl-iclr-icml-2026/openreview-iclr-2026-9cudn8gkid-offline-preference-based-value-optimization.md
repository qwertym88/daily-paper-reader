---
title: Offline Preference-Based Value Optimization
title_zh: 离线偏好价值优化
authors: "Hyungkyu Kang, Min-hwan Oh"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=9cUdn8GKId"
tags: ["query:rl-control"]
score: 8.0
evidence: 离线偏好强化学习通过值对齐损失优化值函数，直接涉及策略优化与值函数学习。
tldr: 离线偏好强化学习中，现有算法要么优化过程不可行，要么训练不稳定。作者提出PVO，通过最小化值对齐损失来直接学习与人类偏好一致的值函数。理论分析证明了其收敛性，实验显示PVO在多个基准上性能领先且方差低。该方法为离线偏好强化学习提供了一个简单有效且可扩展的实用算法。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有离线偏好强化学习算法存在计算不可行或训练不稳定、方差大等问题，缺乏既实用又有理论保证的方法。
method: 提出偏好价值优化(PVO)算法，通过最小化新颖的值对齐损失直接学习与偏好一致的值函数。
result: 理论证明PVO具有收敛性，且在标准基准上显著优于现有算法，训练更稳定、方差更低。
conclusion: PVO以简单且可扩展的方式解决了离线偏好强化学习的实践瓶颈，兼顾性能与可证明保证。
---

## Abstract
We study the problem of offline preference-based reinforcement learning (PbRL), where the agent learns from pre-collected preference data by comparing trajectory pairs. 
  While prior work has established theoretical foundations for offline PbRL, existing algorithms face significant practical limitations: some rely on computationally intractable optimization procedures, while others suffer from unstable training and high performance variance.
  To address these challenges, we propose Preference-based Value Optimization (PVO), a simple and practical algorithm that achieves both strong empirical performance and theoretical guarantees.
  PVO directly optimizes the value function consistent with preference feedback by minimizing a novel \emph{value alignment loss}.
  We prove that PVO attains a rate-optimal sample complexity of $\mathcal{O}(\varepsilon^{-2})$, and further show that the value alignment loss is applicable not only to value-based methods but also to actor–critic algorithms.
  Empirically, PVO achieves robust and stable performance across diverse continuous control benchmarks. 
  It consistently outperforms strong baselines, including methods without theoretical guarantees, while requiring no additional hyperparameters for preference learning.
  Moreover, our ablation study demonstrates that substituting the standard TD loss with the value alignment loss substantially improves learning from preference data, confirming its effectiveness for PbRL.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究背景**：离线偏好强化学习（Offline Preference-based Reinforcement Learning, PbRL）旨在从预先收集的轨迹对偏好数据中学习智能体策略，而无需在线交互或显式奖励函数。该范式在人类反馈难以量化、在线探索成本高昂的真实场景中（如机器人控制、推荐系统）具有重要意义。
- **核心问题**：现有离线 PbRL 算法存在两个主要瓶颈：
  - 部分算法依赖**计算上不可行的优化过程**（如复杂的双层优化或非凸规划），缺乏实用性；
  - 另一些算法虽具有理论保证，但**训练不稳定、性能方差大**，难以在实际中复现可靠效果。
- **研究目标**：在保证理论严谨性的同时，设计一种**简单、可扩展、训练稳定**的实用算法，弥补现有方法在理论与实践之间的鸿沟。

---

### 2. 论文提出的方法论

- **核心思想**：提出**偏好价值优化（Preference-based Value Optimization, PVO）**算法，其核心是**直接学习与人类偏好一致的值函数**，而非间接通过奖励建模或策略优化。
- **关键技术**：最小化一个新颖的**值对齐损失（Value Alignment Loss）**，该损失函数直接度量值函数输出与偏好关系的一致性——即若一条轨迹被偏好，则其状态-动作值应系统性高于另一条轨迹。
- **与 actor–critic 的结合**：作者进一步证明，值对齐损失不仅适用于基于值的方法，也可无缝嵌入 **actor–critic 框架**，拓展了其适用范围。
- **理论保证**：证明 PVO 达到样本复杂度上的**最优速率**，即 \(\mathcal{O}(\varepsilon^{-2})\)，表明其在统计效率上具有可证明的最优性。
- **算法流程（文字说明）**：
  1. 输入预收集的轨迹对及偏好标签；
  2. 使用值对齐损失训练值函数，使其与偏好信号一致；
  3. 在基于值的方法中直接由学习到的值函数推导策略；
  4. 在 actor–critic 变体中将该损失与策略更新交替优化。

---

### 3. 实验设计

- **基准场景**：使用**多样的连续控制基准**（continuous control benchmarks），覆盖多个标准机器人控制任务，典型场景包括 MuJoCo 类环境中的运动控制任务。
- **对比基线**：
  - 对比了多种强基线方法，包括**具有理论保证的离线 PbRL 算法**以及**无理论保证的启发式方法**，以便全面评估 PVO 的性能与稳定性。
- **消融实验**：专门设计了消融研究，将标准 TD 损失替换为值对齐损失，以验证该方法对偏好学习的直接贡献。
- **评估指标**：侧重于**平均性能**与**训练方差**，考察不同随机种子下的稳定性。

---

### 4. 资源与算力

- **说明**：论文的摘要与元数据中**未明确提及具体算力资源**（如 GPU 型号、数量、训练时长等）。
- **补充判断**：由于实验环境为标准连续控制基准，推测其算力需求属常规规模（单块或少量 GPU 即可完成），但无法从现有信息确认。作者未提供能耗或硬件配置细节，这属于描述中的**信息缺失项**。

---

### 5. 实验数量与充分性

- **实验数量**：
  - 主实验覆盖**多个连续控制基准**（具体任务数量未在摘要中列出）；
  - 包含一组**消融实验**，用于验证值对齐损失的核心作用；
  - 可能包含多次随机种子重复实验（用于报告均值与方差），但具体重复次数未说明。
- **充分性评估**：
  - **优点**：涵盖多种任务、多种基线（含无理论保证方法），并设置消融，基本能够支撑核心贡献的验证。
  - **不足**：
    - 未提及**与真实人类偏好数据**的对比实验，可能仍以合成偏好为主；
    - 未报告**超参数敏感性**分析；
    - 缺少跨领域（如推荐、对话）的泛化实验；
    - 实验的**随机种子数**和**统计显著性检验**未说明，公平性难以完全确认。

---

### 6. 论文的主要结论与发现

- **性能领先**：PVO 在标准连续控制基准上**显著优于现有基线**，包括那些没有理论保证的方法，同时**不需要额外的偏好学习超参数**。
- **训练稳定**：相比基线方法，PVO 表现出**更低的性能方差**，训练过程更稳定可靠。
- **理论有效**：验证了 PVO 具有最优样本复杂度 \(\mathcal{O}(\varepsilon^{-2})\)，实现了理论与实践的统一。
- **损失函数有效性**：消融实验表明，**将标准 TD 损失替换为值对齐损失可显著提升偏好学习效果**，证明该损失函数是 PbRL 中更合适的替代方案。
- **扩展性**：值对齐损失可适配 actor–critic 架构，说明其具有算法框架层面的通用性。

---

### 7. 优点

- **简单性与实用性**：PVO 结构简洁，不引入额外超参数，易于在现有强化学习框架中实现，降低了使用门槛。
- **理论—实践兼备**：在达到最优样本复杂度的同时，实现了业界领先的实证性能，填补了离线 PbRL 中理论与实用之间的空白。
- **训练稳定性**：低方差是实际部署中的关键优点，PVO 在这方面表现突出。
- **通用性**：损失函数设计不依赖于特定算法族，可同时应用于 value-based 和 actor–critic 方法，具备良好的可扩展性。
- **清晰的贡献验证**：消融实验设计合理，直接证明了核心组件的有效性。

---

### 8. 不足与局限

- **信息缺失**：
  - **算力与实现细节未披露**，复现门槛较高；
  - **未报告实验任务的具体数量与随机种子重复次数**，难以精确评估统计显著性。
- **实验覆盖范围有限**：
  - 仅验证了连续控制任务，**未覆盖离散动作环境**、稀疏奖励场景或**真实人类偏好数据集**；
  - 缺少与**在线偏好学习**或奖励建模方法的系统性对比。
- **潜在偏差风险**：
  - 若偏好数据由脚本生成（而非真人标注），可能存在**分布偏差**，影响结论的普适性；
  - 对偏好噪声的鲁棒性未做深入分析，实际人类反馈通常包含噪声。
- **理论假设限制**：
  - 最优样本复杂度结论可能依赖于特定覆盖率或函数类假设，在低数据或高维空间中是否成立尚需更充分的实证支撑。
- **应用限制**：
  - 值对齐损失的设计可能更适用于**轨迹级偏好**，对**步骤级细粒度反馈**的适配性未知。

---

（完）
