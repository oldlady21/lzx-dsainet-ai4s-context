---
prompt_id: DSAINET_MI_EEG_PROJECT
version: '3.3'
level: 3
parent: {prompt_id: MIEEG_AI4S_EXECUTION, version: '3.3'}
status: ACTIVE
---
# DSAINet 项目适配 v3.3

## 阅读与研究认识入口

研究认识与唯一来源索引见 [研究总览](research/CURRENT_UNDERSTANDING.md)。该总览指向基模阅读材料与本地实现依据；本 L3 不重复列举论文路径。

首次采用基模理解时，重点核对局部编码后 token、Fine／Coarse 时间感受野、intra／inter 与读出的位置；架构跨任务复用不等于权重迁移，候选 E／A 统计也不自动对应生理频带或已证实互补。 已有同版本核对可复用，缺口只限制依赖它的判断。

新判定映射要区分规范 DSAINet 宿主、具体 P0 定义、匹配训练配方和候选新增价值；不同窗口／数据／profile 的旧门不可直接移植，原 P0 关闭边界仍保留。 实际判定路径的对应、接线缺口与最小验证按 [L2 第2节](../../prompts/LEVEL2_EXECUTION_v3.3.md#2-用现有-brief-完成一页决策)执行，共享细则不在本 L3 重复。

本文件仅在唯一索引为本 Program 选定兼容 v3.3 链后生效。是否使用由 `ai4s/PROMPT_INDEX.yaml` 决定；已有 campaign、Run、operation 及冻结续接按其原绑定处理。本文件不保存运行状态、候选排名、动态阈值或最新效果。

## 1. 入口与来源

| 用途 | 精确入口 |
|---|---|
| 执行器、规范 baseline 配置 | `ai4s/programs/dsainet/PROGRAM.yaml` |
| 活动身份与运行状态 | `ai4s/programs/dsainet/research/STATE.yaml` |
| 证据与精确关闭边界 | `ai4s/programs/dsainet/research/EVIDENCE_INDEX.yaml` |
| 统一科学入口／模型构造 | `scripts/run_dsainet_bnci2014001.py` |
| Program 候选实现 | `src/models/ai4s/dsainet/`，由冻结 `model.class_path` 定位具体类 |
| 历史研究问题定位 | `docs/notes/DSAINET_BASELINE_EVIDENCE_MAP_2026-08-26.md`、`docs/notes/SAFSS_CYCLE_HANDOFF_2026-08-26.md` |

先按证据用途和 exposure 选择材料，以上路径是定位入口，不是全部必读清单或有效性证明。重要判断回到精确合同、实现与合格 intake；历史记录的设计状态不替代 State。SAFSS、FCPSM、RACR 等关闭路线按精确来源保留，不因更新提示词重开。

## 2. 宿主语义与必要核对

候选通过 `DSAINetAI4S` 和受限 `src.models.ai4s.dsainet.<module>:<Class>` 进入统一 runner。采用完整结构或训练适配时，先说明与规范 baseline／当前宿主的关系及研究权限，复用现有入口；不要为每个候选另建训练主体。

只沿本次干预涉及的路径核对以下问题，在 brief 引用所用源码身份；无关项不变成每轮门：

- **token 与分支：**输入经过哪些变换、轴和池化后进入 fine／coarse、intra／inter 及读出？保留 token 名称或形状不证明保留原生功能，不同分支不证明互补。
- **作用与控制：**新机制实际进入 forward、loss、gradient 或登记路径的哪个位置？主比较检验整体收益还是增量归因？需要哪些简单控制排除容量、参数共享、读出或训练配套解释？
- **随机性与训练：**同 seed 不保证改结构后共享参数同初始化；涉及初始化归因时核对实际参数／RNG 路径。dropout、参数归属、optimizer／scheduler 与 checkpoint 选择以冻结实现和配置为准，不从论文示意图或历史简称推断。
- **数据：**001 与 004 分别核对 trial／cue 时间锚点、通道、标签、划分及选模数据角色。001 的事实、B0、门或资源画像不自动用于 004；跨数据集支持按各自证据判断。

上述是设计关注点，不宣称所有历史候选具备同一结构。scale separation、branch stability、support/context、interaction 等历史观察仅在原证据范围内解释，相关性、可读性与可训练收益分开。

## 3. 一页决策与结果解释

按 L2 在既有 brief 对齐拟议 Primary Claim 或成文关键缺口。优先建立 DSAINet 主方法候选或补齐其关键证据；已有均值收益、分支可读性或历史支持不足以转入辅助模块搜索。辅助创新须说明解决主线哪个具体局限。可以选择结构、学习目标、完整适配、简化、重分析或停止，不要求先证明宿主缺陷。

每个使用的 arm 单独定义模块／开关、作用路径和配对关系。B0/S0/N0/P0/C0 只是接口 ID，未用项 `enabled=false`；不继承其他 Program 的科学语义，旧 C2/P2 不可仅改名接入。

普通 accuracy screen 区分比例与百分点，明确 `metric_unit=accuracy_pp`；旧比例 harm floor `-0.10` 对应 `-10 pp`，具体门以原合同为准。新门的用途、单位、对象及阈值写入唯一冻结配置，不把历史常量当作新设计的默认科研标准。

有收益但机制控制未支持、对象间风险不同、复核未支持时分别保留事实。因子设计、统计单位和分析规则与冻结任务一致，通用分类器不适用就修分析路径或标明缺口。筛查支持不升级为母项目 Claim；正式评价按共享 `EVALUATION_EVIDENCE.md`。

按 L2 第6节在一个稳定研究总览维护拟议主张、关键缺口与当前认识，原分析保留直接证据。认识标明 001／004、宿主、适配包、读出／联合训练范围及数据角色；保留反例和仍未区分的解释。下一份 brief 说明这些认识实际改变了什么设计或对照，避免重新从全部实验流水归纳。精确负边界限制被检验实例，不自动否定整个机制；新实例须说明实质差异、合法依据和授权，不能换名重开。

## 4. 执行边界

字段接口按 runtime“字段接口与产物闭环”核验；遥测补写后的顶层与嵌套 technical 镜像须一致，实际样例覆盖补写到汇总，不能只测训练函数。P0 的显存字段冲突保留原失败，不放宽检查器，也不因字段失败默认重训。

新 Transaction 合同默认启用 `analysis_v1` 精简回传；冻结前按共享 runtime“新合同冻结前检查”运行 `validate-new`，明确实际分析依赖、包上限和核验超时，缺字段即停止准备并补齐。已有冻结 Run／Bundle 继续原规则，不补写字段或自动迁移。

执行、验收及工程恢复遵循 L2 和 `ai4s/prompts/TRANSACTION_RUNTIME.md`。按受影响真实路径验证，沿原合同逐任务判定复用，不因后置校验失败整套重训。真实技术门要求的完整进程观测缺失时保留缺口；遥测未知、容量等待与训练失败分别报告。

普通工程修复、累计成本、有效进展和资格通过后的授权衔接统一按 [L2 工程恢复](../../prompts/LEVEL2_EXECUTION_v3.3.md#5-工程恢复先保留成果再关闭实际缺口)。token／接口／汇总器修复须恢复原声明的候选行为；改变 Fine／Coarse 定义、融合或训练配方属于科学设计变化。原矩阵、曝光与累计成本保留，技术资格不变成支架效用证据。

资源数值从适用执行器、冻结合同和包内摘要读取，本 L3 不复制显存、并发或余量。既有共卡策略不因适配本版改变。旧 Run 继续原链和原恢复规则；本版适配不启动研究，不更新 State、Evidence Index 或 Prompt Index。



