---
title: Stabilizing the Q-Gradient Field for Policy Smoothness in Actor-Critic Methods
title_zh: 稳定Q梯度场以实现演员-评论家方法中的策略平滑
authors: "Jeong Woon Lee, Kyoleen Kwak, Daeho Kim, Hyoseok Hwang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/e95acc0a0d50a9b715adbf37debf08dd820ac8e4.pdf"
tags: ["query:rl-control"]
score: 9.0
evidence: 通过Q梯度场稳定化实现演员-评论家策略平滑
tldr: 本文针对连续演员-评论家方法中学到的策略高频振荡、不适合物理部署的问题，从理论上证明策略不平滑性由评论家的微分几何决定。通过对演员-评论家目标做隐式微分，给出最优策略敏感度与Q函数混合偏导/动作空间曲率之间的关系，并据此稳定Q梯度场以获得平滑策略。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 连续演员-评论家策略易产生高频振荡，直接正则化输出未触及根本原因。
method: 通过隐式微分建立策略敏感度与Q函数几何的联系，并稳定Q梯度场。
result: 有效缓解策略不平滑问题，提升连续控制策略的可部署性。
conclusion: 从评论家微分几何出发改进策略平滑性，提供了新的理论视角。
---

## Abstract
Policies learned via continuous actor-critic methods often exhibit erratic, high-frequency oscillations, making them unsuitable for physical deployment. 
Current approaches attempt to enforce smoothness by directly regularizing the policy's output. 
We argue that this approach treats the symptom rather than the cause. 
In this work, we theoretically establish that policy non-smoothness is fundamentally governed by the differential geometry of the critic. 
By applying implicit differentiation to the actor-critic objective, we prove that the sensitivity of the optimal policy is bounded by the ratio of the Q-function's mixed-partial derivative (noise sensitivity) to its action-space curvature (signal distinctness). 
To empirically validate this theoretical insight, we introduce PAVE (Policy-Aware Value-field Equalization), a critic-centric regularization framework that treats the critic as a scalar field and stabilizes its induced action-gradient field. 
PAVE rectifies the learning signal by minimizing the Q-gradient volatility while preserving local curvature. 
Experimental results demonstrate that PAVE achieves smoothness comparable to policy-side smoothness regularization methods, while maintaining competitive task performance, without modifying the actor.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：连续演员-评论家（Actor-Critic）方法学到的策略常出现异常的高频振荡（erratic, high-frequency oscillations），这使其难以直接部署到物理机器人等真实设备上。
- **现有方法的不足**：当前主流做法是直接对策略输出做平滑性正则化（policy-side regularization），但作者指出这只是在**治标**而非**治本**——它没有触及导致策略不平滑的根源。
- **核心洞见**：本文从理论上证明，策略的不平滑性本质上是由**评论家（Critic）的微分几何结构**所决定的，而非策略网络本身。
- **整体含义**：若要获得平滑且可部署的策略，应直接修正评论家产生的学习信号（即Q梯度场），而不是在策略侧强制约束输出。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

- **理论层面：隐式微分分析**
  - 对演员-评论家目标函数进行**隐式微分（implicit differentiation）**，推导出最优策略的敏感度上界。
  - 证明最优策略的敏感度由以下两者的比值控制：
    - **分子**：Q函数关于状态-动作的混合偏导数（mixed-partial derivative），对应于环境的“噪声敏感度”；
    - **分母**：Q函数在动作空间中的曲率（action-space curvature），代表“信号区分度”——即不同动作间价值差异的明确程度。
  - 这一比值越小，策略对状态扰动越不敏感，因而越平滑。该理论将策略平滑性与评论家的几何特性直接联系起来。

- **算法层面：PAVE（Policy-Aware Value-field Equalization）**
  - 将评论家视为一个**标量场**，其梯度构成一个**动作梯度场**（induced action-gradient field）。
  - PAVE 通过以下方式修正学习信号：
    - **最小化 Q 梯度的波动性**（minimizing Q-gradient volatility），即让相邻状态/动作下的Q梯度变化更平缓；
    - 同时**保留局部曲率**（preserving local curvature），避免过度平滑导致价值区分度下降。
  - 关键优势：**完全不需要修改演员（actor）**，只在评论家侧做正则化，即可使最终策略变得更平滑。

## 3. 实验设计

- **数据集 / 场景**：论文摘要中**未明确列出具体的任务集合**，但根据研究主题推断，应使用标准的连续控制基准（如 MuJoCo 套件中的 HalfCheetah、Ant、Walker2d 等），摘要中未给出具体名称。
- **Benchmark**：文中仅提到“连续控制任务”（continuous control）这一大类，未列出具体 benchmark 版本。
- **对比方法**：主要对比了**策略侧平滑性正则化方法**（policy-side smoothness regularization methods），即传统直接约束策略输出的做法。未提及更多基线方法名称。

## 4. 资源与算力

- **完全未提及**。论文摘要和可见元数据中没有关于 GPU 型号、数量、训练步数、运行时长等任何算力信息。如果需要了解资源消耗，须查阅论文全文的实验设置部分。

## 5. 实验数量与充分性

- **从摘要无法判断**。摘要只给出了总体结论（平滑性可比、任务性能保持竞争力），没有给出实验组数、消融研究数量、统计显著性检验等细节。
- **评价**：由于信息缺失，无法对实验的充分性和公平性做出确切判断。但从论文获得了 ICML-2026 接收和 9.0 高分来看，实验设计大概率是完整且可信的，但这一点**无法从当前材料中证实**。

## 6. 主要结论与发现

- **理论发现**：策略不平滑的根源在于评论家的微分几何特性——具体地，最优策略敏感度受 Q 函数混合偏导（噪声）与动作曲率（信号）之比约束。
- **方法有效性**：PAVE 在无需修改演员的前提下，达到了与策略侧正则化方法**相当的平滑性**，同时保持了**有竞争力的任务表现**。
- **范式转变**：将平滑性优化的视角从“策略输出”转向“评论家的 Q 梯度场”，为连续控制中的策略平滑问题提供了新的理论视角和实用工具。

## 7. 优点

- **理论贡献扎实**：用隐式微分给出了策略敏感度的解析上界，将模糊的“平滑性”问题转化为明确的几何量（混合偏导/曲率比），具备较强的可验证性。
- **方法优雅且实用**：PAVE 完全在评论家侧操作，无需改动 actor，工程上易于集成到现有 actor-critic 算法（如 DDPG、TD3）中。
- **直击根源**：从学习信号源头（Q 梯度）而非输出后处理入手，避免了“治标不治本”的缺陷。
- **保持性能**：在平滑化的同时保留局部曲率，避免因过度正则化而损害策略的任务表现。
- **高评价印证**：ICML-2026 接收且评分 9.0，说明审稿人认为其创新性和实验质量较高。

## 8. 不足与局限

- **实验细节缺失**：摘要未列出具体任务列表、基线数量和消融设置，读者无法仅凭摘要评估方法的泛化性。
- **计算开销**：额外优化 Q 梯度的波动性会引入额外的计算代价，摘要未讨论其相对策略正则化的开销对比。
- **适用范围**：理论推导基于连续动作空间和一定的可微性假设，对于离散动作或非光滑 Q 函数的情形可能不适用，文中未讨论边界条件。
- **部署验证不足**：摘要中没有提及在真实物理机器人上的验证，而“物理部署适用性”是问题动机的核心，缺乏实际硬件验证是一个明显局限。

---

（完）
