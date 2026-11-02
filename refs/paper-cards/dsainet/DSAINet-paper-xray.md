# DSAINet X-Ray：双尺度从哪里来，交互究竟做了什么

> 阅读日期：2026-10-14。原文：Ma 等，*DSAINet: An Efficient Dual-Scale Attentive Interaction Network for General EEG Decoding*，本地 PDF 标记 arXiv:2604.18095v1，2026-04-20。
> 阅读范围：完整 13 页 PDF，包括正文、公式 1–21、Figures 1–7、Tables I–V、脚注及参考文献列表；没有另附的 appendix 或 supplementary material。本次回到 PDF 核查关键公式、协议和数值，复用已有 Reader 与图片；未检查作者代码、未复现实验、未外查参考文献。
> 原文 SHA-256：`c71585841480ba3d9697480d4d1d803a22a4efdb7db94250d175a72b8c90678f`。
> 本文中“原文”表示作者报告；“阅读判断”表示据此作出的解释；“教学例子”是人为构造的数值，不是论文实验。研究路径是从成稿重建的设计逻辑，不能当作作者真实的实验时间线。

<!-- reading-navigation:start -->
<a id="reading-top"></a>

[全部论文](<../README.md>) · [综合笔记](<DSAINet-note.md>) · [研究卡片](<DSAINet-paper-card.md>) · **设计精读** · [原文对照](<DSAINet-paper.md>)

**章节导航**

- [一、先把这篇论文真正解决的问题说准确](#reading-section-01)
- [二、作者押注的是什么：先形成表征，再协调表征](#reading-section-02)
- [三、沿数据流看清楚：两个尺度共享什么，又在哪里分开](#reading-section-03)
- [四、把关键公式算一遍](#reading-section-04)
- [五、哪些设计真的贡献了结果](#reading-section-05)
- [六、主结果究竟有多强：把赢的幅度和实验条件放在一起](#reading-section-06)
- [七、逐张图读：作者希望你相信什么，图又保留了什么反证](#reading-section-07)
- [八、读完应该带走的设计认识](#reading-section-08)
- [来源与既有材料](#reading-section-09)
<!-- reading-navigation:end -->

<a id="reading-section-01"></a>

## 一、先把这篇论文真正解决的问题说准确

DSAINet 提供一套可以在不同 EEG 数据集上分别训练、而不用为每个任务重新设计主体结构的轻量分类架构。其关键安排是：先用共同的时空编码器压缩输入，再用不同卷积核形成两路时间表征；在各路内部做 self-attention，再让两路通过 cross-attention 交换内容，最后学习哪些 token 值得进入分类向量。作者在十个公开数据集上报告了表内领先的结果，并在 PhysioNet-MI 上报告约 77K 参数的复杂度。[原文：PDF pp. 1–5、7–10]

这里的“通用”首先是**结构可复用**。它没有展示一套训练好的权重直接处理未见任务，也没有把十个数据集联合训练为一个基础模型。不同数据集仍使用不同训练过程、输入通道和类别数，训练超参数与预处理也会变化。因而读这篇论文时真正要追问的是：同一种模块组织方式为什么能适应不同时间特征，而不是它如何实现零样本跨任务迁移。[原文：PDF pp. 1、6–7；阅读判断]

最有说服力的证据是 Tables III–IV 的跨数据集表现；最容易被读过头的是把这种表现进一步解释为“已经证明了尺度互补机制”“所有被试上都稳定领先”或“已经具备实时部署优势”。下面沿着设计和证据之间的距离展开。

<a id="reading-section-02"></a>

## 二、作者押注的是什么：先形成表征，再协调表征

### 1. 起点不是 EEG 缺少一个更大的网络

引言承认已有 CNN、attention 和混合架构已经能提取多尺度特征。作者指出的困难是：特征提取与尺度协调常常混在一起。独立多尺度分支若只在末端拼接，分支在形成表示时不能利用对方内容；若把各种职责都交给深 attention，又可能增加复杂度。[原文：PDF pp. 1–3]

这一论证隐含一个可检验的押注：**卷积先做足够好的时间表示后，浅 attention 就足以承担协调工作**。若必须不断加深 attention 才能获得表现，这个紧凑化理由便会减弱；若末端拼接同样有效，中途交互的理由也会减弱。Fig. 3 和 Table V 分别承担这两部分证据。

### 2. Figure 1 是设计主张，不是机制实验

![Figure 1：DSAINet 与其他混合架构的结构比较](<./refs/paper-cards/dsainet/assets/fig-01-architecture.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-01-architecture.png>)

图中 DSAINet 把卷积分支、分支内 attention 和分支间 attention 分开画，试图让读者接受“职责分开后可以保持紧凑”的解释。[原文：PDF p. 2，Fig. 1]

但框图本身没有控制参数量、训练预算或数据处理。它也没有测出别的模型是否真的存在“职责混杂”。因此，合理重建是“作者选择了这种分工，并用后续实验检验整体效用”；不能写成“作者已经发现并证明其他网络失败的唯一原因”。论文没有提供被放弃方案的实验历史。

### 3. 得到统一架构时，作者放弃了什么

作者选择较通用的 tokenizer 和 attention，没有显式加入电极拓扑、解剖结构或频率先验，并把这点写入 limitations。[原文：PDF p. 12]

这个取舍解释了整个设计：共同骨干降低了针对不同范式改结构的负担，但不会自动拥有每种任务最合适的先验。本文取得的是在十个已评估数据集上的折中表现；它没有证明统一配置对每个数据集都是单独调优后的最优方案。

<a id="reading-section-03"></a>

## 三、沿数据流看清楚：两个尺度共享什么，又在哪里分开

![Figure 2：从输入 EEG 到分类输出](<./refs/paper-cards/dsainet/assets/fig-02-overall-architecture.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-02-overall-architecture.png>)

完整数据流见原文 PDF p. 4，Fig. 2。以下省略 batch 维度，所有 shape 都按单个 trial 表示。

| 位置 | 张量 | 发生的变化 |
|---|---|---|
| 输入 | $X\in\mathbb R^{C\times T}$ | $C$ 个电极、每个电极 $T$ 个采样点 |
| 时空 tokenizer | $F\in\mathbb R^{f_2\times1\times N}$ | 时间滤波、跨电极空间卷积、两级池化 |
| 公共 token | $Z_0\in\mathbb R^{N\times d}$ | 转置、投影、缩放、加入位置编码 |
| 细/粗卷积分支 | $Z_f,Z_c\in\mathbb R^{N\times d}$ | 不同卷积核改变时间感受野，长度相同 |
| 分支内细化 | 两个 $N\times d$ 矩阵 | 各自根据自身 token 建立内容关系 |
| 分支间交互 | $Z'_f,Z'_c\in\mathbb R^{N\times d}$ | 向另一分支查询和接收内容 |
| 池化与分类 | $p_f,p_c\in\mathbb R^d$，拼接为 $2d$ | 两支各自加权汇总，再作线性分类 |

[原文：PDF pp. 3–5，Eqs. 1–19]

三个容易误解的地方值得先说明。

第一，电极轴在分支出现以前就压到 1，但 $f_2$ 个特征通道仍能保存多个学到的空间投影。因此“共同空间编码”不等于“只剩一个空间特征”。真正成立的是：两分支拿到同一组已编码的时空特征，没有各自从原始电极重新学习独立 tokenizer。[原文：Eqs. 2–6；阅读判断]

第二，fine/coarse 并不代表两支使用不同采样率或不同 token 数。两支都是 $N\times d$；区别主要在 token 轴卷积核。正文用 temporal resolutions 描述这种差异时，应结合公式理解为不同感受野，而不是两条真正不同分辨率的数据流。

第三，kernel 3、7、11、15 都作用于池化后的 token。它们不是原始 EEG 的 3、7、11、15 个采样点，更不能直接分别对应某个脑电频段。

<a id="reading-section-04"></a>

## 四、把关键公式算一遍

以下例子都用于解释算子，不代表训练后的真实权重。论文固定 $d=40$、4 个 attention heads；例子将维度缩小以便手算。归一化例子取仿射参数为 1 和 0，并忽略极小的数值稳定项；实际计算包含这些参数和稳定项。

### 1. Tokenizer：先把电极和时间压成可比较的 token

Eqs. 2–5 的任务是让后续两分支在相同表示空间里工作：

$$
F=\Phi_{tok}(X),\quad \widetilde Z=\operatorname{Transpose}(\operatorname{Squeeze}(F)),\quad Z^{(0)}=P(\widetilde Z),\quad Z_0=\sqrt d\,Z^{(0)}+E.
$$

$\Phi_{tok}$ 是包含卷积和池化的编码器；$\widetilde Z$ 的形状为 $N\times f_2$；$P$ 将特征宽度变为 $d$，当 $f_2=d$ 时为恒等映射；$E\in\mathbb R^{N\times d}$ 表示可学习的位置项。最后一式把原文的 $PE(\sqrt d Z^{(0)})$ 展开为加性位置编码写法。[原文：PDF p. 3，Eqs. 2–5]

**教学例子。** 某个时间滤波器在两电极上的同一时刻输出为 $(2,6)$，一个空间投影用权重 $(0.25,0.75)$，得到 $0.25\times2+0.75\times6=5$；另一空间投影完全可以使用别的权重，保留别的空间组合。这说明电极轴压缩之后仍可有多个特征通道。

设最终得到两个二维 token $\widetilde Z=[(1,0);(0,1)]$，取 $P=I$、$d=2$，位置项为 $E=[(0.1,0);(0,0.2)]$，则

$$
Z_0=[(1.5142,0);(0,1.6142)].
$$

这个例子没有用位置项取代时间特征，而是在同一 token 内容上加了位置线索。Table V 的位置编码消融支持该线索在所测设置中的效用，不能由此推出卷积本身不编码顺序。

### 2. 双尺度：感受野不同不等于功能已经分离

先把 $Z_0$ 转成 $H_0=Z_0^\top\in\mathbb R^{d\times N}$，便于沿 token 轴卷积。每层计算一个修正项，再残差相加：

$$
\widetilde H_b^{(\ell)}=\operatorname{BN}\!\left(PW_{b,2}^{(\ell)}\!\left(\operatorname{GELU}\!\left(PW_{b,1}^{(\ell)}\!\left(\operatorname{GELU}(DW_{k_b^{(\ell)}}(H_b^{(\ell-1)}))\right)\right)\right)\right),
$$

$$
H_b^{(\ell)}=H_b^{(\ell-1)}+\alpha_b^{(\ell)}\widetilde H_b^{(\ell)}.
$$

$b\in\{f,c\}$ 标识分支，$\ell$ 是层号；$DW$ 对每个特征通道独立作时间卷积；$PW_1$ 将通道扩张、$PW_2$ 投回 $d$；中间使用分组逐点变换。$\alpha$ 是可学习标量，控制新增修正的强度。[原文：PDF pp. 3–4，Eqs. 6–9]

**卷积块教学例子。** 取单特征通道的局部三个数 $(1,2,3)$ 和均值核 $(1/3,1/3,1/3)$，卷积输出为 2。为展示完整次序，设这个小例子的两个逐点线性映射都是恒等映射、BN 处于均值 0 方差 1 的恒等状态，则两次 GELU 的结果依次约为 $1.9545$ 和 $1.9050$。取 $\alpha=0.1$，中心位置原值为 2，残差输出约为 $2+0.1\times1.9050=2.1905$。例子简化了通道扩张，实际模型的扩张比为 4，不能把实际块理解成普通均值滤波。[原文：PDF p. 7；教学假设]

为了隔离尺度的作用，再看一个简化的线性局部平均例子：序列 $(0,0,0,9,0,0,0)$ 的中心，3 点均值为 3，7 点均值为 $9/7\approx1.2857$。短核保留更尖的局部响应，长核把同一峰放进更宽背景。这解释了不同核提供不同归纳偏置；真实学习到的核并不必须是平均核，也可能对同一种模式产生很接近的响应。

按单位 stride、无 dilation 的卷积假设，两层核 3 和 7 对 token 的理论感受野是 $1+(3-1)+(7-1)=9$；核 11 和 15 则是 25。它们仍只是 tokenizer 之后的名义范围。若两级池化总步幅按 $4\times8=32$ 估算，250 Hz 下相邻 token 间隔约 128 ms，9 个 token 的中心跨度约 $8\times128=1024$ ms；500 Hz 下约为 512 ms。完整感受野还须加入 tokenizer 自身范围和边界处理。因此固定 kernel 超参数不等于固定生理时间尺度。[原文：PDF p. 7；上述感受野为条件性推导，非作者测量]

原文 Eq. 10 还允许回注共同输入：$Z_f\leftarrow Z_f+\alpha_1Z_0$，粗支同理。若某 token 为 $(1,2)$、共同输入为 $(2,0)$、$\alpha_1=0.25$，结果是 $(1.5,2)$。回注可保留公共信息，同时也可能让两支更相似。没有 $\alpha$ 的数值、分支内容或干预证据时，不能从不同核直接宣称“已形成互补”。

### 3. Self-attention：每个 token 的输出依赖同支其他 token 的内容

Eqs. 11–12 对每支先执行带残差的 attention 和 LayerNorm，再执行 FFN、残差和 LayerNorm：

$$
\overline Z=\operatorname{LN}(Z+\operatorname{MHA}(Z,Z,Z)),\qquad Z^{new}=\operatorname{LN}(\overline Z+\operatorname{FFN}(\overline Z)).
$$

为展开原文封装的 MHA，用标准单头 attention 说明其内部计算：

$$
Q=ZW_Q,\quad K=ZW_K,\quad V=ZW_V,\qquad A=\operatorname{softmax}_{row}(QK^\top/\sqrt{d_h}),\quad O=AV.
$$

$Q,K\in\mathbb R^{N\times d_h}$ 是 query/key，$V\in\mathbb R^{N\times d_v}$ 是 value，$A\in\mathbb R^{N\times N}$ 是每个接收位置对各发送位置的权重。多头分别计算后拼接、输出投影回 $d$。这段是标准算子的教学展开，不是论文额外报告的新公式。

**教学例子。** 取 $Z=[(1,0);(0,1)]$，使用一头且 $d_h=1$，令 $W_Q=(1,0)^\top$、$W_K=(\ln3,0)^\top$、$W_V=I$。于是第一行 query 的 scores 为 $(\ln3,0)$，softmax 为 $(3/4,1/4)$，接收内容为 $(0.75,0.25)$；第二行 query 为 0，权重是 $(1/2,1/2)$，接收内容为 $(0.5,0.5)$。

若输出投影取恒等映射，残差结果为 $[(1.75,0.25);(0.5,1.5)]$。逐 token 做 LayerNorm，第一行均值 1、标准差 0.75，成为 $(1,-1)$；第二行均值 1、标准差 0.5，成为 $(-1,1)$。为算完这个小例子，令 FFN 输出为零，则第二次 LN 后仍为这两个向量。

这也提醒我们：attention 做的是内容搬运与混合，不只是给“重要 token”乘一个系数。原文将它安排为 refinement，是设计用途；self-attention 本身仍能建立长程关系，卷积与 attention 的职责并没有被数学上强制隔离。

### 4. Cross-attention：谁提问，谁的分支就被更新

Fine 接收 coarse 的方向写为：

$$
\overline Z_f=\operatorname{LN}\left(Z_f+\beta_1\operatorname{MHA}(Z_f,Z_c,Z_c)\right),\quad
Z'_f=\operatorname{LN}(\overline Z_f+\operatorname{FFN}(\overline Z_f)).
$$

粗支方向则交换 $f,c$ 并使用 $\beta_2$。$Z_f,Z_c$ 都是 $N\times d$；$\beta_1,\beta_2$ 是标量。Q 来自接收方，K/V 来自提供内容的一方。原文两式使用 refined 的原分支，而非先更新 fine 再把 $Z'_f$ 送进 coarse。[原文：PDF pp. 4–5，Eqs. 13–16]

**教学例子。** 针对一个 fine token，设其 query 为 1，coarse 的两个 key 为 $(\ln3,0)$，value 为 $[(2,0);(0,2)]$，单头宽度为 1，输出投影取恒等。它从 coarse 接收 $0.75(2,0)+0.25(0,2)=(1.5,0.5)$。若 fine 原 token 为 $(0,1)$、$\beta_1=0.5$，残差得到 $(0.75,1.25)$，LN 后为 $(-1,1)$；令 FFN 输出为零，第二次 LN 后不变。

反过来，同样人为取 coarse query 对 fine keys 产生权重 $(0.25,0.75)$，fine values 为 $[(1,0);(0,1)]$，则接收 $(0.25,0.75)$。若 coarse 原 token 为 $(2,0)$、$\beta_2=1$，残差为 $(2.25,0.75)$，LN 后为 $(1,-1)$，零 FFN 后不变。两个方向结构对称，却并不意味着消息、强度或功能相同。

另外，$\beta_1=0$ 仅使跨分支消息项归零。LN、FFN 仍在，所以一般不能把“交互强度为零”直接等同于“整个交互模块被删除”。这对理解消融尤其重要。

### 5. 聚合与分类：共享打分器不要求共享权重分布

模型需要把 $N$ 个 token 变成固定长度向量。Eqs. 17–19 用同一个可学习 $q\in\mathbb R^d$ 给两分支分别打分：

$$
w_{b,n}=\frac{\exp(q^\top z_{b,n})}{\sum_{j=1}^N\exp(q^\top z_{b,j})},\qquad p_b=\sum_{n=1}^Nw_{b,n}z_{b,n},\qquad \widehat y=W_{cls}[p_f\Vert p_c]+b_{cls}.
$$

$z_{b,n}\in\mathbb R^d$ 是交互后的 token，$w_{b,n}$ 是标量且同一分支之和为 1；$p_b\in\mathbb R^d$；若有 $K$ 类，$W_{cls}\in\mathbb R^{K\times2d}$、$b_{cls}\in\mathbb R^K$，输出是 logits。[原文：PDF p. 5]

**教学例子。** 取 $q=(\ln3,0)$，fine tokens 为 $[(1,0);(0,2)]$，权重为 $(0.75,0.25)$，所以 $p_f=(0.75,0.5)$。coarse tokens 为 $[(0,1);(1,1)]$，同一 $q$ 给出的权重变成 $(0.25,0.75)$，所以 $p_c=(0.75,1)$。

拼接得到 $(0.75,0.5,0.75,1)$。取二分类矩阵的两行为 $(1,0,1,0)$ 和 $(0,1,0,1)$，偏置为 $(0.2,0)$，logits 就是 $(1.7,1.5)$，softmax 第一类概率约为 0.5498，最终预测第一类。共享评分向量约束的是“如何给内容打分”，不是把两支的权重图强行设成一样。

当 $q=0$ 时，所有 scores 都为 0、$w_n=1/N$，该机制精确退化为均值池化。对刚才 fine 分支，均值为 $(0.5,1)$，与学习打分得到的 $(0.75,0.5)$ 不同。这解释了为什么一个很小的读出模块也能改变分类结果。

另一个直接好处是分类头宽度不随 $N$ 增长。以教学配置 $N=30,d=40,K=4$ 计算，双支 flatten 的线性头有 $2\times30\times40\times4+4=9604$ 个参数；池化后的头为 $2\times40\times4+4=324$，另加共享 $q$ 的 40 个参数。这里只比较读出部分，不是重新估算整网参数。

### 6. 指标：weighted F1 不能替换成 ACC，也不是 macro F1

Eqs. 20–21 中作者重新用 $N$ 表示测试样本数、$C$ 表示类别数，与方法段的 token 数、电极数同名。为避免混淆，这里记测试样本数为 $M$、类别数为 $K$：

$$
ACC=\frac{\text{正确预测数}}{M},\qquad F1_{weighted}=\sum_{k=1}^K\frac{M_k}{M}\frac{2P_kR_k}{P_k+R_k}.
$$

**教学例子。** 10 个样本里 A 类 8 个、B 类 2 个，全部预测成 A。ACC 为 0.8；A 的 precision 为 0.8、recall 为 1、F1 为 $8/9$，B 的 F1 按零预测的常用处理取 0，所以 weighted F1 为 $0.8\times8/9=0.7111$，macro F1 则为 $4/9=0.4444$。这个例子也说明 weighted F1 仍受类别占比影响，不能仅凭它判断少数类表现。零分母处理属于例子的明确约定，论文未在公式旁展开该实现细节。

<a id="reading-section-05"></a>

## 五、哪些设计真的贡献了结果

Table V 给出完整模型 ACC：BCIC-IV-2a 为 61.79%，2b 为 76.41%，ADFTD 为 59.65%。下表的数字是按原表重新相减得到的下降量，单位均为百分点，不是相对百分比。[原文：PDF p. 8]

| 改动 | 2a 下降 | 2b 下降 | ADFTD 下降 | 能作出的判断 |
|---|---:|---:|---:|---|
| 去位置编码 | 2.03 | 0.70 | 2.59 | 报告均值支持其贡献 |
| 仅 fine 分支 | 1.97 | 0.47 | 1.08 | 完整双支优于此单支变体 |
| 仅 coarse 分支 | 1.60 | 0.67 | 1.81 | 完整双支优于此单支变体 |
| w/o Attentive Interaction | 2.43 | 0.51 | 2.03 | 该变体较差；与下一类删减的细节差异未充分交代 |
| 去 intra-branch attention | 1.72 | 0.92 | 0.68 | 分支内细化有报告均值贡献 |
| 去 inter-branch attention | 1.65 | 0.85 | 2.00 | 分支间交互有报告均值贡献 |
| adaptive aggregation 换均值池化 | 1.97 | 0.83 | 2.73 | 读出选择同样影响结果，ADFTD 上下降最大 |

这些删减都没有让结果崩溃，所以按 X-Ray 的严格口径，最合适的判断是 **contributing**，且限于所报告均值；论文没有统计检验来确认每项下降的稳定性。不能把每个模块都称作不可或缺的 load-bearing 核心。

**Tokenizer 的必要性未被单独隔离。** 作者在消融总结里把它也列为整体贡献的一部分，但表里没有替换或删除 tokenizer 的对照。位置编码消融只覆盖其中一个设计。

**双尺度的独特贡献尚未完全隔离。** 单支删减同时影响容量和计算。论文没有用同等预算的双同尺度分支、加宽单支、相同卷积核双支来排除“多一路容量或参数化带来的收益”。因此它支持双支组合有效，但不足以确认收益只来自尺度互补。

**两条 interaction 消融的界线不清。** p. 9 把 w/o Attentive Interaction 描述为仅在末端融合，同时又单列 w/o Inter-Branch Attn.，两者结果不同。仅靠文字和 Table V 无法确认两者究竟分别保留了哪些残差、FFN、intra-attention 或融合操作。这里应保留为待查作者实现的问题，不能自行解释为“双 attention 全删”和“仅 cross-attention 删”。

**双向交互、共享评分向量及回注标量的独立必要性均未建立。** 没有单向交互、共享/非共享 $q$、去共享回注等对应对照。结构显眼不等于它已经被实验单独证明。

<a id="reading-section-06"></a>

## 六、主结果究竟有多强：把赢的幅度和实验条件放在一起

| 数据集 | DSAINet ACC | 表内第二名 ACC | 差值（百分点） |
|---|---:|---:|---:|
| BCIC-IV-2a | 61.79 | CTNet 60.08 | 1.71 |
| BCIC-IV-2b | 76.41 | DBConformer 76.37 | 0.04 |
| Zhou2016 | 78.21 | DBConformer 76.69 | 1.52 |
| OpenBMI | 82.89 | Deformer 81.99 | 0.90 |
| PhysioNet-MI | 63.90 | Deformer 63.38 | 0.52 |
| Mumtaz2017 | 89.33 | Conformer 87.79 | 1.54 |
| ADFTD | 59.65 | Deformer 57.74 | 1.91 |
| Rockhill2021 | 75.85 | CTNet 74.19 | 1.66 |
| EEGMat | 72.83 | Deformer 72.53 | 0.30 |
| Shin2018 | 84.81 | Deformer 82.35 | 2.46 |

[原文：PDF p. 8，Tables III–IV；差值为本次算术整理]

跨十项数据集全部取得最高 ACC 均值，是整体架构可复用的实际证据。但 BCIC-IV-2b 的领先只有 0.04 个百分点，weighted F1 与 DBConformer 同为 75.91%。不能把“表内第一”替换为“每个任务都有明显优势”。

还应区分“论文共列了 13 种基线”和“每个数据集都比较 13 种”。Table III 的 MI 比较没有 Conformer、MGFormer；Table IV 没有 MSVTNet、DBConformer，两表各列 11 种基线。两表联合覆盖 13 种，不能读成完整的 13×10 比较矩阵。

### 1. LOSO 的验证集描述存在直接冲突

p. 6 开头说训练、验证、测试三者被试互斥。但同页紧接着写，BCIC-IV-2a、2b、Zhou2016 的 LOSO 每次留一名被试测试，并从**每个剩余训练被试**中抽 20% 样本验证、80% 训练。

依照这条具体步骤，测试被试与训练/验证被试分离，但训练和验证共享被试。例如 2a 留第 9 人测试，第 1–8 人各拿 80% trial 训练、20% 验证，两组都包含第 1–8 人。因此不能同时满足前面的三者互斥概括。

这会**限制“严格被试互斥验证”的范围**，但并不直接证明测试被试泄漏。后者需要实际 split 或代码证据。X-Ray 以具体操作说明为阅读依据，同时保留文字冲突。已有 Reader 的 S009 将三者互斥直接作为结论，应以这里的限定解释为准。

其余数据集按 subject-level k-fold：一折测试，剩余折随机选一折验证，其余训练；Rockhill2021 用 5 折，其余用 10 折。这种文字描述支持三者被试互斥。[原文：PDF pp. 6–7]

### 2. 架构固定与选择过程不是同一件事

正文给出 $d=40$、4 heads、两层 temporal block、一层 attentive depth、dropout 0.25 等固定架构配置。Table II 同时显示 batch size 为 32 或 128、learning rate 为 $10^{-3}$ 或 $10^{-4}$、epochs 为 30 或 100；Table I 的采样率从 200 到 500 Hz 不等。Shin2018 虽属非 MI，也使用 100 epochs，因此不能笼统说非 MI 全部训练 30 epochs。[原文：PDF pp. 6–7]

Fig. 3 和 Fig. 4 展示深度及分段长度对性能的影响，正文据此选择主实验工作点；但没有充分交代这些选择是否在独立验证层完成，或汇总测试表现是否参与最终选择。这里是**选择流程报告不足**，不能直接判定已发生 test-set tuning，也不能替作者假定进行了完整 nested validation。

### 3. 小标准差还没有回答“所有被试是否稳定”

p. 7 写五个 seeds，并对 folds 或 LOSO runs 汇总 mean±std；没有给出足以重建全部聚合顺序的公式或每个单位结果。正文随后把小 std 解释为稳定的跨折/跨被试泛化。仅凭汇总数无法区分：是全部 unit 的离散度，还是先平均 folds 后的 seed 波动。不能因为数值看起来小，就替原文确定为后一种。

例如两个 seeds 的被试准确率都为 $(40,80)$，每个 seed 的平均值都为 60，seed 均值的 std 为 0；但被试间差异依然有 40 个百分点。这个教学例子说明为什么必须知道聚合层级。论文也未给成对置信区间或统计检验，表内 std 不能替代配对比较。

### 4. 预处理与基线公平性仍有未报告项

论文说明了滤波、重采样、分段和 channel-wise z-score，但没有充分规定 z-score 的统计量究竟按 trial、被试还是训练集合拟合，也没有逐项给所有基线的搜索预算、选 checkpoint 规则和代码版本。因而可以报告其统一实验框架，不能进一步断言所有基线都获得了同等充分的调优。

Rockhill2021 与 EEGMat 使用 50% 重叠分段。只要按被试分组，重叠本身不必跨入测试折；不能看到 overlap 就判定泄漏。但它会增加同一被试样本的相关性，所以数千个片段也不能替代数千个独立个体的证据。

<a id="reading-section-07"></a>

## 七、逐张图读：作者希望你相信什么，图又保留了什么反证

### Figure 3：浅层足够，但不是越浅越好

![Figure 3：时间卷积深度与 attention 深度](<./refs/paper-cards/dsainet/assets/fig-03-hyperparameter-sensitivity.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-03-hyperparameter-sensitivity.png>)

作者希望用两层卷积、一层 attention 的总体表现支持紧凑设计。图中继续加深通常收益有限，但各数据集曲线并非同一形状；“整体最合适”不等于每个指标都在同一深度取严格最大值。该图只改变了两个深度参数，也不能代表卷积核、嵌入宽度及所有超参数的完整搜索。[原文：PDF pp. 9–10，Fig. 3]

它支持“当前实验里深 attention 没有成为必要条件”，却没有单独证明原因必然是“职责划分得足够清楚”；正则化、数据量、优化难度都是没有被排除的解释。

### Figure 4：片段长度改变的不止时间上下文

作者强调中等窗口是稳健工作点，但 Mumtaz2017 随长度增长，ADFTD、Rockhill2021 则在 4 s 左右达峰。这已经表明没有一个对所有任务一致的长度响应。[原文：PDF p. 10，Fig. 4]

更关键的是，更换长度同时改变每段上下文、生成的片段数及训练样本相关性。它是分段设置敏感性实验，而不是保持样本预算等所有变量不变的纯时间尺度实验。

### Figure 5：静态计算量优势明确，性能标签有不一致

原文报告 DSAINet 为 76.99K 参数、73.67 MMACs，Deformer 为 2.60M、586.92 MMACs；按这些数值，MACs 比值约 7.97、参数比值约 33.77。这里的“约八倍”指静态乘加计数比，不是实测速度。[原文：PDF p. 10]

数值核查发现：p. 10 效率段把 DSAINet 的 63.87 和 Deformer 的 63.37 都称为 ACC；但 Table III 中这两个值属于 weighted F1，ACC 分别是 63.90 和 63.38。Figure 5 的纵轴也标 ACC，不能靠图上近似坐标解决这个 0.01–0.03 的差别。应分别报告：**主表 ACC 提升为 0.52 个百分点；效率段所引 0.50 个百分点对应主表 F1 差值。**这是原文内部指标标签不一致，不应把它默默修平。

此外横轴是对数坐标，视觉距离不是线性计算量差；图中也存在 MACs 或参数更少的模型。图支持的是性能与复杂度之间的有利折中，不能推出模型在所有资源指标上绝对最小。原文 p. 12 也明确承认没有部署导向评估。

### Figure 6：空间相容性不能补上因果链

原文呈现八个数据集的九张平均 saliency 图，ADFTD 分开画 AD 与 FTD。疾病相关图只纳入相应患者组。因此图能够支持“平均归因随数据集变化，且可与某些任务相关区域对应”，并不直接展示患者与健康者之间的归因差异或个体一致性。[原文：PDF pp. 10–11，Fig. 6]

作者将其解释为 physiologically meaningful 的表征；本次阅读保留为作者解释。没有遮挡、随机化 sanity check 或独立机制实验，无法排除不同归因方法、预处理、伪迹和样本平均方式的影响。

### Figure 7：看到了不同 attention 图，不等于证明了互补内容

![Figure 7：三个数据集的分支内与跨分支 attention](<./refs/paper-cards/dsainet/assets/fig-07-attention-patterns.png>)

[打开原图，放大查看](<./refs/paper-cards/dsainet/assets/fig-07-attention-patterns.png>)

这里的轴是 token，不是电极或脑区。BCIC-IV-2a 有集中的列状响应，Shin2018 有对角或带状结构；作者据此解释两类 attention 的分工。[原文：PDF pp. 11–12]

但各子图的色标范围并不统一，颜色深浅不能跨图直接比较交互强度。实际消息还依赖 $V$、输出投影与 $\beta$；attention 权重分散不等于影响更大，集中也不等于更重要。论文没有在图旁给出这些量以及对预测的因果效应，所以此图支持“内容依赖的关系模式有所不同”，对“跨尺度互补已被验证”的支持仍有限。

<a id="reading-section-08"></a>

## 八、读完应该带走的设计认识

DSAINet 最值得吸收的是一条完整的计算安排：共同编码保证两支处于可交互空间，不同核提供不同时间偏置，self-attention 在各自表示里混合内容，cross-attention 让另一尺度参与更新，最后用固定大小的读出向量控制分类头成本。把这些步骤接起来，比逐一记住五个模块名字更接近论文的实际方法。

实验证据说明这种组合在给定数据与协议下有竞争力，也说明删掉若干模块会降低所报告的均值。但“不同核”到“学到不同功能”，再到“不同功能通过交互产生收益”，仍是三件需要分别证明的事。本文走通了整体分类效果，没有完全走通这条机制链。

下一次引用本文时，最稳妥的表述是：DSAINet 用共享主体结构在多个 EEG 数据集上分别训练评估，通过轻量双尺度卷积、分支内及跨分支注意力和自适应聚合，取得表内领先均值与较低的离线复杂度。涉及 LOSO 的训练/验证被试关系、效率段 ACC/F1、统计聚合层级时，应带上本次回读发现的限制。

尚未回答的关键问题是：双支增益有多少来自尺度、有多少来自容量？两个交互方向是否都必要？参数共享和残差强度实际起多大作用？相同核配置在不同采样率及输入条件下是否形成相近的有效时间尺度？这些是理解论文尚缺的证据，并非本文已经得出的负面结论，也不构成新的实验授权。

<a id="reading-section-09"></a>

## 来源与既有材料

- 主来源：[论文 PDF](<Ma 等 - 2026 - DSAINet An Efficient Dual-Scale Attentive Interaction Network for General EEG Decoding.pdf>)。文中页码均为这份 PDF 的 1–13 页。
- 既有阅读底稿：[DSAINet-paper.md](DSAINet-paper.md)。其 S009 的三者被试互斥概括、Figure 5 段落的 ACC 数字应按本次原文对照理解。
- 既有卡片：[DSAINet-paper-card.md](DSAINet-paper-card.md)。本次 X-Ray 独立保存，未修改既有 Reader、Paper Card 或 PDF。
- 原图复用当前目录 `assets/`，仅作原论文证据定位；图片自身的历史裁切不替代本次查看的完整 PDF 页面。

[返回章节导航](#reading-top)
