---
title: "EUGens: Efficient, Unified and General Dense Layers"
title_zh: EUGens：高效、统一和通用的密集层
authors: "Sang Min Kim, Byeongchan Kim, Arijit Sehanobish, Somnath Basu Roy Chowdhury, Rahul Kidambi, Dongseok Shim, Kumar Avinava Dubey, Snigdha Chaturvedi, Min-hwan Oh, Krzysztof Marcin Choromanski"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=tIR9Naukr3"
tags: ["query:neural-arch"]
score: 8.0
evidence: 提出高效统一的全连接层，降低推理复杂度
tldr: 本文提出EUGens（高效、统一和通用的密集层），通过随机特征逼近标准全连接层并引入输入范数依赖，在降低推理复杂度的同时统一现有高效全连接层扩展。该方法从理论上统一了多种效率优化技术，并在实际部署中显著减少计算和参数瓶颈，适用于资源受限环境。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1290, \"height\": 570, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1332, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1413, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1400, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1414, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1409, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1409, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1392, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 758, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1449, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 796, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1394, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1342, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1369, \"height\": 2166, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 591, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1361, \"height\": 1716, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1419, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1293, \"height\": 1940, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1427, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1437, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1326, \"height\": 307, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1357, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1409, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1384, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1426, \"height\": 1194, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1423, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1384, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1434, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1420, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 849, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tir9naukr3/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 1419, \"height\": 295, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1433, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1504, \"height\": 500, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 950, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1120, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1132, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1451, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1317, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 900, \"height\": 182, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1300, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 955, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1133, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tir9naukr3/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 837, \"height\": 415, \"label\": \"Table\"}]"
motivation: 全连接层是神经网络中的计算和参数瓶颈，现有高效扩展缺乏统一框架。
method: 利用随机特征和输入范数依赖，设计新的密集层函数，统一并扩展现有高效FFL。
result: 降低了推理复杂度，并在多个任务上保持或提升性能。
conclusion: EUGens为高效密集层提供了统一视角，适用于实时和资源受限应用。
---

## Abstract
Efficient neural networks are essential for scaling machine learning models to real-time applications and resource-constrained environments. Fully-connected feedforward layers (FFLs) introduce computation and parameter count bottlenecks within neural network architectures.  To address this challenge, in this work, we propose a new class of dense layers that generalize standard fully-connected feedforward layers, $\textbf{E}$fficient, $\textbf{U}$nified and $\textbf{Gen}$eral dense layers (EUGens).  EUGens leverage random features to approximate standard FFLs and go beyond them by incorporating a direct dependence on the input norms in their computations. The proposed layers unify existing efficient FFL extensions and improve efficiency by reducing inference complexity from quadratic to linear time. They also lead to $\textbf{the first}$ unbiased algorithms approximating FFLs with arbitrary polynomial activation functions. Furthermore, EuGens reduce the parameter count and computational overhead while preserving the expressive power and adaptability of FFLs. We also present a layer-wise knowledge transfer technique that bypasses backpropagation, enabling efficient adaptation of EUGens to pre-trained models. Empirically, we observe that integrating EUGens into Transformers and MLPs yields substantial improvements in inference speed (up to $\textbf{27}$\%) and memory efficiency (up to $\textbf{30}$\%) across a range of tasks, including image classification, language model pre-training, and 3D scene reconstruction. Overall, our results highlight the potential of EUGens for the scalable deployment of large-scale neural networks in real-world scenarios.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

全连接前馈层（FFL）是 Transformer、MLP、NeRF 等现代大规模神经网络的主要计算与参数瓶颈。尽管这些模型在自然语言处理、计算机视觉、3D 重建等领域取得巨大成功，但 FFL 的推理复杂度为 O(d² + dl)（输入维度 d，隐藏单元数 l），导致在实时或资源受限场景中难以部署。现有高效扩展（如低秩近似、结构化矩阵、剪枝、量化）缺乏统一框架，且多数无法同时保证近似无偏性与通用性。本文提出 **EUGens（Efficient, Unified, and General dense layers）**，旨在统一并泛化现有高效 FFL 扩展，将推理复杂度降至线性时间，同时首次实现任意多项式激活函数的无偏近似，并引入对输入范数的直接依赖以提供超越标准 FFL 的表达能力。

## 2. 方法论

### 核心思想
利用随机特征（Random Features, RF）技术将权重矩阵 W 与输入 x 解耦，分别通过非线性映射 f(x) 和 g(W) 转化为低维向量，然后通过点积连接，从而避免直接计算 Wx 的二次复杂度：  
**EUGen_k(W, x) = g(W)^T f(x)**，其中 f、g 由共享的随机投影矩阵 G_ij 与非线性函数 Φ、Ψ 构成。

### 关键技术细节
- **k 阶 EUGen 层**：f(x) = Φ(concat_{i=0..k} [∏_{j=1}^i G_{ij} x_+])，g(W) = Ψ(concat_{i=0..k} [∏_{j=1}^i G_{ij} w_+])，其中 x_+, w_+ 分别与 1 和 ∥x∥₂ 拼接。
- **无偏性定理（Theorem 3.1）**：当 Φ、Ψ 为恒等函数，G_ij 各行独立且服从特定零均值分布时，EUGen 可无偏估计具有任意多项式激活函数的 FFL。
- **浓度界限（Theorem 3.2 & 3.3）**：给出方差公式与指数型概率上界，保证近似可靠性。
- **QMC 改进**：使用高斯正交矩阵（GOM）作为投影矩阵，降低方差。
- **连续激活扩展（Theorem 3.4）**：利用 Bernstein 多项式逼近任意连续函数。
- **线性层合并技巧**：EUGen 后接线性层可压缩为单一矩阵，进一步减少参数。
- **无反向传播的层式蒸馏**：利用闭式解（最小二乘）或轻量梯度优化，快速适应预训练模型。

## 3. 实验设计

### 数据集与场景
| 任务 | 数据集/场景 | 基准模型 |
|------|-------------|----------|
| 合成近似 | 随机数据（d=512） | SNNK、低秩近似 |
| LLM 预训练 | OpenWebText（~36.8B tokens） | GPT-2 124M 参数 |
| 图像分类 | ImageNet、Places365、CIFAR-10/100、DTD、Oxford Pets | ViT-Base、ViT-Large |
| 3D 新视角合成 | Synthetic NeRF、Mip-NeRF 360（360_v2） | NeRF、Mip-NeRF 360 |
| 动态场景 | D-NeRF 数据集 | D-NeRF |
| 真实场景 NeRF | Mip-NeRF 360 数据集 | Zip-NeRF |
| 3D 符号距离场（SDF） | ReplicaCAD（6 个场景） | iSDF |
| 自然语言理解 | GLUE 基准（8 个任务） | BERT、DistilBERT |

### 对比方法
- 低秩近似（固定秩矩阵）
- SNNK（Universal Random Feature 层）
- 原始 FFL（基线）
- 参数匹配的降维基线

## 4. 资源与算力

论文明确提及的算力信息：
- **LLM 预训练（GPT-2）**：4 块 NVIDIA A6000 GPU，训练 50K 迭代。
- **合成近似实验**：单块 NVIDIA RTX 4090，训练 3K 轮。
- **NeRF 系列实验**：单块 NVIDIA RTX 4090 + AMD Ryzen 7 7700 CPU。
- **iSDF 实验**：单块 GPU（未指明具体型号）。
- **ViT 图像分类**：未明确说明 GPU 数量，但使用 batch size 4096 或 16，推测使用多块 GPU（如 8 块）。
- 未给出每次实验总耗时或总 GPU 小时数，仅报告了单步时间或推理加速比例。

## 5. 实验数量与充分性

- **合成近似**：3 种激活函数（ReLU、Softplus、GELU），3 种方法对比，每组 10 次随机重复，报告 MSE。
- **LLM 预训练**：替换 2~11 层（共 12 层）的 FFL，与低秩对比，报告验证 loss 与参数-性能折衷图。
- **ViT 图像分类**：在 ImageNet（300 epoch）和 Places365（80K steps）上，替换 1~12 层，提供参数-精度折线图；额外在 CIFAR-10/100、DTD、Pets 上验证；还实验了 ViT-L（24 层，替换 18/21 层）。
- **3D 重建**：NeRF（8 场景）、Mip-NeRF 360（7 场景）、D-NeRF（8 场景）、Zip-NeRF（7 场景）、iSDF（6 场景×3 随机种子）——均报告平均指标与多数单场景结果。
- **蒸馏实验**：NeRF 上比较闭式解与可训练 G，Zip-NeRF 和 iSDF 上验证。
- **消融实验**：可训练 vs 固定 G、随机特征数量、正交随机特征 vs 普通 RF、多项式阶数 k（≤5）、激活函数选择（ReLU vs Softplus）、非线性 vs 低秩。
- **NLP 图灵测试**：GLUE 8 任务，平均 5 随机种子。

充分性评价：**充分且公平**。覆盖了多种模态（NLP、视觉、3D）、多种模型结构（Transformer、MLP、隐式表示）、多种训练范式（从头训练、微调、蒸馏）。对比基线涵盖低秩、SNNK 和参数匹配降维。所有关键组件（随机特征数、G 是否可训练、阶数 k）均有消融。唯一不足：未对所有任务报告标准误差或置信区间（仅部分任务报告多次重复）。

## 6. 主要结论与发现

1. **近似能力**：EUGen 在合成设置中 MSE 显著低于 SNNK 和低秩方法，可高精度逼近 ReLU、Softplus、GELU 激活的 FFL。
2. **LLM 预训练**：替换 GPT-2 中最多 11/12 层 FFL 后，验证 loss 仅小幅上升，推理参数减少约 27%，速度提升近 27%。
3. **ViT 图像分类**：替换 6 层（共 12 层）后，ImageNet 精度仅下降约 0.5%，参数减少 30%；在多个微调数据集上保持精度。
4. **3D 重建**：NeRF 系列（NeRF, Mip-NeRF 360, D-NeRF, Zip-NeRF）在几乎不损失 PSNR/SSIM 的前提下，推理速度提升 6%~27%，模型存储减少 30%。
5. **iSDF**：SDF 重建质量相似，训练时间加快 5%，推理时间加快 22.6%。
6. **蒸馏有效性**：分析式蒸馏（闭式解）可在数秒内将 EUGen 适配到预训练 NeRF，恢复约 99% 质量；可训练 G 的蒸馏可恢复至 99.8%。
7. **关键设计**：可训练的 G 矩阵、非线性的 Φ/Ψ、正交随机特征均能提升效果；多项式阶数 k≤3 已足够，更高 k 可进一步提升质量但速度下降。

## 7. 优点

- **理论贡献**：首次给出任意多项式激活 FFL 的无偏随机特征近似定理，并提供浓度界与连续激活扩展。
- **统一性**：将低秩层、SNNK、不对称核函数等作为特例纳入同一框架，并允许直接使用输入范数。
- **实用性**：推理复杂度从 O(d²) 降至 O(m d k²)（m << d），压缩参数的同时通过层合并进一步加速。
- **蒸馏灵活性**：提供无需反向传播的闭式解蒸馏，适用于零样本加速预训练模型。
- **跨领域验证**：在 NLP、视觉、3D 重建三大领域，跨越 10 多种任务和 5 种不同架构上均有显著加速，证明方法的通用性。
- **正交兼容**：可与剪枝、量化、低秩等其他效率技术结合。

## 8. 不足与局限

1. **多项式阶数限制**：虽然可通过 Bernstein 多项式逼近连续函数，但非多项式激活（如 ReLU 在无限区间）的近似误差理论上无界；实际中仅在小阶数 k≤3 下实验，更高阶的收益与代价未充分探索。
2. **资源报告不够详尽**：仅 LLM 预训练明确 GPU 数量，其他实验未说明具体训练总耗时或 GPU 型号版本，不利于复现能耗评估。
3. **蒸馏的实验覆盖有限**：蒸馏仅在 NeRF、Zip-NeRF、iSDF 上验证，未在 Transformer/LLM 上验证，其闭式解蒸馏在大规模场景下的有效性未知。
4. **随机特征数量与表现之间的权衡**：部分场景使用较大随机特征数（如 1024）才达到与基线媲美的质量，此时推理速度优势被削弱（但仍优于原始 FFL）；更极端的压缩（如 m=16）则质量下降明显。
5. **偏倚风险**：所有实验均使用作者实现的代码库，部分基线（如低秩）可能未经过最优调整；此外，仅报告了单向加速比，未分析训练额外开销（如蒸馏时间）。
6. **应用限制**：EUGen 目前主要替换 FFL 中的扩展层（expansion layer），在注意力层或 embedding 层未经测试；且需要一定的随机特征数量，在移动端极低计算资源下的表现未知。
7. **统计显著性**：多数消融实验仅给出单次或平均结果，缺少误差棒或置信区间，难以判断改进是否统计显著。

（完）
