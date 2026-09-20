---
title: "MetaKoopman: Bayesian Meta-Learning of Koopman Operators for Modeling Structured Dynamics under Distribution Shifts"
title_zh: MetaKoopman：面向分布偏移下结构化动力学的Koopman算子贝叶斯元学习
authors: "Mahmoud Selim, Sriharsha Bhat, Karl Henrik Johansson"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=BJ3z1hYuKx"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 面向分布偏移下非线性动力学的Koopman算子贝叶斯元学习
tldr: 在分布偏移下建模与预测非线性动力学对鲁棒决策至关重要。本文提出MetaKoopman，一种通过线性潜表示建模非线性动力学的贝叶斯元学习框架。它学习Koopman算子的矩阵正态-逆Wishart先验，可基于近期轨迹段进行闭式贝叶斯更新，并给出未来状态轨迹的闭式后验预测分布。该方法同时捕捉认知与偶然不确定性，在卡车-拖车系统上验证有效。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 分布偏移下建模与预测非线性动力学对鲁棒决策至关重要。
method: 提出MetaKoopman，学习Koopman算子的MNIW先验并做闭式贝叶斯更新与后验预测。
result: 给出未来状态轨迹的闭式后验预测分布，同时捕捉认知与偶然不确定性。
conclusion: 为分布偏移下的动力学建模与鲁棒决策提供了不确定性感知的Koopman框架。
---

## Abstract
Modeling and forecasting nonlinear dynamics under distribution shifts is essential for robust decision-making in real-world systems. In this work, we propose **MetaKoopman**, a Bayesian meta-learning framework for modeling nonlinear dynamics through linear latent representations. MetaKoopman learns a Matrix Normal-Inverse Wishart (*MNIW*) prior over the Koopman operator, enabling closed-form Bayesian updates conditioned on recent trajectory segments. Moreover, it provides a closed-form posterior predictive distribution over future state trajectories, capturing both epistemic and aleatoric uncertainty in the learned dynamics. We evaluate MetaKoopman on a full-scale autonomous truck and trailer system across a wide range of adverse winter scenarios—including snow, ice, and mixed-friction conditions—as well as in simulated control tasks with diverse distribution shifts. MetaKoopman consistently outperforms prior approaches in multi-step prediction accuracy, uncertainty calibration and robustness to distributional shifts. Field experiments further demonstrate its effectiveness in dynamically feasible motion planning, particularly during evasive maneuvers and operation at the limits of traction. Project website: [https://mahmoud-selim.github.io/MetaKoopman/](https://mahmoud-selim.github.io/MetaKoopman/)

---

## 论文详细总结（自动生成）

# MetaKoopman 论文总结

> 说明：提供的 PDF 提取文本实际为 OpenReview 验证页面，未包含论文正文。以下总结主要依据同批给出的标题、摘要与元数据；凡正文中可能涉及但当前材料未明确说明的内容，均标注为“未说明/无法确认”。

## 1. 核心问题与整体含义
- **研究动机**：在真实系统中，非线性动力学常因环境、摩擦条件、负载或任务变化而发生分布偏移，导致模型预测和决策鲁棒性下降。
- **核心问题**：如何在分布偏移下建模和预测非线性动力学，并为鲁棒决策提供不确定性感知的预测。
- **整体含义**：论文提出 **MetaKoopman**，将 Koopman 算子方法与贝叶斯元学习结合，用线性潜表示刻画非线性动力学，并学习可快速适应新条件的先验。
- **应用背景**：面向安全关键系统，尤其是全尺寸自动驾驶卡车-拖车系统在雪、冰、混合摩擦等恶劣冬季场景下的运动规划与控制。

## 2. 方法论
### 核心思想
- 通过 **Koopman 算子** 将非线性动力学提升到线性潜空间，从而利用线性系统工具进行多步预测与控制。
- 使用 **贝叶斯元学习** 学习 Koopman 算子的 **Matrix Normal-Inverse Wishart（MNIW）先验**，使模型能够在分布偏移下根据近期轨迹快速适应。
- 预测不仅给出未来状态轨迹的点估计，还给出 **闭式后验预测分布**，同时捕捉 **认知不确定性** 与 **偶然不确定性**。

### 关键技术细节
- **MNIW 先验**：在 Koopman 算子上设置矩阵正态-逆 Wishart 先验，为元学习提供共轭贝叶斯结构。
- **闭式贝叶斯更新**：以近期轨迹段为条件，对 Koopman 算子后验进行闭式更新，无需数值采样或复杂优化。
- **闭式后验预测**：对未来状态轨迹给出闭式后验预测分布，可直接用于不确定性量化和鲁棒规划。
- **线性潜表示**：用线性潜动态表示非线性动力学，兼顾表达能力和可计算性。
- **不确定性类型**：摘要明确强调同时捕捉 epistemic uncertainty（认知不确定性）和 aleatoric uncertainty（偶然不确定性）。

### 算法流程（文字描述）
1. **元训练阶段**：从多个任务/多个分布偏移下的轨迹中学习 Koopman 算子的 MNIW 先验。
2. **在线适应阶段**：给定近期轨迹段，基于共轭先验进行闭式贝叶斯更新，得到当前条件下的 Koopman 算子后验。
3. **预测阶段**：利用后验预测分布生成未来状态轨迹分布，用于多步预测。
4. **决策/规划阶段**：将预测分布及其不确定性用于动态可行运动规划，尤其在避让机动和牵引力极限操作中。
- **公式细节**：当前提供的材料未给出具体公式、变量定义或完整算法伪代码，无法进一步展开。

## 3. 实验设计
- **真实系统场景**：
  - 全尺寸自动驾驶卡车-拖车系统。
  - 多种恶劣冬季场景：雪、冰、混合摩擦条件。
- **仿真控制任务**：
  - 包含多种分布偏移的控制任务。
- **评价目标**：
  - 多步预测精度。
  - 不确定性校准。
  - 对分布偏移的鲁棒性。
  - 动态可行运动规划效果，尤其是避让机动和牵引力极限操作。
- **Benchmark**：当前材料未给出统一 benchmark 名称或标准数据集名称。
- **对比方法**：摘要仅称“prior approaches”，未列出具体基线方法名称。
- **项目网站**：https://mahmoud-selim.github.io/MetaKoopman/

## 4. 资源与算力
- 当前提供的文本中 **未提及** GPU 型号、GPU 数量、训练时长、参数量、推理成本或计算资源规模。
- 因此无法总结算力开销，也无法判断训练与在线适应的实际计算可行性。

## 5. 实验数量与充分性
- 从摘要可见，实验至少覆盖两类：
  - 真实全尺寸卡车-拖车冬季多场景实验。
  - 仿真控制任务中的多种分布偏移实验。
- 任务层面覆盖了多步预测、不确定性校准、鲁棒性和运动规划。
- **但当前材料未说明**：
  - 具体实验组数、数据规模、轨迹数量。
  - 消融实验设置。
  - 统计显著性检验。
  - 基线方法细节和公平性配置。
- **充分性判断**：真实系统与仿真结合提升了应用说服力，但由于缺少基线、指标定义、消融和统计信息，无法客观评估实验是否充分、公平。

## 6. 主要结论与发现
- MetaKoopman 在多步预测精度、不确定性校准和对分布偏移的鲁棒性上 **持续优于先前方法**。
- 现场实验表明，该方法能有效支持动态可行运动规划，尤其在 **避让机动** 和 **牵引力极限操作** 中表现有效。
- 通过闭式后验预测分布，方法能够同时表达认知与偶然不确定性，为不确定性感知决策提供基础。
- 整体上，论文为分布偏移下的非线性动力学建模与鲁棒决策提供了一个不确定性感知的 Koopman 框架。

## 7. 优点
- **方法融合新颖**：将 Koopman 线性潜表示、贝叶斯元学习和 MNIW 共轭先验结合，兼顾可解释性与适应性。
- **闭式计算友好**：闭式贝叶斯更新和闭式后验预测避免了复杂近似推断，潜在提升在线适应效率。
- **不确定性量化完整**：同时考虑认知与偶然不确定性，有利于安全关键场景下的鲁棒规划。
- **真实系统验证**：在全尺寸卡车-拖车和恶劣冬季场景中验证，应用价值较强。
- **任务覆盖较广**：涵盖仿真与现场、预测与规划、分布偏移与牵引力极限等挑战性条件。

## 8. 不足与局限
- **材料限制**：当前 PDF 提取内容为验证页，无法核实正文中的公式、算法细节、实验表格和理论证明。
- **基线不明确**：未列出具体对比方法，难以判断性能提升是否来自公平比较。
- **实验细节缺失**：未说明数据集规模、实验组数、消融、统计检验和评价指标定义。
- **算力与可复现性未说明**：未提供 GPU、训练时长、代码或数据可用性信息。
- **假设限制**：Koopman 线性潜表示和 MNIW 先验可能对强非线性、非平稳或突变动力学存在建模限制。
- **长期预测与实时性未知**：多步误差累积、在线更新频率、实时控制延迟等未在可见材料中讨论。
- **现场实验限制**：恶劣冬季实车实验成本高、风险大，可重复性和安全性边界需更多说明。
- **应用范围**：目前主要验证于卡车-拖车系统，向其他机器人或通用动力学系统的泛化能力尚不明确。

（完）
