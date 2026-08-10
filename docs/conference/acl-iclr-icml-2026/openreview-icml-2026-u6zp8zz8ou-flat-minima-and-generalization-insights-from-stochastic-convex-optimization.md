---
title: "Flat Minima and Generalization: Insights from Stochastic Convex Optimization"
title_zh: 平最小值与泛化：来自随机凸优化的洞见
authors: "Matan Schliserman, Shira Vansover-Hager, Tomer Koren"
date: 2026-04-30
pdf: "https://openreview.net/pdf/09c9a12837312c47addc57bdfc0dfd563c781cf7.pdf"
tags: ["query:rl-control"]
score: 5.0
evidence: 研究随机凸优化中平最小值与泛化行为，与凸优化理论和算法设计直接相关
tldr: 该论文在随机凸优化这一规范性设定下研究平最小值与泛化的关系，发现即使在此基本设定中，平经验最小值可能达到平凡的总体风险，而尖锐最小值却可以最优泛化。进一步证明该现象扩展至锐度感知算法。这一发现挑战了‘平最小值利于泛化’的普遍直觉，提示在优化算法设计中需要重新审视平最小化策略的有效性。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 理解学习算法为何泛化良好，常归因于收敛到平最小值；该文选取随机凸优化作为规范性设定检验此联系。
method: 在非负β-光滑随机凸优化目标下，理论上比较平经验最小值与尖经验最小值的总体风险，并分析锐度感知算法。
result: 发现平经验最小值可导致平凡泛化，而尖最小值泛化最优，与常见认知相反。
conclusion: 平最小值不一定带来好泛化，研究中需谨慎使用平最小化作为设计原则。
---

## Abstract
Understanding the generalization behavior of learning algorithms is a central goal of learning theory. A recently emerging explanation is that learning algorithms are successful in practice because they converge to flat minima, which have been consistently associated with improved generalization performance. 
In this work, we study the link between flat minima and generalization in the canonical setting of stochastic convex optimization with a non-negative, $\beta$-smooth objective.
Our first finding is that, even in this fundamental setting, flat empirical minima may incur trivial $\Omega(1)$ population risk while sharp minima generalizes optimally.
We then demonstrate that this phenomenon extends to sharpness-aware algorithms introduced by Foret et al. (2021), namely Sharpness-Aware Gradient Descent (SA-GD) and Sharpness-Aware Minimization (SAM).
For SA-GD we prove that it successfully converges to a flat minimum at a fast rate, but the population risk of the solution can still be as large as $\Omega(1)$.
For SAM we show that although it minimizes the empirical loss, it may converge to a sharp minimum and also incur population risk $\Omega(1)$. 
Finally, we establish population risk upper bounds for both SA-GD and SAM using algorithmic stability techniques.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与整体含义
- **研究动机**：理解学习算法为何能泛化良好是学习理论的核心问题。近年来一种流行解释是，算法实践成功是因为收敛到“平最小值”（flat minima），其与更好的泛化性能高度相关。
- **核心问题**：本文在**随机凸优化**这一规范、基础的理论设定下，严格考察平最小值与泛化之间的因果关系：平最小值是否必然带来低总体风险？
- **整体含义**：研究结果表明，即便在最基本的随机凸优化框架中，“平最小值利于泛化”这一普遍直觉也可能失效，这对以“平最小化”作为算法设计原则的做法提出了挑战。

## 2. 论文提出的方法论
- **理论设定**：考虑目标函数为非负且 $\beta$-光滑的随机凸优化问题。
- **研究路径**：
  - 对比**平经验最小值**与**尖（sharp）经验最小值**的总体风险（population risk）；
  - 将现象扩展到两类**锐度感知算法**：Sharpness-Aware Gradient Descent (SA-GD) 与 Sharpness-Aware Minimization (SAM)；
  - 对 SA-GD 分析其收敛行为与最终解的泛化风险；
  - 对 SAM 分析其经验损失最小化能力与收敛点的锐度/泛化特性；
  - 使用**算法稳定性（algorithmic stability）** 技巧为 SA-GD 和 SAM 建立总体风险上界。
- 论文为纯理论分析，摘要未提供具体的公式推导或算法伪代码细节。

## 3. 实验设计
- 摘要中**未提及任何数据集、benchmark 或实验对比方法**。
- 从内容推断，该工作属于**理论性研究**，以数学证明而非实验验证为主要手段。
- 没有说明是否在合成数据、实际数据集或具体任务上进行了数值验证。

## 4. 资源与算力
- 论文**未提及任何算力相关信息**，如 GPU 型号、数量、训练时长等。
- 由于缺少实验部分，推测主要依赖数学推导，计算资源需求不在讨论范围内。

## 5. 实验数量与充分性
- **实验数量**：未报告实验，因此不存在多组数据集实验或消融实验。
- **充分性与客观性评估**：
  - 理论证明结果需要依靠证明的严谨性来判断，但摘要中未给出证明细节；
  - 缺乏数值实验来展示理论结果在实际优化中的典型性；
  - 作为理论论文，其结论的普遍性取决于假设条件（非负、$\beta$-光滑、凸性）是否覆盖实际场景，这一局限性需读者自行评估。

## 6. 论文的主要结论与发现
- **发现一**：即使在随机凸优化这一基础设定下，**平经验最小值也可能导致平凡的 $\Omega(1)$ 总体风险**，即泛化差；而**尖锐最小值却可以实现最优泛化**。
- **发现二**：该现象可扩展至锐度感知算法：
  - **SA-GD** 能以较快速度收敛到平最小值，但其解的总体风险仍可能高达 $\Omega(1)$；
  - **SAM** 虽然最小化了经验损失，但可能收敛到尖锐最小值，同时也会产生 $\Omega(1)$ 的总体风险。
- **正面贡献**：利用算法稳定性技巧，为 SA-GD 和 SAM 建立了总体风险的上界，给出了泛化保证。

## 7. 优点
- **基础性挑战**：在规范的理论框架下，直接挑战“平最小值必然泛化更好”的主流认知，具有较高的理论价值。
- **覆盖流行算法**：同时分析 SA-GD 与 SAM 这两类当前广泛使用的锐度感知方法，使结论具有较强的现实相关性。
- **方法多样性**：结合凸优化分析与算法稳定性技术，为后续研究提供了分析工具。
- **结论清晰**：明确指出平最小化并不保证泛化，有助于引导研究者谨慎使用平最小化作为设计原则。

## 8. 不足与局限
- **假设范围的局限**：仅讨论非负、$\beta$-光滑的随机凸优化，而实际深度学习模型通常高度非凸，结论能否推广到非凸场景尚不明确。
- **缺乏实验验证**：论文未提供数值实验或实证案例，无法直观展示理论现象在实际训练中是否常见。
- **定义细节缺失**：摘要未说明“平”与“尖”的具体度量方式（如 Hessian 谱、邻域半径等），这可能会影响结论的适用范围。
- **反直觉例子的普遍性**：虽然构造了平最小值泛化差的例子，但未说明这类情况是否在典型优化问题中普遍存在，因此可能仅代表病态情形。
- **实际应用限制**：对 SAM/SA-GD 的负面结果可能依赖特定目标结构和噪声分布，在真实数据上的影响有待进一步研究。

（完）
