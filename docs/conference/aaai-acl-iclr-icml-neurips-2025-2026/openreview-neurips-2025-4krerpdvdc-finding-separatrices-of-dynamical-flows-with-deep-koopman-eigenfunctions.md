---
title: Finding separatrices of dynamical flows with Deep Koopman Eigenfunctions
title_zh: 用深度Koopman特征函数寻找动力流的分离面
authors: "Kabir Vinay Dabholkar, Omri Barak"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4KRERpdVDC"
tags: ["query:koopman-rl"]
score: 8.0
evidence: 用深度Koopman特征函数刻画动力流
tldr: 许多自然系统是高维多稳态动力系统，现有分析工具多只描述平衡点附近行为，难以刻画划分吸引域边界的分离面。本文提出结合Koopman理论与深度神经网络的数值框架，近似在分离面上恰好为零的Koopman特征函数。利用这些标量特征函数，优化方法可高效刻画高维系统的分离面，为多稳态系统的全局结构分析提供了新工具。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 高维多稳态动力系统的分离面难以刻画，现有工具多只描述平衡点附近行为。
method: 结合Koopman理论与深度神经网络，近似在分离面上为零的Koopman特征函数。
result: 利用标量特征函数与优化方法高效刻画高维系统的分离面。
conclusion: 为多稳态系统的全局结构分析提供了数值工具。
---

## Abstract
Many natural systems, including neural circuits involved in decision making, are modeled as high-dimensional dynamical systems with multiple stable states. While existing analytical tools primarily describe behavior near stable equilibria, characterizing separatrices -- the manifolds that delineate boundaries between different basins of attraction -- remains challenging, particularly in high-dimensional settings. Here, we introduce a numerical framework leveraging Koopman Theory combined with Deep Neural Networks to effectively characterize separatrices. Specifically, we approximate Koopman Eigenfunctions (KEFs) associated with real positive eigenvalues, which vanish precisely at the separatrices. Utilizing these scalar KEFs, optimization methods efficiently locate separatrices even in complex systems. We demonstrate our approach on synthetic benchmarks, ecological network models, and high-dimensional recurrent neural networks trained on either neuroscience-inspired tasks or fit to real neural data. Moreover, we illustrate the practical utility of our method by designing optimal perturbations that can shift systems across separatrices, enabling predictions relevant to optogenetic stimulation experiments in neuroscience. Our code is available on [GitHub](https://github.com/KabirDabholkar/separatrixLocator), and we share an interactive description of the work and its extensions in a [UniReps blog](https://unireps.github.io/blog/2025/Separatrix-Locator/).

---

## 论文详细总结（自动生成）

> 说明：提供的 PDF 提取文本仅为 OpenReview 的 CAPTCHA 验证页，未包含论文正文。以下总结主要依据论文元数据、标题、作者、摘要与 TLDR 信息整理；凡正文可能包含但当前材料未出现的内容，均标注为“未说明”或“无法确认”。

## 1. 核心问题与整体含义

- **研究背景**：许多自然系统，尤其是参与决策的神经回路，可建模为**高维多稳态动力系统**，即存在多个稳定平衡点与不同吸引域。
- **核心问题**：现有分析工具多聚焦于稳定平衡点附近的局部行为，难以刻画**分离面**——划分不同吸引域边界的高维流形。
- **整体含义**：若能在高维系统中定位分离面，就能理解系统全局结构，并进一步设计扰动使系统从一个吸引域切换到另一个吸引域。
- **应用价值**：该问题与神经科学中的决策、生态网络稳定性、光遗传刺激等场景密切相关。

## 2. 方法论

- **核心思想**：结合 **Koopman 理论**与**深度神经网络**，近似 **Koopman 特征函数**，并利用其在分离面上的特殊取值来定位分离面。
- **关键观察**：与**实正特征值**相关联的 Koopman 特征函数，会在分离面上**恰好为零**。因此，分离面可被理解为这些标量特征函数的**零水平集**。
- **技术路线**：
  - 使用深度神经网络参数化或近似 Koopman 特征函数；
  - 关注具有实正特征值的特征函数，而非所有谱成分；
  - 得到标量 KEF 后，通过优化方法在状态空间中搜索其零水平集，从而高效刻画高维分离面；
  - 进一步利用这些特征函数设计**最优扰动**，使系统跨越分离面。
- **算法流程（据摘要概括）**：
  1. 给定动力系统或由其产生的轨迹数据；
  2. 用深度网络学习 Koopman 特征函数；
  3. 筛选/约束与实正特征值对应、且在分离面上为零的标量函数；
  4. 通过优化定位零水平集，得到分离面；
  5. 基于该几何信息设计扰动，实现吸引域切换。
- **细节限制**：具体损失函数、网络结构、训练目标、优化器、理论保证等，在提供的材料中**未说明**。

## 3. 实验设计

- **实验场景**：摘要提到三类主要场景：
  - **合成基准**动力系统；
  - **生态网络模型**；
  - **高维循环神经网络**，包括：
    - 在神经科学启发任务上训练的 RNN；
    - 拟合真实神经数据的 RNN。
- **Benchmark**：未明确说明具体 benchmark 名称、评价指标或标准数据集。
- **对比方法**：摘要未提及与哪些基线方法进行比较，例如传统数值延拓、谱方法、线性化分析等，因此无法确认对比设置。
- **应用展示**：通过设计最优扰动使系统跨越分离面，展示其对**光遗传刺激实验**的预测价值。
- **代码与交互材料**：代码公开于 GitHub，并有 UniReps 博客交互说明。

## 4. 资源与算力

- 提供的材料中**未说明**使用的 GPU 型号、数量、训练时长、参数量、内存或总算力。
- 因此无法评估该方法的计算成本、可扩展性与复现所需资源。

## 5. 实验数量与充分性

- 从摘要可知，实验至少覆盖**合成基准、生态网络、高维 RNN**等若干场景，说明作者尝试验证方法的跨领域适用性。
- 但具体做了多少组实验、涉及多少数据集、是否有消融实验、随机种子数量、统计显著性检验等，均**未说明**。
- 由于缺少基线、评价指标和实验表格，当前材料**不足以判断实验是否充分、客观、公平**。
- 总体看，实验设计在应用覆盖面上较广，但可验证性依赖论文正文。

## 6. 主要结论与发现

- 与实正特征值相关的 Koopman 特征函数可用于刻画分离面，因为它们在分离面上为零。
- 结合深度神经网络与优化方法，可以较高效地定位高维系统中的分离面。
- 该方法在合成系统、生态模型和神经 RNN 上均被展示为可行。
- 基于 KEF 可设计最优扰动，使系统跨越分离面，从而为光遗传刺激等干预实验提供预测工具。
- 该工作为多稳态动力系统的**全局结构分析**提供了新的数值框架。

## 7. 优点

- **理论联系新颖**：将 Koopman 谱理论与分离面几何联系起来，利用实正特征值对应的特征函数刻画边界。
- **方法简洁有潜力**：将高维分离面问题转化为标量 KEF 的零水平集搜索，便于使用优化方法。
- **应用场景丰富**：覆盖合成系统、生态网络、神经科学任务与真实神经数据，并延伸到光遗传扰动设计。
- **可复现性较好**：公开代码，并提供交互式博客说明。
- **问题重要**：高维多稳态系统的分离面刻画是动力系统与计算神经科学中的难点。

## 8. 不足与局限

- **材料限制**：当前 PDF 提取失败，无法核实正文中的公式、算法细节、实验表格和附录。
- **算力与复现细节缺失**：未说明 GPU、训练时长、超参数和计算成本。
- **实验公平性未知**：未说明基线方法、评价指标、消融实验和统计检验，难以判断方法相对优势。
- **理论假设较强**：依赖 Koopman 特征函数存在性、实正特征值对应关系以及深度网络近似精度。
- **高维可扩展性待验证**：虽然声称适用于高维系统，但未提供复杂度、稳定性和失败案例分析。
- **优化风险**：零水平集搜索可能受非凸性、局部极小值和数值误差影响。
- **应用限制**：光遗传刺激预测仍需真实实验验证；对噪声、时变系统或非多稳态系统的适用性未说明。

（完）
