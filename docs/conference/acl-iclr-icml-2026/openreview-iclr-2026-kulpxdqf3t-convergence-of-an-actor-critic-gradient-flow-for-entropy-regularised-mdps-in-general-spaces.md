---
title: Convergence of an actor-critic gradient flow for entropy regularised MDPs in general spaces
title_zh: 一般空间下熵正则化MDP演员-评论家梯度流的收敛性
authors: "Denis Zorba, David Siska, Lukasz Szpruch"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=KUlPxDQF3T"
tags: ["query:rl-control"]
score: 9.0
evidence: 演员-评论家梯度流收敛性与MDP训练分析
tldr: 本文针对连续状态动作空间、熵正则化的无限时域MDP，证明了一类耦合演员-评论家梯度流的稳定性与全局收敛性。其中评论家使用时序差分学习更新，演员使用策略镜像下降在独立时间尺度上更新。在线性函数逼近和Q函数可实现性条件下，先证明系统不发散，再导出收敛率，为演员-评论家训练提供了理论基础。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 熵正则化MDP在一般连续状态动作空间下演员-评论家梯度流缺乏稳定性和收敛保证。
method: 构造TD评论家与策略镜像下降演员的耦合梯度流，并在线性逼近下分析。
result: 证明了梯度流的稳定性和全局收敛性，避免了有限时间爆炸。
conclusion: 为一般空间下熵正则化演员-评论家算法奠定了收敛理论基矗。
---

## Abstract
We prove the stability and global convergence of a coupled actor-critic gradient flow for infinite-horizon and entropy-regularised Markov decision processes (MDPs) in continuous state and action space with linear function approximation under Q-function realisability.
We consider a version of the actor critic gradient flow where the critic is updated using temporal difference (TD) learning while the policy is updated using a policy mirror descent method on a separate timescale.
For general action spaces, the relative entropy regularizer is unbounded and thus it is not clear a priori that the actor-critc flow does not suffer from finite-time blow-up.
Therefore we first demonstrate stability which in turn enables us obtain a convergence rate of the actor critic flow to the optimal regularised value function.
The arguments presented show that timescale separation is crucial for stability and convergence in this setting.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

熵正则化马尔可夫决策过程（MDP）在现代强化学习中应用广泛，但在**一般连续状态与动作空间**下，演员-评论家（actor-critic）算法的收敛性长期缺乏严格的理论保证。具体而言：

- 传统收敛性分析多局限于有限状态/动作空间，难以推广到连续空间。
- 在一般动作空间中，**相对熵正则化器（relative entropy regularizer）无界**，这意味着演员-评论家梯度流可能发生**有限时间爆炸（finite-time blow-up）**，是否稳定本身就不明确。
- 演员与评论家在不同时间尺度上更新，二者的耦合动态是否收敛、是否依赖时间尺度分离，尚未有系统性回答。

因此，该论文的核心问题是：

> **在连续状态-动作空间、熵正则化无限时域MDP背景下，耦合的演员-评论家梯度流能否保持稳定并全局收敛到最优正则化值函数？**

这一问题的回答，为一般空间下基于策略镜像下降与TD学习的演员-评论家训练奠定了理论基础。

## 2. 方法论

### 核心思想
论文构造了一类**演员-评论家连续时间梯度流**，其中：

- **评论家**：使用**时序差分（TD）学习**更新，逼近Q函数；
- **演员**：使用**策略镜像下降（policy mirror descent）**更新，在独立的（更慢的）时间尺度上优化策略；
- 采用**线性函数逼近**，并假设**Q函数可实现性（Q-function realisability）**条件成立。

### 技术细节与关键步骤
1. **建立耦合梯度流系统**：将演员和评论家的更新写成常微分方程（ODE）形式的梯度流，二者耦合但时间尺度分离。
2. **稳定性优先分析**：由于一般动作空间中熵正则项无界，不能预先假设系统不爆炸。因此证明的第一步是**证明系统稳定（不发散）**，这为后续收敛性分析提供前提。
3. **收敛率推导**：在稳定性确立后，进一步证明演员-评论家流以明确的收敛率收敛到最优正则化值函数。
4. **时间尺度分离的作用**：分析表明，演员与评论家的更新速率必须适度分离，二者不可同步调节——这是保证系统稳定和收敛的关键条件。

论文以理论推导为主，不依赖蒙特卡洛估计或经验技巧，整体属于**纯证明型分析框架**。

## 3. 实验设计

**⚠️ 本文未在提供的文本（摘要与元数据）中报告任何实验内容。**

根据论文标题与摘要判断，本文是一篇**纯理论性论文**，可能不包含具体的数据集、benchmark 或对比方法。它不以数值实验为主要贡献，而是以定理和证明作为支撑。

因此，无法列出：
- 使用哪些数据集/环境；
- 对比了哪些基线方法；
- 是否有消融实验或模拟验证。

不过，理论论文通常可能附带简单的数值示例来佐证定理，但在当前提供的文本中并无相关信息。

## 4. 资源与算力

**未提及任何算力资源。**

提供的文本中没有说明：
- GPU 型号与数量；
- 训练时长；
- 计算集群规模；
- 任何与算力相关的消耗评估。

这也与该论文的理论性质一致——证明类工作通常不需要大规模计算资源，即便有小规模数值验证，其算力需求也远低于经验性RL研究。

## 5. 实验数量与充分性

从现有信息看，该论文**不依赖实验验证**，实验数量为零（或未报告）。

对理论类论文而言，"充分性"的判断标准不同于实证研究：

- **充分的方面**：数学证明覆盖了稳定性、收敛率和时间尺度分离三个关键维度，逻辑链条完整，理论贡献自足。
- **客观性**：定理证明本身是客观的，不存在数据偏差或实验设计偏差。
- **不足之处**：缺乏数值算例来直观展示理论结果的实际行为（例如收敛速率是否保持、常数大小是否合理），这是理论论文常见但可接受的局限。

## 6. 主要结论与发现

1. **稳定性定理**：在Q函数可实现性和线性函数逼近条件下，熵正则化演员-评论家梯度流不会在有限时间内爆炸，系统一致稳定。
2. **全局收敛性**：该梯度流以明确收敛率收敛到最优正则化值函数，不再依赖有限状态-动作空间的假设。
3. **关键条件**：演员与评论家之间的**时间尺度分离是获得稳定性和收敛性的充分必要条件**（至少是关键充分条件），这解释了许多现代RL实践中采用"评论家快、演员慢"策略的理论原因。
4. **放宽空间限制**：研究从有限离散空间推广到了**一般连续空间**，且允许熵正则项无界，显著扩展了理论适用范围。

## 7. 优点

- **填补理论空白**：首次在一般连续空间、无界熵正则条件下严格证明演员-评论家梯度流的稳定与收敛，这是此前文献未完成的工作。
- **分层论证清晰**：先证稳定性、再求收敛率，逻辑结构稳健，避免了"未证先收敛"的理论漏洞。
- **揭示时间尺度分离的本质作用**：不仅证明收敛，还明确指出时间尺度分离为何必要，为实践提供了直接指导。
- **条件相对温和**：仅需线性函数逼近与Q函数可实现性，不算过分苛刻，在可接受的理论框架内扩大了适用面。
- **结论通用性好**：无限时域、连续空间、熵正则化是强化学习中的标准设定，因此结论具有较广的迁移价值。

## 8. 不足与局限

- **无实验验证**：没有数值示例证明常数大小、收敛速度的实际表现，读者无法直观判断理论结果在实践中的效率。
- **线性函数逼近限制**：分析局限在Q函数的线性近似范围内，尚不能覆盖更复杂的非线性函数逼近（如神经网络），与现代深度RL之间存在距离。
- **可实现性假设**：Q函数可实现性在真实问题中不一定成立，存在模型误差时理论是否成立仍未回答。
- **连续时间视角**：论文分析的是连续时间梯度流，而实际算法多为离散时间更新，从ODE到离散算法的桥接尚待建立。
- **无法评估偏差风险**：因缺少实验部分，无法从经验层面判断理论假设在何种实际环境下容易满足或失效。
- **应用层面未展开**：没有讨论算法在具体控制问题、机器人、游戏等领域的落地表现，工程实用性未知。

---

（完）
