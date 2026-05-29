---
title: Neural Collapse is Globally Optimal in Deep Regularized ResNets and Transformers
title_zh: 神经坍缩在深度正则化ResNet和Transformer中是全局最优的
authors: "Peter Súkeník, Christoph H. Lampert, Marco Mondelli"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=8WKOk4U9R4"
tags: ["query:neural-arch"]
score: 4.0
evidence: 理论分析了深度正则化ResNet和Transformer中的神经坍缩现象
tldr: 本文对深度正则化ResNet和Transformer中神经坍缩现象进行了严格理论分析。证明了在交叉熵或均方误差损失下，全局最优解近似表现为神经坍缩，且随深度增加而更紧。该工作填补了现代架构（如残差网络和Transformer）在数据感知场景下缺乏理论分析的空白，为理解这些架构的表示特性提供了重要基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-8wkok4u9r4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1371, \"height\": 1327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8wkok4u9r4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 733, \"height\": 1574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-8wkok4u9r4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 727, \"height\": 528, \"label\": \"Figure\"}]"
motivation: 现有神经坍缩理论大多限于多层感知机，缺乏对现代架构的分析。
method: 通过理论推导，证明在数据感知场景下深度正则化ResNet和Transformer的全局最优解近似满足神经坍缩。
result: 证明随着深度增加，全局最优解与神经坍缩的近似程度越紧。
conclusion: 为现代架构中神经坍缩现象提供了理论依据，加深了对特征表示的理解。
---

## Abstract
The empirical emergence of neural collapse---a surprising symmetry in the feature representations of the training data in the penultimate layer of deep neural networks---has spurred a line of theoretical research aimed at its understanding. However, existing work focuses on data-agnostic models or, when data structure is taken into account, it remains limited to multi-layer perceptrons. Our paper fills both these gaps by analyzing modern architectures in data-aware regime: we prove that global optima of deep regularized transformers and residual networks (ResNets) with LayerNorm trained with cross entropy or mean squared error loss are approximately collapsed, and the approximation gets tighter as the depth grows. More generally, we formally reduce any end-to-end large-depth ResNet or transformer training into an equivalent unconstrained features model, thus justifying its wide use in the literature even beyond data-agnostic settings. Our theoretical results are supported by experiments on computer vision and language datasets showing that, as the depth grows, neural collapse indeed becomes more prominent.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：神经坍缩（Neural Collapse, NC）是一种在深度神经网络训练末期观测到的几何结构现象，表现为：同一类样本的特征向量汇聚到各自的类均值（NC1）；类均值构成等角紧框架（NC2）；类均值与最后一层权重矩阵的行对齐（NC3）。该现象在计算机视觉、语言模型等多个领域被广泛观测，对于理解泛化、表示学习、迁移学习等具有重要价值。然而，现有理论研究主要基于“无约束特征模型”（UFM）这一简化框架，或者仅针对多层感知机（MLP）进行端到端分析，缺乏对现代架构（如ResNet、Transformer）在考虑数据结构的真实场景下的分析。
- **核心问题**：本文旨在填补这一空白，**证明深度正则化的ResNet和Transformer（带LayerNorm）在交叉熵（CE）或均方误差（MSE）损失下的全局最优解近似满足神经坍缩，且随着深度增加，近似程度越紧**。此外，论文还建立深层ResNet/Transformer与无约束特征模型之间的形式化联系，为UFM在现代架构中的使用提供理论正当性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过将端到端训练问题转化为等价的无约束特征模型（GUFM），证明深层网络全局最优解收敛到GUFM的最优解，而后者已证明满足神经坍缩。具体分为两类架构分析：
  - **单线性层每块的架构（L-RN1, L-Tx1）**：正则化强度恒定，证明随层数L趋于无穷，全局最优解接近GUFM最优解，从而体现神经坍缩。证明关键在于构造性方法：通过将网络块分组，每组负责移动一个样本沿预设平滑轨迹逼近最优特征，且总正则化代价随L增大趋于0（例如，将大变化分摊到多个小权重层，实现代价O(1/L)）。
  - **双线性层每块的架构（L-RN2, L-Tx2）**：需要深度相关的正则化强度λ(L)=o(1/log L)（即随深度趋于零），因为双线性层中改变特征的成本与权重范数平方呈线性关系，而非平方关系，因此恒定正则化下无法使总代价趋于0。
- **关键技术细节**：
  - 定义广义无约束特征模型（GUFM）：在特征向量满足零均值、单位范数约束且同类样本特征相等（若数据中相同样本必然相同标签）的条件下，优化交叉熵或MSE损失加权重正则化。
  - 引理4.1：GUFM的近最优解必然接近最优解集。
  - 引理4.2：GUFM在CE和MSE损失下的全局最优解完全满足神经坍缩。
  - 定理4.3：对于L-RN1和L-Tx1，在恒定正则化下，深层网络全局最优解对应的最后层特征(WL, X^L)趋于GUFM最优解集，从而近似坍缩。
  - 定理4.6：对于L-RN2和L-Tx2，在深度相关衰减正则化下，也成立。
  - 证明利用残差网络的“分裂”特性：通过不断增加层数，将特征移动分解为许多小步，使总正则化代价收敛到0。

## 3. 实验设计

- **数据集**：MNIST（手写数字）、CIFAR10（彩色图像）、IMDB（电影评论情感分析，语言任务）。
- **架构**：
  - ResNet：L-RN1（每块单线性层）、L-RN2（每块双线性层）。
  - Transformer：L-T11（注意力和MLP均为单层）、L-T12（单层注意力+双层MLP）等，包括预层归一化（pre-LN）版本用于语言。
- **基准对比**：无对比方法，主要实验自身不同深度下神经坍缩指标的变化趋势。
- **设置**：深度L∈{2,3,5,8,13,21,34}，隐层维度64，学习率0.005（视觉）/0.001（语言），正则化强度：单层架构0.005恒定，双层架构0.005/L。每个设置5个不同随机种子，训练5000 epochs，报告均值与标准差。使用交叉熵损失。
- **评估指标**：NC1（类内/类间方差比）、NC2（权重矩阵到ETF的距离）、NC3（样本与最后一层权重行余弦相似度均值减1）。

## 4. 资源与算力

- **明确说明**：论文未具体说明使用的GPU型号、数量、训练总时长。只提到“实验需要适度计算资源”（modest computational resources）。因此无法给出具体算力消耗。
- **可能推测**：由于是标准小规模数据集（MNIST、CIFAR10、IMDB）和中等深度（最大34层），可认为在单块消费级GPU（如RTX 3090）上数小时内即可完成。

## 5. 实验数量与充分性

- **实验总量**：
  - 图1（主实验结果）：4个子图，分别对应L-RN1 on CIFAR10、L-T11 on CIFAR10、pre-LN L-T11 on IMDB、L-RN2 on MNIST。每个子图展示NC1、NC2、NC3随深度的变化，共约12条曲线。
  - 附录D：补充了MNIST上L-RN1、L-T11、L-RN2的结果（图2），以及总正则化损失随深度变化（图3）。
- **充分性评价**：
  - **优点**：覆盖了视觉和语言两种模态，ResNet和Transformer两类现代架构，单层和双层线性层变体，不同深度范围较广（2~34层），使用多个随机种子报告误差棒。
  - **不足**：
    - 理论假设要求数据满足特定条件（Assumption 4.4：ResNet样本唯一，Transformer上下文唯一确定标签），但实验中未验证这些条件是否严格满足（例如MNIST中可能有相同样本？但数据集通常无重复）。
    - 缺少与现有NC理论（如UFM、MLP结果）的直接比较。
    - 仅使用交叉熵损失，未验证MSE损失（理论同样覆盖）。
    - 消融实验有限：例如未对比不同正则化强度的影响（除了双层时γ∝1/L）。
    - 语言任务仅用IMDB，单一任务，代表性有限。

## 6. 论文的主要结论与发现

- **理论结论**：
  1. 在数据感知场景下，深度正则化ResNet和Transformer（单层或双线性层）的全局最优解满足近似神经坍缩，且随着深度增加，逼近程度更紧。
  2. 深层网络可以约化为等效的广义无约束特征模型（GUFM），因此UFM在现代架构分析中具有理论正当性。
  3. 对于双线性层架构，需要正则化强度随深度衰减（λ(L)=o(1/log L)）才能保证坍缩；若恒定正则化，则坍缩不会发生（附录C给出反例直观论证）。
- **实验结论**：
  - 在不同数据集和架构上，NC1、NC2、NC3指标均随深度增大而降低（即坍缩更明显），对数尺度下大致线性（斜率约-0.335），与理论预测的~O(L^{-1/2})收敛速度定性一致。
  - 双层架构在恒定正则化下NC指标不随深度改善（图2底部），支持理论预测。

## 7. 优点

- **理论贡献显著**：首次对现代架构（ResNet、Transformer）进行端到端神经坍缩全局最优性分析，填补了MLP以外的空白。
- **方法论精巧**：通过构造性证明将端到端问题约化为UFM，利用了残差网络“分裂”代价的特性（代价随深度反比缩放），技巧新颖。
- **理论覆盖广**：同时处理单层和双层每块的变体，以及CE和MSE两种损失，并对语言模型中的非确定性延续场景也提供讨论（使用定理4.3可推广）。
- **实验验证支持**：实验结果与理论定性一致，且发现线性趋势，增强了说服力。
- **对实践有指导意义**：提示从业者可通过增加深度来增强神经坍缩，从而提升下游性能（如迁移学习、OOD检测）。

## 8. 不足与局限

- **理论层面**：
  - 主要分析全局最优解，而非梯度下降学习动态；实际训练可能因优化困难而达不到全局最优。
  - 双线性层架构需正则化衰减，这在实际中通常不采用（常使用固定权重衰减），限制了直接应用。
  - 假设数据唯一性（Assumption 4.4）较强，在真实数据集上可能不完全满足（如图像增强产生的相同样本）。
  - 收敛速率仅给出定性估计（~O(L^{-1/2})），未给出精确界；且实验中的坡度-0.335对应L^{-0.335}，与理论估计有差异，需更多分析。
- **实验层面**：
  - 实验规模有限：仅3个数据集（其中IMDB为单一语言任务），且MNIST和CIFAR10较简单，未在更大规模（如ImageNet、现代LLM）上验证。
  - 仅使用交叉熵损失，未验证MSE损失下的神经坍缩指标（虽理论支持）。
  - 未与现有端到端神经坍缩理论（如Jacot et al., 2025）进行经验比较，也未报告UFM基准下的NC指标。
  - 一些架构（如L-T12、L-T22）未包含在实验中。
  - 预训练语言模型（如GPT-2）场景未测试，仅讨论了非确定性标签的理论。
- **可复现性**：论文未提供代码，仅描述足够详细（超参数、种子数），但未公布代码或数据预处理细节，可能影响精确复现。
- **偏差风险**：理论结果的渐近特性（L→∞）在实际有限深度下仅近似成立，实验显示深度3~34层，趋势明显但数值上NC指标并非极低（log10 NC1在约-0.2~-1.6之间），坍缩程度有限。

（完）
