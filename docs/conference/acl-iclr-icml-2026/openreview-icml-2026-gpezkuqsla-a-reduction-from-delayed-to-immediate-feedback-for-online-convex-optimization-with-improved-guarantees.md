---
title: A Reduction from Delayed to Immediate Feedback for Online Convex Optimization with Improved Guarantees
title_zh: 从延迟反馈到即时反馈的约简：在线凸优化的改进保证
authors: "Alexander Ryabchenko, Idan Attias, Daniel M. Roy"
date: 2026-01-23
pdf: "https://openreview.net/pdf/5f25322f6c165329114e136b4f34bc17cc17d9f0.pdf"
tags: ["query:rl-control"]
score: 9.0
evidence: 针对延迟反馈在线凸优化提出约简框架，改进bandit与一阶凸优化的遗憾界，属于凸优化算法/求解器研究
tldr: 该文提出一种基于约简的框架，用于处理在线凸优化中的延迟反馈问题。通过引入连续时间模型，将遗憾分解为延迟无关的学习项与延迟引起的漂移项，从而可将任意在线线性优化算法转换为支持任意延迟的算法。在bandit凸优化上显著改进遗憾界，在一阶反馈中恢复最优界且分析更简洁，统一并提升了对延迟反馈的理论保证。
source: ICML-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 在线凸优化中延迟反馈带来额外遗憾，现有结果不一致，需要统一且改进的处理框架。
method: 提出延迟自适应约简，利用连续时间模型将在线线性优化算法改造为支持任意延迟的在线凸优化算法。
result: bandit凸优化遗憾界显著改进，一阶反馈恢复最优界且分析简化。
conclusion: 该框架为延迟反馈在线凸优化提供了统一且更强的理论保证，可兼容多种优化算法。
---

## Abstract
We develop a reduction-based framework for online learning with delayed feedback that recovers and improves upon existing results for both first-order and bandit convex optimization. Our approach introduces a continuous-time model under which regret decomposes into a delay-independent learning term and a delay-induced drift term, yielding a delay-adaptive reduction that converts any algorithm for online linear optimization into one that handles arbitrary delays. For bandit convex optimization, we significantly improve existing regret bounds, with delay-dependent terms matching state-of-the-art first-order rates. For first-order feedback, we recover state-of-the-art regret bounds via a simpler, unified analysis.    
    
Quantitatively, for bandit convex optimization we obtain $O(\sqrt{d_{\text{tot}}} + T^{\frac{3}{4}}\sqrt{k})$ regret, improving the delay-dependent term from $O(\min\{\sqrt{T d_{\text{max}}},(Td_{\text{tot}})^{\frac{1}{3}}\})$ in previous work to $O(\sqrt{d_{\text{tot}}})$. Here, $k$, $T$, $d_{\text{max}}$, and $d_{\text{tot}}$ denote the dimension, time horizon, maximum delay, and total delay, respectively. Under strong convexity, we achieve $O(\min\{\sigma_{\text{max}} \ln T, \sqrt{d_{\text{tot}}}\} + (T^2\ln T)^{\frac{1}{3}} k^{\frac{2}{3}})$, improving the delay-dependent term from $O(d_{\max} \ln T)$ in previous work to $O(\min\{\sigma_{\text{max}} \ln T, \sqrt{d_{\text{tot}}}\})$, where $\sigma_{\text{max}}$ denotes the maximum number of outstanding observations and may be considerably smaller than $d_{\text{max}}$.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究问题**：在线凸优化（Online Convex Optimization, OCO）中，反馈信号往往存在**时间延迟**（delayed feedback），这会导致累积遗憾（regret）相比即时反馈情形产生额外损失。如何在存在延迟的情况下获得尽可能低的遗憾界，是该领域的核心难题。
- **背景动机**：
  - 现有针对延迟反馈的研究结果在**一阶反馈**（first-order feedback，即梯度反馈）和**bandit反馈**（仅函数值反馈）之间不一致，缺乏统一的处理框架。
  - 已有方法的延迟相关遗憾界存在明显改进空间，例如bandit凸优化中延迟项为 $O(\min\{\sqrt{T d_{\max}}, (T d_{\text{tot}})^{1/3}\})$，而强凸情形下延迟项为 $O(d_{\max} \ln T)$，均弱于预期最优水平。
  - 需要一个**统一、简洁且更强**的约简框架，使得任意在线线性优化（Online Linear Optimization, OLO）算法都能直接转化为支持**任意延迟**的在线凸优化算法。

## 2. 提出的方法论：核心思想与技术细节

- **核心思想**：提出一种**基于约简（reduction-based）** 的延迟自适应框架，将延迟反馈问题转化为即时反馈问题。
  - 引入**连续时间模型（continuous-time model）**，将遗憾分解为两个部分：
    - **延迟无关的学习项**（delay-independent learning term）
    - **延迟引起的漂移项**（delay-induced drift term）
  - 通过控制漂移项的增长，实现延迟自适应的约简。
- **关键转化机制**：该约简框架可以将**任意在线线性优化算法**转换为支持**任意延迟**的在线凸优化算法——即“从延迟反馈到即时反馈的约简”。
- **遗憾界公式**：
  - **Bandit凸优化**：获得 $O(\sqrt{d_{\text{tot}}} + T^{3/4}\sqrt{k})$ 的遗憾界，将延迟相关项从 $O(\min\{\sqrt{T d_{\max}}, (T d_{\text{tot}})^{1/3}\})$ 改进到 $O(\sqrt{d_{\text{tot}}})$。其中 $k$ 为维度，$T$ 为时间范围，$d_{\max}$ 为最大延迟，$d_{\text{tot}}$ 为总延迟。
  - **强凸情形**：获得 $O(\min\{\sigma_{\max} \ln T, \sqrt{d_{\text{tot}}}\} + (T^2 \ln T)^{1/3} k^{2/3})$ 的遗憾界，将延迟相关项从 $O(d_{\max} \ln T)$ 改进到 $O(\min\{\sigma_{\max} \ln T, \sqrt{d_{\text{tot}}}\})$。其中 $\sigma_{\max}$ 为**最大未处理观测数**（outstanding observations），通常远小于 $d_{\max}$。
- **一阶反馈**：通过更简洁的统一分析恢复现有最优遗憾界。

## 3. 实验设计

- **数据集/场景**：论文内容中**未明确描述**具体实验数据集或评测场景。从方法论性质来看，该工作属于**理论型研究**（regret bound 分析），通常可能采用合成数据或在线学习benchmark的数值模拟来验证遗憾界，但提取的文本中未提供相关细节。
- **Benchmark 与对比方法**：未明确列出对比的基线方法，但在理论层面参照了前人在bandit凸优化和强凸场景下的遗憾界结果（如 $O(\min\{\sqrt{T d_{\max}}, (T d_{\text{tot}})^{1/3}\})$ 和 $O(d_{\max} \ln T)$ 等）。

## 4. 资源与算力

- 论文内容中**完全没有提及**所需的算力资源，包括GPU型号、数量、训练时长等。
- 由于该工作侧重理论推导与遗憾界证明，推测其计算资源需求较低（可能仅需小规模模拟验证），但这一点在可获取的内容中**未得到确认**。

## 5. 实验数量与充分性

- **实验数量**：从可获取的文本内容来看，**未提供任何实验设计信息**，因此无法确认是否开展了数值实验及实验组数。
- **充分性评估**：
  - 该论文的核心贡献在于**理论保证的改进**，其充分性主要体现为遗憾界的严格数学推导是否自洽、与已有结果的对比是否完备。
  - 然而，缺少必要的数值验证（如不同延迟分布、维度、时间范围下的模拟对比），在实验层面客观上**不够充分**。
  - 若存在实验，其公平性（如是否与同设置下的基线统一部署）也无法从现有材料中判断。

## 6. 论文的主要结论与发现

- **统一框架**：提出了一种延迟自适应的约简框架，能够将任意在线线性优化算法转化为支持任意延迟的在线凸优化算法，统一了此前不同反馈模式下的分散结果。
- **Bandit凸优化改进**：遗憾界中的延迟相关项从 $O(\min\{\sqrt{T d_{\max}}, (T d_{\text{tot}})^{1/3}\})$ 显著改进到 $O(\sqrt{d_{\text{tot}}})$，且延迟项匹配了当前最先进的一阶反馈速率。
- **强凸场景改进**：延迟相关项从 $O(d_{\max} \ln T)$ 改进到 $O(\min\{\sigma_{\max} \ln T, \sqrt{d_{\text{tot}}}\})$，其中 $\sigma_{\max}$（最大未处理观测数）可能比 $d_{\max}$ 小得多，从而在实际延迟模式中收益更大。
- **一阶反馈**：在更简洁的统一分析下恢复了最优遗憾界。
- **总体结论**：该框架为延迟反馈在线凸优化提供了**统一且更强**的理论保证，且具备良好的算法兼容性。

## 7. 优点

- **理论创新性强**：连续时间模型下的遗憾分解（学习项 + 漂移项）是一个干净且富有解释力的分析工具。
- **统一性**：同时覆盖一阶反馈与bandit反馈，弥合了此前两类结果之间的理论鸿沟。
- **改善显著**：bandit凸优化的延迟项从 $T$ 的函数改进为仅依赖 $d_{\text{tot}}$，改进幅度大。
- **灵活性**：任何在线线性优化算法都可通过该约简“即插即用”，适用范围广。
- **分析简洁**：即使在一阶反馈中也能通过统一框架恢复最优结果，说明框架本身不是以牺牲简洁性为代价的。

## 8. 不足与局限

- **缺乏实验验证信息**：可获取的内容中未提及任何数值实验，难以验证理论界在实际问题中是否紧致、常数因子是否合理。
- **依赖假设未完全展开**：例如 $\sigma_{\max}$ 与 $d_{\max}$ 的大小关系、延迟的分布假设（是否有界、是否随机）等细节在可获取内容中未充分讨论。
- **实际部署问题**：将任意OLO算法转化为延迟自适应算法的过程是否引入额外的计算开销或存储开销，文中未提及。
- **仅限凸设置**：该框架针对在线凸优化，扩展到非凸或对抗性更强的设定可能受限。
- **发表状态**：该论文标记为 ICML-2026-Rejected-Public，虽然评分较高（9.0），但被拒原因在提供内容中无从得知，可能存在审稿人指出的未被覆盖的缺陷。

（完）
