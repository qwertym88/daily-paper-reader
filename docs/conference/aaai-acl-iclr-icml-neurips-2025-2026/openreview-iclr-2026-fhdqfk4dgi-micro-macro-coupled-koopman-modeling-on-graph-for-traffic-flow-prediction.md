---
title: Micro-Macro Coupled Koopman Modeling on Graph for Traffic Flow Prediction
title_zh: 用于交通流预测的图上微观-宏观耦合Koopman建模
authors: "Bairan Xiang, Chenguang Zhao, Huan Yu"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=fhDqFk4DgI"
tags: ["query:koopman-rl"]
score: 7.0
evidence: 非线性多尺度动力学的Koopman建模
tldr: 交通系统具有微观车辆交互与宏观流量非线性共演的多尺度特性，单一微观或宏观模型各有局限。本文提出微观-宏观耦合Koopman建模（MMCKM），将耦合动力学提升到高维线性观测空间统一表示，采用车辆中心动态图在图上离散PDE以兼顾微观扰动与宏观守恒律，并用意图驱动的自适应Koopman演化器进行预测。结果表明该方法提升了交通流预测精度，展示了Koopman建模处理多尺度动力学的能力。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 交通系统微观交互与宏观流量非线性共演，单一尺度模型存在局限。
method: 提出MMCKM，将耦合动力学提升到高维线性观测空间，在车辆中心动态图上离散PDE并使用自适应Koopman演化器。
result: 兼顾微观扰动与宏观守恒律，提升交通流预测精度。
conclusion: 展示了Koopman建模处理多尺度非线性动力学的能力。
---

## Abstract
Traffic systems are inherently multi-scale: microscopic vehicle interactions and macroscopic flow co-evolve nonlinearly. Microscopic models capture local interactions but miss flow evolution; macroscopic models enforce aggregated consistency yet overlook stochastic vehicle-level dynamics. We propose Micro–Macro Coupled Koopman Modeling (MMCKM), which lifts the coupled dynamics to a high-dimensional linear observation space for a unified linear-operator representation. Unlike grid-based discretizations, MMCKM adopts a vehicle-centric dynamic graph that preserves microscopic perturbations while respecting macroscopic conservation laws by discretizing   PDEs onto this graph. At the micro scale, scenario-adaptive Koopman evolvers selected by an Intent Discriminator are designed to model vehicle dynamics. A Koopman control module explicitly formulate how flow state influences individual vehicles, yielding bidirectional couplings. To our knowledge, this is the first work to jointly model vehicle trajectories and traffic flow density using a unified Koopman framework without requiring   historical trajectories. The proposed MMCKM is validated for trajectory prediction on NGSIM and HighD. While MMCKM uses only real-time measurement, it achieves comparable or even higher accuracy than history-dependent baselines.  We further analyze the effect of the operator interval and provide ablations to show the improvement by intent inference, macro-to-micro control, and diffusion. Code and implementation details are included to facilitate reproducibility.

---

## 论文详细总结（自动生成）

> 说明：提供的 PDF 提取内容实际为 OpenReview 的浏览器验证页面，未包含论文正文；以下总结主要依据论文标题、摘要与元数据（ICLR-2026-Accepted，score 7.0）整理，涉及公式、实验细节和算力的部分无法从正文核验。

## 1. 核心问题与整体含义

- **研究动机**：交通系统本质上是多尺度系统，微观车辆交互与宏观交通流非线性共演。
- **现有局限**：
  - 微观模型能刻画局部车辆交互，但难以描述整体流演化；
  - 宏观模型能保证聚合一致性，但忽略车辆级随机动力学。
- **整体含义**：论文试图在一个统一的 Koopman 框架中联合建模车辆轨迹与交通流密度，兼顾微观扰动与宏观守恒律，并避免依赖历史轨迹，仅用实时测量进行预测。

## 2. 方法论：MMCKM

- **核心思想**：提出 **Micro–Macro Coupled Koopman Modeling（MMCKM）**，将微观-宏观耦合动力学提升到高维线性观测空间，用统一线性算子表示复杂非线性演化。
- **关键设计**：
  - **车辆中心动态图**：不同于网格离散，MMCKM 在车辆中心动态图上离散 PDE，以保留微观扰动，同时满足宏观守恒律。
  - **微观尺度**：设计场景自适应 Koopman 演化器，由 **Intent Discriminator** 选择，用于建模车辆动力学。
  - **宏观到微观控制**：设置 Koopman 控制模块，显式刻画交通流状态如何影响个体车辆。
  - **双向耦合**：微观车辆行为与宏观流状态相互影响，形成双向耦合建模。
- **算法流程（文字描述）**：
  1. 将微观车辆交互与宏观流量耦合动力学映射到高维线性观测空间；
  2. 构建车辆中心动态图，并在图上离散 PDE；
  3. 通过意图判别器选择场景自适应的微观 Koopman 演化器；
  4. 利用 Koopman 控制模块注入宏观流状态对个体车辆的影响；
  5. 在统一线性算子框架下进行交通流/轨迹预测。
- **重要特点**：据摘要称，这是首个无需历史轨迹、联合建模车辆轨迹与交通流密度的统一 Koopman 框架。

## 3. 实验设计

- **数据集 / 场景**：
  - **NGSIM**
  - **HighD**
  - 任务为轨迹预测。
- **Benchmark / 对比方法**：
  - 对比 **history-dependent baselines**，即依赖历史轨迹的基线方法。
  - 摘要未列出具体基线名称与实现细节。
- **消融与分析**：
  - 分析 **operator interval** 的影响；
  - 消融 **intent inference**；
  - 消融 **macro-to-micro control**；
  - 消融 **diffusion**。
- **评价重点**：MMCKM 仅使用实时测量，却达到与历史依赖基线相当甚至更高的精度。

## 4. 资源与算力

- 提供的摘要与元数据中 **未提及 GPU 型号、数量、训练时长、显存或计算资源**。
- 因此无法判断该工作的算力需求与可复现成本。
- 摘要仅提到“Code and implementation details are included to facilitate reproducibility”，但未说明具体硬件环境。

## 5. 实验数量与充分性

- **大致实验组数**：
  - 两个数据集：NGSIM、HighD；
  - 至少包含针对 intent inference、macro-to-micro control、diffusion 的消融实验；
  - 还包含 operator interval 影响分析。
- **充分性判断**：
  - 从摘要看，实验覆盖了主要模块消融和关键超参数分析，方向较完整；
  - 但无法确认是否包含多随机种子、统计显著性检验、不同预测时域、不同交通密度场景等；
  - 对比方法仅笼统称为 history-dependent baselines，公平性与调参充分性无法核验；
  - 由于正文不可得，无法判断实验是否客观、公平、可复现。

## 6. 主要结论与发现

- MMCKM 能够在统一 Koopman 框架下联合建模车辆轨迹与交通流密度。
- 车辆中心动态图上的 PDE 离散有助于同时保留微观扰动和宏观守恒律。
- 意图驱动的自适应 Koopman 演化器、宏观到微观控制以及双向耦合对性能有提升。
- 仅使用实时测量的 MMCKM，在 NGSIM 和 HighD 上达到与历史依赖基线相当或更高的轨迹预测精度。
- 结果展示了 Koopman 建模处理多尺度非线性动力学的能力。

## 7. 优点

- **统一框架**：将微观车辆动力学与宏观交通流提升到同一高维线性观测空间，思路新颖。
- **多尺度耦合**：显式建模宏观流对微观车辆的控制影响，形成双向耦合。
- **车辆中心图离散**：相比网格离散，更贴合车辆交互结构，有利于保留微观扰动。
- **场景自适应**：通过 Intent Discriminator 选择 Koopman 演化器，增强对不同驾驶意图/场景的适应能力。
- **无需历史轨迹**：仅依赖实时测量即可预测，降低对历史数据依赖，具有实际部署潜力。
- **可复现性承诺**：摘要提到包含代码和实现细节。

## 8. 不足与局限

- **正文不可得**：当前材料仅为验证页面与摘要，无法核验公式、算法细节、实验设置和结论可靠性。
- **实验覆盖有限**：仅 NGSIM 和 HighD，均为高速公路轨迹数据集，未覆盖城市道路、信号交叉口、混合交通等更复杂场景。
- **基线信息不足**：未列出具体对比方法、超参搜索和公平性控制，难以判断优势是否稳健。
- **算力未报告**：缺少 GPU 型号、数量、训练时长等信息，影响复现与成本评估。
- **依赖模块风险**：Intent Discriminator 的准确性、PDE 在图上的离散误差、实时测量噪声与缺失可能影响性能。
- **理论保证有限**：摘要未说明 Koopman 提升后的线性表示误差界、稳定性或泛化理论保证。
- **应用限制**：真实交通中意图不可观测、传感器噪声、通信延迟等问题可能限制部署效果。

（完）
