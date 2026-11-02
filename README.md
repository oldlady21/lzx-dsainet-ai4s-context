# MI-EEG Paper 1

本仓库服务于第一篇以公开运动想象脑电（MI-EEG）解码为对象、以深度学习网络结构或模块创新为核心的高水平论文，覆盖文献整理、模型复现、研究设计、实验分析和论文写作。

**当前已具备多基模复现、统一评估归档与多轮机制诊断基础，正在收敛最终方法和论文主张。** 研究与证据摘要已于 2026-09-23 更新到 [PAPER.md](PAPER.md)；本页提供项目概览和工作入口，实时运行状态从各 Program 读取。

## 从哪里开始

| 需要了解或开展的工作 | 入口 |
| --- | --- |
| 论文问题、已有证据、局限与写作准备度 | [PAPER.md](PAPER.md) |
| 当前优先任务 | [TASKS.md 的当前工作台](TASKS.md#当前工作台) |
| 方向、协议与重要取舍的由来 | [DECISIONS.md](DECISIONS.md) |
| 进入或继续一个 AI4S 研究 | [AI4S 工作入口](ai4s/README.md) → [唯一 Prompt Index](ai4s/PROMPT_INDEX.yaml) |
| 公开数据上的模型比较 | [统一评估协议](experiments/UNIFIED_EVALUATION_PROTOCOL.md) → [结果归档](results/archives/mieeg-uep-v1.0/README.md) |
| 本地实验、远端执行与归档 | [本地工作流](experiments/LOCAL_WORKFLOW.md)、[远端工作流](experiments/REMOTE_WORKFLOW.md)、[仓库维护](docs/REPOSITORY_MAINTENANCE.md) |
| 查找或恢复已迁移的历史资产 | [外盘归档资产指南](docs/ASSET_ARCHIVE.md)：批次结果、最新状态、清单与恢复步骤 |
| 下一批清理规划与 GitHub 更新准备 | [第三轮方案](docs/DISK_HYGIENE_BATCH3_PLAN_20261016.md)、[Git 整理与上传检查](docs/GIT_MAINTENANCE_20261016.md) |
| 文献、代码与草稿 | [文献入口](refs/README.md)、[脚本入口](scripts/README.md)、[写作目录](draft/README.md) |

## 当前研究阶段

论文的工作问题是：**在多分支、多尺度 MI-EEG 模型中，结构差异何时形成可利用的增量信息，以及这种信息如何转化为稳定的解码收益？** 这一表述用于收敛论文叙事，尚未冻结为所有 Program 的共同实验假设。

DBConformer 保留早期主 baseline 定位，DSAINet 是核心匹配对照；MVCNet、SST-DPN 已有各自的研究积累。最终 proposed model、贡献列表和正式评估范围仍待证据收敛，Program 的建立或活跃程度不直接决定论文主模型。

目前的论文准备重点是明确主表的数据语义、从已有证据中选择主候选、核验最终入表资产，并同步撰写背景与协议。具体优先级和判断依据见 [PAPER.md 第八部分](PAPER.md#8-成文所需的下一步)。

## 已有基模与实验资产

截至本次文档核对，BNCI2014001 与 BNCI2014004 均已有多模型实验。[中央结果登记](results/archives/mieeg-uep-v1.0/result_registry.csv) 包含 **34 条模型×数据集×协议记录**，[完整性摘要](results/archives/mieeg-uep-v1.0/integrity_summary.json) 登记 34/34 完整和 2880 条 split fingerprint；这是既有归档范围，不代表全部 checkpoint 当前可恢复。

| 模型 | 已有公共数据覆盖 | 比较与研究定位 |
| --- | --- | --- |
| DBConformer / DSAINet | 两数据集 CO / CV / LOSO，各六项中央登记 | 同一数据、拆分、公共 seeds 与训练 profile 下的 exact-paired 核心对照；DBConformer 作者原生路径另行保留。 |
| MVCNet | 两数据集六项 UEP 登记 | eval-compatible 管线对照及多视图研究基础；VCN-P1 有历史限定范围支持，不能直接扩成新模块或跨数据集结论。 |
| SST-DPN | 两数据集 CO / CV / LOSO 有完成记录，中央已登记四项 | 保留原生训练 profile 的 eval-compatible 对照；001 CO/CV 是已有结果的登记缺口，先核验再补登记。 |
| SMANet-100 | 两数据集六项 UEP 登记 | 单阶段 100 epochs 的独立重构，与后续 cue-v2 会话协议和两阶段训练分别报告。 |
| STGMFM | 两数据集六项统一迁移登记 | eval-compatible 图与多尺度频率结构对照，不等同原始干电极任务的论文性能复现。 |

SMANet 后续已有旧输入三臂 81 项诊断及独立 cue-v2 会话重构 27 项验收结果；cue-v2 仍有原文实现歧义、性能差距和实验外审未完成边界。新旧 Sinc 幅值比较的进度见其 [独立状态记录](experiments/records/smanet/2026-09-22_sinc_gain_comparison/STATUS.md)，SMANet 未建立 Program。完整分析见 [PAPER.md 第五部分](PAPER.md#5-当前研究与证据地图)。

LI-DSN 保留独立复现差距与结构参考用途。CFSPMNet / PA-TCNet 的 XW-Stroke 适配仍受目标标签选优等边界限制；STGMFM 的 source-only 修正版 XW-Stroke 结果与旧结果分别追溯。它们不混入当前公开 MI 主表，详见 [基模资产说明](PAPER.md#4-基模与可用实验资产) 和 [实验记录入口](experiments/README.md)。

### 使用结果前需要核对

- **输入窗口。** 2026-09-22 的审计确认，旧 SMANet paper_holdout 及已核验的 DSAINet 共享 BNCI2014001 资产采用 trial 相对 [0,4)，对应 cue 相对 [-2,2)。旧输入上的配对事实保留，但不能称为 cue 后四秒的原文复现。其他消费者按输入身份核对；SMANet cue-v2 使用独立修正资产。见 [窗口审计](experiments/records/smanet/2026-09-22_reconstruction_followup/RECONSTRUCTION_PLAN.md)。
- **比较范围。** exact-paired 与 eval-compatible 分别支持匹配设置下的架构比较和完整管线比较；原生路径、论文协议重构、诊断结果分开使用。统计推断以被试为单位，不把多个 seed 的运行当作独立被试。
- **指标与证据。** F1 的 macro/weighted 不能直接混排，补算前须验证具体预测或 checkpoint 可恢复。完整运行、技术检查和局部诊断分别按其证据范围报告；工程失败 INVALID 不等于科学 NO_SIGNAL。

## AI4S Program 与研究入口

新研究按基模绑定 Program，同一 Program 容纳多个 research。活动 L1/L2/L3 版本以 [Prompt Index](ai4s/PROMPT_INDEX.yaml) 为准；进入时读取对应 PROGRAM、State、Evidence Index，并核对 active_run 与 active_operation。新研究默认使用 v3.1 规则：诊断必须对应设计取舍，筛查和诊断结果必须登记后续处置，下一轮必须说明上一轮新增证据如何改变设计。既有 campaign、Run、operation 和冻结续接按 Prompt Index 中的绑定链收尾。

| Program | 配置 | 运行状态 | 证据入口 |
| --- | --- | --- | --- |
| MVCNet | [PROGRAM](ai4s/programs/mvcnet/PROGRAM.yaml) | [State](ai4s/programs/mvcnet/research/STATE.yaml) | [Evidence Index](ai4s/programs/mvcnet/research/EVIDENCE_INDEX.yaml) |
| DSAINet | [PROGRAM](ai4s/programs/dsainet/PROGRAM.yaml) | [State](ai4s/programs/dsainet/research/STATE.yaml) | [Evidence Index](ai4s/programs/dsainet/research/EVIDENCE_INDEX.yaml) |
| DBConformer | [PROGRAM](ai4s/programs/dbconformer/PROGRAM.yaml) | [State](ai4s/programs/dbconformer/research/STATE.yaml) | [Evidence Index](ai4s/programs/dbconformer/research/EVIDENCE_INDEX.yaml) |
| SST-DPN | [PROGRAM](ai4s/programs/sstdpn/PROGRAM.yaml) | [State](ai4s/programs/sstdpn/research/STATE.yaml) | [Evidence Index](ai4s/programs/sstdpn/research/EVIDENCE_INDEX.yaml) |
| OTA | [PROGRAM](ai4s/programs/ota/PROGRAM.yaml) | [State](ai4s/programs/ota/research/STATE.yaml) | [Evidence Index](ai4s/programs/ota/research/EVIDENCE_INDEX.yaml) |

State 管运行，Evidence Index 管证据，按需建立的 Program Claim Ledger 管逐 Claim 判断。正式候选按活动链适用的 [评估规则](ai4s/prompts/EVALUATION_EVIDENCE.md) 准备评估计划与 Claim Ledger；普通探索沿用现有流程。跨 Program 通过论文问题地图共享证据、负边界和设计约束，不合并不可比指标，也不自动继承执行授权。

[Foundry](idea-stage/foundry/) 独立生成候选，用户选择后交接对应 Program；AI4S 也接受直接给定的 idea。交接不自动创建研究或启动实验。proposed 旧流程已退役，历史合同、结果与精确关闭边界继续作为来源，历史路径可通过 [路径映射](ai4s/archive/PATH_MAP.json) 查找。

README、PAPER 和 TASKS 是入口与摘要。执行按活动合同和已有授权推进，结果经回拉、manifest/hash 验证、intake 与冻结分析后登记；逐 Claim 判断再按适用审查要求完成。外审触发与复用规则见 [EXTERNAL_REVIEW.md](ai4s/prompts/EXTERNAL_REVIEW.md)。

## 实验环境与工作方式

本地用于数据与模型检查、调试和适合本机资源的小规模实验；完整多被试、多 seed 或长时间任务按资源情况使用服务器。默认本地环境为 `mieeg`，从仓库根目录工作。

- 本地目录、exp_id、运行和结果归档：[LOCAL_WORKFLOW.md](experiments/LOCAL_WORKFLOW.md)、[操作手册](experiments/LOCAL_EXPERIMENT_MANUAL.md)。
- 服务器选择、连接与平台操作：[REMOTE_WORKFLOW.md](experiments/REMOTE_WORKFLOW.md)、[ENVIRONMENT.md](experiments/ENVIRONMENT.md)；AI4S 的具体执行器和资源策略以 Program 与合同为准。
- 协作与文档职责：[AGENTS.md](AGENTS.md)；关键选择记录到 DECISIONS，当前任务更新到 TASKS，论文证据与写作判断维护在 PAPER。
- 实验结束后的产物分层与保留范围：[REPOSITORY_MAINTENANCE.md](docs/REPOSITORY_MAINTENANCE.md)。

## 仓库结构

| 路径 | 用途 |
| --- | --- |
| `PAPER.md`、`TASKS.md`、`DECISIONS.md` | 论文摘要、当前工作与关键取舍 |
| `ai4s/` | Program、活动链、研究合同、运行状态与证据索引 |
| `idea-stage/foundry/` | 独立候选生成与交接材料 |
| `refs/` | 文献、阅读卡与参考模型材料 |
| `src/`、`scripts/`、`tests/` | 数据/模型/训练评估代码、运行入口与验证 |
| `experiments/` | 实验协议、配置、环境与解释记录 |
| `results/` | 结果表格、图和经筛选的证据归档 |
| `data/`、`output/`、`checkpoints/`、`runs/` | 数据与机器产物；部分历史机器产物已迁至外盘，按归档索引定位 |
| `draft/` | 论文草稿、开题与调研材料 |
| `review/<project>/` | 需要独立协作时的任务交接与审查材料 |
| `docs/`、`_work/` | 维护说明、专题资料与治理/文档快照 |

优先围绕当前论文收敛问题、模型和证据；保持可复现记录，并让写作随实验推进。
