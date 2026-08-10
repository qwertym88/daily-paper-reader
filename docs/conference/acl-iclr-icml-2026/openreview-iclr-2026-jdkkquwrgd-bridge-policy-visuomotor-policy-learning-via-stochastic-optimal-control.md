---
title: "Bridge Policy: Visuomotor Policy Learning via Stochastic Optimal Control"
title_zh: 桥策略：基于随机最优控制的视觉运动策略学习
authors: "Zhaoyang Liu, Mokai Pan, Zhongyi Wang, Kaizhen Zhu, Haotao Lu, Jingya Wang, Ye Shi"
date: 2025-09-14
pdf: "https://openreview.net/pdf?id=jDkKquWRgd"
tags: ["query:rl-control"]
score: 8.0
evidence: 基于随机最优控制与扩散桥构建视觉运动策略，用于机器人控制。
tldr: 模仿学习中的生成式策略常在正向与反向过程中施加条件，导致流形偏差与估计误差。本文提出BridgePolicy，利用扩散桥公式将观测显式纳入前向过程，其理论基础为随机最优控制。动作从观测分布而非噪声中采样，避免了条件生成带来的偏差。在机器人视觉运动策略学习上，该方法无需条件生成即可提升策略质量。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有生成式模仿策略施加条件导致流形偏差和估计误差，影响机器人视觉运动策略质量。
method: 提出BridgePolicy，基于随机最优控制的扩散桥将观测纳入前向过程，从观测分布采样动作。
result: 避免条件生成带来的偏差，在机器人视觉运动策略学习上提高了策略质量。
conclusion: 为视觉运动策略提供了一种无条件的生成式最优控制方法，降低了模仿学习的偏差。
---

## Abstract
Imitation learning has been widely used in robotic learning, where policies are derived from expert demonstrations. Recent advances leverage generative models, such as diffusion and flow-based methods, to better capture multi-modal action distributions and temporal dependencies. However, these approaches typically impose conditioning during the forward and reverse process, which inevitably introduces manifold deviation and estimation error. In this work, we propose BridgePolicy, a condition-free generative visuomotor policy that explicitly incorporates observations into the forward process through a diffusion bridge formulation grounded in stochastic optimal control. By sampling actions from observation distributions instead of random noise, BridgePolicy reduces stochasticity and achieves more controllable policy behaviors. However, directly bridging observations to actions poses new challenges, as the action distribution may exhibit mismatched data shape, and the robot observations are inherently multi-modal. In contrast, the diffusion bridge can only connect one-to-one distributions with the same shape.  To address the challenges of aligning distributional endpoints and handling multi-modal robot observations, we design a semantic aligner for distribution shape alignment, and a modality fusion module for unifying robot states and visual inputs. Experiments across 52 tasks on 3 benchmarks and 4 real-world tasks demonstrate that BridgePolicy consistently outperforms state-of-the-art generative policies.

---

## 论文详细总结（自动生成）

# 论文总结：Bridge Policy（桥策略）

## 1. 核心问题与整体含义

- **研究背景**：模仿学习是机器人学习中的常用范式，策略从专家示范中学习。近年来，扩散模型和基于流的方法等生成式模型被引入模仿学习，以更好地捕捉多模态动作分布和时间依赖关系。
- **核心问题**：现有生成式模仿策略通常在扩散/流模型的正向过程和反向过程中对观测施加条件（conditioning），这种做法不可避免地引入**流形偏离**（manifold deviation）和**估计误差**（estimation error），进而降低策略质量。
- **整体含义**：如何避免条件生成带来的偏差，构建一种"无条件"（condition-free）的生成式视觉运动策略，是本文要解决的核心问题。

## 2. 方法论

- **核心思想**：提出 **BridgePolicy**，一种无条件的生成式视觉运动策略，通过**扩散桥**（diffusion bridge）公式将观测显式纳入前向过程，其理论基础为**随机最优控制**（stochastic optimal control, SOC）。
- **关键差异**：动作是从**观测分布**中采样，而非从随机噪声中采样，从而降低随机性，使策略行为更可控，并避免条件生成带来的流形偏差。
- **面临挑战与对应技术**：
  - **分布形状不匹配**：扩散桥只能连接同形状的一对一分布，而观测到动作的分布形状可能不一致。→ 设计**语义对齐器**（semantic aligner）进行分布形状对齐。
  - **观测多模态**：机器人观测本质上是多模态的（如视觉、状态信息）。→ 设计**模态融合模块**（modality fusion module）统一机器人状态与视觉输入。

## 3. 实验设计

- **Benchmark 与数据集**：在 **3 个基准** 上的 **52 个任务** 以及 **4 个真实世界任务** 上进行评估。
- **对比方法**：与最先进的生成式策略（state-of-the-art generative policies）进行对比。
- **评估内容**：涵盖模拟环境中的多任务学习以及真实机器人操作任务，验证 BridgePolicy 的泛化能力和实际可用性。

## 4. 资源与算力

- 论文提供的元数据与摘要中**未明确说明**使用的 GPU 型号、数量、训练时长等算力资源信息。
- 仅能确定实验规模较大（52 个模拟任务 + 4 个真实任务），但具体计算成本无法从当前获取的信息中得知。

## 5. 实验数量与充分性

- **实验数量**：实验规模较大，覆盖 52 个模拟任务和 4 个真实世界任务，共 3 个 benchmark，且在多个任务上均显示一致的性能提升。
- **充分性与公平性**：
  - 从摘要看，实验覆盖面较广，涵盖了多基准、多任务和真实世界场景，具备较强的说服力。
  - 但摘要未提供消融实验的细节、基线方法的实现细节、以及统计显著性检验等信息，因此无法完全评估实验的公平性和严谨性。

## 6. 主要结论与发现

- BridgePolicy 在 52 个模拟任务和 4 个真实世界任务上**一致优于**最先进的生成式策略。
- 通过扩散桥将观测纳入前向过程并直接从观测分布采样动作，能够**避免条件生成带来的偏差**，从而提升视觉运动策略的质量与可控性。
- 实验证明该方法在机器人视觉运动策略学习上是有效且可泛化的。

## 7. 优点

- **方法新颖**：将随机最优控制与扩散桥引入视觉运动策略学习，提出无条件的生成式策略范式，理论上避免了条件生成的固有偏差。
- **问题针对性强**：直接针对现有生成式模仿策略的两个核心痛点（流形偏离、估计误差）进行建模突破。
- **技术完整**：针对扩散桥的分布形状限制和机器人观测多模态问题分别设计了语义对齐器与模态融合模块，形成完整解决方案。
- **实验扎实**：大规模多基准验证，涵盖模拟与真实世界，相比已有工作在实验广度上有一定优势。

## 8. 不足与局限

- **算力信息缺失**：未报告训练所需的 GPU 资源、训练时长和计算成本，难以评估方法的实际部署成本。
- **消融实验信息不足**：摘要中未说明语义对齐器和模态融合模块的单独贡献，无法判断各组件的重要性。
- **基准细节不明确**：未指明具体使用了哪些 benchmark（如 RoboMimic、RLBench、MetaWorld 等），也未知各任务的难度分布。
- **可行性与泛化边界**：目前缺乏关于失败案例、任务复杂性上限以及对分布外（OOD）场景泛化能力的讨论。
- **对比方法覆盖面有限**：仅笼统表述为"state-of-the-art generative policies"，未列出具体基线，难以判断性能优势的具体来源。

---

（完）
