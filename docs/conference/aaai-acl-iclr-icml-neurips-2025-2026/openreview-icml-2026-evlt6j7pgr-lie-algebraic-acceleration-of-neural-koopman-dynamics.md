---
title: Lie-Algebraic Acceleration of Neural Koopman Dynamics
title_zh: 神经Koopman动力学的李代数加速
authors: "Jongwon Lee, Jiwoong Kim, Jungwoo Park, Sungwoo Park"
date: 2026-04-30
pdf: "https://openreview.net/pdf/c2831b9a916b7fcb49ce10f3e567a6d5f3df61d3.pdf"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 李代数神经Koopman动力学与长时程预测
tldr: 神经Koopman动力学的序列传播计算负担重，且难以兼顾代数结构与长时程预测。本文提出李代数方法建模Koopman动力学，约束神经生成元在给定李子代数内演化，并通过神经Magnus展开构造有限时间流，保持李群复合一致性。利用李群复合的结合性，采用前缀扫描算法将时间复合深度从线性降到对数级，从而实现精确长时程预测并显著降低计算开销。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 神经Koopman动力学的序列传播计算负担重，难以兼顾代数结构与长时程预测。
method: 用李子代数约束神经生成元，结合神经Magnus展开与前缀扫描算法构造分段传播子。
result: 将时间复合深度从线性降至对数级，实现精确长时程预测并降低计算量。
conclusion: 为可扩展的神经Koopman动力学建模提供了具代数结构的加速框架。
---

## Abstract
We present a Lie-algebraic approach to model Koopman dynamics that integrates algebraic structure with computational scalability.
The proposed formulation constrains the neural generators to evolve within prescribed Lie subalgebras and constructs finite-time flows through a neural Magnus expansion construction, thereby maintaining consistency with the associated Lie-group composition over each time segment. To address the computational burden inherent in sequential propagation, we exploit the associativity of Lie-group compositions and construct segmentwise propagators via a prefix-scan algorithm, which reduces the depth of temporal composition from linear to logarithmic. Consequently, the framework enables accurate long-horizon prediction while improving computational efficiency, and provides a principled foundation for scalable Koopman operator learning for nonlinear systems.

---

## 论文详细总结（自动生成）

### 材料说明
- 当前提供的 PDF 提取文本实际为 OpenReview 的浏览器验证页面，并非论文正文。
- 以下总结主要依据论文标题、作者、摘要、TLDR、motivation、method、result、conclusion 等元数据；凡正文未提供的信息，将明确标注为“未说明/无法判断”。

### 1. 核心问题与整体含义
- **研究动机**：神经 Koopman 动力学的序列传播计算负担较重，尤其在进行长时程预测时，时间复合深度会随步数线性增长。
- **关键矛盾**：现有方法难以同时兼顾代数结构一致性与长时程预测效率。
- **整体含义**：论文试图用李代数/李群结构来约束和加速神经 Koopman 动力学，为非线性系统的可扩展 Koopman 算子学习提供更具原则性的框架。

### 2. 方法论
- **核心思想**：将神经生成元约束在给定李子代数内演化，并通过神经 Magnus 展开构造有限时间流，使每个时间段的传播子保持与对应李群复合的一致性。
- **关键技术细节**：
  - **李子代数约束**：神经生成元不再任意演化，而是在 prescribed Lie subalgebras 内演化。
  - **神经 Magnus 展开**：用 Magnus 展开从生成元构造有限时间流/传播子，保持李群复合结构。
  - **分段传播子**：将时间轴分段，每段构造 segmentwise propagator。
  - **前缀扫描算法**：利用李群复合的结合性，对分段传播子进行层级合并，将时间复合深度从线性降到对数级。
- **算法流程文字说明**：时间分段 → 每段在李代数内学习或构造生成元 → 通过神经 Magnus 展开得到段传播子 → 利用李群复合结合性进行前缀扫描合并 → 得到长时程传播子并用于预测。
- **公式与具体实现**：当前材料未给出具体公式、算法伪代码或网络结构细节。

### 3. 实验设计
- **数据集/场景**：未说明。当前材料未提供任何数据集、任务场景或实验环境信息。
- **Benchmark**：未说明。
- **对比方法**：未说明。
- **评价指标**：未说明。
- **可能关联**：元数据标签含 `query:koopman-rl`，提示可能与 Koopman 强化学习相关，但正文材料未展开，无法确认。

### 4. 资源与算力
- 未提及 GPU 型号、GPU 数量、训练时长、参数量、计算预算或推理成本。
- 因此无法总结资源与算力使用情况。

### 5. 实验数量与充分性
- 未提供实验组数、数据集数量、消融实验、基线对比或统计显著性分析。
- 无法判断实验是否充分、客观、公平。
- 可确认的仅有：论文被 ICML-2026 接收，元数据评分 `score: 8.0`；这是正面同行评审信号，但不能替代对实验细节的审查。

### 6. 主要结论与发现
- 提出一种李代数神经 Koopman 动力学框架，将代数结构与计算可扩展性结合。
- 通过李子代数约束和神经 Magnus 展开，保持每段时间内与李群复合的一致性。
- 利用李群复合结合性和前缀扫描算法，将时间复合深度从线性降至对数级。
- 该框架能够支持准确的长时程预测，同时改善计算效率。
- 为非线性系统的可扩展 Koopman 算子学习提供了原则性基础。

### 7. 优点
- **结构创新**：将李代数、李群复合、Magnus 展开与神经 Koopman 动力学结合，理论动机清晰。
- **计算加速**：利用结合性做前缀扫描，将时间复合深度降至对数级，具有明显算法亮点。
- **长时程预测**：直接针对序列传播负担与长时程预测难题设计。
- **可扩展性**：为大规模 Koopman 算子学习提供潜在可扩展路径。
- **同行认可**：ICML-2026 接收且评分 8.0，表明方法在评审层面获得一定认可。

### 8. 不足与局限
- **材料局限**：当前无论文正文，实验、算力、baseline、指标均无法验证。
- **实验覆盖未知**：无法判断是否覆盖多种非线性系统、高维场景、真实数据或强化学习任务。
- **偏差风险未知**：摘要与 TLDR 为作者自述，缺少消融、负结果和公平性细节。
- **潜在方法限制**：
  - 约束到给定李子代数可能依赖先验选择，并可能限制模型表达能力。
  - Magnus 展开的截断误差、高阶项处理和长时程误差累积未在现有材料中说明。
  - 前缀扫描的数值稳定性、并行实现开销和内存成本未讨论。
- **应用限制**：对高维、强非线性、真实复杂系统的泛化能力尚无法从当前材料判断。

（完）
