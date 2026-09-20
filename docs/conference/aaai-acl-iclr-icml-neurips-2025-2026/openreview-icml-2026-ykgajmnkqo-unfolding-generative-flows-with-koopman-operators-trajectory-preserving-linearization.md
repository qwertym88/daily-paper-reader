---
title: "Unfolding Generative Flows with Koopman Operators: Trajectory-Preserving Linearization"
title_zh: 用Koopman算子展开生成流：保持轨迹的线性化
authors: "Erkan Turan, Ari Siozopoulos, Louis Martinez, Julien Gaubil, Emery Pierson, Maks Ovsjanikov"
date: 2026-04-30
pdf: "https://openreview.net/pdf/5eef0bfdc3a3220e1063f6b8c4d5f06b27f6c8e8.pdf"
tags: ["query:koopman-rl"]
score: 5.0
evidence: 通过Koopman理论全局线性化流动态
tldr: 连续归一化流虽能优雅地生成建模，但迭代采样代价高且中间状态缺乏可解释性。本文将条件流匹配提升到高维Koopman空间，用单一线性算子表示其演化，实现保持轨迹的全局线性化。不同于仅蒸馏边界的方法，该视角保留教师模型的中间动态，加速采样的同时提升可解释性，为生成模型与Koopman理论的结合提供了新途径。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 连续归一化流迭代采样代价高、中间状态缺乏可解释性，且现有加速方法丢弃中间动态。
method: 将条件流匹配提升到高维Koopman空间，用单一线性算子表示演化实现轨迹保持线性化。
result: 在加速采样的同时保留教师模型中间动态并提升可解释性。
conclusion: 为生成模型与Koopman理论的结合提供了新视角。
---

## Abstract
Continuous Normalizing Flows (CNFs) enable elegant generative modeling but remain bottlenecked by their iterative nature requiring costly sampling and lacking interpretability of the intermediate states. Recent approaches accelerate sampling by straightening trajectories or distilling endpoints, yet they treat the original generative process as a black box, discarding the teacher’s intermediate dynamics. We propose a fundamentally different perspective: globally linearizing flow dynamics via Koopman theory to achieve trajectory-preserving linearization. By lifting Conditional Flow Matching (CFM) into a higher-dimensional Koopman space, we represent its evolution with a single linear operator. Crucially, unlike boundary-only distillation, our method enforces infinitesimal consistency with the teacher's vector field along *the full generative path*. We derive a practical, simulation-free training objective that ensures this global alignment and yields two key benefits. First, sampling becomes one-step and parallelizable. Second, because the linearization is faithful to the dynamics, the Koopman operator provides unique insights on the generation. We demonstrate that this structure enables novel applications unavailable in prior approaches, including discovery of semantically coherent editing directions, inversion with a teacher-aligned linear operator and class-conditional spectral signatures. Empirically, our approach achieves competitive sample quality, while enabling spectral analysis and control of the *entire trajectories* of generative flows.

---

## 论文详细总结（自动生成）

# 论文总结：用 Koopman 算子展开生成流：保持轨迹的线性化

> 说明：提供的 PDF 提取文本实际为 OpenReview 的 CAPTCHA 验证页，未能获取论文正文。以下总结主要依据论文标题、摘要与元数据；涉及数据集、算力、实验组数等正文细节时，将明确标注为“未说明/无法确认”。

## 1. 核心问题与整体含义
- **研究动机**：连续归一化流（CNFs）能优雅地进行生成建模，但依赖迭代采样，代价高，且中间状态缺乏可解释性。
- **现有方法局限**：近期加速方法多通过“拉直轨迹”或“蒸馏端点”来减少采样步数，但通常把原始生成过程当作黑箱，丢弃教师模型的中间动态。
- **整体含义**：论文提出一种不同视角：利用 Koopman 理论对生成流动态进行全局线性化，实现“保持轨迹的线性化”。其目标不是只匹配边界分布，而是在完整生成路径上保持与教师流的一致性，从而同时实现加速采样与可解释性。

## 2. 方法论
- **核心思想**：
  - 将条件流匹配（Conditional Flow Matching, CFM）提升到高维 Koopman 空间。
  - 在该空间中，用**单一线性算子**表示生成流的演化。
  - 通过全局线性化，使采样可一步完成并并行化，同时保留教师模型的中间动态结构。
- **关键技术细节**：
  - 与仅做边界蒸馏的方法不同，本文强调与教师向量场沿**完整生成路径**的“无穷小一致性”（infinitesimal consistency）。
  - 推导了一个实用的、**无需模拟**（simulation-free）的训练目标，用于保证这种全局对齐。
  - 由于线性化忠实于动态，Koopman 算子可提供对生成过程的独特洞察。
- **算法流程（文字描述）**：
  1. 以 CFM 定义的连续时间生成流作为教师模型。
  2. 学习一个提升映射，将状态映射到高维 Koopman 空间。
  3. 在 Koopman 空间中学习线性算子，使沿完整生成路径的演化与教师向量场保持一致。
  4. 采样时在 Koopman 空间中进行线性推进，实现单步或并行生成。
- **直接收益**：
  - 采样变为一步且可并行。
  - 保留教师中间动态，支持谱分析与控制。
  - 支持语义一致编辑方向发现、教师对齐线性算子反演、类条件谱签名等新应用。

## 3. 实验设计
- **可识别的评估维度**（来自摘要）：
  - 样本质量：摘要称达到“有竞争力”的样本质量。
  - 语义一致的编辑方向发现。
  - 使用教师对齐线性算子进行反演。
  - 类条件谱签名。
  - 对生成流“整个轨迹”的谱分析与控制。
- **数据集 / 场景**：
  - 摘要未给出具体数据集、任务场景或数据模态。
  - 未说明是图像生成、类条件生成，还是其他生成建模任务。
- **Benchmark**：
  - 未明确说明使用了哪些 benchmark。
- **对比方法**：
  - 摘要仅泛称与“拉直轨迹”“边界蒸馏”等加速/蒸馏思路不同。
  - 未列出具体基线方法名称。
- **评价指标**：
  - 未说明 FID、似然、采样步数、加速比、编辑质量等具体指标。

## 4. 资源与算力
- 提供的摘要与元数据中**未提及**：
  - GPU 型号、数量；
  - 训练时长；
  - 参数量、训练成本；
  - 采样阶段的计算开销或加速比。
- 因此无法从现有材料判断其算力需求与效率优势的具体程度。

## 5. 实验数量与充分性
- 摘要提到“Empirically”达到有竞争力的样本质量，并展示了若干新应用，说明论文至少包含样本质量评估与若干应用性实验。
- 但现有材料**未提供**：
  - 具体实验组数；
  - 不同数据集上的结果；
  - 消融实验；
  - 统计显著性；
  - 与基线的公平比较设置。
- 因此无法评估实验是否充分、客观、公平；这些需要查阅论文正文或补充材料。

## 6. 主要结论与发现
- 通过 Koopman 理论对 CFM 进行全局线性化，可以在保持轨迹的同时实现加速采样。
- 与仅蒸馏边界的方法相比，本文方法保留了教师模型的中间动态，因此线性化更忠实。
- Koopman 算子提供了对生成过程的可解释分析能力，例如谱分析、轨迹控制、类条件谱签名。
- 采样可变为一步且并行化。
- 方法支持语义编辑方向发现和教师对齐的反演。
- 整体上，论文为生成模型与 Koopman 理论的结合提供了新途径。

## 7. 优点
- **理论视角新颖**：将 Koopman 动力系统理论引入连续归一化流与条件流匹配的加速问题。
- **轨迹保持**：不是只匹配初始/终止边界，而是约束完整生成路径上的动态一致性。
- **训练目标实用**：提出 simulation-free 目标，避免昂贵的轨迹模拟。
- **采样高效潜力**：一步、并行采样，具备显著加速潜力。
- **可解释性强**：线性算子便于谱分析、方向发现与轨迹控制。
- **应用面较广**：语义编辑、反演、类条件谱签名等应用在传统蒸馏方法中较难自然获得。

## 8. 不足与局限
- **材料限制**：提供的 PDF 文本为 CAPTCHA 页面，无法核验正文，实验、公式、理论证明等细节均缺失。
- **实验覆盖未知**：未说明数据集、benchmark、基线、指标，无法判断实验充分性与公平性。
- **算力与效率未说明**：缺少 GPU、训练时长、加速比、内存开销等信息。
- **方法潜在限制**：
  - 高维 Koopman 空间的维度选择、计算成本和数值稳定性未在摘要中说明。
  - 对强非线性、多模态、高分辨率生成任务的保真度与泛化性未知。
  - 线性化误差、理论保证与失败模式未

未在现有材料中给出明确结论；其误差传播、长期稳定性与分布匹配的理论保证均无法从摘要判断。
- **基线比较不明确**：摘要仅以“拉直轨迹/边界蒸馏”概括对照思路，未列出具体基线方法、统一评估协议或公平性设置。
- **应用评估细节缺失**：语义编辑、反演、类条件谱签名等应用缺乏定量指标、用户研究或失败案例分析。
- **可扩展性未知**：高分辨率、多模态、长序列等场景下的 Koopman 维度爆炸与计算瓶颈未讨论。

## 9. 可复现性与开放问题
- **代码与数据**：现有元数据未说明是否公开代码、预训练模型或数据集。
- **训练细节**：超参数、提升映射结构、Koopman 算子参数化、优化策略、训练步数等均未提供。
- **评估协议**：采样步数、加速比、生成质量指标、编辑方向评价标准等未说明。
- **理论问题**：有限维 Koopman 近似何时能忠实表示原生成流？误差是否有界？对多模态、强非线性分布的适用条件是什么？
- **应用边界**：谱分析、轨迹控制、类条件谱签名等是否依赖特定数据模态或条件结构，尚无法确认。
- **与相关工作的关系**：与一致性模型、整流流、分数蒸馏、扩散蒸馏等加速范式的定量差异与互补性，需要正文验证。

## 10. 总体评价
- **潜在贡献**：若正文按摘要所述实现，该工作将 Koopman 动力系统理论引入条件流匹配，强调“保持轨迹”的全局线性化，而非仅匹配端点分布，在生成模型加速与可解释性之间提供了新结合点。
- **主要不确定性**：由于当前 PDF 提取文本为 CAPTCHA 页面，无法核验公式推导、理论证明、实验设置与结果数值。因此，样本质量“有竞争力”、一步并行采样、谱可解释性等结论目前只能视为作者主张，不能独立确认。
- **阅读建议**：若关注生成模型加速、流匹配、动力系统线性化或可解释生成，该论文值得进一步查阅正文；但应重点核查实验基线是否公平、计算成本是否真实降低、高维场景是否可扩展、理论保证是否充分，以及应用展示是否具有统计与语义上的稳健性。
- **总体判断**：选题新颖，问题意识明确，具备理论吸引力；但在缺乏正文证据的情况下，尚不能对其实际效果、通用性与可复现性作出强判断。

（完）
