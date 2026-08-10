---
title: "Wasserstein Policy Gradient: Implicit Policies, Entropy Regularization and Linear Convergence"
title_zh: Wasserstein策略梯度：隐式策略、熵正则化与线性收敛
authors: "Zhaoyu Zhu, Shuhan Zhang, Rui Gao, Shuang Li"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=fEhJNjUeNG"
tags: ["query:rl-control"]
score: 9.0
evidence: 推导隐式策略的Wasserstein近端策略梯度更新并证明线性收敛。
tldr: 连续控制RL中，Wasserstein近端策略梯度常需策略密度或得分函数，限制其应用于隐式随机策略。本文提出新的WPPG更新，通过Wasserstein距离将迭代投影到参数策略族，无需密度或得分函数。在熵正则化与log-Sobolev条件下，证明精确与近似价值函数估计下迭代均线性收敛。实验还表明算法实现简单且在标准基准上表现竞争力。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: Wasserstein近端策略梯度依赖策略密度或得分函数，无法直接用于隐式随机策略。
method: 利用Wasserstein距离将迭代投影到参数策略族，导出无需密度或得分的新更新规则。
result: 在熵正则化和log-Sobolev条件下证明线性收敛，并在基准任务上表现优异。
conclusion: 为隐式策略的RL策略优化提供了可行且高效的Wasserstein梯度方法。
---

## Abstract
We revisit Wasserstein Proximal Policy Gradient (WPPG) for continuous control in infinite-horizon discounted reinforcement learning. By projecting the iterate of Wasserstein proximal gradient onto a parametric policy family with respect to the Wasserstein distance, we derive a new WPPG update that eliminates the need for policy densities or score functions. This makes our method directly applicable to implicit stochastic policies. We prove a linear convergence rate for the WPPG iterate under entropy regularization and a log-Sobolev condition on the policy class, for both exact and approximate value function estimates. Empirically, our algorithm is simple to implement and achieves competitive performance on standard benchmarks.

---

## 论文详细总结（自动生成）

好的，以下是基于您提供的论文元数据与摘要，对该论文进行的结构化中文总结。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：传统的**Wasserstein近端策略梯度（WPPG）** 方法在求解连续控制强化学习问题时，其每次迭代更新**严重依赖策略的密度函数或得分函数**。这种依赖导致该方法**无法直接应用于隐式随机策略**。
- **研究动机**：在连续控制任务中，许多先进的策略表示形式（如生成模型或某些随机模拟器）只能提供样本，而无法显式计算概率密度。为了打破WPPG的这一应用限制，本文旨在设计一种新的更新规则，使策略优化能够仅依赖样本（状态-动作对），从而扩展到更广泛的策略类别。

### 2. 论文提出的方法论

- **核心思想**：提出一种新的WPPG更新方法，通过引入**Wasserstein距离**作为度量，将Wasserstein近端梯度迭代步骤中的中间解**投影到参数化策略族**上。
- **关键技术细节**：
  - 摒弃了传统方法中必须计算策略概率密度或得分函数的步骤，使得算法可以直接作用于隐式策略模型。
  - 通过这种投影机制，算法实现了“无模型密度”的策略更新，只需从策略中采样即可完成迭代。
- **理论框架**：
  - 在目标函数中加入**熵正则化**项，以保证策略的探索性和分布形态。
  - 基于策略类满足的 **log-Sobolev不等式（LSI）** 条件，对迭代的收敛性进行刻画。
  - 分别在**精确价值函数估计**和**近似价值函数估计**两种情形下，均证明了WPPG迭代生成的策略序列以**线性收敛速度**收敛到最优策略。

### 3. 实验设计

- **实验场景与基准（Benchmark）**：论文使用了**标准强化学习连续控制基准任务**，但摘要及元数据中**未具体列出**使用了哪些具体的模拟环境（如MuJoCo、OpenAI Gym、DM Control等）。
- **对比方法**：摘要中仅说明算法“实现了具备竞争力的性能”（competitive performance），但**未明确提及**对比了哪些具体的基线算法（如PPO、SAC、TRPO或原版WPPG等）。

### 4. 资源与算力

- **说明**：论文摘要及提供的元数据中，**均未提及任何关于算力资源的信息**，包括GPU型号、数量、训练运行时长或总计算量预算等。

### 5. 实验数量与充分性

- **实验数量**：摘要中仅概括性地提到在“标准基准”上表现优异，**未提供具体的实验数量信息**（如测试了多少个任务、进行了多少组消融实验、做了多少次随机种子重复等）。
- **充分性与客观性评估**：基于现有的摘要信息，**无法对实验的充分性、客观性或公平性做出判断**。由于对比基线、任务列表和统计口径均未披露，当前的实验描述缺乏足够的透明度来支撑“竞争力”的全面验证。

### 6. 论文的主要结论与发现

- **方法可行性**：提出了一种无需密度/得分函数的WPPG变体，成功地将Wasserstein策略优化方法推广至隐式随机策略场景。
- **收敛性保证**：在熵正则化与log-Sobolev条件下，该算法在精确和近似价值函数估计下均实现了**线性收敛速度**，为实际应用提供了坚实的理论保障。
- **实践表现**：算法易于实现，在标准控制基准上取得了具有竞争力的性能，验证了理论设计的实用性。

### 7. 优点

- **理论创新性强**：在理论上巧妙利用Wasserstein几何结构进行投影，避免了密度估计这一隐性瓶颈，并给出了严格的线性收敛性证明，贡献扎实。
- **方法论具有普适性**：新方法打破了对策略密度或得分函数的依赖，为隐式策略（例如基于采样的模型）在强化学习优化中扫清了主要障碍。
- **理论与实践兼顾**：不仅提供了完整的数学证明（涵盖精确和近似估计两种工况），还给出了简单的实现方式和实证结果，填补了理论到应用的鸿沟。

### 8. 不足与局限

- **实验细节缺失（主要局限）**：摘要和元数据中没有列出具体的benchmark名称、对比基线和超参数设置，导致读者难以评估其在社区公认标准下的真实性能位次。
- **理论假设限制**：线性收敛性的成立依赖于**熵正则化**和**log-Sobolev条件**（通常对分布尾部有要求），这在某些目标分布极复杂或高维场景下可能难以满足，限制了理论保证的适用范围。
- **资源与消融说明空白**：缺少关于计算资源、训练时长以及消融实验（如对熵系数、学习率、投影步数敏感性的探讨）的说明，使得复现成本和技术调优细节对读者不够友好。
- **应用边界**：文章主要针对连续控制问题，对离散动作空间或混合动作空间的有效性尚无讨论。

---

（完）
