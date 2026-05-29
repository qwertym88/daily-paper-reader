---
title: Reducing Deep Network Complexity via Sparse Hierarchical Fourier Interaction Networks
title_zh: 通过稀疏层次化傅里叶交互网络降低深度网络复杂度
authors: Andrew Jeremy Kiruluta
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=49TFMeqNKd"
tags: ["query:neural-arch"]
score: 9.0
evidence: 统一卷积与注意力的稀疏傅里叶架构
tldr: 针对深度学习网络中卷积和自注意力机制计算复杂度高的问题，提出稀疏层次化傅里叶交互网络(SHFIN)，利用分块快速傅里叶变换和可学习的稀疏频率掩码，在保持空间局部性的同时实现全局信息混合。该方法以O(s log s)复杂度替代卷积和注意力的高计算需求，实验表明在图像分类等任务上取得有竞争力的结果。为设计高效网络架构提供了新范式。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-49tfmeqnkd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 957, \"height\": 1409, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-49tfmeqnkd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1144, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49tfmeqnkd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1017, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49tfmeqnkd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1133, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-49tfmeqnkd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 935, \"height\": 256, \"label\": \"Table\"}]"
motivation: 卷积和自注意力机制计算开销大，需要更高效的统一算子。
method: 提出SHFIN原语，用稀疏傅里叶算子统一替代卷积和自注意力。
result: 在多个视觉任务上以更低复杂度达到与基线相当或更好的性能。
conclusion: 稀疏傅里叶交互是一种有前景的低复杂度架构设计方向。
---

## Abstract
In this work, we introduce \emph{Sparse Hierarchical Fourier Interaction Networks} (SHFIN), a novel architectural primitive designed to replace both convolutional kernels and the quadratic self‑attention mechanism with a unified, spectrum‑sparse Fourier operator.  SHFIN is built upon three core components: (1) a hierarchical patch‑wise fast Fourier transform (FFT) stage that partitions inputs into localized patches and computes an $O(s\log s)$ transform on each, preserving spatial locality while enabling global information mixing; (2) a learnable $K$‑sparse frequency masking mechanism, realized via a Gumbel‑Softmax relaxation, which dynamically selects only the $K$ most informative spectral components per patch, thereby pruning redundant high‑frequency bands; and (3) a gated cross‑frequency mixer, implemented as a low‑rank bilinear interaction in the retained spectral subspace, which captures dependencies across channels at $O(K^2)$ cost rather than $O(N^2)$. An inverse FFT and residual fusion complete the SHFIN block, seamlessly integrating with existing layer‑norm and feed‑forward modules.

Empirically, we integrate SHFIN blocks into both convolutional and transformer‑style backbones and conduct extensive experiments on ImageNet‑1k. On the ResNet‑50 and ViT‑Small scales, our SHFIN variants achieve comparable Top‑1 accuracy (within 0.5 pp) while reducing total parameter count by up to 60\% and improving end‑to‑end inference latency by roughly 3× on NVIDIA A100 GPUs. Moreover, in the WMT14 English–German translation benchmark, a Transformer‑Small augmented with SHFIN cross‑attention layers matches a 28.1 BLEU baseline with 55\% lower peak GPU memory usage during training.  These results demonstrate that SHFIN can serve as a drop‑in replacement for both local convolution and global attention, offering a new pathway toward efficient, spectrum‑aware deep architectures.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现代深度学习架构（卷积神经网络CNN和Transformer）在捕获全局依赖关系时面临严重计算瓶颈——CNN通过堆叠层来扩大感受野，效率低下；Transformer的二次自注意力（O(N²)）在长序列上开销巨大。此外，现有的傅里叶方法（如FNet、GFNet、AFNO）虽能实现次二次复杂度，但存在三个关键缺陷：① 处理所有频率系数，未剔除冗余成分；② 使用全局FFT，丧失空间局部性；③ 缺乏显式的频谱稀疏性学习机制。
- **整体含义**：鉴于自然信号（图像、音频、文本嵌入）在频域中具有高度可压缩性（能量集中在少数频带），本文提出一种统一的**频谱-稀疏傅里叶算子**——SHFIN，旨在以线性复杂度替代卷积核和二次自注意力，同时保持全局上下文混合能力和局部敏感度。

## 2. 论文提出的方法论

### 核心思想
SHFIN块由三个相互增强的组件构成，形成端到端的频谱处理管道：

1. **层次化分块快速傅里叶变换（Hierarchical Patchwise FFT）**  
   - 将输入特征图X∈R^(L×C)沿序列维度划分为P个非重叠patch，每个patch长度s（L=Ps）。  
   - 对每个patch逐通道应用s点FFT，计算复杂度O(s log s)，总复杂度O(L log s)。  
   - 保留空间局部性，同时允许全局信息混合。

2. **可学习的K-稀疏频率掩码（Learnable K‑sparse Spectral Masking）**  
   - 每个patch引入二进制掩码g∈{0,1}^s，约束恰好有K个1（K≪s）。  
   - 通过Gumbel-Softmax松弛实现可微的topK选择：从实数值logit α出发，添加Gumbel噪声，经温度τ缩放后取topK，前向传播使用硬掩码，反向传播使用连续松弛。  
   - 掩码后的频谱仅保留K个最信息量的频率系数，从而剔除冗余高频带。

3. **门控低秩双线性混合器（Gated Low‑Rank Bilinear Mixer）**  
   - 将保留的频谱系数堆叠成Z^(p)∈R^(K×C)。  
   - 学习三个投影矩阵：W_q, W_k∈R^(C×r)（r≪K），W_v∈R^(C×C)。  
   - 计算Q=Z W_q，K=Z W_k，V=Z W_v；构造相似性矩阵A=softmax(QK^T / √r)；用元素级门控h∈(0,1)^K调制，输出M=(h⊙A)V。  
   - 复杂度O(P(Kr + K² + CK))，主要是线性于C和K²。

- **逆变换与残差融合**：将混合后结果零填充回完整频谱，再通过IFFT回到空间域，最后与原始输入残差连接并LayerNorm。

### 复杂度分析
- 总复杂度约O(L log s + 256 L)（当s=16, K=16, r=4, C=256时），远低于O(L k² C)的卷积和O(L² C)的自注意力。

## 3. 实验设计

### 数据集与场景
- **图像分类**：ImageNet-1k（128万训练/5万验证，1000类，224×224）、CIFAR-10/100（5万训练/1万测试，32×32）。  
- **机器翻译**：WMT14 English→German（128 token截断，BPE分词）。

### 基准（Benchmark）与对比方法
- 卷积类：ResNet-50、ConvNeXt-Tiny。  
- Transformer类：ViT-Small/16。  
- 傅里叶类：FNet-Base/AFNO-Tiny。  
- 所有基线使用统一训练协议（AdamW、余弦学习率、相同数据增强）以确保公平。

### 主要结果
- **表1（ImageNet）**：SHFIN-Small Top-1 80.7%（vs ResNet-50 80.4%，ViT-Small 81.2%），参数仅10.3M（少于ResNet的25.6M和ViT的22.1M），FLOPs 2.0G，推理延迟2.1ms（比ResNet快2.6×，比ViT快3.1×）。  
- **表2（CIFAR）**：SHFIN-Tiny在CIFAR-10达95.1%（与AFNO持平），CIFAR-100达82.3%（高于FNet的80.5%），参数3.8M。  
- **表3（翻译）**：用于替换Transformer-Small自注意力，BLEU 27.8（vs 28.1），参数减少45%，推理延迟从49ms降至24ms，训练峰值内存降低55%。  
- **表4（消融）**：探索K和r的影响——K=8性能略降（79.8%），K=32性能最高（81.0%）但参数和延迟增加；r=2导致性能下降。

### 消融实验
- 在ImageNet-1k上对K（8/16/32）和r（2/4）进行联合消融，验证稀疏度和秩对性能与效率的权衡。

## 4. 资源与算力

- 文中明确提到：所有模型在**NVIDIA L4 GPU**和**Apple M1 Pro**上训练，使用自动混合精度（AMP）。  
- 未报告具体GPU数量或集群规模。  
- 训练配置：视觉模型100 epochs，有效batch size 256（ImageNet）或512（CIFAR）；翻译模型300K优化步，batch size 64。  
- 推断延迟测量：100次运行取平均（排除前10次预热），batch size 64。  
- **资源信息不够完整**，未提供总GPU小时数或训练时间。

## 5. 实验数量与充分性

- **实验数量**：覆盖3个任务（分类×2数据集+翻译），对比4～5个基线，含1个系统性消融（表4），总计约4个主表+2个图表。实验量属于中等规模。  
- **充分性判断**：
  - **正面**：对比基线涵盖了CNN、Transformer、Fourier三大方向，并使用统一训练协议控制变量；消融覆盖核心超参数（K, r）。  
  - **不足**：① 仅在中等规模模型（ResNet-50/ViT-Small级别）测试，未在大规模模型（如ViT-Large）上验证；② 未报告多次运行的标准差或置信区间，统计显著性存疑；③ 缺少对更高分辨率（如384×384）或更多下游任务（如目标检测、语义分割）的评估；④ 翻译任务仅一个基准（WMT14），未在其他语言对或更大规模语料上验证。

## 6. 论文的主要结论与发现

- SHFIN作为统一的频谱-稀疏算子，可以在保持与主流架构相当精度的前提下，将参数减少多达60%，推理速度提升约3倍，内存占用降低55%。  
- 分层分块FFT结合可学习K-稀疏掩码是有效的：K=16即足以捕获大部分信息，进一步增大K收益递减。  
- 低秩双线性混合器在狭窄的频谱子空间内以O(K²)成本实现了通道间依赖建模，优于密集注意力。  
- SHFIN可作为“即插即用”模块替代卷积或自注意力，为构建高效、频谱感知的深度网络提供了新范式。

## 7. 优点

- **创新性**：首次将层次化分块FFT、可微分稀疏选择、低秩频域混合统一为单一算子，兼具局部性和全局感受野。  
- **效率优异**：理论复杂度线性于L，实际推理延迟显著低于卷积和Transformer。  
- **扩展性**：可无缝集成到现有CNN/Transformer骨干中，作为drop-in替换。  
- **可解释性**：频谱掩码提供直观的频率选择行为，有利于理解模型关注的频带。  
- **实验设计公平**：与基线使用相同优化器、学习率调度、数据增强，避免不公平优势。

## 8. 不足与局限

- **超参数敏感**：K和r需要仔细调优，过小的K可能导致信息丢失，过大的K牺牲稀疏性。Gumbel-Softmax随机性可能增加训练方差。  
- **硬件依赖**：性能高度依赖FFT库优化；在缺乏高效FFT支持的设备上，可能不如手工优化的卷积核。  
- **局部-全局权衡**：patch大小s的选择造成矛盾——小patch保留细节但增加FFT调用次数，大patch减少计算但可能丢失局部结构。  
- **实验覆盖不足**：未进行大模型（如ViT-Large、GPT风格）验证；缺少多次运行的标准差；只测试了ImageNet-1k单一分辨率；翻译任务仅一个数据集。  
- **理论分析缺失**：缺乏对SHFIN逼近能力相对卷积/注意力的形式化刻画。  
- **未公开代码**（论文未明确说明，但检查清单未提供代码链接），影响可复现性。

（完）
