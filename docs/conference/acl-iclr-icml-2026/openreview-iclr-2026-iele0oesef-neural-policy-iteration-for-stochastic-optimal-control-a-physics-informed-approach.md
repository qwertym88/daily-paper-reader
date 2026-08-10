---
title: "Neural Policy Iteration for Stochastic Optimal Control: A Physics-Informed Approach"
title_zh: 随机最优控制的神经策略迭代：一种物理信息方法
authors: "Yeongjong Kim, Yeoneung Kim, Minseok Kim, Namkyeong Cho"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=iElE0OESEf"
tags: ["query:rl-control"]
score: 9.0
evidence: 面向随机最优控制的物理信息策略迭代，基于HJB方程
tldr: 随机最优控制问题常由二阶Hamilton-Jacobi-Bellman方程描述，现有确定性PINN方法难以直接推广。论文提出PINN-PI框架：在每次迭代中训练神经网络近似值函数，并利用固定策略下线性PDE残差实现系统性的L2误差控制。进一步推导了值函数梯度误差对策略更新传播的Lipschitz型界，从而在训练中可评估策略质量。该方法为随机最优控制中的策略迭代提供了可解释的数值求解途径。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 随机最优控制问题求解困难，需可解释且误差可控的数值策略迭代方法。
method: 将策略评估步骤转化为线性PDE，用物理信息神经网络近似值函数并控制L2误差。
result: 导出值函数误差传播的理论界，提升训练可解释性与策略质量评估。
conclusion: 为随机最优控制提供了基于PINN的可靠策略迭代框架。
---

## Abstract
We propose a physics-informed neural network policy iteration (PINN-PI) framework for solving stochastic optimal control problems governed by second-order Hamilton--Jacobi--Bellman (HJB) equations. At each iteration, a neural network is trained to approximate the value function by minimizing the residual of a linear PDE induced by a fixed policy. This linear structure enables systematic $L^2$ error control at each policy evaluation step, and allows us to derive explicit Lipschitz-type bounds that quantify how value gradient errors propagate to the policy updates. This interpretability provides a theoretical basis for evaluating the quality of policy during training. Our method extends recent deterministic PINN-based approaches to stochastic settings, inheriting the global exponential convergence guarantees of classical policy iteration under mild conditions. We demonstrate the effectiveness of our method on several benchmark problems, including stochastic cartpole, pendulum problems and high-dimensional linear quadratic regulation (LQR) problems in up to 10D.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义

- **研究动机**：随机最优控制问题广泛存在于机器人、金融、工程等领域，其核心难点在于求解二阶 Hamilton–Jacobi–Bellman（HJB）方程。传统数值方法受维数灾难和问题非线性限制，而现有的物理信息神经网络（PINN）方法多面向确定性系统，难以直接推广到随机情形。
- **整体含义**：论文试图构建一个兼具理论可解释性与数值可靠性的神经网络策略迭代框架，使得随机最优控制问题可以在高维场景下被高效求解，并保证迭代过程的误差可控与收敛性。

## 2. 方法论

- **核心思想**：将经典策略迭代（Policy Iteration, PI）与物理信息神经网络结合，提出 **PINN-PI** 框架。
- **关键步骤**：
  1. 在每次迭代中，固定当前策略，将 HJB 方程转化为关于值函数的**线性偏微分方程**；
  2. 使用神经网络近似值函数，通过最小化线性 PDE 残差进行训练；
  3. 利用线性结构实现对每次策略评估步骤的 **L² 误差控制**；
  4. 推导值函数梯度误差向策略更新传播的 **Lipschitz 型显式界**，从而在训练过程中量化策略质量。
- **理论保证**：在温和条件下，该方法继承了经典策略迭代的全局指数收敛性质，并扩展了近期确定性 PINN 方法到随机环境。

## 3. 实验设计

- **基准场景**：
  - 随机 cartpole（小车倒立摆）
  - 随机 pendulum（摆锤）问题
  - 高维线性二次调节（LQR）问题，维度最高至 **10D**
- **数据与对比**：摘要未提及具体数据集来源，也未明确列出对比的基线方法（如传统 PINN、数值求解器、其他强化学习算法等），因此外部对比信息不详。

## 4. 资源与算力

- 论文摘要与元数据中**未说明** GPU 型号、数量、训练时长或任何计算资源细节。
- 仅可推断实验涉及神经网络训练，但具体算力需求未知。

## 5. 实验数量与充分性

- **实验数量**：从摘要看，至少包含 3 类基准问题（cartpole、pendulum、10D LQR）。但未提供具体实验组数、消融实验或参数敏感性分析。
- **充分性评价**：
  - 场景覆盖**从低维非线性控制到高维线性控制**，有一定代表性；
  - 但缺少与现有方法的定量对比、消融实验（如误差界有效性验证、网络结构影响等），因此**实验充分性和公平性证据不足**，暂不能完全确认方法在不同条件下的稳健性。

## 6. 主要结论与发现

- 提出的 PINN-PI 框架能够为随机最优控制提供**可解释、误差可控**的策略迭代求解途径。
- 理论分析了值函数误差对策略更新的影响，为训练中评估策略质量提供了依据。
- 实验表明方法在多个随机控制 benchmark 以及高维 LQR 问题上有效。

## 7. 优点

- **理论性强**：将策略评估转化为线性 PDE，从而获得 L² 误差控制与 Lipschitz 传播界，这比通常纯黑箱的神经网络方法更具可解释性。
- **扩展性**：将确定性 PINN 策略迭代推广到随机 HJB 方程场景，且保持经典策略迭代的指数收敛性质。
- **高维能力**：成功应用于 10 维 LQR 问题，展示了对维数灾难的一定缓解。

## 8. 不足与局限

- **实验细节匮乏**：缺少对数据集、对比方法、超参数、网络结构、训练时间等具体描述，难以复现或评判。
- **验证范围有限**：仅商业基准（cartpole、pendulum、LQR），未涉及更复杂的随机非线性系统或实际控制任务。
- **误差界的实用性**：Lipschitz 界虽然在理论上提供了策略质量评估，但未展示其在训练中如何具体计算或使用，可能依赖不易估计的常数。
- **算力信息缺失**：未报告计算资源，无法判断部署成本或扩展至更高维（如 50D、100D）的可行性。
- **公平性风险**：由于没有与主流基线（如深度强化学习、传统有限差分、其他 PINN 变体）的显式对比，难以确认实际性能优势。

（完）
