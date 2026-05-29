---
title: "Energy Landscape-Aware Vision Transformers: Layerwise Dynamics and Adaptive Task-Specific Training via Hopfield States"
title_zh: 能量景观感知的Vision Transformer：通过Hopfield状态的层动态与自适应任务特定训练
authors: "Runze Xia, Richard Jiang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Z6aBp0AJI1"
tags: ["query:neural-arch"]
score: 7.0
evidence: 提出基于层动态的自适应训练方法优化ViT效率
tldr: 本文从能量记忆系统视角分析Vision Transformer的层动态，发现某些层会收敛到吸引子状态，表明功能专门化和早期稳定化。基于此，提出层不稳定指数（LII）来量化每层的不稳定性，并开发自适应任务特定训练策略，仅训练不稳定的层，从而大幅降低计算开销。在多个视觉任务上验证了该方法的效率提升。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-z6abp0aji1/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1416, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-z6abp0aji1/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1432, \"height\": 494, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-z6abp0aji1/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 687, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z6abp0aji1/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1457, \"height\": 495, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z6abp0aji1/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1371, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-z6abp0aji1/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 439, \"label\": \"Table\"}]"
motivation: ViT深层均匀结构导致计算开销大，而层动态存在差异。
method: 引入层不稳定指数（LII），识别稳定层，仅训练不稳定层以降低计算量。
result: 在多个视觉任务上显著降低训练成本，同时保持精度。
conclusion: 利用层动态特性可有效优化ViT的训练效率。
---

## Abstract
Recent advances in Vision Transformers (ViTs) have shown remarkable performance across vision tasks, yet their deep, uniform layer structure introduces significant computational overhead. In this work, we explore the emergent dynamics of ViT layers through the lens of energy-based memory systems, drawing a connection between self-attention and modern Hopfield networks. We introduce a novel metric—Layer Instability Index (LII)—derived from the operational softmax mode and its variability, to quantify the metastability of each Transformer layer over time. Our analysis reveals that certain layers exhibit consistent convergence to attractor-like states, suggesting functional specialisation and early stabilisation. Leveraging this insight, we propose an adaptive training framework that dynamically freezes or skips stable layers based on their energy landscape behavior. Our method reduces training costs while maintaining or improving accuracy. Extensive experiments on ViT-S/B/L on CUB-200-2011, CIFAR-10/100, Food-101, Stanford Dogs, and Beans demonstrate the generality and efficiency of our approach. This work provides new theoretical and practical perspectives for energy-aware optimisation of deep Transformer models.

---

## 论文详细总结（自动生成）

## 论文总结：Energy Landscape-Aware Vision Transformers

### 1. 核心问题与整体含义（研究动机和背景）
- **问题**：Vision Transformers（ViTs）在视觉任务上表现优异，但其深层均匀结构导致巨大的计算开销。现有效率优化方法（如令牌剪枝、早期退出、参数高效微调）均未利用层间的内部收敛行为差异，即某些层会迅速稳定（收敛到吸引子状态），而其他层仍保持自适应。
- **背景**：自注意力机制可视为现代 Hopfield 网络的能量最小化过程，提供理解层动态的理论框架。作者旨在将这一理论洞察转化为实际效率优化，通过识别并冻结稳定层，减少训练和推理成本。

### 2. 方法论：核心思想、关键技术细节
- **核心思想**：提出**层不稳定指数（Layer Instability Index, LII）**，量化每层注意力分布随输入的变异性。低 LII 层处于能量景观的平坦盆地，可安全冻结；高 LII 层则需继续训练。
- **关键定义 – 操作模式（Operational Mode）**：对于每层 ℓ 和每个注意力头，计算需要累积 90% 注意力质量的最小令牌数 `¯k_ℓ`。该值反映注意力低能盆的宽度（小值表示注意力集中）。
- **LII 计算**：在滑动窗口（默认 ∆=20 个 batch）内，对 `¯k` 序列计算**中位数绝对偏差（MAD）**，即 `LII_ℓ = median_t |¯k_ℓ^t – median_{t'}(¯k_ℓ^{t'})|`。
- **理论支撑**：
  - **能量间隙上界**：证明 LII 线性上界期望的 Hopfield 能量间隙（Lemma 1）。
  - **Fisher 信息迹上界**：低 LII 层对应 Fisher 平坦，冻结不会损害泛化。
  - **与 1-Wasserstein 距离关联**：低 LII 意味注意力的 earth-mover 距离小。
- **训练流程（三阶段）**：
  1. **预热阶段**（前 T 步，T≈3∆）：所有层可训练，累积每层的 LII。
  2. **冻结决策**（一步式）：若 `LII_ℓ < τ_freeze`，冻结该层（`requires_grad=False`）。
  3. **巩固阶段**：仅训练未冻结层，无额外 LII 开销。
- **优势**：无需引入任何额外参数（门控网络、适配器等），直接利用现有注意力分数。

### 3. 实验设计
- **数据集**：
  - 主实验：CUB-200-2011, Stanford Dogs, NABirds, Beans, CIFAR-10/100, Food-101。
  - 大规模验证：ImageNet-1K。
- **模型**：ViT-S/16, ViT-B/16, ViT-L/16；额外使用 DeiT-B 和 ALaST 的对比实验。
- **对比方法**：
  - 全微调（Baseline）
  - 自适应层选择 ALaST（对比实验）
  - 不同冻结比例（ELA-ViT-25%, 35%, 45%, 50%, 75%）
- **评估指标**：Top-1 准确率、微调时间（分钟/小时）、冻结参数比例。
- **超参数**：AdamW 优化器，余弦退火学习率，batch size 32。不同模型采用不同学习率和权重衰减。

### 4. 资源与算力
- **硬件**：单张 NVIDIA V100 GPU，50 GB 显存。
- **软件**：PyTorch，基于 HuggingFace ViT 实现。
- **训练时间**（文中报告）：
  - 全微调 ViT-B on ImageNet-1K 需 43.45 小时；ELA-ViT-50% 降至 38.81 小时（–10.7%）。
  - 对 CIFAR-100 等较小数据集，时间节省约 9–14%。
- **未明确的信息**：未说明具体使用的 GPU 数量（从描述看为单卡），也未详细说明推理阶段的 latency 测试环境。

### 5. 实验数量与充分性
- **实验数量**：覆盖 5 个标准分类数据集 + 2 个额外数据集（Food-101, CIFAR-100）。使用 3 种 ViT 骨干（S/B/L），并额外测试 DeiT 和 ALaST 对比。包含 ImageNet-1K 大规模实验。
- **充分性**：
  - 完整报告了准确率、训练时间、冻结比例。
  - 进行了消融：不同冻结比例下的精度-时间 Pareto 曲线。
  - 与当前最先进的层预算学习 ALaST 进行了公平对比（相同训练协议）。
  - 提供了层间 LII 可视化（U 型曲线），验证方法的可解释性。
- **客观性与公平性**：实验设置详实，对比基准一致。但论文提到“平均 3 个种子”，未在正文中给出误差棒（在 Checklist 中解释为不适用于此场景，但若能提供标准差会更严谨）。

### 6. 主要结论与发现
- **层不稳定模式**：浅层（如第 3–4 层）LII 最低，优先稳定；深层（7–11 层）LII 高，仍需自适应。该 U 型曲线跨数据集保持一致。
- **效率提升**：ELA-ViT 可冻结 40–70% 参数，训练时间减少最多 12.2%（ViT-L on CUB），同时保持或提升准确率。
- **准确率改善**：在细粒度数据集（CUB, Stanford Dogs）上，冻结稳定层反而提升泛化（最高 +6.9 pp）。
- **与 ALaST 对比**：ELA-ViT 以更少的时间节省（9–14% vs 19–39%）实现了准确率提升或维持，而 ALaST 在 75% 冻结预算下准确率显著下降（高达 –11.6 pp）。ELA-ViT 的冻结决策更优，因为其基于能量动力学而非随机学习预算。
- **可扩展性**：在 ImageNet-1K 上，ELA-ViT-50% 仅损失 0.61 pp 准确率，训练时间降低 10.7%，推理延迟降低 16.7%。

### 7. 优点
- **理论深度**：将自注意力重新解释为 Hopfield 能量最小化，并证明 LII 与能量间隙、Fisher 信息迹的定量关系，为层冻结提供坚实理论依据。
- **无参数开销**：LII 直接从前向传播的注意力分数计算，不引入额外门控、适配器或损失项，实现零参数增加的效率优化。
- **与现有方法正交**：可轻松与 LoRA、条件适配器等 PEFT 方法结合，进一步推动计算-精度 Pareto 前沿。
- **可解释性**：LII 曲线揭示 ViT 层功能的自然分化，有助于理解模型内部动态。
- **实验覆盖广**：在多种规模、多种数据集上验证，并提供了大规模 ImageNet-1K 结果。

### 8. 不足与局限
- **指标代理风险**：LII 基于注意力集中度（操作模式），可能不完全反映表示稳定性。对于某些任务，注意力分布变化小而权重变化大，LII 可能低估层的不稳定性。
- **预热阶段 overhead**：需要积累 3×W 步（约 60 个 batch）来估计 LII，在资源极低场景下可能引入延迟。
- **小模型欠拟合**：在 ViT-S 上对 Beans 和 CIFAR-10 出现精度下降（–1.6 和 –1.7 pp），说明冻结策略可能过度正则化容量不足的模型。
- **实验未覆盖多模态或 LLM**：论文仅展望了扩展到其他模态的可能性，但未提供实验验证。
- **冻结决策一次性**：虽然可选重新评估，但默认策略仅做一次冻结决定，可能错过后期稳定化层（论文声称一次已够，但未系统分析动态重新评估的影响）。
- **未提供统计误差**：尽管声称平均 3 种子，但未报告标准差或置信区间，难以评估结果的稳定性。

（完）
