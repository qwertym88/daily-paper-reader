---
title: Conformal Online Learning of Deep Koopman Linear Embeddings
title_zh: 深度Koopman线性嵌入的共形在线学习
authors: "Ben Gao, Jordan Patracone, Stephane Chretien, Olivier Alata"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=O8Ifwhylnr"
tags: ["query:koopman-rl"]
score: 9.0
evidence: 面向非线性系统的深度Koopman线性嵌入在线学习
tldr: 非线性系统Koopman表示常需离线训练，难以适应流式数据与分布变化。本文提出COLoKe，在提升空间中结合深度特征学习与多步预测一致性，动态更新Koopman不变表示。方法引入类共形机制，将关注点从新状态一致性转向当前Koopman模型一致性，仅当预测误差超过动态校准阈值时才触发算子与嵌入的选择性精修。实验在基准动力学系统上验证了其抗过拟合与自适应能力，为在线Koopman建模提供了新框架。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 非线性系统的Koopman表示多依赖离线训练，难以适应流式数据与分布漂移。
method: 提出COLoKe，结合深度特征学习与多步预测一致性，并用类共形阈值机制选择性更新Koopman算子。
result: 在基准动力学系统上实现了自适应更新并抑制过拟合。
conclusion: 为在线Koopman表示学习提供了新的自适应框架。
---

## Abstract
We introduce Conformal Online Learning of Koopman embeddings (COLoKe), a novel framework for adaptively updating Koopman-invariant representations of nonlinear dynamical systems from streaming data. Our modeling approach combines deep feature learning with multistep prediction consistency in the lifted space, where the dynamics evolve linearly. To prevent overfitting, COLoKe employs a conformal-style mechanism that shifts the focus from evaluating the conformity of new states to assessing the consistency of the current Koopman model. Updates are triggered only when the current model’s prediction error exceeds a dynamically calibrated threshold, allowing selective refinement of the Koopman operator and embedding. Empirical results on benchmark dynamical systems demonstrate the effectiveness of COLoKe in maintaining long-term predictive accuracy while significantly reducing unnecessary updates and avoiding overfitting.

---

## 论文详细总结（自动生成）

# 论文总结：Conformal Online Learning of Deep Koopman Linear Embeddings

> 说明：提供的“PDF 提取文本”实际为 OpenReview 验证页面，未包含论文正文。以下总结主要依据论文摘要与元数据（标题、作者、TLDR、motivation、method、result、conclusion 等）；实验、算力等细节在可获取内容中大多缺失，无法确认。

## 1. 核心问题与整体含义
- **研究背景**：非线性动力系统的 Koopman 表示通常依赖离线训练，难以适应流式数据、在线场景和分布漂移。
- **核心问题**：如何从持续到来的数据中自适应更新深度 Koopman 线性嵌入与 Koopman 算子，同时保持长期预测精度并避免过拟合。
- **整体含义**：论文提出 COLoKe，将深度特征学习、Koopman 线性嵌入与“类共形”更新触发机制结合，为在线 Koopman 建模提供新框架。其关注点不是单纯让新状态符合旧模型，而是判断当前 Koopman 模型本身是否仍然一致可靠。

## 2. 方法论
- **核心思想**：在提升空间中学习深度特征，使非线性动力学近似线性演化；通过多步预测一致性约束提升表示质量，并用类共形机制决定是否更新模型。
- **关键技术细节**：
  - 结合 **深度特征学习** 与 **多步预测一致性**，在 lifted space 中学习 Koopman-invariant representation。
  - 引入 **conformal-style mechanism**：从“评估新状态的一致性”转向“评估当前 Koopman 模型的一致性”。
  - 仅当当前模型的预测误差超过 **动态校准阈值** 时，才触发更新。
  - 更新并非全量重训，而是对 **Koopman 算子与嵌入进行选择性精修**，以减少不必要更新并抑制过拟合。
- **算法流程（文字说明）**：
  1. 接收流式数据；
  2. 用当前深度嵌入将状态提升到线性演化空间；
  3. 基于当前 Koopman 算子进行多步预测；
  4. 计算当前模型的预测误差/一致性；
  5. 与动态校准阈值比较；
  6. 若超过阈值，则选择性更新嵌入与 Koopman 算子；否则保持模型不变；
  7. 持续重复，实现长期在线自适应。
- **公式与细节**：可获取文本中未给出具体公式、阈值校准方式、损失函数或优化算法细节。

## 3. 实验设计
- **数据集/场景**：摘要仅称在 **benchmark dynamical systems** 上验证，未列出具体系统名称、数据规模、采样方式或训练/测试划分。
- **Benchmark**：未明确说明具体 benchmark 名称，只能确认是“基准动力学系统”类任务。
- **对比方法**：可获取内容未提及任何基线方法或对比算法。
- **评价目标**：从摘要可推断包括长期预测精度、不必要更新次数、过拟合抑制能力，但具体指标未给出。

## 4. 资源与算力
- 可获取内容中 **未提及 GPU 型号、数量、训练时长、参数量或计算开销**。
- 因此无法总结资源与算力使用情况；这一点属于信息缺失。

## 5. 实验数量与充分性
- **实验组数**：摘要未说明使用了多少数据集、多少组实验、是否包含消融实验。
- **充分性**：仅凭摘要无法判断实验是否充分。虽然提到“benchmark dynamical systems”，但缺少基线、指标、统计显著性和消融细节。
- **客观性与公平性**：无法评估。没有对比方法、数据划分、调参协议等信息，难以判断实验是否客观公平。
- 元数据中标注 `score: 9.0`，可能表示检索或评审相关评分较高，但这不能替代对实验细节的独立评估。

## 6. 主要结论与发现
- COLoKe 能在基准动力学系统上从流式数据自适应更新 Koopman 表示。
- 方法在保持 **长期预测精度** 的同时，能 **显著减少不必要的更新**。
- 类共形阈值触发机制有助于 **避免过拟合**。
- 总体结论：为在线 Koopman 表示学习提供了一个新的自适应框架。

## 7. 优点
- **在线自适应**：面向流式数据和分布变化，而非固定离线训练。
- **更新触发机制新颖**：将类共形思想用于模型一致性判断，而非仅判断新样本是否异常。
- **选择性精修**：只在误差超过动态阈值时更新，可减少计算与过拟合风险。
- **多步预测一致性**：在提升空间中约束长期动力学一致性，比单步拟合更关注长期预测。
- **框架通用性**：可望适用于多类非线性动力学系统的在线建模。

## 8. 不足与局限
- **正文不可得**：提供的 PDF 文本是验证页面，无法验证方法细节、实验设置和结论可靠性。
- **实验信息缺失**：未列出具体数据集、benchmark、对比方法、评价指标、消融实验和统计结果。
- **算力与效率未说明**：没有 GPU、训练时长或在线更新开销信息。
- **理论与机制细节不足**：动态阈值如何校准、是否有理论保证、超参数敏感性等均未说明。
- **应用限制**：依赖 Koopman 线性嵌入假设；对强非线性、高维真实系统、剧烈分布漂移的适应性尚不明确。
- **可复现性风险**：缺少实现细节和实验协议，难以复现或公平比较。

（完）
