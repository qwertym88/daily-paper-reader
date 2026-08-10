---
title: "Differentiable Weightless Controllers: Learning Logic Circuits for Continuous Control"
title_zh: 可微无权重控制器：学习连续控制的逻辑电路
authors: "Fabian Kresse, Christoph H. Lampert"
date: 2026-04-30
pdf: "https://openreview.net/pdf/65cbfd4d6a15fbd3f3946a03b2b02b0f53302371.pdf"
tags: ["query:hum-ctrl"]
score: 5.0
evidence: 在MuJoCo中基于强化学习进行连续控制并涉及人形机器人基准，为机器人运动提供高效控制器。
tldr: 面向需要低延迟、低能耗的真实世界控制，本文提出可微无权重控制器(DWC)：一种符号可微架构，既能端到端梯度训练，又能直接编译为FPGA兼容的逻辑电路，实现每动作单周期延迟和纳焦级能耗。在包含高维Humanoid的五个MuJoCo任务上，DWC达到与深度网络相当的回报。这项工作为受限环境下的机器人运动控制提供了高效的新选择。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 真实世界控制要求低延迟和低能耗，与高精度深度神经网络控制器的需求相矛盾。
method: 提出可微无权重控制器(DWC)，一种符号可微架构，可端到端训练并编译为FPGA兼容电路，实现极低延迟和纳焦级能耗。
result: 在五个MuJoCo基准(包括高维Humanoid)上，DWC达到与深度网络相当的回报，同时大幅降低延迟和能耗。
conclusion: 该工作为连续控制提供了高效紧凑的控制器，适合实时受限的机器人应用。
---

## Abstract
Controlling autonomous systems under real-world conditions often requires policies that can be evaluated with low latency and minimal energy consumption. Unfortunately, these conditions are at odds with the use of high-precision deep neural networks as controllers. In this work, we introduce Differentiable Weightless Controllers (DWCs), a symbolic-differentiable architecture that learns flexible, non-linear, yet highly efficient control policies. DWCs can be trained end-to-end via gradient-based techniques, yet compile directly into FPGA-compatible circuits with few- or even single-clock-cycle latency and nanojoule-level energy cost per action. Across five MuJoCo benchmarks, including high-dimensional Humanoid, DWCs achieve returns competitive with standard deep policies (full-precision or quantized neural networks). Furthermore, DWCs exhibit structurally sparse and interpretable connectivity patterns, enabling direct inspection of which input values influence control decisions.

---

## 论文详细总结（自动生成）

# 论文总结：可微无权重控制器：学习连续控制的逻辑电路

## 1. 核心问题与整体含义（研究动机与背景）

真实世界中的自主系统（如机器人）在运行时常面临严格的延迟和能耗约束，尤其是在边缘计算或嵌入式设备上。然而，当前作为主流控制策略的高精度深度神经网络（DNN）往往计算开销大、推理延迟高、能量消耗高，难以满足实时控制的需求。这一矛盾构成了本论文的核心研究动机。

作者提出了一种名为**可微无权重控制器（Differentiable Weightless Controllers, DWCs）** 的新型架构，旨在同时兼顾两个看似冲突的目标：
- **可学习性与灵活性**：能够通过梯度方法端到端训练，学习复杂的非线性控制策略。
- **硬件高效性**：可直接编译为 FPGA 兼容的逻辑电路，实现极低延迟（每动作可低至单时钟周期）和纳焦级能耗。

整体含义：这项工作为受资源约束的机器人运动控制提供了一种既能保持学习能力又具备硬件友好性的新选择，探索了“符号可微架构 + 硬件编译”这一独特路线。

## 2. 方法论：核心思想、关键技术细节

**核心思想**：利用“无权重”的符号逻辑电路（而非数值权重矩阵）来表示控制策略。传统的神经网络依赖大量浮点乘加运算，而 DWC 通过逻辑门电路实现输入与输出之间的映射，可以在不损失表达能力的前提下大幅降低计算成本。关键在于，该架构是**可微的**，因此可以通过标准的反向传播与强化学习流程进行端到端训练，训练完成后可直接转换为硬件逻辑电路。

**关键技术细节**（根据摘要和元数据推断）：
- **训练方式**：使用基于梯度的端到端训练方法（结合强化学习，环境为 MuJoCo）。
- **硬件编译能力**：训练好的策略可直接编译为 FPGA 兼容电路；电路中每个动作的执行仅为几个或单个时钟周期，能量消耗为纳焦级别。
- **结构特性**：DWC 的策略结构是稀疏且可解释的，具有结构化的连接模式，可以直接观察哪些输入值影响控制决策——这显著优于深度神经网络的“黑箱”特性。
- **灵活性**：能够学习非线性的控制策略，并非线性无关的简单模型。

注：摘要中未提供具体的数学公式或算法伪代码，但从概念上可将其理解为一种“可微逻辑门网络”，类似于可微的二值化/符号化网络结构。

## 3. 实验设计：数据集、基准与方法对比

- **基准场景**：使用 MuJoCo 物理仿真环境，共包含 5 个连续控制任务，其中包含高维的 **Humanoid（人形机器人）** 基准，以及其他四个控制任务（推测为经典的 MuJoCo 连续控制任务）。
- **任务性质**：强化学习（RL）环境下的连续控制，目标为最大化累积回报。
- **对比方法**：
  - 标准深度神经网络策略（full-precision，全精度网络）
  - 量化神经网络策略（quantized neural networks，低精度网络）
  - DWC（本方法）

## 4. 资源与算力

论文提供的摘要和元数据中**未明确说明**训练所使用的 GPU 型号、数量、训练时长等算力资源信息。仅从元数据可知实验基于 MuJoCo 环境，并通过强化学习进行训练。若论文全文包含算力细节，通常会在实验设置或附录中说明，但从本次提供的文本片段无法获知。

## 5. 实验数量与充分性

- **实验数量**：
  - 5 个 MuJoCo 连续控制基准任务（含 Humanoid 高维任务）
  - 对比了三类方法：全精度深度网络、量化网络、DWC
- **充分性评估**：
  - ✅ 任务多样性尚可：连续控制任务从低维到高维（Humanoid）均有覆盖。
  - ✅ 对比对象合理：不仅有标准全精度网络，还对比了量化网络，体现出 DWC 与硬件友好型替代方案的相对优势。
  - ⚠️ 局限性：从摘要中**未看到消融实验的信息**（例如逻辑门数量、输入维度的影响、训练超参数敏感性等）；也未见对真实硬件部署（FPGA 实测延迟和功耗）的实验验证，摘要仅报告了理论层面的“纳焦级能耗”和“单时钟周期延迟”。
  - ⚠️ 关于公平性：摘要未提供不同方法之间的参数量、训练预算、运行时间等对齐信息，因此难以完全判断对比是否公平。

## 6. 主要结论与发现

- DWC 在五个 MuJoCo 基准任务（包括高维 Humanoid）上，取得了与标准深度策略（全精度或量化网络）**相当的回报**。
- DWC 在设计上大幅降低了推理延迟和能耗（纳焦级/动作，单时钟周期），优于深度神经网络。
- DWC 的结构稀疏且可解释，可直接检查哪些输入特征影响控制决策，有利于可信控制和安全分析。
- 整体结论：DWC 为连续控制提供了一种高效、紧凑、硬件友好的控制器，特别适合实时受限的机器人应用场景。

## 7. 优点

- **创新性强**：将逻辑电路与可微训练结合，开辟了“可微符号控制”的新路径，突破了神经网络必须依赖权重矩阵的定式。
- **兼顾学习能力与硬件效率**：既保持了深度学习端到端优化的优势，又实现了深度网络难以企及的极低延迟和能耗。
- **可解释性**：结构稀疏、模式可读，可直接观察输入对决策的影响，这对于机器人等高风险控制场景尤为重要。
- **应用前景明确**：目标场景（低延迟、低功耗实时控制）具体且具有实际工业价值。

## 8. 不足与局限

- **实验覆盖有限**：仅在 MuJoCo 模拟环境中的 5 个任务上验证，尚未涵盖更复杂的真实世界硬件部署（如实际机器人上的 FPGA 部署验证）。
- **缺乏消融实验细节**：摘要层面无法获知 DWC 在逻辑门数量、网络拓扑、输入编码方式等设计维度上的敏感性分析。
- **对比公平性存疑**：未提供与基线网络在参数量、训练样本、训练时间等维度上的对齐说明；能量和延迟对比是基于理论推算还是实测数据，也需进一步核实。
- **规模化问题**：高维状态空间（如 Humanoid 的状态维度可能上百维）下，逻辑电路是否会出现门数量爆炸或可扩展性瓶颈，摘要未作说明。
- **文字信息有限**：本次分析的依据仅为摘要和元数据，缺少完整论文正文中的公式推导、实验细节、硬件实测和失败案例分析。

## （完）
