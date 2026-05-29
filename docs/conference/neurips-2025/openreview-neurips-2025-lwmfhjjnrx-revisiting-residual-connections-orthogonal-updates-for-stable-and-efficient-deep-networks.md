---
title: "Revisiting Residual Connections: Orthogonal Updates for Stable and Efficient Deep Networks"
title_zh: 重新审视残差连接：正交更新实现稳定高效的深层网络
authors: "Giyeong Oh, Woohyun Cho, Siyeol Kim, Suhwan Choi, Youngjae Yu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=LWmfHjJnrx"
tags: ["query:neural-arch"]
score: 9.0
evidence: 对残差连接进行正交更新改进
tldr: 本文重新审视残差连接，提出正交残差更新方法：将模块输出相对于输入流分解，仅添加正交分量。该设计鼓励模块学习全新表示方向，避免特征重复，从而提升训练效率和模型表现。实验证明该方法在深层网络中更稳定，学习到更丰富的特征。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1313, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1336, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1453, \"height\": 860, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 916, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1040, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1446, \"height\": 875, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1433, \"height\": 488, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1436, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1459, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1448, \"height\": 864, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1436, \"height\": 1313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lwmfhjjnrx/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1428, \"height\": 1090, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 732, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 563, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1200, \"height\": 800, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 930, \"height\": 328, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 979, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 979, \"height\": 524, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 746, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1432, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1181, \"height\": 785, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1127, \"height\": 786, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 949, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 872, \"height\": 780, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 742, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lwmfhjjnrx/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1297, \"height\": 769, \"label\": \"Table\"}]"
motivation: 标准残差更新可能使模块输出过于强化现有方向，限制学习新特征的能力。
method: 将模块输出分解为相对于输入流的平行和正交分量，仅加入正交分量。
result: 正交更新促进新特征学习，训练更稳定高效，在图像分类等任务上表现更好。
conclusion: 为残差网络提供了一种改进更新策略，可推广至多种架构。
---

## Abstract
Residual connections are pivotal for deep neural networks, enabling greater depth by mitigating vanishing gradients. However, in standard residual updates, the module’s output is directly added to the input stream. This can lead to updates that predominantly reinforce or modulate the existing stream direction, potentially underutilizing the module’s capacity for learning entirely novel features. In this work, we introduce _Orthogonal Residual Update_: we decompose the module’s output relative to the input stream and add only the component orthogonal to this stream. This design aims to guide modules to contribute primarily new representa-tional directions, fostering richer feature learning while promoting more efficient training. We demonstrate that our orthogonal update strategy improves generalization accuracy and training stability across diverse architectures (ResNetV2, Vision Transformers) and datasets (CIFARs, TinyImageNet, ImageNet-1k), achieving, for instance, a +3.78 pp Acc@1 gain for ViT-B on ImageNet-1k. Code and models are available at https://github.com/BootsofLagrangian/ortho-residual.

---

## 论文详细总结（自动生成）

# 论文总结：Revisiting Residual Connections: Orthogonal Updates for Stable and Efficient Deep Networks

## 1. 核心问题与整体含义（研究动机与背景）
- **研究动机**：标准残差连接（Residual Connection）中，模块输出直接加到输入流上，导致更新主要强化或调节已有方向，可能抑制模块学习全新特征的能力，造成容量浪费。
- **核心问题**：如何让残差模块更有效地贡献新表示方向，而非重复调制现有流方向。
- **整体含义**：提出一种简单而原则性的修改——正交残差更新（Orthogonal Residual Update），仅添加模块输出中与输入流正交的分量，从而促进特征多样性、提升训练稳定性与泛化能力。

## 2. 方法论
- **核心思想**：将模块输出 \( f(\sigma(x_n)) \) 相对于输入流 \( x_n \) 分解为平行分量 \( f_\parallel \) 和正交分量 \( f_\perp \)，然后仅将正交分量 \( f_\perp(x_n) \) 加回输入流，即：
  \[
  x_{n+1} = x_n + f_\perp(x_n), \quad f_\perp(x_n) = f(\sigma(x_n)) - s_n x_n
  \]
  其中 \( s_n = \frac{\langle x_n, f(\sigma(x_n)) \rangle}{\|x_n\|^2 + \epsilon} \)，\(\epsilon\) 为数值稳定性常数。
- **关键技术细节**：
  - 投影操作基于 Gram-Schmidt 过程，计算简单，仅需点积和缩放。
  - 提供两种变体：**特征维度正交化（Feature-wise）**：沿特征通道（Transformer 的 d 或 CNN 的 C）独立计算；**全局正交化（Global）**：沿所有非批维度展平后计算，适用于 CNN。
  - 保持身份路径（Identity Path）不变，梯度流不受阻碍。
  - 算法流程：计算点积 → 计算缩放因子 → 减去平行分量 → 加回正交分量。
- **理论保证**：
  - 从微分几何角度，近似于流形上的指数映射的一阶近似。
  - 从神经 ODE 视角，正交更新可抑制流范数的径向变化，使流保持在近似常范数状态。

## 3. 实验设计
- **数据集**：CIFAR-10/100（32×32）、TinyImageNet（64×64, 200类）、ImageNet-1k（224×224, 1000类）。
- **架构**：ResNetV2（-18, -34, -50, -101）和 Vision Transformer（ViT-S, ViT-B）。
- **基准方法**：标准线性残差连接（Linear Residual Update）作为基线。
- **对比方法**：
  - Orthogonal-F（特征维度正交化）
  - Orthogonal-G（全局正交化，仅用于CNN）
  - 额外消融：学习率扫描、连接类型切换、正交概率π、层模式、稳定性常数ε、初始化方法、统一残差族(ρ,θ)等。
- **评估指标**：Top-1/5验证准确率（Acc@1/Acc@5），有效秩、谱熵、CKA相似度、特征标准差等表征指标。

## 4. 资源与算力
- **ImageNet-1k**：
  - ViT-B：8× NVIDIA L40S GPU，约42小时
  - ViT-S：8× NVIDIA L40S GPU，约15小时
- **CIFAR/TinyImageNet（ViT）**：
  - ViT-B：2× NVIDIA H100，约1-2小时
  - ViT-S：8× NVIDIA RTX 3090，约1-2小时
- **ResNetV2**：4× NVIDIA RTX 3090，例如ResNetV2-34 on CIFAR-10约18小时。
- 所有训练均采用标准超参数（详见附录A）。

## 5. 实验数量与充分性
- **实验数量**：非常充分。涵盖4个数据集、7种架构（ViT-S/B, ResNetV2-18/34/50/101），每个设置5次独立运行（ImageNet-1k未给出次数，但主表及内部动态图均含标准差）。
- **消融实验**：
  - 学习率鲁棒性（5个LR × 2数据集）
  - 连接类型切换（有/无优化器重置，2种方向 × 3数据集）
  - 正交概率π（从0到1，4个间隔）
  - 正交层模式（7种组合）
  - 稳定性常数ε（6个数量级）
  - 初始化方法（3种）
  - 统一残差族（2种起点）
- **公平性**：所有实验使用相同超参数、数据增强，对比基线一致；报告均值±标准差，统计显著。
- **结论**：实验充分、客观、公平，系统验证了方法的有效性和鲁棒性。

## 6. 主要结论与发现
- **性能提升**：正交更新在几乎所有设置下优于线性基线。例如，ViT-B在ImageNet-1k上Acc@1提升+3.78 pp。
- **收敛加速**：训练损失下降更快，验证精度在更少迭代内达到更高水平。
- **训练稳定性**：正交更新稳定了流范数，避免了线性残差中出现的平行分量抑制和流范数衰减。
- **表征改进**：有效秩和谱熵增加（频谱更均匀），特征标准差降低（更稳定），CKA显示与基线有结构性差异。
- **连接类型切换实验**：早期应用正交更新效果最好，后期可切换为线性更新进一步精炼。
- **概率与层模式**：更多层使用正交更新或更高概率均带来正向收益。

## 7. 优点
- **方法简洁高效**：仅需额外计算点积和缩放，FLOPs增加可忽略（≤2% for ViT, 3-13% for ResNetV2），易于集成。
- **理论支撑**：从几何、ODE、梯度路径三个角度提供解释，动机清晰。
- **实验全面**：覆盖多种架构、数据集、消融实验，含多次重复与统计检验。
- **表征分析**：提供有效秩、谱熵、CKA等内部状态分析，揭示机制。
- **实用价值**：可直接替换现有残差连接，无额外超参数（除稳定性常数ϵ，默认1e-6鲁棒）。
- **开源代码**：提供完整实现。

## 8. 不足与局限
- **实验规模限制**：仅测试到ViT-B和ImageNet-1k，未在更大模型（如ViT-L/H）或更大规模数据集（如JFT、LLM）上验证。
- **架构覆盖有限**：未评估ResNetV2在ImageNet-1k上的表现（因计算限制）；未测试更深的ResNet-152等。
- **理论深度有限**：缺乏严格的理论保证说明“何时/为何”正交更新优于线性更新；长期训练稳定性未深入分析。
- **适用场景局限**：仅聚焦图像分类，未在分割、检测、生成、序列建模等任务上验证。
- **潜在偏差**：正交更新可能对特定宽度/深度比（γ）敏感，但文中仅给出初步对比。
- **数值稳定性**：ϵ为1e-6，但ϵ过小可能导致除法不稳定，过大则偏离正交性；文中未探讨动态调整。

（完）
