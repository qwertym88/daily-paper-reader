---
title: Auto-Compressing Networks
title_zh: 自动压缩网络
authors: "Vaggelis Dorovatas, Georgios Paraskevopoulos, Alexandros Potamianos"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eIDa6pd9iQ"
tags: ["query:neural-arch"]
score: 8.0
evidence: 用加法长前馈连接替代短残差连接，实现自动压缩
tldr: 深度神经网络中短残差连接虽成功但导致计算冗余。本文提出自动压缩网络（ACN），用跨层加性长前馈连接替代传统短残差连接。这种设计使网络在训练中自动将信息压缩到浅层，增强表征效率。实验表明ACN在多种任务上以更少参数达到或超过基线性能。该工作为残差连接设计提供了新范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-eida6pd9iq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eida6pd9iq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1433, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eida6pd9iq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 449, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eida6pd9iq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 528, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eida6pd9iq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 603, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eida6pd9iq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 487, \"height\": 399, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eida6pd9iq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 873, \"height\": 710, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-eida6pd9iq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1422, \"height\": 859, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eida6pd9iq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1458, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eida6pd9iq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1436, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eida6pd9iq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 443, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eida6pd9iq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1167, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eida6pd9iq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1260, \"height\": 476, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eida6pd9iq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 906, \"height\": 341, \"label\": \"Table\"}]"
motivation: 传统短残差连接导致计算冗余，本文旨在通过新的连接方式实现信息自动压缩。
method: 用跨层加性长前馈连接替换短残差连接，利用梯度下降的动力学特性实现自动压缩。
result: 在多个数据集上以较少参数实现与或超过基线性能。
conclusion: 所提ACN架构通过连接设计有效减少冗余，提升网络效率。
---

## Abstract
Deep neural networks with short residual connections have demonstrated remarkable success across domains, but increasing depth often introduces computational redundancy without corresponding improvements in representation quality. We introduce Auto-Compressing Networks (ACNs), an architectural variant where additive long feedforward connections from each layer to the output replace traditional short residual connections. By analyzing the distinct dynamics induced by this modification, we reveal a unique property we coin as *auto-compression*—the ability of a network to organically compress information during training with gradient descent, through architectural design alone. Through auto-compression, information is dynamically "pushed" into early layers during training, enhancing their representational quality and revealing potential redundancy in deeper ones. We theoretically show that this property emerges from layer-wise training patterns found only in ACNs, where layers are dynamically utilized during training based on task requirements. We also find that ACNs exhibit enhanced noise robustness compared to residual networks, superior performance in low-data settings, improved transfer learning capabilities, and  mitigate catastrophic forgetting suggesting that they learn representations that generalize better despite using fewer parameters. Our results demonstrate up to 18\% reduction in catastrophic forgetting and 30-80\% architectural compression while maintaining accuracy across vision transformers, MLP-mixers, and BERT architectures. These findings establish ACNs as a practical approach to developing efficient neural architectures that automatically adapt their computational footprint to task complexity, while learning robust representations suitable for noisy real-world tasks and continual learning scenarios.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现代深度神经网络广泛使用短残差连接（如ResNet中的恒等跳跃连接），虽然解决了梯度消失问题并支持深层网络训练，但这种架构常导致计算冗余：许多深层实际上贡献很小（可被随机丢弃而不影响性能），参数利用率低。此外，信息在层间均匀分布而非集中到关键层，限制了表征效率。
- **整体含义**：本文提出**自动压缩网络（Auto-Compressing Networks, ACNs）**，通过将每一层直接连接到输出的**加性长前馈连接**替换传统的短残差连接，使网络在梯度下降训练过程中**仅靠架构设计**就能自然地将信息“推”到浅层，自动识别并压缩冗余深层，从而在保持性能的同时大幅减少有效参数和推理计算量，并提升泛化、鲁棒性、迁移学习与持续学习能力。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：在深度网络中，每一层的输出都通过加法直接贡献到最终输出（而非只传递给下一层）。这种连接模式改变了梯度传播的动力学：各层梯度包含一个**直接梯度（DG）分量**（从输出直接回传到该层），以及**网络介导梯度（NG）分量**（经过后续层传播回来）。当权重初始化接近零时，DG在早期训练中占主导，使得浅层梯度远大于深层，形成**逐层训练**的动态——信息被“压”到早期层，深层变得冗余（自动压缩）。
- **关键技术细节**：
  - **ACN公式**：设输入 \(x_0\)，第 \(i\) 层输出 \(x_i = f_i(x_{i-1})\)，网络最终输出 \(y = \sum_{i=0}^L x_i\)（包含输入 embedding 和所有层输出之和）。
  - **与ResNet对比**：ResNet的梯度有指数级多条路径（\(2^{L-i}\)），导致DG占比极低，因此没有自动压缩效果；ACN只有 \(L-i+1\) 条路径（含一条直接路径），DG占比较大，驱动早期层优先学习。
  - **实现**：在ViT、MLP-Mixer、BERT等架构上，只需将短残差求和替换为对输出的长求和，分类头共享，不增加额外参数或损失。推理时可只使用前k层输出作为最终预测，实现动态深度剪枝。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：
  - 图像：CIFAR-10、ImageNet-1K（ILSVRC-2012）。
  - 自然语言理解：GLUE中的SST-2（情感分析）、QQP（释义检测）、QNLI（问答自然语言推理）。
  - 持续学习：Split CIFAR-100（20个5类任务）。
  - 迁移学习：CIFAR-100 → CIFAR-10。
- **基准架构**：Vision Transformer (ViT)、MLP-Mixer、BERT（小型变种，12层）。
- **对比方法**：
  - **残差网络**：原始ResNet风格（Res-Mixer, Residual ViT, Residual BERT）。
  - **其他残差变体**：DenseNet（密集连接）、DenseFormer（可学习加权平均）、Feedforward Network (FFN)。
  - **正则化压缩方法**：Aligned (Jiang et al., 2025) 与 LayerSkip (Elhoushi et al., 2024) ——两者均使用中间层损失与权重调度。
  - **持续学习方法**：Naive Fine-tuning 和 Synaptic Intelligence (SI)。
  - **剪枝方法**：Magnitude Pruning 和 Movement Pruning。
  - **早期退出机制**：Branches（专用分类头）与 Shared EE Head（共享分类头）对比。

## 4. 资源与算力

- **明确信息**：
  - 使用 EuroHPC JU 的 LEONARDO@CINECA 超级计算机（计划ID: EHPC-AI-2024-A04-051）。
  - AC-ViT 在 ImageNet-1K 上训练 700 个 epoch，Residual ViT 300 个 epoch；均使用 256 的 batch size。
  - 持续学习实验每任务训练 10 epoch；迁移学习实验训练至在 CIFAR-100 上达到相近性能。
- **未明确信息**：
  - 未详细说明具体 GPU 型号、数量、总GPU‑小时。论文仅在资源限制部分提及“small-scale tasks”，未提供精确的计算资源统计。
  - 未报告模型参数量与 FLOPs 的精确计算细节（仅提供近似值，如 AC-BERT 46M 参数、Res-BERT 110M；AC-ViT 51M、Res-ViT 86M）。

## 5. 实验数量与充分性

- **实验组数**：论文包含至少 7 组主要实验：
  1. **梯度动力学分析**（图1、图2）：展示梯度分布、层间学习模式。
  2. **自动压缩验证**（图3、图4）：不同任务难度（2/5/10 类）下的层使用情况。
  3. **语言模型微调**（图5）：AC-BERT vs. Residual BERT 在三个 GLUE 任务上的逐层性能。
  4. **噪声鲁棒性**（表2）：高斯噪声与椒盐噪声，多种强度。
  5. **低数据场景**（图6）：CIFAR-10 每类仅100个样本的训练/测试损失曲线。
  6. **持续学习**（表3）：Split CIFAR-100，三种深度（5/10/15层），两种方法（Naive FT 和 SI）。
  7. **迁移学习**（表4）及消融：与 Aligned、LayerSkip 对比。
- **附加实验**：
  - 附录E：与 DenseNet、DenseFormer 在相同epoch下的公平对比（700 epoch）。
  - 附录G：后训练剪枝（Magnitude 和 Movement Pruning）。
  - 附录H：早期退出集成（Branches 与 Shared Head）。
- **充分性评价**：
  - **优点**：覆盖多模态（图像、文本）、多架构（ViT、Mixer、BERT）、多任务类型（分类、NLU、迁移、持续学习），并包含消融（任务难度、噪声强度、深度、剪枝率）。
  - **局限性**：所有任务均为中等规模（最大 ImageNet-1K 但仅 12层 ViT）；未在更大规模模型（如 GPT‑style 或超大 ViT）上验证；大多数实验只报告一次或有限随机种子（除持续学习报告 mean±std），统计显著性未充分展示。

## 6. 论文的主要结论与发现

- ACN **自动压缩**层数：在 ViT 上仅需前6层即可达到完整12层精度（压缩50%）；在 BERT 上约75%的层可被剪枝而性能不变；且压缩比例随任务难度降低而增加。
- **噪声鲁棒性**优于 ResNet，高斯噪声 σ=0.4 时 AC-ViT 比 Res-ViT 高约6个百分点；椒盐噪声 10% 时高近10个百分点。
- **低数据场景**：AC-Mixer 训练与测试损失下降更快，泛化更好。
- **持续学习**：遗忘率下降最高18%（SI + 15层 ACN 仅遗忘32% vs. ResNet 50%），且增加层数有助于减少遗忘（ResNet 相反）。
- **迁移学习**：AC-Mixer 在 CIFAR-100 → CIFAR-10 上优于 Aligned 和 LayerSkip，无需调参。
- **与其它技术兼容**：ACN 天然适合早期退出（EG 加速3.3倍）和后训练剪枝（同等参数量下精度更高）。

## 7. 优点

- **架构简洁**：仅改变连接方式（短→长），无需额外损失、超参数或训练技巧，即可自动实现压缩。
- **理论解释清晰**：通过梯度分解（DG vs. NG）揭示了逐层训练与自动压缩的机制，提供了对比 FFN、ResNet 的统一分析框架。
- **多场景验证**：涵盖图像、语言、持续学习、迁移学习、噪声、剪枝、早退，证明 ACN 是一种通用设计原则。
- **实际效率**：推理时可直接截断浅层，无需复杂的路由或门控，内存和计算节省显著（30-80%）。
- **可组合性**：与现有正则化（SI）、剪枝（Movement）、早退等方法互补，进一步提升效果。

## 8. 不足与局限

- **训练较慢**：ACN 需要更多 epoch 达到收敛（如 AC-ViT 700 epoch vs. Res-ViT 300 epoch），虽然最终精度相当或略优，但训练成本增加。论文认为这有助于学习更鲁棒的表征，但未分析如何加速训练。
- **规模限制**：所有实验限于“small-scale tasks”（如 ViT‑Tiny/Base，BERT‑base 12层）。未在更大模型（如 LLaMA、GPT‑3、ViT‑Large）或更大数据集（如完整 ImageNet‑21K）上验证。此点也在“Limitations”中承认。
- **超参数敏感度**：虽然ACN无需额外超参数，但在对比实验中与 Aligned/LayerSkip 对比时，后两者使用了其最优超参数，而ACN固定默认设置，可能忽略了微调带来的差异。
- **统计报告**：大部分实验未提供多次运行的标准差（仅持续学习有误差条）。噪声实验只报告平均精度，未显示波动范围。这可能影响结论的统计可靠性。
- **消融不足**：
  - 未研究不同长连接变体（如加权求和、门控）的效果。
  - 未分析ACN在自监督（如MAE、SimCLR）或生成式（如扩散模型）场景下的表现。
  - 附录中提到更长的训练时间可能归因于较少的信息路径，但未提供严格的因果证据。
- **持续学习基准单一**：仅使用 Split CIFAR-100 和 Task‑IL 设置，未在类增量或域增量等其他场景评估。
- **实际部署考虑**：虽然推理时可压缩，但训练时需要存储所有层的输出用于梯度计算（因为每层都连接输出），内存开销与ResNet类似（需保存所有激活）。论文未讨论训练时的内存对比。

（完）
