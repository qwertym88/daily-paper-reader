---
title: Learning the Koopman Operator using Attention Free Transformers
title_zh: 使用无注意力Transformer学习Koopman算子
authors: "Mohammed Nagdi, Evangelos-Marios Nikolados, Alexey Yermakov, Mars Liyao Gao, J. Nathan Kutz, Filippo Menolascina"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=94pU0rTHLD"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 用无注意力潜在记忆学习Koopman算子以实现鲁棒线性预测
tldr: 用自编码器学习Koopman算子虽能在潜空间做线性预测，但长时程推演会偏离学习流形，在切换、连续谱或强瞬态系统中产生相位与幅值误差。本文引入两个组件提升鲁棒性：一是无注意力的潜在记忆块，聚合过去潜变量产生校正残差；二是动态重编码。该方法以近线性复杂度抑制误差发散。该工作直接推进了Koopman算子的学习与预测鲁棒性。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 自编码器学习的Koopman算子在长时程推演时易偏离流形，产生相位与幅值误差。
method: 引入无注意力潜在记忆块聚合历史潜变量产生校正残差，并提出动态重编码。
result: 以线性时间复杂度和相近参数量抑制误差发散，提升长时程预测鲁棒性。
conclusion: 显著增强了Koopman预测器在复杂动力学上的稳定性与精度。
---

## Abstract
Learning Koopman operators with autoencoders enables linear prediction in a latent space, but long-horizon rollouts often drift off the learned manifold, leading to phase and amplitude errors on systems with switching, continuous spectra, or strong transients. We introduce two complementary components that make Koopman predictors substantially more robust. First, we add an \emph{attention-free latent memory} (AFT) block that aggregates a short window of past latents to produce a corrective residual before each Koopman update. Unlike multi-head attention, AFT operates in linear time with nearly identical parameter count to the baseline, yet captures the local temporal context needed to suppress error divergence. Second, we propose \emph{dynamic re-encoding}: lightweight, online change-point triggers (EWMA, CUSUM, and sequential two-sample tests) that detect latent drift and project predictions back onto the autoencoder manifold. Across three benchmark systems—Duffing oscillator, Repressilator, IRMA—our model consistently reduces error accumulation compared to a Koopman autoencoder and matched-capacity multi-head attention. We also compare against GRU and Transformer autoencoders, evaluated both from initial conditions and with a 50-step context, and find that Koopman+AFT (with optional re-encoding) attains markedly lower long-horizon error while maintaining substantially lower inference latency. We report improvements over horizons up to 1000 steps, together with ablations over trigger policies. The resulting predictors are fast, compact, and geometry-preserving, providing a practical path to long-term forecasting with Koopman methods.

---

## 论文详细总结（自动生成）

# 论文总结：Learning the Koopman Operator using Attention Free Transformers

> 说明：提供的 PDF 提取文本仅为 OpenReview 的 CAPTCHA/验证页面，未能获取论文正文。以下总结主要依据论文摘要与元数据，部分细节无法核实，已在不明确处标注。

## 1. 核心问题与整体含义
- **研究动机**：使用自编码器学习 Koopman 算子，可以在潜空间中实现线性预测，但长时程 rollout 容易偏离已学习到的流形，导致相位和幅值误差。
- **关键困难**：在具有切换行为、连续谱或强瞬态的动力系统中，这种误差累积尤其严重，影响长期预测的可靠性。
- **整体含义**：论文试图提升 Koopman 预测器的长时程鲁棒性，使其在保持线性预测优势的同时，减少潜空间漂移和几何失真，为长期预测提供更实用的路径。

## 2. 方法论
- **核心思想**：在 Koopman 潜空间线性推进的基础上，引入两个互补组件，分别从“局部时序校正”和“流形投影纠正”两个层面抑制误差发散。
- **组件一：无注意力潜在记忆块（Attention-Free Latent Memory, AFT）**
  - 聚合一小段过去潜变量窗口。
  - 在每次 Koopman 更新前产生一个校正残差。
  - 与多头注意力不同，AFT 以近似线性时间运行，参数量与基线几乎相同。
  - 目标是捕捉局部时序上下文，从而抑制长时程误差发散。
- **组件二：动态重编码（Dynamic Re-encoding）**
  - 使用轻量、在线的变点触发机制检测潜空间漂移。
  - 触发方法包括 EWMA、CUSUM 和序贯双样本检验。
  - 当检测到漂移时，将预测投影回自编码器流形，以纠正偏离。
- **算法流程（文字描述）**：
  1. 用自编码器将系统状态编码到潜空间。
  2. 维护短窗口历史潜变量。
  3. AFT 块根据历史潜变量生成校正残差。
  4. 在残差校正后进行 Koopman 线性更新。
  5. 动态重编码模块在线监测潜变量漂移。
  6. 若检测到漂移，则将预测重新编码/投影回自编码器流形。
  7. 继续长时程 rollout。
- **复杂度与参数**：AFT 具有近线性复杂度，参数规模与基线接近，因此方法在计算上较实用。

## 3. 实验设计
- **数据集/场景**：三个基准动力系统：
  - Duffing oscillator
  - Repressilator
  - IRMA
- **Benchmark 目标**：评估长时程预测中的误差累积、鲁棒性以及推理延迟。
- **对比方法**：
  - Koopman autoencoder 基线
  - 容量匹配的多头注意力模型（matched-capacity multi-head attention）
  - GRU autoencoder
  - Transformer autoencoder
  - Koopman+AFT（可选加入 re-encoding）
- **评估设置**：
  - 从初始条件直接预测。
  - 使用 50 步上下文进行预测。
  - 报告最长至 1000 步的预测表现。
  - 对触发策略进行消融实验。
- **主要评估指标**：长时程误差、误差累积、推理延迟等。

## 4. 资源与算力
- 摘要与元数据中**未明确说明**使用的 GPU 型号、数量、训练时长、内存或总算力。
- 因此无法评估该方法的训练成本、可复现性以及相对基线的完整计算公平性。
- 文中提到推理延迟较低，但这属于模型推理效率，不等同于训练算力开销。

## 5. 实验数量与充分性
- 按摘要可识别出的实验矩阵大致包括：
  - 3 个基准动力系统。
  - 至少 5 类模型/变体对比。
  - 2 种评估条件：初始条件预测、50 步上下文预测。
  - 最长 1000 步的长时程评估。
  - 触发策略消融实验。
- 因此实验覆盖了多个系统、多个基线和长时程场景，整体设计较充分。
- **公平性方面**：论文与容量匹配的多头注意力比较，并控制参数量接近，显示了一定的公平比较意图。
- **但不足是**：由于正文不可得，无法确认是否报告了随机种子、方差、统计显著性、超参数搜索范围、训练预算一致性等，因此不能完全判断实验的客观性和可复现性。

## 6. 主要结论与发现
- Koopman+AFT（可选加入动态重编码）在多个基准系统上**一致降低误差累积**。
- 相比 Koopman autoencoder 和容量匹配的多头注意力模型，该方法长时程误差更低。
- 相比 GRU autoencoder 和 Transformer autoencoder，Koopman+AFT 在长时程预测上误差显著更低，同时保持更低的推理延迟。
- 改进在最长 1000 步的预测范围内仍然存在。
- 动态重编码和触发策略消融表明，在线漂移检测与流形投影有助于提升鲁棒性。
- 最终预测器被描述为快速、紧凑且几何保持，适合长期预测。

## 7. 优点
- **方法层面**：
  - AFT 以近线性复杂度提供局部时序记忆，避免标准注意力的二次复杂度。
  - 参数量与基线接近，实用性强。
  - 动态重编码轻量、在线，能检测潜空间漂移并投影回流形。
  - 同时处理“局部时序校正”和“全局流形漂移”，思路互补。
- **实验层面**：
  - 覆盖三个不同动力系统。
  - 对比多种基线，包括 Koopman、注意力、GRU、Transformer。
  - 同时评估初始条件和带上下文预测。
  - 评估长时程至 1000 步，并报告推理延迟。
  - 对触发策略进行消融，增强方法解释性。
- **应用层面**：强调快速、紧凑、几何保持，适合长期预测和实时性要求较高的场景。

## 8. 不足与局限
- **信息可验证性受限**：提供的 PDF 文本仅为验证页面，无法核对正文公式、算法伪代码、超参数和完整实验表格。
- **实验覆盖有限**：基准系统为三个动力系统，可能偏仿真/低维或特定生物动力学场景，未提及真实世界高维、噪声数据或更复杂分布外场景。
- **触发策略依赖**：EWMA、CUSUM、序贯检验等在线触发方法通常需要阈值和分布假设，可能对超参数敏感，论文摘要未说明其鲁棒性边界。
- **流形依赖**：动态重编码依赖自编码器学习到的流形质量；若流形学习不准，投影回流形可能无法纠正甚至引入偏差。
- **公平性与统计性未知**：虽然提到容量匹配，但未说明训练预算、随机种子、误差棒和显著性检验，无法完全排除调参或评估偏差。
- **算力未报告**：缺少 GPU 型号、数量、训练时长等信息，影响可复现性和计算成本评估。
- **应用限制**：长时程 1000 步虽已较长，但对于真实长期预测任务仍可能不足；方法在切换、连续谱和强瞬态系统上的泛化能力仍需更多外部验证。

（完）
