---
title: Option Discovery via Differentiable Neural Decomposition
title_zh: 通过可微神经分解进行选项发现
authors: "Reza Abdollahzadeh, Parnian Behdin, Kiarash Aghakasiri, Levi Lelis"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=znsrpkKqrp"
tags: ["query:rl-control"]
score: 6.0
evidence: 通过可微神经分解学习神经元与输入掩码，在RL中发现可复用选项。
tldr: 基于神经网络分解的选项发现面临组合搜索难题，因为网络子函数数量随规模指数增长。本文将子函数提取转化为对神经元和输入学习掩码的可微问题，从而将组合搜索变为可微优化。神经元掩码决定执行哪些子函数，输入掩码决定如何调用。实验表明该可微方法能有效发现下游任务可用的选项，扩展了RL的时间抽象学习。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 网络规模增大使子函数数量指数增长，导致传统选项发现陷入困难的组合搜索。
method: 将子函数提取转化为网络神经元与输入的掩码学习，使组合搜索成为可微优化问题。
result: 实验显示可学习到下游任务有用的子函数与默认输入参数，提高选项发现效率。
conclusion: 为RL中的时间抽象发现提供可微方案，降低了组合搜索的复杂度。
---

## Abstract
Option discovery via neural network decomposition is a promising way of discovering temporally extended actions in reinforcement learning. The challenge is that the number of sub-functions a network encodes grows exponentially with its size, so finding sub-functions that can be useful in downstream tasks is a difficult combinatorial search problem. In this paper, we turn this combinatorial search problem into a differentiable problem by showing that extracting sub-functions from a network is equivalent to learning masks over the neurons of the network. In addition to extracting sub-functions, we can also learn default input parameters to such sub-functions through masks over the inputs. Neuron masks select what to execute; input masks specify how to call it. We evaluate our masking scheme on grid-world problems with binary observations \rev{and on a robotics task with continuous action and observation spaces}, using feedforward and recurrent policies. Our results show that masking can produce sub-functions with default input parameters that improve sample efficiency on downstream tasks.

---

## 论文详细总结（自动生成）

## 论文核心信息

### 1. 核心问题与研究动机

- **背景**：选项发现（Option Discovery）是强化学习中实现时间抽象（temporally extended actions）的关键手段，而基于神经网络分解（neural network decomposition）的方法为此提供了有前景的途径。
- **核心问题**：神经网络中编码的子函数（sub-functions）数量随网络规模呈**指数级增长**，因此如何从网络中提取对下游任务有用的子函数，本质上是一个**困难的组合搜索问题**，阻碍了选项发现的可扩展性和实用性。

### 2. 方法论

- **核心思想**：将子函数提取这一**组合搜索问题转化为可微优化问题**。具体地，论文证明了从网络中提取子函数等价于对网络**神经元**和**输入**学习掩码（mask）的过程。
  - **神经元掩码（Neuron masks）**：决定执行哪些子函数。
  - **输入掩码（Input masks）**：决定如何调用子函数，即学习子函数的**默认输入参数**。
- **技术细节**：通过掩码机制，模型可以在训练过程中以端到端、可微的方式自动发现有用的子函数及其默认参数，从而规避了显式枚举子函数组合的指数复杂度。

### 3. 实验设计

- **场景与基准（Benchmark）**：
  - **网格世界任务（Grid-world）**：使用二值观测（binary observations）。
  - **机器人任务（Robotics task）**：使用连续动作和观测空间。
- **策略架构**：评价中同时使用了**前馈网络（Feedforward）** 与**循环网络（Recurrent）** 策略。
- **对比方法**：文中未明确列出具体的基线算法对比清单，主要聚焦于验证掩码机制自身能否有效发现可复用选项。

### 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量及训练时长等算力信息。
- 该论文在元数据中未包含计算资源相关的声明，读者无法据此评估实验的计算成本与可重复性。

### 5. 实验数量与充分性

- **实验组数**：总体实验规模较小，主要覆盖两个任务场景（网格世界与机器人任务）和两种策略架构（前馈与循环）。
- **充分性评估**：
  - **不充分**：缺乏大规模基准测试、跨领域任务验证及与多种基线的系统性对比。
  - **消融实验**：文中未明确提及对掩码机制各组件（如神经元掩码 vs. 输入掩码）的独立消融分析。
  - **客观性说明**：该论文为 ICLR-2026 被拒稿件（Rejected），审稿人可能对实验覆盖度或对比公平性存在疑虑，因此结论的稳健性有待更强证据支撑。

### 6. 主要结论

- 掩码方案能够成功学习出**包含默认输入参数的子函数**，这些子函数在**下游任务上可有效复用**，从而提升了样本效率（sample efficiency）。
- 该工作为强化学习中的时间抽象发现提供了**可微化的新思路**，显著降低了组合搜索的复杂度。

### 7. 优点

- **问题转化巧妙**：将棘手的组合搜索问题转化为可微优化，具备优雅性与理论简洁性。
- **方法通用性**：同时支持二值观测（网格世界）与连续观测/动作（机器人任务），且兼容前馈与循环策略，说明方法具有一定泛化潜力。
- **实用价值**：学习默认输入参数的设计能够提升子函数的即插即用性，对下游任务学习有实际增益。

### 8. 不足与局限

- **实验覆盖有限**：仅两个任务场景，缺乏更具挑战性或更复杂的连续控制基准，难以验证方法在更大规模问题上的扩展性。
- **缺乏方法对比**：未与已有的选项发现方法（如基于互信息、谱聚类等）进行系统性比较，无法判定其相对优势。
- **算力信息缺失**：未报告任何计算资源信息，影响实验的可重复性评估。
- **论文被拒**：作为 ICLR-2026 被拒稿件，暗示研究在理论深度、实验结果或写作呈现上可能尚存明显不足，读者需谨慎看待其结论的普适性。

（完）
