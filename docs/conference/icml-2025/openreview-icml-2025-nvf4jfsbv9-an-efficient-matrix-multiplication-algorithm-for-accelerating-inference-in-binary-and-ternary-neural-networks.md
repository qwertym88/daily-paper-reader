---
title: An Efficient Matrix Multiplication Algorithm for Accelerating Inference in Binary and Ternary Neural Networks
title_zh: 一种用于加速二值和三值神经网络推理的高效矩阵乘法算法
authors: "Mohsen Dehghankar, Mahdi Erfanian, Abolfazl Asudeh"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Nvf4jFsbv9"
tags: ["query:neural-arch"]
score: 4.0
evidence: 针对二值/三值网络的高效推理算法
tldr: 本文为了解决深度神经网络推理效率低下的问题，提出了一种针对二值/三值权重矩阵的高效矩阵乘法算法。该方法利用训练后权重不变的特点进行预处理并构建索引，以对数因子降低存储需求并加速推理。实验验证了其在加速推理和减少内存占用方面的有效性。这项工作为低比特网络的高效部署提供了实用算法。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1771, \"height\": 720, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 776, \"height\": 705, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 829, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 829, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1762, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 595, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 802, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 838, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1769, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1761, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 752, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 771, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-nvf4jfsbv9/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 845, \"height\": 584, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-nvf4jfsbv9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 668, \"height\": 113, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nvf4jfsbv9/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 856, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nvf4jfsbv9/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 858, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nvf4jfsbv9/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 791, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nvf4jfsbv9/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 888, \"height\": 164, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nvf4jfsbv9/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 883, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-nvf4jfsbv9/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1246, \"height\": 708, \"label\": \"Table\"}]"
motivation: DNN推理效率低，依赖高性能计算基础设施。
method: 利用权重矩阵不变性进行预处理和索引构建，降低存储并加速矩阵乘法。
result: 实验证明该方法有效减少存储需求并加速推理。
conclusion: 为低比特网络的高效部署提供了实用算法。
---

## Abstract
Despite their tremendous success and versatility, Deep Neural Networks (DNNs) such as Large Language Models (LLMs) suffer from inference inefficiency and rely on advanced computational infrastructure.
To address these challenges and make these models more accessible and cost-effective, in this paper, we propose algorithms to improve the inference time and memory efficiency of DNNs with binary and ternary weight matrices.
Particularly focusing on matrix multiplication as the bottleneck operation of inference, we observe that, once trained, the weight matrices of a model no longer change. This allows us to preprocess these matrices and create indices that help reduce the storage requirements by a logarithmic factor while enabling our efficient inference algorithms.
Specifically, for a $n\times n$ weight matrix, our efficient algorithm guarantees a time complexity of $O(\frac{n^2}{\log n})$, a logarithmic factor improvement over the standard vector-matrix multiplication.
Besides theoretical analysis, we conduct extensive experiments to evaluate the practical efficiency of our algorithms. Our results confirm the superiority of our approach both with respect to time and memory, as we observed a reduction in the multiplication time up to 29x and memory usage up to 6x. When applied to LLMs, our experiments show up to a 5.24x speedup in the inference time.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
深度神经网络（DNN）和大型语言模型（LLM）虽然性能卓越，但在推理阶段存在效率低下、对高性能计算基础设施依赖严重的问题。高计算成本和内存需求限制了模型在普通设备（如个人电脑、移动端）上的部署，且依赖远程API调用还会引入延迟、成本和隐私风险。为提升推理效率和可访问性，本文聚焦于量化神经网络（特别是二值/三值权重网络），意图通过改进矩阵乘法这一核心瓶颈运算，实现推理加速和内存压缩。已有研究表明，1.58位LLM可在保持接近全精度模型准确性的同时大幅降低计算开销，这为算法优化提供了基础。

## 2. 论文提出的方法论
### 核心思想
利用训练后权重矩阵固定不变的特点，对权重矩阵进行**预处理**，构建索引（permutation + segmentation），将原始矩阵存储替换为更紧凑的索引表示，从而将存储复杂度从 \(O(n^2)\) 降低至 \(O(n^2/\log n)\)。推理时，通过索引实现快速向量-矩阵乘法。

### 关键技术细节
1. **问题约简**：将三值矩阵 \(A \in \{-1,0,1\}^{n\times n}\) 分解为两个二值矩阵 \(B^{(1)}, B^{(2)}\) 之差 (\(A = B^{(1)}-B^{(2)}\))，从而将三值乘法转化为二值乘法。
2. **预处理步骤**（Algorithm 1）：
   - **分块**：将二值矩阵 \(B\) 的列划分为大小为 \(k\) 的列块 (\(k \le \log n\))。
   - **行排列**：对每个列块，按行的二进制数值进行字典序排序，生成排列 \(\sigma_{B_i}\)。
   - **分割**：对排序后的块计算全分割列表 \(L_i\)（长度为 \(2^k\)），记录每种二进制行值出现的起始位置。
3. **推理算法**：
   - **RSR算法**：对每个块，先利用排列和分割计算输入向量 \(\vec{v}\) 的**分段和**（Segmented Sum）\(\vec{u}\)（式5），然后计算 \(\vec{u} \cdot \text{Bin}^{[k]}\)（\(\text{Bin}^{[k]}\) 是包含所有 \(2^k\) 种 \(k\) 位二进制行的矩阵），最后拼接各块结果。时间复杂度 \(O(n^2/(\log n - \log\log n))\)。
   - **RSR++算法**：进一步优化步骤二，利用 \(\text{Bin}^{[k]}\) 的特殊结构（按二进制序排列），将 \(\vec{u} \cdot \text{Bin}^{[k]}\) 的计算由 \(O(k2^k)\) 降低至 \(O(2^k)\)（Algorithm 3）。总时间复杂度达到 \(O(n^2/\log n)\)。
4. **推广性**：可扩展至任意q位量化矩阵（分解为q个二值矩阵加权和）。
5. **并行化**：各列块计算独立，适合CPU/GPU并行；GPU实现中通过构造3D张量将推理转化为单次张量乘法。

## 3. 实验设计
### 数据集/场景
- **矩阵乘法基准测试**：随机生成的二值/三值权重矩阵，规模 \(n\) 从 \(2^{11}\) 到 \(2^{16}\)。
- **LLM推理测试**：使用三个问答数据集——**ShortQuestions**（GPT-4生成的短事实问题）、**SimpleQuestions**、**TREC QA**。
- **模型**：1.58位量化版的 **Llama3-8B**、**Falcon3-3B**、**Falcon3-10B**。

### 基准方法
- **Standard**：标准向量-矩阵乘法（原生C++实现、NumPy `np.dot`、PyTorch基线）。
- **RSR / RSR++**：本文提出的算法。
- 附加对比：与 **BitNet.cpp**（I2S核）对比如图13。

### 实现环境
- C++原生实现：避免运行时噪声，验证理论复杂度。
- Python NumPy实现：模拟实际高性能计算环境。
- PyTorch实现（CPU/GPU）：评估真实LLM推理速度。

## 4. 资源与算力
论文**未明确给出**训练或推理使用的具体GPU型号、数量、训练时长等信息。在LLM推理实验中提及使用“16-core Intel Xeon CPU, NVIDIA Tesla T4 GPU, 32GB RAM, Debian 11”，但未说明GPU的详细性能参数或并行配置。实验目的仅为验证推理速度，未涉及模型训练，因此算力开销相对较小。

## 5. 实验数量与充分性
论文进行了多组对比实验，覆盖不同维度：
- **算法对比**：原生C++中对比Standard、RSR、RSR++（6种矩阵规模，每种取10次均值）。
- **NumPy对比**：二值/三值矩阵乘法（6种规模，每种4次均值）。
- **LLM CPU推理**：3个模型 × 3个数据集，每个结果取平均值，共9个实验点，同时验证了输出一致性。
- **LLM GPU推理**：3个模型，各测量标准与RSR的推理时间（微秒±标准差，表1）。
- **参数k优化**：分别对RSR和RSR++进行超参数搜索（图9），并展示最优k选择过程。
- **模块级分析**：针对Llama3模型各Transformer模块分别测量加速比（图14）。
- **附加对比**：与BitNet.cpp的对比（图13，4种规模）。

总体来看，实验覆盖了**理论验证**（原生实现）、**实际库对比**（NumPy/PyTorch）、**真实模型推理**（多种LLM和数据集）、**模块细粒度分析**以及**超参数敏感性**。实验设计较为全面，结果客观展示了算法在不同设定下的优势。但部分实验（如GPU推理）仅给出微秒级单次推理时间，未提供多次重复统计分布细节；另外，与BitNet.cpp的对比中仅给出单一线图，缺少误差范围或显著性检验。

## 6. 论文的主要结论与发现
- **理论贡献**：针对二值/三值权重矩阵，提出了RSR和RSR++两种算法，向量-矩阵乘法时间复杂度达到 \(O(n^2/\log n)\)，存储复杂度降至 \(O(n^2/\log n)\)。
- **实践效果**：
  - 原生C++实现：最大**29倍**推理加速（\(n=2^{16}\)）。
  - NumPy实现：二值矩阵乘法加速达**24倍**（\(n=2^{15}\)），三值矩阵加速达**12.76倍**。
  - 内存压缩：预处理后仅需存储排列和分割列表，相比完整矩阵节省**5.99倍**空间。
  - LLM推理（CPU）：Llama3-8B-1.58bit上最高**5.24倍**加速（Falcon3-3B-1.58bit上5.24x，其他约4-5x）。
  - LLM推理（GPU）：GeForce T4上实现约**1.7-2.7倍**加速。
- **可推广性**：算法可自然扩展到任意q位量化网络，并支持并行化。

## 7. 优点
- **算法创新性**：利用权重不变性进行预处理，通过索引（排列+分段）显著减少冗余计算，思路简洁高效。
- **理论保证扎实**：给出了严格的时间/空间复杂度分析，并证明了对数因子改进。
- **实验全面**：覆盖了从原生实现到实际库（NumPy、PyTorch）、从孤立矩阵乘法到完整LLM推理的多个层次，验证了理论在实际环境中的可行性。
- **硬件无关性**：算法以应用层实现，不依赖特殊硬件指令，可即插即用于已有二值/三值模型，无需重新训练。
- **内存压缩优势**：预处理后仅需存储索引，大幅降低模型存储和传输开销，对边缘部署尤为有利。

## 8. 不足与局限
- **小规模矩阵效果受限**：对于小于 \(2^{10}\) 的矩阵，常数开销可能大于理论增益，实际加速不明显。但论文指出真实LLM矩阵规模通常更大。
- **GPU实现优化不足**：当前GPU版本仅使用PyTorch高阶API，未利用底层CUDA自定义核（如排列、分段求和），导致加速比远低于CPU实验（仅约2x）。对比BitNet.cpp的手工优化核时同样暴露了算法级与硬件级优化的差距。
- **消融实验缺乏**：未进行如不同k值对性能影响的系统消融，仅通过固定搜索给出最优k；未分析激活函数、层归一化等非矩阵运算对整体推理时间的影响。
- **一致性验证有限**：仅通过单token生成验证输出一致性（对比Standard与RSR结果是否相同），未测试多步生成或长文本场景下的模型输出差异。
- **资源/算力描述缺失**：未提供训练所需GPU时长、能耗等数据，也未明确推理实验的硬件并行配置细节（如CPU线程数、GPU并行度）。
- **应用范围限制**：当前只针对量化网络（二值/三值），对于更高位宽（如4位、8位）网络虽可扩展，但复杂度线性增长，实际加速比会降低。

（完）
