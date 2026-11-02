# DSAINet Paper Card

> Source coverage: Full paper（13 页 PDF；补充材料未提供）  
> Extraction confidence: Mixed（全文文本与页码可靠；公式 7/11/12/14/16 的自动抽取不完整，已结合原 PDF 人工核对；图表由既有 reader 产物核验）  
> Locator mode: page-grounded  
> Primary analytical lens: methods  
> Secondary analytical lens: None  
> Context verification: Paper-only（Section 15 另含本地项目证据连接，不构成外部文献查证）  
> Card completeness: Complete relative to supplied source  
> Evidence labels: `[Paper]` 原文陈述；`[Analysis]` 基于证据的分析；`[Hypothesis]` 待检验解释；`[User]` 当前项目材料中的既有结论

<!-- reading-navigation:start -->
<a id="reading-top"></a>

[全部论文](<../README.md>) · [综合笔记](<DSAINet-note.md>) · **研究卡片** · [设计精读](<DSAINet-paper-xray.md>) · [原文对照](<DSAINet-paper.md>)

**章节导航**

- [01 基本信息](#reading-section-01)
- [02 一句话总结](#reading-section-02)
- [03 研究问题](#reading-section-03)
- [04 研究背景与发展路径](#reading-section-04)
- [05 论文识别的核心痛点](#reading-section-05)
- [06 核心思想](#reading-section-06)
- [07 方法总览](#reading-section-07)
- [08 核心模块拆解](#reading-section-08)
- [09 必要公式与符号](#reading-section-09)
- [10 实验设计与证据链](#reading-section-10)
- [11 结论的正确解释](#reading-section-11)
- [12 作者明确承认的局限](#reading-section-12)
- [13 批判性分析](#reading-section-13)
- [14 学到的知识](#reading-section-14)
- [15 与既有知识的连接](#reading-section-15)
- [16 研究候选](#reading-section-16)
<!-- reading-navigation:end -->

<a id="reading-section-01"></a>

## 01 基本信息

| 字段 | 内容 |
|---|---|
| 题目 | DSAINet: An Efficient Dual-Scale Attentive Interaction Network for General EEG Decoding |
| 作者 | Zhiyuan Ma, Zeyuan Li, Zihao Qiu, Jinhao Li, Lingqin Meng, Xinche Zhang, Yixuan Liu, Xinke Shen, Sen Song |
| 单位 | 清华大学生物医学工程学院、清华脑与智能实验室、IDG/McGovern 脑科学研究院；清华大学基础医学院；清华大学心理与认知科学系；南方科技大学生物医学工程系 |
| 载体与年份 | IEEE Journal of Biomedical and Health Informatics 稿件版式；2026；PDF 标记 arXiv:2604.18095v1（2026-04-20）[Paper: PDF p. 1, metadata/footer] |
| DOI | supplied source 中未见 DOI，Not assessable |
| 论文类型 | 方法 / 算法论文 |
| 领域 | 通用 EEG 解码、跨被试学习、多尺度时间建模、轻量注意力网络 |
| 关键词 | EEG；general EEG decoding；subject-independent generalization；dual-scale temporal modeling；attentive interaction [Paper: PDF p. 1, Index Terms] |
| 代码 | https://github.com/zy0929/DSAINet [Paper: PDF p. 1, Abstract] |
| 数据 | 10 个公开数据集、5 类 EEG 范式；论文未贡献新数据集 [Paper: PDF pp. 5-6, Table I] |
| 阅读日期 | 2026-08-30 |
| 在当前研究中的位置 | `[Analysis]` DSAINet 是当前 MI-EEG 主线中的候选统一架构与双时间尺度基线；Paper Card 只评估论文证据，不释放实验、机制或论文 claim。 |

<a id="reading-section-02"></a>

## 02 一句话总结

`[Paper]` DSAINet 先把原始 EEG 压缩为共享时空词元，再以细/粗时间卷积、分支内自注意力、双向跨分支注意力和自适应词元池化完成分类；作者报告该固定架构在十个公开数据集的跨被试评估中取得表内最优或并列最优结果，同时保持约 77K 参数的紧凑规模。[Paper: PDF pp. 1, 3-5, 7-10, Tables III-IV, Fig. 5]

<a id="reading-section-03"></a>

## 03 研究问题

### 具体问题

`[Paper]` 不同 EEG 任务的判别信息具有不同的时间组织和尺度，而许多模型把任务特定的时间归纳偏置写入架构，导致跨任务时需要重新设计或重新设置架构。[Paper: PDF pp. 1-2, Introduction]

### 为什么重要

`[Paper]` 作者把 general EEG decoding 定义为：在跨被试评估中，用共享架构和一致的架构相关超参数处理多个 EEG 任务。该目标同时考察对未见被试的稳健性和跨任务复用性。[Paper: PDF p. 1, S001-S002]

### 为什么已有路线不足

`[Paper-framed; external verification not performed]` CNN 的多尺度提取通常缺少显式的尺度间自适应协调；Transformer 或 CNN-Transformer 混合模型常让注意力同时承担时间依赖、特征细化和融合等多种职责，可能增加复杂度与计算成本。[Paper: PDF pp. 1-3, Introduction and Related Work]

### 精确研究问题

能否在不按数据集改变架构相关超参数的前提下，用轻量双尺度卷积负责时间模式提取、用结构化注意力分别负责尺度内细化和尺度间交互，从而在异质 EEG 任务的跨被试评估中获得稳定的准确率—效率折中？

<a id="reading-section-04"></a>

## 04 研究背景与发展路径

> 本节为 `[Paper-framed; external verification not performed]`。它重构论文自己的 related-work 叙事，不把作者的历史定位当作独立查证的新颖性结论。

| 阶段 | 代表路线 | 论文认可的优势 | 论文指出的局限 | DSAINet 的声称位置 |
|---|---|---|---|---|
| 紧凑 CNN | ShallowConvNet、DeepConvNet、EEGNet | 从原始 EEG 高效学习局部时空模式；EEGNet 用深度可分离卷积降低参数量 | 主要侧重不同时间范围的特征提取，任务相关尺度选择与跨尺度交互有限 | 继承轻量卷积效率，但显式加入双尺度协调 [Paper: PDF p. 2, Sec. II-A] |
| 多分支 / 多尺度 CNN | ADFCNN、CP-MixedNet、MFRC-Net | 扩大或并行覆盖不同感受野 | 多尺度往往在独立提取后简单融合 | 用分支内注意力与分支间交叉注意力拆分“细化”和“整合” [Paper: PDF pp. 1-2] |
| Attention EEG | channel/temporal attention、DAEST | 可选择性强化任务相关表征 | 轻量注意力适应性有限；注意力职责未必清晰 | 把注意力放在卷积已形成的尺度特征之后 [Paper: PDF pp. 2-4] |
| CNN-Transformer | Conformer、MSVTNet、CTNet、Deformer、DBConformer、MSCFormer | 同时建模局部特征、全局依赖和跨域关系 | 深注意力堆栈可能把多种功能耦合并增加成本 | 用两层轻量时间卷积 + 一层浅注意力完成职责分离 [Paper: PDF pp. 2-4, 9, Fig. 3] |
| 通用 EEG 解码 | EEGNet、Conformer、LMDA-Net、Deformer、DBConformer | 展示架构在多个范式中的可用性 | 论文认为仍缺少统一的跨被试、多任务、固定架构评估 | 在十个数据集上以同一组架构超参数评估 [Paper: PDF pp. 3, 6-8] |

`[Analysis]` DSAINet 的核心位置不是“发明多尺度”或“首次把注意力用于 EEG”，而是把三件事组合成一个紧凑合同：共享词元化、显式细/粗时间支路、分层次的尺度内/尺度间注意力。论文证据更适合支持这一系统组合的经验有效性，不足以把其中任一概念单独声明为新颖。

![Figure 1：DSAINet 与代表性 CNN-Transformer 混合架构的结构对照](<./refs/paper-cards/dsainet/assets/fig-01-architecture.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-01-architecture.png>)

*Figure 1｜作者给出的结构对照。该图用于理解 DSAINet 的职责拆分，不构成外部新颖性验证。[Paper: PDF p. 2, Fig. 1]*

<a id="reading-section-05"></a>

## 05 论文识别的核心痛点

| 痛点 | 表现 | 原因或作者解释 | 论文证据 |
|---|---|---|---|
| 时间组织异质 | MI、疾病、负荷、注意等任务的判别信息分布在不同时间尺度 | 任务范式和信号特性不同，跨被试变异进一步改变其表现 | [Paper: PDF p. 1, Introduction; pp. 5-6, Table I] |
| 任务定制架构难复用 | 换任务时需要改时间感受野或结构设计 | 架构包含任务特定时间归纳偏置 | [Paper: PDF pp. 1-2, Introduction] |
| 多尺度提取与协调混在一起 | 独立分支常在末端简单融合，或由注意力同时承担提取、细化和融合 | 职责耦合会增加复杂度，且尺度特异信息未被显式协调 | [Paper: PDF pp. 1-2, Introduction] |
| 跨被试稳健性 | 未见被试的时空表现存在较强变化 | inter-subject variability | [Paper: PDF p. 1, Introduction] |
| 准确率与效率冲突 | 强 CNN-Transformer 可能参数和 MACs 较高 | 深注意力和复杂混合结构增加计算负担 | [Paper: PDF pp. 1-2; p. 10, Fig. 5] |

`[Analysis]` 论文直接展示了“不同数据集上的性能差异”和“固定架构可运行”，但没有直接测量每个任务实际需要哪一种时间尺度。因此，“时间组织异质”是合理的设计动机和作者解释，不是由主实验单独识别出的因果根因。

<a id="reading-section-06"></a>

## 06 核心思想

### 表层方法

`[Paper]` 用两个不同感受野的轻量时间卷积分支提取 fine/coarse 表征，再依次执行分支内自注意力、双向跨分支注意力和加权词元池化。[Paper: PDF pp. 3-5, Fig. 2, Eq. 6-19]

### 核心洞见

`[Paper]` 将“时间模式提取”和“尺度信息协调”显式解耦：卷积承担主要的长短程时间提取，注意力只在已形成的尺度表征上做尺度内细化与尺度间交换。[Paper: PDF pp. 2-4, Sec. III]

### 可迁移的一般经验

`[Analysis]` 对异质任务的统一模型，不一定要用更深的全局模块；更可检验的做法是先给各模块分配单一职责，再用消融分别验证“表示形成”“交互”和“聚合”。这里的重点是职责可审计，而不只是参数少。

<a id="reading-section-07"></a>

## 07 方法总览

### 输入与输出

- `[Paper]` 输入：单试次 EEG，$X\in\mathbb{R}^{C\times T}$，其中 $C$ 为通道数，$T$ 为时间采样点。[Paper: PDF p. 3, Eq. 1]
- `[Paper]` 输出：类别 logits $\hat y$，由两个池化分支表示拼接后线性分类得到。[Paper: PDF p. 5, Eq. 19]

### 数据流

```text
EEG X (C × T)
  -> Shared Spatiotemporal Tokenization
     temporal conv -> channel-spanning depthwise spatial conv
     -> pooling -> temporal conv -> pooling -> projection + position
  -> shared tokens Z0 (N × d)
  -> Fine Temporal Convolution [kernels 3, 7]
  -> Coarse Temporal Convolution [kernels 11, 15]
  -> Intra-Branch Attentive Refinement (self-attention per branch)
  -> Inter-Branch Attentive Interaction (bidirectional cross-attention)
  -> Adaptive Token Aggregation (weighted pooling per branch)
  -> concatenate pf || pc
  -> linear classifier -> logits
```

[Paper: PDF pp. 3-5, Fig. 2, Eq. 1-19]

![Figure 2：DSAINet 完整架构与数据流](<./refs/paper-cards/dsainet/assets/fig-02-overall-architecture.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-02-overall-architecture.png>)

*Figure 2｜共享时空词元化 → 细/粗时间卷积 → 分支内细化 → 分支间交互 → 自适应聚合与分类。该图是理解方法调用链的主图。[Paper: PDF p. 4, Fig. 2]*

### 训练与实现合同

- `[Paper]` 固定架构设置：embedding dimension $d=40$，4 个 attention heads；tokenizer 的 $f_1=16$，时间核 64/16，depth multiplier $D=2$，pooling 4/8；细支路核 3/7，粗支路核 11/15；卷积 expansion ratio 4，FFN expansion ratio 2，dropout 0.25。[Paper: PDF p. 7, Sec. IV-D]
- `[Paper]` 优化：Adam，weight decay $10^{-4}$；batch size、learning rate 和 epochs 按数据集改变，详见 Table II。[Paper: PDF p. 7, Table II]
- `[Paper]` 计算环境：8× NVIDIA GeForce RTX 4090。[Paper: PDF p. 7, Sec. IV-D]
- `[Paper]` 反馈环：标准监督分类训练；论文未描述在线反馈、自适应部署或跨任务联合训练。

### 方法假设

1. `[Analysis]` 在进入双时间分支前，将空间维压缩为单一通道的共享词元仍能保留任务所需空间信息。[Paper: PDF p. 3, Eq. 2-3]
2. `[Paper/Analysis]` 不同 kernel 的并行支路足以形成有意义的细/粗时间尺度；论文用结构命名和分支消融支持有效性，但没有在主文中直接测量 realized receptive field。[Paper: PDF pp. 3-4, Eq. 7-10; pp. 8-9, Table V]
3. `[Paper/Analysis]` 浅层注意力足以完成细化与交互；Fig. 3 提供四个数据集上的深度敏感性证据。[Paper: PDF p. 9, Fig. 3]

<a id="reading-section-08"></a>

## 08 核心模块拆解

| 模块 | 功能 | 为什么需要 | 输入与输出 | 支持证据 | 移除后的已测效果 |
|---|---|---|---|---|---|
| Shared Spatiotemporal Tokenization | 从原始 EEG 形成紧凑共享词元 | 统一不同通道数/时长输入到共同 token 表示 | $X:C\times T\rightarrow Z_0:N\times d$ | 方法定义；未单独整体移除 [Paper: PDF p. 3, Eq. 1-5] | 仅测去 positional embedding：2a 61.79→59.76，2b 76.41→75.71，ADFTD 59.65→57.06 [Paper: PDF p. 8, Table V] |
| Fine/Coarse-Scale Temporal Convolution | 以不同 kernel 捕获局部与更宽时间上下文 | 避免只依赖单一时间范围 | $Z_0\rightarrow Z_f,Z_c$ | 单支路消融 [Paper: PDF pp. 3-4, Eq. 6-10; p. 8, Table V] | 仅细支：59.82/75.94/58.57；仅粗支：60.19/75.74/57.84，均低于完整模型 61.79/76.41/59.65；只支持三项任务中的组合优势 |
| Intra-Branch Attentive Refinement | 同尺度内部自注意力细化 | 强化每支内的 salient token relation | $Z_b\rightarrow Z_b^{ref}$ | 去分支内注意力消融 [Paper: PDF p. 4, Eq. 11-12; p. 8, Table V] | 2a/2b/ADFTD 为 60.07/75.49/58.97 |
| Inter-Branch Attentive Interaction | 细↔粗双向 cross-attention | 交换不同时间尺度上下文 | $(Z_f,Z_c)\rightarrow(Z'_f,Z'_c)$ | 去分支间注意力与去全部 interaction 消融 [Paper: PDF pp. 4-5, Eq. 13-16; p. 8, Table V] | 去 inter：60.14/75.56/57.65；去全部 attentive interaction：59.36/75.90/57.62 |
| Adaptive Token Aggregation | 学习 token 权重并池化 | 避免把所有 token 展平到重分类头，也避免等权平均 | $Z'_b\rightarrow p_b\in\mathbb{R}^d$ | 与平均池化比较 [Paper: PDF p. 5, Eq. 17-18; p. 8, Table V] | 59.82/75.58/56.92；ADFTD 降幅最大 2.73 pp |
| Linear classifier | 拼接两个分支向量并分类 | 以紧凑 readout 输出 logits | $[p_f\Vert p_c]\rightarrow\hat y$ | 无独立 head 对照 [Paper: PDF p. 5, Eq. 19] | Not assessable；没有 matched-parameter nonlinear readout 对照 |

`[Analysis]` Table V 是删减式组合消融。它表明列出的完整组合在三个数据集上优于相应删减版本，但没有证明每个模块在所有十个数据集上都必要，也没有把“模块预期功能”与“其实际实现的功能机制”完全隔离。

<a id="reading-section-09"></a>

## 09 必要公式与符号

### 9.1 共享词元化

$$
X\in\mathbb{R}^{C\times T},\qquad
F=\Phi_{tok}(X)\in\mathbb{R}^{f_2\times1\times N}
$$

$$
\tilde Z=\operatorname{Transpose}(\operatorname{Squeeze}(F))\in\mathbb{R}^{N\times f_2},
\qquad Z^{(0)}=P(\tilde Z)\in\mathbb{R}^{N\times d}
$$

- $C,T,N,d$：通道数、采样点数、token 数、embedding dimension。
- 目的：把不同通道数的 EEG 转为统一 token 序列。
- 直觉：先做局部时间滤波与全通道空间混合，再让后续双时间分支共享同一输入基底。
- 来源：[Paper: PDF p. 3, Eq. 1-5]

### 9.2 轻量时间卷积残差

$$
H_b^{(\ell)}=H_b^{(\ell-1)}+\alpha_b^{(\ell)}\tilde H_b^{(\ell)},\qquad b\in\{f,c\}
$$

其中 $\tilde H_b^{(\ell)}$ 由 depthwise temporal convolution、grouped pointwise expansion/projection、GELU 和 BN 组成；$\alpha_b^{(\ell)}$ 是可学习残差缩放。

- 目的：以低成本堆叠不同 kernel 的时间变换。
- 直觉：每层学习一个受标量门控的时间残差，而不是重写整支表示。
- 来源：[Paper: PDF pp. 3-4, Eq. 7-8]

### 9.3 分支内自注意力

$$
\bar Z_b^{(m)}=\operatorname{LN}\bigl(Z_b^{(m-1)}+
\operatorname{MHA}(Z_b^{(m-1)},Z_b^{(m-1)},Z_b^{(m-1)})\bigr)
$$

$$
Z_b^{(m)}=\operatorname{LN}\bigl(\bar Z_b^{(m)}+\operatorname{FFN}(\bar Z_b^{(m)})\bigr)
$$

- 目的：在已形成的单一尺度内细化 token 关系。
- 来源：[Paper: PDF p. 4, Eq. 11-12]

### 9.4 双向跨分支交互

$$
\bar Z_f=\operatorname{LN}\bigl(Z_f+\beta_1\operatorname{MHA}(Z_f,Z_c,Z_c)\bigr)
$$

$$
\bar Z_c=\operatorname{LN}\bigl(Z_c+\beta_2\operatorname{MHA}(Z_c,Z_f,Z_f)\bigr)
$$

- $\beta_1,\beta_2$：两个交互方向的可学习强度。
- 目的：让 fine query 吸收 coarse context，同时让 coarse query 吸收 fine detail。
- 直觉：两个方向共享“交互范式”，但 query 与 key/value 的角色相反。
- 来源：[Paper: PDF pp. 4-5, Eq. 13-16]

### 9.5 自适应词元聚合与分类

$$
w_{b,n}=\frac{\exp(q^\top z_{b,n})}{\sum_{j=1}^{N}\exp(q^\top z_{b,j})},
\qquad p_b=\sum_{n=1}^{N}w_{b,n}z_{b,n}
$$

$$
\hat y=W_{cls}[p_f\Vert p_c]+b_{cls}
$$

- $q$：实现中两分支共享的可学习 token 打分向量。
- 目的：把可变长度 token 序列压缩为两个 $d$ 维分支向量。
- 来源：[Paper: PDF p. 5, Eq. 17-19]

### 9.6 编号公式覆盖索引

下表补齐方法链中的全部编号公式。上文已展开核心公式；这里只说明其在数据流中的位置，避免把相邻的 reshape、残差和 FFN 更新误当成独立贡献。

| 论文公式 | 作用 | 定位 |
|---|---|---|
| Equation 1 | 定义输入 $X\in\mathbb{R}^{C\times T}$ | [Paper: PDF p. 3, Equation 1] |
| Equation 2 | tokenizer 输出特征 $F$ | [Paper: PDF p. 3, Equation 2] |
| Equation 3 | squeeze + transpose 得到 token 序列 $\tilde Z$ | [Paper: PDF p. 3, Equation 3] |
| Equation 4 | 投影到统一 embedding $Z^{(0)}$ | [Paper: PDF p. 3, Equation 4] |
| Equation 5 | 缩放并加入 learnable positional encoding，得到 $Z_0$ | [Paper: PDF p. 3, Equation 5] |
| Equation 6 | 转成 channel-first 的 $H_0=Z_0^\top$ | [Paper: PDF p. 3, Equation 6] |
| Equation 7 | 定义 depthwise temporal + grouped pointwise 的分支变换 $\tilde H_b^{(\ell)}$ | [Paper: PDF p. 3, Equation 7] |
| Equation 8 | 以 $\alpha_b^{(\ell)}$ 缩放的时间卷积残差更新 | [Paper: PDF p. 4, Equation 8] |
| Equation 9 | 把两个时间分支恢复为 token form $Z_f,Z_c$ | [Paper: PDF p. 4, Equation 9] |
| Equation 10 | 以 $\alpha_1,\alpha_2$ 把共享 token 回注入两分支 | [Paper: PDF p. 4, Equation 10] |
| Equation 11 | 分支内 MHA 残差与 layer normalization | [Paper: PDF p. 4, Equation 11] |
| Equation 12 | 分支内 FFN 残差与 layer normalization | [Paper: PDF p. 4, Equation 12] |
| Equation 13 | fine query 从 coarse key/value 吸收信息 | [Paper: PDF p. 4, Equation 13] |
| Equation 14 | fine 方向 cross-attention 后的 FFN 更新 | [Paper: PDF p. 5, Equation 14] |
| Equation 15 | coarse query 从 fine key/value 吸收信息 | [Paper: PDF p. 5, Equation 15] |
| Equation 16 | coarse 方向 cross-attention 后的 FFN 更新 | [Paper: PDF p. 5, Equation 16] |
| Equation 17 | softmax token 权重 $w_{b,n}$ | [Paper: PDF p. 5, Equation 17] |
| Equation 18 | 加权池化分支向量 $p_b$ | [Paper: PDF p. 5, Equation 18] |
| Equation 19 | 拼接两分支并线性分类 | [Paper: PDF p. 5, Equation 19] |
| Equation 20 | ACC 定义 | [Paper: PDF p. 7, Equation 20] |
| Equation 21 | weighted F1 定义 | [Paper: PDF p. 7, Equation 21] |

<a id="reading-section-10"></a>

## 10 实验设计与证据链

### 10.1 数据、协议与预算

| 维度 | 论文设置 |
|---|---|
| 范式与数据集 | MI：BCIC-IV-2a、2b、Zhou2016、OpenBMI、PhysioNet-MI；精神障碍：Mumtaz2017；神经退行性：ADFTD、Rockhill2021；心理负荷：EEGMat；认知注意：Shin2018 [Paper: PDF pp. 5-6, Table I] |
| 总体规模 | 9-109 subjects；3-64 channels；1,800-21,600 trials；2-4 classes [Paper: PDF p. 6, Table I] |
| 预处理 | MI、Rockhill2021、Shin2018：0.5-40 Hz；ADFTD/EEGMat：0.5-45 Hz；Mumtaz2017：0.3-75 Hz + 50 Hz notch；channel-wise z-score [Paper: PDF pp. 5-6] |
| 跨被试协议 | 2a、2b、Zhou2016 用 LOSO；其余 10-fold subject-level CV，Rockhill2021 用 5-fold [Paper: PDF pp. 6-7, Table II] |
| LOSO 验证集 | 每个训练被试内部按标签分层保留 20% samples 做 validation；剩余 80% training [Paper: PDF p. 6, Sec. IV-C] |
| k-fold 验证集 | 一折 test；从剩余折中随机选一折 validation；其余 training [Paper: PDF pp. 6-7, Sec. IV-C] |
| 指标与不确定性 | ACC、weighted F1；5 seeds；对所有 folds 或 LOSO runs 与 seeds 汇总 mean±std [Paper: PDF p. 7, Eq. 20-21] |
| 基线 | 13 个代表模型：Shallow/DeepConvNet、EEGNet、ADFCNN、Conformer、LMDA-Net、MSVTNet、CTNet、TMSA-Net、MGFormer、Deformer、DBConformer、MSCFormer；不同表因适用性未必每项齐全 [Paper: PDF p. 6; pp. 8, Tables III-IV] |
| 训练预算 | architecture fixed；batch/LR/epochs dataset-specific。MI 多为 100 epochs；多项非 MI 为 30 epochs；无 wall-clock、每模型调参预算或独立重复训练成本表 [Paper: PDF p. 7, Table II] |
| oracle input | 无显式 oracle；标签用于监督训练、分层和验证选择。论文未说明模型选择是否对所有基线使用完全一致的搜索预算。 |
| end-to-end status | 从预处理 EEG 到分类为离线 end-to-end supervised decoder；不包含采集、实时推理、部署或闭环 BCI。 |

### 10.2 Claim-evidence matrix

| 实验 | 检验的主张 | 比较与条件 | 结果 | 可支持结论 | 不能支持的更强结论 | 来源 |
|---|---|---|---|---|---|---|
| 五个 MI 数据集主比较 | 固定架构能适用于异质 MI 设置 | subject-independent；ACC/weighted F1；11-12 个方法 | DSAINet ACC：61.79、76.41、78.21、82.89、63.90；2b F1 与 DBConformer 同为 75.91 | 在论文给定 pipeline 和汇总方式下，DSAINet 在五个 MI 表内 ACC 均最高 | 对所有 MI 数据、设备域或预处理都最优；差异统计显著 | [Paper: PDF p. 8, Table III] |
| 五个非 MI 数据集主比较 | 架构优势不局限于 MI | 四类其他任务；subject-level CV | ACC/F1 均列第一；Shin2018 相对第二名 +2.46/+2.63 pp | 表内结果与跨范式复用相一致 | 未见范式的零样本迁移；跨任务联合训练能力 | [Paper: PDF pp. 7-8, Table IV] |
| 位置编码消融 | token order cue 有用 | 去 positional embedding，三项任务 | ACC 分别降低 2.03、0.70、2.59 pp | 在三项任务的当前实现中，位置编码与性能相关 | 位置编码在所有十项任务中必要；降幅只由 token order 机制导致 | [Paper: PDF p. 8, Table V] |
| 双尺度分支消融 | 两支组合优于单支 | single fine / single coarse vs full | 三项任务中 full 均最高；2b 上 single fine 75.94 接近 full 76.41 | 组合在三项任务上提供小到中等增益 | 两支一定学习到固定的生理 fine/coarse 语义；两支在每个样本上互补 | [Paper: PDF pp. 8-9, Table V] |
| 注意力消融 | 尺度内细化与尺度间交互有贡献 | 去全部 interaction、去 intra、去 inter | 三项任务均低于 full；降幅随数据集变化 | 这些模块在三项代表任务中具有组合效用 | 每个 attention map 的视觉结构就是效用来源；双向方向均独立必要 | [Paper: PDF pp. 8-9, Table V] |
| 聚合消融 | 学习 token 权重优于均值池化 | adaptive aggregation vs average pooling | ADFTD 59.65→56.92，2a 61.79→59.82，2b 76.41→75.58 | 当前三项任务中自适应聚合优于简单均值 | 学到的权重是可靠时域解释；共享 $q$ 最优 | [Paper: PDF pp. 8-9, Table V] |
| 架构深度敏感性 | 紧凑深度已足够 | temporal blocks 1-4；attention layers 0-3；四数据集 | 2 个 temporal blocks 和 1 个 attention layer整体最佳或近最佳 | 深度增加收益有限，支持紧凑选择 | 搜索覆盖全部重要超参数；该深度对所有十数据集最优 | [Paper: PDF p. 9, Fig. 3] |
| segment length | 对切段长度不过度敏感 | 四个非 MI 数据集，多种时长 | 多数在中等窗口附近最佳；模式因数据集不同 | 在测试范围内性能对时长具有一定稳健性 | 任意切段策略都稳健；时长变化与样本数量变化已完全解耦 | [Paper: PDF p. 10, Fig. 4] |
| 复杂度比较 | 准确率—效率折中有利 | PhysioNet-MI；MACs、parameters、ACC | 76.99K、73.67 MMACs、63.87% ACC；Deformer 2.60M、586.92 MMACs、63.37% | 离线静态复杂度和参数规模有利 | 实机低延迟、低功耗或高吞吐部署已验证 | [Paper: PDF p. 10, Fig. 5] |
| saliency 与 attention 可视化 | 模型学习任务相关的空间/交互结构 | 8 个代表数据集显著性图；3 个数据集注意力图 | 图样随数据集而变，部分与已知脑区叙述相容 | 提供与任务相关表征一致的后验解释线索 | 脑机制因果发现；attention weight 等同 explanation | [Paper: PDF pp. 10-12, Figs. 6-7] |

### 10.3 主要图表的论证角色清单

- `[Paper]` Fig. 1：把 DSAINet 与 Conformer/CTNet、MSVTNet/MSCFormer、Deformer 的职责组织方式作结构对照。[Paper: PDF p. 2, Fig. 1]
- `[Paper]` Fig. 2：完整数据流与各模块关系，是方法主图。[Paper: PDF p. 4, Fig. 2]
- `[Paper]` Fig. 3：时间卷积块数与注意力深度的敏感性。[Paper: PDF p. 9, Fig. 3]
- `[Paper]` Fig. 4：四个数据集的 segment length 敏感性。[Paper: PDF p. 10, Fig. 4]
- `[Paper]` Fig. 5：PhysioNet-MI 的 ACC、MACs 与参数量折中。[Paper: PDF p. 10, Fig. 5]
- `[Paper]` Fig. 6：八个代表数据集的平均显著性图。[Paper: PDF pp. 10-11, Fig. 6]
- `[Paper]` Fig. 7：三数据集的 intra/inter attention map。[Paper: PDF pp. 11-12, Fig. 7]
- `[Paper]` Table I：十数据集规模、通道、任务与切段设置。[Paper: PDF p. 6, Table I]
- `[Paper]` Table II：各数据集 batch、LR、epochs 与 protocol；揭示“固定架构、可变优化”的边界。[Paper: PDF p. 7, Table II]
- `[Paper]` Tables III-IV：十数据集主性能比较。[Paper: PDF p. 8, Tables III-IV]
- `[Paper]` Table V：三项代表任务的组件消融。[Paper: PDF p. 8, Table V]

### 10.4 图形证据阅读

![Figure 3：架构深度敏感性](<./refs/paper-cards/dsainet/assets/fig-03-hyperparameter-sensitivity.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-03-hyperparameter-sensitivity.png>)

*Figure 3｜两个 Temporal Convolution blocks 与一层 attention 在四个代表数据集上整体最佳或近最佳。它支持紧凑配置选择，但不是全部架构超参数的完整搜索。[Paper: PDF p. 9, Fig. 3]*

![Figure 4：segment length 敏感性](<./refs/paper-cards/dsainet/assets/fig-04-segment-length.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-04-segment-length.png>)

*Figure 4｜不同任务对片段长度呈现不同曲线；中等窗口通常较稳健。长度变化同时改变时间上下文与样本构造，因此不能只解释为模型时间感受野变化。[Paper: PDF p. 10, Fig. 4]*

![Figure 5：PhysioNet-MI 的准确率—效率比较](<./refs/paper-cards/dsainet/assets/fig-05-accuracy-efficiency.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-05-accuracy-efficiency.png>)

*Figure 5｜横轴为静态 MACs、气泡为参数量。该图支持离线复杂度优势，不等同于目标设备上的 latency、memory 或 energy 证据。[Paper: PDF p. 10, Fig. 5]*

<a id="reading-section-11"></a>

## 11 结论的正确解释

### 论文证据能够支持

1. `[Paper]` 在作者给定预处理、训练与跨被试协议下，DSAINet 使用同一组架构相关超参数，在十个已评估数据集的表内 ACC 均第一，weighted F1 第一或并列第一。[Paper: PDF pp. 7-8, Tables II-IV]
2. `[Paper]` 在 BCIC-IV-2a、BCIC-IV-2b 和 ADFTD 上，完整模型优于列出的单支路、去注意力和均值池化变体。[Paper: PDF pp. 8-9, Table V]
3. `[Paper]` 在 PhysioNet-MI 的离线静态计算量比较中，DSAINet 位于有利的 ACC—MACs—parameters 区域。[Paper: PDF p. 10, Fig. 5]
4. `[Paper]` 架构深度和 segment length 分析说明主配置在有限搜索范围内是稳定、紧凑的操作点。[Paper: PDF pp. 9-10, Figs. 3-4]

### 必须保留的边界

- **任务范围：** 十个数据集覆盖五类范式，但每个数据集分别训练；不是一个模型权重跨十任务联合训练，也不是 unseen-task zero-shot transfer。[Analysis; Paper: PDF pp. 5-8]
- **协议范围：** 跨被试不等于跨数据集、跨设备或跨中心。LOSO 与 subject-level CV 也不是同一统计单位。[Analysis; Paper: PDF pp. 6-7]
- **固定内容：** 固定的是 architecture-related hyperparameters；batch size、learning rate、epochs 和 protocol 随数据集变化。[Paper: PDF p. 7, Table II]
- **不确定性：** mean±std 是在 seeds 与 folds/subjects 的集合上汇总；论文未给出成对统计检验、置信区间或每被试差值分布，因此不能仅凭均值差宣称统计显著。[Analysis; Paper: PDF p. 7, Sec. IV-E]
- **基线公平性：** 论文列出 13 个基线和结果，但主文未完整披露每个基线的搜索空间、early stopping/model selection 细节、实际训练预算与代码版本；“全部公平调优”不能从主文单独确认。[Analysis; Paper: PDF pp. 6-8]
- **最难情况：** BCIC-IV-2b 的 ACC 优势仅 0.04 pp，F1 与 DBConformer 同为 75.91；这说明统一架构可用，但该数据集上优势很弱。[Analysis; Paper: PDF p. 8, Table III]
- **部署：** MACs 和参数量是离线 proxy；没有端侧延迟、吞吐、显存、功耗或实时闭环证据。[Paper: PDF pp. 10, 12]
- **解释性：** saliency/attention 图是后验关联可视化，不构成神经生理因果证据。[Analysis; Paper: PDF pp. 10-12, Figs. 6-7]

### 有界重述

`[Analysis]` 最稳妥的结论是：DSAINet 提供了一个约 77K 参数、职责分明的双尺度 EEG 分类架构；在论文所选的十个公开数据集和各自跨被试协议中，它以固定架构配置取得了稳定的表内竞争力。现有证据支持这一架构作为紧凑、多任务可复用基线，但尚不足以证明跨数据集机制恒定、统计显著优于全部基线、实时部署有效，或具有已验证的神经生理机制。

### 解释性图像的正确读法

> 下列图像都是后验关联可视化。它们可以说明模型归因与任务相关脑区/时间结构相容，但不能单独证明真实神经生理机制、因果定位或 attention weight 等同 explanation。

![Figure 6：八个代表数据集的平均显著性图](<./refs/paper-cards/dsainet/assets/fig-06-saliency-maps.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-06-saliency-maps.png>)

*Figure 6｜显著性分布随数据集变化，并与作者引用的任务相关脑区叙述相容；需要 deletion、shuffle 与随机化 sanity checks 才能提升机制解释强度。[Paper: PDF pp. 10-11, Fig. 6]*

![Figure 7：分支内与分支间注意力模式](<./refs/paper-cards/dsainet/assets/fig-07-attention-patterns.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-07-attention-patterns.png>)

*Figure 7｜三数据集上的 intra/inter attention pattern 不同。图样支持“交互并非固定模板”的描述，但不直接隔离其 label utility 或两个方向的独立必要性。[Paper: PDF pp. 11-12, Fig. 7]*

<a id="reading-section-12"></a>

## 12 作者明确承认的局限

| 局限 | 具体表现 | 作者提出的未来方向 | 来源 |
|---|---|---|---|
| 缺少 EEG-specific priors | task-agnostic tokenizer/attention 没有显式使用电极拓扑、解剖结构或频率依赖特征 | 在保留共享 backbone 的前提下发展 structure-aware DSAINet | [Paper: PDF p. 12, Sec. VI] |
| 部署效率未验证 | 效率主要以离线复杂度比较评估 | compression、pruning、distillation，用于低延迟 EEG 解码 | [Paper: PDF p. 12, Sec. VI] |
| 泛化范围有限 | 证据只覆盖已评估设置，不是所有 EEG 场景的最终方案 | 更广范式、更大跨被试 benchmark，并继续研究 task-adaptive multi-scale behavior | [Paper: PDF p. 12, Sec. VI] |

<a id="reading-section-13"></a>

## 13 批判性分析

| `[Analysis]` 观察 | 潜在问题或替代解释 | 为什么重要 | 如何检验 | 依据 |
|---|---|---|---|---|
| “固定架构”与“固定训练合同”不是一回事 | 优化超参数、epochs 和 CV/LOSO 协议变化可能贡献跨数据集稳定性 | 决定 generality 是来自 architecture 还是 dataset-specific optimization | 冻结统一 training profile，与原 dataset-specific profile 成对比较；报告每数据集性能下降和失败率 | [Paper: PDF p. 7, Table II] |
| 双尺度是结构定义，不等于 realized function | 不同 kernel 可能学到相似或近 identity 的变换 | 影响“fine/coarse 协同”的机制解释和后续创新入口 | 冻结 checkpoint 做 effective receptive-field/occlusion、residual observability 和 branch-role stability audit；预先定义方向门与不可观测停止规则 | [Paper: PDF pp. 3-4, Eq. 7-10; p. 8, Table V] |
| 消融只覆盖三项任务 | 组件贡献可能显著依赖数据条件 | 不能把必要性外推到全部十项任务 | 在其余七数据集做轻量 paired ablation 或先做 frozen source-only diagnostic；按 task/seed/subject 报告 | [Paper: PDF p. 8, Table V] |
| 汇总 std 的统计单位不透明 | folds、subjects、seeds 直接混合可能掩盖层级相关性 | 小优势尤其容易被误读为稳定优胜 | 使用以 subject 为单位的 paired difference、层级 bootstrap 或 seed×subject matrix；公开 per-unit predictions | [Paper: PDF p. 7, Sec. IV-E; p. 8, Tables III-IV] |
| baseline tuning budget 未充分披露 | DSAINet 和强基线可能接受不同程度的调参或实现适配 | 影响排行榜因果归因 | 固定 preprocessing、split、early stopping、search space、seed 和 compute cap；审计每模型 config 与 prediction | [Paper: PDF pp. 6-8] |
| 空间信息在双时间支路前已压缩 | 两支共享单一空间基底，无法直接形成 scale-conditioned spatial representation | 若时间尺度与空间拓扑存在交互，现有结构可能提前丢失 | 先做 branch-conditioned spatial perturbation audit；若无稳定差异则停止，不直接加图模块 | [Paper: PDF p. 3, Eq. 2-3; p. 12, Sec. VI] |
| saliency 与 attention 解释可能过强 | 后验权重既可能反映决策证据，也可能反映相关噪声或结构偏置 | 决定可解释性是否能支撑神经生理叙述 | 做 electrode/time-window deletion、label-preserving shuffle、sanity randomization、fold/subject stability，并关联 prediction change | [Paper: PDF pp. 10-12, Figs. 6-7] |
| 静态复杂度不等于部署效率 | GPU kernel、memory access、batch size 与序列长度会改变实测 latency | 影响“高效”的实际含义 | 在目标设备上以 batch=1 报告 latency、peak memory、energy、throughput 和 cold/warm start | [Paper: PDF p. 10, Fig. 5; p. 12, Sec. VI] |

<a id="reading-section-14"></a>

## 14 学到的知识

### Agent-derived knowledge candidates

1. **职责拆分比统一使用 attention 更容易审计。** `[Analysis]` 当 convolution、self-attention、cross-attention 和 pooling 各自承担明确功能时，可用更直接的删减实验定位效用；代价是仍需额外 functional diagnostic 验证模块是否真的实现其命名职责。
2. **“共享架构”应拆为三层。** `[Analysis]` 架构拓扑是否固定、架构超参数是否固定、优化协议是否固定是三个不同命题。DSAINet 固定前两者的大部分内容，但允许训练配置因数据集改变。[Paper: PDF p. 7, Table II]
3. **双尺度结构需要 realized-scale 证据。** `[Analysis]` kernel 大小只规定 nominal receptive field；学习到的残差、有效影响范围和最终决策贡献需要从 checkpoint 中测量。
4. **消融回答“删掉会怎样”，不自动回答“为什么有效”。** `[Analysis]` Table V 支持组合效用，却不能单独确认 attention map、跨尺度互补性或生理时间尺度就是增益来源。
5. **轻量模型的效率证据至少分三层。** `[Analysis]` parameters / MACs 属于静态工程 proxy；实际 latency / memory / energy 属于部署证据；闭环 BCI 的稳定性属于系统证据。论文只覆盖第一层。[Paper: PDF pp. 10, 12]
6. **统一模型的统计汇总必须尊重层级。** `[Analysis]` seed、fold 和 subject 的重复不是简单独立样本；公开 unit-level 结果比单个 mean±std 更适合判断稳定性。

<a id="reading-section-15"></a>

## 15 与既有知识的连接

### 15.1 论文内部连接

- `[Paper-framed]` DSAINet 与 EEGNet/LMDA-Net 共享“跨范式紧凑架构”的目标，与 ADFCNN/MSVTNet/MSCFormer 共享多尺度提取思路，与 Deformer/DBConformer 共享 convolution-attention 混合路线；它的区别主要是把尺度提取、尺度内细化和跨尺度交互显式分层。[Paper: PDF pp. 2-4]
- `[Analysis]` 与标准 Transformer “用 attention 直接承担全局建模”相比，DSAINet 更接近 convolution-first、attention-as-refinement 的设计哲学。这可能解释为什么一层 attention 已足够，但该解释仍需 matched-compute 对照。[Paper: PDF p. 9, Fig. 3]

### 15.2 与当前仓库 DSAINet 证据地图的连接

> 以下不是论文证据，也不是外部文献验证；它们是当前项目中已冻结、范围受限的 machine diagnostics。所有结论保持 `claim_release=none`。

| 论文叙述 | `[User]` 当前项目证据 | 连接后的正确理解 |
|---|---|---|
| 不同 kernel 对应 fine/coarse temporal modeling | BNCI2014001 official-preproc LOSO 的 RBIA 在 45 checkpoints 上支持方向性 effective-scale separation，median ratio 2.1556；但不能升级为生理语义 | `[Analysis]` 论文的 nominal scale 在一个冻结 scope 中获得 realized-scale 支持，但不是跨数据集恒定机制。项目依据：`docs/notes/DSAINET_BASELINE_EVIDENCE_MAP_2026-08-26.md` Sec. 1-2 |
| 两支应协同且都被使用 | 001 中两支 contribution 均实质、identity same-index stable；高 CKA 不等于双向可替代 | `[Analysis]` “共存”有局部诊断支持，但“互补 label utility”不能由表示依赖直接推出。项目依据：同上 Sec. 2.2、4.1 |
| 跨任务使用统一双尺度结构 | BNCI2014004 中 scale-specific residual，尤其 branch2，常近 identity/不可观测；但 downstream slot 仍被使用，且没有稳定 performance-harm anchor | `[Analysis]` 统一架构可以在不同数据集有效，不意味着各数据条件下由同一内部尺度机制实现。项目依据：同上 Sec. 1、4.2 |
| cross-branch interaction 具有功能 | fixed lag/equalizer、fixed product readout、direction-indexed residual adapter 等多个窄入口已关闭；广义 interaction 问题仍未知 | `[Analysis]` 论文消融支持 native interaction module 的组合效用，但不能为已关闭的替代路线转移 signal，也不能证明所有 interaction 机制。项目依据：同上 Sec. 4.1 |
| 作者提出 structure-aware future work | 项目证据尚未为 topology-conditioned model 提供正式性能锚点 | `[Analysis]` 下一步应先做低成本、可证伪的空间敏感性诊断，而不是把“作者局限”直接当作新模块授权。项目依据：同上 Potential intervention link |

### 15.3 外部知识状态

`Not assessable as externally verified.` 本轮没有进行专门文献查新，因此不声明 DSAINet 的首创性，也不判断 Section 16 候选是否已有充分 prior art。

<a id="reading-section-16"></a>

## 16 研究候选

> 以下均为 `Agent-derived research candidates`，不是已授权实验、已登记 family、创新结论或论文 claim。所有候选的创新状态均为 `unverified; prior-art search required`。

### 候选 A：Branch-conditioned Spatial Sensitivity Audit

- **来源缺口：** tokenizer 在进入双时间支路前执行跨全部通道的空间压缩；作者也承认没有显式电极拓扑/解剖先验。[Paper: PDF p. 3, Eq. 2-3; p. 12, Sec. VI]
- **核心假设 `[Hypothesis]`：** 在至少一项主要数据条件下，fine 与 coarse 分支对局部邻域、半球和全局通道扰动呈现稳定且不同的敏感性；现有共享空间基底没有充分表达这种 time-scale × spatial-topology interaction。
- **相对论文的 delta：** 第一阶段不改模型，只测 frozen checkpoint 的分支条件空间敏感性；只有通过预冻结门后，才允许讨论轻量 topology-conditioned residual。
- **初始方法：** 使用固定 montage 定义 local-neighborhood、hemisphere 和 global-channel perturbations；比较 branch residual、pooled representation、logits 和 target/seed-stable difference-in-differences。
- **验证：** 先在 BNCI2014001 主 scope 做 source-only audit；matched perturbation strength，固定 trials/checkpoints；主指标为 branch×perturbation interaction effect 与方向稳定性。
- **直接 falsifier：** 两分支的相对空间敏感性差异接近零、跨 seed/target 不稳定，或差异不传递到 logits；触发后不进入训练模块。
- **可能失败原因：** 共享空间压缩已足够；电极 montage 太稀疏；扰动引入非生理分布偏移；空间差异存在但与标签效用无关。
- **已知负面边界：** 不把通道 index kernel 当拓扑；不假定 long time=global space、short time=local space；不重开 hard routing、simple modulation 或 branch reweighting。
- **创新状态：** unverified; prior-art search required。

### 候选 B：Architecture-vs-Optimization Generality Decomposition

- **来源缺口：** 论文固定 architecture-related hyperparameters，但 batch、LR、epochs 与 protocol 随数据集变化。[Paper: PDF p. 7, Table II]
- **核心假设 `[Hypothesis]`：** DSAINet 的跨数据集稳定性主要来自共享架构，而不是数据集特异优化设置；在统一 training profile 下，其相对基线优势应大部分保留。
- **相对论文的 delta：** 不改变模型；新增统一优化合同与原论文配置的成对比较。
- **初始方法：** 选择代表性小/大数据集和 MI/非 MI 任务；冻结 optimizer、LR schedule、epoch cap、early stopping 与 compute budget；同时保留原配置 arm。
- **验证：** 对 DSAINet 和至少一个紧凑 CNN、一个强 hybrid baseline 使用完全一致预算；报告 seed×subject paired ACC/F1、失败率、收敛速度和 rank stability。
- **直接 falsifier：** 统一 profile 下 DSAINet 的跨任务 rank 或性能显著崩溃，且原 dataset-specific 设置才能恢复。
- **可能失败原因：** 单一 profile 对不同规模数据本就不合理；baseline 对超参数敏感性不同；预算公平与最佳性能目标冲突。
- **创新状态：** unverified; prior-art search required。

### 候选 C：Deployment-grounded Efficiency Verification

- **来源缺口：** 作者明确说明效率主要基于离线复杂度比较，尚无部署评估。[Paper: PDF pp. 10, 12, Fig. 5 and Sec. VI]
- **核心假设 `[Hypothesis]`：** DSAINet 的低 parameters/MACs 能在目标硬件 batch=1 推理中转化为更低 latency、peak memory 和 energy，而不被 attention/kernel launch overhead 抵消。
- **相对论文的 delta：** 架构和权重不变；把效率证据从静态 proxy 扩展到实机测量。
- **初始方法：** 固定输入长度、precision、warm-up、线程、batch=1；在 CPU、消费级 GPU 和至少一种边缘设备上与 EEGNet、Deformer 或其他适用强基线比较。
- **验证：** median/P95 latency、throughput、peak RAM/VRAM、energy per trial、模型加载时间；同时核对输出数值一致性。
- **直接 falsifier：** 在目标设备上 latency/energy 不优于更简单 baseline，或低 MACs 未转化为可重复的实际收益。
- **可能失败原因：** 小 attention 算子受 kernel launch 限制；运行库优化差异；I/O 与预处理主导总延迟；量化破坏精度。
- **创新状态：** unverified; prior-art search required。

### 候选 D：Hierarchical Uncertainty Re-analysis

- **来源缺口：** 论文报告跨 folds/LOSO runs 与五 seeds 的 mean±std，但没有展示 subject-level paired uncertainty 或统计检验。[Paper: PDF p. 7, Sec. IV-E]
- **核心假设 `[Hypothesis]`：** 主表优势在以 subject 为一级统计单位、控制 seed 重复后仍保持正方向，且不是少数 subjects 或 folds 驱动。
- **相对论文的 delta：** 不重训时可先用已有 per-unit predictions 重算；只改变统计分析层。
- **初始方法：** 建立 dataset×seed×subject/fold 的配对矩阵；使用 hierarchical bootstrap 或 mixed-effects model，报告 effect size、interval、win/tie/loss 和 hardest subjects。
- **验证：** 对所有主基线或至少 second-best baseline 重算 ACC/F1；预先固定 primary contrast 和 multiplicity 处理。
- **直接 falsifier：** 区间跨零、优势集中于少数被试，或排名对 seed/validation fold 高度不稳。
- **可能失败原因：** 缺少可配对 predictions；不同基线 split/index 不一致；小被试数据集统计功效有限。
- **创新状态：** unverified; prior-art search required。

[返回章节导航](#reading-top)
