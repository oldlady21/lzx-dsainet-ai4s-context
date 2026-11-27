# MI-EEG Paper 1

本仓库围绕第一篇公开运动想象脑电（MI-EEG）解码论文开展研究。以已复现的模型为起点，找出影响解码的具体问题，再通过结构或模块改动检验能否改善。

## 从哪里开始

| 要处理的事 | 先读 |
| --- | --- |
| 查研究主线、已有证据和成稿条件 | [论文与证据](PAPER.md) |
| 确定当前优先事项 | [工作台](TASKS.md#当前工作台) |
| 查清某项取舍的依据 | [有效决策](DECISIONS.md#当前有效决策入口) |
| 设计、继续或核对一个 Program 的研究 | [AI4S 工作入口](ai4s/README.md) |
| 查协议、比较结果或实验原件 | [实验记录](experiments/README.md) · [结果归档](results/README.md) |
| 查原文、读精读卡或整理实验室来件 | [文献与复现材料](refs/README.md) |
| 生成 GPT 讨论库的本地预览 | [同步说明](docs/GPT_CONTEXT_SYNC.md) |

## 当前研究阶段

当前优先在已有模型上找到一项有实验正信号的结构改进。先定位模型在什么条件下表现受限，再用匹配对照检验改动能否解决问题。候选出现可信的正信号后，再考虑收敛成稿。

DSAINet 是论文首选主线。MVCNet 已在特定比较中取得实质性改进，保留同一优先级。DBConformer、SST-DPN 和 OTA 并行探索，形成有实质收益的改进时按其证据评估，也为 DSAINet 提供可借鉴的诊断、对照和反例。 [研究定位](PAPER.md#1-当前论文定位)

科研工作主要由 AI4S 承担，工作流也随实际研究持续调优。DSAINet 和 MVCNet 各自已有明确的探索方向，具体内容按对应 Program 的活动 L3 读取，当前研究任务见工作台。 [活动链索引](ai4s/PROMPT_INDEX.yaml) · [当前工作台](TASKS.md#当前工作台)

## 已有基模与实验资产

[中央 UEP 归档](results/archives/mieeg-uep-v1.0/README.md)覆盖 BNCI2014001 和 BNCI2014004。登记包括 DBConformer、DSAINet、MVCNet、SST-DPN、SMANet-100 和 STGMFM，共 34 条模型、数据集与协议组合。DBConformer 和 DSAINet 可在匹配训练设置下比较，其他条目各自保留训练配方和实现身份。SST-DPN 的 BNCI2014001 CO/CV 已有实验记录，正式入表前还需核对登记来源。

补充数据各有独立协议。[PhysioNet-MI](results/archives/mieeg-physionet-subject10fold-v1/README.md)登记两种模型的被试级十折结果，[Zhou2016](results/archives/mieeg-zhou2016-loso-v1/README.md)登记 DSAINet 的三分类 LOSO 基线。[BNCI2014002](experiments/BNCI2014002_EVALUATION_PROTOCOL.md)已完成数据与划分验收，固定 DSAINet 三臂本地 LOSO 已复算，P0 未通过效用和风险门。各结果的协议与证据范围见[论文数据表](PAPER.md#31-已有数据身份)。

SMANet 的旧输入诊断、cue-v2 会话重构和 Sinc 幅值比较，以及 LI-DSN 和 XW-Stroke 的复现记录，都可以从[论文证据说明](PAPER.md#4-基模与可用实验资产)查到。它们各自沿用原比较设置。

### 使用结果前需要核对

- 核对输入窗口和参考事件。已审计的 BNCI2014001 共享输入使用 trial 后四秒，对应 cue 相对 [−2, 2)，其他消费者按实际输入身份判断。 [窗口审计](PAPER.md#32-必须在稿件中披露的窗口发现)
- 核对数据、划分、训练设置和种子配对。exact-paired 支持匹配设置下的架构比较，eval-compatible 比较完整管线。 [统计口径](PAPER.md#33-可比性与统计口径)
- 核对 F1 的 macro 或 weighted 口径及原始预测的可恢复性。对技术通过、工程失败、诊断结果和性能结果，沿用各自的证据类别。 [结果入口](results/README.md)

## AI4S Program 与研究入口

先从 [Prompt Index](ai4s/PROMPT_INDEX.yaml) 定位 Program，再读取对应版本的 L1/L2/L3。已有 campaign、Run、operation 和冻结续接按记录中的绑定继续。State 登记运行，Evidence Index 指向证据，正式主张按相应 Claim Ledger 的判定引用。诊断和筛查需要说明结果改变了哪项设计或去留判断。 [AI4S 读取顺序](ai4s/README.md#每次任务的读取顺序) · [评估规则](ai4s/prompts/EVALUATION_EVIDENCE.md)

| Program | 配置 | 运行 | 证据 |
| --- | --- | --- | --- |
| MVCNet | [PROGRAM](ai4s/programs/mvcnet/PROGRAM.yaml) | [State](ai4s/programs/mvcnet/research/STATE.yaml) | [Evidence Index](ai4s/programs/mvcnet/research/EVIDENCE_INDEX.yaml) |
| DSAINet | [PROGRAM](ai4s/programs/dsainet/PROGRAM.yaml) | [State](ai4s/programs/dsainet/research/STATE.yaml) | [Evidence Index](ai4s/programs/dsainet/research/EVIDENCE_INDEX.yaml) |
| DBConformer | [PROGRAM](ai4s/programs/dbconformer/PROGRAM.yaml) | [State](ai4s/programs/dbconformer/research/STATE.yaml) | [Evidence Index](ai4s/programs/dbconformer/research/EVIDENCE_INDEX.yaml) |
| SST-DPN | [PROGRAM](ai4s/programs/sstdpn/PROGRAM.yaml) | [State](ai4s/programs/sstdpn/research/STATE.yaml) | [Evidence Index](ai4s/programs/sstdpn/research/EVIDENCE_INDEX.yaml) |
| OTA | [PROGRAM](ai4s/programs/ota/PROGRAM.yaml) | [State](ai4s/programs/ota/research/STATE.yaml) | [Evidence Index](ai4s/programs/ota/research/EVIDENCE_INDEX.yaml) |

一个 Program 对应一个基模，可承载多项研究。用户可以直接给出方向，也可以从 [Foundry](idea-stage/foundry/) 选定候选再交接。交接后按 Program 的授权和冻结流程推进。旧 proposed 研究按精确合同和[历史路径映射](ai4s/archive/PATH_MAP.json)追溯，外审按[触发与复用规则](ai4s/prompts/EXTERNAL_REVIEW.md)办理。

## 实验环境与工作方式

本机默认使用 `mieeg`，负责短时低负载的源码核对、单批 smoke、小样本技术检查和结果复算。新长时 AI4S 实验默认使用 Lab10，已有 Run 按冻结执行器收尾。实际环境、连接和资源策略由 Program 与合同指定。 [本地工作流](experiments/LOCAL_WORKFLOW.md) · [本地操作手册](experiments/LOCAL_EXPERIMENT_MANUAL.md) · [远端工作流](experiments/REMOTE_WORKFLOW.md) · [Lab10 手册](experiments/REMOTE_LAB10_AI4S.md) · [环境说明](experiments/ENVIRONMENT.md)

实验的完整机器产物与论文所用的结果分别归档。历史载荷缺失时，先从归档索引核实原件，再按对应清单恢复。协作、留存与发布分工见[协作说明](AGENTS.md)、[仓库维护](docs/REPOSITORY_MAINTENANCE.md)和[外盘归档](docs/ASSET_ARCHIVE.md)。

## 仓库结构

| 目录 | 内容 |
| --- | --- |
| `ai4s/`、`idea-stage/foundry/` | Program 研究、证据与候选交接 |
| `refs/` | 正式文献、精读卡和复现参考源码 |
| `src/`、`scripts/`、`tests/` | 实现、[运行入口](scripts/README.md)与验证 |
| `experiments/`、`results/` | 实验协议、解释记录与结果归档 |
| `data/`、`output/`、`checkpoints/`、`runs/` | 数据与机器产物 |
| `draft/` | [论文草稿与开题材料](draft/README.md) |
| `review/<project>/`、`docs/`、`_work/` | 协作交接、专题资料和文档历史 |
