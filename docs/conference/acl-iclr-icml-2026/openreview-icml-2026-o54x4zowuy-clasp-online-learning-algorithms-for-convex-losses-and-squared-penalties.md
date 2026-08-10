---
title: "CLASP: Online learning algorithms for Convex Losses And Squared Penalties"
title_zh: CLASP：面向凸损失与平方罚项的在线学习算法
authors: "Ricardo N. Ferreira, Joao Xavier, Claudia Soares"
date: 2026-04-30
pdf: "https://openreview.net/pdf/e813f37cee491f3eb7521ef25279d73196e68883.pdf"
tags: ["query:rl-control"]
score: 8.0
evidence: 面向带约束在线凸优化的框架，使用平方罚函数与投影简化算法，直接针对凸优化求解问题。
tldr: 在带约束的在线凸优化中，投影操作往往代价高昂。本文提出CLASP框架，引入平方罚函数并利用收缩算子处理静态决策集与时变约束，支持联合或分离式更新。理论分析给出凸损失下强遗憾界，且实现更简单。该工作为在线约束优化提供了灵活且高效的新算法族。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 在线凸优化需要在动态变化的约束下同时最小化累积损失，已有方法在投影复杂时效率低。
method: 提出CLASP框架，联合或分离处理静态决策集和时变约束，并利用收缩算子理论分析保证。
result: 在凸损失下，CLASP算法实现了领先的遗憾界，同时在投影困难时也更易实现。
conclusion: CLASP为约束在线凸优化提供了统一、灵活的算法框架，并提供了新的理论分析工具。
---

## Abstract
Addressing Constrained Online Convex Optimization (COCO), we introduce CLASP (Convex Losses And Squared Penalties), a framework that minimizes cumulative loss together with squared constraint violations. We propose two variants of CLASP, CLASP-I and CLASP-F, allowing for a joint or separate handling of the static decision set and the time-varying constraints, a decoupling flexibility that affords simpler implementations when projections onto the static decision set are easy. Our theoretical analysis departs from prior work by fully leveraging the variety of \emph{cutter operators}, and contraction properties such as the strongly quasi-nonexpansiveness, a proof strategy not previously applied in this setting. For convex losses, both CLASP algorithms achieve regret $O\left(T^{\max\\{\beta,1-\beta\\}}\right)$ and cumulative squared penalty $O\left(T^{\\{1-\beta\\}}\right)$ for any $\beta \in (0,1)$. Most importantly, for strongly convex problems, we provide the first logarithmic guarantees on both regret and cumulative squared penalty: In the strongly convex case, both CLASP algorithms guarantee that the regret is upper bounded by $O( \log T )$ and the cumulative squared penalty is also upper bounded by $O( \log T )$.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- 本文研究**带约束的在线凸优化（Constrained Online Convex Optimization, COCO）**问题，即在每个时刻决策者需要从静态决策集与一系列时变约束中做出选择，同时最小化累积损失。
- 现有方法的一个主要瓶颈是：当约束或决策集结构复杂时，**投影操作的计算代价高昂**，导致算法难以在大规模或实时场景中高效运行。
- 已有理论分析往往依赖投影算子的特定性质，对更一般的算子族缺乏统一处理，限制了算法设计的灵活性。
- 本文提出的 CLASP 框架旨在**同时最小化累积损失与平方约束违反量**，通过引入平方罚项来避免频繁投影，从而在保证遗憾界的同时简化实现。
- 整体而言，这项工作为在线约束优化提供了一种更灵活、高效且理论上可保证的新思路。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 核心思想
- 将原始约束优化问题转化为**“损失 + 平方罚项”**的联合优化问题：在每个时刻，算法不仅考虑当前损失，还考虑对时变约束的违反程度，并以平方罚形式加入目标。
- 为了处理静态决策集和时变约束，CLASP 提供了两种变体：
  - **CLASP-I**：联合处理静态决策集与时变约束；
  - **CLASP-F**：分离处理两者，特别适用于静态决策集上投影简单的场景。
- 这种解耦灵活性允许在投影操作容易时采用更简单、低代价的更新规则。

### 关键技术细节
- 理论分析不再局限于常见的正交投影算子，而是**充分利用“割算子”（cutter operators）的多样性**。
- 引入**强准非扩张性（strongly quasi-nonexpansiveness）**等收缩性质，作为证明遗憾界的关键工具。这是一种此前未被应用于该问题场景的证明策略。
- 算法更新规则通过收缩算子与平方罚项结合，避免了对时变约束集的显式投影，从而降低计算复杂度。

### 算法流程（文字描述）
1. 初始化决策变量。
2. 对每个时刻 \( t \)：
   - 接收当前损失函数（凸或强凸）；
   - 基于平方罚项构造一个包含损失和约束违反的中间目标；
   - 使用收缩算子（cutter operator）对决策变量进行更新，同时处理静态决策集与时变约束（CLASP-I），或分别处理（CLASP-F）；
   - 输出决策并观察实际损失。
3. 累积更新过程，并利用强准非扩张性进行遗憾分析。

### 理论保证（公式摘要）
- 对任意 \(\beta \in (0,1)\)，在凸损失下：
  - 遗憾界：\(O\left(T^{\max\{\beta,1-\beta\}}\right)\)
  - 累积平方罚：\(O\left(T^{1-\beta}\right)\)
- 在强凸损失下（重要贡献）：
  - 遗憾界：\(O(\log T)\)
  - 累积平方罚：\(O(\log T)\)
- 这是**首个同时获得对数级遗憾与对数级平方罚保证**的结果。

## 3. 实验设计

- 论文摘要及元数据中**未提供任何关于实验数据集、场景或基准（benchmark）的信息**。
- 也**未提到与哪些基线方法进行对比**（如标准的在线投影梯度法、惩罚对偶法等）。
- 因此，本总结无法基于现有文本描述具体实验设计。若需要完整实验细节，需访问论文全文（当前 PDF 提取文本被 CAPTCHA 阻断，仅有摘要与元数据）。

## 4. 资源与算力

- 文中**没有提供任何关于 GPU 型号、数量、训练时长或计算资源的信息**。
- 考虑到该工作属于在线优化理论方向，可能以理论分析与简单数值模拟为主，但现有文本无法确认。

## 5. 实验数量与充分性

- 由于未获取到实验章节，**无法判断进行了多少组实验、是否包含消融研究、是否覆盖多样本场景**。
- 基于摘要来看，理论贡献是主要卖点，但**实验验证的充分性无法评估**。
- 若论文包含实验，需要进一步阅读全文来判断其客观性与公平性；从当前信息无法给出评价。

## 6. 主要结论与发现

- CLASP 框架能够有效地解决带约束在线凸优化问题，同时处理损失最小化与约束满足。
- 两种变体（CLASP-I 与 CLASP-F）在凸损失下的遗憾界与平方罚界达到了理论上的合理折中。
- 在强凸情形下，CLASP 同时实现了遗憾 \(O(\log T)\) 与累积平方罚 \(O(\log T)\)，这是该领域内首次给出的对数级双重保证。
- 通过引入割算子与强准非扩张性，提供了新的分析工具，拓宽了在线约束优化算法的设计空间。

## 7. 优点

- **统一的算法框架**：联合或分离处理静态集与时变约束，适应不同场景，具有很好的灵活性。
- **实现简单**：在静态决策集投影容易时，CLASP-F 可大幅简化更新步骤。
- **理论贡献突出**：首次在强凸问题上同时给出遗憾与平方罚的对数界，意义较大。
- **证明技术新颖**：用强准非扩张收缩性质分析在线约束问题，证明策略有启发性。

## 8. 不足与局限

- **实验信息缺失**：根据现有提取文本，无法验证算法在实际数据上的表现，缺乏与现有方法的实证对比。
- **应用限制**：算法中的收缩算子与平方罚参数选择需要一定调优，可能影响实际收敛速度。
- **理论假设**：结果依赖于凸性或强凸性假设，对于非凸损失或更复杂的约束结构，适用性尚未说明。
- **计算复杂度**：虽然避免投影，但割算子的计算代价可能因问题而异，文中未讨论具体实现细节。
- **可读性受限**：当前 PDF 文本被验证页阻断，导致无法全面评估细节，以上局限性仅为基于摘要的推断。

（完）
