---
title: Dynamic Programming for Epistemic Uncertainty in Markov Decision Processes
title_zh: 马尔可夫决策过程中认知不确定性的动态规划
authors: "Axel Benyamine, Julien Grand-Clément, Marek Petrik, Michael I. Jordan, Alain Oliviero Durmus"
date: 2026-04-30
pdf: "https://openreview.net/pdf/c5006090f541129760edc1284b2fb905c4ccbd9d.pdf"
tags: ["query:rl-control"]
score: 9.0
evidence: 将动态规划与贝尔曼算子扩展到模糊厌恶型MDP
tldr: 传统MDP忽略转移概率的不确定性，本文提出模糊厌恶MDP框架，将转移概率视为随机变量并用风险度量评估策略回报。在此框架下扩展了值函数和贝尔曼算子，建立了动态规划原则，包括平稳策略存在性、值迭代与策略迭代算法。工作还刻画了与动态规划兼容的律不变风险度量，统一了多种认知不确定性MDP模型。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 传统MDP未建模认知不确定性，现有模糊厌恶模型缺乏统一理论。
method: 提出模糊厌恶MDP框架，用随机转移概率与风险度量定义策略评价，扩展动态规划算子。
result: 证明了平稳策略存在性，给出值和策略迭代算法，并刻画可兼容的风险度量类。
conclusion: 统一了多种带认知不确定性的MDP模型，为鲁棒决策提供理论支撑。
---

## Abstract
In this paper, we propose a general theory of ambiguity-averse MDPs, which treats the uncertain transition probabilities as random variables and evaluates a policy via a risk measure applied to its random return. This ambiguity-averse MDP framework unifies several models of MDPs with epistemic uncertainty for specific choices of risk measures.  We extend the concepts of value functions and Bellman operators to our setting. Based on these objects, we establish the consequences of dynamic programming principles in this framework (existence of stationary policies, value and policy iteration algorithms), and we completely characterize law-invariant risk measures compatible with dynamic programming. Our work draws connections among several variants of MDP models and fully delineates what is possible under the dynamic programming paradigm and which risk measures require leaving it.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机与背景）

- 传统马尔可夫决策过程（MDP）假设转移概率已知，忽略了现实决策中普遍存在的**认知不确定性**（epistemic uncertainty）。
- 已有的模糊厌恶（ambiguity-averse）MDP 模型虽然尝试建模这种不确定性，但缺乏统一的理论框架，不同模型之间相互割裂。
- 本文的目标是提出一个**一般化的模糊厌恶 MDP 理论**，将转移概率视为随机变量，并通过风险度量（risk measure）评估策略的随机回报，从而统一多种带认知不确定性的 MDP 模型，为鲁棒决策提供理论支撑。

## 2. 提出的方法论：核心思想、技术细节与算法流程

- **核心思想**：不再假设转移概率是固定已知的，而是将其建模为随机变量；策略的价值被定义为该策略在随机转移概率下随机回报的风险度量值。通过选择不同的风险度量，该框架可以统一现有的多种模糊厌恶 MDP 模型。
- **关键扩展**：将传统 MDP 中的**值函数**与**贝尔曼算子**概念推广到上述模糊厌恶 MDP 设定中。
- **动态规划原则**：基于扩展后的值函数和贝尔曼算子，证明了动态规划原则在该框架下成立，具体包括：
  - 平稳策略（stationary policies）的存在性；
  - 值迭代（value iteration）算法的可行性；
  - 策略迭代（policy iteration）算法的可行性。
- **刻画兼容性条件**：完整刻画了与动态规划兼容的**律不变风险度量**（law-invariant risk measures）类，明确了哪些风险度量能够保留动态规划结构，哪些需要放弃动态规划范式。

## 3. 实验设计

- 论文内容中**未提供任何具体实验设计**，包括使用的数据集、场景、基准（benchmark）或对比方法。
- 从摘要来看，该工作以理论推导和性质刻画为主，并未强调数值实验或应用验证。

## 4. 资源与算力

- 文中**未提及**任何计算资源信息，例如 GPU 型号、数量、训练时长等。
- 鉴于论文为理论性工作，可能不涉及大规模算力消耗，但这一点在提供的内容中没有明确说明。

## 5. 实验数量与充分性

- 由于论文材料中**没有实验部分**，无法评估实验组数、消融实验或对比实验。
- 仅从摘要判断，该研究主要通过数学证明完成理论构建，其充分性更体现在理论推导的严密性与统一性上，而非实证验证。

## 6. 主要结论与发现

- 提出了一个统一的一般化模糊厌恶 MDP 框架，能够涵盖多种带认知不确定性的 MDP 模型。
- 将值函数和贝尔曼算子扩展到该框架，并证明了动态规划原则（平稳策略存在性、值迭代与策略迭代算法）依然成立。
- 完整刻画了与动态规划兼容的律不变风险度量，界定了动态规划范式的适用边界，即回答了“哪些风险度量可以用动态规划，哪些必须离开该范式”的问题。
- 该工作为鲁棒决策提供了统一的理论基础，并联系了多个 MDP 变体模型。

## 7. 优点

- **统一性强**：将多种模糊厌恶 MDP 模型纳入同一框架，用风险度量这一统一视角连接不同变体。
- **理论贡献深刻**：不仅扩展了动态规划概念，还给出了律不变风险度量与动态规划兼容性的完全刻画，具有明确的边界性结论。
- **方法论价值高**：证明了平稳策略、值迭代和策略迭代等核心算法在该框架下仍然有效，直接可指导后续算法设计。
- **表述清晰**：摘要信息密集，问题、方法、结果和结论环环相扣。

## 8. 不足与局限

- **缺乏实验验证**：提供的材料中没有数值实验或案例研究，无法直观展示框架在实际决策问题中的效果。
- **适用范围受限**：风险度量仅限于“律不变”类别，对于非律不变风险度量，动态规划原则可能失效，需要另寻方法。
- **理论门槛较高**：框架高度抽象，对实际从业者来说理解与应用可能有一定难度。
- **未讨论计算复杂度**：值迭代和策略迭代在模糊厌恶设定下的具体计算成本与实现细节未被提及。

（完）
