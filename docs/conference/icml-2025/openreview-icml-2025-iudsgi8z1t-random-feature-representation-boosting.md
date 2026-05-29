---
title: Random Feature Representation Boosting
title_zh: 随机特征表示提升
authors: "Nikita Zozoulenko, Thomas Cass, Lukas Gonon"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=iUDsgI8z1T"
tags: ["query:neural-arch"]
score: 7.0
evidence: 通过Boosting构建的新型深度残差随机特征网络
tldr: 针对随机特征神经网络（RFNN）性能受限的问题，本文提出随机特征表示提升（RFRBoost）方法。利用Boosting理论逐层学习网络表示的梯度，将残差块的拟合转化为约束二次规划问题。在表格数据回归与分类任务上，RFRBoost显著超越传统RFNN和端到端训练方法，且保留了凸优化的优势。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 811, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 245, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1493, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1570, \"height\": 943, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1218, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1227, \"height\": 1835, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1655, \"height\": 1648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-iudsgi8z1t/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1660, \"height\": 1629, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 406, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 811, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 766, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1782, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1780, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1786, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1235, \"height\": 1022, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1348, \"height\": 1358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1351, \"height\": 1398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1756, \"height\": 1407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1201, \"height\": 731, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1219, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1208, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-iudsgi8z1t/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1272, \"height\": 782, \"label\": \"Table\"}]"
motivation: RFNN性能有限，本文希望结合残差连接和Boosting提升其表达能力和性能。
method: 每层使用随机特征学习表示的函数梯度，将残差块拟合建模为带约束的最小二乘问题。
result: 在多种表格数据集上取得了比RFNN和端到端训练更好的性能。
conclusion: 提出了一种构建深度残差随机特征网络的有效框架，兼具凸优化和Boosting的优势。
---

## Abstract
We introduce Random Feature Representation Boosting (RFRBoost), a novel method for constructing deep residual random feature neural networks (RFNNs) using boosting theory. RFRBoost uses random features at each layer to learn the functional gradient of the network representation, enhancing performance while preserving the convex optimization benefits of RFNNs. In the case of MSE loss, we obtain closed-form solutions to greedy layer-wise boosting with random features. For general loss functions, we show that fitting random feature residual blocks reduces to solving a quadratically constrained least squares problem. Through extensive numerical experiments on tabular datasets for both regression and classification, we show that RFRBoost significantly outperforms RFNNs and end-to-end trained MLP ResNets in the small- to medium-scale regime where RFNNs are typically applied. Moreover, RFRBoost offers substantial computational benefits, and theoretical guarantees stemming from boosting theory.

---

## 论文详细总结（自动生成）

# 随机特征表示提升（Random Feature Representation Boosting）论文详细总结

## 1. 核心问题与研究动机

- **背景**：随机特征神经网络（RFNN）仅训练顶层线性层，避免了非凸优化和梯度消失问题，计算高效且具有泛化保证。但将其扩展到深度残差网络时存在困境：简单堆叠随机特征层可能导致性能退化——若残差块幅度太小则初始表示主导，若太大则丢失前层信息。
- **核心问题**：如何构建深度残差RFNN，使其既能利用深度提升表达能力，又不破坏凸优化优势？传统端到端训练的ResNet通过SGD调整权重学习适当表示，而RFNN因隐藏层固定而缺乏这一机制。
- **解决方案思路**：利用Boosting理论，让每层随机特征去学习网络表示的函数梯度（functional gradient），从而得到最优的残差块映射。

## 2. 方法论

### 核心思想
- **梯度表示提升（Gradient Representation Boosting）**：将ResNet视为网络表示$\Phi_t$的加法更新：$\Phi_t = \Phi_{t-1} + \eta A_t f_t$，其中$f_t$为随机特征，$A_t$为线性映射。通过拟合负函数梯度来学习$A_t$，使残差块在该方向更新表示。
- **两种策略**：
  - **Exact-Greedy（精确贪婪）**：直接最小化包含顶层线性层的整体风险，得到残差块的最优解。适用于MSE损失，可推导闭式解。
  - **Gradient-Greedy（梯度贪婪）**：对任意可微损失，利用一阶泰勒展开，在约束条件$\|g\|_{L^2(\hat\mu)}=1$下最大化内积。等价于求解二次约束最小二乘问题。

### 关键技术细节
1. **Sandwiched Least Squares问题**（MSE损失）：求解$A_t$使$\frac{1}{n}\sum_i \|r_i - W_{t-1}^\top A f_t(x_i)\|^2$最小化。文中给出了标量、对角、稠密三种情形下$A$的闭式解（Theorem 3.1），通过谱分解等方法实现高效计算。
2. **一般损失下的梯度拟合**（Theorem 3.2）：将内积最大化解转化为约束最小二乘，得到$A = \frac{\sqrt{n}}{\|G\|_F} G^\top F (F^\top F)^{-1}$（当$F$满秩时），其中$G$为函数梯度矩阵，$F$为特征矩阵。
3. **算法流程**：
   - 初始化表示$\Phi_0$和顶层线性头$W_0$。
   - 每层：生成随机特征$f_t$（可依赖输入$x$和前层输出$\Phi_{t-1}$）；计算残差（MSE）或函数梯度（一般损失）；求解$A_t$（闭式解或最小二乘）；线搜索学习率$\alpha_t$；更新表示$\Phi_t = \Phi_{t-1} + \eta\alpha_t A_t f_t$；更新顶层线性头$W_t$（通过最小二乘或凸优化）。
4. **理论保证**：在样本分割设置下，给出了基于Rademacher复杂度的遗憾界（Theorem 3.4），依赖于弱学习条件$(\beta,\epsilon)$。

## 3. 实验设计

### 数据集与场景
- **主实验**：OpenML curated tabular regression（Fischer et al., 2023）和classification（Bischl et al., 2021）benchmark，共**91个数据集**（34个回归+57个分类），限制最多5000样本。预处理：独热编码+数值特征标准化。
- **额外实验**：
  - 合成点云分离任务：同心圆分类，10000个点，隐藏维度限制为2。
  - 大规模实验：4个数据集（OpenML ID 23517分类、44975回归，CoverType分类、YearPredictionMSD回归），训练规模从2^11到~500k样本。

### 评估方式
- 主实验：嵌套5折交叉验证，内层用Optuna进行100次贝叶斯超参数调优，外层报告平均测试指标。
- 统计方法：Critical Difference diagram（Wilcoxon signed-rank test with Holm correction, $\alpha=0.05$）。
- 点云任务：5折交叉验证网格搜索，重复10次报告均值与标准差。
- 大规模实验：固定验证集网格搜索，指数增长训练子集，重复5次。

### 对比方法
- **基线**：Ridge/Logistic Regression、RFNN（单层随机特征）、E2E MLP ResNet（Adam优化，余弦退火）、XGBoost。
- **RFRBoost变体**：标量/对角/稠密$A$（回归），梯度贪婪版（分类）。
- 随机特征：默认使用SWIM初始化，并与i.i.d.高斯对比（消融）。

## 4. 资源与算力

- 主实验：**单CPU核**（AMD EPYC 7742节点）上运行，未使用GPU。
- 点云任务：未明确说明，推测CPU。
- 大规模实验：**单张NVIDIA RTX 6000 GPU**（Turing架构）。
- 训练时间（均值）：
  - 回归：RFRBoost梯度版1.688s，稠密贪婪版2.734s，E2E ResNet 19.309s，XGBoost 1.958s，RFNN 0.053s。
  - 分类：RFRBoost 2.519s，E2E ResNet 20.881s，XGBoost 3.859s，RFNN 1.189s。
- 论文未说明总的训练时长（如全部实验累积GPU/CPU小时数），仅给出单次拟合时间。

## 5. 实验数量与充分性

- **实验数量**：91个数据集×5折×（100 trials/折）的调优，加上点云任务（10次重复×5折）和大规模实验（4数据集×5次重复×多子集），总计实验量庞大。
- **公平性**：所有方法使用相同的数据预处理、评价流程、调优次数（100 trials），超参数范围合理。随机特征模型均使用SWIM（与i.i.d.比较时单独控制变量）。统计检验方法标准（CD图）。
- **充分性**：
  - 覆盖了表格数据的回归和分类常见任务。
  - 消融研究：SWIM vs i.i.d.随机特征（结论：性能接近但SWIM略有优势）。
  - 不同$A$形式的比较（标量<对角<稠密）。
  - 大规模扩展分析（但仅4个数据集）。
  - **局限**：未涵盖图像、时间序列、自然语言等领域；未与更多深度RFNN方法对比（如Fourier RFNN深度版）；超参数搜索次数（100 trials）对于深度模型可能不够充分。

## 6. 主要结论与发现

1. **RFRBoost在表格数据上显著优于单层RFNN和E2E MLP ResNet**，同时训练速度快1~10倍。
2. **与XGBoost相比**：回归中XGBoost RMSE略低但平均排名更低；分类中两者准确率相同但RFRBoost排名更高。CD图显示RFRBoost与XGBoost无显著差异且为第一梯队。
3. **精确贪婪 vs 梯度贪婪**：对于MSE损失，梯度贪婪版（加入$L^2$范数约束）优于精确贪婪版，与既往SGD训练中的观察相反，归因于范数约束保留了梯度的方向。
4. **稠密$A$优于对角和标量**：表明学习完整的线性映射比简单缩放更有效。
5. **点云分离任务**：RFRBoost达到近乎完美分离（99.7%），而E2E ResNet和RFNN失败（分别为73.2%和88.7%），展示了深度表示提升的威力。
6. **大规模实验中**：RFRBoost始终优于RFNN；但在最大训练规模下，E2E网络和XGBoost在3/4和2/4数据集上反超。作者建议未来将RFRBoost作为预训练初始化。

## 7. 优点

- **方法创新**：将Boosting理论与随机特征相结合，克服了深度RFNN的表示退化问题，同时保留凸优化性质。
- **闭式解与高效性**：MSE损失下获得sandwiched LS的解析解（Theorem 3.1），计算时间复杂度为$O(T[N(D^2+Dd+p^2+pD)+D^3+dD^2+p^3+Dp^2])$，在CPU上即比E2E ResNet快一个数量级。
- **理论保证**：给出遗憾界（Theorem 3.4），基于Radmacher复杂度和弱学习条件，为算法提供了严谨的理论支撑。
- **全面的实验**：91个数据集+统计检验，结果可靠；包含消融、不同$A$形式、大规模扩展。
- **兼容多种随机特征**：除SWIM外，支持任意随机特征层（如i.i.d.、Fourier等）。

## 8. 不足与局限

- **应用范围有限**：实验仅覆盖表格数据（回归/分类），未在图像（如CIFAR、ImageNet）、时间序列、自然语言等主流深度学习场景上验证。
- **大规模场景下性能天花板**：在~500k样本的CoverType和YPMSD上，E2E网络和XGBoost超越RFRBoost，说明深度RFNN在极大数据量下可能不如可训练的全参数模型。
- **超参数调优深度有限**：每折仅100次Optuna trials，对于具有多个超参数的模型（如层数、正则化、学习率、SWIM scale）可能未彻底探索最优配置。
- **随机特征依赖**：主实验采用SWIM随机特征，虽然进行了i.i.d.对比，但SWIM需要计算样本对距离和梯度，增加了预处理开销和实现复杂度，且性能优势不明显。
- **未探索动量或自适应步长**：当前算法使用固定学习率$\eta$和线搜索，未结合动量、AdaGrad等优化技巧，可能限制收敛速度。
- **潜在偏差**：数据集限制最多5000样本，部分数据集较小，结论可能不适用于超大规模但特征维度高的场景（如文本Embedding）。
- **理论假设较强**：遗憾界依赖于弱学习条件（$(\beta,\epsilon)$）和样本分割，在实际中$G_t$满足该条件可能不易保证，且$\beta$未知。

（完）
