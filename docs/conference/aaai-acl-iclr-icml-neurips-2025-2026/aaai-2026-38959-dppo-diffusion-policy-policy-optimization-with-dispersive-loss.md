---
title: "D²PPO: Diffusion Policy Policy Optimization with Dispersive Loss"
title_zh: D²PPO：带分散损失的扩散策略策略优化
authors: "Guowei Zou, Weibing Li, Hejun Wu, Yukun Qian, Yuhang Wang, Haitao Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38959/42921"
tags: ["query:rl-control"]
score: 4.0
evidence: 面向机器人操作带正则的策略优化
tldr: 扩散策略擅长机器人操作中的多模态动作建模，但存在表示坍缩问题，语义相似的观测被映射为难以区分的特征，影响对细微关键变化的处理。本文提出D²PPO，引入分散损失正则化，将批次内所有隐表示视为负对，迫使网络学习判别性表示，并结合策略优化进行训练。结果表明该方法提升了复杂操作任务的表现，缓解了扩散策略的表示坍缩问题。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 890, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1819, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1826, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 790, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1831, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1792, \"height\": 847, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38959/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 689, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38959/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1705, \"height\": 496, \"label\": \"Table\"}]"
motivation: 扩散策略在机器人操作中存在表示坍缩，相似观测被映射为不可区分的特征。
method: 提出D²PPO，引入分散损失正则化，将批次内所有隐表示视为负对以学习判别性表示。
result: 缓解表示坍缩并提升复杂机器人操作任务性能。
conclusion: 为扩散策略结合策略优化提供正则化改进思路。
---

## Abstract
Diffusion policies excel at robotic manipulation by naturally modeling multimodal action distributions in high-dimensional spaces. Nevertheless, diffusion policies suffer from diffusion representation collapse: semantically similar observations are mapped to indistinguishable features, ultimately impairing their ability to handle subtle but critical variations required for complex robotic manipulation. To address this problem, we propose D²PPO (Diffusion Policy Policy Optimization with Dispersive Loss). D²PPO introduces dispersive loss regularization that combats representation collapse by treating all hidden representations within each batch as negative pairs. D²PPO compels the network to learn discriminative representations of similar observations, thereby enabling the policy to identify subtle yet crucial differences necessary for precise manipulation. In evaluation, we find that early-layer regularization benefits simple tasks, while late-layer regularization sharply enhances performance on complex manipulation tasks. On RoboMimic benchmarks, D²PPO achieves an average improvement of 22.7% in pre-training and 26.1% after fine-tuning, setting new SOTA results. In comparison with SOTA, the results of real-world experiments on a Franka Emika Panda robot show the excitingly high success rate of our method. The superiority of our method is especially evident in complex tasks.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
面向机器人操作带正则的策略优化。

### 2. 核心内容
扩散策略擅长机器人操作中的多模态动作建模，但存在表示坍缩问题，语义相似的观测被映射为难以区分的特征，影响对细微关键变化的处理。本文提出D²PPO，引入分散损失正则化，将批次内所有隐表示视为负对，迫使网络学习判别性表示，并结合策略优化进行训练。结果表明该方法提升了复杂操作任务的表现，缓解了扩散策略的表示坍缩问题。

### 3. 对应检索需求
Papers central to 面向动力学与控制理论与强化学习结合的技术栈拓展，涵盖硬约束RL、嵌入式可微优化、数值凸优化与概率决策。, especially work that connects or combines: optimal control theory and dynamic programming; reinforcement learning policy optimization and value functions; actor-critic algorithm architecture and training; constrained reinforcement learning with hard safety constraints; convex optimization problems and solvers; probabilistic decision making under uncertainty; How to integrate optimal control theory with reinforcement learning for robotic control; methods for enforcing hard constraints in reinforcement learning policy optimization; differentiable optimization as a layer inside neural network control policies; applying convex optimization and numerical methods to reinforcement learning.

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38959](https://ojs.aaai.org/index.php/AAAI/article/view/38959)
