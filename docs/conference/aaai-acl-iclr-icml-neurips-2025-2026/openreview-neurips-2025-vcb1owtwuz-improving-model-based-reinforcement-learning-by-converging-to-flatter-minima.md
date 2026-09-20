---
title: Improving Model-Based Reinforcement Learning by Converging to Flatter Minima
title_zh: 通过收敛到更平坦极小值改进基于模型的强化学习
authors: "Shrinivas Ramasubramanian, Benjamin Freed, Alexandre Capone, Jeff Schneider"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=vcB1OwtWUZ"
tags: ["query:koopman-rl"]
score: 4.0
evidence: 面向控制的基于模型强化学习世界模型训练
tldr: 模型强化学习依赖学习的动力学模型，其误差会沿想象轨迹累积，损害下游控制性能。本文将锐度感知最小化作为即插即用目标融入世界模型训练，并用PAC-Bayes界将一阶锐度与值估计差距及模型最优与真实最优策略的性能差距联系起来。实验表明该方法降低模型锐度并提升策略表现，为提升MBRL鲁棒性提供简单有效手段。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 基于模型的强化学习中动力学模型误差会沿想象轨迹累积，影响下游控制效果。
method: 将锐度感知最小化作为即插即用目标融入世界模型训练，并用PAC-Bayes界分析锐度与性能差距的关系。
result: 实验显示SAM降低模型锐度并提升策略性能，理论界也得到收紧。
conclusion: 为提升基于模型强化学习鲁棒性提供了简单有效且带理论支撑的手段。
---

## Abstract
Model-based reinforcement learning (MBRL) hinges on a learned dynamics model whose errors can compound along imagined rollouts. We study how encouraging \emph{flatness} in the model’s training loss affects downstream control, and show that steering optimization toward flatter minima yields a better policy. Concretely, we integrate \emph{Sharpness-Aware Minimization} (SAM) into world-model training as a drop-in objective, leaving the planner and policy components unchanged. On the theory side, we derive PAC-Bayesian bounds that link first-order sharpness to the value-estimation gap and the performance gap between model-optimal and true-optimal policies, implying that flatter minima tighten both. Empirically, SAM reduces measured sharpness and value-prediction error and improves returns across HumanoidBench, Atari-100k, and high-DoF DeepMind Control tasks. Augmenting existing MBRL algorithms with SAM increases mean return, with especially large gains in settings with high dimensional state–action space. We further observe positive transfer across algorithms and input modalities, including a transformer-based world-model. These results position flat-minima training as a simple, general mechanism for more robust MBRL without architectural changes.

---

## 论文详细总结（自动生成）

# 论文总结：Improving Model-Based Reinforcement Learning by Converging to Flatter Minima

> 说明：提供的 PDF 提取文本为 OpenReview 的浏览器验证页，未能获取论文正文；以下总结主要依据论文标题、元数据与摘要。因此，涉及具体公式、实验组数、算力等信息时，只能基于可获取内容进行概括，并明确指出缺失部分。

## 1. 核心问题与整体含义

- **研究动机**：基于模型的强化学习（MBRL）依赖学习到的动力学模型进行想象 rollout；模型误差会在多步想象中累积，进而损害下游控制策略的性能。
- **核心问题**：训练动力学模型时，优化到“更平坦的极小值”是否能提升下游控制？平坦性如何与值估计误差、模型最优策略与真实最优策略之间的性能差距发生联系？
- **整体含义**：论文试图将“平坦极小值训练”引入 MBRL 世界模型训练，作为一种不改变规划器与策略结构的通用鲁棒性提升机制。其意义在于：如果模型损失曲面更平坦，模型在想象 rollout 中对扰动和误差更鲁棒，从而带来更好的控制表现。

## 2. 方法论

- **核心思想**：将 **Sharpness-Aware Minimization (SAM)** 作为即插即用目标融入世界模型训练，保持 planner 和 policy 组件不变。
- **关键技术细节**：
  - SAM 不单纯最小化当前参数处的训练损失，而是倾向于寻找参数邻域内损失较平坦的极小值。
  - 一般流程可概括为：先沿能最大化损失的方向对模型参数施加扰动，再在扰动后的参数处计算梯度并更新原参数，从而惩罚尖锐极小值。
  - 在本文中，该目标被用于 MBRL 的 world-model 训练，而不是改变策略学习或规划算法。
- **理论分析**：
  - 论文推导了 **PAC-Bayesian 界**，将一阶锐度与以下两者联系起来：
    1. 值估计差距；
    2. 模型最优策略与真实最优策略之间的性能差距。
  - 理论含义是：更平坦的极小值会收紧上述两个差距，从而为“平坦性提升下游控制”提供理论支撑。
- **公式与算法说明**：当前可获取文本未给出显式数学公式、扰动半径、采样次数或完整伪代码，因此无法进一步展开具体实现细节。

## 3. 实验设计

- **使用场景 / 数据集 / Benchmark**：
  - HumanoidBench；
  - Atari-100k；
  - 高自由度 DeepMind Control（DMC）任务。
- **对比方法**：
  - 将 SAM 融入已有 MBRL 算法，与未使用 SAM 的对应基线进行对比。
  - 摘要提到跨算法、跨输入模态的正向迁移，包括一个基于 transformer 的世界模型。
- **评估指标**：
  - 模型锐度（measured sharpness）；
  - 值预测误差（value-prediction error）；
  - 策略回报 / 平均回报（returns / mean return）。
- **主要实验现象**：
  - SAM 降低了模型锐度和值预测误差；
  - 在多个 benchmark 上提升回报；
  - 在高维状态-动作空间任务中增益尤其明显；
  - 对不同 MBRL 算法、输入模态和 transformer world-model 均表现出正向迁移。

## 4. 资源与算力

- 在当前提供的文本中，**未明确说明使用的 GPU 型号、数量、训练时长、总计算量或实验集群规模**。
- 由于正文不可访问，无法判断论文是否在附录或实验设置中报告了算力细节。

## 5. 实验数量与充分性

- 从摘要可见，实验覆盖了至少三类主要 benchmark：HumanoidBench、Atari-100k、高自由度 DMC。
- 还涉及跨算法、跨输入模态以及 transformer-based world-model 的验证。
- 但当前文本**未给出具体任务数量、随机种子数、消融实验数量、统计显著性检验或超参数搜索细节**。
- 因此：
  - 从覆盖范围看，实验设计具有一定的多样性和跨域验证意图；
  - 但从可获取信息看，无法充分判断实验是否足够全面、客观和公平。
- 公平性方面，若 SAM 仅作为 world-model 训练目标且保持 planner/policy 不变，则比较逻辑相对清晰；但 SAM 会带来额外计算开销，若未控制训练预算或调参预算，比较可能存在不公平风险。

## 6. 主要结论与发现

- 将优化引导至更平坦的极小值，可以改善 MBRL 的下游控制性能。
- SAM 作为即插即用目标，能降低世界模型的锐度和值预测误差，并提升策略回报。
- 在高维状态-动作空间任务中，SAM 带来的收益更大。
- 该方法在不同算法和输入模态间具有正向迁移性，包括 transformer-based world-model。
- 总体结论是：**平坦极小值训练是一种简单、通用、无需架构改动即可提升 MBRL 鲁棒性的机制**。

## 7. 优点

- **即插即用**：不改变 planner 和 policy，易于集成到现有 MBRL 流程。
- **理论与实验结合**：用 PAC-Bayes 界将平坦性与值估计差距、策略性能差距联系起来。
- **跨域验证**：覆盖 HumanoidBench、Atari-100k、高自由度 DMC，并测试多种算法与输入模态。
- **关注高维控制**：在高维状态-动作空间中报告了较大增益，切中 MBRL 的难点。
- **通用性潜力**：对 transformer world-model 也观察到正向效果，说明方法可能不局限于特定架构。

## 8. 不足与局限

- **正文不可获取**：当前总结无法核实具体公式、算法伪代码、实验表格和附录细节。
- **算力与开销未说明**：未报告 GPU 型号、数量、训练时长，也未讨论 SAM 带来的额外计算成本。
- **实验细节不足**：缺少任务数量、种子数、消融实验、超参数敏感性和统计显著性信息。
- **公平性风险**：若 SAM 增加计算量但未匹配基线训练预算，性能提升可能部分来自更多计算而非平坦性本身。
- **理论假设限制**：PAC-Bayes 界通常依赖特定假设，实际 MBRL 中的非平稳性、模型偏差和分布偏移可能影响结论外推。
- **应用限制**：未提及真实机器人、安全约束、在线适应或计算资源受限场景下的表现。
- **偏差风险**：实验可能集中在特定 benchmark 和高维任务上，低维任务、稀疏奖励或长时程任务中的效果仍需验证。

（完）
