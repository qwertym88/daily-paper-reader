---
title: "DR-SAC: Distributionally Robust Soft Actor-Critic for Reinforcement Learning under Uncertainty"
title_zh: DR-SAC：不确定性下基于分布鲁棒的柔性演员-评论家强化学习
authors: "Mingxuan Cui, Duo Zhou, Yuxuan Han, Grani A. Hanasusanto, Qiong Wang, Huan Zhang, Zhengyuan Zhou"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=a19MA0ksbc"
tags: ["query:rl-control"]
score: 9.0
evidence: 将SAC扩展到分布鲁棒的离线强化学习，属于演员-评论家架构
tldr: 实际部署中深度强化学习常因环境不确定性而失效，现有分布鲁棒RL方法多局限于表格型价值方法。本文提出DR-SAC，首次将软演员-评论家算法扩展到连续动作空间的离线分布鲁棒学习，在KL散度约束的不确定集内最大化熵正则奖励的最坏情况。算法推导并使用了分布鲁棒形式的软策略评估，为提升真实环境下的鲁棒性提供了可扩展且有理论依据的方案。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 深度强化学习在实际环境中易受不确定性影响，而现有分布鲁棒方法难以处理连续动作空间。
method: 提出DR-SAC算法，把软演员-评论家扩展到分布鲁棒离线学习，对抗最坏转移模型。
result: 推导了分布鲁棒软策略评估形式，形成首个非表格的演员-评论家DR-RL算法。
conclusion: 为离线连续控制中的不确定性提供更强的鲁棒性保障，扩展了分布鲁棒RL的应用范围。
---

## Abstract
Deep reinforcement learning (RL) has achieved remarkable success, yet its deployment in real-world scenarios is often limited by vulnerability to environmental uncertainties. Distributionally robust RL (DR-RL) algorithms have been proposed to resolve this challenge, but existing approaches are largely restricted to value-based methods in tabular settings. In this work, we introduce Distributionally Robust Soft Actor-Critic (DR-SAC), the first actor–critic based DR-RL algorithm for offline learning in continuous action spaces. DR-SAC maximizes the entropy-regularized rewards against the worst possible transition models within an KL-divergence constrained uncertainty set. We derive the distributionally robust version of the soft policy iteration with a convergence guarantee and incorporate a generative modeling approach to estimate the unknown nominal transition models. Experiment results on five continuous RL tasks demonstrate our algorithm achieves up to $9.8\times$ higher average reward than the SAC baseline under common perturbations. Additionally, DR-SAC significantly improves computing efficiency and applicability to large-scale problems compared with existing DR-RL algorithms.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：深度强化学习（Deep RL）在模拟环境与真实场景中取得了显著成功，但在实际部署中极易受到环境不确定性的影响，例如状态转移概率偏差、环境扰动或建模误差，这严重制约了其可靠性和安全性。
- **现有方法局限**：已有的分布鲁棒强化学习（DR-RL）方法试图通过在最坏环境模型下优化策略来提升鲁棒性，但绝大多数方法局限于表格型（tabular）价值迭代场景，难以扩展到连续动作空间，也缺乏可扩展的演员-评论家（actor-critic）实现。
- **核心问题**：如何将分布鲁棒思想与连续动作空间下高效的演员-评论家算法相结合，使离线强化学习策略在面对未知转移模型扰动时依然保持稳定和高回报。
- **整体含义**：论文提出了 DR-SAC 算法，首次在连续动作空间中实现基于演员-评论家架构的离线分布鲁棒强化学习，为真实环境下深度 RL 的安全部署提供了一条有理论保障且可扩展的技术路径。

## 2. 论文提出的方法论

- **核心思想**：DR-SAC 将软演员-评论家（Soft Actor-Critic, SAC）扩展到分布鲁棒离线学习框架中。它不再假设真实转移模型与训练时的名义转移模型完全一致，而是构造一个由 KL 散度约束的不确定集（uncertainty set），要求策略在集合中**最坏（worst-case）的名义转移模型**下最大化熵正则化奖励。
- **关键公式/理论推导**：
  - 论文推导了分布鲁棒版本的**软策略迭代**（soft policy iteration），并证明其具有收敛性保证。
  - 在此框架下，策略评估阶段被替换为“分布鲁棒软策略评估”，即同时考虑熵正则项和对抗性转移模型的影响。
- **技术细节**：
  - 为了估计未知的名义转移模型，论文引入**生成式建模方法**（generative modeling），从而能够在离线数据上构建可行且合理的转移模型分布。
  - DR-SAC 保留了 SAC 的随机策略和最大熵特性，使策略既具备探索能力，又能在不确定环境下保持鲁棒。
  - 由于采用演员-评论家架构，DR-SAC 不再受限于表格型状态表示，可直接处理连续状态和动作空间。
- **算法流程概述**（文字说明）：
  1. 从离线数据集中学习名义转移模型及其不确定性集（基于 KL 散度）。
  2. 在每一轮迭代中，评论家网络对最坏转移模型下的熵正则化 Q 值进行估计。
  3. 演员网络根据该鲁棒 Q 值更新策略，同时保持熵最大化目标。
  4. 交替执行策略评估与策略改进，直至收敛到分布鲁棒最优策略。

## 3. 实验设计

- **任务场景**：论文在 **5 个连续控制任务**（continuous RL tasks）上进行实验，覆盖常见的 Mujoco/Gym 类连续动作控制基准，但具体任务名称在提供的摘要信息中未逐项列出。
- **Benchmark**：以 **SAC 基线**作为主要对比对象，同时与已有 DR-RL 算法进行比较。
- **扰动设置**：采用“常见扰动”（common perturbations），用于模拟环境转移模型的不确定性。
- **对比方法**：
  - SAC（标准软演员-评论家，无鲁棒性处理）
  - 既有 DR-RL 算法（现有分布鲁棒强化学习方法，通常基于表格型价值迭代）

## 4. 资源与算力

- 在提供的摘要和元数据中，**未明确说明**使用的 GPU 型号、数量、训练时长或具体计算资源。
- 仅从文本可知，作者强调了 DR-SAC 相较于现有 DR-RL 算法**显著提升了计算效率**，并能够扩展到大规模问题，但未给出量化资源消耗数据。

## 5. 实验数量与充分性

- **实验组数**：摘要提及 5 个连续控制任务，核心对比为 DR-SAC 与 SAC 基线，以及 DR-SAC 与现有 DR-RL 算法的效率对比。
- **充分性评价**：
  - **优点**：任务数量虽然不算多，但连续控制任务覆盖了不同动力学特性，能够初步验证算法在连续动作空间的泛化能力；与 SAC 的对比也直接体现了鲁棒性提升。
  - **不足**：由于提供的文本只包含摘要，无法得知是否有消融实验（如对 KL 散度约束大小、生成模型选择、不确定集半径的敏感性分析）、多个随机种子的方差统计、以及不同扰动强度下的完整曲线。因此实验充分性在现有信息下**难以完全评估**，可能略偏薄弱。

## 6. 论文的主要结论与发现

- **性能优势**：在 5 个连续控制任务上，DR-SAC 在常见扰动下的平均奖励比 SAC 基线最高可提升 **9.8 倍**，说明鲁棒性优化能显著改善策略在环境变化下的表现。
- **理论贡献**：给出了分布鲁棒软策略迭代的收敛性保证，为非表格、基于演员-评论家的 DR-RL 提供了理论支撑。
- **实用价值**：相比既有 DR-RL 算法，DR-SAC 在计算效率和可扩展性上明显更好，适合更大规模的连续控制问题。
- **总体结论**：DR-SAC 是首个面向连续动作空间的演员-评论家结构分布鲁棒 RL 算法，成功将 SAC 的熵正则化优势与分布鲁棒优化结合，扩展了 DR-RL 的应用范围。

## 7. 优点

- **填补空白**：首次将 DR-RL 从表格型方法扩展到连续动作空间的演员-评论家框架，是方法论上的重要突破。
- **理论坚实**：推导并证明分布鲁棒软策略迭代的收敛性，算法有据可依。
- **技术实用**：采用生成式建模估计名义转移模型，避免了表格方法对大状态空间的不可行性，同时保持 KL 不确定集的简洁性与可解释性。
- **实验效果显著**：在扰动下相比 SAC 获得最高 9.8 倍平均奖励提升，展示了鲁棒性的巨大价值。
- **计算效率**：与已有 DR-RL 方法相比，DR-SAC 更适合大规模问题，具备实际部署潜力。

## 8. 不足与局限

- **实验细节缺失**：提供的文本未列出具体环境名称、扰动类型、超参数设置、种子的数量，无法验证实验结果的统计显著性。
- **消融与敏感性分析不足**：未提及对 KL 散度约束半径、生成模型容量、熵系数等关键设计选择的消融研究。
- **部署风险**：只测试了“常见扰动”，未覆盖对抗性最强、非平稳或结构性突变的最坏情况，鲁棒性的边界尚不明确。
- **离线学习依赖**：算法依赖离线数据集以及生成式建模对名义转移模型的估计，若离线数据覆盖不足或模型生成偏差较大，可能影响鲁棒性能。
- **理论假设限制**：KL 散度约束的不确定集是一种特定的模糊性描述，真实环境中可能存在不符合该假设的扰动类型。
- **资源信息不透明**：论文未披露训练所用的算力，限制了可复现性评估。

（完）
