# DECISIONS.md

## 2026-10-09 DSAINet/Zhou2016现有结果纳入本地补充基线

用户明确确认按现有结果归档和纳入本地基线。采纳唯一实验 `2026-10-09_dsainet_zhou2016_loso_full_local_w2`，20/20×100epoch、validation_best；ACC75.4423%、Weighted-F1 74.5420%，保持 `paper-aligned`、`ARCHIVED_LOCAL_BASELINE_WITH_WARNINGS`。原文均值差−2.77/−3.31pp、独立审查WARN和诊断因果未闭环均保留，不升级为精确复现，不进入BNCI UEP主表。原冻结机器/分析证据不改，新增诊断与用户确认附录；本轮工作关闭，后续官方执行路径对照需另行授权，不自动补训、调参或上传。见[诊断及确认](results/archives/mieeg-zhou2016-loso-v1/dsainet/diagnosis_20261009/README.md)。









本文件记录第一篇 MI-EEG 论文推进过程中的关键决策。  




只记录“为什么这样做”的事项，不记录日常流水。









---









## 当前有效决策入口









2026-09-25 新增 `D-180`（已实施）：AI4S 新研究统一迁移到 L1/L2/L3 v3.0。新版以论文问题、可执行干预和最小配对对照组织研究；诊断、筛查和负结果必须登记后续处置，并在下一轮说明新增证据如何改变设计。MVCNet、DSAINet、DBConformer、SST-DPN、OTA 的既有 campaign、Run、operation 和冻结续接沿原绑定链收尾；跨 Program 只共享证据与设计约束，不自动共享指标或执行授权。五项入口、兼容回归和集中外审处置见 [验收报告](ai4s/_work/workflow_review_20260924/V3_IMPLEMENTATION_REPORT.md)；本次未启动实验或追加预算。









2026-09-24 DBConformer NDD-D0关闭：54配对经冻结合同及独立复算，主判定OUTPUT_DIRECTION_COMPONENT_SUPPORT；仅解释APR源验证NLL的输出几何成分，不改变APR支持不足结论，不自动晋级候选或续轮。见 [报告](ai4s/programs/dbconformer/research/ndd_d0/REPORT.md)。









2026-09-24 DBConformer APR-R1 按冻结门判为 `INSUFFICIENT_SOURCE_PROJECTION_ADAPTATION_SUPPORT`：Q/K低秩适配改善原模型源验证NLL，但相对等参数Q/V、V/O未达到预设净优势，关闭本rank-1、20epoch精确实例，不自动调参或换臂晋级。仅source-valid筛查，不作目标域或因果主张；跨版本初始化校验修正本地确定性验收，专项外审未完成。权威结果见 [APR-R1](ai4s/programs/dbconformer/research/apr_r1/REPORT.md) 和Program Evidence Index。









2026-09-24 DBConformer DRA-R1 按冻结门判为 `INSUFFICIENT_SOURCE_DISTANCE_ADAPTATION_SUPPORT`：诊断中的距离敏感性未在本轮转化为足够的适配净收益，关闭本7参数共享偏置、20epoch精确实例，不否定全部距离建模方向。权威决策与范围见 [DRA-R1结果](ai4s/programs/dbconformer/research/dra_r1/REPORT.md) 及对应Program Evidence Index；不新增论文主张。









2026-09-19 新增 `D-179`：按用户选择建立 DBConformer、SST-DPN Program，使用 v2.1 新接入链；历史来源和精确边界保留，初始不创建 campaign。









本节只提供检索入口，不替代后文原始决策，也不改变任何既有 `D-xxx` 编号。2026-09-21 按 D-178 对齐顶层入口：旧 proposed 管理规则仅适用于历史追溯与明确旧 Run 收尾；原始决策正文保留。活动链与运行状态从 `ai4s/PROMPT_INDEX.yaml` 和对应 Program 读取，表内历史快照不授予新实验权限。日常工作优先核对：









| D-ID | topic | status | one-line scope |




|---|---|---|---|




| `D-178` | AI4S 承接与 proposed 退役 | 有效 | Program 科研流程；Foundry 独立交接；正式评估与 Claim Ledger 按需使用，按 Program 激活 |




| `D-180` | AI4S v3.0 研究闭环 | 有效 | 五 Program 新工作使用新版 L1/L2/L3；旧绑定收尾；证据通过问题地图跨 Program 复用，验收见实施报告 |




| `D-001` | 仓库定位 | 有效 | 仓库始终服务第一篇 MI-EEG 论文，保持轻量 |




| `D-032` | 实验记录分层 | 有效 | 机器/实验/任务/论文/决策层逐级记录，不重复记账 |




| `D-042` | 公开评估合同 | 有效 | 公开横向比较用 `mieeg-uep-v1.0`，区分 `exact-paired` 与 pipeline-level |




| `D-044` | [REDACTED_MACHINE] 调度 | 有效 | 证据约束的自主 Bundle 调度与回拉验证链 |




| `D-065` | ODF-v1 | 已关闭 | 精确合同关闭；不外推为全部输入因子化方向失败 |




| `D-066`–`D-068` | proposed 契约 | 历史适用（流程由 D-178 替代） | 项目契约、薄编排、方法 Skill、重要文档中文 |




| `D-071` | BBF-v0 | 已关闭 | D0 关闭；无训练或性能证据 |




| `D-086` | RCCF-v0 | 已关闭 | D0 construct hard gate 关闭；重开须回 S2 建新版本 |




| `D-103` | LCUS family / ACUS | Family paused · evidence_gap | 四轮线性互补入口均无发现信号 |




| `D-104` | CPDI / RCOD / UOD | Family exhausted · re-entry 无下一步 | K/V 替换轴已穷尽；同一快照不再搜索 |




| `D-107` | proposed 流程 | 历史适用（D-178） | family/cycle 双层成熟流程（v4.1 的基础） |




| `D-109` | proposed 流程 | 历史适用（D-178） | S6R 后强制 Family Maturation Review，性能门槛不再直接关闭 family |




| `D-110` | PCSR / PCHR / PCRR / PTAR | 四版均 no_signal；PTAR 已 S9；family exhausted | 对齐减轻 extra K/V 税，仍未过 vanilla 主门 |




| `D-111` | proposed 流程 | 历史适用（D-178） | v4.2 分离 family 成熟度、路线、child readiness 与暂停原因，并以轻量自然交接呈现 |




| `D-114` | TPCR / SATR | Family exhausted | SATR-v0.1 complete no-signal；唯一 child budget 已用且无新可归因诊断 |




| `D-115` | FAGER / event specialist | Historical core decision | gated residual 输给 ungated control；R1 曾形成 selection-used child anchor，后续状态见 D-118 |




| `D-116` | EFSR / DSAINet scale routing | Historical preupload record | r4 Bundle 本地验收的历史节点；后续结果见 D-120 |




| `D-118` | FAGER / IER re-entry | Historical review | 旧机制下未形成 child；更新机制的 diagnostic-ready 历史见 D-124 |




| `D-119` | proposed 流程 | 历史适用（D-178） | family re-entry 改为 Agent 主动、受限地搜索证据增量，child 门槛不放宽 |




| `D-120` | EFSR / DSAINet scale routing | Exact cycle closed · family paused(evidence_gap) | verified 36-unit primary 为 ambiguous；不跑 controls 或 rescue |




| `D-125` | EFSR optimization diagnostic | Completed · no_anchor | final fine residual scale 不解释 seed 翻转；family 恢复 paused(evidence_gap) |




| `D-121` | FAGER / IER re-entry | Historical diagnostic-ready route | IER-RIO-v0 后续结果见 D-122 |




| `D-122` | FAGER / IER-RIO / FAER | Historical child-ready route | FAER-v0.1 后续创建状态见 D-123 |




| `D-123` | FAGER / FAER | Historical creation | child budget 扩为 2/2 并创建 frozen-anchor child；最终结果见 D-136 |




| `D-124` | FAGER / IER re-entry | Historical diagnostic-ready route | 同 checkpoint residual on/off 路线；执行结果见 D-122 |




| `D-126` | FAGER / FAER S5 | Historical implementation gate | 本地 S5 已通过；远端结果与关闭见 D-136 |




| `D-127` | 顺序远端执行 | 队列完成并已回拉 | 六组 full 均 complete/intake；未判读 |




| `D-128` | 服务器顺序队列守护进程 | 有效 | 多实验按序执行改到 [REDACTED_MACHINE] nohup；本机不必在阶段之间在线 |




| `D-129` | SIGSEGV 后迁 mieeg-modern | 待命 | 当前 mieeg 队列正常则不动；再出现 SIGSEGV 则中止并迁剩余实验到 modern |




| `D-128` | EFSR activation diagnostic | Panel B 完成 · Panel A blocked | 官方同权零样本对象形成后被 intra 抹掉；不改父结论 |




| `D-129` | EFSR local train-then-probe | Panel C 完成 | 本地 36-unit 训练后对象更干净，仍被 intra 抹掉 |




| `D-130` | EFSR Panel A | 完成 | 父远端 36 checkpoint 回拉并探针；同样被 intra 抹掉 |




| `D-131` | EFSR intra 子层分解 | 完成 | attention residual 先跌、norm1 再补完；seed 主导性不一致 |




| `D-132` | EFSR family re-entry / ESFS child | Historical creation | compact event subsequence；最终结果见 D-137 |




| `D-134` | FAER r3 + PTAR 入队 | Historical execution | FAER r3 执行完成；科学判读见 D-136 |




| `D-135` | ESFS 远端 54-unit | Historical intake | 54/54 complete；科学判读与关闭见 D-137 |




| `D-136` | FAER S6D / event-specialist S6M | Exact cycle closed · family exhausted | 六-unit frozen-anchor screen no_signal；budget 2/2，无第 3 child 或 claim release |




| `D-137` | ESFS S6D / EFSR family S6M | Exact child closed · family exhausted | 54-unit screen no_signal；N1 不运行；budget 1/1，无救援或 claim release |




| `D-152` | OCSO / shared-operator moments | Exact cycle closed · family no_go | 45/45 moment 诊断未过 0.08 锚点；不实现 adapter |




| `D-162` | BSSF / band-specific spatial residual | Exact cycle closed · family paused(evidence_gap) | 18-unit P1−B0 `−0.270 pp`，no_signal；不重开 BSRD |




| `D-163` | WOET / window-origin TimeGraph | Exact cycle closed · family decision_pending | 45/45 origin-shift 过锚点；child 见 D-165 |




| `D-164` | BSRA / branch similarity-replaceability | Exact cycle closed · family paused(evidence_gap) | similar_but_not_replaceable；不创建 complementarity child |




| `D-165` | MOT / multi-origin window training | Child created | WOET 唯一 child；budget 1/1；S5 见 D-166 |




| `D-166` | MOT S5 | Implementation verified | D0/check/smoke PASS；非正式性能 |




| `D-167` | MOT S6D launch | Historical launch | A1 本地；P1 远端；判读见 D-168 |




| `D-168` | MOT S6D / family S6M | Exact child closed · family exhausted | 18-unit no_signal；budget 1/1 |




| `D-169` | MVCNet paper-release reconciliation | S2 contract frozen · S3 pending | MPRF-P1-v0.1 supporting provenance；未授权实现、训练或 claim |




| `D-170` | DSAINet RACR | Exact S6D no_signal · paused at S6M direct-exception boundary | r5 54/54 exact-paired intake；B1/B2/pairing gates failed；无 rescue 或 claim |




| `D-175` | VCN-P1 S8 claim 复核 | 有效 | 本地 checkpoint 回拉不是硬门；UTIL/ATTR scoped yes |




| `D-176` | VCN-P1 S9 收口 | 已关闭 | supporting evidence；保留 scoped UTIL/ATTR；不进入论文写作 |









查找具体依据时直接搜索决策编号；不要从本索引推断未写明的实验授权或 claim readiness。









---









## D-001 当前仓库围绕第一篇 MI-EEG 论文推进









- 当前仓库的组织方式围绕单篇 MI-EEG 高水平论文展开




- 文献、代码、实验和写作都服务这篇论文本身




- 仓库结构保持轻量，方便持续维护和 AI 协作









**原因：**




当前阶段更需要一个聚焦、清晰、低维护成本的论文仓库，以便尽快形成文献—复现—创新—写作闭环。









---









## D-002 研究主线聚焦公开数据集上的 MI-EEG 解码









- 第一篇论文主要使用公开 MI-EEG 数据集




- 优先围绕标准公开 benchmark 开展复现、改模与实验




- 暂不将自采数据或临床数据作为论文主实验前提









**原因：**




公开数据集协议更成熟，便于快速复现、做对比实验和形成高质量论文。









---









## D-003 第一篇论文优先走“结构创新”路线









- 当前优先考虑网络结构创新、模块创新、多尺度时空建模、混合模型增强




- 暂不把大模型、几何学习、复杂损失函数优化作为主线









**原因：**




该路线与已有文献整理、导师意见和当前能力积累最匹配，也更利于形成清晰论文叙事。









---









## D-004 默认选择 DBConformer 作为统一复现底座









- 当前默认以 DBConformer 作为主 baseline




- 其他模型如 MVCNet、MSVTNet 可作为横向参考或补充对照









**原因：**




DBConformer 结构清晰、数据集覆盖广、仓库成熟，适合作为统一实验平台与后续改模起点。









---









## D-005 当前工作流采用轻量文档驱动模式









核心文件固定为：




- `README.md`




- `AGENTS.md`




- `DECISIONS.md`




- `TASKS.md`




- `PAPER.md`









**原因：**




保持仓库简单，降低理解和维护成本，优先保证推进效率。









---









## D-006 论文写作与实验并行推进









- 不等所有实验完成后再开始写作




- 从早期开始同步积累 outline、related work、method、experiments 草稿









**原因：**




论文写作本身有助于暴露问题和收敛实验设计，越早开始越有利于整体推进。









---









## D-007 候选创新方向 A 进入初步讨论（跨分支交互）【待确认】









- 在文献梳理和讨论阶段，识别出 DBConformer 的主要设计弱点之一：




  temporal 和 spatial 两个分支完全独立，late fusion 损失联合时空结构信息




- 初步候选方向为在中间层引入双向跨分支交互模块（CBI）




- 该方向尚未经过完整文献验证和代码分析，不作为固定决策









**原因：**




在用户尚未完成 DBConformer 完整阅读前，保留候选方向记录，方便后续对齐与收敛。









---









## D-008 当前工作重心切换到 DBConformer 精读与复现准备









- `refs/` 目录已完成第一轮整理，能够支撑后续 baseline 精读与对照阅读




- 当前不再继续扩张文献池，优先把精力集中到 `DBConformer`




- 下一阶段默认按“论文精读 -> 代码结构拆解 -> 最小复现骨架 -> 跑通 baseline”推进









**原因：**




前期文献压缩与仓库整理已经达到“可以开工 baseline”的程度。此时继续泛化调研的收益下降，而尽快建立对 `DBConformer` 论文与代码的可操作理解，更有利于进入真正的复现闭环。









---









## D-009 本地-服务器协作采用轻量 SFTP 工作流









- 本地始终作为代码、配置、文档和正式实验记录的真源




- 服务器作为实验运行环境，只生成机器实验产物




- 服务器完整实验产物统一放在 `outputs/`




- 本地整理后的论文结果统一放在 `results/`




- `data/`、`checkpoints/`、`runs/`、`tmp/` 默认不参与同步




- 第一阶段先手动 SFTP，同步脚本等路径和目录稳定后再实现









**原因：**




当前优先目标是尽快跑通 DBConformer baseline 最小复现闭环。轻量 SFTP 能满足本地改代码、服务器跑实验、结果回流本地的需求，同时避免过早引入复杂协作和自动化。









---









## D-010 服务器 baseline 环境先固定为 `mieeg`









- 实验服务器：`[REDACTED_MACHINE]`




- 登录账号：`bdi2l_ski`




- 个人工作路径：`[REDACTED_MACHINE]`




- Miniconda 路径：`[REDACTED_MACHINE]`




- conda 环境目录：`[REDACTED_MACHINE]`




- 当前 baseline 环境名：`mieeg`




- Python 版本：`3.9.25`




- Python 解释器：`[REDACTED_MACHINE]`




- 系统：`Ubuntu 20.04.6 LTS`




- GPU：`10` 张 NVIDIA GeForce GPU，每张约 `11 GB` 显存




- Driver / CUDA：`510.39.01` / `11.6`




- 内存：约 `566 GiB`




- 主要可用空间：个人盘约 `2.5T` 可用，数据盘约 `2.8T` 可用









**原因：**




先固定一个明确、可复查的服务器运行环境，便于后续 DBConformer baseline 复现、实验日志记录和结果回流。当前服务器 CUDA 为 `11.6`，环境内优先安装与 CUDA 11.x 匹配的 baseline 必需包，暂不引入与当前论文主线无关的大量依赖。









---









## D-011 DBConformer 初次复现以 MOABB 生成的 BNCI2014001 数据为准









- 已完成 `DBConformer` 在 `BNCI2014001` 上的第一次 CO / LOSO / CV 复现




- 正式有效结果使用 MOABB 流程重新生成的数据，而不是早期手工 `.mat` 提取数据




- 本次复现结果：




  - CO: `77.85714`




  - LOSO: `76.29630`




  - CV: `83.31034`




- 每个协议均完成 `5 seeds x 9 subjects = 45` 条正式结果




- 服务器端使用 wrapper 控制实验入口，没有直接修改官方 `DBConformer_CO.py`、`DBConformer_LOSO.py`、`DBConformer_CV.py` 的默认循环




- 服务器端对 `utils/network.py`、`utils/utils.py`、`utils/data_utils.py` 的改动暂定为兼容修复，不视为方法创新；是否迁入本地代码需单独审查









**原因：**




早期手工 `.mat` 提取数据导致 CO 结果约 `64.29%`，明显偏离论文目标；改用 MOABB 重新生成数据后，结果回到合理区间。为了后续 baseline 与 proposed 实验一致，BNCI2014001 的 DBConformer 路径应优先以 MOABB 生成数据为准，并在实验记录中明确数据来源。









---









## D-012 本地电脑作为日常实验主环境









- 本地电脑承担日常实验工作，包括代码迁移、wrapper 调试、smoke test、小规模复跑和 proposed model 最小验证




- 本地完整机器产物放入 `output/local/<exp_id>/`




- 本地筛选后值得保留的关键日志放入 `results/logs/local/<exp_id>/`




- 本地正式实验记录由 `experiments/records/<model>/` 维护；当前推荐的协议级记录粒度见 D-032，已有按 `exp_id` 建立的历史记录继续保留




- `data/`、`output/`、`checkpoints/`、`runs/`、`tmp/` 默认不进入 Git




- 实验室服务器继续用于完整协议、多 seed、多 subject、多 baseline、多数据集和长时间实验









**原因：**




本地电脑已有可用 GPU 环境，适合承担更自由、更快速的日常迭代；服务器多卡和大内存优势仍适合最终批量验证。这样可以在不增加复杂管理系统的前提下，同时保留本地灵活性和服务器算力优势。









---









## D-013 BNCI2014001 的第一版 baseline 以 2026-06-09 本地全量复现为当前参照









- 已在本地 `mieeg` 环境完成 DBConformer / BNCI2014001 的 CO、LOSO、CV 全量复现




- 三个协议均覆盖 `5 seeds x 9 subjects = 45` 条正式结果，未发现缺失或重复




- 本地复现结果：




  - CO: `77.85714 +/- 1.21405`




  - LOSO: `76.29630 +/- 0.99701`




  - CV: `83.32567 +/- 0.85176`




- 本地结果与 2026-05-18 服务器回流复现高度一致




- 后续 proposed model 在 BNCI2014001 上的第一版最小实验，应优先以这轮本地 baseline 作为直接比较参照




- 在 proposed 出现稳定正信号前，暂不盲目扩展多个新数据集









**原因：**




本地已经跑通并复核完整 CO / LOSO / CV 闭环，结果可重复地落在服务器复现附近。此时继续扩展数据集的边际收益低于先基于稳定 baseline 做最小创新实验；先收敛 BNCI2014001，有利于保持论文主线清晰。









---









## D-014 BNCI2014004 作为第二个经典数据集 baseline 已完成本地全量复现









- 已在本地 `mieeg` 环境完成 DBConformer / BNCI2014004 的 CO、CV、LOSO 全量复现




- 原始数据已复制到项目库 `data/raw/BNCI2014004/`




- 有效训练数据使用 MOABB 流程生成，并同步到官方 DBConformer 数据目录




- 三个协议均覆盖 `5 seeds x 9 subjects = 45` 条正式结果，未发现缺失或重复




- 本地复现结果与论文 Table IV 对照：




  - CO: 本地 `75.00000 +/- 0.97112`，论文 `75.09 +/- 1.5`




  - CV: 本地 `73.18519 +/- 0.47068`，论文 `74.17 +/- 0.6`




  - LOSO: 本地 `69.77778 +/- 0.85787`，论文 `69.85 +/- 0.5`




- 运行时采用 subject 分片三路并行，以提高本地 GPU 利用率；未改变 batch size、epoch、seed、模型超参或评价协议




- BNCI2014004 后续可作为 proposed model 的第二数据集验证，但不改变“先在 BNCI2014001 上做最小改动验证”的当前主线









**原因：**




BNCI2014004 是 BCI Competition IV-2b，属于 MI-EEG 经典二分类数据集，且与 BNCI2014001 形成稀疏通道场景互补。本轮复现已经证明本地环境能稳定完成该数据集的 DBConformer 三协议 baseline，结果与论文基本对齐，可为后续 proposed 泛化验证提供直接参照。









---









## D-015 DSAINet 进入候选核心文献复现队列









- DSAINet 暂作为候选核心文献，而不是已确认核心 baseline




- 第一阶段只做本地可控复现判断，优先使用 BNCI2014001




- 官方仓库保留在 `refs/models/DSAINet-main/DSAINet-main/` 作为只读参考




- 本地实验入口、数据适配和结果记录放在项目侧 `scripts/`、`experiments/`、`results/`




- 不直接使用官方训练入口作为正式复现入口，因为它存在 Linux 路径硬编码、eager import 所有预处理脚本、缺少依赖清单等问题




- 只有当 BNCI2014001 复现结果稳定、产物完整且协议差异可解释时，才考虑将 DSAINet 晋升为核心文献









**原因：**




DSAINet 与当前论文关注的多尺度、交互式 EEG 解码方向高度相关，但其开源代码需要本地适配后才能稳定复现。先用 DBConformer 已验证的数据与记录标准进行可控复现，可以避免过早把不稳定代码纳入核心对照体系。









---









## D-016 暂不将 DSAINet 晋升为核心文献 baseline









- 已完成 DSAINet / BNCI2014001 的 CO、LOSO、CV 本地全量复现




- 三个协议的运行产物完整，训练脚本和数据索引未发现明显异常




- 当前本地结果：




  - CO：`64.290%`




  - LOSO：`45.039%`




  - CV：`73.993%`




- 其中 LOSO 与原文 BCIC-IV-2a 结果差距较大，暂不作为核心 baseline




- 当前结果记录为 `DSAINet model + 本仓库统一 MOABB/DBConformer 数据管线` 的受控复现，而不是严格官方 DSAINet 数据管线复现




- 后续若继续评估 DSAINet，应优先补一版等价官方 `0.5-40 Hz` GDF/BCIC-IV-2a 预处理，并诊断官方脚本中的 `All Epoch` / test-best 评价口径影响









**原因：**




本轮核查显示 LOSO 划分、模型超参、训练 epoch、batch size、学习率、Z-score 和 classwise augmentation 与官方脚本基本一致；差异主要集中在数据预处理来源和评价口径。官方 DSAINet 预处理从 GDF 读取并做 `0.5-40 Hz` 滤波、去 EOG、`0-4 s` epoch，而当前本地数据来自 MOABB/DBConformer 管线后裁剪到 1000 samples。此外官方训练脚本同时保存 validation-best 与 test-best 两类模型，若原文结果接近 test-best 口径，会高于本地 validation-best wrapper。为避免引入不稳定对照，暂不将 DSAINet 作为核心 baseline。









---









## D-017 DSAINet 官方风格预处理 LOSO 结果已与原文对齐









- 已用官方风格预处理数据重跑 DSAINet / BNCI2014001 LOSO




- 本轮仍采用 validation-best 口径，没有使用 `test-best / all-epoch`




- 完整性：`45/45` seed-subject pairs，无缺失、无重复




- 官方风格预处理 LOSO 结果：




  - ACC：`62.052%`




  - F1：`60.978%`




  - Kappa：`49.403%`




- 原文 BCIC-IV-2a 参考：ACC `61.79 +/- 0.68`，F1 `59.65 +/- 0.77`




- 当前判断：DSAINet 在 BNCI2014001 的官方可比 LOSO 协议上已经达到原文附近；上一轮 `45.039%` 主要由预处理管线不一致导致




- DSAINet 可重新进入核心文献候选的正向队列，但 CO/CV 仍属于本仓库补充协议，不能直接声称是原文同协议复现




- 已补充官方风格预处理下的本仓库 CO/CV 结果：




  - CO：ACC `64.074%`, F1 `63.525%`




  - CV：ACC `78.959%`, F1 `78.811%`









**原因：**




更换到官方风格 `0.5-40 Hz`、`0-4 s`、22 EEG 通道预处理后，LOSO 性能从 `45.039%` 提升到 `62.052%`，与原文结果基本一致。这说明 DSAINet 对 BCIC-IV-2a 预处理管线高度敏感；后续若将其作为核心 baseline，应明确区分官方可比 LOSO 结果和本仓库补充 CO/CV 结果。









---









## D-018 优先在 DSAINet 统一协议下重跑 DBConformer









- 既有 DBConformer / BNCI2014001 LOSO `76.296%` 对应第一 session 的左手/右手二分类、EA 和 DBConformer 原生训练协议




- DSAINet Table III 对应两个 session、四分类、无 EA、严格被试独立 LOSO，因此两组数值不能直接比较




- DSAINet 原文统一协议下的参考结果：




  - DBConformer：ACC `58.14 +/- 0.36%`，F1 `55.48 +/- 0.41%`




  - DSAINet：ACC `61.79 +/- 0.68%`，F1 `59.65 +/- 0.77%`




- 当前优先补跑统一协议 DBConformer，再决定是否先扩展 DSAINet 的第二数据集




- 实验产物与原版 DBConformer 复现隔离，但复用 DSAINet 已验证的官方风格数据、LOSO 划分、增强、Z-score 和 validation-best 训练评估入口




- 原版 `scripts/run_dbconformer_bnci2014001.py` 保持不变；统一协议使用独立入口、配置、`exp_id` 和 checkpoint 目录




- 已完成 check、模型前向和单被试 1 epoch smoke，尚未运行正式 100 epoch 结果









**原因：**




当前最关键的证据缺口不是 DSAINet 能否在更多数据集上运行，而是其相对 DBConformer 的提升能否在同一数据、类别、划分和训练口径下独立复现。先完成这一公平对照，可以避免把二分类原版 DBConformer 结果与四分类 DSAINet 结果混用，并直接决定 DSAINet 是否足以晋升为核心文献和横向 baseline。









---









## D-019 DSAINet 统一协议下相对 DBConformer 的提升已复现









- DBConformer 统一四分类 LOSO 全量结果：




  - ACC：`57.612%`，seed mean std `0.571%`




  - F1：`55.283%`，seed mean std `0.743%`




  - 原文参考：ACC `58.14 +/- 0.36%`，F1 `55.48 +/- 0.41%`




- 本地同协议 DSAINet：




  - ACC：`62.052%`




  - F1：`60.978%`




- DSAINet 相对 DBConformer：




  - ACC：`+4.441 pp`




  - F1：`+5.694 pp`




  - 五个 seed 的 ACC 提升均为正




- 45 个同 seed-subject 配对结果中，DSAINet 的 ACC 在 36 对更高、2 对持平




- ACC 配对 t 检验 `p=6.10e-08`，Wilcoxon `p=8.88e-07`




- DSAINet 可正式纳入核心文献，并作为统一 subject-independent 四分类协议下的强横向模型




- DBConformer 原论文二分类结果仍作为 proposed 开发主 baseline，不能与本次四分类比较混用









**原因：**




本轮 DBConformer 的 ACC 和 F1 分别只比 DSAINet 原文表格低 `0.528` 和




`0.197` 个百分点，说明统一比较框架已基本复现。DSAINet 在完全一致的数据、




划分、训练和模型选择口径下取得稳定且统计显著的提升，因此原文关于相对




DBConformer 的性能优势在本地得到支持。









---




## D-020 DSAINet 第二数据集优先复现 BNCI2014004 的官方 LOSO









- 已从本地连续信号 MAT 文件生成 BNCI2014004 全部五个 session 的官方风格数据




- 数据包含 6520 trials、3 EEG channels、左右手二分类，类别完全平衡




- 预处理为 `0.5-40 Hz`、250 Hz、cue 后 `0-4 s`




- CO、LOSO、CV 的数据检查和短 smoke 均已通过




- DSAINet 原文只在该数据集报告 subject-independent LOSO：




  - ACC `76.41 +/- 0.31%`




  - F1 `75.91 +/- 0.36%`




- 已先完成本仓库补充协议的 CO/CV 全量实验：




  - CO：ACC `75.508%`、F1 `75.356%`




  - CV：ACC `75.910%`、F1 `75.758%`




  - 两个协议均为 `45/45` seed-subject pairs，CV 为 `225/225` fold rows




- 已完成官方可比 subject-independent LOSO 全量实验：




  - ACC `73.052%`，seed mean std `0.506%`




  - F1 `72.699%`，seed mean std `0.566%`




  - Kappa `46.105%`




  - 完整性为 `45/45` seed-subject pairs，无缺失、无重复




- 本地 LOSO 比原文低 `3.358 pp` ACC 和 `3.211 pp` F1，说明跨数据集复现趋势成立，




  但当前实现尚未完全达到原文 BCIC-IV-2b 数值




- 上述 CO/CV 仍只作为本仓库补充协议，不能作为原文同协议复现




- 既有 DBConformer / BNCI2014004 `69.778%` LOSO 只使用第一 session 和 EA，




  不能直接与本次 DSAINet 全 session 结果比较









**原因：**




BNCI2014004 是 DSAINet 原文明确覆盖的第二个经典 MI 数据集，并提供仅 3 通道




的低空间分辨率场景。本轮已经完成相同全 session、3 通道和 subject-independent




LOSO 口径的本地全量实验。结果明显高于随机水平且五个 seed 稳定，但仍低于原文




约 3 个百分点；后续比较应保留这一复现差距，避免与第一 session + EA 的




DBConformer 结果混用。









---









## D-021 BNCI2014001 统一协议 CO/CV 公平对照已补齐









- 在与 DSAINet 相同的官方风格数据、双 session、四分类、无 EA、




  validation-best、5 seeds × 9 subjects 设置下补跑 DBConformer：




  - CO：ACC `65.293 +/- 0.672%`，F1 `65.035%`




  - CV：ACC `75.540 +/- 0.215%`，F1 `75.357%`




- 同设置 DSAINet：




  - CO：ACC `64.074 +/- 1.481%`，F1 `63.525%`




  - CV：ACC `78.959 +/- 0.562%`，F1 `78.811%`




- CO 中 DSAINet ACC 低 `1.219 pp`，配对 t 检验 `p=0.176`，




  Wilcoxon `p=0.065`，没有稳定显著差异




- CV 中 DSAINet ACC 高 `3.419 pp`，45 对中胜出 `37` 对，




  配对 t 检验 `p=1.79e-06`，Wilcoxon `p=3.00e-07`




- 结合既有 LOSO `+4.441 pp`，当前结论是 DSAINet 在 CV 和 LOSO 下具有




  稳定优势，但 CO 下没有优于 DBConformer




- 运行时命令行 `--protocol co/cv` 决定实际划分；配置文件中遗留的




  `protocol.name: loso` 只属于元数据，不参与训练分支选择，正式记录中需注明









**原因：**




补齐 CO/CV 后可以避免从单一 LOSO 结果泛化为“DSAINet 在所有协议都优于




DBConformer”。本地证据显示其改进更可能集中在需要更强泛化或表征学习的




CV/LOSO 场景；CO 下两者性能接近，DBConformer 均值反而略高。









---









## D-022 BNCI2014004 统一协议三协议公平对照已补齐









- 已在与 DSAINet 相同的全 5 sessions、3 通道、二分类、无 EA、




  validation-best、5 seeds × 9 subjects 设置下完成 DBConformer：




  - CO：ACC `77.530 +/- 0.863%`




  - CV：ACC `75.702 +/- 0.458%`




  - LOSO：ACC `71.490 +/- 0.460%`




- 同设置 DSAINet：




  - CO：ACC `75.508 +/- 0.479%`




  - CV：ACC `75.910 +/- 0.410%`




  - LOSO：ACC `73.052 +/- 0.506%`




- CO 中 DSAINet 低 `2.022 pp`，配对 t 检验 `p=0.0030`，




  DBConformer 显著更高




- CV 中 DSAINet 仅高 `0.208 pp`；配对 t 检验 `p=0.697`，




  虽然 Wilcoxon `p=0.0129`，但效应很小，应判断为均值基本持平




- LOSO 中 DSAINet 高 `1.562 pp`，配对 t 检验 `p=4.88e-04`，




  Wilcoxon `p=0.0015`，跨被试优势在第二数据集得到支持




- DSAINet 在 BNCI2014004 的 LOSO 提升小于 BNCI2014001 的 `4.441 pp`，




  说明提升幅度具有数据集依赖性









**原因：**




第二数据集的完整公平对照进一步收敛了结论：DSAINet 的主要优势是跨被试泛化，




而不是在所有协议下全面优于 DBConformer。CO 更适合保留 DBConformer，




CV 两者近似，LOSO 才是 DSAINet 最稳定的优势场景。









---









## D-023 DSAINet test-best 只作为诊断上界，不进入正式结果









- 已完成 DSAINet / BNCI2014001 / 官方风格预处理 LOSO 的 test-best 全量实验




- test-best 严格复用官方 `All Epoch` 逻辑：每个 epoch 在测试被试上评估，




  按最高 test accuracy、并列时最低 test loss 选择 checkpoint




- 完整性为 `45/45` seed-subject pairs




- 结果：




  - test-best ACC `66.906 +/- 0.463%`




  - test-best F1 `66.466 +/- 0.526%`




  - validation-best ACC `62.052 +/- 1.015%`




  - validation-best F1 `60.978 +/- 1.295%`




  - 原文 ACC `61.790 +/- 0.680%`




  - 原文 F1 `59.650 +/- 0.770%`




- test-best 相对 validation-best 提升 `4.853 pp` ACC 和 `5.489 pp` F1，




  相对原文高 `5.116 pp` ACC 和 `6.816 pp` F1




- 该提升来自测试集参与模型选择，属于乐观偏差，不代表真实泛化提升




- 正式结果继续使用 validation-best；test-best 仅保留为复现诊断和评价口径敏感性证据




- BNCI2014004 test-best 全量实验后续已完成，结论见 D-024









**原因：**




本地 validation-best 已与原文基本对齐，而 test-best 明显超过原文。这排除了




“必须依赖 test-best 才能复现原文”的解释，并说明官方 All Epoch 输出若被用于




主结果，会高估模型性能。为了保持公平和可发表性，后续 baseline/proposed




比较必须禁止测试集选 epoch。









---









## D-024 BNCI2014004 原文结果与 test-best 几乎精确对齐









- 已完成 DSAINet / BNCI2014004 / 官方风格预处理 LOSO test-best 全量实验




- 完整性：`45/45` seed-subject pairs




- 本地 test-best：




  - ACC `76.487 +/- 0.264%`




  - F1 `76.358 +/- 0.268%`




- 原文：




  - ACC `76.410 +/- 0.310%`




  - F1 `75.910 +/- 0.360%`




- 本地 test-best 与原文差值：




  - ACC `+0.077 pp`




  - F1 `+0.448 pp`




- 本地 validation-best 为 ACC `73.052%`、F1 `72.699%`




- test-best 相对 validation-best 提升 `3.435 pp` ACC 和 `3.659 pp` F1；




  45 个配对 ACC 全部提高




- 数值与波动的高度一致，是原文 BCIC-IV-2b 结果采用或高度接近官方




  All Epoch/test-best 输出的强证据，但不是对取值来源的直接证明




- 正式公平比较仍使用 validation-best；test-best 只用于解释原文数值









**原因：**




test-best 通过测试集逐 epoch 选模型，必然产生乐观偏差。它在 BNCI2014004




上与原文几乎精确对齐，解释了 validation-best 低约 3 个百分点的原因；




但 BNCI2014001 的 test-best 又明显高于原文，提示原文不同数据集可能采用了




不同输出口径，或仍存在未复现的汇总细节。不能因此把 test-best 设为后续标准。









---









## D-025 MVCNet 复现结束，暂不晋升为核心 baseline









- 已完成 MVCNet / BNCI2014001 的 CO、CV、LOSO 全量本地复现




- BNCI2014001 本地结果与原文 Table IV 对照：




  - CO：本地 `81.587 +/- 1.785%`，原文 `83.17 +/- 0.74%`，差值 `-1.583 pp`




  - CV：本地 `82.830 +/- 0.341%`，原文 `84.49 +/- 0.61%`，差值 `-1.660 pp`




  - LOSO：本地 `83.858 +/- 0.477%`，原文 `76.02 +/- 0.57%`，差值 `+7.838 pp`




- BNCI2014001 的 CO/CV 接近但低于原文；LOSO 明显高于原文，不能判断为同口径对齐




- 已用官方 `MVCNet_LOSO.train_target` 抽查 BNCI2014001 seed 1 的 subjects 0/1：




  - subject 0：`79.861%`




  - subject 1：`70.833%`




  - 两个结果均与本仓库 wrapper 全量表完全一致，说明偏差不是 wrapper 引入




- 已完成 MVCNet / BNCI2014004 的 CO、CV、LOSO 本地扩展实验：




  - CO：`74.537 +/- 1.656%`




  - CV：`75.204 +/- 0.348%`




  - LOSO：`70.574 +/- 0.328%`




- 但 MVCNet 原文 Table IV 不包含 BNCI2014004，因此 BNCI2014004 结果只能作为本地扩展对照，不能作为原文同表复现证据




- 当前结论：MVCNet 保留为 related work 中“多视图/对比学习”代表或次级横向参考，暂不纳入核心 baseline；除非后续需要专门核查论文表格口径，不再继续扩展 MVCNet 复现实验









**原因：**




BNCI2014001 LOSO 与原文 Table IV 不对齐，且官方入口单点复查复现了同一批




wrapper 结果，基本排除了本地 wrapper 造成偏差的解释。BNCI2014004 虽然已经




完成三协议本地扩展，但原文没有该数据集结果。继续投入 MVCNet 复现的边际收益




低于回到 DBConformer/DSAINet 已验证基线上的 proposed model 最小验证。









---









## D-026 记录 DBConformer baseline 来源，并将 proposed 开发入口迁入 src









- 2026-06-09 BNCI2014001 和 2026-06-13 BNCI2014004 原生协议复现继续作为当前可信 baseline




- 使用 SHA-256 manifest 记录原始 DBConformer 模型、CO/CV/LOSO 训练入口和关键历史结果




- 项目侧 wrapper、`src/` 运行接口和 proposed 注入代码保持可维护，不纳入强制哈希锁




- 哈希检查只在显式运行 `scripts/verify_dbconformer_baseline.py` 时执行，不在普通训练、import 或模型加载时自动阻断




- `refs/models/DBConformer-main/` 保持为原始 baseline 参考源码，不直接承载 proposed 开发




- 在 `src/models/dbconformer/` 提供 baseline 加载接口




- 在 `src/training/dbconformer_protocol.py` 提供模型工厂注入点，复用原生 CO/CV/LOSO 训练循环




- baseline 与 proposed 共用的结果汇总逻辑迁入 `src/evaluation/`，原 CLI 脚本保留兼容




- 第一版 CBI 及后续创新实现放入 `src/`，并先通过迁移 baseline 等价性检查









**原因：**




现有 baseline 已形成可复现闭环，但官方源码和项目 wrapper 分散在 `refs/models/`




与 `scripts/`。在 proposed 开发前记录原始来源并隔离创新代码，有助于回溯




baseline；同时避免把审计机制耦合进日常开发路径，保留 wrapper 与 proposed




接口的正常演进空间。









---









## D-027 第一版 proposed 先验证 CfC 时间主干替换









- 在 DBConformer 双分支框架中保留原 Temporal Stem、空间分支、通道注意力池化和分类头




- 仅将 Temporal Transformer 替换为 full-gated CfC，默认仍使用拼接融合




- 第一轮严格复用 BNCI2014001 原生二分类 + EA 的 CO/CV 数据、划分、优化器、seed 和 epoch 设置




- gate fusion 暂不与 CfC 同时引入，避免把时间主干与融合方式的效果混在一起




- CfC 路线先作为候选 B 的最小结构实验，不自动取代仍待差异化论证的 CBI 候选 A




- CO/CV 的 check、单 seed/单 subject/2 epochs smoke 已通过；CO/CV/LOSO 全量实验均已完成，45/45 seed-subject pairs 完整；第一轮结果为 CO `76.34921`、CV `83.89710`、LOSO `74.75309`




- 2026-07-10 短诊断显示：增大 `cfc_hidden_size/backbone_units` 没有稳定收益；更小 `patch_size` 在 LOSO 子集上有正信号




- `patch_size=77` 的三协议 full 已完成：CO `78.57143`、CV `83.81554`、LOSO `76.51235`；较初版 CfC 分别为 `+2.22222`、`-0.08155`、`+1.75926 pp`，其中 LOSO 提升显著（paired t-test `p=0.01923`），CO/CV 不退化




- 三协议相对 DBConformer 的差值为 `+0.71429`、`+0.48987`、`+0.21605 pp`，均无显著差异；后续 CfC 优先固定该设置并进入跨数据集验证，代价是训练时间明显增加




- BNCI2014004 的 p77 三协议 full 已完成：CO `72.03704`、CV `72.55556`、LOSO `66.27778`，相对 DBConformer 分别为 `-2.96296`、`-0.62963`、`-3.50000 pp`；其中 LOSO 显著下降（paired t-test `p=3.21e-05`），因此当前 CfC 只保留为需诊断的候选路线，不宣称跨数据集泛化优势




- BNCI2014004 LOSO 的 p125 对照为 `67.77778`，较 CfC p77 显著提高 `+1.50000 pp`（`p=0.03692`），但仍显著低于 DBConformer p125 `69.77778`（`-2.00000 pp`，`p=4.07e-04`）；细 token 会加重退化，但其与固定 timespan 的失配当时仍只是待检验因素




- 固定 p77 的短配对诊断（subjects `0/2/4/6/8`、seeds `1/2`、30 epochs）中，`cfc_timespan=0.308 s` 为 `69.75000`，低于默认 `0.500 s` 的 `70.16667`（`-0.41667 pp`；paired t-test `p=0.32212`，Wilcoxon `p=0.53125`，胜/平/负 `2/2/6`）；因此没有证据表明仅按 patch 时长对齐 timespan 能修复 p77 的低通道 LOSO 缺口




- 2026-08-09：经 `2026-08-09_dbconformer_cfc_reassessment` 对原始产物、实现/协议和相关工作的复核，用户关闭该“时间 Transformer → CfC”的 `proposed_v1` 主线，记为**范围限定的 NO-GO**。不得在此主线下继续以宽度、patch、timespan、gate fusion、跨分支交互或 `diagnostic`/`pilot`/`full` 方式作后验救援；保留代码和完整产物作为负边界证据。该决定不外推为 CfC 在所有 EEG 或时间序列任务中无效；不规则、缺失或异步 MI 若要研究，须作为新科学问题重新建立明确合同与周期。









**原因：**




CfC 可以在不改动空间分支和训练协议的前提下形成清晰的单变量主干对照，并将当前




模型参数量从 `93,747` 降至 `64,107`。先验证其准确率与效率信号，再决定是否扩展




门控融合或与跨分支交互结合，可以减少第一轮实验中的结构混杂。









---









## D-028 固定 2025-2026 MI-EEG 文献搜集与纳入标准









- 时间范围固定为 `2025-2026`；仅收集以真实 MI-EEG 数据集为实验对象的论文或预印本




- 核心纳入方向必须是网络结构或可拆分模块创新：




  - 可作为深度学习网络结构强 baseline 的工作




  - 对时空频等多域特征学习、显式双分支/多分支建模或融合机制有直接启发的工作




- 不纳入以预训练、基础模型/tokenizer、测试时适配、参数高效微调，或以损失函数/对齐目标优化为主要贡献的工作；若论文含有这些成分，但其核心价值明确在可独立评估的网络结构模块，才可保留其结构部分




- 期刊论文原则上要求中科院二区及以上；按以下优先级覆盖来源：




  - 神经工程与生物医学工程：`IEEE Transactions on Biomedical Engineering`、`IEEE Transactions on Neural Systems and Rehabilitation Engineering`、`Journal of Neural Engineering`、`IEEE Journal of Biomedical and Health Informatics`




  - AI 与信号处理：`IEEE Transactions on Neural Networks and Learning Systems`、`Pattern Recognition`、`Neural Networks`、`IEEE Transactions on Signal Processing`




  - 脑机制与临床 EEG：`NeuroImage`、`Clinical Neurophysiology`、`Human Brain Mapping`、`Neurorehabilitation and Neural Repair`




  - 在线 BCI/临床转化：`Nature Biomedical Engineering`、`Nature Communications`、`Nature Machine Intelligence`、`npj Digital Medicine`、`Science Robotics`、`IEEE Transactions on Human-Machine Systems`




  - 高质量结构创新与可复现 baseline 补充：`Knowledge-Based Systems`、`Information Sciences`、`Neurocomputing`、`Applied Soft Computing`、`Measurement`




- 综合性顶刊、在线 BCI 和临床转化论文仍须通过同一结构门槛：若主贡献是闭环范式、用户训练、系统工程、损失/样本重加权或微调，而非可独立评估的解码结构/模块，则仅作为应用背景，不进入正式结构文献池或复现队列




- 不将 `Scientific Reports`、`Frontiers` 系列作为正式高价值文献或复现候选；已检索到的相关论文仅可作为背景线索，不进入主文献池




- 会议论文要求至少 CCF-B；会议等级、正式发表状态和会议/期刊版本需在纳入前核验




- 优先纳入有作者公开代码的论文；无代码时，必须同时满足研究质量、任务相关性和结构启发性明显更高，才可作为精读或相关工作条目，不自动进入复现队列




- 检索以 `research-lit` 的多源流程为总入口，结合 arXiv 获取最新预印本、Semantic Scholar 核验发表元数据与引用信息，并以 DOI/出版社页面确认最终版本；每篇纳入前记录数据集、任务、协议、代码状态与相对 DBConformer/DSAINet 的价值









**原因：**




当前论文主线已收敛到 MI-EEG 的结构创新与双分支/多域融合。固定时间、任务、创新




类型和来源质量门槛，可以避免文献池重新扩张为预训练、适配或低相关方法的混合清单，




并使后续精读、复现和 proposed 设计始终服务于 DBConformer/DSAINet 之上的可发表创新。









---









## D-029 将 LI-DSN 建成带来源账本的独立 MI 复现实验包









- 作者代码尚未公开，当前实现明确标记为基于 arXiv:2604.01889v1 的独立复现，不作为官方实现




- 第一阶段限定 BNCI2014001、BNCI2014004 及 CO/CV/LOSO，不扩展情绪识别和 SSVEP




- 论文明确值优先；未说明的 heads、卷积核、patch、FFN expansion、CWLP 归一化和 early-stopping 细节集中记录为推断值




- 使用项目自有训练协议执行 EA、训练集内 20% 分层验证、validation-loss early stopping，并在恢复最佳验证权重后一次性评估测试集




- 提供 full、去位置编码、late fusion、simple concat、去 cosine gate、去电极位置编码和去 adaptive fusion 七种入口




- 两数据集的数据/model check 已通过，BNCI2014001 CO/CV 和 BNCI2014004 LOSO 的单 seed、单被试、2 epochs smoke 已通过；这些结果只验证链路，不用于论文性能判断









**原因：**




LI-DSN 与 CBI 的问题定义直接重叠，仅靠文字精读不足以判断交互位置和信息形式的




差异。带显式来源账本的独立实现可以用于结构审查和后续公平对照，同时避免在作者




代码缺失时把本地补全参数误写成论文事实。









---









## D-030 SST-DPN 完成项目统一协议全量复现，并按数据路径分层解释









- MVCNet 的状态保持不变：BNCI2014001 与 BNCI2014004 三协议复现均已收口，但因 BNCI2014001 LOSO 与原文不对齐，仍只作为 related work / 次级参考




- SST-DPN 的代码、数据接口、训练日程和优化器检查已完成；参考仓库源码与本地 `mieeg` 环境未修改，正式运行通过项目 wrapper 管理




- BNCI2014004 在论文 Dataset II 日程和无参数重叠的 AdamW + Adam 配置下，项目统一预处理路径的 CO/CV/LOSO 已完成，ACC 分别为 `74.601%`、`75.555%`、`71.060%`




- BNCI2014004 reference `load_bcic("2b")` 的五 seed CO 已完成，ACC `84.961%`、Kappa `0.69923`，较论文 `86.650% / 0.73300` 低 `1.69 pp / 0.03377`；这是当前最可信的论文口径对齐证据




- reference-loader trial union 的五折 CV 已完成，ACC `85.254%`、Kappa `0.70508`，但属于本地扩展协议，不能与论文 session hold-out 主表直接比较




- BNCI2014001 在论文 Dataset I 日程下已完成 CO/CV 本地实验与 LOSO AutoDL 五路实验，ACC 分别为 `78.850%`、`86.902%`、`60.876%`；远程 LOSO 为 `45/45` 完整，Kappa `0.47834`




- AutoDL 运行使用的 wrapper hash 与本地当前版本一致；实际环境为 PyTorch `2.13.0`/CUDA `13.0`，与本地环境不同，故保留为远程统一协议结果而非跨环境的严格逐位复跑




- SST-DPN 当前定义为“项目统一协议全量完成、等待主结果表口径取舍”；不再把 BNCI2014001 LOSO 写成未启动或待补跑









**原因：**




本地产物已经覆盖两数据集、多协议和论文参考 loader，对 SST-DPN 继续使用“复现前




检查”或“尚未复现”的表述会低估实际进度。与此同时，不同数据路径和协议的结果




不能混为同一类证据；分层记录既能承认已完成工作，也能避免把本地扩展结果误写为




原文主表复现。









---









## D-031 四个近期模型按真实实验阶段分层记录









- LI-DSN / BNCI2014001 左右手二分类 LOSO 已完成 5 seeds x 9 subjects，共 45/45 任务；ACC `56.497%`，较论文 `77.86%` 低 `21.36 pp`




- LI-DSN 结果定义为“可运行的独立复现基线”，不能称为论文性能复现；BNCI2014004 目前仅有 check/smoke




- CFSPMNet / XW-Stroke 已完成 24 被试、单 seed、三路 LOSO 适配运行；ACC `64.375 +/- 11.886%`，较论文低 `3.855 pp`




- PA-TCNet / XW-Stroke 已完成 24 被试、单 seed、三路 LOSO 适配运行；ACC `64.583 +/- 11.961%`，较论文低约 `1.98 pp`




- CFSPMNet / PA-TCNet 均使用公开数据中的 29 个可用 EEG 通道，公开包缺失组件由本地补齐，且当前 runner 使用目标真实标签参与逐 epoch 模型选择；因此只记为适配复现和工程证据




- 2019-Stroke 的 63 通道顺序未核验，CFSPMNet / PA-TCNet 的第二数据集继续阻断，不使用猜测通道映射




- STGMFM / BNCI2014001 统一四分类 LOSO 只完成 check 与单 subject、2 epochs smoke；下一阶段是 3-subject pilot，未运行 45-job full









**原因：**




四个模型已经形成 full、smoke 和阻断状态并存的局面。按真实阶段分层可以保留已有




工程进度，同时避免把独立实现、迁移 smoke、目标标签参与模型选择的适配结果混写成




严格原文复现或统一主表证据。









---









## D-032 实验进度采用逐级记录与条件升级









- 最底层机器产物仍按唯一 `exp_id` 保存；人类可读记录以“模型 x 数据集 x 任务空间 x 协议”为单位，在同一文档中按时间追加 `started`、`check`、`smoke`、`pilot`、`full`、`diagnostic`、`ablation`、`interrupted` 或 `failed` 阶段




- 普通阶段结束时只强制核对机器产物并更新对应模型/协议记录，不再机械同步所有顶层文档




- `TASKS.md` 只在模型或数据集级里程碑完成、下一步任务改变，或启动此前未跟踪的全新模型实验时更新




- `PAPER.md` 只接收稳定 full、能支持或否定论文判断的诊断结果，以及模型在论文中的角色变化




- `DECISIONS.md` 只在 baseline 层级、协议口径、是否继续投入、论文结论或风险判断发生变化时更新




- 有保留价值的日志进入 `results/logs/local|remote/<exp_id>/`；可进入论文汇总时再整理 `results/tables/` 或 `results/figures/`




- check/smoke/pilot 只记录链路状态，不写成正式性能；中断、失败、部分 shard 完成和用户主动停止必须保留真实状态




- 启动一个此前未跟踪的全新模型实验时，即使尚未达到 check/smoke，也必须立即建立 `started` / `preflight` 底层记录，写明预期数据集、任务、协议、入口和当前阻断，并在 `TASKS.md` 留下一条模型级启动项









**原因：**




详细进度集中在底层协议记录，可以避免同一数值和状态在多个顶层文档重复维护；按




里程碑逐级上报又能保证论文控制面及时获得真正重要的变化。全新模型启动单独设为




强制记录点，可避免探索已经开始却在项目文档中完全不可见。









---









## D-033 SwanLab 纳入日常实验的统一辅助追踪流程









- SwanLab 固定写入 `workspace="oldlady"` 下的 `project="MI-EEG"`，用于远程观察、




  配置比较、低频标量曲线、subject/seed/fold 进度和并行 shard 聚合




- SwanLab 只作为旁路辅助层；`output/local|remote/<exp_id>/`、结果 CSV、summary、




  checkpoint、退出码和模型/协议实验记录继续作为可复现证据与正式判断真源




- `check` / `preflight` 默认禁用；`smoke`、`pilot`、`full`、`diagnostic` 和




  `ablation` 默认启用；无网环境使用 offline，临时排障可显式 disabled




- Codex 启动实际训练前应检查 runner 是否已通过公共 adapter 接入；未接入时先在




  wrapper 层补充最小旁路，不修改第三方参考训练循环或训练协议




- 配置、指标、单位和状态统一命名；Accuracy 使用 `_percent` 后缀，每 epoch 至多记录




  一次，默认不记录 batch 级指标，不上传原始 EEG、checkpoint、大型数组或凭证




- 普通实验使用 `name=<exp_id>`；并行 shard 使用独立 run 和共同




  `group=<logical_exp_id>`，生成的 run ID 与 `success` / `crashed` / `aborted` 状态写回




  `swanlab_status.json`




- SwanLab 未安装、未登录、网络或上传失败时必须降级为本地警告/no-op，不得改变




  seed、数据划分、优化器、训练结果或正式训练退出码




- 后续本地和远程实验依赖清单统一固定 `swanlab==0.9.0`；升级必须更新环境快照，




  offline 日志使用与生成时兼容的版本同步









**原因：**




MI-EEG 的多 subject、多 seed、LOSO 和并行 shard 实验持续时间长，远程可观察性和统一




索引能显著降低迟发现错误和人工巡检成本。把追踪限制在公共旁路适配器、低频标量和




非阻断失败边界内，可获得进度监控与对比收益，同时不让云端工具成为训练协议或实验




证据的依赖。









---









## D-034 STGMFM 采用 DSAINet 统一协议与 100 epoch 公平预算









- STGMFM 的正式迁移 baseline 采用 DSAINet 公开数据路径、CO/CV/LOSO 划分、训练集派生 Z-score、`validation-best`、无 EA、5 seeds × 9 subjects 和 100 epoch 预算；DBConformer 在该框架中是同协议横向对照模型，而非协议来源。




- 统一预算使用 DSAINet 的训练超参数：batch size `32`、Adam `lr=1e-3`、weight decay `1e-4`、无学习率调度；不迁移 DSAINet 专属的 classwise segment augmentation，STGMFM 保持 `0` 段。




- BNCI2014001 使用 released BCIC-IV-2a 的 22 通道初始图；BNCI2014004 的处理产物未提供可供生理图推断的已核验通道顺序，因此只使用通道顺序无关的 3 节点全连接初始化图，并将其标记为模型适配而非电极拓扑事实。




- 先前 1000 epoch LOSO pilot 与两次中断的本地 full 保留为链路/耗时证据，不进入正式结果表；所有新协议从 check 重新开始。









**原因：**









STGMFM 的原始训练日程与私有 23 通道、三分类数据设定绑定，45 个 1000-epoch LOSO 单元在本地的预测时长超过 10 小时阈值，也无法与现有 100-epoch DSAINet/DBConformer 横向结果区分“结构收益”和“训练预算收益”。以 DSAINet 为协议锚点可覆盖两个公开数据集和三种任务空间，并保留验证集选模与未使用 EA 的公平边界；空间图的跨数据集差异则必须明确记录，不能伪装成已验证的生理通道关系。









---









## D-035 XW-Stroke 跨被试对照采用 source-only validation 修正版 LOSO









- STGMFM 的 XW-Stroke 迁移使用 CFSPMNet / PA-TCNet 论文筛选的同一 24 被试队列；




  每折完整保留其余 23 名 source subjects，不因并行 shard 缩减源域池。




- held-out target 的真实标签不得参与 early stopping、checkpoint 选择或超参数选择；




  验证集从每名 source subject 内按类别分层抽取 20%，目标标签只用于最终一次测试。




- 统一训练上限为 200 epochs、patience 30；STGMFM 保持自身单阶段监督训练，




  不复制 SPPM、PGTC 等模型专用阶段。




- XW-Stroke 的 29 通道顺序已有 `channel_info.json` 证据，因此空间图使用标准




  10-20 坐标的 4-nearest-neighbor 对称图，不使用 dense graph，也不虚构原文




  30 通道口径。




- 当前 CFSPMNet / PA-TCNet 单 seed 结果因目标标签参与模型选择，只能作为适配与




  工程证据；若进入正式主表，须按本无泄漏边界重跑或明确降为补充结果。




- 2019-Stroke 在 63 通道顺序核验前继续 NO-GO，不通过 dense graph 绕过数据证据缺口。









**原因：**









现有 XW-Stroke 适配实验已经证明数据与模型链路可运行，但 target 标签参与模型选择会




高估跨被试泛化。将模型专用训练逻辑与共同评估边界分开，可以让 STGMFM、




CFSPMNet 和 PA-TCNet 在相同队列、相同 LOSO 单元和无泄漏模型选择下形成可解释对照；




已核验的电极顺序也足以为图模型建立公开、可审计的空间先验。









---









## D-036 proposed_v2 作为独立输入解耦路线，首版 pilot 后不直接进入 full









- `proposed_v2` 从原版 DBConformer 直接分叉，探索 BraSTORM 启发的输入级




  temporal waveform / spatial-spectral energy 解耦；它不继承 CfC、CBI、门控或




  proposed v1 的其他模块与超参数。




- BraSTORM 的论文事实与本地适配必须分开：论文使用四频带 DE、2D 电极网格、




  TCN/ViT、自监督对齐与重建；本地首版使用 8–32 Hz 范围内三频带 log-variance、




  channel tokens、原 DBConformer 双 Transformer 和纯监督原生协议。




- 频带标准化只能由当前折 post-EA source training trials 估计；held-out target 不得




  参与。首个 BNCI2014001 原生 LOSO pilot 的 9 个折均核对为




  `1,152 trials × 22 channels = 25,344` 个统计样本。




- seed 1、9 subjects、100 epochs 的 proposed_v2 pilot ACC 为 `74.074%`；相同




  seed、subject、epoch 的原版 DBConformer 为 `77.778%`，配对均值下降




  `3.704 pp`，3 胜、0 平、6 负。




- 当前判断分为两层：实现与统一协议链路为 `GO`；直接启动 5 seeds × 9 subjects




  full 为 `NO-GO`。下一步先做 token LayerNorm 单变量诊断，仍无正信号时再判断




  是否调整频带/时间粒度或暂停该方向。




- check、smoke、pilot 及本次配对只用于链路、稳定性与资源决策，不进入论文正式性能




  表；在 full 或更强诊断证据形成前不更新 `PAPER.md` 的核心结论。









**原因：**









该路线已经证明输入解耦可以在不修改原生 DBConformer 划分、EA、优化器和训练日程的




条件下稳定运行，而且参数量没有扩张；但同 seed 配对 pilot 已出现清晰负信号。此时




直接扩大到 45 个 full 单元会把计算预算投入一个尚未解决的结构问题。先用单变量诊断




检验 token 尺度稳定性，更符合“先收敛、后扩展”和可归因实验原则。









---









## D-037 proposed_v2 token LayerNorm 诊断否定，保留 no-LN 但继续阻断 full









- token LayerNorm 诊断只在 spatial-spectral channel token 投影后增加




  `LayerNorm(40)`；同 seed 下其余共同 state tensor 逐项一致，只新增 `80` 个




  gamma/beta 参数。




- seed 1、9 subjects、100 epochs 的 LayerNorm pilot ACC 为 `72.917%`，较 no-LN




  的 `74.074%` 下降 `1.157 pp`，3 胜、0 平、6 负。




- 相对同 seed 原版 DBConformer `77.778%`，LayerNorm 下降 `4.861 pp`，仅 subject 7




  提高，其他 8 个 subjects 均下降。




- token LayerNorm 标记为 `REJECT`；当前 proposed_v2 仍以 no-LN 为较优首版，但




  no-LN 相对 baseline 的 `-3.704 pp` 负信号没有改变。




- 5-seed full 继续 `NO-GO`。若继续探索，应转向频带或时间粒度的单变量机制诊断，




  不再投入 LayerNorm、CfC、门控或额外损失的组合堆叠。




- 本轮 check/smoke/pilot 只支持结构筛选与资源决策，不进入 `PAPER.md` 正式性能表。









**原因：**









LayerNorm 对困难 subject 1 有改善，但对大多数 subjects 的损害更大，说明首版问题




不是简单的 token 尺度不稳定。继续扩大 seed 或叠加模块不能解决当前可归因的负信号；




先拒绝该变量并维持 full 门槛，能避免用计算预算掩盖结构方向尚未收敛的问题。









---









## D-038 proposed_v2 转为空间对比频谱残差，并进入第二数据集验证









- relative log-power 的 source/target 表示漂移较 absolute log-variance 增加 `17.1%`，




  因此未投入训练；沿 channel 维构造的 spatial-contrast 特征被选为下一单变量。




- 仅用 spatial-contrast token 替换原空间 stem 的 seed 1 pilot 为 `75.154%`，较




  absolute replacement 提高 `1.080 pp`，但仍较原版 DBConformer 低 `2.623 pp`。




- 因此不再坚持“频谱输入完全替换空间输入”，改为保留原版 `PatchEmbeddingSpatial`，




  以 `z_raw + alpha * z_spectral_contrast` 做小尺度残差增强；`alpha` 初始化为 `0.1`。




- 该残差版只新增 `745` 个参数；同 seed 下，baseline 已有模块的初始权重逐项一致，




  且 raw spatial 与 spectral residual 均通过梯度检查。




- BNCI2014001 原生 LOSO 5-seed full 完成 45/45 单元，ACC 为




  `77.08333 +/- 1.67990%`；同协议原版 DBConformer 为




  `76.29630 +/- 0.99701%`，提高 `0.78704 pp`。




- 5 个 seed mean 差值为




  `[+0.69444, +2.62346, -1.77469, +1.69753, +0.69444] pp`；




  4/5 seeds 为正。9 个 subject mean 为 7 胜、1 平、1 负。




- 45 个 seed-subject 单元为 19 胜、4 平、22 负；正均值来自正差值幅度，而不是




  逐单元多数获胜，因此不能将“4/5 seeds、7/9 subject means 为正”扩写为全面稳定提升。




- 统计边界：subject-mean 配对的探索性双侧 Wilcoxon `p=0.03125`，但 seed-mean




  Wilcoxon `p=0.43750`；前者说明增益覆盖面较广，后者不支持把小幅均值提升表述为




  已证明的随机种子稳定优势。




- 45 个 checkpoint 的 `alpha` 全部为正，均值 `0.10062`，范围




  `0.00014–0.39255`；模型未统一关闭残差，但使用强度具有明显 seed/subject 差异。




- 决策：该结构标记为 proposed_v2 当前主候选，BNCI2014001 full 为 `GO`；停止在同一




  数据集上继续调 LayerNorm、频带和 `alpha`，下一步按固定配置进入 BNCI2014004 原生




  LOSO 的无调参验证。




- 新增独立主候选配置




  `experiments/configs/proposed_v2/residual_contrast_dbconformer_bnci2014001_native_local.yaml`；




  不覆盖首版 absolute replacement 配置，以保留消融复现边界。




- 只有第二数据集也形成稳定正向趋势后，才将其升级为论文主创新结论；当前在




  `PAPER.md` 中只记录为“单数据集 full 正信号、跨数据集待验证”。









**原因：**









首版失败的主要问题不是频谱特征本身完全无效，而是用低维频谱能量 token 取代了原始




空间卷积表征。残差结构保留 baseline 信息通路后，频谱视图从“替代表示”变为“增量先验”，




在不改变数据划分、EA、训练日程或模型选择规则的前提下形成了首个 5-seed 正信号。由于




效应仅 `0.787 pp` 且 seed-level 检验不显著，立即进行第二数据集固定配置验证比继续在




BNCI2014001 上后验搜索更能检验机制可迁移性。









---









## D-039 proposed_v2 固定配置在 BNCI2014004 未复现正向趋势，停止该机制调参









- 使用与 BNCI2014001 完全固定的三频带、spatial-contrast、`alpha=0.1` 初值、无




  LayerNorm、原生 LOSO/EA、100 epochs 和 final-epoch 规则，在 BNCI2014004 3-channel




  数据上完成 check、smoke、seed 1 pilot 和 5 seeds × 9 subjects full。




- 45/45 pairs、45/45 checkpoint 和全部 post-EA source-only 统计均完整；每折计数为




  `960 source trials × 3 channels = 2,880`，SwanLab 六个 run 均 `success`。




- proposed_v2 为 `69.64815 +/- 0.62908%`，同协议 DBConformer 为




  `69.77778 +/- 0.85787%`，差值 `-0.12963 pp`。




- seed mean 差值为 `[+1.48148, +1.38889, -2.22222, -0.64815, -0.64815] pp`；




  2/5 为正。subject mean 为 4 胜、5 负，45 个单元为 19 胜、4 平、22 负。




- subject-mean Wilcoxon `p=0.97656`、seed-mean Wilcoxon `p=1.00000`；没有任何




  统计证据支持该低通道场景下的收益。




- `alpha` 仍全部为正（均值 `0.47250`），不能解释为模型把频谱残差简单关闭；更稳妥的




  解释是该固定空间对比频谱先验在 3-channel 场景中没有提供可迁移的附加信息。




- 补充协议边界：BNCI2014004 的 CO 为 `75.000%`、与 baseline 持平，CV 为 `73.537%`、




  `+0.352 pp`；BNCI2014001 的 CO seed-1 pilot 为 `-2.778 pp` 并停止扩大，CV 5-seed




  full 为 `82.864%`、较 baseline `-0.461 pp`。CV 的 seed-1 `+1.382 pp` 未在 full 复现。




- 决策：proposed_v2 从“当前主候选”降级为“BNCI2014001 单数据集探索证据”；不进入论文




  主性能结论，不再对频带、残差尺度、LayerNorm 或投影维度做后验搜索，也停止该冻结结构的




  性能扩跑。









**原因：**









BNCI2014001 的 `+0.787 pp` 本来就小且 seed-level 不显著。固定迁移到低通道




BNCI2014004 后，结果与 baseline 基本持平而略低，直接否定了“该机制具有跨数据集稳定




优势”的表述。保留正负两侧结果比继续微调更有价值；若继续创新探索，应引入一个新的、可




独立归因的机制，而不是为单一数据集或通道数回调现有残差。









---









## D-040 proposed_v2.2 动态窗残差形成可行信号，但不足以升级主性能结论









- 为拆解初版动态拓扑双路的 `-7.176 pp` 退化，先在固定 `proposed_v2` spatial-contrast residual 主干中仅将整段频谱改为 250-sample window / 125-sample hop 的 7-window 表示；保留 raw spatial stem、残差融合、训练日程与 source-only 边界。




- BNCI2014001 原生 LOSO 5-seed full 完成 `45/45` 单元、45 个 checkpoint 和完整本地/SwanLab 产物。动态窗 residual 为 `77.238 ± 1.599%`，DBConformer 为 `76.296 ± 0.997%`，平均差 `+0.941 pp`；五个 seed mean 的双侧 exact Wilcoxon `p=0.1875`。




- 相对固定 static spectral residual（`77.083 ± 1.680%`）仅 `+0.154 pp`，五 seed Wilcoxon `p=0.6250`。因此该结果支持“动态时间分段没有破坏 residual 路径、可作为输入因素”的可行性，不支持“已证明稳定性能增益”。




- 在动态窗 parent 上增加 22 个真实电极节点的 mask-aware 8-neighbor topology residual 后，seed-1 pilot `78.781%`，较动态窗 parent `-0.309 pp`；该拓扑实现避免了空网格零填充卷积造成的显著退化，但未提供独立增益，标记为 `REJECT`。




- 决策：`proposed_v2.2-DW-residual` 保留为 BNCI2014001 单数据集的可复现探索证据；不做窗口、hop、残差尺度或邻域的后验搜索，不直接触发跨数据集性能扩跑，也不升级为论文主创新。若未来重新检验其泛化，必须在预先冻结的配置、独立数据集和明确的 source-only 选择规则下进行。









---









## D-041 proposed_v2.3 保留时间动态弱信号，否定当前 Pearson 通道关系视图









- `proposed_v2.3` 从原版 DBConformer 直接分叉，不再使用空间–频谱联合视图；只借鉴 BraSTORM 将分支边界前移到输入阶段的思想，并按 DBConformer 原 temporal / spatial 语义构造时间动态视图与通道关系视图。




- BNCI2014001 原生 LOSO seed-1 pilot 中，集成版为 `77.778%`，与同 seed DBConformer 完全持平；逐被试为 3 正 / 6 负，不能视为正向性能信号。




- 预注册归因消融显示：只替换时间输入时为 `78.549%`（`+0.772 pp`），只替换空间输入为 trial-wise 零对角 Pearson 通道关系时为 `76.389%`（`-1.389 pp`）。模型参数量分别与 baseline 相同或仅少 48，差异不由容量增长解释。




- 决策：当前 Pearson 通道关系视图标记为 `REJECT`，集成 v2.3 不进入 5-seed full，不进行相关矩阵权重、对角线或投影宽度的后验搜索。时间动态视图仅保留为单 seed 弱正锚点，尚不是论文证据。




- 若继续该方向，固定时间动态视图和训练协议，只单变量重构更具时间局部性的通道关系 token；不得同时重新加入频谱、电极拓扑、门控或额外损失。









### 初始化控制与 EA-residual covariance 复验（2026-07-28）









- 初始化控制采用“同一 entry RNG state 构造 DBConformer → 显式复制所有结构共享参数”的方式。temporal-only 复制 temporal stem、原 spatial stem、位置编码、两组 Transformer、分类头与空间池化；relation-only 仅将关系投影保留为独立参数。




- temporal-only 的 `78.549%` 与先前逐被试结果完全相同，确认其 `+0.772 pp` 弱信号不来自初始化差异。Pearson relation-only 在控制后为 `77.315%`（`-0.463 pp`），仍是负向。




- 触发的独立 EA-residual covariance 替换以 native EA 后每个 trial 的 `Cov(X_EA) - I` 作为关系输入，保留对角方差残差，不增加额外拟合统计；其 seed-1 pilot 为 `76.698%`（`-1.080 pp`），低于 baseline 与 Pearson relation-only。




- 决策收束：v2.3 的“用 trial-level 通道关系矩阵完全替换原 spatial waveform 输入”子方向标记为 `REJECT`，不再做 Pearson、EA residual covariance、对角线、尺度或投影宽度后验调参，也不进入 5-seed full。时间动态视图只能保留为孤立的单 seed 弱正观测，不能作为双视图结构或论文主张。




- 在 source-only token 诊断后，唯一最小修复固定保留原 `PatchEmbeddingSpatial`，并以 `z_raw + 0.1*z_Pearson` 加入关系残差；其 shared-init seed-1 原生 LOSO pilot 为 `75.694%`，较 baseline `-2.083 pp`（3 正 / 6 负，exact Wilcoxon `p=0.0977`）。因此“静态 trial-level Pearson 关系作为原空间 token 的有界残差”也标记为 `REJECT`；不做同容量对照、尺度扫描或 5-seed full。该负结果支持当前数据下 relation view 本身而非仅完全替换方式是主要风险。




- 零视图融合诊断直接启用原 DBConformer 的 sigmoid gate，保持两条 raw waveform 输入、两 stem、位置编码和两组 Transformer 与 concat baseline 一致；其 seed-1 原生 LOSO 为 `76.235%`，较 baseline `-1.543 pp`（2 正 / 7 负，exact Wilcoxon `p=0.0742`）。因此简单 gate 也不是当前性能瓶颈的解法，`REJECT`；不继续试 cross-attention 或把该负结果解释成容量问题（gate 总参数反而少 `1,001`）。




- temporal-only 的冻结 5-seed 原生 LOSO 验证完成：`76.481 ± 1.366%`，baseline `76.296 ± 0.997%`，平均差仅 `+0.185 pp`；3/5 seed 正向，五个 seed mean 的 paired exact Wilcoxon `p=0.8125`。因此先前 seed-1 `+0.772 pp` 不能升级为确认效应，不调 `difference_weight`，也不将 temporal dynamics 作为论文性能主张。




- v2.3 收束：静态 relation replacement、relation residual、零视图简单 gate 与 temporal-dynamics 单变量均未形成稳定增益；不再扩展分段 relation token 或更多手工输入视图。后续若要推进交互机制，应另立、可归因地评估已有文献支持的复杂交互路线（如 LI-DSN 的分层 TSIA 或 STGMFM 的图-频率三分支），不得把它们与已否定的 v2.3 输入视图堆叠。









## D-042 固定 `mieeg-uep-v1.0` 为存量结果优先的公开 MI-EEG 共同评估合同









- 正式协议文件为 `experiments/UNIFIED_EVALUATION_PROTOCOL.md`。它固定




  BNCI2014001/BNCI2014004 的 DSAINet 官方风格 processed arrays、0.5–40 Hz / 250 Hz /




  `[0,4)` s 输入、EA 禁用、session-based CO、seed-dependent stratified 5-fold CV、




  LOSO、source-only 内层验证边界、禁止 test-best、指标、汇总与 subject-level 统计单位。




- 协议采用“共同评估合同 + training profile”两层结构：`tp-dsainet100-v1` 保留




  DBConformer/DSAINet 的 100-epoch Adam、train-only Z-score 和既有模型选择；




  `tp-sstdpn-native-v1` 保留 SST-DPN 的两阶段 AdamW+Adam 与 validation-loss 选择。




  前者之间可以作架构级严格配对；后者与前者只作相同评估合同下的模型管线比较。




- 为最大吸收存量结果，DBConformer、DSAINet 与 SST-DPN 的零重跑共同 paired seeds 固定为




  `[1,2,3,4]`；CO/LOSO 各为 36 个 subject-seed 单元，CV 为 180 个 fold 单元及 36 个




  汇总单元。各模型各自已有 5-seed 结果仍保留作稳定性描述。若最终主表必须五个公共




  seeds，只补最终入表的 DSAINet-100 profile 模型 seed 5，不重跑已有 seeds。




- ACC 与 Kappa 可直接进入共同结果表。F1 必须标明 Macro/Weighted；跨模型 F1 只在从同一




  checkpoint 对固定测试索引离线重算后进入共同列。该只读推理不改变模型选择或训练结果。




- 每次运行与汇总均强制记录 `protocol_id`、`training_profile`、`compatibility_label`；




  对数据、outer split、EA、测试边界、指标定义、CV 聚合或统计单位的改变必须创建新的




  protocol ID，不能原地修改 `mieeg-uep-v1.0`。









**原因：**









DBConformer、DSAINet 与 SST-DPN 已共享同一 processed data 路径和外层 CO/CV/LOSO




评估结构，但其内层验证、标准化与训练日程并不相同。强行统一全部训练设置会将完整的




SST-DPN 及部分已完成 baseline 结果排除在外；反之不区分训练 profile 又会把 pipeline




比较误写为架构消融。两层协议既保留严格配对的 DBConformer/DSAINet 证据，也保留




SST-DPN 作为非 Transformer 管线基线的可解释位置。









---









## D-043 SMANet Sinc 随机截止频率不作为统一 LOSO 性能改进继续扩展









- 在冻结的 SMANet unified 100-epoch、source-only LOSO 协议下，`paper_uniform_cutoffs` 与固定 2-Hz 带宽 reference 完成 BNCI2014001/BNCI2014004 各 `5 seeds × 9 subjects` 的严格配对 full。




- Sinc 变体的 ACC 分别为 `56.169%` 与 `70.248%`，相对 reference 的均值仅 `+0.378 pp` 与 `+0.106 pp`；按每名 subject 的五个 paired seeds 求均值后，双侧 Wilcoxon 分别为 `p=0.30078` 与 `p=0.65234`。




- 决策：保留固定 2-Hz Sinc 初始化作为 SMANet 主 baseline；`paper_uniform_cutoffs` 保留为已完成、数值合理的 paper-aligned reconstruction 变体，但不作为性能提升主张，不再扫描 cutoff 范围、带宽、初始化 seed 或与 CenterLoss 补偿组合。




- CenterLoss 梯度补偿仍只具有小规模独立 pilot 证据，未因本决策获得 full 扩展授权。









**原因：**









两个公开数据集的完整配对结果都只有极小的正均值差，且 subject-level 检验不支持稳定获益。继续后验调整 Sinc 初始化会把计算预算投入到未形成可归因、可迁移信号的分支；应保持 reference baseline 稳定，并将 CenterLoss 作为独立的未决诊断，而非与 Sinc 叠加调参。









---









## D-044 [REDACTED_MACHINE] 采用证据约束的自主 Bundle 调度









- 当用户已明确模型、数据/任务 scope 与目标 full 时，Codex 默认自主准备并冻结 Bundle，完成 `preflight -> check -> pilot -> full`、回流与验证；用户不再负责选择每卡 lane 数或在普通并发候选失败后逐步批准。




- 调度算法升级并冻结为 `ccmu-lane-autopilot-v2`：新 profile 依次检查 1 lane、冻结上探 lane 与必要的二分回退；最多 3 个 pilot Run；以稳定候选的实测聚合吞吐选择 lane，最高值 3% 内优先较低 lane。OOM、吞吐回落、停滞和单次候选失败自动回退，不能被写作实验失败或性能证据。




- 每个自主 Bundle 必须冻结 `remote_execution_plan.json` 和公共调度合同；pilot 输出带 lane/GPU 实测映射的 `scheduler_metrics.json`，控制器输出 `scheduler_report.json`，本地输出与报告哈希绑定的 `scheduling_decision.json`。profile 指纹同时绑定全部冻结调度参数；远端控制器会重新校验决策与所请求 lane，只有决策为 `submit_full` 且二者匹配时才自动提交 full。




- 历史 lane 仅在 source/协议/数据/task-shape/环境/硬件/模板版本精确匹配、已有稳定完成 pilot 且证据不超过 30 天时复用；仍须做一次并发确认 pilot。协议、环境或研究 `NO-GO` 冲突，以及基线 lane 无法稳定运行时必须暂停确认。









**原因：**









服务器的两张 GPU 应由同模型的可核验调度证据驱动，而不是固定的保守 lane 或人为反复选择；




同时，资源调度自动化不得绕过实验协议、环境隔离、研究结论门禁或结果审计。









---









## D-045 关闭 proposed_v2 手工输入视图家族，并以机制中立的新周期返回 S1









- `proposed_v2-A1` 已补测真正的动态频谱窗序列：保留 raw spatial stem，以可学习窗注意力




  聚合 7 个窗口，禁止 fixed mean；BNCI2014001 原生 LOSO seed-1 pilot 为 `73.765%`，




  较同 seed DBConformer `-4.012 pp`，较 static residual `-4.707 pp`。




- A1 的 temporal mask contribution 为 `+24.69 pp`，spatial mask contribution 仅




  `+0.077 pp`；`alpha=0` 与原预测 9/9 完全相同。它补上了先前动态窗被均值抹平的设计




  缺口，但仍未证明频谱分支提供因果贡献。




- 预注册的 `+1.5 pp` pilot 门槛失败，A1 不进入 5-seed full，也不搜索窗口、hop、频带、




  LayerNorm、残差尺度、注意力形式或辅助损失。




- 停止范围是“在 DBConformer 上用低维手工频谱/关系视图进行 replacement、弱 residual 或




  序列聚合的 proposed_v2 家族”，不是“所有输入解耦思想”或“改进 DBConformer”这一上层




  研究问题。









**原因：**









replacement、static/dynamic residual、关系视图、简单 gate、辅助监督和真正动态频谱序列已经




覆盖了该手工输入视图家族的主要可解释变体。继续在频带、窗口或损失上后验搜索会削弱归因，




且无法解决离线诊断和 A1 一致暴露的弱空间视图问题。保留负向证据并返回机制选择阶段，比把




新交互或图模块堆叠到已否定的 v2 输入上更符合当前证据边界。









---









## D-046 关闭 R2-A BraSTORM-mechanism adaptation 的冻结合同









- R2-A P1 remote pilot 在 BNCI2014001 native LOSO/EA、`mieeg-uep-v1.0`、两个冻结公共 seed 和每折 source-only 20 epochs composite pretraining 下完成 `18/18` outer-fold tasks 与 `36/36` pretrained/scratch 配对行；归档 SHA-256、共同初始化、source-only manifest、discarded decoder 与 fixed-final target-once 边界均已核验。




- composite pretrained 相对同构 scratch 在 seed 1、2 分别为 `+0.849 pp`、`+1.389 pp`，因此仅保留“预训练对该较弱 R2-A 架构的窄范围两-seed 信号”这一事实。




- 但冻结 P1 同时要求 R2-A pretrained 不低于 verified same-profile DBConformer anchor，并且不出现新的双位数 subject-level collapse。实际相对 anchor 分别为 `-7.253 pp`、`-5.864 pp`，存在 6 个不低于 10 pp 的回落（最差 `-15.972 pp`）；两项停止条件均失败。




- 决策：冻结 R2-A 设为 `NO-GO`。不以增减 pretraining epoch、频带、topology、mask、loss weight、temperature、encoder width、fusion 或 fine-tuning schedule 进行挽救；不进入 A1、five-seed full、第二数据集或任何论文/机制主张。保留代码、Bundle 与完整负向证据，只可在一个重新定义并获授权的新机制周期中复用。









**原因：** P1 的相对 scratch 正向差异不足以抵消对已验证主 baseline 的一致大幅退化，且受试者级稳定性条件明确失败；继续同合同扩展会破坏预声明归因和停止规则。









---









## D-047 冻结 IP1 半球共同—侧化可逆分解为输入并行方向的首选合同









- IP1 以固定左右反射算子 `P` 将同一 trial 分解为 `x_common=(x+P(x))/2` 与




  `x_lateral=(x-P(x))/2`，并保持 `x=x_common+x_lateral`；中线通道仅进入 common，




  左右成对通道在 lateral 中保留方向符号。




- 第一作用域固定为 BNCI2014001 左/右手 MI 的 DBConformer native LOSO/EA fixed-final




  边界。两路使用同构、独立参数和相同初始化的容量受控 encoder，仅以归一化拼接和单一




  分类头融合；首屏不加入 mirror/contrastive loss、gate、cross-attention、pretraining、




  spectral branch 或新骨干。




- 机制归因必须包含 duplicated-raw、固定随机非镜像配对、固定随机正交分解、branch-only




  与 branch-mask 对照。半球差异、通道镜像、双分支和差分均不是新颖性声明；IP1 只按




  supporting component 定位。




- 冻结停止规则：D0 构造/probe 门失败即关闭；P1 仅在 D0、check、smoke 通过后运行




  `2 seeds × 9 targets`，须两个 seed 平均差均为正、合并至少 `+0.5 pp` 且无新增双位数




  subject collapse。失败后不以宽度、融合、损失、预训练、频带或配对搜索救援。




- 本决策只冻结 Idea Contract v1，并把周期推进到 S3 direction challenge；不授权 D0、实现、




  check、smoke、pilot 或 full。完整合同与状态以




  `experiments/records/2026-08-09_dbconformer_input_parallel_reframing/research_cycle.md` 为准。









**原因：**









旧 proposed_v2/v2.2/v2.3 与 R2-A 的主要失败来自有损输入替换、辅助分支缺少因果贡献或弱架构




即使预训练也显著落后 baseline。IP1 保留完整 raw input，并能用配对破坏和等容量反事实区分




“生理语义分解”与“仅增加双分支容量”，是当前最小且可证伪的重构方向。









---









### D-048：IP1 输入级 common/lateral 分解以对称兼容坐标系重构为 v2；v1 停止（2026-08-09）









**背景**：IP1 v1 的半球 common/lateral 分解虽然代数可逆，但 BNCI2014001 的原始 22 通道以左乳突为参考，且 DBConformer native runner 使用不受反射算子约束的全通道 EA。一般情形下 EA 白化矩阵不与左右反射 `P` 对易，故不能把 native-EA 输出上的分量解释为原电极空间的 symmetric/antisymmetric 证据。









**决定**：用户接受修复并正式 supersede v1。IP1 v2 固定为：先 CAR `H=I-11^T/C`，再以 `R_sym=(R+PRP^T)/2` 的中心子空间谱伪逆平方根 `R_sym^{+,-1/2}` 做 subject-wise、无标签 symmetry-preserving EA，最后做 `z_common=(z+Pz)/2` 与 `z_lateral=(z-Pz)/2`。CAR 使全空间降秩，故不使用不存在的普通逆平方根；信息保持只针对 CAR 后对齐坐标 `z`，不宣称无损恢复原始左乳突参考坐标。性能主比较改为同 CAR+symmetry-preserving-EA 的单路 DBConformer；native DBConformer 仅保留为外部历史性能锚点。









**边界与门槛**：IP1 仍只是 supporting component，不宣称半球差异、镜像或双分支本身的新颖性。D0 必须先验证 `P^2=I`、`HP=PH`、`WP≈PW` 和重构误差，再做 source-only probe；P1 必须相对同预处理单路基线满足双 seed 正向且合并 `>=+0.5 pp`。随机配对/正交分解、duplicated-raw、branch necessity 为后续 A1 的强制对照。BNCI2014004 仅作后续 bipolar stress test。









**当前状态**：v2 仅完成合同和 in-session direction review，`go` 只到 S4 计划阶段；未授权 D0、实现、check、smoke、pilot、full 或任何性能声明。









### D-049：冻结 IP1 v2 的对称 EA LOSO 实验协议与运行梯度（2026-08-09）









**协议**：新增 `ip1-sym-ea-loso-v1` 与 `tp-ip1-dbconformer-loso-symea-v1`。它固定 BNCI2014001 session T、左右手二分类、9-subject LOSO、100 epoch fixed-final、Adam `lr=1e-3`、batch size `32`、无 augmentation、source-per-subject 对称 EA 与 target causal（仅截至当前 trial）无标签对齐。EA 改变使其不能写为 `mieeg-uep-v1.0`；`exact-paired` 只指该新 profile 内的 arm 比较。









**比较与顺序**：主比较为 IP1 v2 对同 CAR+symmetry-preserving-EA 单路 DBConformer。D0 无训练；check 与 1×1×2-epoch smoke 仅链路；P1 是两 seed × 九 target 的两 arm 固定终点比较；只有 P1 通过才运行 duplicated-raw、random involution、random orthogonal 和 branch-necessity A1。native DBConformer 只作历史外锚。









**数值边界**：CAR 使全空间协方差降秩，EA 冻结为中心子空间的谱伪逆平方根，阈值 `1e-10*lambda_max`；分解可逆性仅对 CAR 后 aligned input `z` 声明。参数匹配从预声明网格按最小参数差、字典序 tie-break 选择；若最小差超过 `5%`，返回合同修订而非扩网格。









**当前状态**：计划完成，但未授权 S5 实现以及任何运行。









### D-050：IP1 v2 参数匹配网格按 DBConformer 10-head 整除约束收紧（2026-08-10）









**发现与决定**：参考 DBConformer 的 attention 实现固定 `num_heads=10`，所以并行 encoder 的 `emb_size` 必须为 10 的倍数。原计划 `{20,22,24,26,28}` 含不可执行宽度，现不看数据、不运行模型地收紧为 `{10,20,30,40}`；`spa_dim={8,10,12}`、最小参数差及字典序 tie-break、5% 上限均不变。









**边界**：该变更仅修正框架整除约束，不构成以指标为依据的超参数搜索、容量救援或科学合同变更。S5 只授权实现，D0/check/smoke/pilot/full 尚未执行。









### D-051：接受 IP1 v2 的精确容量匹配修订（2026-08-10）









**决定**：用户接受将两路独立同构 encoder 固定为各自 `temporal/channel depth=1/1`、`emb_size=40`、`spa_dim=12`。该结构共 93,748 个可训练参数，对同 profile 单路 DBConformer 的 93,747 个参数差 `0.0011%`；它替代此前不可满足 5% 上限的 depth `2/2` 双路网格。









**边界**：修订依据仅为无数据构造级参数计数，不使用任何 target、source 指标或训练结果；两路仍独立更新、初值数值相同。runner 将拒绝其他候选，D0 前不得再改变该容量配置。









### D-052：IP1 v2 对称 EA 的 source-only D0 probe 失败，关闭该冻结合同（2026-08-10）









**结果**：在冻结 `ip1-sym-ea-loso-v1` 上，9 个 BNCI2014001 LOSO target 的 D0 完整成功结束。构造审计通过：`P²=I`、`HP=PH`、最大归一化 `WP-PW=1.08e-13`、source aligned `z` 的最大相对重构误差 `5.99e-08`，每个 transform 的有效秩均为 `21`。但预注册 source-only lateral `log(var)` probe 平均仅 `52.701%`，较固定随机 involution 为 `-6.481 pp`，仅 `2/9` target 不劣；未达到 `55%`、`+2.0 pp`、`6/9` 的三项 D0 门。









**决定**：这不是映射或数值实现错误，且不触发唯一允许的确定性数值修复。关闭 IP1 v2 的 check、smoke、[REDACTED_MACHINE] pilot、A1、full 与所有后验配对/probe/网络/损失/频段调参。保留 `src/training/ip1_sym_ea.py`、并行 wrapper、冻结 config 以及完整 D0 负证据；该 no-go 只适用于此 symmetry-preserving common/lateral 因子化合同，不否定输入级解耦和并行编码器这一上位研究问题。









**证据**：`output/local/2026-08-10_ip1_sym_ea_bnci2014001_loso_d0_r2/d0_report.json`、`d0_targets.csv`、`run_metadata.json`、`swanlab_status.json`，以及 `experiments/records/2026-08-09_dbconformer_input_parallel_reframing/`。









### D-053：开启 source-only task-aligned complementary factorization 的独立研究周期（2026-08-10）









**决定**：在 IP1 v2 的固定镜像分解 D0 no-go 后，用户明确进入下一周期。新周期不把 IP1 作为可调参父模型，而只保留“输入级解耦 + 并行编码器”的上位问题。候选机制暂定为仅用 LOSO source training data 学习判别子空间投影 `P_D`，并以 `P_Dx` 与 `(I-P_D)x` 形成可重构的互补输入；投影准则、秩、数据表示、协议和网络均未冻结。









**边界**：先完成 CSP/FBCSP、监督降维、Riemannian spatial filtering 与既有多分支 MI decoder 的近邻工作审查；若该组合已被等价覆盖，则不以改名继续。不得引入 target 标签/指标选择、mirror pairing、频谱分支、pretraining、额外损失、cross-attention 或任何 IP1 后验救援。当前无实现、check、smoke、pilot、full 或性能授权。









**记录**：`experiments/records/2026-08-10_dbconformer_task_aligned_factorization/research_cycle.md`。









### D-054：SCF v2 与 multi-subject/transfer/stationary CSP 高碰撞，实施前关闭（2026-08-10）









**结果**：用户冻结后完成 SCF v2 的 in-session 查新、反证和研究审查。`Multi-subject learning for CSP` 已学习 global 与 subject-specific spatial filters；subject-transfer CSP 已用跨被试差异正则化空间滤波；`Divergence Framework` 已联合优化判别性和稳定性子空间；CSP-Net、POC-CSP 已将固定/可学习且正交约束的 CSP 融入神经网络。共享/私有双分支也已有直接相邻实现。SCF 的 `C` 对 `V` 目标、互补残差与双 encoder 组合不足以形成可防守的机制差异。









**决定**：在任何实现、数据访问或 D0 前关闭 SCF v2。禁止通过更换 generalized-eigen 目标、rank 阈值、whitening、residual fusion、encoder 容量或 source-consistency regularizer 对该合同救援；不运行 check、smoke、pilot 或 full。保留路线和查新记录；本 no-go 仅关闭“source-consensus spatial factorization + complementary residual + parallel encoder”的重参数化家族，不否定输入级解耦/并行编码这一上位研究问题。









**证据**：`experiments/records/2026-08-10_dbconformer_task_aligned_factorization/research_cycle.md` 的 S3 段，以及 Devlaminck et al. (2011)、Kumar et al. (2019)、Jiang et al. (2024)、Partovi et al. (2025) 的近邻工作链接。









### D-055：回到上位方向 S1，开启非空间投影型输入解耦周期（2026-08-10）









**决定**：用户明确要求回到 S1，继续在“输入级解耦 + 并行编码器”上位方向下提出创新问题。新周期 `2026-08-10_dbconformer_nonspatial_input_factorization` 不继承 IP1 的左右镜像算子，也不把 SCF 的空间子空间投影作为可调父模型；旧结果仅作为边界证据。









**S1 结论**：定向检索排除了普通 temporal/spectral 双流、预测信号/innovation residual、Hilbert amplitude/phase、slow/fast 与 normalization-only 路线。当前推荐 `R1 ODF`：把每个通道的试次精确表示为保留原时间索引的幅值秩轨迹与按分位轴排序的幅值曲线，两路联合可逆、无需标签或学习型预处理；`R2 RCT` 的稳健核心/尾部残差作为更易实现但归因较弱的备选。









**边界**：该结论仅通过 candidate-readiness，尚未冻结候选，也未完成 S2 idea contract 或 S3 查新反证。当前无实现、数据访问、D0、check、smoke、pilot、full 或性能授权；本地 `verify_papers.py` 不可用，文献元数据虽经 arXiv/PubMed/DOI/会议主页核对，仍不得把 S1 差异信号写成正式查新结论。









**记录**：`experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/research_cycle.md`。




### D-056：ODF-v1 完成 S2 最小结构收敛，等待合同冻结（2026-08-10）




**决定**：用户选择 `R1 ODF` 进入 S2。经 DBConformer 架构核对，候选不再使用两套完整 encoder，而是保持原模型 temporal / spatial-channel 两路 stem、Transformer、池化、拼接和分类头不变，只把时间索引上的归一化幅值秩轨迹 `O(x)` 送入 temporal stream，把保留原幅值尺度的排序分位曲线 `Q(x)` 送入 spatial/channel stream。该接法无新增可训练参数，可与原始 raw/raw DBConformer 进行 exact-capacity 配对。









**归因边界**：`O/Q` 输入对在编码前可由稳定排序索引精确重构原试次，但不声明独立、正交、统计解耦或模型内部可重构。全局秩轨迹会移除绝对 ERD/ERS 幅值，分位曲线会移除原时间/频谱组织，联合可逆不保证晚期融合可利用跨视图对应关系；这是必须由 source-only D0、`O/raw`、`raw/Q` 与交换映射 `Q/O` 反证的核心风险。









**门禁**：S2 合同状态为 `proposed_v1_ready_for_freeze`，当前等待用户确认冻结。冻结前不进入 S3；当前仍无实现、数据访问、D0、check、smoke、pilot、full 或性能授权，也不得通过复制 encoder、局部秩、归一化、辅助损失、gate/cross-attention 或与 R2/IP1/SCF 组合进行后验救援。









**记录**：`experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/research_cycle.md`。




### D-057：用户冻结 ODF-v1，进入 S3 方向挑战（2026-08-10）




**决定**：用户确认冻结 S2 的 `ODF-v1` 精确合同，包括 `O(x) -> temporal stream`、`Q(x) -> spatial/channel stream`、baseline 同参数结构、`B0/P1/A1/A2/A3` 归因对照及全部反事实边界。后续 S3 只审查该冻结对象；如需改变输入定义、分支映射、融合或声明范围，必须将本合同标记为 superseded 并返回相应阶段。









**证据与授权**：冻结只形成稳定审查对象，不提高现有 `literature_grounded` 证据，不代表创新性、有效性或可实现性成立。当前仍为 `authorized_run_level=none`；S3 允许查新与 in-session 反证，不允许实现、访问实验数据或运行 D0/check/smoke/pilot/full。









**记录**：`experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/research_cycle.md`。




### D-058：ODF-v1 S3 建议谨慎 GO，但新颖性只保留精确接口与路由（2026-08-10）




**查新结果**：未检出与“完整时间秩轨迹 + 完整排序幅值曲线 + DBConformer 原生两路同参数路由”等价的方法；但 2026 年 DWPE 双分支 MI 方法已经把 raw EEG 与保留幅值敏感性的序数复杂度作为互补输入，经典/神经 copula 方法也早已把 marginal distribution 与 dependence 分开建模。故不得声称序数+幅值双分支、order/distribution separation 或可逆 order-statistic mechanics 本身新颖。









**门禁建议**：S3 in-session 综合评分 `5.5/10`，建议仅以 supporting structure 身份谨慎 GO 到 S4，等待用户接受。可保留的新颖性候选仅为完整 rank/quantile 试次接口、无新增参数的 DBConformer 角色路由及其严格归因实验；该建议不构成独立审查、实现或实验授权。









**核心风险**：输入层联合可重构不代表两路压缩编码后仍能使用幅值—时间对应关系；若 source-only D0、`O/raw`、`raw/Q` 或 `Q/O` 对照不支持互补性，应关闭 ODF-v1，不追加局部秩、归一化、融合、损失或第三分支救援。









**记录**：`experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/research_cycle.md`。









### D-059：用户接受 ODF-v1 的受限 S3 GO，S4 固定为先诊断后训练的精确配对计划（2026-08-10）









**决定**：用户接受 ODF-v1 仅作为 supporting structure 进入 S4。计划冻结候选协议 `odf-dbconformer-native-loso-ea-v1`：保留 DBConformer 原生 BNCI2014001 左/右 MI、9-target LOSO、EA、100 epoch fixed-final profile；它不冒充 `mieeg-uep-v1.0`。B0 raw/raw、P1 O/Q、A1 O/raw、A2 raw/Q、A3 Q/O 在同一 profile 内严格按 seed、target、配置和数据指纹配对，且没有新增可训练参数。









**门禁与止损**：先做稳定排序/重构与 source-only 双视图 D0；O、Q 任一视图未同时超过其 200 个 source-label permutation 控制的单侧 95% 阈值并满足 6/9 target 不劣，即关闭 ODF-v1。随后 raw/raw wrapper 数值等价 check、seed 1/target 0 的 2-epoch smoke，最后才是 seed 1、再 seed 2 的两波 P1；两 seed 的预注册正向条件全部满足后，才运行 A1/A2/A3 的条件 P2。P1 或 P2 失败均不以局部秩、归一化、融合、损失、第三分支、跨数据集或后验调参救援。









**当前状态**：S4 计划已形成，但尚待用户冻结；`authorized_run_level=none`。下一次明确授权最多可限于 S5 的最小实现与 M0，不自动包含 check、smoke、pilot、远端上传或 full。









**记录**：`experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/EXPERIMENT_PLAN.md` 与同目录 `research_cycle.md`。









### D-060：ODF-v1 完成最小零参数路由实现，D0 前不读取实验数据（2026-08-10）









**实现**：用户授权 S5 后，新增 `src/models/proposed/odf_dbconformer.py`。该实现直接继承锁定的 DBConformer，只覆盖前向输入路由：`B0=raw/raw`、`P1=O/Q`、`A1=O/raw`、`A2=raw/Q`、`A3=Q/O`；排序使用 `torch.argsort(..., stable=True)`，逆置换可在编码前重构原试次。未添加可训练层、分支、损失、统计量或目标侧逻辑。`src/training/odf_protocol.py` 仅将该模型构造器注入原生 DBConformer 协议；`scripts/run_odf_dbconformer_bnci2014001.py` 只实现 D0/check，明确不提供 smoke/pilot/full 入口。









**验证与边界**：在本地 `mieeg` 环境通过 `py_compile` 和 `tests/test_odf_dbconformer.py` 的五项无数据合约：重构与 ties 稳定、正单调仿射下秩轨迹不变、冻结路由表、B0 与原始 DBConformer 的 state/参数/评估 logits 精确一致、P1 同参数量且原 temporal/channel stem 都获得梯度。`pytest` 未安装，故使用标准库兼容的直接回归入口；这不是 D0 或 check 机器产物。未读取 EEG 数组，未产生 `output/local` 实验目录，未运行任何训练。









**当前状态**：证据仅提升到 `implementation_verified`，`ODF-C0` 为 partial；下一步待用户授权预注册 M0 D0。check、smoke、pilot、远端上传和 full 仍未授权。









**记录**：`experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/research_cycle.md`、`EXPERIMENT_PLAN.md`、`experiments/configs/proposed/odf_dbconformer_bnci2014001_native_loso.yaml`。









### D-061：ODF-v1 的 D0 GO 与 check/smoke 链路验证完成，pilot 仍需单独授权（2026-08-10）









**结果**：预注册 M0 在 `odf-dbconformer-native-loso-ea-v1` 的九个 native EA/LOSO target 上完成。order source-only probe 为 `58.873%`，高于 200 个 source-label permutation 控制均值的 p95 `53.318%`，且 `8/9` target 不低于各自控制中位数；quantile 分别为 `68.133%`、`52.863%` 与 `9/9`。因此严格 D0 判据为 GO。M1 随后通过：B0 与锁定 DBConformer 的 state 初始化、`93,747` 参数量、fused feature 与 eval logits 完全一致，B0/P1/A1/A2/A3 均为有限梯度且同参数量。M2 clean retry 以 seed 1、target 0、2 epochs 成功运行原生 EA/LOSO 的 B0/P1，并回收两份 checkpoint；B0 `64.583%`、P1 `68.056%` 仅属于 smoke 链路输出。









**过程真实性**：D0 首次因用户目录下 MNE 配置权限错误而未进入数组加载，第二次因交互式时间上限中断；二者均保留为 `crashed/aborted` 机器产物。修复仅将 MNE 配置切换到工作区路径并加入逐 target 断点续跑，不改变 probe、数据、置换序列或门槛。首次 smoke 在首个训练迭代前因适配器缺少原生固定字段 `args.weight` 而 crashed，未产生 accuracy/checkpoint；修复仅补齐原始 DBConformer 同值的 `F1/D/F2/weight` 字段，clean retry 使用新 exp_id。SwanLab clean retry final status 为 `success`；其对字符串 arm 指标的两条上传告警未改变本地训练或机器产物。









**边界与下一步**：D0 证明两种非空间输入含有可测 source-only 标签信息；check/smoke 证明实现与训练链路可运行。它们均不支持 ODF-C1 utility、ODF-C2 allocation mechanism、统计显著性、性能改进或论文主张。P1a（B0/P1、seed 1、9 target、100 fixed epochs）仍须用户明确授权；不得据此自动进行远端提交、P1b、A1/A2/A3、P2 或 full，也不得以本轮结果引入后验救援。









**证据**：`output/local/2026-08-10_odf_dbconformer_bnci2014001_native_loso_d0_r3/d0_report.json`、`d0_targets.csv`、`output/local/2026-08-10_odf_dbconformer_bnci2014001_native_loso_check/check_summary.json`、`output/local/2026-08-10_odf_dbconformer_bnci2014001_native_loso_smoke_r2/smoke_summary.json`、`subject_results.csv` 与 `checkpoints/local/2026-08-10_odf_dbconformer_bnci2014001_native_loso_smoke_r2/`。









### D-062：用户授权 ODF-v1 P1a 远端 pilot，r2 已通过远端门禁并运行（2026-08-10）









**授权范围**：用户明确授权提交远端 P1a，仅包括 native EA/LOSO 的 `B0 raw/raw` 与 `P1 O/Q`、seed 1、9 个 target、100 fixed-final epochs。固定服务器环境为 [REDACTED_MACHINE] `mieeg`（Python 3.10.20、PyTorch 1.12.1+cu113、CUDA runtime 11.3），GPU 0/1 各一条 lane；不授权 P1b、A1/A2/A3、P2、full 或任何后验调参。









**过程真实性**：服务器 preflight、外层 SHA-256、bundle manifest、不可变数据 manifest、环境 `pip check` 与 CUDA gate 均通过。首个 r1 bundle 漏打包 ODF runner 的直接依赖 `scripts/run_dbconformer_bnci2014001.py`，9 个 lane 均在模型构造前以 `ModuleNotFoundError` 退出，未产生训练 step、checkpoint 或 score；该失败保留，不作为 pilot 结果。r2 仅补齐此文件，以新 bundle/run ID 重建后通过同一远端门禁，当前 controller/run status 为 `running`。









**边界**：r2 尚无完整 subject 行、summary 或回拉结果，不能产生 ODF-C1/C2 的支持、反驳或性能叙述。完成后必须先验证 archive SHA-256、bundle/data manifests、9 个任务和 18 条 B0/P1 配对行以及 shard 状态，才可在本地解释冻结 P1a gate。









### D-063：ODF-v1 P1a r2 回拉失败归因为旧环境 stable-argsort 不兼容，进入受限环境修复门（2026-08-10）









**回拉证据**：已获取 r2 archive，外层 SHA-256 为 `28c6b14e43159413af69451c1b222feb592e18a57c775e45427d45b474ad1d31`，并验证 38 个 bundle 文件。`scheduler_metrics.json` 显示计划 9、完成 0、缺失 9；9 个 lane log 均完整运行 B0 后，在 P1 调用 `src/models/proposed/odf_dbconformer.py:65` 时触发显式运行时保护：`mieeg` 的 PyTorch `1.12.1+cu113` 不接受 `torch.argsort(..., stable=True)`。因此不存在完整 B0/P1 配对、canonical subject CSV、summary 或可解释的 pilot 统计；日志中的 B0-only 数字为不完整任务副产物，不得作为 baseline 或性能结论。









**只读兼容性核验**：服务器已有 `mieeg-modern`（PyTorch `2.5.1+cu121`）支持稳定排序，并可直接导入 ODF、`timm`、`sklearn`、`mne` 与 `moabb`；小张量 ODF 的 order/quantile 形状正常且严格重构原输入。该探针未读取 EEG 数据、未构造优化器或训练，不改变任何共享环境或冻结模型定义。









**决定与边界**：r2 是环境/API 失败，不能被解释为 ODF-v1 的负向实验。建议的唯一修复是新建不可变 P1a r3 bundle，并将既有环境从 `mieeg` 重绑定为 `mieeg-modern`；B0/P1、seed 1、9 targets、100 fixed-final epochs、数据/划分、初始化、GPU 0/1 和一 lane/GPU 均保持不变。环境是原冻结 plan 的实质执行字段，故 r3 需要用户明确授权；在此之前不提交、不改稳定 ties 语义、不加 fallback，也不启动 P1b、A1/A2/A3、P2 或 full。









**记录**：`results/logs/remote/2026-08-10_odf_dbconformer_bnci2014001_loso_p1a_ccmu_pilot_r2/pilot_r2_intake_analysis.md` 与 `experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/research_cycle.md`。









### D-064：用户授权 ODF-v1 P1a r3 仅重绑定至现有 mieeg-modern 并已启动（2026-08-10）









**授权与不变量**：用户明确授权将 P1a 运行环境固定为服务器已有 `mieeg-modern`。r3 保持 `B0 raw/raw` 与 `P1 O/Q`、seed 1、9 个 targets、100 fixed-final epochs、native EA/LOSO 数据与划分、共同初始化、GPU 0/1 及每卡一 lane；不加入 fallback、不放松 `stable=True` ties 语义，也不授权 P1b、A1/A2/A3、P2 或 full。









**执行证据**：只读探针确认 `mieeg-modern` 为 PyTorch `2.5.1+cu121`、CUDA `12.1` 且支持稳定排序。新 immutable Bundle/RunId 均为 `2026-08-10_odf_dbconformer_bnci2014001_loso_p1a_ccmu_pilot_r3`，外层 archive SHA-256 为 `a9eba9123b46bb95c7872cb077a821caf47c888a11c639fb3a79652084335fc5`；117 个 tar 成员、远端 stage 和执行计划均已验证。远端 `run_metadata.json` 记录 `env_name=mieeg-modern`、GPU `0,1`、每卡一 lane；控制器已通过 immutable bundle verification 并处于 running。









**边界**：r3 目前没有 subject result、完整 pair 或 aggregate pilot statistic。完成后只能先 fetch、核验 archive/manifests、9 个 task 与 18 条 B0/P1 paired rows，再按冻结 P1a 门槛解释；不得提前叙述性能或方向结论。









### D-065：ODF-v1 P1a r3 完整回拉后触发冻结 NO-GO，关闭精确合同（2026-08-10）









**完整性与环境**：r3 已在 `mieeg-modern`（Python 3.10.13、PyTorch `2.5.1+cu121`、CUDA `12.1`）完成。回拉 archive SHA-256 为 `fb8c9fe1e05ac0a4b63b4c3bb2a35b12a1fdb73d74d7ac7d39f366b77652a6a2`；137 个 archive members、122 个 bundle-manifest 文件、数据资产合同、9/9 scheduler tasks、18 条 canonical B0/P1 rows、9 个 per-target pilot summaries 和零 scheduler failure 均验证通过。该结果是完整 exact-paired pilot，不是 r1/r2 的基础设施失败延续。









**冻结 P1a 结果**：B0/P1 分别为 `77.778%/72.454%`，mean paired `P1-B0=-5.324 pp`；仅 `2/9` targets 不负（4、8），而 targets 0、1、2、6 分别为 `-11.806/-6.944/-6.944/-11.806 pp`，均满足 `<=-5 pp` collapse 条件。故 P1a 的三项固定继续条件（mean `>=+0.5 pp`、至少 `6/9` 不负、无 `<=-5 pp` collapse）全部失败。









**结果到主张判读（in-session）**：ODF-C1“角色匹配 O/Q 输入改善 exact-paired native LOSO”的主张不受支持，并对 `odf-dbconformer-native-loso-ea-v1` 合同关闭。实验支持 ODF-v1 可在现代环境中按冻结定义完整执行；它不支持效用、角色分配机制、跨数据集/seed 一般化或论文性能主张。P1 未通过，因此 ODF-C2 无条件归因证据。









**停止规则**：不运行 P1b、A1/A2/A3、P2、full、跨数据集迁移或任何后验 rescue。保留实现、r1/r2 失败归档与 r3 完整负向证据；若继续上位“输入级解耦 + 并行编码”方向，必须另起 S1 科学机制，不得重包装 ODF-v1 变体。









**记录**：`results/logs/remote/2026-08-10_odf_dbconformer_bnci2014001_loso_p1a_ccmu_pilot_r3/pilot_analysis.md`、`experiments/records/2026-08-10_dbconformer_nonspatial_input_factorization/research_cycle.md`。









### D-066：Proposed-research 工作流采用“项目契约—薄编排—方法 Skill”v2（2026-08-11）









**决定**：新建 `experiments/PROPOSED_RESEARCH_WORKFLOW.md` 作为 MI-EEG 项目级契约，并更新全局 `advance-proposed-research` Skill。编排器只维护周期隔离、证据状态、门禁、方法路由和文档升级；`idea-creator`、`research-lit`、`research-refine`、`novelty-check`、`research-review`、`experiment-plan`、`diagnosing-bugs`、`result-to-claim` 与 `experiment-audit` 保留各自的方法职责，但其默认执行预算、输出目录、并行状态、reviewer 线程、seeds/baselines 和写入 fallback 均受项目契约覆盖。









**交互与证据边界**：默认在当前对话以 T0/self 连续推进，一次请求可自动完成多个已授权常规动作，只在方向、未授权 full、最终 claim、实质 protocol/scope 变化、repair/no-go 等真实边界停下。T0 主张上限为 `exploratory`；只有用户显式授权的独立上下文审查可到 `provisional`，有完整 trace 的跨模型/人工审查才可到 `eligible/audited`。默认不创建新的用户对话或任务。









**流程变化**：`grilling` 不再是 S3 必经步骤；S6 拆为本地证据迭代与远端执行；远端结果须经 SHA-256/manifest verify 与 intake 才能进入 claim ledger；新增 S9 evidence-to-writing。状态新增 `review_tier`、`last_failure_class` 与 `escalation_pending`，仅 scientific failure 进入科学 claim 判断。已有 cycle 不批量重写，按保守默认兼容，并在下一次证据性变更时补字段。









**不变项**：本决定不修改 `mieeg-uep-v1.0`、任何已冻结模型/数据/训练协议或历史研究结论；技能库扁平化、共享 reference 修复、历史周期补账另行审计，不与本次工作流改造混做。









### D-067：补强 proposed-research 的方法可用性与状态一致性（2026-08-11）









**决定**：在 D-066 的三层工作流上增加方法解析与依赖完整性规则。编排器先使用精确注册的下游 Skill；未注册时仅允许从配置 Skill 根目录的标准浅层/双层路径读取唯一 `SKILL.md`。方法体缺失或歧义时为 `blocked`，不得由编排器凭记忆替代。每次方法返回记录 `method_source`、`method_completeness` 与 `missing_dependencies`；缺少 reviewer independence、acceptance、citation、integrity 或 evidence-precheck 等裁决性依赖时，禁止 supportive/ambiguous verdict。









**状态语义**：v2 模板移除遗留的 `review_mode`，保留其仅用于读取 v1 周期；`session_mode` 管对话拓扑，`review_tier` 管当前门禁独立性。Claim status 改为纯事实判断（`untested/supported/partial/unsupported/indeterminate/review_unavailable`），`claim_readiness` 单独描述释放资格。周期正文新增 Review Ledger，分别保留 direction、pre-full 与 final 的审查档位，不由一次后续审查覆盖。









**权限与写作**：S9 可从完整 S8 或满足“可复用论文边界”的 scientific `no_go` 进入。只有适用 `AGENTS.md` 授权的主协调者可更新受保护顶层文档；其他执行者只产生 escalation 与待写草案。`AGENTS.md` 增加 proposed 研究入口。此决定不恢复缺失 ARIS shared references，不批量改写历史周期，也不修改已冻结的科学协议或结论。









### D-068：全局科研编排 Skill 更名并固定重要文档中文输出（2026-08-11）









**决定**：全局科研编排 Skill 从 `advance-proposed-research` 更名为 `proposed-research`，目录、frontmatter、UI 名称、默认提示词、项目契约与 `AGENTS.md` 入口同步更新。后续以 `$proposed-research` 调用；历史决策中出现的旧名称仅代表当时的实现，不改变其科学内容。









**文档语言**：工作流生成或更新的 canonical、面向用户或研究决策的重要文档必须使用中文，包括 cycle record、实验计划、Idea/Claim/Review Ledger、实验结论、S9 写作素材及顶层项目文档更新。论文题名、直接引文、标识符、代码、路径、命令、配置键、原始指标字段和参考文献元数据可保留原语言；raw reviewer response、日志、trace、manifest 和机器过程产物不强制翻译，但进入 canonical 文档后的解释必须中文。









### D-069：冻结 BBF-v0 与 UEP 四分类 LOSO，并以受控 finding 而非 burst 首创进入实验规划（2026-08-12）









**方向与协议**：用户明确冻结 `2026-08-12_dbconformer_input_factorization_reconstruction` 周期的 BBF-v0，首轮使用 `mieeg-uep-v1.0`、`tp-dsainet100-v1`、`exact-paired`、BNCI2014001 四分类 subject-independent LOSO。主方法用 source-only 无标签 beta-burst mask 构造 `x_burst` 与 `x_context=x-x_burst`，并以同构双 DBConformer encoder 编码；当前不延续 native binary/EA，也不启动 PAF 并行候选。









**查新修订**：Papadopoulos et al. 的 *Surfing beta burst waveforms to improve motor imagery-based BCI*（DOI `10.1162/imag_a_00391`）已直接使用 waveform-resolved beta-burst rate 做 MI 分类；2026 gamma-burst multi-stream decoder、BraSTORM 与 EEG-DBNet 又分别覆盖 burst 多流、输入双视图和 MI 双分支。因此关闭“首次 burst MI”“burst + dual branch 即创新”和 detector 首创口径。保留的狭义问题只是：在容量、初始化、训练预算和输入能量受控时，exact burst-support/complement 是否超过 raw/raw 与时间位置被破坏的匹配对照。该差异目前只有同会话查新，外部 Phase C/reviewer backend 不可用，`BBF-C3` 不得释放。









**实验合同**：冻结 B0 原始 DBConformer、B1 raw/raw 双编码器、P1 burst/context、A1 occupancy/duration/energy 匹配的 shifted-mask 四变体。detector 固定为 13–30 Hz、4th-order Butterworth、Hilbert envelope、每 outer fold/channel 仅由未增强 source inner-training 数据拟合 q75、最短 50 ms；pilot 后不得搜索频带、阈值、时长、mask、gate、loss 或训练策略救援。顺序固定为 D0 输入/伪迹硬门、B0 no-op、check/smoke、seed-0 九 target、条件 seed-1 resolution，再按预注册门槛决定是否进入 5-seed full。









**授权边界**：本次只冻结方向、协议、claim map、对照、stop rules 与 `EXPERIMENT_PLAN.md`。未授权实现、数据级 D0、check、smoke、pilot、full 或跨数据集运行；`authorized_run_level=none`。由于没有结果，`TASKS.md` 不登记模型启动项，`PAPER.md` 不新增论文证据。









**记录**：`experiments/records/2026-08-12_dbconformer_input_factorization_reconstruction/research_cycle.md`、同目录 `EXPERIMENT_PLAN.md`、`_work/novelty/NOVELTY_CHECK.md` 与 `_work/review/SELF_CRITICAL_REVIEW.md`。









### D-070：用户授权 BBF-v0 进入本机 S5，并预登记一次版本隔离的诊断重试（2026-08-12）









**授权范围**：按冻结顺序在本机执行 D0、B0 no-op、check、smoke 和 BBF-v0 的 seed-0 / 条件 seed-1 LOSO pilot；若 E3 门槛满足，可继续进入原计划的 pre-full gate 与后续冻结环节。训练仍必须使用 `mieeg-uep-v1.0`、`tp-dsainet100-v1`、`exact-paired`、BNCI2014001 四分类 LOSO，并保留 source-only 阈值、无 target-label 训练/选择、100 epoch、validation-best 与 B0/B1/P1/A1 因果控制。









**一次性覆盖**：若完整初版两-seed pilot 无正信号，先封存全部 BBF-v0 产物，再完成只读原因诊断。仅当 source-only D0 指标定位到一个可表述的变换缺陷时，允许一个新版本 `BBF-v0.1` 修改一个确定性输入变换细节；不得用 target 指标选改动，或搜索频带、阈值、时长、位移、架构、gate、loss、优化器或训练日程。优化版必须从 D0/B0/check/smoke 重新验证并运行相同 pilot；v0 与 v0.1 的结果不得合并、择优或被当作 confirmatory 证据。若重试仍无正信号，关闭本轮 BBF 精确家族，不再进行第二次救援。









**证据边界**：授权仅启动执行，不把 D0/check/smoke 或 pilot 自动提升为性能、机制或新颖性主张；外部 novelty/review 缺口维持，`BBF-C3` 仍不可释放。









### D-071：BBF-v0 在 D0 输入硬门处 NO-GO，未启动任何训练（2026-08-12）









**结果**：在本机 `mieeg`（Python 3.10.20、PyTorch 2.7.1+cu128、SciPy 1.15.3、RTX 5060 Laptop GPU）完成 BBF-v0 `r4` 的 9-fold source-only D0。`x_burst+x_context` 最大误差为 `9.536743e-07`；A1 RMS 相对误差 median `0`、p95 `1.11e-07`；首尾 100 ms 聚合 burst-energy 最大占比 `7.48%`，单通道最大占比 `9.97%`，均通过。唯一硬门失败为 held-out target 7 的整体 burst occupancy median `42.64% > 35%`，并且该 target 的所有通道中位 occupancy 为 `39.3%–46.2%`，与同 fold source 的约 `15.7%` 明显分离。









**决定**：这是冻结 source-only detector 在跨被试 target 上出现的 amplitude/occupancy domain-shift，有效地否定了 BBF-v0 的输入对象可比性；它不是平台、环境、训练或性能失败。按 E0 停止：不运行 B0 no-op、check、smoke、pilot、seed-1、full 或跨数据集；不以调整频带、q75、最短时长、mask、缩放或训练策略救援。用户预授权的一次诊断重试只适用于已完成初版 pilot 后无正信号，不能扩展到本 D0 失败。









**过程真实性**：`r1/r2` 由本地前台控制通道 60 s 时限中断，未产生 D0 报告；`r3` 完成但错误地以任意单 trial 最大边界能量判断，故仅保留为实现错误痕迹。`r4` 按冻结的聚合口径重算并为唯一结论来源。完整产物位于 `output/local/2026-08-12_bbf_v0_bnci2014001_uep_loso_d0_r4/`。









### D-072：冻结 RBSF-v1 后的 S3 方向门为 REVISE（2026-08-12）









**冻结对象**：用户明确冻结 RBSF-v1。它保留 BBF-v0 的 13–30 Hz、source-inner-training q75、50 ms、exact complement 和 B0/B1/P1/A1 控制，但把 detector 坐标改为 trial/channel 内 log-envelope 减 1 s running median、再除 robust MAD 的相对 beta 显著性。该构造对常数正幅值增益近似 mask-invariant；冻结不继承 BBF-v0 的 S5 授权。









**查新碰撞**：Papadopoulos 已直接覆盖 beta-burst MI；2026 年 *Single-channel gamma burst dynamics and adaptive deep learning for robust EEG motor state decoding* 又覆盖滑窗局部统计 baseline、adaptive burst threshold、burst/ERD-envelope 多流和 instance-level drift normalization。fBOSC、EEG window-level within-channel normalization、EEG-DBNet 与 2026 DWPE 双分支分别覆盖 relative-background burst detection、实例归一化和 MI 并行编码。故关闭 detector、local normalization、burst multi-stream 与 dual-encoder 的主创新口径。未发现精确同构的仅是 gain-invariant exact event/context 接口加 raw/raw、matched timing-destruction 的严格 LOSO finding；外部 novelty Phase C 不可用，`RBSF-C3` 不可释放。









**临界判定**：T0 方向 verdict 为 `REVISE`。常数 gain invariance 不等于真实 subject invariance；running median/MAD 可能删除持续 ERD/ERS；exact complement 不代表编码后互补；trial normalization 还可能退化为隐式 fixed-top-k。若继续 RBSF-v1，必须由用户明确接受其降级为 finding-focused supporting line，再建立新的 S4；若仍要求承担论文主创新，则返回 S2。当前不授权实现、D0、check、smoke、pilot 或训练。









**记录**：`experiments/records/2026-08-12_dbconformer_input_factorization_reconstruction/_work/novelty/RBSF_V1_NOVELTY_CHECK.md`、`_work/review/RBSF_V1_SELF_CRITICAL_REVIEW.md` 与 `research_cycle.md`。









### D-073：保留 RBSF-v1，主线返回方法重构并形成 POEF-v0 候选（2026-08-12）









**方向处置**：用户明确选择返回方法重构，同时保留 RBSF-v1。RBSF-v1 的冻结 detector、输入接口、对照、查新碰撞和 `REVISE` 结论均不改写；它不再是 active proposed，也不继承 BBF-v0 的 S5 授权。继续调整 running median、MAD、阈值、频带或 normalization 被视为同一 burst-detector 家族内的救援，不作为新主线。









**候选重构**：按神经生理对象、信号分解、跨被试稳健性、架构归因与可证伪性五个顺序视角生成并机械筛选 10 个候选。当前首选为 `POEF-v0`（Phase-preserving Oscillatory-Excess Factorization）：对每个 trial/channel 的复频谱估计 trial-local aperiodic floor，以互补 soft mask 构造相位保留的 oscillatory-excess 与 aperiodic-carrier 两个时域视图，再用容量与初始化匹配的双 DBConformer 编码。该对象不同于 burst threshold、固定 band split 和 generic dual-stream。









**证据边界**：2026 年关于 reconstruction-based EEG foundation model 的研究提示 aperiodic/低频与被试身份偏置，但不能直接证明监督式 DBConformer 存在同一缺陷；故 POEF-v0 仅为 T0 `recommended candidate`，不是冻结 idea contract 或 novelty pass。外部 idea jury 与 Phase C 不可用，短窗 aperiodic 拟合、尺度性质、频率位置破坏对照和 DBConformer 问题真实性仍需在 S2/S3 解决。









**当前门禁**：活动 `proposed_ref` 清空，周期退回 `S1_ground_direction`，等待用户决定是否将 POEF-v0 冻结为新的 S2 对象。当前不授权实现、D0、check、smoke、pilot、full；没有新实验启动或论文证据，因此不更新 `TASKS.md`、`PAPER.md`。









**记录**：`experiments/records/2026-08-12_dbconformer_input_factorization_reconstruction/_work/ideas/METHOD_RECONSTRUCTION_CANDIDATES.md` 与同周期 `research_cycle.md`。









### D-074：冻结并完成 POEF-v0 最小方法实例化（2026-08-12）









**Problem Anchor**：POEF-v0 检验在 BNCI2014001 四分类跨被试 MI 中，将 trial-local aperiodic floor 之上的周期振荡超额与互补 carrier 显式分开编码，是否能为 DBConformer 提供超过容量匹配 `raw/raw` 的可归因信息。2026 年 reconstruction-based EEG foundation model 的 aperiodic/低频偏置只作为问题线索，不写成监督式 DBConformer 已存在同一缺陷的事实。









**冻结变换**：输入沿用 `mieeg-uep-v1.0`、`tp-dsainet100-v1`、`exact-paired`、BNCI2014001 四分类 LOSO。每 trial/channel 在 Z-score 后使用 `NW=3`、`Kmax=5` 的等权 DPSS multitaper，于 `[4,38] Hz` 在 log-log 坐标进行三轮正残差剔除的稳健直线谱底拟合；以功率相对谱底的超额生成 `[0,1]` soft mask，经固定 `2.25 Hz` Hann 平滑后乘原复频谱。`x_osc` 保留原相位，`x_carrier=x-x_osc` 固定 exact complement。该变换没有可训练参数，不使用 target 标签、target-subject 汇总统计、峰中心或类别先验。









**架构与对照**：B0 为原始 DBConformer；B1/P1/A1/A2 共用相同的双 DBConformer feature encoder 与单一 reference head、成对初始化、参数量和训练预算。P1 为 oscillatory-excess/carrier；A1 在 `[4,38] Hz` 以预定频移破坏真实峰位置并匹配分支 RMS；A2 为固定 `8–30 Hz`/complement。learned mask、IRASA 时域回构、FOOOF 标量分支、gate、cross-attention、auxiliary/alignment/domain loss 与后验频谱搜索均排除。









**硬门与主张边界**：训练前 9-fold D0 必须检查 exact reconstruction、有限性、短窗谱底拟合、常数增益尺度不变性、相位保持、视图能量、跨被试塌缩、A1 可构造性及 P1/A2 非退化；任一硬门失败即关闭该精确实例。POEF-C0/C1/C2 仍为 `untested`，POEF-C3 为 `unverified`；不声称首次 periodic/aperiodic 分离、生理源分离、aperiodic 为噪声或跨数据集泛化。









**状态与权限**：POEF-v0 成为 active proposed，RBSF-v1 保留为 `retained / not active`。当前只完成 S2 合同，允许进入正式 S3 查新与临界评审；未授权 S4、配置/代码实现、D0、check、smoke、pilot 或 full。`research-refine` 的外部 Codex reviewer backend 与共享输出 references 不可用，故方法返回为 `degraded`，不产生 supportive direction verdict。









**记录**：`experiments/records/2026-08-12_dbconformer_input_factorization_reconstruction/_work/refine/POEF_V0_IDEA_CONTRACT.md` 与同周期 `research_cycle.md`。









### D-075：POEF-v0 在 S3 方向门处 NO-GO，不进入实验规划（2026-08-12）









**直接查新碰撞**：Bindra & Panwar 2026 的 *A spectral audit framework reveals task-dependent aperiodic reliance across EEG and ECG deep learning*（arXiv:2606.08583v2）已经在短 cue-locked PhysioNet MI trial 上使用 multitaper periodic/aperiodic 分解、保留 Fourier phase 的 raw-signal interventions、sham、simulation、IRASA agreement 和 train-on-representation controls，并在 EEGNet、ShallowFBCSPNet 与 Deep4Net 上发现 aperiodic reliance 很弱。Roy 2022（DOI `10.1016/j.bspc.2021.103496`）又已在 MI 分类中显式融合 periodic/aperiodic 谱参数；SSVEP BCI、癫痫深度分类、FourierMask 与既有 MI 双流网络分别覆盖两类谱对象融合、深度 periodic/aperiodic 建模、频域 mask 和 parallel encoding。因此，POEF 未检出精确同构的“exact residual + matched dual DBConformer + B1/A1/A2”主要是控制组合差异，不足以承担论文主创新。









**问题与实例化缺口**：reconstruction-based EEG foundation model 的 aperiodic/低频偏置不能外推到监督式 DBConformer，且最近多架构 MI audit 给出相反先验，故 POEF 的 aperiodic-dominance Problem Anchor 未建立。冻结公式又把功率比例 `W` 直接作为复振幅 mask，导致分支功率按 `W²` 缩放；`x-x_osc` 只是算术 residual，不是 aperiodic 时域源；mask 来自 multitaper `P_mt` 却作用于 untapered `X`。此外，先 factorize 再做 classwise segment augmentation 后，训练视图通常不再等于增强 raw 的 POEF 变换；两支完全相同初始化也削弱 B1 raw/raw 容量对照。









**决定**：T0 S3 verdict 为 `NO-GO`，不是 `REVISE`。局部重写增强顺序、初始化、A1 或幅值 mask 不能消除直接先例和问题前提不足；POEF-v0 作为论文主创新关闭，不进入 S4、配置/代码实现、D0、check、smoke、pilot 或训练。`POEF-C0/C1/C2` 保持 `untested_closed`，`POEF-C3=direct_collision_no_go`；RBSF-v1 继续 `retained / not active`。若未来仅需解释性 supporting control，可另行冻结 full/aperiodic/flattened/sham audit，但不得继承 POEF-v0 的方法口径或执行授权。









**审查边界与记录**：外部 novelty Phase C / research-review backend 不可用，因此没有 independent/cross-model supportive verdict；该缺口不阻止依据直接碰撞作保守 `NO-GO`。普通文献碰撞不进入 S9 或 `PAPER.md`，也没有新实验启动，故不更新 `TASKS.md`。记录位于同周期 `_work/novelty/POEF_V0_NOVELTY_CHECK.md`、`_work/review/POEF_V0_SELF_CRITICAL_REVIEW.md`、`_work/review/POEF_V0_RESEARCH_REVIEW_REQUEST.md` 与 `research_cycle.md`。









### D-076：POEF-v0 关闭后返回 S1，重构为前线索状态—持续响应条件关系候选（2026-08-12）









**方向重置**：用户明确要求返回 S1 重构新的科学对象。POEF-v0 的 S3 `NO-GO`、未测试 claims 和禁止进入 S4/实现/实验的边界全部保留；RBSF-v1 继续 `retained / not active`。新主线不再生成 burst threshold、periodic/aperiodic、固定频带/图频谱、microstate、协方差轨迹、AR/Granger 或 generic dual-stream 的改名版本。









**S1 推荐对象**：形成未冻结的 `PSRF-candidate`（Pre-cue State–Response Factorization）。它把 trial 表示为 cue 前 ongoing state `b=x[-1,0)` 与排除 cue 邻近段后的 sustained MI response `r=x[tau,4)`；真正要检验的是同一 trial 的正确 `b-r` pairing 是否为四分类 subject-independent decoder 提供超过 late-only、容量匹配 late/late 和 subject/session/run 内确定性 label-blind shuffled-pairing 的条件信息。该对象是时间/生成阶段分解，不要求 `b+r=x`，不声称两者为独立生理源；`tau`、条件算子和模型实例均未冻结。









**查新边界**：Lemm 2009 已建立 state-conditional ERD；Maeder 2012、Bamdadian 2014、Geronimo 2016 与 Mohamed 2025 已覆盖 pre-cue state 对 MI 表现、single-trial gating 或后续 ERD 的影响；Reuderink 2011 已覆盖 pre-trial covariance second-order baselining；Bakas 2025 已揭示 cue 后首段的 class-discriminative eye/visual artifact 风险；TCPL 2025 已用 subject support-set prompt 做 conditioned cross-subject MI decoding。因此关闭“首次使用 pre-cue EEG”“首次状态依赖/条件响应”“baseline whitening”“trial gating”“conditioned prompt”和“early/late 双流”口径。当前未检出的只是 cue-excluded 四分类 LOSO 中，trial-specific 正确 pairing 相对 label-blind shuffled pairing 的增量加严格 capacity/integrity controls；这仍是高风险 T0 检索缺口，不是 formal novelty pass。若 S2 实例退化为 state conditioning、ERD、whitening 或 prompt fusion，应在 S3 前关闭。









**协议与权限**：只读检查表明本地 18 个 BNCI2014001 raw `.mat`、108 个有效 run 在 `run.trial` onset 前均至少保留 250 samples（250 Hz 下 1.0 s），数组上可构造 pre-onset view。但 `mieeg-uep-v1.0` 只冻结 `[0,4)`；raw event 语义、filter boundary 与 cue-exclusion window 尚未冻结。若用户选择进入 S2，必须建立新的 versioned protocol/profile 并在同一协议下重跑 DBConformer 对照，不得沿用旧 UEP 的 `exact-paired` 标签。当前 `proposed_ref` 为空、`authorized_run_level=none`，不实现、不运行，也不更新 `TASKS.md` 或 `PAPER.md`。









**记录**：`experiments/records/2026-08-12_dbconformer_input_factorization_reconstruction/_work/ideas/S1_SCIENTIFIC_OBJECT_RECONSTRUCTION_V2.md`、同周期 `_work/literature/S1_OBJECT_LANDSCAPE_V2.md`、`_work/literature/s1_v2_candidate_papers.json`、`_work/literature/s1_v2_verified_papers.json` 与 `research_cycle.md`。









### D-077：冻结 PSRF-v0 并完成 S2 最小实例化（2026-08-12）









**冻结对象**：用户明确冻结 S1 推荐对象并进入 S2。`PSRF-v0`（Pre-cue State–Response Factorization）成为唯一 active proposed；它检验同一 trial 的 cue 前 ongoing state 是否为排除 cue 邻近段后的 sustained MI response 提供 trial-specific 条件信息。RBSF-v1 继续 `retained / not active`，POEF-v0 继续 `closed / NO-GO`，且不继承既往任何实现或运行授权。









**时间轴与新协议**：官方范式中 trial start 后 2 s 才出现方向 cue；因此本地 MAT 的冻结映射为 `cue_onset=int(run.trial)-1+500`，而非把 `run.trial` 直接称为 cue onset。状态视图固定 cue-relative `[-1,0)`（250 samples），持续响应固定 `[1.5,4.0)`（625 samples）；`tau=1.5 s` 由 1.25 s cue duration 加 0.25 s buffer 前验确定，不按 target accuracy 搜索。18 个 MAT、108 个有效 run、5,184 个 trial 的前后边界全部可构造，四类各 1,296。新协议冻结为 `mieeg-psrf-v1.0` / `tp-psrf-dbconformer100-v1` / `psrf-v1-exact-paired`：连续 run 使用与现有统一预处理频带一致的因果 0.5–40 Hz 4th-order Butterworth SOS filter；所有变体关闭 classwise segment augmentation，避免跨 trial 拼段破坏 pairing。既有 `mieeg-uep-v1.0` 数值不能替代本协议的新 B0，也不得跨协议称为 exact pair。









**最小方法与对照**：context/response 分别由 250/625-sample DBConformer feature encoder 编码为 80 维表示，唯一新增算子固定为零初始化的有界单向乘性调制 `gamma=0.10*tanh(W h_c)`、`h_cond=h_r*(1+gamma)`；context 不得 concat/add 到分类头，训练只用 CE。B0 为 cue-excluded response-only；B1 用 `[1.5,2.5)` late context 加完整 late response 控制容量与重复信息；P1 用真实 pre-cue/late pairing；A1a 在训练和评价中使用 subject/session/run 内冻结 trial-ID hash 的 deterministic label-blind derangement，A1b 只在 P1 checkpoint 推理时施加同一 derangement；A2 检查 pre-cue-only 泄漏；A3 检查 early-only 与 frontocentral shortcut。prompt、cross-attention、auxiliary/domain loss、trial rejection、per-trial whitening、test-time adaptation 和后验窗口搜索均排除。









**反证与权限**：事件映射或 causal filter 无法复核即 protocol NO-GO；A2 稳定可分类先按泄漏审计；P1 不优于 A1 则关闭 trial-pairing 机制，P1 不优于 B1 则不能归因于 pre-cue state，收益依赖 cue-near/额区 shortcut 则不支持 sustained-response claim。`research-refine` 的外部 Codex reviewer backend 与共享输出 references 不可用，方法完整性记为 `degraded`，不产生 supportive direction verdict。当前只完成 S2 合同，允许进入正式 S3 查新与临界评审；`authorized_run_level=none`，不实现、不运行，也不更新 `TASKS.md` 或 `PAPER.md`。









**记录**：`experiments/records/2026-08-12_dbconformer_input_factorization_reconstruction/_work/refine/PSRF_V0_IDEA_CONTRACT.md` 与同周期 `research_cycle.md`。









### D-078：PSRF-v0 在 S3 因科学对象直接碰撞而 NO-GO（2026-08-12）









**决定性查新碰撞**：Li et al. 2020 的 *Endogenous activity modulates stimulus and circuit-specific neural tuning and predicts perceptual behavior*（Nature Communications 11:4014，DOI `10.1038/s41467-020-17729-w`）已经直接使用同一 trial、对 upcoming category 本身无信息的 pre-stimulus endogenous activity 条件化 post-stimulus category decoder，逐试次调整分类边界，明确以 gain modulation 为例，并控制 previous-trial、重复类别与 trial-order effects。该工作与 PSRF-v0 的 Problem Anchor、单向条件化机制及“pre 本身无类别信息但同 trial context 改善 post-response decoding”的判别逻辑高度同构。Lemm 2009、Maeder 2012、Geronimo 2016、Mohamed 2025、Reuderink 2011、TCPL 2025 与通用 FiLM 又分别覆盖 state-conditional response、MI pre-cue state/gating/baselining、conditioned cross-subject decoder 与 feature-wise modulation。cue-excluded scalp MI LOSO 和更完整控制包属于 replication/generalization 与验证严谨性差异，不足以恢复主方法新颖性。









**临界归因问题**：冻结 A1 的 trial-ID hash rotation 在破坏同 trial pairing 时也破坏时间邻近性，因此 `P1>A1` 无法区分 neural state 与 slow drift、run position、previous-trial carry-over、阻抗或 causal-filter settling nuisance。B1 又把完整 response 的子区间作为 context，只能控制参数量与重复 late 信息，不能排除“额外非冗余时段”解释。A2 阴性、A1b inference derangement 和 ±10% bounded adapter 均不能单独关闭联合 nuisance shortcut；保留 artifact trials 也扩大了状态与采集伪迹的歧义。









**决定**：T0 S3 verdict 为 `NO-GO`，不是 `REVISE`。即使补入 temporal-drift-matched null、clean-stratum sensitivity、filter-settling audit 和更公平的 context control，PSRF 也只会成为已知 state-conditioned decoding 原理在 cue-excluded scalp MI LOSO 上的严格复现/推广。PSRF-v0 作为当前论文主创新关闭，不进入 S4、配置/代码实现、D0、check、smoke、pilot 或训练；`PSRF-C0/C1/C2/C3=untested_closed`，`PSRF-C4=direct_collision_no_go`。cue-relative 时间轴、causal pre-cue protocol 与控制思想可以保留，但若降级为 supporting audit，必须返回 S1/S2 另立合同，不继承当前主创新口径或执行授权。RBSF-v1 继续 `retained / not active`，POEF-v0 继续关闭。









**审查边界与记录**：外部 novelty Phase C / research-review backend 不可用，因此没有 independent/cross-model supportive verdict；该缺口不阻止依据直接全文碰撞作保守 `NO-GO`。本轮没有实验启动或论文证据，故不更新 `TASKS.md`、`PAPER.md`。记录位于同周期 `_work/novelty/PSRF_V0_NOVELTY_CHECK.md`、`_work/review/PSRF_V0_SELF_CRITICAL_REVIEW.md`、`_work/review/PSRF_V0_RESEARCH_REVIEW_REQUEST.md` 与 `research_cycle.md`。









### D-079：研究顺序切换为 defect-first，并形成 PTSR 未冻结候选（2026-08-12）









**顺序覆盖**：用户明确要求不改 `experiments/PROPOSED_RESEARCH_WORKFLOW.md`，只把本轮工作顺序改为“先诊断 DBConformer full baseline，再从稳定缺陷选择机制”。PSRF-v0 的 S3 `NO-GO`、RBSF-v1 的 `retained / not active` 和此前所有负边界均保留；旧 proposed 的实现/训练权限不继承。本轮只授权读取既有 checkpoint、重放 frozen target 和执行 diagnostic perturbation/probe。









**完整性与主要发现**：2026-06-18 的 BNCI2014001 四分类 LOSO `mieeg-uep-v1.0 / tp-dsainet100-v1` 共 45 个 validation-best checkpoint 已全部精确重放。五-seed 平均最差 subjects 为 S5 `40.83%`、S4 `45.14%`、S1 `46.28%`；1,399/5,184 trials 被五 seeds 全部判错，占所有 seed-error instances 的 `63.67%`。删除 trial-start-relative `[2.0,2.5)` / `[2.5,3.0)` s 分别下降 `4.78/4.43 pp`；`+160 ms` 零填充 shift 下降 `5.41 pp`，但 `+80/-80 ms` 仅下降 `1.35/0.68 pp`，故关闭“±80 ms 即崩溃”口径。单通道删除平均下降 `3.79–19.43 pp`，P2、CP3、CPz、POz、Cz、C3 和 P1 最敏感。









**分支机制改判**：原分类头的 full 与 temporal-only 零视图 prediction 一致率为 `98.95%`；temporal-only ACC `57.62%`、spatial-only `25.35%`。固定的 source-inner-training-only Ridge probes 又得到 temporal `57.62%`、spatial `26.46%`、concat `57.58%`。因此高达约 71–74% 的 temporal/spatial prediction disagreement 不是两个强分支的系统性冲突，而是 spatial representation 接近机会水平、full 决策被 temporal branch 支配。空间分支没有提供可解码增量，temporal stem 却对单电极删除脆弱，这是当前最强 defect。









**候选机制与边界**：形成未冻结的 `PTSR-candidate`（Phase-Token Spatial Recovery）。它不再做 input factorization 或新建 generic parallel encoders，而是只把原 spatial branch 的 `AdaptiveAvgPool1d(1)` 改为继承 baseline 八个 0.5 s patches 的 phase-resolved channel tokens，以共享 spatial transformer 逐 phase 建模，再做低参数 phase aggregation。候选解释是：原 spatial branch 在跨通道交互前过早全时段池化，丢失了 failure map 显示集中于 cue/early-MI 邻近 `[2,3)` s 的 phase-resolved evidence。该解释仍待 A0 容量/计算对照、A1 label-blind phase permutation 和独立数据集证伪；不得声称已证明视觉 cue、MI physiology 或 patch-boundary 因果。









**确认防火墙与权限**：因为全部 BNCI2014001 target labels 已用于 failure-map 机制选择，该数据集从现在起只作 discovery；同一 9 subjects 上后续改进不能作为独立 confirmatory evidence。进入 S2 前必须冻结一个未参与本轮诊断、通道数足以检验空间机制的 confirmation dataset，并预先固定 K、aggregator、loss 与 stop rules。当前 `PTSR-candidate` 未冻结，`authorized_run_level=none`；不进入实现、训练、SwanLab 或 `PAPER.md`。完整记录见同周期 `_work/diagnostics/DBCONFORMER_BASELINE_FAILURE_MAP.md` 与 `output/local/2026-08-12_dbconformer_bnci2014001_loso_failure_map_diagnostic/`。









### D-080：PTSR 转出当前会话，S1 收敛为 PGSF 输入适配候选（2026-08-12）









**范围校正**：用户明确指出，PTSR 所处理的 phase-token spatial recovery 更接近另一会话的“双分支间信息融合交互”主创新。当前会话只研究原始输入确定性解耦、输入双分支与两个独立同构 encoder；目标降为找到逻辑合理、可归因的独立正信号，并把模块保留为未来交互方向的可选适配器，不要求单独支撑整篇论文，也暂不做联合实验。PTSR 因此记为 `deferred / out of scope`，不是 `NO-GO`；RBSF-v1 继续 `retained / not active`，POEF-v0、PSRF-v0 和既有负边界不变。









**S1 推荐候选**：形成未冻结的 `PGSF-candidate`（Patchwise Gain–Shape Factorization）。对增强后的 EEG 按 DBConformer 原有 125-sample / 0.5 s patch，计算每个 `channel × patch` 的 RMS gain `g`，构造广播的 `log(g)` gain view 与 `x/g` shape view，满足输入层精确乘法重构 `x=exp(log(g))*(x/g)`。两张 `C×T` 视图分别进入两个完整、同构且参数不共享的 DBConformer feature encoder，只允许固定 late concatenation 和单一分类头；不加入 cross-attention、gate、prompt、辅助/对比损失或另一主创新模块。









**因果边界与对照**：PGSF 不增加输入信息，不称为生理源分离或 statistical disentanglement。最小问题是局部尺度场与单位波形形态的显式分工能否超过容量匹配的 `(raw,raw)` 双编码器。若进入 S2，必须冻结 B0 单模型、B1 raw/raw、P1 gain/shape 和 A1 label-blind gain-patch 错位后重算 shape 的精确重构控制；P1 只有同时超过 B1 与 A1 才形成模块级机制信号。failure map 的 `amplitude×0.5 -6.47 pp` 与 `[2,3)` s 证据集中仅支持候选生成，不确认机制；BNCI2014001 继续只作 discovery。









**查证与权限**：EEG-DBNet、Dual-TSST、左右半球 dual-CNN、GFP-normalized topography 与一般 physiological shape/amplitude decoupling 已覆盖双分支和幅值—形态分离的宽口径，故 PGSF 暂定仅有 `3/10` 模块级新颖性，不作 standalone claim。外部 idea jury 与 `verify_papers.py` 不可用，当前为 `T0/self, degraded`；没有 formal novelty pass 或独立评审。`PGSF-candidate` 尚未冻结，`authorized_run_level=none`：不修改模型/config，不执行 D0、check、smoke、pilot 或训练，不更新 `TASKS.md`、`PAPER.md`。









**记录**：`experiments/records/2026-08-12_dbconformer_input_factorization_reconstruction/_work/ideas/S1_INPUT_DECOUPLED_DUAL_ENCODER_CANDIDATES.md` 与同周期 `research_cycle.md`。









### D-081：冻结 PGSF-v0 并完成 S2 方法实例化（2026-08-12）









**冻结范围**：用户明确冻结 Patchwise Gain–Shape Factorization v0（PGSF-v0）并进入 S2。它是当前会话唯一 active proposed，定位为未来“双分支间信息融合交互”主方向的输入适配 supporting component；本轮只要求独立正信号和合理归因，不要求单独支撑论文，也不做联合实验。PTSR 继续 `deferred / out of scope`，RBSF-v1 继续 `retained / not active`，POEF-v0、PSRF-v0 与既有负边界不变。









**数学与执行接口**：冻结 `mieeg-uep-v1.0 / tp-dsainet100-v1` 的 BNCI2014001 四分类 LOSO matched profile。PGSF 在 inner-training-only channel-wise Z-score 和训练 batch 的 `classwise_segments=8` 增强之后执行；将 `B×22×1000` 输入按原生 125-sample patch 划为八段，以 `g=sqrt(mean(x²)+1e-12)`、`A=log(g)`、`U=x/g` 构造两张同形视图，在浮点容差内满足 `x=exp(A)⊙U`。不追加 view normalization，不读取标签、target aggregate 或 sample order；gain/shape 只解释为局部 log-RMS 尺度场与去除局部正尺度后的有符号波形，不解释为生理源或 statistical disentanglement。









**容量与初始化控制**：B1/P1/A1 共用两个参数不共享、拓扑完整但降深的 DBConformer feature encoder，每支 `emb_size=40`、temporal/spatial depth `1/1`、`spa_dim=12`，各输出 80 维，concat 后仅用 `Linear(160,4)`。四分类 constructor 只读审计得到 B0 `93,813` parameters、dual wrapper `93,990`，差 `177` 即 `0.1887%`；这不是实现、D0 或性能证据。两 outer encoder 使用不同 deterministic 初值以避免 raw/raw 对称退化，B1/P1/A1 的对应分支和 head 则加载相同快照。









**对照与证伪**：arms 冻结为 B0 原 DBConformer、B1 `(raw,raw)`、P1 `(A,U)`、A1 将八个 gain patch 固定循环位移四格并以 `U_shift=x/g_shift` 重算的错位精确因子化。A1 保持 gain 多重集和 raw reconstructability，但会改变 shape 的局部尺度统计，因此不是完美自然数据 null；未来 D0 必须先冻结并检查 view RMS、quantile、极值和 patch-boundary jump，若出现数量级异常则 A1 不得承担机制控制，必须返回 S2，不能事后搜索 shift。PGSF 只有在 P1 同时优于同构 B1 与 A1、不明显劣于 B0、无新增 subject collapse，且 branch-only/deletion 不支持单支完全解释时，才形成模块级正信号。









**审查与权限**：Problem Anchor、数学/模型接口、初始化、claims、anti-claims 和 D0 falsifiers 已冻结于 `_work/refine/PGSF_V0_IDEA_CONTRACT.md`。外部 GPT-5.6-Sol 方法评审 backend 不可用，`research-refine` 完整性记为 `degraded`；T0 自审不构成 READY、novelty pass 或独立方向 GO。当前 S2 完成，下一门禁是 S3 正式查新与临界评审；`authorized_run_level=none`，不修改模型/config，不执行 D0、check、smoke、pilot 或训练，不更新 `TASKS.md`、`PAPER.md`。









### D-082：PGSF-v0 在 S3 NO-GO，并返回 S1 形成 RCCF 未冻结候选（2026-08-12）









**PGSF 查新结论**：raw/normalized multivariate time series 联合分类、local slice normalization + statistical-property modeling、shape/amplitude physiological signal decoupling 以及 MI dual/multi-input encoder 均已有直接或强近邻。未检出逐项相同的 125-point RMS + dual DBConformer + B1/P1/A1，但剩余差异主要是工程坐标与控制包；T0 supporting-module 新颖性仅约 `3/10`，不能单独补偿归因缺口。









**决定性临界问题**：冻结 profile 为 `T=1000`、`classwise_segments=8`；参考增强代码令 `seg_len=T//8=125`，从同类别 donor 逐段拼接。PGSF 又在增强后按完全相同的 125 点边界计算 gain/shape，因而 factorization 单元与 label-conditioned augmentation donor 边界一一重合。任何正信号都可能来自增强拼接几何。A1 为保持 raw reconstruction 会同步改变 shape 分支局部尺度；而 `Linear(concat(h_gain,h_shape))` 只表达两支边际 logit 相加，不能显式建模合同声称的 local pairing。修复必须改变 patch/augmentation 关系、A1 或 head，已超出 S4 细化并可能侵入另一会话的 interaction 方向。









**S3 决定**：冻结 PGSF-v0 为 `NO-GO`，不进入 S4、配置/代码实现、D0、check、smoke、pilot 或训练。`PGSF-C0/C1=untested_closed`、`PGSF-C2=attribution_invalid_no_go`、`PGSF-C3=compositional_collision_no_go`。外部 novelty Phase C / research-review backend 不可用，故没有 supportive independent verdict；该缺口不推翻由冻结本地代码和合同直接支持的保守关闭。B1 raw/raw、独立 A/B 初始快照、跨 arm 配对初始化和容量控制思想继续保留。









**按用户条件返回 S1**：新的 T0 推荐对象为未冻结的 **Reference-aligned Common–Contrast Factorization（RCCF-candidate）**。BCI IV-2a 为左乳突共同参考的 22 通道 monopolar EEG，当前 official-preproc 未做 CAR。九个 LOSO fold 的无标签输入审计显示，source-Z-score 坐标中的已知参考方向 `q∝[1/s_c]` 占 held-out trial 总能量的 subject-median `70.13%–88.03%`，九 subject 中位数 `80.70%`；source PC1 与 q 的余弦绝对值 `0.9941–0.9948`，PC1 占 covariance trace `80.07%–83.10%`。该统计只证明稳定的 reference-aligned dominant geometry，不证明其为噪声或具有类别贡献。









**候选接口与边界**：RCCF 令 `z_common=qq^Tz`、`z_contrast=(I-qq^T)z`，两视图 exact additive、channel-orthogonal、同形，且固定逐时点线性算子与 classwise segment reconstruction 严格可交换。候选问题是把 dominant common mode 与低能 channel contrast 分别交给独立 encoder，能否比容量匹配 raw/raw 恢复空间增量；不声称 reference artifact removal、皮层源分离或跨分支 pairing。q 与 PC1 高度一致使 reference-specific claim 受限，新颖性 T0 约 `4/10`，只定位 supporting adapter。









**当前权限**：RCCF 尚未冻结，没有 active idea contract、formal novelty pass、外部 jury verdict 或性能证据；`protocol_id/training_profile/compatibility_label=null`，`authorized_run_level=none`。等待用户是否冻结后进入 S2；本轮没有新实验或论文证据，不更新 `TASKS.md`、`PAPER.md`。









**记录**：同周期 `_work/novelty/PGSF_V0_NOVELTY_CHECK.md`、`_work/review/PGSF_V0_SELF_CRITICAL_REVIEW.md`、`_work/review/PGSF_V0_RESEARCH_REVIEW_REQUEST.md`、`_work/diagnostics/RCCF_INPUT_GEOMETRY_AUDIT.md`、`_work/literature/S1_REFERENCE_SUBSPACE_LANDSCAPE_V3.md`、`_work/ideas/S1_INPUT_FACTORIZATION_RECONSTRUCTION_V3.md` 与 `research_cycle.md`。









### D-083：冻结 RCCF-v0 并完成 S2 方法实例化（2026-08-12）









**冻结范围**：用户明确冻结 Reference-aligned Common–Contrast Factorization v0（RCCF-v0）并进入 S2。RCCF-v0 成为当前会话唯一 active proposed，定位为未来“双分支间信息融合交互”主方向的可选输入适配 supporting component；当前只要求独立正信号与合理归因，不要求独立支撑整篇论文，也不做联合实验。RBSF-v1 继续 `retained / not active`，PTSR 继续 `deferred / out of scope`，PGSF-v0、POEF-v0、PSRF-v0 与既有负边界不变，且不继承任何旧实现或运行授权。









**数学与协议接口**：冻结 BNCI2014001 四分类 LOSO 的 `mieeg-uep-v1.0 / tp-dsainet100-v1 / exact-paired` discovery profile。每个 `(seed,target)` 直接复用 inner-training-only channel-wise Z-score 标准差，令 `q=normalize([1/s_c])`、`P_q=qq^T`，在增强后 model forward 起点构造 `z_common=P_qz` 与 `z_contrast=(I-P_q)z`。两视图 exact additive、channel-orthogonal、能量守恒、同为 `22×1000`，并与固定 donor map 的 classwise segment augmentation 严格可交换；不增加 per-view normalization、learned projector、target calibration 或 interaction 模块。









**容量、初始化与对照**：B1/P1/A1/A2 共用两个参数不共享的降深 DBConformer feature encoder，每支 `emb_size=40`、temporal/spatial depth `1/1`、`spa_dim=12`，各输出 80 维，concat 后仅用 `Linear(160,4)`。冻结 B0 原 DBConformer、B1 `(z,z)`、P1 `(P_qz,(I-P_q)z)`、A1 magnitude-matched sign-scrambled q projector/complement、A2 source-PC1 projector/complement；对应 branch/head 跨 arm 共享初始化快照，A/B 自身采用不同 deterministic 快照。容量目标为 dual `93,990` 对 B0 `93,813`、差 `0.1887%`，S5 仍须重新核验。









**归因边界**：A1 保持 q 的逐通道载荷绝对值但不匹配投影能量，故 `P1>A1` 不是 reference-specific 充分证据。S1 中 source PC1 与 q 的余弦绝对值已达 `0.9941–0.9948`，因此 A2 的首要作用是限制口径：若 P1 与 A2 相当，只能声称 dominant reference-aligned common/contrast routing，不能声称 reference physics 优于 generic PC1。common view 不得称为噪声或 reference artifact，contrast view 不得称为纯净神经源；RCCF 不构成 ICA、REST、source separation 或 statistical disentanglement。









**正信号草案与权限**：RCCF-C1 的 S2 草案为共同 discovery units 上 `P1-B1 >=+0.5 pp`、至少 `6/9` subjects 为正、`P1-B0 >=-0.5 pp`、无新增 subject 平均 `<=-10 pp` collapse；机制还要求 branch-only/deletion 不支持单支完全解释。精确 seeds、统计、stop rules 和 pilot/full gate 留给 S4。完整合同位于 `_work/refine/RCCF_V0_IDEA_CONTRACT.md`；外部 GPT-5.6-Sol method reviewer backend 不可用，`research-refine` 完整性为 `degraded`，不产生 READY、novelty pass 或独立方向 GO。当前 S2 完成，下一门禁为 S3 正式查新与临界评审；`authorized_run_level=none`，不修改代码/config，不执行 D0、check、smoke、pilot 或训练，不更新 `TASKS.md`、`PAPER.md`。









### D-084：RCCF-v0 通过 claim-reduced S3，仅进入 supporting utility 规划（2026-08-12）









**查新结论**：average-reference/centering 的 rank-one projector、MI 中的 common-reference/CAR/bipolar/ICA/CSP 比较、common/class-specific factorization 与 dual/multi-input late fusion 均有直接先例。未检出 `source-Z-score q + 同时保留 P_qz/(I-P_q)z + 容量匹配双 DBConformer + B1/A1/A2 + 四分类 LOSO` 的逐项同构工作，但剩余增量只够定位为窄 supporting adapter；T0 新颖性约 `3/10`，不支持独立论文主创新或 reference theory contribution。外部 `novelty-check` Phase C 与 `research-review` backend 不可用，formal/supportive novelty verdict 继续阻塞。









**不可解除的口径边界**：共同投影包含 scalp global mean 与 reference term 的混合，不能恢复 reference electrode signal；common/contrast 不得称为 artifact/clean neural source。source PC1 与 q 的余弦绝对值为 `0.9941–0.9948`，故当前数据不能识别 reference-specific superiority。A1 只匹配 channel loading magnitudes、不匹配 covariance projection energy，`P1>A1` 也不是 reference-alignment 的决定性证据。









**方向决定**：S3 T0 verdict 为 `GO_WITH_CLAIM_REDUCTION`。只允许进入 S4 冻结 bounded utility 合同：以 P1 vs B1 为决定性容量/路由比较，以 P1 vs B0 检查代价，并用 branch-only/deletion 排除单支退化。若未来为正，只能声称“对冻结 DBConformer discovery profile，显式 dominant common/contrast routing 比复制 raw input 给双 encoder 更有用”。RCCF-C2 的 reference-specific 子主张关闭，RCCF-C3 降为 `low_novelty_supporting_only`。当前 `authorized_run_level=none`，不实现、不做 D0/check/smoke/pilot 或训练；下一决策边界为是否进入 S4。









**记录**：同周期 `_work/novelty/RCCF_V0_NOVELTY_CHECK.md`、`_work/review/RCCF_V0_SELF_CRITICAL_REVIEW.md`、`_work/review/RCCF_V0_RESEARCH_REVIEW_REQUEST.md` 与 `research_cycle.md`。









### D-085：冻结 RCCF-v0 supporting-utility 实验合同（2026-08-12）









**合同目标**：只检验一个 discovery-only 问题：在相同 dual wrapper、参数量、初始化、训练日程和线性 late head 下，`P1=(P_qz,(I-P_q)z)` 是否优于 `B1=(z,z)`，且不明显劣于通过 no-op 核验的 B0。A1 只作任意 sign-scrambled rank-one orientation 的弱控制；A2 只量化 q 与 source-PC1 的等价性并限制口径；二者都不支持 reference-specific superiority。









**运行结构与停止规则**：E0 对全部 45 个 `(seed,target)` 做 source-only provenance、投影代数、重构、正交、能量、augmentation 交换律与 synthetic shift D0；E1 先核验 B0 45-row checkpoint/protocol 可复用性，再完成 B1/P1/A1/A2 check/smoke。E2 只训练 B1/P1 的 `2 seeds × 9 targets`；pilot positive signal 冻结为 `mean(P1-B1)>=+0.5 pp`、至少 `6/9` subject 为正、`mean(P1-B0)>=-0.5 pp` 且无新 `<=-10 pp` collapse。未达正信号即关闭 exact RCCF-v0 utility contract，不扩 seed 或改 projector/架构救援。只有 E2 positive 才执行 E3 的 A1/A2/deletion attribution pilot；full 仍需用户另行授权。









**边界与记录**：full 成功也只支持 T0/exploratory 的 BNCI2014001 discovery finding；不释放 novelty、reference recovery、artifact removal、reference physics 或跨数据集一般化主张。活跃计划见同周期 `EXPERIMENT_PLAN.md`，旧 BBF-v0 计划已原样归档在 `_work/archive/`；`TASKS.md` 已登记模型级等待项，`PAPER.md` 不更新。当前 `authorized_run_level=none`。









### D-086：RCCF-v0 在 E0/D0 construct hard gate 关闭（2026-08-13）









**执行范围**：用户授权的最小实施/E0–E1 中，先完成了 RCCF wrapper/config、seed 0/target 0 的四 arm check，以及 r2 的全量 `5 seeds × 9 targets = 45` source-only D0；没有训练。r1 被外层 120 秒命令时限中断，只保留 5 个部分 manifest，不参与判定。r2 的机器产物在 `output/local/2026-08-13_rccf_dbconformer_bnci2014001_uep_loso_d0_r2/`。









**硬门结果**：P1/A2 held-out common-energy median 为 `70.1279%–88.7302%`，但 A1 sign-scrambled rank-one common view 为 `0.3160%–4.9040%`，全部 45 fold 低于冻结 `[5%,95%]` 非退化下限。P1/A1/A2 的 train/validation/test 重构 max 均为 `9.536743e-7`，donor-map 的 P1 augmentation commute 为零；但 float32 synthetic-shift contrast max 为 `2.384186e-6`，43/45 超过冻结 `1e-6`。A1 的能量失败本身已经足以关闭构造合同，数值精度失败不作为修补后继续运行的理由。









**判定与边界**：这是 `construct/control` failure，不是性能、模型、B0 或 OOF 失败。`RCCF-C0=construct_no_go`；C1/C2 未测试关闭。严格按合同不运行 B0 no-op、smoke、pilot、A1/A2/deletion 或 full，也不把 check 的可运行性写作结果。check 中四 arm forward/backward、跨 arm 同初始化和 A/B 独立初始化通过；`Linear(160,4)` 的实际容量为 `94,070`，相对 B0 `93,813` 为 `+0.274%`，仍在 ±0.5% 上限内，但并不复现历史 `93,990` 机械数，已作为合同一致性警示保留。









**后续约束**：RCCF-v0 保持关闭。若继续该上位方向，必须新建版本并从 S2 重构 control/non-degeneracy 和数值审计合同；不得通过 energy matching、改 A1 seed、放宽能量/精度阈值或改 projector 来“救回” RCCF-v0。









### D-087：Proposed-research 改为单 idea 的“宽进严出”v3（2026-08-13）









**决定**：`proposed-research` 继续保持当前会话、精确 cycle 隔离、证据/授权/claim 分离和中文重要文档，但每个 cycle 只管理一个 baseline 上的一个核心模块或 idea，不增加模块组合阶段。流程增加 `discovery / consolidation / confirmation` 三个正交研究相位：早期允许新颖性或机制逻辑较弱但可实施、公平且成本受控的 supporting candidate 进入受限正信号筛选；只有冻结版本、披露选择路径、建立未参与选择的 confirmation scope、完成 full 完整性检查和逐 claim 判读后，结果才可成为论文证据。









**D0 与探索迭代**：D0 分为 `D0-C` 构造、`D0-P` 协议、`D0-N` 控制有效性和 `D0-O` 可观测性。控制退化只返回实验设计，不再等同于模块科学失败；D0-O 默认是风险提示，只有与核心假设严格绑定时才是硬门。Discovery 可在预先冻结的版本预算内进行透明、编号化迭代，但必须保留所有版本、修改前已读证据与失败结果，不得合并或择优后冒充 confirmation。









**解释与审查**：每次 Discovery Idea Contract 首次冻结或发生实质再冻结后，编排器显式调用 `wait-what`，用中文重新解释 baseline 问题、单一改动、可能作用、首个比较、最大风险、失败范围和 anti-claims；该步骤不评审或授权。外部模型/独立审查不再是强制门禁，T0 当前会话自审可推进并在 full 证据与完整性合同齐备时形成 paper-eligible claim；T1/T2 只作为用户显式授权的独立性增强，任何自审仍必须诚实标注。









**兼容边界**：本决策不回改既有 cycle 的科学结果，也不修改 `mieeg-uep-v1.0`。活动 legacy cycle 只在状态对账时修复非法枚举和失败路由；实质新机制由用户显式启动新 cycle。









### D-088：冻结并解释 RCCF-Core-v1（2026-08-13）









**冻结决定**：用户明确要求冻结并解释重建后的 `RCCF-Core-v1`。冻结科学对象为 source-only `q=normalize(D^-1 1)` 下的 `P1=(P_qz,(I-P_q)z)`，两张 view 分别进入参数独立、容量匹配的 DBConformer encoder，concat 后仅用 `Linear(160,4)`。不引入 learned projector、attention、gate、跨分支交互、辅助损失或新 backbone；定位仍是未来交互主方向的 supporting input adapter，不要求独立支撑整篇论文。









**冻结比较与失败边界**：首轮唯一决定性比较为 `P1 vs B1-DR`。`B1-DR=(sqrt(rho_q)z,sqrt(rho_c)z)` 的尺度只由 outer-fold inner-training 数据拟合，用于同时控制双编码容量、对应初始化、late head 与总体分支 RMS；B0 只作安全锚点。旧 A1 不再前置；只有 P1 获得正信号后才允许设计并校验 `A1-DR`。若公平 utility screen 无正信号，则关闭精确 RCCF-Core-v1，不用 normalization、learned projector、loss、宽度或 interaction 救援；若 A1-DR 退化，只关闭 orientation attribution，不反向否定 utility。









**解释与方法溯源**：冻结后已用中文完成 baseline 问题、单一改动、可能作用、首个比较、最大风险、失败范围和 anti-claims 七项解释。最初记录把 `wait-what` 误判为没有唯一可解析的本地方法文件；D-089 已复核并修正其注册元数据、自动调用策略和 context 适配，现有解释按唯一直接路径重新对账为 `method_completeness=full`。这一修正不改变冻结科学内容。最大口径限制仍是 q 与 source-PC1 近共线，故不允许 reference-specific、source separation 或 physiology claim。









**阶段与权限**：S2 冻结和解释完成，周期定位到 S3 查新/临界评审决策边界；S3 尚未执行，`signal_status=not_tested`、`claim_readiness=ineligible`、`authorized_run_level=none`。当前不实现、不运行 D0/check/smoke/pilot/full，也不更新 `TASKS.md` 或 `PAPER.md`。正式记录见 `experiments/records/2026-08-13_dbconformer_reference_common_contrast_routing/research_cycle.md`、`_work/refine/RCCF_CORE_V1_IDEA_CONTRACT.md` 与 `_work/explain/RCCF_CORE_V1_WAIT_WHAT.md`。









### D-089：修复 `wait-what` 注册、自动调用与冻结合同 context 适配（2026-08-13）









**问题**：旧安装位于双层目录，`SKILL.md` frontmatter 含当前规范不接受的 `disable-model-invocation`，同时 `agents/openai.yaml` 设置 `allow_implicit_invocation: false`。这与 proposed-research 在合同冻结后自动调用 `wait-what` 的要求冲突，并导致一次执行在未完成双层路径核验时错误记录为 `blocked`。









**修复**：将 `wait-what` 规范化到标准 Skill 根目录，frontmatter 仅保留 `name/description`，允许 implicit invocation，并把冻结解释定义为有界 context 操作。primary context 必须是精确版本的 frozen Idea Contract；supporting context 只允许当前 cycle 的 `research_cycle.md`、项目工作流/`AGENTS.md`/直接相关协议，以及合同或 cycle 明确引用且与七项解释有关的 review、literature、experiment plan 或 decision。`CONTEXT.md` 改为可选补充，不存在不降级；禁止扫描其他 cycle 或按文件新旧推断上下文。









**记录与边界**：每次解释记录实际 method source 以及 primary/supporting/excluded/gaps context manifest。来源冲突时仍以冻结合同为准，差异交回编排器决定是否再冻结；`wait-what` 本身不改合同、不评审、不授权、不升级证据。RCCF-Core-v1 的既有解释已按该规则重新对账，科学内容、阶段、claim 与运行权限均未改变。









### D-090：RCCF-Core-v1 以弱新颖性 supporting candidate 通过 S3（2026-08-13）









**查新结论**：BraSTORM 已直接占据 EEG input-level spatio-temporal factorization、并行独立 encoder 与 late representation fusion 的高层叙事；DBConformer、EEG-DBNet、EEGEncoder、LI-DSN 等进一步说明 temporal/spatial/spectral dual-stream 已是拥挤设计空间。average-reference/centering 的 rank-deficient orthogonal-projector 性质也是已知数学对象。因此 RCCF-Core-v1 不得声称首次输入级双流、首次独立双编码器、新 projector、新 reference theory 或 standalone architecture novelty。当前聚焦检索未发现同时使用 source-only `q=normalize(D^-1 1)`、保留 `P_qz/(I-P_q)z` 两张同形 view、独立 DBConformer encoders、无 interaction/loss 且以 `B1-DR` 做 exact-paired utility 比较的逐项同构工作；该剩余差异只足以支撑 bounded supporting discovery。









**临界评审**：S3 T0/self 未发现 fatal defect。插入点真实、P1 对象非退化、`q/rho` 可保持 inner-training-only、B1-DR 能控制容量/对应初始化/head/总体 RMS，首轮成本可限制为 P1/B1-DR。RCCF-v0 的旧失败是 A1 `D0-N` 退化，P1/B1 从未训练，故不是本候选的可靠负证据重复。最大未消除混杂是 P1 与 B1-DR 的有效秩、协方差谱和高阶学习难度不同；因此正结果只能支持完整 routing intervention 的 utility，不能支持 orientation、reference physics 或双支必要性。









**S3 判定与权限**：`gate_decision=go`、`s3_verdict=GO_WITH_CLAIM_REDUCTION`、`candidate_role=supporting_candidate`、`novelty_status=weak`。周期进入 S4 实验合同设计决策边界，但 `signal_status=not_tested`、`claim_readiness=ineligible`、`authorized_run_level=none`。当前不实现或运行 D0/check/smoke/pilot/full。`novelty-check` 与 `research-review` 的外部 reviewer/trace 依赖未调用或不可用，方法完整性诚实记录为 `degraded`，实际评审层级为 T0/self；这不阻塞 discovery，但禁止声称独立或跨模型审查。









**记录**：`experiments/records/2026-08-13_dbconformer_reference_common_contrast_routing/_work/novelty/RCCF_CORE_V1_NOVELTY_CHECK.md`、`_work/review/RCCF_CORE_V1_S3_CRITICAL_REVIEW.md` 与同周期 `research_cycle.md`。









## D-098：TPCR-v0.2 通过 B0 native-safety gate，进入冻结 path-use 诊断









- 日期：2026-08-13




- 完整性：远端 B0 safety pilot `2026-08-13_tpcr_v0_2_dbconformer_bnci2014001_b0_ccmu_pilot_r4_w1` 完成 18/18 个 `(seed,target)`；归档 SHA-256、317 个成员及 257 个清单文件均已验证并 intake。B0 18 个 predictions/checkpoints 与本地 B1/P1/A1 合计 72 个 prediction 逐项重算一致，split、runner/model hash 及语义配置匹配。




- 门禁结果：B0 `56.983%`，P1 `58.285%`，`P1-B0=+1.302 pp`，满足冻结 `>=-0.5 pp` safety 规则。该结果只解除 B0 safety 阻塞，授权既有 P1 checkpoint 的 aux-zero/aux-shuffle path-use 诊断。




- 关键限制：B0 运行在 [REDACTED_MACHINE] PyTorch `1.12.1+cu113` / RTX 3090；B1/P1/A1 运行在本机 PyTorch `2.7.1+cu128` / RTX 5060。故 B0 不是环境完全配对的主性能 comparison；本轮唯一 exact-paired 主比较仍是本机的 P1-B1 与 P1-A1。不得由此作 paper-facing 性能、机制、泛化或新颖性主张。




- 禁止范围：不重训 B0/P1，不修改科学对象、窗口、aux、阈值或 selection scope，不访问 confirmation candidate；S7/confirmation 仍须在 path-use 和选择历史审计后另行冻结。









## D-099：TPCR-v0.2 的 auxiliary path 已被使用，但转入 S7 confirmation 边界









- 日期：2026-08-13




- M6 结果：对 18 个冻结 P1 checkpoint 的无训练推理复放中，intact 预测逐 fold 与原 P1 完全一致；aux-zero 相对 intact 为 `-4.581 pp`，确定性的 within-fold aux-shuffle 为 `-9.549 pp`。zero 在两 seed 均下降、8/9 subject two-seed mean 下降；shuffle 在两 seed 均下降、9/9 subject two-seed mean 下降。




- 判断：这足以说明 selected P1 实例实际使用了 context auxiliary path，故不能把主 discovery 正信号简化为“aux 完全未用”。它只属于 selection-contaminated discovery 的描述性 path-use 证据；不证明 context 的生理含义或因果机制。




- 当前边界：BNCI2014001 的全部 P1/B1/A1/B0/path-use 结果均是 discovery selection history；B0 还存在本机/服务器环境差异。下一步必须在 S7 明确披露选择历史并冻结一份真正 untouched 的 confirmation scope，之后才能授权任何 confirmation 训练。不得自动猜测或访问 confirmation 数据集/seed。









## D-100：TPCR-v0.2 冻结 BNCI2014004 为辅助外部诊断，而非 001 的性能否决（2026-08-13）









- 暴露审计：未发现 TPCR-v0.2 在 BNCI2014004 的配置、训练、checkpoint、prediction、target aggregate 或性能结果。TPCR-v0.1 只曾把 004 写为未执行 confirmation candidate，故 004 对 v0.2 是 outcome-untouched，但不是完全无先验概念的盲数据。




- 数据边界：004 为 3 EEG 通道、左右手二分类、全 5 session；虽与 001 同为 250 Hz / `[0,4)` s / 1000 samples，可原样使用 `[2,3)` s mask，但不等价于 001 的 22 通道四分类空间学习条件。




- 冻结执行：只运行 B1/P1，各 `5 seeds × 9 LOSO targets`、`mieeg-uep-v1.0 / tp-dsainet100-v1`、004 内 exact-paired。只允许 `channels=3`、`classes=2` 与二分类 head 的 dataset adapter；不得根据 004 改窗口、aux、loss、训练日程、seed 或建立 TPCR-v0.3。B0/A1/M6 不在 004 重跑。




- 判读：004 是辅助外部诊断。普通正、平或小幅负差均不作为 TPCR-v0.2 的严格性能门；若 mean `P1-B1 <= -5.0 pp` 且至少 4/5 seed means 非正、6/9 subject means 非正，则仅阻断跨数据集一致性／一般化主张，并要求诊断，不推翻 001 的 exact discovery finding。




- 权限：本次只冻结 S7 范围与合同，未创建 004 训练、预测或性能结果；`authorized_run_level=none`。正式文件见当前 cycle 的 `_work/refine/TPCR_V0_2_S7_CONFIRMATION_SCOPE_REFINEMENT.md`、`_work/review/TPCR_V0_2_S7_CRITICAL_REVIEW.md`、`_work/plan/TPCR_V0_2_S7_CONFIRMATION_EXECUTION_PLAN.md` 与 `_work/explain/TPCR_V0_2_S7_WAIT_WHAT.md`。









## 待补充决策









后续应继续补充：




- 目标投稿期刊范围




- 主数据集选择




- 指标与协议统一方式




- 第一版创新点最终收敛结果




- baseline 对照组最终名单




## D-091：冻结 RCCF-Core-v1 discovery 合同并授权分阶段自主执行









- 日期：2026-08-13




- 决定：冻结 `P1` 对 `B1-DR` 的 `mieeg-uep-v1.0 / tp-dsainet100-v1 / exact-paired` discovery 合同，进入 S5。




- selection：seeds 0–1 × 9 subjects × `P1/B1-DR`；正信号要求 18 对均值至少 `+1.0 pp`、两个 seed 均为正、至少 6/9 subjects 为正，并通过 B0 安全规则。




- confirmation：仅在 screen positive 后使用 untouched seeds 2–4；不得据此继续选择版本、阈值或控制。




- B0 边界：先做历史 45-row no-op；若唯一失败是旧运行缺少 inner-split provenance，则补跑 selection 范围 B0，属于合法分母修复而非科学改版。




- 授权：用户要求按工作流跑完 RCCF，中间人工审阅由 Codex 自审；若精确 RCCF 无法修复或严格 NO-GO，则转 RBSF supporting line。




- 证据边界：D0/check/smoke 只证明构造、协议或链路；pilot 是 discovery，只有 untouched confirmation 才能升级稳定性口径。




## D-092：RCCF-Core-v1 在完整 paired pilot 上 NO-GO，并转 RBSF supporting line









- 日期：2026-08-13




- 完整性：P1/B1-DR 各 18 个唯一 rows、checkpoints、predictions；36 份 prediction 的 ACC/Kappa/Macro-F1 重算一致，split/q/对应初始化 SHA-256 配对一致。




- 结果：B1-DR ACC `57.263%`，P1 `57.128%`，差 `-0.135 pp`；seed 差 `-0.540 pp` 与 `+0.270 pp`，只有 4/9 subjects 的 two-seed mean 为正。




- 决定：触发冻结的 `mean(P1-B1-DR) <= 0` no-signal。关闭精确 RCCF-Core-v1，不做 projector、normalization、width、loss、branch-order 或超参救援，不触碰 confirmation seeds 2–4。




- 边界：历史 B0 缺少 inner-split fingerprints，只作 context；主 no-signal 不依赖 B0。D0/rank 审计修复和 SwanLab GBK 降级均已记录，前者不改阈值，后者不影响本地训练结果。




- 路由：按用户预授权转入保留的 RBSF-v1 finding-focused supporting line；必须建立独立 cycle 和 S4 合同，不继承 RCCF 或 BBF 的实验权限与结论。




## D-093：RBSF-v1-FF 修复 detector scale validity，但因 A1 公平性在 D0 关闭









- 日期：2026-08-13




- D0 scope：seed 0 × 9 LOSO targets，无训练。




- 通过：gain challenge disagreement/equivariance 均为 0；target occupancy `16.42%–18.88%`，source-relative ratio `0.932–1.117`；slow-envelope、non-fixed-top-k、event、edge/channel 与 reconstruction 均通过。旧 D-ABS 的 A08 target occupancy `42.64%` 在 RBSF 下为 `18.88%`。




- 失败：A1 circular-shift 后前后 100 ms 边界 occupancy 相对 P1 差 `2.42–4.62 pp`，9/9 超过冻结 `2 pp`。occupancy/duration/RMS 虽匹配，但位置分布伪迹使 timing attribution 无效。




- 决定：这是 control 科学设计失败，不是实现/数值错误。关闭精确 RBSF-v1-FF，不运行 B0/check/smoke/pilot；C0 只保留构造性 partial evidence，C1/C2 未测试关闭，C3 继续禁止。




- 后续边界：若重开必须新建 matched timing-destruction control、版本和 cycle；不得修改 shift 后沿用 v1-FF，亦不得继承本轮 D0 PASS。









## D-094：TPCR-v0.1 在完整 paired discovery pilot 中 NO-GO









- 日期：2026-08-13




- 构造与链路：`TPCR-v0.1` 的 18-fold D0-C/P/N、四臂 check/smoke 均通过；S4 在任何结果产生前把仅有一个内部边界的 A1 `[3,4)` 静态修复为同宽双边界 `[1,2)`，未读取标签或性能。




- 完整性：B1/P1 各有 18 行、18 checkpoint、18 prediction；36 份预测的 ACC/Kappa/Macro-F1 可精确重算，`y_true` 与冻结数据标签一致，split 和对应初始化 SHA-256 逐对一致。




- 结果：B1 ACC `57.552%`，P1 ACC `57.533%`，差 `-0.019 pp`；两个 seed 分别 `-0.058/+0.019 pp`，仅 `4/9` subjects 的双 seed 均值为正。




- 决定：同时触发 `mean(P1-B1) <= 0` 和 `positive subjects <= 4/9` 的冻结 no-signal 条款，关闭精确 TPCR-v0.1；不进行后验窗口、宽度、损失或编码器修改。




- 停止边界：A1/B0 discovery 补臂不能挽救主效用失败，故不再运行；S7/S8 与 BNCI2014004 confirmation 未触碰。按用户授权停止，不自动切换下一方向。









## D-095：冻结 TPCR-v0.2 非对称 Event-Main / Context-Aux Discovery Idea Contract









- 日期：2026-08-13




- 决定：用户明确冻结 `TPCR-v0.2`。该对象建立独立 cycle `2026-08-13_dbconformer_asymmetric_event_context_routing`，继承但不改写 D-094：TPCR-v0.1 的两个完整同构 encoder no-go 保持有效，v0.2 不属于其 rescue 或扩大实验。




- 冻结接口：BNCI2014001 的 fixed `[2,3)` s event 只进入 DBConformer native temporal main（`D=40/depth=2`）；full raw 始终进入 native spatial path（`D=40/depth=2`）；exact context complement 进入参数独立的 lightweight temporal auxiliary（`D=20/depth=1/bottleneck=10`）。只做固定 concat 和单一 CE head，不加入 dynamic/learnable mask、attention、gate、FiLM、interaction、auxiliary loss 或预训练。




- 容量与对照：aux 预估 `7,210` 参数，为 native temporal-main path 的 `16.64%`；B1/P1/A1 总参数预估 `101,663` 且必须 exact-equal，D0 仍须以实际构造复核。B1=`main(full)+spatial(full)+aux(context)` 是 primary capacity baseline；P1=`main(event)+spatial(full)+aux(context)`；A1=`main(context)+spatial(full)+aux(event)` 是 assignment-swap；B0 原 DBConformer `93,813` 参数只作安全锚点。




- Discovery 门槛：BNCI2014001 seeds 0–1 × 9 LOSO subjects 为 selection scope。P1 必须同时在 paired mean、两个 seed 和至少 5/9 subject means 上优于 B1，并在 paired mean 与至少 5/9 subjects 上优于 A1；同时 `P1-B0 >= -0.5 pp` 且无 subject `P1-B1 <= -10 pp` collapse。无效 control、check/smoke 或 partial rows 不参与信号判定。




- 债务与边界：当前只完成 S2 T0/self 冻结与 `wait-what` 七点解释，没有实现或性能证据。S3 仍需正式碰撞分级和临界评审；context-zero/shuffle 与 path-use diagnostics 是正信号后的机制债务。不得声称 event 是 MI onset、context aux 必要、event/context 已解耦、generic dual branch/input decomposition 有新颖性，或形成 paper-facing claim。




- 防火墙与权限：BNCI2014001 已参与 failure map、TPCR-v0.1 与宿主诊断，只能 discovery。具体 confirmation scope 暂不绑定，S7 前必须审计所有 selection exposure 后严格冻结；此前禁止访问任何 confirmation candidate。当前 `authorized_run_level=none`，不实现、不运行 D0/check/smoke/pilot/full；下一门禁为 S3。









## D-096：TPCR-v0.2 以弱新颖 supporting candidate 通过 S3









- 日期：2026-08-13




- 查新边界：BraSTORM 已占据 EEG 输入级时空分解与独立双编码器的高层叙事；DBConformer 及大量 MI-EEG 工作已占据 temporal/spatial 双分支；time-window selection 与自适应时段研究亦已有长期积累。TPCR-v0.2 不得声称上述通用元素首创。




- 剩余差异：本次聚焦检索未发现同时采用 `event-main + full-spatial + exact-context lightweight aux`，并以前置 `B1` capacity control 和 `A1` assignment-swap 控制分配方向的逐项同构工作。该差异只足以支持组合级、宿主适配型 discovery，不足以支撑独立架构新颖性。




- 临界评审：T0/self 未发现 fatal defect。B1 能隔离 main full/event 的 utility，A1 能检验高/低容量路径的 assignment，但不能排除 occupancy、边界形态、cue ERP、眼动或 hard-crop regularization；正结果仍只允许完整 intervention utility，机制需后续 context/path-use diagnostics。




- 决定：`gate_decision=go`、`s3_verdict=GO_WITH_CLAIM_REDUCTION`、`candidate_role=supporting_candidate`、`novelty_status=weak`。自动进入 S4 合同设计；在 S4 冻结与授权前仍不得实现或训练。









## D-097：TPCR-v0.2 通过 primary 与 A1 direction discovery 门禁后暂停









- 日期：2026-08-13




- 构造与链路：D0-r2 18/18、四臂 check 与四臂 2-epoch smoke 均通过。B0 为 `93,813` 参数；B1/P1/A1 各 `101,663`，main/spatial/aux/head 为 `43,320/43,097/7,210/8,036`；对应初始化、独立存储与 exact complement reconstruction 均通过。




- 完整性：B1/P1/A1 各 18 rows、18 checkpoints、18 predictions；54 份预测的 ACC/Kappa/Macro-F1 从 frozen labels 重算一致，split、对应初始化、runner/model/config hashes 均一致，issues=`0`。




- Primary：B1 `56.067%`，P1 `58.285%`，差 `+2.218 pp`；seed 差 `+1.813/+2.623 pp`，8/9 subject means 正向，最差 `-3.212 pp`，通过冻结 primary gate。




- Direction：A1 `56.424%`，P1-A1 `+1.861 pp`；seed 差 `+0.926/+2.797 pp`，8/9 subject means 正向，通过冻结 assignment-direction gate。




- 口径：当前仅为 `discovery partial-positive`，支持 exact routing 的 utility 与 assignment direction；不证明 MI onset、context 生理意义、context aux 必要性、完整机制或 paper-facing performance。




- 暂停：用户明确要求 A1 门禁结束后暂停。未启动 B0 safety、aux-zero/shuffle path-use、S7 或 confirmation；`authorized_run_level=none`。恢复时唯一合法下一步是按原合同运行 B0 18-unit safety anchor，不得先改版或访问 confirmation candidate。









## D-101：S7 改为 claim-specific confirmation，并将 BNCI2014004 默认降为辅助压力测试（2026-08-14）









- 通用决定：`proposed-research` 的 S7 不再把“选择一个不同数据集”当作确认的必要或充分条件。每个范围必须绑定 Claim IDs、outcome exposure、paired denominator、允许适配、读取结果前的判断规则和负结果的精确后果，并标记为 `primary_confirmation`、`frozen_replication` 或 `auxiliary_stress_test`。




- 暴露边界：在参与版本、阈值或控制选择的数据集上增加新 seed，只能增强冻结复现和随机性稳定性，不能消除数据集级选择污染。若当前没有与主 claim 匹配的未触碰范围，保留 `confirmation_debt` 并限制口径，不用不匹配的数据集强行替代。




- 001/004 覆盖：对以 BNCI2014001 为主且依赖空间信息的模块，BNCI2014004 默认只作 3 通道、二分类、五 session 的辅助压力测试。004 内只看 proposed-baseline exact-paired delta；普通正、平、小幅负或高方差不否决 001。只有预冻结、按 004 自身波动校准且 mean/seed/subject 多层一致的严重退化，才限制跨数据集一致性/一般化 claim 并触发不改版诊断。




- 严格门禁：只有 intended claim 明确包含低导联鲁棒性、montage invariance 或跨数据集一般化时，004 才对相应 claim 成为严格门。更全面外部数据集不是每个 cycle 的固定 S7 要求，但释放高密度空间机制或广泛泛化主张前，必须解决相应 confirmation debt。




- 兼容边界：本决定只更新通用 Skill、项目工作流和后续 S7 记录格式，不回改任何已冻结 cycle、既有 TPCR-v0.2 S7 数值阈值、科学结论或运行权限。









## D-102：Proposed 远端实验委托项目自主调度，且新规则不追溯在途 Bundle（2026-08-14）









- 分权：`proposed-research` 只冻结科学范围、task matrix、授权、停止规则和证据角色；项目 `REMOTE_WORKFLOW.md` 负责环境、Bundle、并发 pilot、lane 决策、提交、状态追踪、回拉、SHA-256/manifest 核验与 intake。不得在通用 Skill 内复制项目调度算法或固定 lane 数。




- 选择：多 subject/seed/fold/ablation 的远端 pilot/full 在项目存在自主入口时必须走该入口。lane 依据同模型、同任务形状的稳定端到端吞吐选择；GPU 利用率、显存和主机资源只作诊断与候选生成，不单独构成科学或调度失败，也不授权修改 batch、epoch、数据、split 或模型。




- 完整性：新 Bundle 的 `bundle_scheduler_contract.json` 与 `remote_execution_plan.json` 必须可机器解析；远端 staging 对调度合同执行 schema/算法/结构校验。编排生命周期必须持续到 `status -> fetch -> verify -> intake`，不能把已提交或进程退出写成完成。




- 非追溯边界：本决定只适用于修改后新建的 Bundle。已冻结、上传、运行、已结束待回拉或正在 full 的 TPCR-v0.2 r2 及其他 Bundle 继续使用原 plan、候选 lane、task plan 和报告哈希链；不重打包、不重启、不改变本轮 90-unit full。









---









## D-103：冻结 LCUS-v0 为独立模块级解耦周期，本地完整性后暂停远端（2026-08-14）









- **对象**：用户明确将下一机制定为 LCUS（用户写作 LUCS）：在冻结 DBConformer 入口插入无偏置 1×1 通道混合 `z1=Wz`、`z2=z-z1`，temporal 吃 `z1`，spatial 吃 `z2`。这是模块级读法，不是 SFRF/形态学/HPSS 手工视图，也不是 PTSR/CBI。




- **周期**：`2026-08-14_dbconformer_learned_complementary_unmixing`。不改写、不接管 TPCR-v0.2。中间评审由用户授权为当前会话自审。




- **合同**：P1 对 B0 与冻结随机 N1；N2 只作塌缩检测。发现门槛为双 seed LOSO 上 `P1-B0` 与 `P1-N1` 均 `≥ +0.5 pp`、至少 6/9 subject 正向、无新的 ≤−10 pp collapse。




- **本地状态**：D0 36/36、check 容量 `93813/94297`、smoke 2 epoch 链路通过。这些不是性能证据。




- **权限**：用户已于 2026-08-15 授权上传。r1 check 因 Bundle 缺少上游 `DBConformer.py` 失败并保留。r2 补入该文件后上传成功，远程 check 通过；scheduler pilot `2026-08-14_lcus_v0_bnci2014001_uep_loso_ccmu_pilot_r2_w1` 已提交。这些都不是发现屏性能证据。




- **S6D（2026-08-15）**：54/54 完整配对后判定 `ambiguous`。subject-mean `P1-B0 = +1.013 pp` 过 +0.5 门槛，但 `P1-N1 = +0.193 pp` 不过，且仅 5/9 subject 的 `P1-B0 > 0`。无 ≤−10 pp collapse。不授权 S6R，不改模块救援。这不是论文性能结论。




- **bounded diagnostic（2026-08-15）**：用户授权在本 cycle 做一次无改动诊断。18 个 P1 checkpoint 的 `W` 未塌向 `I`（中位相对距离 0.49，残差 pair-share 0.34），也未停在 `0.5 I`（0.65）。S7 对 B0 的大增益几乎同样出现在 N1。`signal_status` 仍为 `ambiguous`，本周期诊断额度用完。




- **Family Re-entry Review（2026-08-16）**：一次性重入审查把可定位 bottleneck 收敛为「无约束 `W` 的 18/18 对角增益吸引子（对角≈0.61，非对角 RMS≈0.063），实现的是两路同一波形的增益分配，而不是通道解混」。形成待授权 child `OD-LCUS-v0`：唯一科学改动是 `W=0.5I+OffDiag(A)`，对角冻结。




- **Child 创建（2026-08-16）**：用户显式要求建立 child。已创建 `2026-08-16_dbconformer_offdiag_complementary_unmixing`，冻结 OD-LCUS-v0 合同与 S4 inherited-plan，完成 wait-what 与 S3-delta。family 转为 `exploratory / active`，child budget `1/1` 已消耗。父 LCUS-v0 以 `handed_off_to_child` 关闭，`ambiguous` 与 W 诊断不改写、不升级为 child 信号。




- **S5（2026-08-16）**：用户授权实现。单元测试 6/6；D0 45/45；check 容量 B0 `93813` / P1 `+462` / A1 `+22` / N1 `93813`；smoke 仅证明 2 epoch 链路。这些不是发现屏或论文数字。上传前暂停，未建 Bundle。









## D-104：CPDI-v0.2 作为弱新颖性 supporting candidate 完成本地门禁并停在远端 upload 前（2026-08-14）









- **对象与查新边界**：CPDI 保留 DSAINet 完整 Query，只把对方相对公共底座 `a0` 的 raw branch increment 作为 cross-attention K/V，不新增参数。未发现 DSAINet/MI-EEG 精确同构，但 `Delta Attention Residuals` 已预占“用增量代替累积状态以减少冗余”的抽象原则；因此 `novelty_status=weak`、`candidate_role=supporting_candidate`，不得把 delta 原则本身写成主创新。




- **冻结计划**：selection 为 BNCI2014001 LOSO target subjects 0–2，seed 0 首屏、seed 1 条件复制；subjects 3–8、seeds 0–4 的 CPDI outcome 作为同域 primary confirmation 防火墙。主 discovery 门按既有 DSAINet seed-level ACC SD `1.015 pp` 缩放为 `+0.51 pp`，而不是套用通用阈值。




- **D0-N 修订**：v0.1 的 `token_roll_delta` 同时置换 K/V，合成回归显示与 P1 logits 最大差为 `0.0`，属于 attention 共同置换不变导致的退化控制，不是性能失败。预算内 v0.2 只改为 `key_roll_delta`（K 固定 roll 1 token，V 不变）；核心机制、selection、阈值和 confirmation scope 未改，版本预算使用 `1/2`。




- **本地证据**：v0.2 unittest `5/5`、合成 D0 `13/13`、legacy/full logits error `0`、参数 `75,645`、五模式 subjects 0–2 只读 check 和各两步合成 optimizer smoke 均通过。上述仅为实现/链路证据，真实数据 training 未启动，`signal_status=not_tested`、claims 全部 `ineligible`。




- **Bundle 与暂停**：发现 Bundle `2026-08-14_dsainet_cpdi_v0_2_bnci2014001_loso_seed0_s0_2_ccmu_r1` 已本地 prepare/verify，archive SHA-256 为 `80182447a7ce79eb1dc2236eda65132c92ebbb280e124bb7c3fa96f811f099d9`；98 个成员、71 个内部哈希、5-task scheduler pilot 与 15-task full-scope discovery task matrix 均通过，无数据/权重/凭证。默认和沙箱外两次只读 preflight 均对 `[REDACTED_MACHINE]:22` timeout；未发生 upload/stage/submit，周期按用户规则暂停。恢复时先重跑 preflight，不得直接提交或把调度 pilot/full-scope discovery 写成正式 full/confirmation。




- **后续状态更新（2026-08-15）**：用户追加显式授权“推送 CPDI 实验”。服务器 SSH preflight 恢复并通过；同一冻结 Bundle 已成功 upload/stage 到 `[REDACTED_MACHINE]`，控制器回报 archive SHA-256 与冻结值一致，远端 source/plan/data manifest 哈希核对一致。当前仍 `paused_before_remote_check`：未执行 check、scheduler pilot、full、submit 或训练，未产生性能证据。









- **S6D（2026-08-16）**：r1 check 的缺失 import 链失败仅作基础设施记录；r2 在唯一工程修复（补入 `DBConformer.py`）后完成 remote check、lane pilot、full discovery，15/15 rows、外层 archive SHA-256 `ac7dbf0190d8beabf1db6e8f080d8d2d9c02bc193baa91494a85cf1ed0d11b1a` 与 218-file Bundle manifest 均通过。冻结 selection 判定为 `no_signal`：P1-B0 mean `-1.157 pp`、仅 1/3 target 正向，ΔKappa `-1.543 pp`；P1-N1=`-0.231 pp`、P1-N2=`-1.215 pp`，未证明互补内容优于扰动或降幅解释。停止 seed 1、confirmation 和性能驱动修复；这只是否定该精确 DSAINet CPDI v0.2 合同的继续训练路线，不否定一般残差或 cross-attention 方向，也不构成论文结果。









- **Family Re-entry Review（2026-08-16）**：一次性重入审查把可定位 bottleneck 收敛为“raw delta 只相对公共底座 `a0` 定义，未保证相对 receiver Query 是新信息”。结合 `delta < zero_delta`、`delta ≈ key-roll` 的父失败边界与聚焦原始文献，形成待授权 child `CPDI-RCOD-v0.1`：唯一科学改动是把 K/V 换为 stop-gradient receiver-query 参考下逐 token、范数保持的正交 delta；不增加 gate、loss、分支或参数。family 进入 `decision_pending`，budget cost=`1` 但尚未消耗；在用户授权前不创建 cycle、不实现、不运行。若转为 shared-space exchange、learnable gate/正则或改变核心因果论题，则应另建 family。




- **Child 创建（2026-08-16）**：用户显式授权后建立 `2026-08-16_dsainet_receiver_conditioned_orthogonal_delta`，消耗 family budget `1/1`。S2-lite 合同与 S4 inherited-plan 已冻结：B0=full、A0=raw delta、P1=rcod、N1=shuffled-receiver rcod；主门仍为 `+0.51 pp` 且 `2/3` 正向，机制门为 P1-A0 与 P1-N1 均 `>= +0.25 pp`。父精确 cycle 以 `negative_boundary / handed_off_to_child` 关闭。family 现为 `exploratory / active`。未授权实现、D0、上传或训练；不得重开父候选，不得把父数字写成 child 信号。




- **Child S5（2026-08-16）**：用户授权后完成本地门禁。unittest 5/5；D0 16/16；参数 `75,645`；`full` 对 legacy logits 误差 `0`；逐 token cosine `5.12e-8`；范数误差 `1.10e-6`；随机 probe 塌缩率 `0`；共线 probe 走确定性零分支；`query.grad is None`；N1 与 P1/A0 均非等价。四臂 subjects 0–2 只读 check 与各 2-step 合成 smoke 通过。这些不是发现屏或论文数字。上传前暂停，未建 Bundle。




- **Child S6D（2026-08-18）**：r3-full `2026-08-17_rcod_v0_1_ccmu_r3-full-w1` 12/12 完整、四臂 config 去 mode 后哈希唯一，B0/A0 与父 seed0 数字逐格相同。冻结数字门通过：P1-B0 mean `+1.100 pp`（2/3 正向）、P1-A0 `+2.257 pp`、P1-N1 `+1.736 pp`、ΔKappa `+1.466 pp`。但 subject 1 占正增益 93.9%，subject 2 为 `-2.431 pp`，P1-N1 仅 1/3 严格为正且 subject 2 上 P1=N1。按 S6D“不得由单一单位驱动”判为 `ambiguous`，不是 `screen_positive`，也不是 `no_signal`。不跑 seed 1 科学复制、不读 r4-pilot（seed1/s0 的 2-task 调度产物）、不写论文性能或机制 claim。family 进入 `decision_pending`。




- **第二次 Family Re-entry（2026-08-18，seed-1 续证）**：用户事后授权的 seed-1 六行完整：P1-B0 `+2.141 pp`、3/3 正向，约 95% 仍来自 subject 1。相对 B0 的优势类别在两 seed 间不固定，但 subject 1 的预测计数大幅迁移是复现规律。源码定位到正交后的满能量回写 `d_perp * ||d_j|| / ||d_perp||`。形成待授权第二 child `CPDI-UOD-v0.1`：只取消范数保持。第一次 Re-entry 的 `exhausted` 路由被本快照取代为 `decision_pending`；RCOD 的 `ambiguous` 与 S9 关闭不改写。不创建 cycle、不实现、不训练，不释放 claim。




- **Child 结果后 Family Re-entry / S9（2026-08-18）**：只读取 r3 已暴露的 prediction，未读取 r4-pilot。RCOD 相对 N1 的净正确数在 subjects 0/1/2 分别为 `-1/+31/0`；pooled fix-minus-harm 按真实 class 0/1/2/3 为 `+76/-22/-6/-18`，优势进一步定位为 subject 1 / class 0 局部校正，而非跨 subject、跨类别的 receiver-specific 互补。现有产物缺少真实数据上的投影平行分量、范数恢复缩放与 attention 输出可观测量，不能把“类别先验偏移”升级为可归因 bottleneck；soft gate、投影强度、取消范数保持或 class-aware 调节均会成为结果驱动的新科学对象。第二 child extension rule 未满足，family budget `1/1` 已用，因此 `dsainet-cpdi` 路由 `exploratory / exhausted`，RCOD exact cycle 以 `ambiguous / prototype_archive / completed_not_promoted` 关闭。r4-full 恢复进程已在重新连网前停止；seed 1、confirmation 与 claims 均不授权。该结论不是一般 delta、residual 或 cross-attention 的 `no_go`。




- **第二次 Family Re-entry（2026-08-18，seed-1 续证）**：用户事后授权的 seed-1 六行完整：P1-B0 `+2.141 pp`、3/3 正向，约 95% 仍来自 subject 1。相对 B0 的优势类别在两 seed 间不固定，但 subject 1 的预测计数大幅迁移是复现规律。源码定位到正交后的满能量回写。形成待授权第二 child `CPDI-UOD-v0.1`：只取消范数保持。第一次 Re-entry 的 `exhausted` 被本快照取代为 `decision_pending`；RCOD 的 `ambiguous` 与 S9 关闭不改写。不创建 cycle、不实现、不训练，不释放 claim。




- **Agent-led Evidence Search（2026-08-18，新协议）**：用户要求按更新后的 family re-entry 机制重做。快照仍是 `#S6D+seed1`，不得另开科学搜索。四类检索（失败边界、源码缺口、已有可观测性、定向文献）确认同一 UOD，不新造 child。产物：`_work/review/FAMILY_REENTRY_EVIDENCE_REVIEW.md`。Oh et al. arXiv:2505.11881 只支持“正交分量以其自身能量存在”，不能单独成立 child。仍待用户授权创建并扩展 budget。




- **UOD child 创建（2026-08-18）**：用户「创建cycle」后建立 `2026-08-18_dsainet_unnormalized_orthogonal_delta`，family budget 扩为 `2/2`。S2-lite 与 S4 已冻结：B0=full、A0=RCOD、P1=uod、N1=shuffled-unnormalized；主门仍 `+0.51 pp` 且 `2/3` 正向，机制门 `+0.25 pp`，稳定性门为单一 subject 占总正增益 `<70%`。未授权实现或训练。不得把 RCOD 数字写成 child 信号。




- **UOD S5（2026-08-18）**：用户授权后完成本地门禁。unittest 5/5；D0 16/16；参数 `75,645`；`full` logits 误差 `0`；UOD 与 RCOD K 差 `3.53e-3`（确认未回写）；A0 仍范数保持。四臂 subjects 0–2 只读 check 与各 2-step 合成 smoke 通过。不是发现屏或论文数字。上传前暂停。




- **入队不上传（2026-08-19）**：用户明确要求先不上传、加入待实验队列。UOD-v0.1 记为排队实验池 #8：seed0 × 四臂 × subjects 0–2 = 12 units。未建 Bundle，未授权远端 check/pilot/full。




- **远端 12-unit 与 S6D（2026-08-20）**：用户先改授顺序远端执行，后又明确要求分析 UOD r2 并继续流程。`2026-08-19_uod_v0_1_ccmu_r2-full-w1` 12/12 complete，外层 SHA-256 `9d3eff52c22da87bbe57629141a1f765596bd286e43a552adfa03ca0e8add803`，NPZ 重算 ACC 差为 0；B0 对齐 RCOD seed-0 B0，A0 对齐 RCOD seed-0 P1。冻结判定 `no_signal`：P1-B0 `+0.926 pp`（3/3，份额 <70%）、P1-N1 `+3.588 pp` 通过，但 P1-A0 `−0.174 pp` 失败关键门。seed 1、subjects 3–8、S6R 均不授权。T0 self；Codex jury 不可用，claims 保持 `ineligible`。




- **S6M / S9（2026-08-20）**：`review_basis: S6D_direct_exception`，`s6r_status: not_run`。UOD exact cycle 以 `negative_boundary / completed_not_promoted` 关闭。`dsainet-cpdi` 为 `exploratory / exhausted`，budget `2/2`，无第三 child。父 CPDI `no_signal` 与 RCOD `ambiguous` 不改写。这不是一般 delta / 正交 / cross-attention 的 `no_go`。




- **分析性 Family Re-entry（2026-08-20）**：用户要求判断该 family 是否还有继续研究的价值。新快照为 UOD seed-0 12-unit，不同于已消耗的 RCOD `#S6D+seed1`。四类检索 + 已有 NPZ 类别分解：RCOD 在 subject 1 / class 0 上的超额救援（75 vs B0 的 31）在 UOD 上消失（32）；UOD 类别占用仍漂移。同 thesis 单变量（raw / 正交+回写 / 正交不回写）已用尽。结论 `no_reentry_evidence`；family 保持 `exhausted`。不是 `no_go`，也不是新 family。同一快照不得再搜索。









## D-105：TPCR-v0.2 的 BNCI2014004 S7 完成，仅形成辅助外部方向（2026-08-14）









- **完整性**：冻结 90-unit B1/P1 full `2026-08-13_tpcr_v0_2_dbconformer_bnci2014004_s7_ccmu_full_w1_r2` 已完成。回拉前未读取结果；随后 outer SHA-256 `237f362a02d665edad58a2a36a2a05860e17539517ab80722a3228d2bea17531`、1,470 个 tar 成员路径/类型、1,194 个 Bundle manifest 文件均通过。intake 后 prediction-level audit 覆盖 90 个 task/row/prediction/checkpoint，冻结标签重算一致、元数据一致、issues=`0`。




- **冻结判读**：`P1-B1 = +0.152 pp`；3/5 seed mean、5/9 subject 五 seed mean 为正，满足 `supportive_external_direction`。未触发 material external divergence（其冻结条件为 mean `<= -5 pp`、至少 4/5 seed nonpositive 且至少 6/9 subject nonpositive 的合取）。




- **口径与后果**：004 是 3-channel/二分类辅助压力测试；该结果只能支持低导联条件下的方向一致性，不替代 001 四分类 discovery，不证明 22-channel spatial validity、MI-onset 生理或普适跨数据集泛化。无修复、无重跑、无自动下一步；`2026-08-13_dbconformer_asymmetric_event_context_routing` 暂停在下一决策边界。




- **审阅记录**：本会话已获用户授权自审；可用工具中没有配置 cross-model audit/claim reviewer backend，故正式记录为 deterministic + self，而非独立复核。该可用性事实不扩大任何 claim。









## D-106：TPCR-v0.2 完成 S9，只释放范围受限的支持性发现（2026-08-14）









- **释放内容**：`ATPCR-C5` 可作为 BNCI2014004 3 通道、二分类辅助压力测试的支持性发现进入写作：P1-B1 `+0.152 pp`，3/5 seed、5/9 subject mean 为正，90/90 单元完整，未触发 material external divergence。事实性结构、对照与审计路径可以描述。




- **未释放内容**：BNCI2014001 的 P1-B1 `+2.218 pp` 与 P1-A1 `+1.861 pp` 属于 selection-used discovery；aux-zero/shuffle 只证明 auxiliary path 被使用。`ATPCR-C2/C3` 不进入论文正式性能或机制结论；`ATPCR-C4` 只允许有限组合级定位，不能声称 standalone novelty。




- **论文角色**：TPCR-v0.2 定位为可供主创新方向适配的 supporting module 或补充消融，不独立承担 headline innovation，也不声称 MI onset 生理、context 语义、22 通道四分类确认或普适跨数据集优势。




- **终止状态**：周期 `2026-08-13_dbconformer_asymmetric_event_context_routing` 在 S9 关闭，`authorized_run_level=none`。写作交接为 `_work/writing/TPCR_V0_2_S9_EVIDENCE_HANDOFF.md`；若将来补主确认或实质改造，须由用户显式重新绑定或建立新周期。









## D-108：TPCR-v0.2 同 fingerprint evidence-continuation 获授权（2026-08-14）









- 用户显式授权建立 `2026-08-14_dbconformer_tpcr_v0_2_evidence_continuation`，仅补足父 cycle `2026-08-13_dbconformer_asymmetric_event_context_routing` 未完成的最小 S6R。




- 科学对象、数据、UEP LOSO、100 epoch、窗口、四臂定义、容量、初始化与 source-only 边界保持 TPCR-v0.2 原样；父 001 discovery 和 004 auxiliary evidence 均不升级。




- 预冻结范围为 BNCI2014001 seeds 2-4 × subjects 0-8 × B0/B1/P1/A1，共 108 个训练单位。所有臂必须在同一非性能选择的远端 `mieeg` 环境完成，新增结果一律标记 `frozen_replication`。




- 先做 provenance/D0/check/local smoke；通过后才可创建远端 Bundle、remote check/pilot/full。S6R 完成后只到 family 决策边界，不自动开启 child、S7Q、CO/CV、004 重跑或 six-cell benchmark。









## D-107：proposed-research 升级为 family/cycle 双层成熟流程（2026-08-14）









- **决定**：一个 cycle 固定对应一个精确 scientific candidate；任何由科研结果驱动的结构、接口、路由、loss、window、fusion 或核心机制修改，必须新建显式 child cycle。工程修复仅可恢复原冻结合同。




- **新增阶段**：S6D 只筛初始信号；S6R 以最小 frozen replication 判断是否值得继续投入；S6M 在 family 预算内提出 child candidate，child 必须重新走 S2-lite/S4/S5/S6D/S6R；S7Q 冻结 benchmark candidate；S8B 与 S8C 分别管理统一 benchmark 与 claim-specific confirmation，可共享完全一致的运行产物。




- **统一 benchmark**：MI-EEG primary method candidate 在 paper handoff 前默认覆盖 BNCI2014001/BNCI2014004 的 CO/CV/LOSO × 5 seeds，并与 exact-compatible B0 进行项目协议下的比较。coverage 完整不等于六格必须全正；每格必须预定义 primary、secondary 或 stress-test 角色。




- **状态与迁移**：`status: closed` 仅关闭 exact cycle。新增轻量 `experiments/records/PROPOSED_FAMILIES.md` 作为 family 唯一状态源，及 `PROPOSED_RESEARCH_MIGRATION.md` 说明旧 cycle；不重写任何历史数值、S9 handoff、claim、运行权限或在途 Bundle。TPCR-v0.2 迁移为 `prototype_archive`，其 family 为 `promising`，不等同 final/paper-ready。




- **停止规则**：family 的 maturation budget 默认先允许 1 个 child；重复失败或预算耗尽进入 `exhausted`，决定性假设否定才进入 `no_go`。重新进入必须有新的 defect、机制证据、文献增量或因果解释，并由用户明确授权。









## D-109：S6R 后必须完成 Family Maturation Review（2026-08-15）









- **问题与修复**：v4.0 将 `replicated_positive` 同时用作 S7Q 性能晋级条件和 S6M maturation 资格，导致未达到稳定性能门槛的 exact candidate 可能绕过 family-level 判断直接进入 S9。v4.1 将两者拆开：`replicated_positive` 仍是直接 S7Q 的严格条件；任何完整、可判读的 S6R 则必须进入 S6M。




- **S6R 口径**：记录 evidence validity、performance replication、mechanism/control evidence、conditional pattern、bottleneck 与 S7Q eligibility 六个独立维度。`incomplete/invalid` 返回 repair/hold；未通过性能门槛只阻断当前 candidate 的 S7Q，不自动成为 family `exhausted/no_go`。




- **S6M 路线**：family review 在 `direct_s7q`、`diagnosis_driven_child`、`bounded_diagnostic`、`pause`、`exhausted` 与 `no_go` 中选择一项。child 必须由机制/规律锚点和单变量、可证伪的 bottleneck 假设支撑，仍须用户显式授权；每次 review 最多允许一次不改 candidate 的 bounded diagnostic。




- **历史兼容**：TPCR-v0.2 S6R 的原始验证结果与冻结 no-signal 判定均保留。新增回溯 S6M review 只澄清该 candidate 未达 S7Q、family 仍有受控诊断价值；不创建 TPCR-v0.3、不改变任何 Claim、协议、远端 Bundle 或运行授权。









## D-110：显式启动 PCSR（Pre-Collapse Spatial Replay）独立周期（2026-08-16）









- **对象**：用户从 `idea-stage/IDEA_REPORT.md` 最新推荐序第 1 项显式选定 PCSR。精确科学对象是：DSAINet 主路仍坍缩 C→1，把被丢弃的 `(B,f1,C,T)` 对齐后作为 Intra/Inter 额外 K/V。




- **周期**：`2026-08-16_dsainet_pre_collapse_spatial_replay`，family `dsainet-pcsr`。不接管、不读取 `dsainet-cpdi`。禁止并入 MCSAT、第三支、每尺度空间 encoder、SNIT/TCDA/PKMB/WPOI。




- **托管授权**：当前会话按流程自动推进到需要上传服务器前暂停；中间审阅为 T0 `self`。卡住且无法修复则暂停退出。




- **计算**：S1 无 compute。可选侧化 probe 仍未单独授权，保留为机制债务。




- **本地 S5（同日）**：`PCSRDSAINet` 零参数适配器通过 unittest `5/5`、合成 D0 `16/16`（`off` logits 误差 `0`，参数 `75,645`）、五模式合成 smoke 与 subjects 0–2 只读 check。首轮 D0 发现加 pos 后再 roll 的 N2 对 attention 置换不变，已改为加 pos 前 roll。




- **S6D（同日续）**：R003 full `2026-08-16_pcsr_v0_1_ccmu_r2-full-w1` 已 fetch/verify/intake（外层 SHA-256 `61dea2da31b7223508c710763626c61d55fd822d4e7336e5b3976566a74c39d7`，12/12）。`mean(P1-B0)=-0.347 pp`，仅 1/3 subject 正向，P1 均值弱于通道打乱。冻结门判定 `no_signal`。不授权 seed 1、A1 或性能驱动改版。claims 仍 `ineligible`。这不是论文结论。




- **Family Re-entry（同日）**：用户授权一次不建 cycle 的审查。构造上索引轴 AdaptiveAvgPool 四个 bin 均左右混叠，与 `P1−N1=−1.042 pp` 同向。写出 ready child PCHR：只用事先冻结的左/中/右均值替换该池化。同一证据快照不得再审。




- **Child 已建（同日）**：用户显式「创建cycle」。精确 ID：`2026-08-16_dsainet_pre_collapse_hemisphere_mean_replay`。S2-lite / wait-what / S4 已冻。不继承父信号。




- **PCHR S5（同日）**：用户授权 S5。`PCHRDSAINet` 仅替换 C 轴为冻结 L/M/R 均值。unittest 5/5、合成 D0 14/14（`off` logits 误差 0，参数 75,645，`S=(B,3,31,40)`）、五模式只读 check 与合成 smoke 通过。




- **PCHR S6D/S9（2026-08-17）**：r3-full-w1 12/12，`mean(P1-B0)=-2.488 pp`（0/3 正向），`P1-N1=-1.273`，`P1-N2=-1.852`。`no_signal`，child 否证成立。精确 cycle S9 负边界。无论文 claim。




- **第 2 个 child PCRR（同日续）**：用户要求按前两版经验构建第三版。新快照 Re-entry 定位：两版都回放整张 `pre`，P1 均弱于通道打乱，换分组更差，故瓶颈在“回放内容是主路回声”而非左右混叠。用户授权后建立 `2026-08-17_dsainet_pre_collapse_residual_replay`，family child budget `2/2`。唯一改动：`stop-grad` 空间卷积通道零空间残差替换 raw `pre`；分组保持 PCSR 的 `AdaptiveAvgPool(C→4)`。




- **PCRR S6D/S9（2026-08-19）**：只认 `2026-08-19_pcrr_v0_1_ccmu_r4-full-w1-retry`（12/12，archive `6e2be078…2432`）。`mean(P1-B0)=-1.678 pp`（1/3 正向），`P1-N1=+2.604`，`P1-N2=+2.025`。`no_signal`（主门未过；对照门通过）。精确 cycle S9 负边界。无论文 claim。失败的首轮 `...-full-w1` 不并入。




- **Family Re-entry（同日续）**：用户要求在 PCRR 新快照上诊断能否继续本 family。三版仍均为 `no_signal`。新锚点：残差内容优于打乱，失败收窄到 flatten 的 extra K/V。写出 ready child PTAR。




- **PTAR 已建（同日续）**：用户「做一下PTAR」。精确 ID：`2026-08-19_dsainet_pre_collapse_time_aligned_residual`。family child budget `3/3`。唯一改动：PCRR 残差按时刻对齐为 extra K/V；B1=`time_pool` 同长度对照。




- **PTAR S6D/S9（2026-08-20）**：只认 `2026-08-19_ptar_v0_1_ccmu_r1-full-w1`（15/15，archive `7ceaa9ef…54b0d4`）。`mean(P1-B0)=-0.058 pp`（1/3 正向），`P1-B1=+1.447`，`P1-N1=+0.868`，`P1-N2=+0.463`。`no_signal`（主门未过；P1>B1 仅诊断）。精确 cycle S9 负边界。family `dsainet-pcsr` extra K/V 线 exhausted。无论文 claim。









## D-111：family/cycle 收口语义与轻量交互分层（2026-08-16）









- **问题**：仅用 `paused` 或单一 family 状态无法说明 cycle 已关闭后 family 的科研含义、child 为什么没有建立、以及用户可否继续；S9 容易被误解为方向关闭。




- **决定**：family 状态拆为 `family_maturity`（科学发展）和 `family_route_state`（下一步路径），`paused` 必须附 `pause_class`；另单独记录 `child_readiness`、阻塞缺口和 `family_falsification_coverage`。exact cycle 在关闭时记录 close reason 及 family 快照。




- **路由**：ready child/diagnostic 为 `decision_pending`，只等用户授权；无 child 但未充分证伪为 `paused/evidence_gap`，用户可请求一次不建 cycle、不授权计算的 Family Re-entry Review；只有预算/重复失败或核心论题决定性失败才进入 `exhausted/no_go`。




- **交互**：Agent 仍以结构化合同和单一状态源行动；仅在 milestone 与 decision 从已绑定字段生成简短中文桥接，说明 exact candidate、family 含义、child readiness、用户选项与 non-claim。routine 不重复合同、不增加常驻上下文或新 Skill。




- **范围**：v4.2 不改 S0–S5、S8B/S8C、UEP、远端调度、历史结果、现有 Bundle 或任何运行授权。既有 family 仅做非破坏性字段迁移。









## D-112：授权 LCUS/PCHR 发现屏前置并建立排队实验池（2026-08-16）









- **授权**：用户要求"先为 lcus 和 pcsr 做好 full 实验前的前置实验，到需要跑 full 实验前停止"。边界解释为：冻结 `remote_execution_plan.json`、构建并上传远端 Bundle、完成远端 check（fetch/verify/intake）；不提交任何 pilot/full，不产生 scheduling_decision。




- **OD-LCUS-v0**：Bundle `2026-08-16_od_lcus_v0_dbconformer_bnci2014001_loso_ccmu_r1`（150 文件，sha256 `8fa68e5e…f6273`）上传 [REDACTED_MACHINE]；远端 check `2026-08-16_od_lcus_v0_ccmu_r1-check`（GPU 0）四臂通过，容量合同与本地一致（`93813/94275/93835/93813`），`training_executed=false`。




- **PCHR-v0.1**：首轮 Bundle r1 因打包遗漏 `scripts/diagnose_pcsr_dsainet_d0.py`（`scripts.` 包内依赖）远端 check 失败；r2 补齐后（45 文件，sha256 `5c6dc28d…93ab`）check `2026-08-16_pchr_v0_1_ccmu_r2-check`（GPU 1）通过：远端 D0 14/14、四模式 split check 各 3 subjects，训练未执行。r1→r2 为工程修复，科学对象、合同与任务面未变。




- **排队实验池**：`PROPOSED_FAMILIES.md` 新增全局"排队实验池"段，只记录队列状态与启动授权缺口，不记录结果。当前池内两项：OD-LCUS 72-unit 发现屏（B0/P1/A1/N1 × seeds{0,1} × 9 targets）与 PCHR 12-unit 发现屏（四模式 × seed0 × subjects 0–2），均冻结 pilot 任务面，等待用户显式授权启动。




- **非声明**：本轮所有 check 均不构成性能证据；`signal_status` 保持 `not_tested`；SATR-v0.1 与 RCOD-v0.1 不在本池（缺远端前置）。不改变任何既有负边界或 family 结论。









## D-113：OD-LCUS-v0 发现屏判读 no_signal；顺序屏流水线推进（2026-08-17）









- **OD-LCUS-v0 S6D**：72-unit 成对屏（`results/logs/remote/2026-08-16_od_lcus_v0_ccmu_r2-full-w1-retry`；首 full 因 `p1_s1_t0` SIGSEGV 失败、部分产物保留且性能未读，判读只认 retry 完整 72 行）按预冻结门槛判读 **`no_signal`**：`mean(P1-B0)=-0.936 pp`（2/9 正向）、`mean(P1-A1)=+0.029 pp`、`mean(P1-N1)=+1.707 pp`（7/9 正向）、无 ≤−10 pp 塌缩；命中 `mean(P1-B0)≤0` 与正向 subject ≤4/9 双条件。C1 不成立，C2 不进入判读（仅诊断记录：可学非对角优于冻结随机非对角，但整体输给 raw baseline 与对角-only）。




- **S6M / S9（2026-08-17 复核）**：独立重算 72 行与上条一致，写成 `SIGNAL_DECISION.md`。S6M 路线为 `pause/evidence_gap`：无 S7Q、无 ready 第二 child，但 child 给出了新诊断（强制混合有害且不优于对角吸引子），故不是 family `no_go` 或自动 `exhausted`。精确 cycle 以 `negative_boundary` 关闭。1×1 空间互补解混可与父 LCUS-v0 合读为 class-level 负边界。用户可请求 Family Re-entry Review 或行政归档；不自动开第二 child，不得把 P1−N1 写成 family 信号。




- **同 family 新 cycle TCUS-v0（2026-08-17）**：用户要求综合两轮发现并建立新方向。已创建 `2026-08-17_dbconformer_temporal_complementary_unmixing`：depthwise k=9，中心头冻结 0.5，只学旁瓣，无通道混合。这不是第二 child。S2/S4 已冻，wait-what 已完成；不授权实现或训练。前两轮数字不升级。




- **TCUS-v0 S6D / S6M / S9（2026-08-18）**：r2-full-w1 72/72 独立重算为 `no_signal`：P1−B0=`−0.415 pp`（3/9 正向）、P1−A1=`−0.318 pp`、P1−N1=`−0.058 pp`。不授权 S6R。精确 cycle 以 `negative_boundary` 关闭。family 暂停为 `paused/evidence_gap`：线性互补入口拆分在空间 1×1 与短时间 FIR 上均无发现信号；无 ready 下一 cycle。不得把 TCUS S0 的 +5.47 pp 或前两轮数字写成正信号。




- **Family Re-entry（2026-08-18）**：一次性重入把三轮共有瓶颈收敛为「互补变换一直被送进主导的时间路」。ready 新 cycle 为 `ACUS-v0`：时间路固定吃 raw，空间路吃 `z−Wz`。不是第二 child，不重开两路都吃变换。family 进入 `decision_pending`；用户授权前不创建 cycle、不实现、不运行。




- **ACUS-v0 创建（2026-08-18）**：用户显式要求创建 cycle。已建立 `2026-08-18_dbconformer_asymmetric_complementary_unmixing`，冻结 ACUS-v0 合同与 S4，完成 wait-what 与 S3-delta。family 转为 `exploratory / active`。当前不授权实现、D0、上传或训练。前三轮数字不升级。




- **ACUS-v0 S5（2026-08-18）**：用户授权实现。单元测试 4/4；D0 36/36；check 容量 B0 `93813` / P1 `+484` / N1 `93813`；smoke 仅证明 2 epoch 链路。这些不是发现屏。上传前暂停。




- **ACUS-v0 S6D / S6M / S9（2026-08-20）**：r2-full-w1 54/54 fetch/verify/intake 后独立重算为 `no_signal`：P1−B0=`−0.482 pp`（4/9 正向）、P1−N1=`−0.145 pp`。不授权 S6R。精确 cycle 以 `negative_boundary` 关闭。当时 family 暂停为 `paused/evidence_gap`：线性互补入口在两路变换与保护时间路两种赋值下均无发现信号。不得把任一轮单点写成正信号。




- **Agent-led Family Re-entry Evidence Search（2026-08-20）**：用户要求只分析、判断 family 是否还有研究价值。快照为 ACUS `#SIGNAL_DECISION`，现已消费。四通道检索（失败边界、插入点、D0 可观测性、定向文献）未产生 in-family child 或判别性诊断。N1 空间 pair-share 约 `0.83–0.88` 且 N1−B0=`−0.338 pp`，故「保护时间路 + 非退化互补残差」已被检验，不必再拆 P1 训练后 `W`。EEGNet 1×1 与 BraSTORM 输入双流只重复弱新颖债务。结果 `no_reentry_evidence`；family 改为 `exploratory / exhausted`。不创建 cycle、不改代码、不训练、不并入 TPCR/CBI/PTSR。这不是一般互补/残差/空间恢复的 `no_go`。产物：`experiments/records/2026-08-18_dbconformer_asymmetric_complementary_unmixing/_work/review/FAMILY_REENTRY_EVIDENCE_REVIEW.md`。同一快照不得再搜索。




- **用户顺序授权（2026-08-16 深夜）**：LCUS 完成后按 PCHR → SATR → RCOD 顺序跑完四个 S6D 屏，等待期静默。SATR 补齐冻结合同内 `--mode screen` 训练入口（本地 2-epoch 验证通过）；SATR/RCOD Bundle 已冻结上传（`2026-08-17_satr_v0_1_…_r1` / `2026-08-17_rcod_v0_1_…_r1`）。




- **基础设施**：服务器网络两度中断（Tailscale 单向死，rx=0；服务器未重启，uptime 证实），训练与结果包不受影响；为此新增 `scripts/remote/ccmu_outage_sequencer.ps1`（提交前探测远端状态防重复 RunId、等待期容忍任意断网、回拉带重试），PCHR 及后续 SATR/RCOD 屏改用该驱动器。




- **非声明**：本条不改变父 LCUS/PCSR/CPDI/TPCR 既有边界；PCHR/SATR/RCOD 未读任何性能结果。









## D-114：SATR-v0.1 S6M 收口 TPCR family 的有限成熟预算（2026-08-18）









- **完整性与 primary**：仅接受 `2026-08-17_satr_v0_1_ccmu_r2-full-w1-retry4`；前两次不完整远端 run 不混入判读。retry4 为 36/36 B1/P1、seeds 5/6、subjects 0–8 的 exact-paired 单元，预测、ACC 重算、配对标签、split/init hash 和回拉校验均通过。P1-B1 `+1.263 pp`，两 seed 均正，但 two-seed positive subjects 为 `4/9`。




- **exact candidate**：按冻结 `positive subjects <=4/9 -> no_signal -> S6M` 条款，SATR-v0.1 不进入 S6R、S7Q、benchmark 或 claim release。B2/A1/M1/N1/B0 controls 的前置 `screen_positive` 未满足，故不运行且不得用其、额外 seed 或结构改动救回。




- **family 路线**：SATR 是 TPCR 已消耗的唯一 diagnosis-driven child（budget `1/1`），但未产生可归因的新 bottleneck；既有 bounded diagnostic 也已消耗。因此 family 记为 `exploratory / exhausted`，而非 `no_go`：这只停止当前 family 内的有限投入，不外推为所有 event/context、双分支或输入路由研究无效。




- **后续边界**：下一步可执行 S9，将 exact SATR cycle 关闭为 `negative_boundary / completed_not_promoted`。在 genuinely new evidence snapshot 与新的明确授权前，不重开 TPCR-v0.1/v0.2/SATR、不跑 SATR controls、不追加 seed，也不以 window/index/stem/capacity/aux/fusion/loss 修改建立第二 child。




- **审查限制**：外部 Grok 只读复核因会导出私有合同和结果而被安全策略拒绝，未伪造独立背书；S6M 路由仅依赖冻结 no-signal 门限与本地机械完整性 intake。









## D-116：EFSR-v0.1 作为独立 DSAINet scale-routing 周期完成本地 preupload（2026-08-18）









- **方向与继承边界**：用户显式以 TPCR 的 `[2,3)` 选择历史为启发，在 DSAINet 上研究 fine-scale event / coarse-scale full。新周期为 `2026-08-18_dsainet_event_full_scale_routing`、family `dsainet-efsr`；它不是 `dbconformer-tpcr` child，也不继承 TPCR 的性能信号、候选资格或 claim readiness。




- **冻结机制**：官方 tokenizer 只运行一次；在 positional encoding 后对共享 `a0` 做零参数 fixed-support routing。B0=`full/full`，P1=`event-fine/full-coarse`，A1=`full-fine/event-coarse`，N1=`shifted-fine/full-coarse`；`N=31` 时 event indices `15..22`、shift indices `7..14`。否决 dual raw tokenizer，避免 shared BatchNorm 统计污染 coarse 因果身份。




- **本地证据**：adapter 新增 trainable parameter 为 0，B0 对 official logits 误差为 0；最终 D0 14/14、split fingerprints 18/18、真实数据 forward/check 15/15、四 route 各 2 optimizer steps smoke 均通过。首轮 D0 的唯一失败来自对官方 ConvTime `alpha=0` 初始化的错误梯度断言，已修正测试而未改模型或合同。以上仅是 engineering evidence。




- **冻结预算与门**：primary 为 B0/P1 × seeds `{0,1}` × 9 targets = 36 units；只有预冻结四门全部通过才可建立 A1/N1 36-unit control continuation。控制任务表已哈希冻结，但当前 Bundle 不提供其 remote stage，`auto_continue=false`。




- **preupload 结果**：唯一 accepted Bundle 为 `2026-08-18_efsr_v0_1_dsainet_bnci2014001_loso_s01_ccmu_r4`，archive SHA-256 `cd8459b8e87ba0a2769cc9811dfb475036b3358961a434eb210febd261edc6e8`。r1–r3 分别因 remote check 配置层级、未入 manifest 的 `.pyc`、冻结 Bundle 合同覆盖不足而拒绝，均未上传。r4 的 plan/contract、25-file source chain、24-record bytes inventory、4/36/36 task matrix、44 tar entries 与 27/27 file-byte match 已本地通过。




- **权限与 claim**：本轮停在 upload 前；没有 SSH 写入、remote check、pilot/full、SwanLab run 或性能读取。Git Bash `bash -n` 因沙箱和审批额度门槛不可执行，作为 tooling gap 保留；T0/self review 不冒充独立审查。EFSR novelty 仅为 host-specific causal probe，当前所有 performance/mechanism claim 均 `ineligible`。









## D-120：EFSR-v0.1 verified discovery screen 为 ambiguous，关闭精确 cycle 并暂停 family（2026-08-18）









- **回拉完整性**：r4 Bundle 的 remote run `2026-08-18_efsr_v0_1_ccmu_r1-full-w1` 为 36/36 complete、无 missing/duplicate。外层 archive SHA-256 `16993ca14d6d2c7b44f3f213c7ce92aeb56317a8523d0290e66ec0b92bed275b` 与回拉 verification 一致；回流 source manifest 与冻结 r4 archive 的 25 行完全相同。36 个 prediction NPZ 与 `subject_results.csv` 成对完整，ACC 重算误差为 0。




- **冻结 S6D 判读**：P1−B0 mean `+0.521 pp`；seed0 `-0.810 pp`、seed1 `+1.852 pp`；`5/9` two-seed subject means 正向，且没有 `<=-10 pp` collapse。两-seed 稳定门失败，故严格为 `ambiguous`，不是 `screen_positive`。




- **资源与 claim 边界**：A1/N1、追加 seed、调窗、选择 subject 和结构救援均不授权；不进入 S6R/S7Q/benchmark/confirmation，不写性能或机制 claim。当前 runtime 没有独立 reviewer backend；用户授权下的 deterministic self-check 只执行冻结否定/停止门，不冒充外部审计。




- **family/S9**：S6M 采用 `S6D_direct_exception`：没有 assignment/timing controls，也没有 branch/token/attention 可观测性来定位可归因 bottleneck。EFSR-v0.1 因此 `prototype_archive / completed_not_promoted`；`dsainet-efsr` 为 `exploratory / paused(evidence_gap)`，child budget `0/1` 未消耗。




- **re-entry**：同一 immutable result snapshot 的一次 analysis-only evidence search 已完成。定向文献再次显示多尺度/时窗领域拥挤且 MI timing 存在跨被试差异，但未提供本 family 的本地锚点；结果为 `no_reentry_evidence`。同快照不重复搜索，只有独立新证据实质改变 seed instability 的解释时才可重启 family 判断。









## D-125：以候选不变的 checkpoint branch-scale probe 尝试定位 EFSR 优化瓶颈（2026-08-19）









- **授权与身份**：用户显式要求结合本轮结果继续 `dsainet-efsr` 的优化探索。新建 diagnostic-only cycle `2026-08-19_dsainet_efsr_branch_optimization_probe`；父 EFSR-v0.1 已关闭且不改写，candidate fingerprint、window、routing、数据与结果均不变。




- **新可观测入口**：父 run 的 `artifact_manifest.json` 登记 36 个 checkpoint；released DSAINet 的 branch1/branch2 各有两个原生 ConvTime `alpha`，并有 learnable big-residual `alpha1/alpha2`。这允许只读检查 final optimization state，但不等同 activation、attention、梯度动力学或机制证据。




- **冻结门**：主观察量为 fine branch 两个 ConvTime alpha 绝对值均值 `F`；比较 paired `ΔF=P1-B0` 与既有 `ΔACC`。只有全体 Spearman `|rho|>=0.50`、两 seed 的 `ΔF/ΔACC` 符号均对齐、且至少 7/9 leave-one-subject-out rho 同号且 `|rho|>=0.30`，才记为 `optimization_anchor`。




- **边界**：本诊断不训练、不读取新 outcome、不跑 A1/N1、不增加 seed、不调窗或 mask。过门也只允许回到 S6M 讨论一个单变量 child；未过门即关闭该优化路线并恢复 family 暂停。




- **授权闭环与完整性**：初次安全审查拒绝远端 artifact 内容读取后，用户对精确只读动作明确批准。probe 随后完成：36/36 checkpoint、18/18 paired rows、key/scalar finite/SHA-256 均通过，issues=`[]`；无远端写入、训练或新 outcome。




- **冻结结果**：`rho(ΔF,ΔACC)=-0.1076`，低于 `no_anchor` 的 `|rho|<0.30` 门；seed0 `mean ΔF=-0.2523` 与 `ΔACC=-0.810 pp` 同号，seed1 `mean ΔF=-0.1972` 与 `ΔACC=+1.852 pp` 反号，alignment=`1/2`；stable leave-one-subject-out=`0/9`。描述量同样未显示与 `ΔACC` 的强同步关系：coarse internal `rho=-0.0507`、fine big residual `rho=0.0279`、coarse big residual `rho=-0.1469`。




- **收口**：机械判为 `no_anchor`，排除“final fine residual scale 可解释 seed 翻转”这一优化路线。不得据此调 alpha、LR、window、mask 或 seed，不创建 child；`dsainet-efsr` 恢复 `exploratory / paused(evidence_gap)`。本诊断仍不支持 activation、causality、性能或机制 claim。









## D-128：本地 GPU 只读诊断显示 EFSR 的 event 对象会被 fine intra-attention 抹掉（2026-08-19）









- **授权与身份**：用户要求在本地 GPU 搜集证据、先不新建方向。新建 diagnostic-only cycle `2026-08-19_dsainet_efsr_activation_attention_probe`；候选 fingerprint、窗口与路由不变，不改写 EFSR-v0.1 或 BOP。




- **Panel A**：父 EFSR 36 个训练后 checkpoint 因 `[REDACTED_MACHINE]` offline 未能回拉；未读取远端权重。该面板保持 blocked。




- **Panel B**：在读取前冻结。使用 18 个本地官方 `loso_official_preproc` validation-best 权重，同一 state 分别做 `full` 与 `event_fine` 只读前向。`full` ACC 与 2026-06-17 表的最大差为 `0.0 pp`。




- **冻结结果**：P1 `M_res=0.884`、相对 B0 `+0.610`、FAR `0.065`，两 seed 均为 `object_formed`。随后 `M_intra=0.254`，`mean(M_res-M_intra)=0.630`，标签为 `destroyed_by_intra`；inter 不再额外毁掉对象。零样本 P1−B0 ACC `-0.974 pp` 只作描述，不重判父屏。




- **收口**：独立新证据说明 hard mask 能在 residual 处造出对象，但 host 的 fine intra-attention 会先把它抹平。不创建 child，不调窗/seed/mask，不把该结果写成性能或论文 claim。family 进入 `decision_pending`，下一步须用户选择：补 Panel A、另开机制，或停在该边界。









## D-129：本地 36-unit EFSR 训练后探针确认对象仍被 intra 抹掉（2026-08-19）









- **授权**：用户要求本机 GPU 跑 EFSR 相关实验。[REDACTED_MACHINE] 仍 offline，故在 AAP cycle 内冻结 Panel C：同一 fingerprint 训练 B0/P1 后再套用对象门。




- **执行**：36 个 100-epoch LOSO unit，3 路并行；`full_s1_t3` 首次 CUDA OOM，单独重跑通过。探针 36/36，ACC 重算差 `0.0 pp`。




- **冻结结果**：P1 `M_res=0.978`、相对 B0 `+0.704`、FAR `0.007`，两 seed 均为 `object_formed`。`M_intra=0.251`，`mean(M_res-M_intra)=0.728`，标签 `destroyed_by_intra`。训练没有保住对象。




- **描述 ACC**：本地 P1−B0 `-0.926 pp`，两 seed 均负，`2/9` 两-seed 正向被试。不得重判父周期 `ambiguous`，不得当作发现屏。




- **收口**：与 Panel B 销毁位置一致。不创建 child，不改窗/mask/seed。Panel A 仍 blocked。









## D-130：父远端 EFSR checkpoint 的 Panel A 与 B/C 销毁位置一致（2026-08-19）









- **授权**：用户明确要求补 Panel A。`[REDACTED_MACHINE]` 已 idle；只读 `scp` 回拉 36 个父 checkpoint，SHA-256 与 manifest 一致。




- **完整性**：36/36 只读前向；ACC 重算最大差 `0.174 pp`，低于 `0.5 pp` 门。无训练、无远端写入。




- **冻结结果**：P1 `M_res=0.977`、相对 B0 `+0.703`、FAR `0.005`，两 seed 均为 `object_formed`。`M_intra=0.249`，`mean(M_res-M_intra)=0.728`，标签 `destroyed_by_intra`。




- **收口**：A/B/C 三块证据一致。不改写父 `ambiguous`，不创建 child。AAP 诊断三面板均已完成。









## D-131：EFSR intra 的 locality 跌落是 attention residual 起始、norm1 补完（2026-08-19）









- **冻结与完整性**：在读取结果前冻结子层分解，只读父远端 36/36 manifest-matched checkpoint，其中 18/18 个 P1 完成。手工分解的 `norm2` 与原始 block 输出最大误差为 `0`，`M_res` 与旧 Panel A 完全一致。




- **分解结果**：均值为 `M_res=0.977458`、`M_attn_res=0.576882`、`M_norm1=0.243908`、`M_ffn_res=0.251705`、`M_norm2=0.249211`。attention residual 贡献正跌落 `0.400577`（`54.42%`），LayerNorm 合计贡献 `0.335468`（`45.58%`），FFN residual 为 `-0.007797`，即轻微恢复。




- **归因边界**：总体机械标签为 `attention_residual_dominant`，但 seed0 是 `layernorm_dominant`，seed1 是 `attention_residual_dominant`。因此稳定结论不是“只有 attention”或“只有 LayerNorm”，而是 attention residual 先造成主要跌落、norm1 再补完的两阶段过程。




- **研究路线**：若继续，fine specialization 应同时穿过 attention 支持域与 norm1，而不是仅在 branch input 一次 routing。当前结果仅测 token-energy locality，不证明 event 语义删除或父屏性能因果；不重判父 `ambiguous`，不自动创建 child。









## D-132：AAP-intra 新快照形成 ESFS-v0.1 diagnosis-driven child（2026-08-19）









- **re-entry**：新快照由 AAP A/B/C 与 intra 子层分解组成。父远端 P1 的 locality 为 `0.977→0.577→0.244→0.249`；attention residual 与 LayerNorm 分占正跌落 `54.42%/45.58%`，且 seed 主导性相反。它定位结构 bottleneck，但不是性能因果证据。




- **单一 child 改动**：`ESFS-v0.1` 不选择只修 attention 或只修 LayerNorm，也不在每个子层反复乘 mask。它在 positional encoding 后取 indices `15..22`，让 fine 以固定 8-token event subsequence 贯穿 ConvTime、intra、unequal-length inter 与独立 pooling；coarse 保持 31-token full。参数量、loss、窗口和原模块公式不变。




- **公平对照**：B0=native full/full；B1=父 EFSR 一次性 31-token zero-mask；P1=8-token event subsequence；conditional N1=同长度 shifted subsequence。54-unit discovery 必须同时通过 P1-B1 和 P1-B0 的跨 seed 门，才允许 18-unit N1。




- **状态与权限**：用户明确授权创建 child，family budget `0→1/1`。child 已完成 focused contract、wait-what、S3 delta 与 S4 冻结，停在 S5 实现授权前。父 EFSR 保持 `closed/ambiguous`；child 不继承任何 signal、benchmark、claim readiness 或执行授权。









## D-115：FAGER-v0.1 的 gate 机制 no-signal，但 event-residual family 保留 child 锚点（2026-08-18）









- **研究对象**：新 family `dbconformer-event-specialist` 的首个 core cycle `2026-08-18_dbconformer_event_gated_temporal_residual`。原生 DBConformer full temporal/full spatial 与 classifier 保持 identity anchor；轻量 event expert 读取固定 `[2,3) s`，以 zero-init `alpha` 和 event-only scalar gate 向 pooled temporal feature 加 residual。




- **S1–S5**：候选以 combination-level、supporting adapter 通过 S3；D0/check 通过，`alpha=0` 时 P1/R1/W1 与 B0 logits 最大误差为 0，base hash 完全一致。四臂 smoke 4/4。一次工程修复只补 runner 的 SwanLab `group=None` 必填参数，不改模型或科学合同。




- **selection-only pilot**：BNCI2014001 seed0、subjects 0–2、B0/R1/P1/W1 共 12/12 单元完成；prediction-level deterministic self-audit 通过。P1-B0 `+1.5625 pp`（2/3 正向），P1-W1 `+0.5787 pp`（2/3），但 P1-R1 `−3.7616 pp` 且 0/3 正向，触发冻结 `no_signal`。不创建、不上传、不提交 full Bundle。




- **机制定位**：P1 gate mean 为 `0.938–0.941`、std `0.021–0.033`，近似常数全开；residual/full norm ratio 为 `0.439–0.514`。因此精确失败落在 event-only scalar gate 没有学出 trial selection 并引入不利缩放，而不是 full 被替换。R1-B0 约 `+5.324 pp` 且 3/3 正向，只是已暴露、selection-used control signal。




- **S6M**：关闭 FAGER-v0.1 精确实例；family 设为 `exploratory / paused`，保留一个未授权 child 机会。未来如继续，必须新 cycle 冻结 ungated 或严格 scale-controlled identity-preserving event residual 的 replication/confirmation 合同，不能把 R1 control 直接晋升 full，也不能回调本 cycle 的 gate/window/阈值。




- **审查边界**：当前 runtime 无 cross-model experiment-audit/result-to-claim backend；外部 verdict 记录 `REVIEW_UNAVAILABLE`。项目允许的 deterministic + 用户授权 self-review 只用于执行预冻结否定门禁，不释放 supportive claim。









## D-117：规范 S6 决策文档，并将新 Bundle 调度改为仅 w1（2026-08-18）









- **S6 文档**：新建或后续首次进入相应阶段的 cycle，在 `_work/decisions/` 写 `S6D_DISCOVERY_DECISION.md`、`S6R_STABILIZATION_DECISION.md`、`S6M_FAMILY_MATURATION_DECISION.md`；仅在实际关闭时写 `S9_CYCLE_CLOSE_DECISION.md`。这些文件是结论入口，不是状态源。`research_cycle.md` 与 `PROPOSED_FAMILIES.md` 仍是唯一状态源。不为未执行阶段伪造正式 decision。




- **历史 cycle**：已关闭且命名漂移的 cycle 只新增 `_work/decisions/DECISION_INDEX.md`（`indexed_from_existing_artifacts`，`evidence_delta: none`）。不移动、不重命名、不删除既有产物。SATR、PCSR、TCUS、EFSR、PCRR 及运行中/已上传/待回拉/等待授权 cycle 不补写事后决策。




- **远端调度**：新 Bundle 默认且仅使用 `ccmu-lane-autopilot-v3`：`check → w1 representative pilot → scheduling_decision → w1 full`。自动 `upper_probe_lane` / w2 / 二分回退停用。已冻结 v2 Bundle 保持原 plan。1 lane 是当前调度策略，不是跨硬件定律；恢复高并发必须显式新授权。




- **非声明**：本条不改变任何历史数值、claim、冻结合同、Bundle 哈希、远端在途实验或科学授权。check/pilot/scheduler 证据仍不是性能结论。









## D-118：FAGER/IER family re-entry 未形成第二个 child（2026-08-18）









- **精确快照**：以 `2026-08-18_dbconformer_identity_event_residual` 为唯一 re-entry snapshot。IER-v0.1 的 9-unit selection pilot 保持 `no_signal`：P1−B0 `−0.463 pp`（1/3 subjects 正向），P1−N1 `+2.836 pp`（1/3），父 FAGER ungated R1 的 `+5.32 pp` 未复现。




- **机制边界**：IER 的 residual/full norm 约 `0.20`、cap trigger `0.969–1.000`，只能排除“残差没注入”。已有 predictions 不含 logits 或 event/full confidence，不能验证 joint reliability gate。IER 中 class 3 的 3/3 净受损在父 R1 的另一组 3/3 units 上反向为净受益，类别条件不具跨快照稳定性。




- **路线审查**：调 `tau`、调窗属于结果驱动搜索；joint gate 缺少直接观测锚点；class-conditional suppression 与父快照冲突；目标被试个体化会改变数据/适配合同。没有一项同时满足可归因、单变量、可证伪。




- **family 状态**：`dbconformer-event-specialist` 保持 `exploratory / paused(evidence_gap)`，child readiness=`not_ready / missing_bottleneck`，budget 仍为 `1/1`。同一 snapshot 的 re-entry 已消费，不得重复；当前没有可授权的第二 child 或 full。




- **非声明**：该结论不否定所有 full+event、residual、attention 或个体化时窗方法，也不释放 benchmark、confirmation 或论文 claim。完整复核见 `experiments/records/2026-08-18_dbconformer_identity_event_residual/_work/review/FAMILY_REENTRY_REVIEW_2026-08-18.md`。









## D-119：Family Re-entry 改为 Agent 主动证据搜索（2026-08-18）









- **决定**：当用户要求继续一个 `paused/evidence_gap` family 时，不再要求其先提供新的机制、baseline defect、文献或模型结构。Agent 绑定精确 family 和最近 evidence snapshot 后，主动开展一次有边界的证据搜索。




- **搜索边界**：只读整合既有失败边界、可读结果/诊断、baseline 与插入点结构审计，以及围绕该具体缺口的定向文献；不自动新建 cycle、改代码、运行诊断、训练、上传或远端资源。每个不可变 snapshot 最多一次，完整记录于 `_work/review/FAMILY_REENTRY_EVIDENCE_REVIEW.md`。




- **严格出口**：只有本地可追溯 evidence anchor 与可检验因果解释共同支持单变量、可证伪修改时，才可形成 `child_ready`；仅能区分问题时可形成 `diagnostic_ready`；改变 baseline defect 或核心 thesis 时仅输出 `new_family_candidate`。其余为 `no_reentry_evidence` 或 `blocked`，不将泛化新 idea、单篇文献或旧结果重述伪装为证据增量。




- **预算与历史**：`decision_pending` 仍等待用户授权。`exhausted/no_go` 不能借 re-entry 绕过既有 child budget；真正改变旧失败解释的证据应进入新的 family 候选。既有 family/cycle 的结论、授权和历史 re-entry 文件均不改写。









## D-124：FAGER/IER 更新机制 re-entry 形成 diagnostic-ready 路线（2026-08-18；编号迁移于 2026-08-19）









- **精确绑定与不变量**：仍以 `2026-08-18_dbconformer_identity_event_residual` 为唯一 evidence snapshot。FAGER-v0.1 与 IER-v0.1 的 `no_signal`、selection-used 暴露、family budget `1/1` 及不进入 full/claim 的边界均不改写。




- **新增结构锚点**：IER 的 P1/N1 将 `t_full + r` 送入同一个 80-D classifier；现有 P1−B0 比较把 residual 的推理时插入效应与 P1 checkpoint 中 native backbone/head 的共同训练适配混在一起。旧 review 未检查这一 baseline/插入点可辨识性，因此不足以消费更新协议下的 re-entry。




- **ready diagnostic**：`IER-RIO-v0` 只读取既有 seed1、subjects 3–5 的 P1/N1 六个 checkpoint，在权重与数据不变时分别计算 residual-on 与 residual-off logits。首要完整性门是 on 路径必须逐样本复现现有 prediction；主要判别为 P1 on−off，并以 P1 与 N1 的 on−off 增量差作为位置控制。该诊断不训练、不调 `tau`/窗口、不复活 gate，也不是第二 child。




- **预声明路由**：只有 P1 on−off 为正、至少 2/3 subjects 正向，且 P1 增量严格优于 N1、均值为正并至少 2/3 正向，才返回 family review；这仍不自动产生 child。generic insertion、局部伤害、mixed/null 均回到 `paused(evidence_gap)`，禁止代理指标扩张。




- **当前状态与权限**：`dbconformer-event-specialist` 为 `exploratory / decision_pending`，readiness=`diagnostic_ready`。尚未创建 diagnostic cycle、未写脚本、未执行前向、未训练或上传；下一步必须由用户显式授权。规范产物为 `experiments/records/2026-08-18_dbconformer_identity_event_residual/_work/review/FAMILY_REENTRY_EVIDENCE_REVIEW.md`。









## D-122：IER-RIO-v0 完成并形成冻结 full anchor 的第二 child 路线（2026-08-18）









- **精确诊断**：用户授权创建并执行 `2026-08-18_dbconformer_ier_residual_insertion_observation`。19/19 source manifest rows、6/6 residual-on 逐 trial reproduction 通过，共 3456 arm-trials；未训练、未改权重、未上传。




- **预声明 verdict**：P1 residual on−off 在 subjects 3/4/5 为 `+2.778/+0.347/+3.819 pp`，mean `+2.315 pp`、3/3 正向；相对 N1 的位置控制为 `+2.431/−0.694/+3.125 pp`，mean `+1.620 pp`、2/3 正向，命中 `event_insertion_supported`。




- **解释边界**：诊断只表明 residual 在 joint-trained P1 checkpoint 内有直接且位置相关的贡献。它不把 off 当作 B0，也不改变 IER P1−独立 B0 `−0.463 pp` 的 no-signal；正式 `result-to-claim` reviewer 不可用，claim release=`none`。




- **family bottleneck**：residual 内部贡献为正而 joint-trained P1 整体仍输给独立 B0，把失败落点收敛到 native backbone/head 与 event path 的 joint co-adaptation 可能损伤 full anchor。该解释是 selection-used post-hoc evidence，不是机制确认。




- **ready child**：`FAER-v0.1` 只把 IER 的 joint optimization 改为冻结已训练 B0 native backbone+classifier，并只训练原 event expert/projection/alpha；`alpha=0` 必须逐 logits 复现 paired B0。不得同时改 `tau`、window、gate、loss、expert 宽度或 scope。首屏仍看 P1−B0 与 P1−N1；任一均值 `<=0` 或少于 2/3 subjects 正向即关闭。




- **权限（历史节点）**：当时 family=`exploratory / decision_pending`、budget=`1/1`，等待扩展与创建授权；后续状态见 D-123。









## D-123：扩展 event-specialist budget 并创建 FAER-v0.1（2026-08-19）









- **授权与预算**：用户明确要求“扩展并创建”。`dbconformer-event-specialist` 的 `max_child_cycles` 从 `1` 扩为 `2`，并在创建时把 `used` 从 `1` 增为 `2`。该扩展只发生一次，依据是 IER-RIO-v0 的可归因诊断已满足预写 extension rule。




- **精确 cycle**：创建 `2026-08-19_dbconformer_frozen_anchor_event_residual`，canonical name=`FAER-v0.1`，relation=`bounded_instantiation`，origin=`diagnosis_driven_child`。Parent 为已关闭的 IER-RIO diagnostic cycle；不重开或改写 FAGER/IER/IER-RIO。




- **唯一科学变量**：相对 IER joint optimization，FAER 加载 paired trained-B0 checkpoint，冻结全部 native backbone 与 classifier，只训练原 IER event expert、projection、alpha。`tau=0.2`、P1 `[2,3) s`、N1 `[3,4) s`、loss、宽度和 selection scope 均不变。




- **公平性边界**：FAER 比 B0 多 stage-2 adapter training，故当前 profile 明确标为 `diagnostic`，不能伪装成等计算量 UEP 主表 exact-paired。P1 必须同时优于 paired B0、同预算 N1 和 inherited joint-trained IER-P1；任一冻结门失败都关闭精确 child，不做解冻层或超参救援。




- **当时状态**：focused S2 Contract、wait-what、S3-delta 和 S4 plan 已冻结；family=`exploratory / active`，budget=`2/2`。当时未实现或运行；后续 S5 状态见 D-126。









## D-126：FAER-v0.1 完成本地 S5，停在 S6D 授权前（2026-08-19）









- **授权**：用户明确“授权S5”。授权覆盖最小实现、3-source preflight、D0-C/P/N/O、B0/P1/N1 check 与 P1/N1 seed1-target3 2-epoch smoke；不覆盖 6-unit selection pilot、full、Bundle、上传、远端或 claim release。




- **实现**：新增一个继承 IER event path 的薄 FAER 模型、一个冻结配置和一个 runner。加载 paired trained-B0 后冻结全部 native+classifier；stage-2 train mode 中 native 强制保持 eval。只训练既有 EventExpert20、projection、alpha；未改 tau/window/gate/loss/lr/epoch/expert width。




- **门禁**：3/3 checkpoint 与 3/3 prediction SHA-256 匹配；P1/N1 alpha0 logits 对 B0 max-abs 均为 `0`；trainable 参数均为 `7,721`，初始化一致；两步梯度链与 cap 通过；native/head 两步 optimizer 前后 SHA-256 不变；check 三臂通过。




- **smoke**：P1/N1 各 1 个 seed1-target3 2-epoch unit 完成，offline tracker success，checkpoint/prediction 落盘；保存后的 native state 与 source anchor 完全一致。smoke 指标不可作 discovery、性能或机制证据。




- **当前状态**：exact cycle=`S5_implementation_verified`，`authorized_run_level=diagnostic`，`highest_evidence_level=implementation_verified`。FAER-C0 构造得到本地验证，C1/C2/C3 仍未测试；下一边界是是否另行授权 S6D 六个 stage-2 units。









## D-127：授权 PCRR→ACUS→UOD→FAER 顺序远端执行（2026-08-19）









- **授权**：用户要求按序在服务器跑完 PCRR-v0.1、ACUS-v0、UOD-v0.1、FAER-v0.1；当时只做运行与最终一次性回拉，不做分析。全部 GPU 0、单卡 1 lane。2026-08-20 用户另授分析 UOD r2；判读见 D-104，不自动扩展到 ACUS/FAER/PTAR/ESFS。




- **工程边界**：PCRR r3 pilot 因 Bundle 内 `run_task.py` 误用 RCOD 配置秒失败，属工程修复；新 Bundle 为 r4。UOD/FAER 首次冻结远端 Bundle。FAER r2 check 因缺 `DBConformer-main/.../DBConformer.py` 失败，改走 r3（见 D-134）。




- **执行**：服务器守护进程 `2026-08-19_authorized_four_cycle_gpu0`；全部完成后一次性 fetch/verify/intake。不升级任何 claim。




- **队列扩展**：用户在无新 SIGSEGV 时授权把 PTAR-v0.1 接到同一 GPU0 1-lane 队列末尾。









## D-128：服务器顺序队列守护进程（2026-08-19）









- **原因**：本机调度器只在阶段交界提交下一 Run；本机断网或进程被 10 小时上限杀掉后，当前 Run 能跑完但队列会停。用户要求以后实验都能在服务器上自主按序执行。




- **做法**：新增 `scripts/remote/ccmu_queue_daemon.sh`（远端 `bin/ccmu_queue_daemon.sh`）与本地 `scripts/remote/ccmu_queue.ps1`。守护进程 resume-safe，固定 `check -> w1 pilot -> decide -> w1 full`，单锁 `queue-daemon.lock`。不改 UEP、不判读。




- **当前队列**：把 `2026-08-19_authorized_four_cycle_gpu0` 挂到该守护进程；PCRR check 已完成、pilot 若在跑则等待，不重提 RunId。本机 PowerShell 顺序器停用。









## D-129：再出现 SIGSEGV 则中止并迁剩余队列到 mieeg-modern（2026-08-19）









- **当前**：PCRR `...-full-w1-retry` 在 `mieeg` / GPU0 上正常运行则不改环境、不重打 Bundle。




- **触发**：后续任一队列 Run 再出现原生 SIGSEGV / `libcuda`/`nvidiactl` 崩溃。




- **动作**：先 abort 当前 Run 并停守护进程；再为**尚未完成**的实验打新 Bundle，`conda_env=mieeg-modern`（PyTorch 2.5.1+cu121），新 RunId，走各自的 check→pilot→full。失败的 mieeg 产物不拼接。




- **配对边界**：已完成的 PCRR `mieeg` check/pilot 不能与 `mieeg-modern` full 写成 exact-paired。FAER 的 `weights_only=True` 在 modern 上更匹配。该迁移不承诺消灭 SIGSEGV。









## D-133：ESFS-v0.1 完成本地 S5，停在 S6D 授权前（2026-08-19）









- **授权**：用户明确“授权S5”。范围为最小实现、preflight、D0-C/P/N、四臂真实数据 check 与四臂 seed0-target0 2-epoch smoke；不含 Bundle、上传、远端执行、54-unit discovery、正式 full 或 claim release。




- **实现**：新增零参数 `ESFSDSAINet` adapter；B0/B1 保留原 31-token 逻辑，P1/N1 分别在 positional encoding 后固定 gather `15..22` / `7..14`，fine 以 8 tokens 贯穿 branch2、residual、intra、unequal-length inter 与独立 pooling，coarse 始终为 31 tokens。未改窗口、loss、attention/LN 公式、宽度或参数量。




- **D0/check**：13/13 hard checks 通过；B0 对 released DSAINet/父 full、B1 对父 event-fine 的 logits 最大绝对误差均为 `0`；四臂参数量均为 `75,645`。P1/N1 的 fine/coarse 长度分别为 `8/31`，forward/backward finite。四臂 check 各 18 行，split fingerprint SHA-256 同为 `2c496c8da8652235711bd7d2d3f3b2dee76057d70505c451e45bffc91d69fb1e`。




- **smoke**：四臂各完成 1 个 2-epoch unit，均有 resolved config、1 行 subject result、checkpoint、prediction 与 offline tracker success。smoke 数值不作性能或机制证据。




- **状态**：`C-ESFS-C0=implementation_verified`；性能与机制 claims 仍未测试。exact cycle 进入 `S5_implementation_verified`，下一边界是另行授权冻结的 S6D；父 EFSR `ambiguous`、AAP locality 与 family selection exposure 均不改写。远端 54-unit 入队见 D-135。









## D-134：FAER r3 工程重建并把 PTAR 挂入 GPU0 队列（2026-08-19）









- **状态检查**：PCRR `...-full-w1-retry`、ACUS r2 full、UOD r2 full 均 `complete`。无新 SIGSEGV。GPU0 空闲。FAER r2 check 因冻结 Bundle 缺少 `refs/models/DBConformer-main/DBConformer-main/models/DBConformer.py` 秒失败；守护进程随之退出。r2 RunId 保持失败归档，不复用。




- **FAER r3**：新 Bundle `2026-08-19_faer_v0_1_dbconformer_bnci2014001_loso_s1_t345_ccmu_r3` 补入 baseline 源文件；`torch.load` 在无 `weights_only` 的 PyTorch 1.12 上退化为默认加载。科学合同不变，仍 `mieeg`。r3 check 已通过；pilot `...-pilot-w1` 已提交。




- **PTAR**：用户「如果正常的话把PTAR也推上去排队」。Bundle `2026-08-19_ptar_v0_1_dsainet_bnci2014001_loso_seed0_s0_2_ccmu_r1` 已 prepare/upload，接在 FAER r3 full 之后。15-unit 五臂 × seed0 × subjects 0–2。不做判读。




- **D-129**：仍待命。当前 FAER r3 在 `mieeg` 上健康则不迁 `mieeg-modern`。









## D-135：授权 ESFS-v0.1 远端 54-unit S6D 并挂入 GPU0 队列（2026-08-19）









- **授权**：用户「把ESFS-v0.1也上传加入队列」。覆盖 prepare/upload 与接入现有 GPU0 1-lane 守护进程；只跑冻结 S6D primary。不含 N1/S6R、额外 seed/窗口、本地双进程恢复、结果判读或 claim release。




- **Bundle**：`2026-08-19_esfs_v0_1_dsainet_bnci2014001_loso_s01_ccmu_r1`（archive SHA-256 `8fe18881b2fa23942612dfe389f8bfccd4e53ee78b32aaa0fe86e3b677eea076`）。check 为 D0 13/13 + 四臂 18-row split；scheduling pilot 为 3 臂 × seed0 × subject0；full 为 B0/B1/P1 × seeds 0–1 × subjects 0–8 = 54 units。




- **队列位置**：PCRR/ACUS/UOD/FAER 已 complete；PTAR r1 check 已过、pilot 运行中；ESFS 排在 PTAR full 之后。父 EFSR `ambiguous` 不改写。









## D-136：FAER-v0.1 六-unit no-signal，event-specialist family exhausted（2026-08-20）









- **回拉与完整性**：FAER r3 RunId `2026-08-19_faer_v0_1_ccmu_r3-full-w1` 已 `complete -> fetch -> SHA-256/manifest verify -> intake`。外层 archive SHA-256 为 `6155d891d1c6431f9f53f09ecb7f5c27978a4525b6dd37e14043e0aaed4515e5`，Bundle 95/95 files verified。6/6 unit、3,456 条预测、6 个 checkpoint、split/标签/指标重算与 6/6 native/head invariant 均通过。




- **冻结判定**：P1−B0 `−1.678 pp`、0/3 正向；P1−N1 `+0.231 pp`、仅 1/3 严格正向；P1−inherited IER-P1 `−1.215 pp`、2/3 正向。三个预注册对照中，B0 与 inherited IER 均值失败，N1 subject-spread 失败，故 exact FAER-v0.1 为 `no_signal`，不是 ambiguous。




- **精确边界**：关闭的是 trained-B0 frozen native/head + 既定 event residual adapter 的精确实例。不得外推为所有 event residual、freezing 或 adapter 失败；IER-RIO 的 checkpoint 内 on/off supporting diagnostic 不改写，也不升级为 joint co-adaptation 机制确认。




- **S6M/S9**：FAGER、IER 与 FAER 三个 exact instances 均已关闭；注册路线覆盖 scalar gate、capped ungated joint residual 与 frozen-anchor adaptation。`dbconformer-event-specialist` 保持 `exploratory`，route 转为 `exhausted`，budget `2/2`，child `not_ready`。FAER exact cycle 以 `negative_boundary / completed_not_promoted` S9 关闭。




- **权限与 claim**：不运行解冻、调 tau/window/lr/epochs、加 gate/loss、额外 seed/subject、benchmark 或第 3 个 child。外部 experiment-audit/result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`，claim release=`none`；确定性负向规则只用于关闭 exact cycle。









## D-137：ESFS-v0.1 54-unit no-signal，dsainet-efsr family exhausted（2026-08-20）









- **回拉与完整性**：RunId `2026-08-19_esfs_v0_1_ccmu_r1-full-w1` 已 complete/intake；archive SHA-256 为 `38d501f34754ec212d71af9ae00a5579514983484e2e34d54f8bf00f8a006c57`，725 个 Bundle 文件验证通过。三臂各 18 units；54 predictions/configs/trackers/checkpoint manifest rows 完整，31,104 条预测的 ACC/Kappa/weighted-F1、test labels 与配对 indices 重算一致。fresh B0/B1 与父 EFSR 的 36 个对应 units 在指标、best epoch 与逐 trial predictions 上 36/36 exact match。




- **冻结判定**：B0/B1/P1 mean ACC 为 `61.796/62.317/62.008%`。P1−B1 `−0.309 pp`（seed `+0.598/−1.215`）；P1−B0 `+0.212 pp`（seed `−0.212/+0.637`）。虽然 P1−B0 有 5/9 subjects 正向、最差仅 `−2.431 pp` 且无单 subject 驱动，但两条跨 seed 主门均失败，故为 `no_signal`。




- **精确解释**：让固定 8-token event subsequence 贯穿 fine path，没有在此 selection-used BNCI2014001 scope 稳定优于 31-token one-shot zero-mask B1 或 native B0。该结果不确认 attention/LN locality 是性能因果，也不否定一般 token pruning、event window 或 multiscale routing。




- **S6M/S9**：冻结合同要求 no-signal 后不运行 N1/S6R并直接关闭 exact child。ESFS-v0.1 为 `negative_boundary / completed_not_promoted`；parent EFSR 仍为 ambiguous。`dsainet-efsr` 保持 exploratory，route 转为 exhausted，budget `1/1`，child not_ready/budget_exhausted，family falsification coverage=partial。




- **权限与 claim**：不追加 seed/窗口、换 shift、重复 mask、替换 attention/LN、增加 loss/gate/宽度或新 child。外部 reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`；T0 self 只执行机械完整性与预注册负向门，claim release=`none`。









## D-138：SCID-v0.1 未建立 scale/channel anchor，精确 cycle 与 family 收口（2026-08-20）









- **回拉与完整性**：RunId `2026-08-20_scid_v0_1_ccmu_r1-full-w1` 已完成 `check → pilot-w1 → full-w1 → fetch → SHA-256/manifest verify → intake`。check/pilot/full archive SHA-256 与 sidecar 一致，内部 Bundle 分别 `17/17`、`30/30`、`23/23` 文件通过；formal denominator 为 subjects `1..9` × seeds `{1,2}` 的完整 `18/18` checkpoints。




- **provenance repair**：S5 记录的 analyzer hash `babd4fb1…` 与实际 Bundle hash `edbbf815…` 不同。旧版已由 S5 bytecode 精确还原并匹配原 hash；唯一差异是把无条件 `torch.load(..., weights_only=True)` 改为按 PyTorch 签名兼容传参。修复发生在 staging/upload 前，3×3 计算、source-only sampling、门限和输出未变；保留 Queue Package 记录滞后披露，不事后改写。




- **冻结判定**：median kernel/group/interaction effect fractions 为 `0.322/0.575/0.073`；native diagonal 为正 `18/18`，三段 margin CV 为 `0.091/0.098/0.075`。但 kernel median 未超过 group median，且仅 `8/18` checkpoints kernel 占优、`4/9` subjects 在两个 seed 间翻转，因此冻结 outcome=`no_scale_identifiability`，S6D=`no_signal`。




- **S6M/S9**：formal S6D 已覆盖预声明的全部 subject/seed 稳定性范围，故以 `S6D_direct_exception` 进入 S6M，不伪造 S6R。family 的核心 thesis 被决定性检验且 extension rule 未满足；`sstdpn-scale-prototype-geometry` 为 `exploratory / no_go`，child=`not_applicable`，budget 保持 `0/1`。exact cycle 以 `negative_boundary / diagnostic_complete` 关闭。




- **权限与 claim**：不实现 scale-indexed prototype head，不补 seed、改 gate、跑 performance、benchmark 或 confirmation。稳定 segment margin 只作范围受限的 source-only 观察，不赋予短/中/长 scale 语义。外部 reviewer 不可用且未授权；本次为 self deterministic negative route，claim release=`none`。









## D-139：BSRD-v0.1 无 distinct responsibility anchor，family no-go（2026-08-20）









- **回拉与完整性**：RunId `2026-08-20_bsrd_v0_1_ccmu_r1-full-w1` 已 complete/fetch/verify/intake。18/18 unit、18 个唯一 subject–seed、18 个 checkpoint 完整；checkpoint SHA-256 同时匹配 artifact manifest 与 analyzer rows，冻结 config/analyzer/runner/model 源码匹配 Bundle source manifest，aggregate 独立重算一致。




- **冻结判定**：18/18 pointwise matrix full rank，median relative smallest singular=`0.180214`，identity gate 通过；但 18/18 checkpoint 的 branch-responsibility cosine 都在 `0.999821..0.999949`，aggregate=`0.999901>0.95`，故为 `no_responsibility_anchor`。median `|rho|=0.128999` 未超过 permutation null p95=`0.466460`；单个 nominal `p<0.05` 不作事后选择。




- **精确解释**：当前 weight-path 量能恢复 band identity，但固定 kernel 7/9/11 branches 学到的是近同质 band 分布，不是稳定不同职责。S6D=`no_signal`；不运行 S6R、router child、A1/N1、追加 seed/dataset 或替换 attribution 救援。




- **Family/S9**：因 distinct responsibility 是该 family 明示的 routing prerequisite，S6M 以 `S6D_direct_exception` 记录 `exploratory / no_go`，falsification coverage=`decisive`，child=`not_ready / missing_responsibility_anchor`。exact BSRD-v0.1 以 `negative_boundary / diagnostic_complete` 关闭。




- **claim 边界**：外部 experiment-audit/result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`，claim release=`none`。该结论不否定一般 Sinc、多尺度卷积或 input-dependent routing；后者若继续，必须作为改变核心 thesis/evidence signature 的新 family candidate。









## D-140：SWID共享平台未在BNCI2014004跨数据集复现（2026-08-20）









- **执行与完整性**：`SWID-XD-v0.1` 复用BNCI2014004 native DSAINet validation-best LOSO checkpoints，完成seeds `{0..4}` × targets `{0..8}` 的45/45 zero-training source-only诊断。45个seed-target/hash唯一，runner failures=0，full-mask identity error与target trial/label access均为0。




- **004内部结果**：grand peak/platform为start23/start19..23，但checkpoint间audit profile Spearman中位数仅`0.162`；start15 rank<=6仅`7/45`、位于自身平台`5/45`，冻结结论=`full45_no_anchor`。15/45 peak落在最后边界start23，不能把聚合晚期趋势写成稳定共享晚期平台。




- **跨数据集门**：001与004 grand audit profile rho=`0.453<0.5`，grand platforms start14..17与start19..23无交集，仅`11/45`个004 checkpoint平台触及001冻结区域，故结论=`cross_dataset_no_platform_replication`。




- **dynamic边界**：004 dynamic candidate=`3/45`且无target跨至少两个seed复现；与001的`2/45`一致不支持subject-specific selector。




- **路线**：`dsainet-dynamic-event-support`转为`exploratory / no_go_cross_dataset_nonreplication`。不把001平台直接用于跨数据集hard/dynamic/soft support model，不自动做branch-resolved后续。若改为dataset-specific或normalized-phase thesis，必须建立新family并重新授权。




- **claim边界**：004是3-channel/2-class相近Graz范式stress test，不区分dataset/task/channel原因。外部reviewer不可用，正式verdict=`REVIEW_UNAVAILABLE`，claim release=`none`。









## D-141：SWID-XD异常主要由跨数据集branch-utilization不等构解释（2026-08-21）









- **独立诊断**：新建 `SWID-MD-v0.1`，不重开SWID-XD或EFSR。Stage A读取001/004各45个既有profiles；Stage B在各45个冻结checkpoint上完成native/fine-input-zero/coarse-input-zero，90/90 hashes唯一、identity error=0、target trial/label access=0、training=none。




- **排除项**：两个数据集均为`[0,4)s`、250 Hz、31-token affine lattice，normalized phase只是重标索引，不能改善profile相关或platform overlap。004末端聚集存在，但H1充分门未过，只作次要边界因素。




- **checkpoint不稳定**：004同target跨seed profile rho中位数`0.150`，与跨target的`0.162`近似；001为`0.647/0.656`。004 profile similarity与更接近ACC/Kappa/best epoch不呈同向关联，说明异常更接近checkpoint-dependent branch function，而非普通性能波动。




- **branch utilization**：004 fine/coarse zero的ACC impact中位数为`2.42/22.76 pp`，fine positive CE share仅`7.66%`；001为`16.81/31.68 pp`与`33.04%`。share差`25.38 pp`，bootstrap 95% CI `[8.02,39.45] pp`，通过冻结H4门。




- **路线**：主路由=`R4_diagnostic_artifact`，secondary=`R3_model_instability_first`。这里artifact是SWID只扰动fine path而两个数据集branch utilization不等构，并非代码错误。D-140的原定义“不复现”不改写，dynamic family仍no-go；但004不再可被当作“一般event support不存在”的干净证据。




- **下一边界**：不调窗、不做normalized-phase rescue、不训练event-full interaction。若未来继续，先另立branch-balanced/branch-invariant temporal diagnostic并证明construct comparability。外部reviewer不可用，claim release=`none`。









## D-142：Branch-balanced诊断形成dataset-conditioned shared support与branch-allocation锚点（2026-08-21）









- **执行**：`BBTS-v0.1`在BNCI2014001/004各45个native DSAINet checkpoints完成shared/fine/coarse matched temporal interventions；90/90、90 hashes唯一、identity error=0、target access=0、training=none。fine视角在90/90上逐元素复现原SWID，4/4回归通过。




- **whole-model稳定性**：001 shared的all-pair/within-target/discovery-audit rho为`0.901/0.899/0.974`；004为`0.595/0.588/0.717`。004相对fine-only的`0.162/0.150/0.398`显著修复，否定“004 whole-model没有稳定temporal organization”的解释。




- **跨数据集**：001/004 shared grand rho=`0.510`，但platform=`15..18`与`21..23`无交集；主路由=`B_dataset_conditioned_shared_support`，不是共同shared platform。004 shared 39/45 peaks位于start23，故只称冻结epoch下late-boundary structure，不作生理边界解释。




- **allocation**：004 checkpoint median shared–coarse/shared–fine rho=`0.913/0.602`，33/45 shared更接近coarse；secondary=`C_branch_allocation_dominates`。001为`0.862/0.842`，两支更均衡。不能把差异归因于channels/classes/dataset单一因素。




- **候选**：只登记`SAFSS-v0.1 / Support-Aware Functional Scale Specialization`为`new_family_candidate_not_cycle_ready`。在边界可识别性、第三数据集/受控confound、source-only deployment合同与外部review完成前，不创建训练cycle或实现adaptive module。




- **claim**：外部reviewer不可用，正式verdict=`REVIEW_UNAVAILABLE`、claim release=`none`。









## D-143：EBID-v0.1确认004的0–4 s profile为右删失，5 s内平台可识别（2026-08-21）









- **数据与合同**：原始18 MAT、45 runs、6520 trials均可读取cue后5 s；0–4 s严格等于0–5 s前1000 samples，shifted `[1,5)`严格等于samples 250:1250，误差均为0。唯一协议变化是native epoch从1000增至1250 samples；8-token窗口仍为1.024 s。




- **M0**：18-checkpoint shifted-crop OOD probe的all-pair/within rho仅`0.086/0.259`，判`ood_unstable`，证明固定长度checkpoint的shifted crop不能替代原生5 s训练。




- **正式结果**：pilot 18 checkpoints触发full gate；完整45-checkpoint 0–5 s结果all-pair/within/discovery-audit rho=`0.768/0.789/0.880`，grand peak/platform=`start26/start24..27`，boundary peak=`0/45`。0–4 s对照为`start23/start21..23`且`39/45`峰在最后位置。




- **解释**：004原0–4 s whole-model shared profile存在crop-right-censoring；原生5 s合同内形成稳定内部晚期平台。该结果不证明精确生理center、性能增益或固定event window，也不直接授权SAFSS。




- **完整性/claim**：45 hashes唯一、identity error=0、target access=0，本地机械检查通过。独立reviewer不可用，正式verdict=`REVIEW_UNAVAILABLE`、claim release=`none`。









## D-144：BACL-v0.1未发现稳定channel-allocation shift，coarse dominance先在001 LR22出现（2026-08-21）









- **受控阶梯**：L0=001 four-class/22ch；L1=001 LR/22ch；L2=同一LR trials的C3/Cz/C4严格切片；L3=004 LR/3ch继承对照。L1/L2的2592 trials、labels、subjects与metadata逐元素一致。




- **执行与完整性**：L1/L2各18个validation-best checkpoints及shared/fine/coarse诊断完整；36 hashes唯一、identity error=0、target trial/label access=0。联合run status与checkpoint index覆盖36/36。




- **主判定**：L1→L2 paired shared/coarse profile rho中位数=`0.816/0.821`，fine rho=`0.223`。fine-share delta绝对值中位数虽为`0.161`，但中位delta=`0`、方向仅`8/18`，未过14/18门，判=`channel_effect_ambiguous`。




- **机制边界**：fine-share中位数L0/L1/L2/L3为`0.344/0.016/0.030/0.035`；coarse dominance在通道仍为22时已于L1出现，所以3通道压缩不是充分解释。L0→L1仍混有class/task-space、trial count及retraining，不能称纯class-count因果；L2→L3也不是纯dataset因果。




- **SAFSS路由**：不得硬编码dataset→branch allocation；未来如独立admission，应以稳定shared support为主锚，仅在branch-specific contribution超过噪声地板且跨checkpoint稳定时启用branch interaction。外部reviewer不可用，正式verdict=`REVIEW_UNAVAILABLE`、claim release=`none`。









## D-145：TBCD-v0.1未把L0→L1聚合分支差异归为稳定单一任务机制（2026-08-21）









- **拆解合同**：A=four-class全trial/4 logits；B=同一冻结L0只取LR trial；C=改用LR source normalization；D=只保留LR logits；E=继承LR-trained L1。A/B/C/D逐target/seed复用同一checkpoint，全部source-only。




- **执行与完整性**：B/C/D共54/54，18个唯一L0 hash；A/B/C/D配对hash mismatch=0，identity error=0，target access=0。四段加法恢复`E−A`的最大误差`2.22e−16`。




- **冻结判定**：总coarse-dominance shift中位数`+0.419`，但仅`12/18`同向，未过14/18门。trial/normalization/decision/retraining的中位分量为`−0.058/−0.004/+0.150/+0.237`，同向数`8/18、9/18、10/18、12/18`，均不合格；route=`total_shift_not_stable`。




- **解释边界**：normalization在本合同下不是主要解释；其余三项表现为target×checkpoint异质并经常抵消。不能把聚合L0/L1差异写成class count、decision set或retraining的单因果，也不能据此硬编码task→branch routing。




- **后续与claim**：head-only refit未触发，不补seed、不做backbone训练或结构救援。独立reviewer不可用，正式verdict=`REVIEW_UNAVAILABLE`、claim release=`none`；SAFSS仍不得因本结果自动admission。









## D-146：冻结SOFC-v0.1 source-only functional calibration与target-free deployment合同（2026-08-21）









- **问题锚点**：TBCD否定task metadata到branch tendency的稳定映射。未来SAFSS不能按dataset/task硬编码routing，必须对每个已选checkpoint在target access前校准functional state。




- **最小对象**：SOFC为零参数、zero-training资格artifact。whole-model shared support提供dataset/epoch-specific宽平台；fine/coarse只在per-source-subject branch-zero CE contribution中位数`>=0.01`且至少75% subjects为正时成为candidate。禁止用近零分母敏感的fine-positive-share作门。




- **验证隔离**：candidate只从确定性source discovery生成；untouched source audit检查shared profile rho/platform及branch positive contribution，不得反向修改artifact或阈值。现有validation曾用于early stopping，故明确标记selection-used diagnostic，不升级为独立performance evidence。




- **冻结门**：必要candidate数不少于10、pooled audit precision`>=0.80`、任一dataset/task stratum不低于`0.70`才判`calibration_valid`；稀疏、失稳或无branch signal均不得SAFSS admission，同版本不调epsilon、subject fraction或window救援。




- **部署边界**：artifact绑定checkpoint/config/split/epoch hash；target inference不得读取target EEG统计、label、loss或在线更新。缺失或不匹配统一`native_only`，branch不合格也不修改native DSAINet前向。




- **权限**：本轮只冻结S4合同和计划；D0/C0/C1执行、模型实现、SAFSS family admission、远程运行和claim release均未授权。外部method reviewer不可用，记录`REVIEW_UNAVAILABLE`。









## D-147：SOFC-v0.1通过source-only calibration门，但只qualify coarse branch（2026-08-21）









- **执行**：用户另行授权后完成D0、001 L0/L1 C0及条件004原生0–5 s C1。正式联合54/54 checkpoints，54 artifacts/checkpoint hashes/split digests唯一；identity error=0、target access=0、training=none。




- **冻结结果**：shared为54/54、precision`1.000`。Coarse为53 candidates/51 audit-valid，pooled precision`0.962`，L0/L1/004 strata为`1.000/0.889/1.000`，route通过。Fine pooled虽为`35/39=0.897`，但L1仅`6/9=0.667<0.70`，不能qualified。




- **部署含义**：最终route=`calibration_valid`、`qualified_branches=[coarse]`。Discovery artifact里的fine candidate不得被模型消费；未来SAFSS若另行admission，首版最多使用dataset/epoch-specific shared platform和coarse-qualified状态，且artifact失败回退native。




- **完整性**：54 artifacts均绑定当前config、实际split index digest、checkpoint与epoch contract；C1 shared重算与EBID逐元素误差0，L0/C1 checkpoint hash mismatch为0；规则测试4/4。




- **停止边界**：不补seed、不调`epsilon_ce=0.01`、75% subject gate、precision门或8-token窗口救fine；不实现continuous gate或fine specialization。本结果不证明SAFSS性能、target generalization或MI physiology。




- **claim**：外部experiment-audit/result-to-claim backend不可用，正式verdict=`REVIEW_UNAVAILABLE`、claim release=`none`。SAFSS family admission仍需独立用户授权。









## D-148：SNPD-v0.1 未建立 source-nuisance prototype anchor，family no-go（2026-08-21）









- **回拉与完整性**：RunId `2026-08-20_snpd_v0_1_ccmu_r2-full-w1` 已 complete/fetch/verify/intake。Transfer verification 记录 archive SHA-256 `4da6f490…`；Bundle manifest 本地逐项重算 `22/22` 通过。Formal denominator 为 subjects `1..9` × seeds `{1,2}` 的完整 `18/18` checkpoints，aggregate 从 per-checkpoint rows 独立重算一致。




- **冻结判定**：source-subject probe margin-over-chance 中位为 `0.640625>=0.10`，说明 source identity 明显可解码；但 ISP/ICP 相对 matched-rank random control 的 prototype overlap excess 中位仅 `0.043677<0.05`，且只有 `2/9<6/9` subjects、`0/2` seeds 同时过门。因此 outcome=`no_source_nuisance_prototype_anchor`，S6D=`no_signal`。




- **精确解释**：结果不是“没有 subject nuisance”。它说明当前 rank-4 source-subject nuisance basis 与 ISP/ICP 的超随机重叠没有形成预声明的跨 subject/seed 稳定 anchor，因而不能据此推进 orthogonalization。




- **Family/S9**：正式 18-checkpoint scope 已直接覆盖预声明稳定性问题，故以 `S6D_direct_exception` 进入 S6M，不伪造 S6R。`sstdpn-source-nuisance-prototypes` 为 `exploratory / no_go`，falsification coverage=`decisive`，child=`not_ready / missing_evidence_anchor`，budget 保持 `0/1`。Exact SNPD-v0.1 以 `negative_boundary / diagnostic_complete` 关闭。




- **权限与 claim**：不使用 target statistics，不调 rank/threshold/random controls，不补 seed/dataset，不实现 orthogonalization child 或性能实验。外部 result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`；确定性负向门仍可执行，但 claim release=`none`。









## D-149：SAFSS-v0.1独立admission、完成S0-S5并本地排队（2026-08-21）









- **独立family与继承边界**：建立`dsainet-support-aware-functional-scale-specialization`与exact cycle `2026-08-21_dsainet_support_aware_functional_scale_specialization`。只继承BBTS/EBID/BACL/TBCD/SOFC的admission rationale与负边界，不继承EFSR/ESFS、dynamic-event或SOFC的signal、预算、claim和运行授权。




- **冻结对象**：SAFSS-v0.1不训练、不增加参数。SOFC artifact的window-start平台按`W=8`取token并集，只投影coarse输入；fine保持完整。B0为native full，B1为L1 modal starts `[15,16,17]`的condition-static coarse，P1为checkpoint-bound coarse；N1 shifted equal-occupancy只预留给S6D正向后的另授权S6R。




- **资格与回退**：P1必须同时匹配SOFC全局route、only-coarse资格、target/seed/checkpoint/config/split/epoch hash和`target_access=0`。任何失败都不得替换邻近artifact或读取target统计，只允许native fallback；formal前置校验失败则repair/hold。




- **S5完整性**：标准库tests `5/5`和Python compile通过；D0为`14/14` assertions、18/18 exact pairs admitted、native logit error `0.0`。target0/seed0的2-trial check与16-trial smoke四臂完整并保存预测/split/label/hash；这些都只构成engineering evidence。




- **S6D合同**：正式队列冻结B0/B1/P1 × subjects 0–8 × seeds `{0,1}`=`54` arm evaluations，统计单位为两seed平均后的target subject。P1−B1和P1−B0必须overall及逐seed均正、至少5/9 subject正、9/9 leave-one-target-out均正才可screen-positive；仍只授权申请N1/S6R。




- **队列与Bundle**：Queue Package v0.1登记为#21。随后按用户要求构建immutable Bundle `2026-08-21_safss_v0_1_dsainet_bnci2014001_lr22_s01_ccmu_r1`，archive SHA-256=`2855da8495d0c829092a9a8bd4bceadc4b2201f37573ccbabf87a5e5439b691e`；64-entry source manifest、v3 plan、LF/bash语法、成员安全和解包运行门通过。18 checkpoints/artifacts随包；217.8 MiB数据保持独立asset contract，不塞入代码包。




- **权限**：当前状态=`local_bundle_built_waiting_upload_and_execution_authorization`。数据资产未登记/上传，Bundle未上传或执行；remote upload、remote execution、正式S6D、S6R、child、benchmark与claim均为false。解包后的单pair runtime dry-run只核对打包入口，临时预测已删除且未判读，不改变`signal_status: not_tested`。




- **审查与claim**：聚焦文献最近碰撞表明learned scale attention已存在，故novelty只能作范围受限的weak-to-moderate候选，不释放强查新声明。外部method/independent reviewer不可用，正式状态=`REVIEW_UNAVAILABLE`；scientific signal=`not_tested`，claim release=`none`。









## D-150：SAFSS-v0.1 正式 S6D 为 no-signal，精确 cycle 与 family 收口（2026-08-21）









- **世代与回拉**：r1 因 data asset verifier 预期键错误冻结，r2 因 prediction path 必须位于 job root 的工程限制冻结；r3 只修复这两项，不改变三臂、数据、checkpoint/artifact、target/seed 或冻结门。正式 RunId `2026-08-21_safss_v0_1_ccmu_r3-full-w1` 已 complete→fetch→SHA-256/manifest verify→intake；archive SHA-256=`5f7b521d4d66a284b5a23fa302dbbc47614107952c70af7ef228b3a18c169a65`，293/293 Bundle files 通过。




- **机械完整性**：18/18 target×seed tasks、54/54 arm rows/prediction NPZ 完整；顶层CSV与18个task CSV逐字段一致。每个NPZ的target indices、labels、prediction SHA-256、ACC/Kappa/weighted F1均重算一致，三臂同unit的indices/labels/provenance hash一致，每unit/arm至少两个预测类别。




- **冻结结果**：B0/B1/P1 ACC=`84.568/81.925/82.427%`。P1-B1=`+0.502 pp`，两seed为正、LOO 9/9为正，但只有4/9 target两-seed均值为正，未过5/9门；P1-B0=`-2.141 pp`，seed0/1=`-0.772/-3.511 pp`，仅1/9 target正且LOO 0/9为正。按“任一primary overall <=0即no_signal”直接停止。




- **流程**：S6D判`no_signal`；N1仅预留给screen-positive后的S6R，故不运行。完整18-pair分母直接检验family core thesis，以`S6D_direct_exception`完成S6M：family=`exploratory / no_go`、falsification coverage=`decisive`、child=`not_ready / missing_localized_attributable_bottleneck`。Exact cycle以`negative_boundary / completed_not_promoted`关闭。




- **边界与claim**：负面边界只覆盖“checkpoint-bound source-only coarse projection同时稳定优于native与condition-static control”的精确命题；不否定所有temporal support或scale specialization。外部experiment-audit/result-to-claim backend不可用，正式verdict=`REVIEW_UNAVAILABLE`；确定性负向门不等于独立审计，claim release=`none`，不补seed/window/mask/branch或运行rescue。









## D-151：ODRF-v0.1 未把 OSE 锚点转化成可筛选 fusion utility（2026-08-21）









- **回拉与完整性**：RunId `2026-08-21_odrf_v0_1_ccmu_r1-full-w1` 已 complete/fetch/verify/intake。Archive SHA-256 `cd0f32ee…`；Bundle manifest 本地逐项重算 `239/239` 通过。18/18 unit、10,368 条预测独立重算与 CSV 一致；18/18 parent checkpoint hash 匹配 OSE manifest。`disagreement` 等于 B0 的 `argmax(z_A)!=argmax(z_B)`，未用 target label 定义 stratum。远端 residual `.pth` 未回拉，不阻断负向屏，但不构成独立 16-param 张量审计。




- **冻结判定**：overall `P1-B0=+0.203 pp`，seed0/1 为 `−0.270/+0.675 pp`，`6/9` subject two-seed mean 正向，无 `<=-10 pp` collapse。因任一 seed mean `<=0`，S6D=`no_signal`。disagreement 18-unit 均值仅 `+0.342 pp`，未过 `+1.0 pp` 正门；agreement `−0.190 pp` 未出现大退化，但不能抵消 seed0 非正。




- **精确解释**：结果不是“A/B 变得冗余”。parent OSE 的 `order_specific_anchor` 不改写。它只说明当前 rank-2 class-aligned probability-disagreement residual 没有稳定优于 exact frozen B0，因此不能进入 N1/S6R 或 benchmark。




- **Family/S9**：按 `S6D_direct_exception` 进入 S6M，不伪造 S6R。`stgmfm-order-specific-evidence` 为 `exploratory / exhausted`，budget `1/1`，falsification coverage=`partial`。Exact ODRF-v0.1 以 `negative_boundary / completed_not_promoted` 关闭。




- **权限与 claim**：不补 seed、不改 rank/gate/公式、不加 branch-C、不把 seed1 局部正差当救援。外部 result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`；确定性负向门仍可执行，但 claim release=`none`。









## D-152：OCSO-v0.1 未建立 order-conditioned input anchor，family no-go（2026-08-21）









- **回拉与完整性**：RunId `2026-08-21_ocso_v0_1_ccmu_r2-full-w1` 已 complete/fetch/intake。45/45 checkpoint SHA-256 与冻结 manifest 一致；analyzer/config 哈希与 S5 冻结值一致。`summary.csv` 独立重算与 `aggregate.json` 的 median、passing subject/seed 和 outcome 一致。same-path floor 45/45 为 `0.0`。外部 experiment-audit/result-to-claim backend 不可用。




- **冻结判定**：median primary relative mean shift=`0.058913<0.08`；passing subjects=`2/9`（仅 S3/S6）；passing seeds=`0/5`。S1 中位 `0.079792` 接近但未达门。outcome=`no_order_conditioned_input_anchor`，S6D=`no_signal`。




- **精确解释**：结果不是“A/B 输入完全相同”，也不是对 OSE disagreement 的否定。它只说明在预声明的 `0.08/0.02/3×` 与 `6/9`、`3/5` 门下，共享卷积入口 moments 没有稳定可分锚点，因此不能据此实现 path-specific BN 或低秩 adapter。




- **Family/S9**：正式 45-checkpoint scope 已直接覆盖预声明稳定性问题，故以 `S6D_direct_exception` 进入 S6M，不伪造 S6R。`stgmfm-order-conditioned-shared-operator` 为 `exploratory / no_go`，falsification coverage=`decisive`，child=`not_ready / moment_anchor_failed`，budget 保持 `0/1`。Exact OCSO-v0.1 以 `negative_boundary / diagnostic_complete` 关闭。不得登记为 OSE child。




- **权限与 claim**：不改阈值、不补 seed、不把 8/45 局部超阈当救援、不实现 adapter/拆 BN/训练。正式 verdict=`REVIEW_UNAVAILABLE`；确定性负向门仍可执行，但 claim release=`none`。









## D-153：SCCD-v0.1 将 SAFSS 损失定位为 context/position 删除，而非 support conditioning 整体无效（2026-08-21）









- **独立对象**：SAFSS-v0.1 保持关闭；建立独立 family `dsainet-support-context-complementarity` 与 exact cycle `2026-08-21_dsainet_support_context_complementarity_decomposition`，只使用 SAFSS r3/SOFC/BBTS 作为 selection-used 边界，不作 rescue 或 re-entry。




- **冻结诊断**：七臂 zero-training factorial scope 覆盖 full、coarse-zero、support-only、non-support-only、equal-occupancy shift 以及两个 position-preserved controls；正式为9 targets×2 seeds×7 arms=`126/126` rows。135项manifest、预测哈希、指标重算、pair provenance均通过，B0/H1与SAFSS r3逐元素一致。




- **因果分量**：`full-hard_support=+2.141 pp`、`nonsupport-coarse_zero=+9.201 pp`、`support-shift=+17.303 pp`、`pos-preserved support-pos-preserved shift=+15.567 pp`，全部通过冻结稳定门。`pos-preserved support-hard_support=+0.772 pp`，`full-pos-preserved support=+1.370 pp`。




- **核心判断**：在mean ACC上，hard-mask损失严格分成position deletion `36.04%`和non-support content deletion `63.96%`。因此SAFSS下降主要属于删除侧；support区域相对shift有明确位置特异性，但support-only不充分。旧P1-B1仅`+0.502 pp`，所以不把宽泛support validity写成checkpoint-specific personalization强有效。




- **路由诚实性**：r1路由错误比较不可加的`D_hard`与`U_cond_*`，暴露结果落入未登记分支。保留原输出并将canonical route记为`route_table_gap_noncommensurate_magnitude`；不在结果后改阈值或伪造预注册标签。component answer仍由冻结contrasts独立支持。




- **收口与下一边界**：exact cycle=`supporting_evidence / diagnostic_complete`，family=`exploratory / decision_pending`。若继续，只能另行refine“保留full context、以source-only support作调制而非hard deletion”的单变量候选；当前child、训练、上传、远端、benchmark与claim均未授权，外部reviewer=`REVIEW_UNAVAILABLE`。









## D-154：建立 FCPSM-v0.1 为 SCCD family 唯一 diagnosis-driven child（2026-08-21）









- **授权与血缘**：用户明确授权 full-context-preserving support modulation child。Exact cycle=`2026-08-21_dsainet_full_context_preserving_support_modulation`，parent=`2026-08-21_dsainet_support_context_complementarity_decomposition`，relation=`bounded_instantiation`；family child budget 由`0/1`消耗为`1/1`。父证据只作selection-used rationale，不继承signal、confirmation或claim。




- **单一机制**：冻结checkpoint的content/position为`u/p`，SOFC mask为`M`；coarse输入=`u*(1+0.5*tanh(theta)*M)+p`，fine=`u+p`。每checkpoint/arm仅一个theta、零初始化；所有原参数冻结，non-support content和全部position保持native，support multiplier限制在`(0.5,1.5)`。




- **source-only fitting**：只用exact LOSO `train_idx`，固定Adam lr`0.05`、12 epochs、batch64、无early stopping/scheduler；valid与target test不参与fit或选择。B0 native，U1 uniform、B1 static、P1 checkpoint、N1 shifted四臂各用相同一标量recipe。




- **判定合同**：P1必须对B0/U1/B1/N1四个ACC contrasts全部通过overall、逐seed、至少5/9 targets及9/9 LOO正向门，才可`screen_positive_support_specific`。任一control失败都有独立冻结路由；不依据结果改gate bound、epoch、lr、mask、shift或seed。









## D-155：FCPSM-v0.1 通过 S5 实现验证并停在 formal discovery 执行边界（2026-08-21）









- **实现验证**：冻结机制已落到独立wrapper与runner；D0的13项identity、单参数、上下界、context/position保持、18-pair provenance、partition隔离、非零梯度和backbone冻结断言全部通过，unit=`4/4`。




- **受限check**：仅运行target0/seed0、64 source trials、16 target trials、2 epochs。五个arms均完成，`5/5`结果行、`14/14`manifest条目和全部prediction artifacts通过机械校验；该运行明确为engineering evidence，未读取或使用ACC排序作科学判断。




- **证据状态**：exact cycle推进到`S5 / implementation_verified`，signal仍为`not_tested`，claim release=`none`。formal scope仍是9 targets×2 seeds×5 arms，含72个source-only scalar fits与90个target evaluations。




- **权限边界**：formal discovery只写入cycle内实验队列；未制作immutable Bundle，未上传、未远端执行，也未授权benchmark、confirmation或claim。下一步必须取得独立formal discovery execution授权。









## D-156：FCPSM-v0.1 accepted immutable local Bundle r3 完成并登记 queue #27（2026-08-21）









- **用户授权与对象**：用户明确要求制作本地Bundle。Accepted Bundle=`2026-08-21_fcpsm_v0_1_dsainet_bnci2014001_lr22_s01_ccmu_r3`，只承载冻结的FCPSM-v0.1-r1五臂discovery，不改变cycle/family/claim状态。r1因打入会变化的queue文档unused；r2在Bundle-root gate暴露遗漏间接import而unused；三版均未上传。




- **冻结内容**：18个DSAINet checkpoints、18个SOFC artifacts、B0/U1/B1/P1/N1五臂runner、D0/unit check、2-pair representative pilot与18-pair formal task plan。Formal总计90 target evaluations和72次source-only one-scalar fits；调度固定`ccmu-lane-autopilot-v3 / 1 lane per GPU`。




- **本地完整性**：accepted r3 archive=`5,280,976 bytes`，outer SHA-256=`d254b73fd582e474d8dac72c807382748a3536bffcdec710a567b2b48a44f2fd`；101个tar members通过路径/类型安全检查，67/67 source manifest本地重算一致，plan/schema、Bundle-root import、4/4 unit tests与unauthorized task-shard拒绝门通过，credential-name scan=`0`。




- **权限边界**：Bundle-local config具备在未来受控submit后运行formal task shard的能力，但同时冻结`upload_authorized=false`与`remote_execution_authorized=false`；权威cycle/config仍保持formal/upload/remote=false。当前仅`local_bundle_built_waiting_upload_and_execution_authorization`，未upload/stage/submit，不构成性能或机制证据。




- **查新与边界**：ReZero、IA3、mask-guided residual及MI temporal saliency均构成明确近邻，focused novelty=`4/10 / PROCEED_WITH_CAUTION`。允许把它作为SCCD evidence-driven child，禁止称为普适新modulation算法。外部method reviewer=`REVIEW_UNAVAILABLE`。




- **当前权限**：授权本地implementation、D0-C/P/N与target0/seed0 bounded engineering check；formal 18-pair discovery、上传、远端、benchmark与claim仍为独立边界。









## D-157：FCSM-v0.1 未形成 factorial mixer 正信号，精确 cycle 负边界关闭（2026-08-22）









- **回拉与修复**：RunId `2026-08-21_fcsm_v0_1_ccmu_r1-full-w1` controller 状态为 complete，archive SHA-256 `50cbbc59…`。controller tar 只有调度元数据，缺少 `subject_results.csv`（entrypoint 只核 18 个 `.pth` 计数）。科学 CSV 从远端 job 输出补拉：P1 `d68ddb13…`。B0 按冻结合同复用 SCID 原 Mixer1D 18 行，CSV `747d3f6c…`；`BNCI2014001_official_preproc/X.npy` SHA-256 与训练超参/split/环境闭合。




- **冻结判定**：18/18 配对完整。P1/B0 ACC mean=`59.144/59.857%`，overall P1−B0=`−0.714 pp`，seed1/2=`−0.405/−1.022 pp`，仅 `3/9` subjects 与 `4/18` units 正向，无 collapse。主方向为负，S6D=`no_signal`。




- **精确解释**：结果只说明容量匹配的 FactorialMixer1D 相对原 Mixer1D 没有可筛选 native LOSO 效用。它不断言尺度语义不存在，也不改写 SCID 的 prototype 负边界。S8 的 `+7.031 pp` 不得作为救援。




- **Family/S9**：按 `S6D_direct_exception` 进入 S6M，不伪造 S6R。`sstdpn-factorial-channel-scale-mixer` 为 `exploratory / paused(evidence_gap)`，budget `0/1`，child=`not_ready / missing_evidence_anchor`。Exact FCSM-v0.1 以 `negative_boundary / completed_not_promoted` 关闭。permutation/同容量对照不运行。




- **权限与 claim**：不重开 prototype family，不改 mix 初始化/kernel，不补 seed/dataset。外部 result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`；确定性负向门仍可执行，claim release=`none`。









## D-158：FCPSM-v0.1 修复 prediction_file 路径降级逻辑并完成 local Bundle r4 制作（2026-08-22）









- **问题与诊断**：FCPSM-v0.1 r3-check 在远端执行时，`scripts/run_fcpsm_v0_1_dsainet.py` 写入 `prediction_file` 字段时调用 `relative_to(PROJECT_ROOT)`；当输出路径为 `CCMU_OUTPUT_DIR`（外部挂载输出目录，不在 Bundle 根目录下）时抛出 `ValueError` 导致 check 异常中止。与 SAFSS r2 为同类工程问题。r3 已冻结并不再复用。




- **代码修复与本地验证**：修改 `scripts/run_fcpsm_v0_1_dsainet.py` 中的 `prediction_file` 和 `meta_path` 解析逻辑，使用 `is_relative_to` 判定：仅在路径位于 `PROJECT_ROOT` 内时生成相对路径，否则安全降级为绝对 POSIX 路径。本地 4/4 单元测试通过，并在独立外部临时目录完成 check 模式前向与保存校验。




- **本地 Bundle r4 就绪**：运行 `scripts/remote/prepare_fcpsm_dsainet_ccmu_bundle.ps1` 完成 accepted local Bundle `2026-08-21_fcpsm_v0_1_dsainet_bnci2014001_lr22_s01_ccmu_r4` 制作。




  - archive: `tmp/remote_upload/2026-08-21_fcpsm_v0_1_dsainet_bnci2014001_lr22_s01_ccmu_r4_upload.tar.gz`




  - bytes: `5,281,002`




  - outer SHA-256: `c2ac188486bcf38567dd9e54444c9797d05f9826b21981006b507d739d7861f4`




  - 101 项 tar member 路径与类型安全校验通过，67/67 source manifest 本地重算一致，v3 调度计划与环境指纹验证 pass。




- **状态与权限边界**：FCPSM-v0.1 r4 已登记至排队系统；r4 Bundle 未上传、未提交远端执行，不改变 exact cycle 的 formal/upload 权限边界，未产生任何性能证据，claim release=`none`。等待后续上传与执行授权。









## D-159：FCPSM-v0.1 五臂正式屏为 ambiguous，exact child 归档且 family exhausted（2026-08-22）









- **回拉与完整性**：RunId `2026-08-21_fcpsm_v0_1_ccmu_r4-full-w1` 已 complete→fetch→verify→intake；archive SHA-256=`6cc69756d2b3e393508d915dd9b6da2e83311ba1e42d46faccab33d6d95b8331`。390 个安全 tar member、348/348 Bundle manifest、18/18 task、90/90 arm evaluation、72/72 source-only scalar fit 完整。90 个 prediction NPZ 的哈希、indices、labels、logits、predictions、theta/gain 与 ACC/Kappa/F1/NLL/margin 均复算一致；五臂 pair provenance、18 份 task config 与六份冻结 source/contract 均通过。




- **冻结判定**：B0/U1/B1/P1/N1 ACC=`84.568/84.722/84.664/84.742/84.471%`。`G_native=+0.174 pp`，但 seed0/1=`-0.116/+0.463 pp`，故未过逐seed稳定门；`G_uniform/G_static/G_shift=+0.019/+0.077/+0.270 pp`也分别因seed、正向target或LOO失败。四个contrast均非stable-positive，按预声明剩余分支判`ambiguous`。




- **精确解释**：full context 保留后没有出现 SAFSS 的明显负差，但这个小总体方向跨 seed 不稳定；因此只能说“hard deletion 的删除侧诊断没有被推翻”，不能说 support conditioning、checkpoint conditioning、location specificity或generic coarse scaling形成稳定性能效用。P1虽在18/18 units降低source-train CE，但相对B1仅改变8/5,184个target判决、净增4个正确；checkpoint-specific transfer很弱。该描述不单独构成机制门。




- **S6M/S9**：FCPSM-v0.1 不进入 S7Q、benchmark、confirmation，以`prototype_archive / completed_not_promoted`关闭。Parent SCCD 的范围受限 deletion decomposition 保留；family=`exploratory / exhausted`，child budget=`1/1`、falsification coverage=`decisive`，不创建第二个同thesis child或结果驱动rescue。




- **审查与claim**：独立 experiment-audit/result-to-claim backend 不可用，verdict=`REVIEW_UNAVAILABLE`；确定性完整性审计不能代替独立背书。Claim release=`none`；不补seed/target，不改mask/bound/fit recipe，不释放性能、机制、泛化或新颖性结论。









## D-160：DCBS-v0.1 建立 ordered-concat 槽位敏感锚点，family 等待唯一 set-fusion child 授权（2026-08-23）









- **回拉与完整性**：RunId `2026-08-21_dcbs_v0_1_ccmu_r2-full-w1` 已 complete→fetch→verify→intake；archive SHA-256=`5e21d1fbb3aabb9165d30230938d933f8e9c4d544e9db006d3a7f47af044e4b8`。本地复算 27/27 Bundle manifest、45/45 checkpoint SHA-256 与 45 个唯一 subject×seed 组合全部通过；config、baseline、analyzer 与 task-runner 指纹和 source manifest 一致。




- **冻结判定**：median mean-abs logit shift=`1.857546329498291`，prediction disagreement=`0.375`；`9/9` subjects、`5/5` seeds 通过，最小单 checkpoint shift 仍为 `0.9239280819892883`。冻结 outcome=`slot_identity_anchor`，S6D=`screen_positive`。




- **精确解释**：结果只证明当前 DSAINet `Linear(2E,C)` 对两个 pooled halves 的 concat 顺序稳定敏感；不证明两支已有稳定 fine/coarse 语义身份，也不证明 descriptor-conditioned/permutation-invariant fusion 会提高准确率。SAFSS/SCCD/FCPSM/CBLR 证据不并入本 family。




- **S6M/S9**：正式 45-checkpoint 面板已覆盖全部预声明 subject/seed 稳定性维度，因此以 `S6D_direct_exception` 完成 family review，不伪造 S6R。Exact cycle=`supporting_evidence / diagnostic_complete`；family=`promising / decision_pending`、budget=`0/1`、falsification coverage=`partial`。唯一 child 已可冻结为共享 branch encoder + 声明 kernel descriptor conditioning + permutation-invariant set pooling 的 head replacement，但创建与 budget 消耗须用户另授。




- **权限与 claim**：不自动创建 child、实现、训练、上传、进入 benchmark 或释放 claim；禁止 target-dependent routing。外部 result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`，claim release=`none`。









## D-161：RBIA-v0.1 未发现可复现 branch index/function mismatch，DCBS set-fusion child 撤回 ready（2026-08-23）









- **精确对象**：`2026-08-23_dsainet_realized_branch_identity_audit`，作为 `dsainet-descriptor-conditioned-branch-set` 的零训练 `diagnostic_probe`；不消耗 child budget。




- **完整性**：formal r2 45/45 verified checkpoints、270/270 correspondence rows、2,880 target trials；native identity error=`0`，float64 additive reconstruction max error=`4.44e-15`；NPZ shape/finite、hash、trial 与冻结 gate 独立复算全部通过。首次 formal 因重复 forward 浮点误差正确标为 invalid，修复后以新 r2 取证，旧目录不用于判读。




- **跨 seed identity**：activation/pooled/contribution median same−swap CKA margin=`+0.065893/+0.024684/+0.037996`，分别 `8/9+10/10`、`6/9+9/10`、`7/9+8/10` 通过预冻结 same-index stability gate；没有 stable swapped panel。




- **kernel validity**：learned residual 45/45 可观测；`[11,15]` vs `[3,7]` empirical mean-lag ratio median=`2.1556`，9/9 target、5/5 seed 通过。只支持方向性 effective scale，不是精确理论 RF 或生理时间尺度。




- **决定**：冻结 outcome=`aligned_stable`，mismatch hypothesis=`no_signal`；RBIA exact=`negative_boundary / diagnostic_complete`。DCBS slot dependence 仍成立，但不足以支持当前 descriptor-conditioned permutation-invariant child。




- **Family route**：`promising / paused(evidence_gap)`；child=`not_ready/missing_evidence_anchor`，budget 保持 `0/1`。不以换 descriptor、threshold、seed、window、dataset 或 fusion 作结果后救援。




- **证据边界**：只覆盖 BNCI2014001 official-preproc LOSO 45 checkpoints；不改写 BBTS/BACL/TBCD 的跨条件异质性。外部 experiment-audit/result-to-claim=`REVIEW_UNAVAILABLE`，claim release=`none`。









## D-162：BSSF-v0.1 未形成混频前空间残差正信号，精确 cycle 负边界关闭（2026-08-23）









- **回拉与完整性**：RunId `2026-08-21_bssf_v0_1_ccmu_r2-full-w1` 已 complete→fetch→verify→intake；archive SHA-256=`cc942e4de4134fc7c13f19458261dcf6499f670cdb770ba01450a81bb526ff98`。18/18 task、split fingerprint 与 data contract SHA 均与 BSRD B0 闭合。预测 NPZ 未写出，P1 checkpoint 未拉回本地；self integrity=`WARN`。




- **冻结判定**：B0 复用 BSRD 未改 SMANet 18-unit acquisition，不是 45-unit 六格表。P1/B0 ACC mean=`55.777/56.047%`，overall P1−B0=`−0.270 pp`，seed0/1=`−1.196/+0.656 pp`，仅 `4/9` subjects 与 `7/18` units 正向，无 collapse。主方向为负，S6D=`no_signal`。




- **精确解释**：结果只说明当前零初始化低秩 band-specific 空间残差相对未改 SMANet 没有可筛选 unified100 LOSO 效用。它不断言频带空间图不存在，也不改写 BSRD 的 routing 负边界。S3 seed1 的 `+6.424 pp` 不得作为救援。




- **Family/S9**：按 `S6D_direct_exception` 进入 S6M，不伪造 S6R。`smanet-band-specific-spatial-factorization` 为 `exploratory / paused(evidence_gap)`，budget `0/1`，child=`not_ready / missing_evidence_anchor`。Exact BSSF-v0.1 以 `negative_boundary / completed_not_promoted` 关闭。A1/N1/shuffle 不运行。




- **权限与 claim**：不重开 routing family，不改 rank/初始化，不补 seed/dataset。外部 result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`；确定性负向门仍可执行，claim release=`none`。









## D-163：WOET-v0.1 建立 4-sample origin 锚点，family 等待唯一 multi-origin child 授权（2026-08-23）









- **回拉与完整性**：RunId `2026-08-21_woet_v0_1_ccmu_r2-full-w1` 已 complete→fetch→verify→intake；archive SHA-256=`a5d36903be01198041492193bc6e8176693a21b814ebeb36cbf5a2d5eee50ab9`。45/45 unique subject×seed、analyzer/config/test SHA 与 S5 及 Bundle source manifest 一致；独立复算与远程 `aggregate.json` 逐项相同。check/pilot 只作工程完成。




- **冻结判定**：median origin disagreement=`0.03125`，repeat floor=`0.0`，shuffle=`0.59375`；`7/9` subjects、`4/5` seeds 通过；31/45 checkpoint `≥ 0.03`，shuffle 无一小于 origin。冻结 outcome=`window_origin_anchor`，S6D=`screen_positive`。




- **精确解释**：结果只证明冻结 STGMFM 对 4-sample circular origin shift 的预测变化高于重复前向 floor，且小于破坏性 time shuffle。median 刚过门（`2/64` trial）。不证明 TimeGraph 已经错误，也不证明训练 2–3 origin 会提高 LOSO。OSE/ODRF/OCSO/CFUD 证据不并入。




- **S6M/S9**：正式 45-checkpoint 面板已覆盖全部预声明稳定性维度，因此以 `S6D_direct_exception` 完成 family review，不伪造 S6R。Exact cycle=`supporting_evidence / diagnostic_complete`；family=`promising / decision_pending`、budget=`0/1`、falsification coverage=`partial`。唯一 child 已可冻结为 2–3 origin 训练 P1，对照 native B0 与推理时 origin logit 平均 A1，但创建与 budget 消耗须用户另授。




- **权限与 claim**：不自动创建 child、实现、训练、上传、进入 benchmark 或释放 claim。1-checkpoint smoke 不是本屏分母。外部 result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`，claim release=`none`。后续 child 创建见 D-165。









## D-165：创建 MOT-v0.1 为 WOET 唯一 diagnosis-driven child（2026-08-23）









- **授权范围**：用户明确要求创建 child。消耗 `stgmfm-window-origin-equivariance` 唯一 `1/1` budget。冻结 S2-lite 合同、wait-what、S3 delta 与 S4 实验计划。




- **精确对象**：`2026-08-23_stgmfm_multi_origin_window_training`。训练时均匀采样 circular roll origin∈`{0,4}`，测试主协议 origin 0；A1 复用 B0 权重并对 `{0,4}` logit 平均。不改 TimeGraph / 损失 / 窗口长度。不继承父 `screen_positive`。




- **探索资格**：self-review `supporting_candidate`，novelty `2.8/10`。近邻是 TTA 与 temporal-shift 增强；A1 为必做对照。无项目内重复失败，`go`。




- **屏合同**：BNCI2014001 LOSO seeds `{0,1}` × 9 subjects，18 P1 新训练。`screen_positive` 要求 P1_native−B0 与 P1_native−A1 同时为正，且 ≥5/9 subject、两 seed 同号、单 subject 不超过正向增益一半。




- **未授权**：S5 实现、D0/check/smoke、训练、上传、远端执行、seeds 2–4、004、第三个 origin、benchmark、claim release。




- **风险**：父 median 仅 `0.03125`，本 child 可以为 no-signal；负结果不改写父锚点。S5 见 D-166。









## D-166：MOT-v0.1 完成本地 S5，停在 S6D 授权前（2026-08-23）









- **实现**：`src/models/mot_stgmfm.py` 在 `STGMFMAdapter` 前对时间维做 `{0,4}` circular roll；训练随机、测试 origin 0。未改 TimeGraph / 损失 / 窗口。




- **D0**：10/10 PASS（roll 代数、origin-0 与 B0 一致、梯度有限、参数量相同、A1 非退化、B0 SHA strict load、LOSO target held-out）。D0-O 未跑。




- **工程运行**：check `2026-08-23_mot_v0_1_check` 跳过训练；smoke `2026-08-23_mot_v0_1_smoke` 为 subject 0 / seed 0 / 2 epoch。smoke 数字不得写入 C-MOT-PERF/MECH。




- **未授权**：18-unit S6D、上传、远端、seeds 2–4、004、第三个 origin、benchmark、claim。S6D 启动见 D-167。









## D-167：MOT-v0.1 S6D 启动：A1 本地完成，P1 18-unit 远端排队（2026-08-23）









- **授权**：用户确认正式 18-unit 发现屏。本地 8 GB / 约 47 小时顺序训练超出手册范围，改走 [REDACTED_MACHINE] GPU0。




- **A1**：18/18 B0 checkpoint 零训练评估完成。重算 origin-0 ACC 与 2026-07-22 归档表逐单位一致。mean A1−B0=`−0.125 pp`。这只是测试时平均对照，不是 P1 结论。




- **P1**：Bundle `2026-08-23_mot_v0_1_stgmfm_bnci2014001_loso_s01_ccmu_r1` 外层 SHA=`4019506c69492d2147fcd15143f963ade716175839de4ad8a3928fcdec1d5e82` 已 staging。队列顺序 ACLT-v0.1 full → DRPG-v0.1 r3 → MOT-v0.1。




- **未完成**：18 次 100-epoch 训练、S6D 判读、claim。seeds 2–4 与 004 仍不跑。判读见 D-168。









## D-168：MOT-v0.1 18-unit no-signal，window-origin family exhausted（2026-08-23）









- **回拉与完整性**：RunId `2026-08-23_mot_v0_1_ccmu_r1-full-w1` complete→fetch→verify→intake；archive SHA-256=`76153be73d26a72d533395eaebf2c794b46327dcd11e3affdde3ec1d72fddc31`。18/18 P1 单元与 prediction 齐全；A1 18/18 的 B0 native 与 2026-07-22 归档表逐单位一致。




- **冻结判定**：subject-mean P1−B0=`−0.627 pp`，seed0/1=`+0.405/−1.659` pp，正向 subjects=`4/9`；P1−A1=`−0.502 pp`。PERF 与 MECH 均未过门，S6D=`no_signal`。




- **精确解释**：只说明冻结 `{0,4}` multi-origin 训练在该 LOSO 屏上没有可筛选增益。不改写父 WOET `window_origin_anchor`，也不把 A1 升级为方法。




- **S6M/S9**：`S6D_direct_exception`；family=`exploratory / exhausted`，budget=`1/1`。Exact MOT=`negative_boundary / completed_not_promoted`。不得救援式换 origin/位移/seed。




- **claim**：外部 result-to-claim=`REVIEW_UNAVAILABLE`；确定性负向门可执行；claim release=`none`。









## D-164：BSRA-v0.1 发现 learned-delta 高相似，但否定双向功能可替代锚点（2026-08-23）









- **精确对象**：`2026-08-23_dsainet_branch_similarity_replaceability_audit`；它是独立




  `dsainet-branch-functional-redundancy` family 的 zero-training core diagnostic，不是 DCBS rescue，不继承




  RBIA/DCBS signal 或 budget。




- **完整性**：formal r2 复用 RBIA 的 45/45 verified checkpoints、每 checkpoint 64 held-out trials；10 个




  native/counterfactual variants、450 variant rows、3150 stage rows 完整。state digest 45/45 前后一致，native




  no-hooks replay identity error=`0`，artifact manifest、复制 hash 与独立 gate recompute 全部 pass。r1/r2




  scientific arrays byte-exact；r1 因 identity 门只闭合同一次 hook 而降为 superseded engineering artifact。




- **相似性来源**：native learned-delta/pooled/contribution CKA median=`0.7384/0.8491/0.7643`；learned-delta




  gate 以 7/9 targets、5/5 seeds 通过。big-residual-off 的 pooled/contribution CKA=`0.8483/0.7507`，几乎




  保留 native；inter-off 降至 `0.3805/0.2838`，说明 final similarity 的主要显式放大来自 inter-attention，




  不是可在 pooled 后减去的 `alpha_b*a0`。




- **可替代性负边界**：delta1-off/joint=`0.8338`、delta2-off/joint=`0.3844`；roll panel=




  `0.8287/0.3061`，0/9 targets、0/5 seeds 通过 bilateral gate。joint-off 改变 673 个 native decisions，其中




  两个 single-off 均保留 native 的只有 133 个（`0.1976`）。冻结 outcome=`similar_but_not_replaceable`。




- **Family/S9**：exact cycle=`negative_boundary / diagnostic_complete`；family=`exploratory /




  paused(evidence_gap)`，child=`not_ready/missing_evidence_anchor`，budget=`0/1`，falsification coverage=`partial`。




  不创建 decorrelation/diversity/complementarity child，也不转 branch2 pruning/weighting rescue。




- **审查与 claim**：external experiment-audit/result-to-claim backend 未暴露，verdict=`REVIEW_UNAVAILABLE`；




  deterministic self-check 不能替代独立审阅，claim release=`none`。









## D-169：建立 MVCNet paper–release dual-branch fusion reconciliation 独立 cycle（2026-08-24）









- **授权与身份**：用户明确授权将 IPB 同快照 re-entry 登记的 `new_family_candidate` 建立为独立 cycle `2026-08-24_mvcnet_paper_release_fusion_reconciliation`（MPRF-v0.1），family=`mvcnet-paper-release-fusion-reconciliation`。它不是 IPB child，不继承 IPB 的负结果、selection 资格、运行授权、benchmark 或 claim readiness，也不消耗 `mvcnet-inference-path-bridge` 的 child budget。




- **研究边界**：先核清论文所述“双分支特征 concat 后分类”与 release-compatible `MVCNet_LOSO.py` 中 `base_network` logits、`netE/netP` 对比路径之间的精确 architecture/provenance 差异；在论文、源码、config、数据与协议形成一个冻结规格前，不把 mismatch 称为 bug，也不把任一 concat/projector/bridge 变体当作 paper-aligned baseline。




- **S0 转序边界（历史）**：建 cycle 时仅授权进入 S1 paper/source/config grounding；当时 Idea Contract、实现、诊断计算、训练、上传、远端执行、benchmark、confirmation 与 claim release 均未授权。




- **S1 结论**：最终期刊记录与 arXiv v4 均声明 final representations fused；全文 Table I/Algorithm 1 规定 `F(Concat(B_c(x), B_t(x)))`。官方仓库 commit `53e1229a` 的分类 CE、验证和保存则只使用 `base_network=IFNet+netC`，`netE/netP` 只进入 CVC/CMC，故 architecture mismatch 已确认，但不得升级为 bug 结论。




- **S1→S2 转序边界（历史）**：S1 artifact=`_work/S1_PROVENANCE_GROUNDING.md`。论文 2-layer vs release 1-layer 是独立差异；四分类 UEP 排除在本 binary cycle 的首轮公平比较外。S2 只审查 fusion-only 单变量合同，不能称完整论文复现。




- **S2 freeze**：MPRF-P1-v0.1 将唯一差异冻结为 `W_c f_c+b → W_c f_c+b+W_t f_t`，`W_t` 是 `(2,512)`、zero-init、唯一注册的 trainable Parameter。B0/P1 共用 canonical pairing manifest；loss、Adam、target-online final-epoch validation、strict inference-only checkpoint 与六项 disposable construct gates 均已唯一化。




- **审查与解释**：`research-refine` 经 3 轮独立 `gpt-5.6-sol` xhigh fallback review，score=`8.00→8.84→9.22`，最终 `READY / Contract Freeze READY`；Codex MCP 与共享输出协议缺失使 review completeness 保持 degraded。首次 `WAIT_WHAT_v0.1` 已完成，不改变合同或证据。




- **当前状态**：cycle=`active / S3_novelty_scope_pending`，Idea Contract=`frozen / MPRF-P1-v0.1`，`authorized_run_level=none`。READY 只允许 S2 文本冻结；代码、construct run、训练、上传、远端、benchmark、confirmation、control/rescue 与 claim 均未授权。









## D-170：建立 DSAINet RACR 独立 cycle/family，并冻结 supporting-only S2–S4（2026-08-24）









- **授权与身份**：用户明确授权把 Foundry `IF-20260823-01 / DS-01` 建立为 exact cycle `2026-08-24_dsainet_role_anchored_conjunctive_readout`（RACR-v0.1），family=`dsainet-role-anchored-conjunctive-readout`。Foundry 排名只作为 selection history，不是科学证据。




- **准入锚点**：RBIA 在 001 冻结 scope 支持 same-index stable realized roles 与 effective-scale ratio `2.1556`；BSRA 同时给出高相似但 `0/9 target、0/5 seed` 双向可替代。两者只把问题收敛为“native additive readout 是否遗漏同-trial joint evidence”，不构成 RACR signal。




- **family 隔离**：RACR 不是 SAFSS/FCPSM、DCBS、BSRA 或 condition-dependent realization 的 child；不使用 support/window/gain/routing、lag/equalizer、decorrelation/set fusion 或 alpha/init repair，也不继承相邻路线的 signal、budget、执行授权、benchmark 或 claim。




- **跨数据集边界**：001 stable identity 不得外推到 004；004 当前只能作为未来另行冻结的 scope/transfer stress，不能作为准入正锚点或泛化主张。




- **S2 精确冻结**：RACR-v0.1 固定为 `E=40,C=4,rank=4` 的 bias-free ordered Hadamard residual，保留 native marginal logits，并用单一 zero-init `tanh` scalar gate 限幅；新增 `337` 参数。必要 M1 为 hidden-4 bias-free GELU residual，同为 `337` 参数。首次 `WAIT_WHAT_v0.1` 已完成；pairing falsifier 只在 source-validation 内做 class-preserving cyclic shift，不读取 target label。




- **S3 查新与角色**：ICLR 2017 low-rank Hadamard 形式为直接碰撞；SecNet/SecTNet/MSAttNet 已覆盖 MI-EEG 多尺度/多分支 second-order 邻域。focused self-review=`4/10 / proceed_with_caution_supporting_only`，不是 novelty clearance；candidate role 从 primary 收窄为 supporting，通用 bilinear novelty claim 不成立。




- **S4 计划**：冻结 B0 native、P1 RACR、337-param M1；BNCI2014001 LOSO seeds `[0,1]` × targets `0..8` 的最小发现块需要 P1/M1 各 18 个新训练 unit，并同时通过 `P1−B0`、`P1−M1` 与 source-only pairing 门。若失败，不换 rank/gate/threshold/seed/window 或 child 救援。




- **S5 实现验证**：以最小 readout-only adapter 落地 P1/M1，未改 DSAINet backbone、native classifier、损失、训练器或协议。标准单元测试 `4/4`、D0 `12/12`、P1/M1 real-data check `2/2` 与两步 synthetic smoke `2/2` 均通过；两臂参数均为 `75,982`（B0=`75,645`，增量 `337`），zero-gate 对 native logits 的最大误差为 `0`。source-only class-preserving pairing 保持 branch-2 multiset 且激活 residual 后 logits 有变化，梯度链可达。以上均为 engineering / implementation evidence，不读取或比较性能结果。




- **S6D 本地准备**：用户授权 S6 后又明确本轮只做本地准备、不直接上传。历史 B0 虽有 45-row archive，但缺少当前合同要求的逐 unit split fingerprint 与 checkpoint 闭环；为避免近似 baseline 混入，r2 Bundle 固定 B0/P1/M1 × seeds `{0,1}` × targets `0..8`=`54` units，其中新增 B0 18 units 只作 exact-paired provenance repair。r2 BundleId=`2026-08-24_racr_v0_1_dsainet_bnci2014001_loso_s01_ccmu_r2`，outer SHA-256=`cf05400648b0aebef98f0eca35d5acb1cfe79a5eced23392fc4905cdad71c533`；135 archive members、103-file source manifest、task identity、scheduler plan 与 bundle-internal unit tests 均通过。r1 因产生 `__pycache__` 而冻结不用。




- **r5 S6D 与完整性**：r5 full 已 `fetch/verify/intake`；B0/P1/M1 × seeds `{0,1}` × targets `0..8` 的 `54/54` unique units、predictions、checkpoints、config、split fingerprints 与 exact paired signatures 均闭合。P1/M1 的36个 validation-best checkpoint 已只读回拉，SHA-256、source-validation split、class-preserving branch-2 permutation 与类内 marginals 均验证通过。




- **冻结结果**：B1 P1−B0 overall=`+0.000 pp`，seed=`+1.389/−1.389 pp`，仅5/9 target 两 seed 平均为正；B2 P1−M1 overall=`+0.569 pp`，但 seed1=`−1.138 pp`；P1 source-only `pair_margin_drop` 在18个 P1 checkpoint 均为`0`。因此 S6D=`no_signal`，关闭 exact rank-4、single zero-start gate、signed Hadamard RACR-v0.1。




- **后续只读边界**：B0 pooled representation 的 classwise true-vs-shuffled CKA drop=`+0.607858`（两 seed 正、9/9 target过门）只说明 paired dependence。随后的18-unit fixed `[p1;p2;p1⊙p2]` held-out source probe 为 `no_anchor_under_fixed_probe`（true-pair interaction increment=`−0.056406` nats）；两者均不支持 native additive underuse 或 RACR interface bug。




- **当前状态**：cycle=`paused / S6D_no_signal`，`gate_decision=no_go`，`authorized_run_level=S6D_full_discovery_completed_and_locally_intaken`，`highest_evidence_level=selection_used_discovery_screen_no_signal`。仅等待明确 `S6M direct exception` 决定；不得 S6R、加 seed、调 rank/gate/threshold/window、重训、创建 RACR child、benchmark、confirmation 或 claim release。外部 reviewer 为 `REVIEW_UNAVAILABLE`。









## D-171：建立 DSAINet RAIA 独立 cycle/family，停在 S0 准入边界（2026-08-27）









- **授权与身份**：用户明确授权将 Foundry `IF-20260825-01 / DS-01 RAIA` 建立为 exact cycle `2026-08-27_dsainet_role_asymmetric_interaction_adapter`（RAIA-v0.1），family=`dsainet-role-asymmetric-interaction-adapter`。它是新 family 的首个 `core_test`，不是 RACR、BSRA、RBIA/DCBS、PCXE 或其他既有路线的 child。




- **准入边界**：原生 `InterAttnBlock` 在两个有序 cross-branch 方向复用同一 MHA 与 FFN；BSRA 的冻结 001 counterfactual 记录到方向非对称的功能响应。二者只形成“共享算子是否限制有序协作”的待检验问题，不证明共享参数有害，也不构成 RAIA 的机制或性能信号。RACR 的 post-pool no-signal 仅划定不同插入点的负边界。




- **隔离与查新边界**：RAIA 的 baseline defect 与核心因果论题独立于 RACR 的 readout conjunction、BSRA 的 redundancy 假设和 DCBS 的 identity/mismatch 假设；不继承它们的 signal、budget、授权、benchmark 或 claim。Foundry 的 nine-paper literature pack 仍全部 `UNVERIFIED`，不释放 novelty claim。




- **当前状态**：cycle=`active / S0_admission_bound_pending_S1_S3`，family=`exploratory / active`，`authorized_run_level=none`，`highest_evidence_level=conceptual`。尚未冻结 adapter 的公式、rank、参数量、B0/P1/控制、数据范围、seeds、阈值或实验计划；也未调用 `wait-what`。




- **未授权边界**：本次只创建 family/cycle 及其状态记录。S1–S3 grounding、Idea Contract、实现、诊断、训练、上传、远端执行、benchmark、confirmation 与 claim release 均未授权。未来合同必须包含 shared equal-capacity control 与 direction-label swap，且不得将 Foundry 排名或 BSRA 不对称反推为形式/参数选择。









## D-172：RAIA 完成 S1-S3 静态冻结，作为 supporting candidate 停在 S4 决策边界（2026-08-27）









- **冻结合同**：在原生 beta-scaled attention message 后插入 bias-free、零起点输出的低秩残差；每个方向 rank=4，P1 共 640 参数。C1 为同 640 参数、两个方向共用的 rank=8 adapter；A1 对同一 P1 checkpoint 只交换两个方向的 adapter 标签、不重训。原生 MHA、FFN、normalization、dropout、beta、pooling、classifier 与 DSAINet 训练档案均不改。




- **grounding 与查新结论**：CrossViT、BCAT、MI-CAT、MSVTNet 及低秩 EEG adapter/attention 邻域表明，双向/多尺度交互、非共享注意力和低秩本身均不是可主张的新颖点。RAIA 只保留为一个宿主内、可证伪的问题：方向索引能否产生 C1 与 A1 均不能复现的 signature。项目 paper verifier 不可用；没有机器核验的 novelty clearance，也没有独立有利评审。




- **当前状态**：cycle=`active / S3_grounding_contract_novelty_completed_pending_explicit_S4_authorization`，candidate_role=`supporting_candidate`，gate=`hold`，最高证据仍为 conceptual。S1 grounding、S2 Idea Contract 与 wait-what、S3 self review 已完成；没有代码、诊断、训练、上传、远端运行、benchmark 或 claim。




- **下一边界**：只有新的明确授权才能创建 S4 实验计划；该计划只能操作化已冻结的 B0/P1/C1/A1，不得 rank/gate/init/seed/subject 后验搜索，也不得因未来失败把 RACR、PCXE、support/window、routing、lag、equalizer、decorrelation 或 BNCI2014004 作为救援路径。









## D-173：RAIA S4 计划冻结，等待 S5 实现验证授权（2026-08-27）









- **计划范围**：冻结 `RAIA-S4-v0.1`：BNCI2014001 official-preproc、LOSO、targets `0..8`、seeds `{0,1}`、`mieeg-uep-v1.0 / tp-dsainet100-v1 / validation_best`。B0/P1/C1 各 18 个训练 unit，A1 仅对 18 个 P1 checkpoint 交换方向 adapter 后评价，不重训；总计 54 训练 + 18 evaluation units。




- **门禁与判读**：先后固定为 preflight → D0-C/P → D0-N → check → smoke → S6D。S6D 仅在 P1-B0、P1-C1、P1-A1 三个对比全部 overall/两 seed/至少 5/9 target/全部 LOTO 为正，且无 `P1-B0 <= -10 pp` target collapse 时为 `screen_positive`；任何 overall 非正为 `no_signal`，其余稳定门失败为 `ambiguous`。A1 只回答 direction-label specificity，不能被说成第二个训练模型。




- **当前状态**：cycle=`active / S4_experiment_plan_frozen_pending_explicit_S5_authorization`，`gate_decision=go` 只表示计划已就绪；`authorized_run_level=none`、最高证据仍为 conceptual。未实现、未作 D0、未 check/smoke、未训练、未建 Bundle、未上传或远端执行。




- **停止与后续**：S5 必须另行明确授权。S4 不允许改 rank、init、activation、gate、bias、normalization、seed、target、dataset 或新增控制；若未来 S6D 非正/不稳，不补 seed 或换参数救援，只等待独立 S6M 路由决定。









## D-174：RAIA S5 实现与最小验证闭合，停在 S6D 授权边界（2026-08-27）









- **完成范围**：用户明确授权 S5 后，RAIA-v0.1 的最小实现、P1/C1 固定配置、单元测试、D0-C/P/N、B0/P1/C1 zero-epoch check、seed0/target0/2-epoch smoke 与两个 A1 evaluation-only 闭合均完成。P1 使用两个独立 rank-4、bias-free adapter；C1 使用一个 shared rank-8 adapter；两者都比 B0 多 640 参数。A1 对已保存 P1 state dict 只交换方向标签，不重训且不改变 state。




- **实现证据**：RAIA 单元测试 `5/5`；D0-C/P/N `18/18`。D0 同时确认 synthetic 与真实 source batch 的 zero-U B0 identity、原生状态映射、source-only LOSO split、两步 U/V 梯度可达，以及 P1/C1 的精确参数/共享结构。三个 smoke 的 split fingerprint 一致；A1 对 check 和 smoke P1 checkpoint 均严格加载、同索引、无重训、无 state mutation。




- **证据边界**：上述 smoke 只用于链路与产物闭合，未读取、比较或解释其性能数值。因此 `C-RAIA-PERF-001` 与 `C-RAIA-MECH-001` 仍为 `untested`，novelty 仍为 `crowded_not_cleared`，最高证据为 `implementation_verified`，不释放任何 claim。




- **下一边界**：cycle=`active / S5_implementation_and_verification_completed_awaiting_explicit_S6D_authorization`。未创建 54 B0/P1/C1 训练或 18 A1 evaluation units，未建 Bundle、未上传、未远端执行、未 benchmark。只有新的明确 S6D 授权可以按冻结 S4 矩阵继续；不得以 S5 产物启动后验救援。









## D-175：RAIA S6D r4 回拉核验后为 no_signal，暂停在 S6M 直接例外决策边界（2026-08-29）









- **完整性与来源**：r4 full 完成 `54/54` 训练 tasks；本地对 54 个预测逐一重算 ACC/kappa/weighted-F1，并核对 B0/P1/C1 的 test index 与标签配对；18 个 A1 evaluation-only 产物的 hard checks、索引和预测也全部通过。下载归档 SHA-256=`5105d62d…49090660`，记录 922 个已验证 bundle files；上传 source manifest 的 105 个文件与 r4 staging bundle 一致。返回 artifact manifest 记录 54 个 checkpoint hashes，但 checkpoint bytes 未随结果树返回，因此未在本地重哈希。




- **冻结判读**：P1−B0 overall=`+0.5401 pp`（seed0=`+1.7747`，seed1=`-0.6944`；LOTO leave-target-5=`-0.1953`）；P1−C1 overall=`+0.4823 pp`（seed0=`+1.0995`，seed1=`-0.1350`；LOTO leave-target-5=`-0.2062`）。两者均不满足稳定门。P1−A1 overall=`0.0000 pp`、两个 seed 和全部 target/LOTO 均为 0，依冻结 S4 taxonomy 直接触发 `no_signal`。




- **结论边界**：这只关闭 RAIA-v0.1 在 BNCI2014001 frozen selection-used screen 上的完整方向特异性 signature；不证明共享参数无害，也不构成广义机制否定。没有性能、机制、novelty、benchmark、generalization 或 paper claim；没有独立外部 experiment-audit 或有利 claim verdict。




- **停止与后续**：cycle/family 现为 `paused / S6D_no_signal_boundary`。不得追加 seed、改 rank/init/gate/threshold/subject、重训 A1、追加 discovery、创建 child、加入 004、benchmark 或 confirmation。唯一后续是用户单独明确授权的 S6M direct-exception 决策。









## D-176：RAIA S6M=no_go，S9 关闭 exact core test（2026-08-29）









- **关闭决定**：用户明确关闭 RAIA。P1−A1=`0.0000 pp` 已决定性触发冻结 `no_signal`；P1−B0/P1−C1 虽有小的 overall 正方向，但 seed-1 与一项 LOTO 不稳定。没有合法的 unchanged-candidate S6R 路由。




- **状态**：exact cycle=`negative_boundary / completed_not_promoted / closed`；family=`exploratory / no_go`，child budget 保持 `0/1`。本次是对已完成 S6D 的成熟审查和关闭，不新增训练、数据、上传或外部执行。




- **非结论**：不证明 native shared MHA/FFN 无害、不证明所有 direction-indexed adapter 或 cross-branch interaction 无效；也不释放 performance、mechanism、novelty、benchmark、generalization 或 paper claim。




- **禁止后续**：不得以 rank/init/gate/seed/target/dataset/A1 重训进行 rescue，不得创建 child、同快照 re-entry、004/benchmark/confirmation。若出现实质不同的 baseline defect，只能另立 independent family，且不继承 RAIA 的 signal、budget、参数或 readiness。









## D-175：VCN-P1 S8 复核——本地 checkpoint 回拉不是硬门（2026-08-28）









- **对象**：`2026-08-23_mvcnet_view_bn_state_routing`（VCN-P1-v0.1）。用户明确授权 claim 复核，并指出「必须把 checkpoint payload 拉回本地」是流程设计缺陷。




- **完整性标准**：预测、真实标签、配对、source hash 与 ACC 独立重算仍是硬门。checkpoint 以 run completion 时远端 manifest 的路径 / 正字节数 / SHA-256 及与 prediction 一一对应为充分条件。七个 S8 r8 full 包 `1,287/1,287` 已核验。不要求本地打开 `.pth`。




- **Claim**：C-VCNP1-UTIL-001 与 C-VCNP1-ATTR-001 在冻结范围（BNCI2014001 LOSO seeds 2–4）均为 scoped `yes`（独立重算 `+1.929012 / +2.501286` pp，均 7/9）。N1 绝对 ACC `55.838%` 必须单列，不得写成 S6 的 chance/collapse。不释放 novelty、全协议泛化或无范围主模型。




- **未授权**：S9 写作交接、第二 child、新训练、与 IPB/MLEV/TAED 混写。T1 审查原文保留，只改门的解释。









## D-176：VCN-P1 S9 收口（2026-08-29）









- **对象**：`2026-08-23_mvcnet_view_bn_state_routing`（VCN-P1-v0.1）。用户明确授权仅做 S9 收口，不进入论文写作。




- **结论**：exact cycle=`supporting_evidence / completed_not_promoted`；S8 全范围已审计，远端 checkpoint completion attestation `1,287/1,287` PASS。保留 `C-VCNP1-UTIL-001`（`+1.929012 pp`）与 `C-VCNP1-ATTR-001`（`+2.501286 pp`）的限定结论。




- **family handoff**：`benchmark_candidate / paused(user_choice)`；child budget `1/1`，child=`not_applicable`。关闭 exact cycle 不关闭 family，也不等于 paper-ready。




- **边界**：不自动写作、不启动新实验或第二 child；N1 absolute `55.838%` 必须披露，不写成 chance/collapse；不释放 novelty、全协议/跨数据集泛化或无范围主模型。




- **流程含义**：后续 [REDACTED_MACHINE] full 回拉，不得把「全部权重必须落地本地」当作 integrity 或 claim 的硬门槛；缺预测、缺配对或缺 completion attestation 仍应 fail-closed。









## D-177：AI4S 三级管理与 Transaction v2 本地实施（2026-09-05）









- **决定**：采用共享 L1/L2、项目独立 L3；Program、State、Evidence Index 与冻结合同继续维护动态事实。MVCNet 围绕冻结 VCN-P1 scaffold 寻找机制互补模块；DSAINet 继承指定 Evidence Map/SAFSS handoff 的有效证据和关闭边界。




- **机器门**：新合同强制 Transaction 身份、授权节点闭集、NEXT_SCIENTIFIC_DECISION、技术条件白名单及真实 intake 后核验、分析和决策。技术 smoke 可同 Transaction 执行，科学 pilot 必须先完成决策才能冻结后续 full；预算不随 Transaction 重置。




- **生效**：MVCNet、DSAINet 均已独立激活 v2。用户授权关闭的 MVCNet VOGD operation 已移入历史并标为 CLOSED_BY_USER，未登记成功 intake、未作科学解释，也未声称远端进程已停止。旧 campaign 不提供新权限。




- **治理**：母项目与子项目入口已统一；进一步物理整理后，15 个退休入口已删除，原文仅存 archive。5,861 个历史研究、Bundle 与工程文件迁入分项目归档，保持字节不变；当前索引已修复，旧不可变引用通过 PATH_MAP 解析。此前 6 个可再生缓存已删除。最新验收见 `ai4s/_work/structure_20260905/REPORT.md`。




- **验证边界**：92 项离线回归通过，包括条件 smoke 到 verified intake 和幂等决策的 CPU 闭环。未上传、未启动 GPU、未创建 heartbeat；真实双环境运输和共卡验收留给后续明确授权的新 campaign。完整报告见 `ai4s/_work/migration_20260905/IMPLEMENTATION.md`。









## AI4S 按时长自主推进与 ccmu 专用卡策略（2026-09-06）









用户明确授权后续研究与上传实验的时长 campaign 内，NO_SIGNAL 仅关闭精确候选。缺少下一轮卡片或合同是 agent 应继续完成的准备工作，不是额外授权门或默认停止理由。控制器显式返回研究准备义务和剩余预算；agent 持续完成证据综合、独立问题选择、准入与新合同，直到达到有依据的停止条件。









ccmu GPU0 按用户说明作为个人专用卡，允许后台短暂占用。新合同冻结共享资源策略：初始最低空闲显存 12288 MiB（按技术画像调整）、温度 80°C、15 秒采样、最多等待 900 秒且计入预算；其他 PID 不再直接判失败。Lab10 规则独立，旧冻结合同不改写。实现与验收见 `ai4s/_work/autonomy_20260906/REPORT.md`。









## Lab10 普通训练默认同账号容量共卡（2026-09-07）









按用户授权，新 Lab10 合同默认采用 admission_mode=capacity、allow_same_owner=true，每卡初始并发上限2，按家族实际画像渐进放量。同账号瞬时利用率用于选卡排序；准入以完整进程峰值、实时空闲显存、未实体化预留、余量和温度为依据。其他账号/未知归属跳过；科学耗时测量仍隔离。旧冻结合同不追溯放宽，不修改已运行任务。实现与离线验证见 `ai4s/_work/lab10_capacity_20260907/REPORT.md`。














2026-09-07：按用户授权将 AI4S 新 campaign/Transaction 默认改为 exclude_resource_wait。纯资源排队不计入实验预算，服务器持续排队后自动执行；保留真实运行超时及不可变历史身份。实现与验证见 ai4s/_work/queue_time_20260907/REPORT.md。














2026-09-10：补齐原版 L2 用户监控交接；手动及自动运输均交付本次 Run 的本地只读看板命令。复用现有状态，不修改科学合同或远端冻结包。














2026-09-14：统一Lab10普通训练memory_only/逐任务预留默认，补齐verified_profile显存估计校准入口；34项回归通过。既有合同/远端实验不变。记录：ai4s/_work/capacity_defaults_20260914/REPORT.md。














2026-09-16：用户要求上传实验时默认自动衔接同一冻结Run的启动与probe；明确只上传时用 --upload-only。执行规则见 ai4s/prompts/TRANSACTION_RUNTIME.md。














## D-178：AI4S 承接科研流程与 proposed 退役（2026-09-17）









- **决定**：新科研编排归 AI4S；一个基模一个 Program，内部承载多个 research。Foundry 独立生成候选，仅交接 AI4S 指针，AI4S 仍可接受直接方向并自主累计学习。不迁入 proposed 的 family/cycle/child/S0–S9 管理。




- **最小新增**：正式候选按需冻结 EVALUATION_PLAN；Program 的 research/CLAIM_LEDGER.yaml 是逐 Claim 判断的唯一权威。State 管运行，Evidence Index 管证据；benchmark 完成不等于支持 Claim。评估、复用、暴露、审计与评议规则集中于 ai4s/prompts/EVALUATION_EVIDENCE.md。




- **退役**：全局 proposed-research 技能完整备份并逐文件 SHA-256 校验后移除；历史工作流、模板、cycle、结果保留，只标注历史用途。旧队列发现默认停用，已提交旧 Run 的精确恢复不变。




- **实现与激活分开**：代码和五个技能已更新，163 项离线回归通过。MVCNet 仍有活动 Run；DSAINet 旧 campaign 未到终止边界，因此两个 Program 的 v2.1 评估链均保持已验证草稿，旧活动链不变。未启动真实实验或为已有研究补造科学结论。




- **交付**：_work/ai4s-proposed-retirement-20260917/REPORT.md；激活只通过逐 Program 的安全边界检查，不要求同步停机。














## OTA-RESEARCH-PREPARATION-20260917：暂停 attention-scale，准备独立OTA（2026-09-17）









用户暂时暂停attention-scale后续研究，转向独立OTA状态占据—滞后关联双分支准备。已选初始函数匹配、source-audit决策/target描述；仅合成D0，未训练/上传/创建Run，原CMCR/CSUI证据不变。









研究入口：`ai4s/_work/ota-v0.1-research-preparation/RESEARCH_PLAN.md`；接入草案：`ai4s/_work/ota-v0.1-research-preparation/ADMISSION_DRAFT.md`。Grok设计审查已返回，五臂只作有界筛查，不能单独建立Q子空间特殊性或生理转移主张。新Program尚未激活；拟议90网络训练+162probe不等于执行授权。














## OTA-PROGRAM-ADMISSION-20260917









用户确认 OTA 接入独立 Program，并授权 Lab10 首轮 5 次单 epoch 技术拟合、90 次正式训练、162 次固定 probe；24 小时（扣除纯资源等待），一次接线/运输修复、零自动训练重试。source-audit 判定后停止，target 不进入本轮执行。活动身份与状态以 `ai4s/programs/ota/research/STATE.yaml` 为准；合同 `ota-r01-v0.1-r2.yaml`。保持 DSAINet attention-scale 暂停；OTA 未有科学结果或论文主张。









## D-179：DBConformer 与 SST-DPN 接入独立 Program（2026-09-19）









- **用户选择**：在候选分析后要求“为DBConformer＋SST-DPN  建立program”。DBConformer 承接已有时空分支研究积累；SST-DPN 补充多尺度表征与决策几何路线。




- **接入**：分别建立 PROGRAM、L3 v0.1、State、Evidence Index、交接记录和历史边界导航，唯一索引新增两条 L1/L2 v2.1 活动链；已有 Program 条目保持原样。




- **身份**：DBConformer 原生作者副本与 DSAINet 统一协议副本分别登记；SST-DPN corrected wrapper、参考源码及不同数据路径保留独立身份。文档/源码 SHA-256 核对不替代模型或数据产物复验。




- **历史**：引用已完成记录与精确关闭边界，不继承 cycle/family/stage 状态机、不重置选择暴露或历史限制。DRPG 支持性诊断及 WARN 保留，不自动选择后续原型实验。




- **权限**：初始 READY、预算/轮次为零，无 campaign、Run、operation 或实验执行授权；首个 research 待后续任务选择。评估计划和 Claim Ledger 按需建立。




- **验证**：两条链、guard、证据来源与无执行授权边界单独检查。共享回归有 163/164 通过，1 项为既有 MVCNet SSH 别名断言差异；不将总套件记为全通过。详见 `ai4s/_work/baseline_program_admission_20260919/REPORT.md`。









### 2026-09-21 SMANet 复现修复与预算补充（D-043 边界内的机制诊断）









用户明确授权继续修复、补充预算并自动实验。保留 CTRL 与既有固定 2-Hz 初始化 baseline 身份；不恢复 paper_uniform_cutoffs 扫描或叠加 CenterLoss 补偿。新 SINC_INTERIOR 将初始带宽 2 Hz 与训练下界 0.5 Hz 分开，用既有 sigmoid 映射，初始有效截止频率与滤波器对齐 CTRL；这是一个预先固定的机制候选，不是下界/初始化超参搜索，也不代表原文已明确此约束。CENTER_PRE 单独作为第三臂对照，不与新 Sinc 组合。









新实验为 BNCI2014001 LOSO、3 臂 × subjects 0–8 × seeds 0–2 × 100 epochs，另有每臂 2-epoch smoke；81 个科学任务，5 小时实际执行预算，排队不计时，无自动训练重试。逐 epoch 源域诊断不参与目标选模。所有结果仍标记 diagnostic，原 20-epoch pilot 已看过的 S1/S2 不称为未接触确认。无 AI4S Program；详细合同见 experiments/records/smanet/2026-09-21_smanet100_repair_budget/EXPERIMENT_PLAN.md。









2026-09-21 预算恢复补充：r1 的科学节点满4小时停止，59/81已完成。用户明确授权“增加预算，继续完成剩余实验”。冻结独立 r3（r2准备版未启动，补充归档输出路径保护后替换），仅运行原矩阵缺失22项，并重新做3个技术smoke；科学源码/config字节不变，3个中断项从原seed重训，已完成59项不重训。追加科学节点6小时、技术节点0.5小时、总6.5小时，排队排除，单任务2小时、无自动重试。旧FAILED Run不改写；已验证旧产物按REUSE_INDEX归档至新输出inherited，完整intake后验收59+22联合闭集，不伪装旧Run完整。记录：experiments/records/smanet/2026-09-21_smanet100_budget_recovery/RECOVERY_PLAN.md。









2026-09-21 最后两项恢复：用户授权恢复最后两项实验。r3因CUDA OOM停止，20项完成，加r1共79项。新r4只运行SINC_INTERIOR seed2 subject7/8（原100epoch配置），新做3个技术smoke；禁止与现有计算进程共卡、每卡1任务，其余科学配置不变。科学4小时、smoke0.5小时，排队排除。79项SHA归档保留旧身份，完整后联合81项验收；记录 experiments/records/smanet/2026-09-21_smanet100_final2_recovery/RECOVERY_PLAN.md。




2026-09-21 用户要求不要按禁止共卡规则等待：确认r4尚未训练并停止其精确进程树；冻结r5允许同账号共卡，保留每卡1个本Run任务、4096MiB任务预估、1024MiB公共余量、80度和原4.5小时预算。最后两项科学范围不变，79项不重训。记录 experiments/records/smanet/2026-09-21_smanet100_final2_shared/。









2026-09-22 SMANet诊断联合81项已验收（r1 59+r3 20+r5 2，旧FAILED状态保留）。CTRL55.6006%、CENTER_PRE56.4815%（+0.8809pp，7/9被试正）、SINC_INTERIOR55.4655%（-0.1350pp）；真实标签逐预测重算通过。新Sinc有效带宽可移动但未获平均提分；CENTER_PRE仅小幅描述性信号，非稳健/原文精确复现主张。77/81选中轮次>=90，收敛未确认；外审WARN/partial，不自动追加实验。完整报告 experiments/records/smanet/2026-09-21_smanet100_final2_shared/RESULT_REPORT.md。









2026-09-22 原文构建复现后续分析：新增事件窗口问题。paper_holdout的5184条输入逐元素等于MAT `trial-1`后1000点，DSAINet共享资产全部起点元数据及108条滤波后探针也使用offset0；官方Graz时序和MOABB MAT映射支持cue在trial后2秒，原文cue后4秒应使用`trial-1+500`后1000点。此前manifest验收不覆盖事件语义，旧81项仍为原冻结输入下的配对诊断，不升级为cue对齐的原文复现。下一步建议独立版本修正paper输入窗口、显式冻结Sinc映射/初始化与未知项、完善两阶段记录，再验证原文会话日程；不覆盖共享资产，不组合CENTER_PRE/SINC_INTERIOR，不重开D-043性能搜索。此次仅分析与只读数组审计，未训练、未建立Program；原始GDF事件对齐尚未执行。详见 `experiments/records/smanet/2026-09-22_reconstruction_followup/RECONSTRUCTION_PLAN.md`。









2026-09-22 用户授权继续自主修复并启动 SMANet 原文复现：独立 cue-v2 资产全量5184条验证，Sinc改为原文raw绝对值映射，训练补齐source-only与两阶段checkpoint/停止阈值记录。固定9人×3seed会话T→E、1500/200+600日程，先短smoke和完整日程source-only技术检查再自动full，预算28.5小时活动时间，同账号按显存共卡。不建立Program，不覆盖旧共享数据。原文iterations按epoch、stage2以stage1末次joint loss为阈值等均为明确实现解释；Grok外审WARN已整合，不声称作者精确实现或性能复现。运行身份与状态见 experiments/records/smanet/2026-09-22_paper_cue_v2/STATUS.md。









2026-09-22 SMANet cue-v2联合27项已全部回拉及哈希/intake验证（r3封存13+r4恢复14，旧FAILED保留）。真实标签与预测指标重算通过：ACC69.6116%、macro-F1 0.687681、Kappa0.594822；原文Table II为80.21%，差距−10.5984个百分点，仅作描述性比较。stage1全部patience停止、无1500上限截断；stage2为1–18轮，其中8/27一轮即停。不能宣称原文性能/作者实现已复现，不能与旧LOSO作修复因果比较。Grok外审两次达轮数上限、无正式报告，外审门仍未闭合；本地分析已完成，未追加训练。详见 experiments/records/smanet/2026-09-22_paper_cue_v2_recovery/RESULT_REPORT.md。









2026-09-22 用户授权SMANet实验后继续修复：本轮冻结旧cue-v2及27项证据；按原文Eq2–4增加显式unit-bandpass Sinc幅值候选并区分checkpoint语义，同时加固native数据入口。现有stage2阈值保留，其他未确认项不盲改。仅做回归和source-only技术smoke，不新增目标性能结论。计划 experiments/records/smanet/2026-09-22_paper_equation_repair/PLAN.md。









2026-09-22 SMANet原文公式幅值候选及入口修复完成：新增unit_bandpass（Hz/Fs系数、无逐滤波器peak归一化），旧peak默认与真实旧checkpoint源域logits逐元素一致；整模跨幅值加载预检、X/y/meta哈希及窗口单位验收补齐。27项源域后验分析中0项在恢复点已低于stage2阈值，固定probe center/CE梯度比约0.13，因此未盲改stage2或center。单因素新配置及source-only CPU 2+1 smoke通过，未新增目标指标或远端full。Grok代码审查无P0/P1、两项P2经本地回归修复；此前实验外审仍incomplete。报告 experiments/records/smanet/2026-09-22_paper_equation_repair/REPORT.md。














2026-09-22 用户要求 SMANet 新旧幅值“进行比较”：冻结 cue-v2 peak 对照与 unit_bandpass 候选的单因素9被试×3seed配对实验。旧27项经源码与隔离训练一致性检验后复用，候选27项依次通过source-only短smoke和完整日程技术pilot后在Lab10自动执行；28.5小时活动预算、允许同账号按显存共卡、5120MiB任务+2048MiB余量。分析规则在启动前冻结，完成verified intake后按9名被试的三seed均值比较ACC；仍为探索性复现证据，无新性能结论、不建Program。实际状态见 experiments/records/smanet/2026-09-22_sinc_gain_comparison/STATUS.md。














2026-09-22 23:35 SMANet幅值配对比较已实际启动Lab10 Run `2026-09-22_smanet_sinc_unit_gain_lab10_r1-full`，launcher PID1899595与合同/源码身份均核验；smoke等待显存，full尚未开始。同账号共卡已允许，队列将按冻结技术门自动推进。无新性能结果。精确状态见 experiments/records/smanet/2026-09-22_sinc_gain_comparison/STATUS.md。









### 2026-09-23 PAPER 文档刷新（证据与写作摘要整理）









按用户确认将 PAPER.md 重组为八部分，依据本地 Program State/Evidence Index、中央结果登记及已有实验报告更新。补充 BNCI2014001 事件窗口语义、SMANet 联合结果和各 Program 的最新已登记判断；历史负边界与限定范围支持结论同时保留。论文工作问题用于收敛叙事，尚未选定新主方法或冻结跨 Program 假设。本次不改变数据、UEP、活动链、实验合同、授权或 Claim 状态。旧版逐字节保存，来源快照与核验见 [_work/paper_refresh_20260923/CHANGELOG.md](_work/paper_refresh_20260923/CHANGELOG.md)。














2026-09-23：新任务默认温度90°C；Transaction节点增加cpu_analysis/gpu_light资源分类，分析不再默认继承full GPU门槛。历史Run不修改。









### 2026-09-23 PhysioNet-MI 两模型基线扩展









用户授权完成前置准备、上传数据资产并自动排队部署DBConformer与DSAINet。沿用统一基线的共同seeds0–4、train-only统计、validation-best、保存预测和被试级汇总原则；PhysioNet采用官方被试级十折和batch128，登记独立 `mieeg-physionet-subject10fold-v1` / `tp-dsainet100-physionet-v1`。矩阵共100个full任务，先每模型一次完整训练路径技术smoke。共享运行时以独立baseline Transaction部署Lab10，不覆盖活动Program研究及历史BNCI协议。详见 `experiments/records/physionet_mi/2026-09-23_baselines/EXPERIMENT_PLAN.md`；当前无性能结论。














2026-09-23 SMANet Paper R1本地实施完成：新增R1=pre-dropout center及独立R2=none pre-log，保留peak及旧训练日程；补齐profile/checkpoint身份、27组固定划分、无副作用诊断和阶段状态。七个回归脚本、三臂真实数据source-only 2+1 smoke通过；最终R0相对冻结旧版的三seed合成数据及A01/seed0真实数据短程对照一致。尚无R1/R2目标性能结论，54项新full未启动；短程一致性不单独授予旧27项正式复用。验收见 experiments/records/smanet/2026-09-23_paper_r1_local/REPORT.md。此前幅值比较Grok外审仍incomplete。









2026-09-23：依据用户“上传并启动实验”授权，SMANet R1/R2以独立冻结Bundle各27项在Lab10启动；source-only smoke→完整日程pilot→full按技术门自动推进，容量等待排除活动预算。R0历史27项只读。启动回执仅证明运行接收，性能判断待完整回拉及核验；详见experiments/records/smanet/2026-09-23_paper_r1_local/STATUS.md。









2026-09-24：SMANet R1/R2固定复现矩阵完成并经SHA/manifest/intake核验；R1中心取点提前未提升本次cue-v2配对ACC（−0.745885pp），R2无平方字面路径明显降低ACC（−33.333333pp）。维持R0 peak/square/post_dropout为当前已测较高的工作参照，不据测试成绩判定作者实现或继续搜参数。已暴露测试集和旧R0复用使判断限定为探索性；详见experiments/records/smanet/2026-09-23_paper_r1_local/RESULT_REPORT.md。









2026-09-24 DBConformer TMR-R1闭环：实验有效，结论为INSUFFICIENT_SOURCE_TEMPORAL_MOMENT_READOUT_SUPPORT。P1−B0 +0.3831 pp，P1−G0 +0.0060 pp，P1−C0 +0.1736 pp，P1的NLL略升；本次324参数、20epoch时间均值/方差读出未证明超出同容量一阶读出的收益。保留该精确负实例，不扩展成所有时间统计方法无效。见 [报告](ai4s/programs/dbconformer/research/tmr_r1/REPORT.md)。









2026-09-24 DBConformer CBR-R1：INSUFFICIENT_SOURCE_CROSS_BRANCH_READOUT_SUPPORT；P1−B0 -0.1197 pp、P1−G0 -0.4071 pp、P1−C0 +0.1137 pp。按预写门槛闭环，保留此前精确关闭边界；无自动追加变体或下一轮。见 [报告](ai4s/programs/dbconformer/research/cbr_r1/REPORT.md)。









2026-09-25 DBConformer SNR-R1：INSUFFICIENT_SOURCE_NUISANCE_READOUT_SUPPORT；P1−B0 +0.3831 pp、P1−G0 +0.0180 pp、P1−C0 +0.0419 pp。按预写门槛闭环，保留此前精确关闭边界；无自动追加变体或下一轮。见 [报告](ai4s/programs/dbconformer/research/snr_r1/REPORT.md)。









## D-181：PhysioNet-MI 双模型纳入本地基线（2026-09-25）









- 用户确认“归档并纳入本地基线”。采用非破坏性原位归档，新增独立协议结果登记与双模型表；保留r1/r3/r4/r5合同、原始产物、失败和审查trace，不搬移或删除。




- 纳入范围为DSAINet/DBConformer各5seed×10被试折，共100项已验收full；训练在Lab10，结果本地回流，不称本机重训。按每seed十折均值再求五seed均值与样本SD。




- 独立协议`mieeg-physionet-subject10fold-v1` / `tp-dsainet100-physionet-v1`，相对论文paper-aligned。继承外审WARN、C1 yes/C2 partial/C3 no，不因归档提升为严格复现、统计显著或等效；不纳入BNCI UEP主表、不改变AI4S Program状态或授予新训练。




- 权威入口：[归档](results/archives/mieeg-physionet-subject10fold-v1/README.md)、[全量分析](experiments/records/physionet_mi/2026-09-25_full_analysis/RESULT_ANALYSIS.md)。后续直接引用已封存基线，不自动重复实验。









## D-180：AI4S v3.0 研究闭环与 Program 迁移（2026-09-25）









- **决定**：新研究统一使用 Prompt Index 登记的 L1/L2/L3 v3.0；以论文问题、可执行干预和最小配对对照组织研究。诊断必须说明设计取舍，筛查和负结果必须登记后续处置，下一轮必须说明新增证据如何改变设计。




- **边界**：MVCNet、DSAINet、DBConformer、SST-DPN、OTA 的既有 campaign、Run、operation 和冻结续接沿原绑定链收尾；新默认链不回写旧合同，不自动恢复暂停研究，不追加实验预算。跨 Program 通过 PAPER 问题地图共享证据和设计约束，不合并不可比指标或执行授权。




- **实施状态**：新版提示词、控制器兼容、活动文档和五个 Program 的新默认链均已接入；旧链绑定、离线回归、集中 Grok 外审及逐 Program 入口检查已完成。结果和外审覆盖限制见 [V3 实施验收](ai4s/_work/workflow_review_20260924/V3_IMPLEMENTATION_REPORT.md)。









2026-09-25 DBConformer v3.0 BPM-R1设计：用户新设6小时仅一轮并授权自动推送；从冻结读出转向参数无增量的三相位时间池化与原B0端到端成对训练。独立资产使用cue[0,4)=trial[2,6)，旧窗口不覆盖且不复用旧checkpoint作数值对照。36次100epoch科学拟合与2次1epoch技术检查；当前仍在本地验收，尚未推送，无效能结果。方案与边界见 [research brief](ai4s/programs/dbconformer/research/bpm_r1/research_brief.md)。









2026-09-25 BPM-R1 已冻结并启动：Run 2026-09-25_dbconformer_bpm_r1_lab10_r1-full-w1，合同SHA b44e6306269baef4fe31c3a2cb89f9aa0d7914151db13ee76b65462eff536235。首次scp运输超时后同包续传，68文件远端SHA均匹配；真实smoke正在运行。尚无科学效能结论。









2026-09-25 BPM-R1 完整闭环：38/38任务（2 smoke + 36联合训练）完成，394文件回拉SHA/manifest校验、verified intake及36 checkpoint原环境CPU重放通过。B0 ACC 57.0505%，P1 55.4880%，差值−1.5625pp；双seed均负、3/9受试者改善，冻结门全部未过。决策 INSUFFICIENT_PAIRED_TRAINING_SUPPORT，关闭精确固定三相位平均池化设计；不外推为所有边界感知或联合训练方向失败。单轮 COMPLETE_MAX_ROUNDS，无论文claim、无自动下一轮。见 ai4s/programs/dbconformer/research/bpm_r1/REPORT.md。














2026-09-25 MVCNet channel-bilinear：用户授权自动下一轮研究，按Program默认10小时、1阶段登记campaign mvcnet-channel-bilinear-20260925。综合source-risk、WCR、QEP、TAPR/TCRD、OCST和dual-atom的适用边界，选择原tconv BN输出的跨latent乘积路径，与S0及等参数C0从头配对训练。没有继承历史阳性或宣布新颖性；旧对象不救援，当前尚无新效能结果。见[研究简报](ai4s/programs/mvcnet/research/channel_bilinear/RESEARCH_BRIEF.md)。









2026-09-25 HDS-R1 准备：用户新设6小时仅一轮并沿用自动推送授权，campaign=dbconformer-v3-20260925c。BPM固定相位池化负对象保持关闭；新候选仅将四个MultiHeadAttention分母由sqrt(40)改为sqrt(head_dim=4)，保持原pool/fusion/参数量，与原B0配对从头训练。非算法创新或已证明错误修复。见 ai4s/programs/dbconformer/research/hds_r1/research_brief.md。









2026-09-25 HDS-R1 已冻结并启动：Run 2026-09-25_dbconformer_hds_r1_lab10_r1-full-w1，Lab10；71个Bundle文件SHA通过，2/2真实数据smoke PASS，36项screen训练已开始。冻结合同4a44bd0f4d46eb3ae6d963ab7f8f085eefeebe1612ad1ad7ec5e6245e093a2e6；当前无效能结论，完整闭合后按原合同回拉校验分析。详见ai4s/programs/dbconformer/research/hds_r1/STATUS.json。









2026-09-25 HDS-R1 检查：screen失败，27项退出成功、P1_s0_seed1在物理GPU9发生CUDA OOM、其余8项P1 seed1未启动即受阻。失败元数据SHA回拉验证完成，控制器登记INVALID并暂停，未分析部分效能；这不是科学证伪。原6小时预算按纯排队抵扣后余额0，未自动补跑。见ai4s/programs/dbconformer/research/hds_r1/failure_intake_20260925/REPORT.md。














2026-09-25 MVCNet channel-bilinear结果收口：同Run完整回拉、manifest校验及verified intake后，P0−S0 −2.980324pp，P0−C0 +0.964506pp但仅4/9被试正向；固定实例NO_SIGNAL，VCN-P1保留，不提升C0或救援rank/分组/激活。控制器COMPLETE_MAX_ROUNDS。证据AI4S-MVCNET-mvcnet-channel-bilinear-screen-lab10-r1；见[报告](ai4s/programs/mvcnet/research/channel_bilinear/REPORT.md)。














2026-09-25 MVCNet ordered-pool：用户要求继续下一轮。综合channel-bilinear/QEP/dual-atom等负边界，不再追加feature旁路，改为固定时间降采样算子的受控训练筛查。P0三角249tap，N0同权重多重集对称错序，保留S0、原目标、BN路由和raw推理。抗混叠有既有文献，不宣称新颖性或缺陷已证实。单阶段10小时，不自动追加。见[研究简报](ai4s/programs/mvcnet/research/ordered_pool/RESEARCH_BRIEF.md)。









2026-09-25 HDS-R1 repair1：用户授权修复并新设6小时仅修复。资源改为fixed_count每卡1任务、拒绝外部compute、6144MiB任务承诺+2048MiB余量，并修复同族计数跨GPU错误；科学协议不变，全新38任务，旧INVALID产物不复用。合同fee412c22444022ce54277013d8d407b7735f351ed8e2a4461bdcd83b2216aec；74文件远端SHA通过，新Run已启动领取且等待资源。见ai4s/programs/dbconformer/research/hds_r1_repair1/REPORT.md。









HDS-R1 repair1终态核验：screen在9900秒冻结执行时限后超时；smoke 2/2 PASS，科学任务29项完成，最后快照3运行+4待执行，现已核验无同Run活跃进程。失败元数据SHA回拉通过并登记INVALID；没有科学分析或新OOM证据，未自动补跑。见ai4s/programs/dbconformer/research/hds_r1_repair1/failure_intake_20260925/REPORT.md。









2026-09-25 HDS-R1 repair2工程恢复：冻结新不可变合同，仅补7缺失任务与2smoke；29项旧原件哈希绑定并保留旧Run身份，不将旧INVALID改为有效。用户新设6小时仅修复；联合36项完整intake与CPU重放后才允许科学判断。外审WARN及本地补验处置见 ai4s/programs/dbconformer/research/hds_r1_repair2/REVIEW_DISPOSITION.md。已上传领取，当前资源排队。









2026-09-26 HDS资源策略修订：依用户明确授权，普通capacity训练允许外部进程共卡、额外预留0MiB；保留6144MiB任务需求、温度及本Run单卡1任务约束。repair2在0训练尝试时主动停止，旧合同不改，新repair3已领取；不是训练失败或科学证伪。范围及预算不扩张。详见 ai4s/programs/dbconformer/research/hds_r1_repair3/REPORT.md。














2026-09-26 MVCNet ordered-pool 收口：54训练+54检查回拉校验与intake完成，冻结决策NO_SIGNAL。P0−S0为−1.012731 pp，P0−N0为+1.321373 pp；关闭固定有序池化实例，原VCN-P1锚点范围不变，不追加实验或论文主张。详见[报告](ai4s/programs/mvcnet/research/ordered_pool/REPORT.md)。









2026-09-26 SVE-R1 准备：HDS-R1 repair3 已完整闭环，配对提升 -1.118827pp，注意力缩放对象关闭。用户新设6小时仅一轮并授权自动推送；新候选只把空间分支每电极早期均值汇聚替换为无参数log方差，恢复原attention与temporal pool。9subjects×seed0×B0/P1=18科学fits+2smoke，全新成对重训；单seed探索不支持跨seed稳定性或正式主张。共卡允许、额外显存预留0，保留任务6144MiB和90度门。设计见 ai4s/programs/dbconformer/research/sve_r1/research_brief.md。














2026-09-26 MVCNet temporal-tied-head：ordered-pool已按NO_SIGNAL收口，用户要求继续下一轮。保留原Stem/AvgPool/VCN-P1及512维辅助目标接口，仅约束CE共享分类头时间位置权重；P0/N0同260参数，S0原2052参数。此为已有参数共享思想的筛查，不证明原头已过拟合，不宣称原创。fresh seed51/52，七源开发检查，单阶段10小时不自动追加。见[研究简报](ai4s/programs/mvcnet/research/temporal_tied_head/RESEARCH_BRIEF.md)。









2026-09-26 SVE-R1 启动状态：合同8be80fd9e607ea7b3a2c1d965df6ad437dcf799d20e4e4d0ddf3e0ed8d479c50、18科学fits+2smoke已冻结并登记；4模型测试、37共享测试及B0/P1合成canonical训练/CPU重放验收通过。ccmu-lab跳板Tailscale离线且SSH超时，Lab10直连关闭；尚未上传、未启动，无科学结果。保持同Run待网络恢复，不增加预算、不重投。状态见 ai4s/programs/dbconformer/research/sve_r1/REPORT.md。









2026-09-26 SVE-R1 repair1：用户要求修复并补跑。原18项中16退出成功、2项共有Conv1d cuDNN失败，INVALID保留。本次16项112工件SHA回拉核验，仅补B0_s5_seed0/P1_s6_seed0及2smoke；模型和训练代码哈希不变。排除GPU1/2是预防性调度，根因未证实；共卡/reserve0不变。10恢复流程+44共享测试通过，199文件SHA上传完成，远端已运行、smoke等待资源。沿用余额且Tx上限2h，完整18项闭环前无科学结论。见 ai4s/programs/dbconformer/research/sve_r1_repair1/REPORT.md。









2026-09-26 SVE-R1 repair1完整闭环：18科学fits（16原身份恢复+2补跑）和2smoke封存回拉、SHA/intake、原Torch1.13.1 CPU全checkpoint重放通过。B0 ACC57.0602%，P1 55.9221%，delta -1.1381pp，3/9正、最差-7.2917pp、LOO最小-1.6493pp；全部冻结支持门未过。INSUFFICIENT_PAIRED_TRAINING_SUPPORT已登记，精确早期空间log方差替换对象关闭；NLL改善不替代预定ACC门。单seed/历史暴露，无论文主张或下一轮执行授权。State COMPLETE_MAX_ROUNDS，余额约2.86h。报告 ai4s/programs/dbconformer/research/sve_r1_repair1/REPORT.md。














2026-09-26 BSD-R1 准备：用户新设6小时仅一轮，沿用自动上传启动授权。SVE/HDS/BPM 精确负边界保留，恢复全部原池化与注意力缩放；本轮仅在训练期 classifier 的双分支80维输入随机整支遮蔽（时间0.1、空间0.1、双支保留0.8，/0.9期望缩放），eval恒等，0新参数。B0/P1各9被试seed0重新训练100epoch，18科学fits+2smoke。只判断净效用，不将收益归因于空间机制；正向后另需一般dropout对照及跨seed确认。详见 ai4s/programs/dbconformer/research/bsd_r1/research_brief.md；当前无效能结果。














2026-09-26 BSD-R1 已冻结并部署：合同4444e059b4ef93efcca28ac1f237e57442f0d28b1ea077df6681e1c684cef115，Run 2026-09-26_dbconformer_bsd_r1_lab10_r1-full-w1。62文件远端SHA通过；5模型+25共享+5路由/门检查及B0/P1合成训练重放通过。远端调度已启动，smoke 2项等待、0运行/失败；10卡当前仅115–237MiB空闲，低于6144MiB任务承诺，共卡允许/reserve0已生效。满足资源后自动执行，暂无科学结果。新6小时仅本轮，详见 ai4s/programs/dbconformer/research/bsd_r1/REPORT.md。














2026-09-27 BSD-R1 检查：同Run终态FAILED，smoke2/2 PASS，science10退出成功、P1_s0 cuDNN算法失败、P1_s2 CUDA OOM、6项未启动受阻。4份失败元数据/日志回拉SHA通过，控制器登记INVALID，仅工程失败，无部分科学结论。补跑须新不可变合同/Run、预算核对及成功产物独立验证。详见 ai4s/programs/dbconformer/research/bsd_r1/failure_intake_20260927/REPORT.md。














2026-09-27 MVCNet temporal-tied-head 收口：112/112闭合，verified intake及31,104行预测复算通过，NO_SIGNAL已登记。S0/P0/N0 ACC为58.198302/38.638117/54.523534%，P0−S0 −19.560185 pp、P0−N0 −15.885417 pp，两seed及9名检查被试均退化。保留原生VCN-P1，关闭完整时间权重绑定和固定乱组实例，不调分组/部分绑定/置乱/缩放/gate救援。七源开发筛查，无B0，不新增anchor归因或论文主张；未例行Grok外审。权威状态与证据已写Program State/Evidence Index，见[报告](ai4s/programs/mvcnet/research/temporal_tied_head/REPORT.md)。














2026-09-27 MVCNet spatial-locality准备：时间共享头NO_SIGNAL后保留8时间桶和原512分类头，仅检验原sconv的局部空间支持；P0/N0同576空间参数，控制逐电极覆盖，S0原1408。不新增支路或改变目标，非原创性主张。种子53/54，七源开发screen。见[研究简报](ai4s/programs/mvcnet/research/spatial_locality/RESEARCH_BRIEF.md)。














2026-09-27 BSD-R1 repair1：用户授权修复并新设6小时仅修复。原10任务70工件SHA核验后恢复，仅补P1 subject0及2–8共8项，另2smoke；原Run INVALID保留。模型/训练脚本原字节不变，暂避GPU7，P1继承原OOM上调7680MiB，B0 smoke6144MiB，共卡/reserve0/90度保持。仅一次OOM工程重试且保留全部尝试；完整18项闭环前无科学判断。13定向+36共享测试通过，151文件SHA上传完成，新Run已核验真实smoke运行。合同b60f49dff90759b63d9f860ccebed3febe489206e3b163d88cd0c8c5bbbf3497。详见 ai4s/programs/dbconformer/research/bsd_r1_repair1/REPORT.md。














2026-09-27 SST-DPN JMR-r01-v0.1 研究准备：JTN repair2的18项训练已完成并verified intake，Joint均值提升但S02损害及跨seed门失败，NO_SIGNAL保持。用户要求针对均值线索继续研究，下一问是共同归一化下的均值保留；拟比较Native、Joint、RMS、同RMS分母中心化对照，共24科学+4技术任务，原被试/seed/训练配置不变。新代码、合同草案和本地检查正在准备，新campaign与GPU运行未授权/未启动；仅探索机制，不新增论文Claim。权威材料见 ai4s/programs/sstdpn/research/jmr-r01-v0.1/research_brief.md，旧失败和负边界保留。









2026-09-27 SST-DPN JMR repair1：用户“修复并补跑”已执行。旧JMR首步前技术失败INVALID保留；新合同保留RMS-vs-centered RMS主分离阈值，将二阶centered RMS-vs-Joint差改为必记录诊断，并在异常前持久化统计/身份。模型字节、24科学fit矩阵与科学判定门不变；26项CPU检查通过，Grok增量设计审查WARN已处置。新Run 2026-09-27_sstdpn_jmr_r01_v0_1_repair1-full-w1 上传启动确认，11:41:47北京时间技术4项等待共享资源，科学未启动，无新Claim。详见 ai4s/programs/sstdpn/research/jmr-r01-v0.1-repair1/STATUS_REPORT.md，State/Evidence Index仍为权威。旧失败成本与38 task-GPU小时/18h Transaction/24h campaign预算保留，仅授权本次1个修复Run。









2026-09-27 SST-DPN JMR repair1收口：4/4技术、24/24科学训练完成，0失败；425文件回拉、manifest/SHA与正式intake通过，13824行预测及checkpoint/配对身份核验，独立复算一致。native/joint/rms/centered_rms ACC为57.5231/59.7222/59.5486/59.5197%；RMS相对三个控制+2.0255/-0.1736/+0.0289pp，S02对native-4.0799pp，稳健被试0/3。冻结NO_SCREEN_SIGNAL→Program NO_SIGNAL/COMPLETE_MAX_ROUNDS，关闭精确RMS均值保留候选，不自动调epsilon/筛被试seed/混合救援。开发筛查无独立确认、无新论文Claim。报告 ai4s/programs/sstdpn/research/jmr-r01-v0.1-repair1/ANALYSIS_REPORT.md；State/Evidence Index与决策已登记。














2026-09-27 MVCNet spatial-locality收口：54训练+54检查+4技术项全部完成并verified intake；P0−S0 −2.517361 pp（9/9被试均值负向），P0−N0 −0.665509 pp，两个seed均未通过主门，正式NO_SIGNAL/COMPLETE_MAX_ROUNDS。保留原生全电极空间卷积和VCN-P1；关闭当前固定9近邻图，不调k/模板/中心/掩码seed/缩放或global支路救援，不晋升N0。 权威记录见 ai4s/programs/mvcnet/research/STATE.yaml、EVIDENCE_INDEX.yaml；报告 [REPORT.md](ai4s/programs/mvcnet/research/spatial_locality/REPORT.md)。














## 2026-09-27 BSD-R1 repair1 完成闭环









8项缺失训练与2项smoke完成；连同10项SHA绑定恢复输入，18项完整科学矩阵已回拉、manifest/SHA验证、verified intake及原环境checkpoint重放。原Run保留INVALID工程记录。原模型ACC 57.0602%，分支遮蔽56.8094%，配对差值-0.25077个百分点，4/9被试提高，LOO最小-0.80295个百分点，冻结四项门均未通过。决策INSUFFICIENT_PAIRED_TRAINING_SUPPORT；关闭本固定0.1/0.1/0.8分类器输入分支遮蔽配置，保留原模型，不推广为所有分支遮蔽无效。单seed探索性结果，不发布论文claim，不自动下一轮。









权威记录：[BSD修复报告](ai4s/programs/dbconformer/research/bsd_r1_repair1/REPORT.md)、[后续处置](ai4s/programs/dbconformer/research/bsd_r1_repair1/FOLLOW_UP.json)。














2026-09-27 MVCNet cosine-readout准备：spatial-locality NO_SIGNAL后保留全电极空间层和原512维时间位置特征；新问题是联合训练分类头是否需要单trial径向幅度。S0原生、C0权重归一化且保留径向、P0权重+特征归一化，P0/C0同log_s可学尺度和2053原始参数项。已登记10h/1阶段新campaign，54训练+54检查，正在实现验收，尚未上传；不继承旧候选正证据或论文主张。详见 ai4s/programs/mvcnet/research/cosine_readout/RESEARCH_BRIEF.md。














## 2026-09-27 SDT-R1 下一轮联合训练筛查









BSD固定融合遮蔽已完整关闭，新增SDT-R1：空间embedding之后、原位置编码之前，按每trial的22个电极减均值，直接测试相对完整原模型的联合训练净效用。保留原时间池化、空间时间均值及sqrt(40)缩放；不把共同分量有害当作已有事实，也不以历史raw CAR诊断作为收益证据。9被试×seed0×B0/P1，18项100epoch训练与2项技术smoke；新6小时仅一轮，不发布claim。









设计与边界：[research_brief](ai4s/programs/dbconformer/research/sdt_r1/research_brief.md)。合同：`ai4s/programs/dbconformer/research/dbconformer-sdt-r1.yaml`，SHA `0d759dd45f74091604c713cf9eaa8150836b9f03ae35050efe471a5615a8385c`。Run `2026-09-27_dbconformer_sdt_r1_lab10_r1-full-w1`，运行状态以Program State为准。














### 2026-09-27 MVCNet cosine-readout v0.1 已冻结并启动









保留 spatial-locality 的 NO_SIGNAL，采用三臂训练期分类径向依赖筛查（已知归一化分类器适配，不主张原创）。r1只在本地准备阶段因依赖/序列化未通过，未上传或登记Run；保留原记录，r2科学规格不变。54训练＋54独立检查，seed55/56，10小时实际预算、1科学阶段；三臂CPU和GPU smoke、配对初值、checkpoint重载通过。2026-09-27 17:00同Run核对 r2 为 diagnostic/RUNNING，暂无科学结论。权威身份与动态状态见 ai4s/programs/mvcnet/research/STATE.yaml；研究与停止边界见 research/cosine_readout/RESEARCH_BRIEF.md、STATUS.md。














## 2026-09-27 SDT-R1 完整闭环









18项科学训练+2项smoke完整完成，已回拉、manifest/SHA验证、verified intake与原环境checkpoint重放。原模型ACC57.0602%，SDT56.9830%，差值-0.07716pp；4/9被试提高，最差-6.59722pp，LOO最小-1.01997pp，冻结四项门均未通过。决策INSUFFICIENT_PAIRED_TRAINING_SUPPORT；关闭空间embedding后、位置编码前跨22电极减均值的固定配置，恢复B0；不事后挑选被试或参数救援，不推断全部相对空间表示无效。单seed探索无论文claim，单轮关闭，无自动后继。









权威记录：[报告](ai4s/programs/dbconformer/research/sdt_r1/REPORT.md)、[处置](ai4s/programs/dbconformer/research/sdt_r1/FOLLOW_UP.json)。














### 2026-09-27 MVCNet cosine-readout v0.1：NO_SIGNAL









证据AI4S-MVCNET-mvcnet-cosine-readout-screen-lab10-r2：54训练＋54检查全部完成，1194文件manifest核验与verified intake后，冻结分析及独立预测复算一致。P0-S0 +0.250772 pp（seed55 -0.231481、seed56 +0.733025；CE增加0.037752），P0-C0 -0.048225 pp，未通过冻结门。关闭当前特征/权重归一化＋scale初值10＋保留bias实例，不以scale/margin/epsilon/部分归一化等救援，不晋升C0。保留VCN-P1原线性分类路径；不推论所有归一化分类器无效。本campaign COMPLETE_MAX_ROUNDS，无后继派发。详细证据与解释见ai4s/programs/mvcnet/research/cosine_readout/REPORT.md。














### 2026-09-27 MVCNet conv-SAM v0.1：新训练过程筛查









cosine-readout维持NO_SIGNAL并保留原生线性头。依据用户继续下一轮研究的授权，建立shared-convolution-parameter-sensitivity问题：固定共享Conv1d weight子集及rho=.05，对照零扰动、完整目标梯度方向和等范数随机方向；原CE/CVC/CMC、增强、VCN路由、Dropout和推理接口不变。双前向同批次重放必须证明S0原生等价及BN只提交一次。已知SAM思想适配，不作为原创模块。54训练+54封存后检查，新seed57/58，10小时实际预算、1阶段；尚未冻结或启动。权威设计见ai4s/programs/mvcnet/research/conv_sam/RESEARCH_BRIEF.md，动态状态见Program State。














## 2026-09-27 EDR-R1：单电极遮蔽训练鲁棒性筛查









SDT-R1 已完整关闭且未通过配对效用门。新增 EDR-R1，原模型 B0 对比训练时每样本恰好随机置零一个已标准化电极的 P1；保留全部原模型结构。历史电极删除证据与当前时窗不同，因此用新 B0 核验当前缺陷，不直接迁移历史损失量。以全部22种单电极置零后的平均准确率为主终点，同时要求清洁平均差值≥0及最差被试保护；这是新鲁棒性目标，不追溯改变旧轮判断。









9被试×seed0×2臂=18项100epoch训练，另2项源验证技术smoke。新6小时仅一轮；同配置明确OOM最多重试一次。合同 `ai4s/programs/dbconformer/research/dbconformer-edr-r1.yaml`，canonical SHA `e2e1993e7baa6940b599671fa56c21ae5b22b95063364452ac5b5f0197e5392c`；Run `2026-09-27_dbconformer_edr_r1_lab10_r1-full-w1`。技术验收与研究取舍见 [研究简报](ai4s/programs/dbconformer/research/edr_r1/research_brief.md)，实际状态以 Program State 和 [运行报告](ai4s/programs/dbconformer/research/edr_r1/REPORT.md) 为准；无科研结果或论文claim。














### 2026-09-28 MVCNet conv-SAM 冻结并提交









本轮合同及91文件source manifest已核验，Run `2026-09-27_mvcnet_conv_sam_lab10_r1-full-w1` 已上传并获远端同Run回执：RUNNING / WAIT_FOR_RESOURCES，当前smoke节点，尚无科学训练。固定54训练+54封存后检查、10小时实际campaign预算，纯资源排队扣除；无固定并发上限，逐项OOM重试。CPU真实三臂smoke、严格checkpoint回放、原生两步状态等价及封存接口已通过；Grok原CONDITIONAL保留，工程意见本地修复验收，不称外审PASS。权威状态见ai4s/programs/mvcnet/research/conv_sam/STATUS.md及Program State。














### 2026-09-28 MVCNet conv-SAM r1工程INVALID与r2修复









r1三项smoke均因最终包遗漏动态加载的DBConformer.py而在初始化失败，训练和检查均未启动；已回拉24项技术文件并核对远端SHA、正式记录工程INVALID，不形成科学负结论。r2仅显式补齐依赖与最终包初始化回归，训练算法/科学矩阵逐字节不变；服务器Python3.9三臂初始化及manifest验证PASS，已启动GPU技术smoke。用户明确追加8小时并启动，累计18小时，纯资源排队扣除；State extensions记录人工追加，不重写旧合同。Run `2026-09-27_mvcnet_conv_sam_lab10_r2-full-w1`；报告ai4s/programs/mvcnet/research/conv_sam/REPAIR_R2_REPORT.md。














2026-09-28 14:24 conv-SAM恢复更新：r2解决缺依赖后S0/P0 GPU smoke完成（峰值7629MiB），N0 cuDNN初始化失败，仍无科学训练；r2记录工程INVALID。已实施本轮第2次/最后一次工程修复r3，对精确CUDNN_STATUS_NOT_INITIALIZED按原3次和任务/GPU冷却作局部重试，不标成OOM、不改算法或增显存。8项容量测试、服务器最终包初始化/manifest通过，r3已提交且当前正常等待资源；累计18小时授权不变。报告ai4s/programs/mvcnet/research/conv_sam/REPAIR_R3_REPORT.md。














## 2026-09-28 EDR-R1 完整闭环









18科学训练+2技术smoke全部完成，0失败/0重试；234文件manifest/SHA和verified intake通过，原训练环境CPU重放清洁及全部22种单电极置零视图通过，独立指标逐行一致。冻结判定 INSUFFICIENT_PAIRED_TRAINING_SUPPORT，唯一失败门为clean_subject_safeguard：清洁ACC 57.0602%→57.1759%（+0.1157pp），但7/9被试下降、s7为−4.1667pp，低于−3pp底线。鲁棒ACC 44.4173%→53.6265%（+9.2093pp），9/9提高。









结论是有效的保护门失败，不是技术失败；关闭当前完整候选，保留精确置零协议下的鲁棒性线索，不外推清洁普遍收益、真实硬件可靠性或论文claim。Grok-4.6-build独立复核保留候选释放BLOCK、限定鲁棒描述WARN；其重放前置条件已满足，不改写原审查结论。单轮已关闭，无活动Run，预算余额0。证据/后续处置及原始外审见 [EDR报告](ai4s/programs/dbconformer/research/edr_r1/REPORT.md)。









2026-09-28 SST-DPN机制归纳（仅既有证据，无新训练）：JMR三种跨通道联合归一化相对Native总体约+2pp，S02损害/S05与S08获益方向一致；但JTN逐通道GN48总体-1.1285pp，不能归纳为任意非BN优越。Joint与centered RMS预测99.21875%一致、跨轮Joint预测100%一致，不能当独立重复。保留“SSA后/MVP前归一化统计参照与轴的条件性不适配”结构线索；未证实BN运行统计失配、均值保留原因或普遍BN缺陷。下一项仅设计固定Native checkpoint的source-only统计重估对照；无新Run。原JTN/JMR NO_SIGNAL与关闭边界不变。详见 ai4s/programs/sstdpn/research/bn-mechanism-synthesis-20260928/MECHANISM_SYNTHESIS.md。














## 2026-09-28 CMN-R1：clean/missing共同学习与条件统计









EDR-R1维持完整关闭：鲁棒ACC +9.2093pp且9/9改善，但clean7/9下降，最差-4.1667pp，未过保护门。已有预测488错出/494纠正仅证明决策重新分配，不证明表征信息永久删除；EDR实际是全部训练trial删除1电极，并无显式表示不变约束。根据用户机制问题及新6小时/仅一轮授权，建立CMN-R1：B0原模型、M0 clean/missing各半且共享BN、P1匹配混合训练且仅分离两个temporal BN的running统计（162额外非参数标量）。M0/P1训练算子匹配，P1额外同checkpoint clean-input/missing-bank检查只用于描述推理统计作用。









27项100epoch训练+3项source-valid smoke；clean均值/最差保护外新增6/9不下降覆盖门，P1须额外通过相对M0增量门。单seed探索，无正式claim、不自动下一轮。Grok设计审查无科学BLOCK，保留WARN及本地主控处置；实施验收、合同及同Run状态以 ai4s/programs/dbconformer/research/cmn_r1/research_brief.md、PRELAUNCH_ACCEPTANCE.json、REPORT.md及Program State为准。














## 2026-09-28 SST-DPN BNR判别对照已启动









固定JMR repair1已有6个Native checkpoint（S02/S05/S08×seed1/2），仅以source train+validation全体矩重估chanConv[1] BN运行统计，与原始checkpoint配对推理。0训练/优化更新，1 source-only技术任务+6科学配对，Lab10 gpu_light共享非独占。Run `2026-09-28_sstdpn_bnr_r01_v0_1-full-w1` 已probe到technical RUNNING，尚无新科学结果。唯一合同 `ai4s/programs/sstdpn/research/bnr-r01-v0.1.yaml`；设计、实现检查与状态 `ai4s/programs/sstdpn/research/bnr-r01-v0.1/`。只支持检验源EMA矩估计窄假设；原RMS关闭与既有NO_SIGNAL保留，非论文claim。














### 2026-09-28 BNR结果闭环（取代上条运行中状态）









同一Run已1技术+6科学配对全部完成，71文件verified intake；冻结分析及apply-decision为NO_SIGNAL。原始57.5231% → source-only BN矩校准57.1759%，差-0.3472pp；S02/S05/S08均值差分别-0.8681/-0.6944/+0.5208pp，仅S08两seed均正，未过事前平均收益与稳健被试数两门。全state核对只允许两BN running buffer变化，原预测6/6精确argmax回放，无训练或优化更新。降低简单源EMA矩估计充分解释的优先级；训练期批耦合、统计轴和源目标失配仍未分离。关闭该校准方案，不扫校准参数或被试选路；缺失统计轴×参照的训练对照仅为后续建议，未启动。Program COMPLETE_MAX_ROUNDS。报告 `ai4s/programs/sstdpn/research/bnr-r01-v0.1/CONCLUSION.md`；决策 `ai4s/programs/sstdpn/research/bnr-r01-v0.1_decision.yaml`，无paper claim。














### 2026-09-28 SST-DPN BJT 缺失格设计与实施









用户要求补 batch-reference + cross-C,T joint statistics，建立 bjt-r01-v0.1。仅新增 S02/S05/S08×seed1/2 六个 batch_joint fit及一个source-only技术epoch，复用已验证 JTN repair2 全18项三格历史对照。训练联合B,C,T标量矩，eval只用源EMA，逐C affine及原100/patience30+30训练日程不变；历史trainable初始化哈希为启动硬门。主门固定batch_joint-Native均值≥1pp、至少2被试双seed皆正、每被试均值≥-3pp；交互仅描述，跨Run比较不称独立因果复现。任务GPU预算4h、共享容量非独占，失败不自动增预算或补跑。设计及证据绑定 ai4s/programs/sstdpn/research/bjt-r01-v0.1/research_brief.md；当前本地实施验收，尚未产生新科学结果。Grok增量审查WARN，无公式阻断；原BNR/JTN/JMR NO_SIGNAL保留，无paper claim。实际冻结与Run以Program State及本轮合同为准。














BJT启动状态更新（2026-09-29 00:00）：`2026-09-28_sstdpn_bjt_r01_v0_1-full-w1` 已完成冻结、81文件Bundle校验、上传及同Run远端ledger核验。当前technical节点RUNNING/WAIT_FOR_RESOURCES，技术任务1 pending/0 running，尚未实际训练、无新科学结果；保持memory_only共享非独占，后台自动等资源且纯排队不计预算。精确状态与监控入口：ai4s/programs/sstdpn/research/bjt-r01-v0.1/STATUS.md、monitor.ps1。














2026-09-29 CMN-R1工程修复：原Run三臂GPU smoke均成功，但task技术报告缺identity_pass/target_evaluated导致Transaction汇总失败，已记录INVALID；27科学fit未开始。repair1补齐实际身份/目标评估字段并完成旧错误复现及三臂真实合成runner→task_evidence→emit_node_result回归；模型源码逐字节不变，全部科学设计/资源规则保持。沿用原6小时余额，独立Run 2026-09-29_dbconformer_cmn_r1_repair1_lab10_r1-full-w1已启动，重跑3smoke+27science，不复用旧权重。详见 ai4s/programs/dbconformer/research/cmn_r1_repair1/REPORT.md，动态状态以Program State为准。














### 2026-09-29 SST-DPN BJT完成闭环









BJT 1技术+6科学训练全部完成，109文件回拉校验/intake通过，冻结分析和原服务器环境24格预测重算一致，Program COMPLETE_MAX_ROUNDS。Native57.4942%、BatchJoint57.7836%、Channel56.3657%、Joint59.7222%；主门BatchJoint-Native +0.2894pp且仅S08双seed皆正，NO_SIGNAL。描述性交互+3.0671pp仅保留统计轴与参照组合、被试异质性线索，不能证明BN普遍缺陷或分离训练/推理因果。关闭精确候选，无追加训练或新轮；任务执行约0.941 GPUh，峰值1387MiB。详见 ai4s/programs/sstdpn/research/bjt-r01-v0.1/CONCLUSION.md；no_paper_claim。














### 2026-09-29 SST-DPN RFX研究设计（未执行）









根据JTN/JMR/BNR/BJT完整证据，将统计轴×参照线索收敛为固定checkpoint的双向推理参照对照：24个既有checkpoint，各保留原轴与权重/affine，对比trial与source-exact，共48科学view，含原部署回放共60不重复view，0新训练。24项hash核验完成；JTN Native与BNR JMR Native 6项hash均不同，不直接复用校准数值。该诊断可判别部署参照敏感性，不能分离纯训练效应；结果必须决定是否继续参照一致性设计或停止。研究登记DESIGN_ONLY，代码/科学合同/新预测尚未执行，原COMPLETE_MAX_ROUNDS与NO_SIGNAL不变。详见 ai4s/programs/sstdpn/research/rfx-r01-v0.1/research_brief.md 与RESEARCH.json。














2026-09-29 CMN-R1 repair1完整闭环：27科学fit+3smoke首次成功，354文件verified intake、原环境全部checkpoint/22缺失视图重放及独立指标复算一致。B0 clean/robust57.0602/44.4173%，M0 57.7160/54.1176%，P1 57.0988/53.1829%；robust均9/9改善，但clean不下降仅3/9与4/9，最差−3.9931/−9.2014pp。冻结判定INSUFFICIENT_PAIRED_TRAINING_SUPPORT，关闭两精确配置；P1无条件统计增量。bank切换平均clean效应−0.0386pp、s7为0，不证明信息毁损或普遍必然取舍。COMPLETE_MAX_ROUNDS，无新Run/claim。权威报告 ai4s/programs/dbconformer/research/cmn_r1_repair1/REPORT.md。














### 2026-09-29 SST-DPN RFX执行授权与实施









用户明确“继续执行”，授权单轮RFX固定checkpoint推理参照诊断。范围为24个既有checkpoint、48科学视图及12原source-EMA回放视图，0训练和0优化器更新，任务GPU时间不超过2小时；采用Lab10 memory_only共享非独占准入。11项本地核函数/入口测试通过，24个checkpoint严格加载及张量一致性检查通过；限定核函数Grok外审无BLOCK，真实源数据技术门仍须服务器验证。结果仅用于判断推理参照敏感性与后续设计取舍，不产生论文主张；最终冻结、运行及闭环状态见 ai4s/programs/sstdpn/research/rfx-r01-v0.1/STATUS.md。









RFX启动状态（2026-09-29 11:26）：`2026-09-29_sstdpn_rfx_r01_v0_1-full-w1` 已冻结、完成100文件Bundle校验、上传及同Run远端核验。当前technical任务1 pending/0 running，WAIT_FOR_RESOURCES；尚未实际预测。保持共享非独占及纯资源等待不计预算，服务器获准入后自动推进本轮技术门与24项科学任务。状态和只读监控见 ai4s/programs/sstdpn/research/rfx-r01-v0.1/STATUS.md、monitor.ps1。














### 2026-09-29 DBConformer CPA-R1 方向切换与准备









用户要求由共享模型鲁棒训练转向clean路径保留、缺失条件专用适配。依据EDR/CMN的逐被试clean损害，建立CPA-R1：冻结9个已验证B0，缺失时训练462参数空间残差，P1仅补偿缺失位置、U0全位置容量对照，clean直接走原模型。9锚点SHA/源码/严格重载/合成B0等价核验与6项CPU合成测试通过；Grok独立审查WARN、无设计BLOCK，但训练/选模/Transaction尚未完成验收。本轮预算待用户确认，0新真实数据fit、无新Run、无claim，旧CMN结论不变。后续状态见 ai4s/programs/dbconformer/research/cpa_r1/REPORT.md 与STATUS.json。














### 2026-09-29 SST-DPN RFX闭环









RFX 1技术+24科学任务、60预测视图完成；回拉manifest/SHA、verified intake、冻结分析和原服务器重算一致。判定NO_SIGNAL，Program COMPLETE_MAX_ROUNDS。trial−source-exact：Native −3.0671pp、Channel +0.7523pp、Joint +0.3472pp、BatchJoint +0.4919pp；两CT臂均未达1pp门。关闭通用部署参照替换候选；保留训练期表征/统计轴交互与被试异质性的后续设计约束，不据此证明BN普遍缺陷，不自动启动新实验。任务内执行0.286 task GPUh，峰值1249MiB，零训练。详见 ai4s/programs/sstdpn/research/rfx-r01-v0.1/CONCLUSION.md；no_paper_claim。









2026-09-29 CPA-R1预算确认：用户回复“确定”，新设6小时且仅一轮；campaign dbconformer-v3-20260929-cpa 已登记，自动upload/launch/probe/fetch/intake授权已绑定。范围18项missing-only适配训练+2项smoke，冻结9个B0与clean路径，U0/P1各462参数；当前实现与验收准备，尚未冻结/启动，旧CMN结论不变。实际状态见 ai4s/programs/dbconformer/research/cpa_r1/STATUS.json。














### 2026-09-29 SST-DPN TAI下一轮研究设计









用户指定固定推理参照、控制训练参照以研究表征与统计轴交互，已登记TAI-v0.1设计。四臂BPC/TPC/BCT/TCT分别控制训练batch/trial参照与per-C/CT统计轴；四臂推理算子连统计轴均统一为source-exact CT，每模型独立无标签源矩。取消历史validation-best/early stop，固定100+30轮及阶段末checkpoint，24项新配对fit（S02/05/08×seed1/2×4臂），旧checkpoint不充作新对照。主交互与CT内trial效用必须同时过门，源表示CKA/有效秩只作描述。资源提案14 task GPUh、共享非独占；这是新fixed-schedule探索协议，不能与历史native协议直接作收益claim。当前DESIGN_ONLY，未实现/训练/上传/建立Run，原RFX NO_SIGNAL与COMPLETE_MAX_ROUNDS保留。详见 ai4s/programs/sstdpn/research/tai-r01-v0.1/research_brief.md、DESIGN_CONFIG.json、RESEARCH.json。














### 2026-09-29 SST-DPN TAI启动授权









用户在收到24项新配对训练、4项source-only技术epoch、固定100+30轮与14 task GPU小时的TAI方案后明确“启动实验”。本轮按该精确范围实施、验收与冻结，Lab10共享非独占；技术门通过后才启动科学任务。准备时点DESIGN_CONFIG/RESEARCH保留不回写为执行证据，执行授权另见 ai4s/programs/sstdpn/research/tai-r01-v0.1/AUTHORIZATION.md。当前尚未提交Run。














### 2026-09-29 CPA-R1 冻结上传与资源排队









用户确认的 6 小时单轮 CPA 已冻结并上传，Run `2026-09-29_dbconformer_cpa_r1_lab10_r1-full-w1` 已获服务器接收。启动前本地训练/重放/控制器回归与服务器 Python3.9.25/Torch1.13.1 下的包、9锚点及6项CPU测试通过；Grok增量WARN及显式eval提醒的本地修复记录完整保留。核验时两个smoke尚在资源队列、0个真实GPU任务开始，原因是当前显存不足6144MiB；已允许共卡且额外预留0，纯资源排队扣时。18项科学训练须smoke通过后执行。当前无新科学结果、无claim，等待同一Run闭合→回拉核验/intake→原环境重放→冻结门判定。权威状态见 ai4s/programs/dbconformer/research/STATE.yaml，运行记录见 ai4s/programs/dbconformer/research/cpa_r1/REPORT.md。









### 2026-09-29 SST-DPN TAI冻结上传与资源排队









TAI-v0.1已按用户“启动实验”冻结，Run `2026-09-29_sstdpn_tai_r01_v0_1-full-w1` 已上传并启动后台Transaction；probe核实WAIT_FOR_RESOURCES。启动核验时4项源-only技术任务pending、0项真实训练开始，24项科学fit等待技术门。共享memory_only、allow_same_owner=true、2048MiB任务承诺+3072MiB保留，非独占；纯资源排队不计14 task GPU小时预算。17项不同本地测试及合成kernel→runner预测重载链通过，Grok外审的合同兼容问题已由主控修复并实测往返；外审原报告与处置保留。真实GPU门尚未通过，无新科学证据/claim，RFX旧NO_SIGNAL不变。权威状态见 ai4s/programs/sstdpn/research/STATE.yaml，启动记录见 ai4s/programs/sstdpn/research/tai-r01-v0.1/STATUS.md。














### 2026-09-29 SST-DPN TAI 修复补跑（repair2）









原TAI四项技术任务在第1轮训练后CUDA RNG恢复失败，正式科学训练0/24；已登记工程INVALID。修复RNG CPU状态恢复，新增真实CUDA回归。repair1漏改固定Run前缀，在调度前失败，0训练；保留失败记录后以repair2更正。









`2026-09-29_sstdpn_tai_r01_v0_1_repair2-full-w1` 已冻结上传启动；当前4技术任务等待共享显存，0科学训练开始，非独占。19项回归和实际冻结Bundle入口/源码闭包检查通过，真实GPU技术门仍待执行。四臂、S02/05/08×seed1/2、固定100+30轮及source-exact CT推理不变；14 task GPU小时不变。整体campaign时间窗口16→18小时，历史成本与起始时间保留；原始授权及补充见 `ai4s/programs/sstdpn/research/tai-r01-v0.1-repair2/`。









没有新科学结果或claim。权威状态为Program STATE/EVIDENCE_INDEX；只读看板与启动状态见该目录 `monitor.ps1`、`STATUS.md`。














### 2026-09-29 CPA-R1 训练完成与验收 INVALID









2技术+18科学任务完成，回拉293项manifest/SHA与verified intake通过，本地20任务CPU重放通过。原服务器全量CPU重放在smoke的candidate22-view校验失败，窄范围诊断和原日志均保留；未放宽冻结容差、未改checkpoint或预测。冻结门据此判为INVALID，这是复现验收未通过，不是研究方向被证伪。暂定缺失ACC B0 44.4173%、U0 52.0807%、P1 56.7884%，clean均57.0602%；这些数值不释放正向科学判定或论文claim。结果处置外审PASS原样保留。Program COMPLETE_MAX_ROUNDS，不启动新实验；后续先处理原环境验证差异。详见 ai4s/programs/dbconformer/research/cpa_r1/REPORT.md、ANALYSIS.json 及 Program STATE/EVIDENCE_INDEX。














### 2026-09-29 SST-DPN TAI repair3









repair2技术3完成/1失败，TCT初始快照cuDNN错误，正式科学0/24，已登记工程INVALID。用户再次授权修复并补跑。repair3将全源GPU输入列表改为按原顺序逐批传输，20项测试通过；本地GPU生产形状快照全部数组精确一致，峰值分配约395→56MiB。cuDNN唯一根因未证明，补显存诊断，不修改训练科学协议/后端或独占策略。









新Run `2026-09-29_sstdpn_tai_r01_v0_1_repair3-full-w1` 已上传启动并核实等待共享显存（4技术pending，科学0/24）；门全通过后自动进入原24项训练。累计task GPU预算14小时不变，技术尝试预算12，整体campaign窗口18→22小时，原开始时间和成本保留。详见 `ai4s/programs/sstdpn/research/tai-r01-v0.1-repair3/STATUS.md`、`DIAGNOSIS.md`、`AUTHORIZATION.md`。无新科学结论。














### 2026-09-29 CPA-R1 replay 数值边界已解释









用户要求正式定位唯一argmax差异。固定原数据/划分/checkpoint/归一化输入，18次CPU前向完成最小复现与线程/后端/FP64对照；原环境跨进程5次输出相同。类别1与3间隔从16ULP经−9/+9ULP扰动变为−2ULP；精确有理数恒等式成立。全矩阵20415/20416预测的margin>2E，唯一例外与差异坐标一致；跨环境FP64最大logit差8.88e−16。结论为该观测差异是有限精度边界翻转，未归责到单一内核。原CPA INVALID/合同/预测不变，无新训练或科学claim；工程证据已追加到Evidence Index。后续验收恢复需独立约定，不能静默放宽旧门。详见 ai4s/programs/dbconformer/research/cpa_r1/replay_discrepancy/REPORT.md。














### 2026-09-30 CPA-R1 同产物预注册恢复验收完成









不重训、不改模型；新规则在完整重放前冻结，保留原1e-5容差，以全部可能winner集合及保守准确率包络验收。原环境20/20任务、80预测族通过，唯一实际argmax差异仍在U0 smoke边界内；科学任务有7个预测族边界行（含重复锚点），均未实际翻转，全部科研门在完整包络内稳定。U0/P1条件适配效用通过，P1相对U0最差被试−6.2263pp门仍失败。恢复处置RETAIN_CONDITIONAL_ADAPTATION_FEASIBILITY_ONLY；原INVALID/合同/分析/State在本次恢复期间均保留原字节，无正式claim。规则、复审、哈希、全量重放及独立分析见 ai4s/programs/dbconformer/research/cpa_r1/replay_recovery_r1/REPORT.md。用户随后另行授权基于结果设计下一轮、追加预算、上传启动；该授权不改写本次恢复的零训练边界。














### 2026-09-30 CPA-U0-R2 固定锚点适配随机性复核准备









基于已完成的CPA预注册恢复验收，下一轮保留U0原462参数结构与训练核心，固定9个seed0 B0/划分/归一化，仅增加adapter seeds1、2，共18科学拟合+2 smoke。按CONFIRM_TO_CAP延续同一饱和键，累计seed0/1/2；每个fresh seed和两seed逐被试均值分别过原效用门，旧seed0不池化救援，P1失败增量不重开。用户已授权自主设计、追加预算、上传启动；追加额度尚待明确，当前仅设计实现与CPU合成检查，未建新campaign/冻结/上传/训练。详见 ai4s/programs/dbconformer/research/cpa_u0_r2/research_brief.md 与 STATUS.json。









### 2026-09-30 CPA-U0-R2 preparation closeout









CPA 同冻结产物恢复验收已关闭（20/20、新规则下科学处置稳定、原 INVALID 保留）。下一轮选择 unchanged U0 + fixed seed0 B0/splits + adapter seeds 1/2，9 被试共18科学拟合与2 source-only smoke；逐 seed 与被试均值三组均须通过既定效用门。P1-U0 最差被试 -6.2263 pp 失败不重开。Grok 第二次审查完成，外部 verdict WARN（设计实现可接受；预算/路由条件）；受审路由补丁已应用并验证，现只待预算额度。用户已授权追加预算、上传和启动，但未提交小时数，不把 fixture 6h 当授权。









记录：`ai4s/programs/dbconformer/research/cpa_u0_r2/REPORT.md`。














### 2026-09-30 CPA-U0-R2 6小时单轮启动与入口修复









用户明确新增6小时、仅一轮，并已授权上传启动。原U0/训练/数值比较核心保持原字节；固定9个B0 seed0锚点，adapter seeds1/2，18科学+2source-only smoke。原R2与packagefix1在上传前发现清单/数据绑定缺口，保留冻结版本；packagefix2真实入口缺ROOT导入路径，零task证据、零科学拟合，已按正式失败元数据流程记工程INVALID。packagefix3只修启动器路径和独立子进程入口回归，正式authorize-invalid-repair后沿同campaign预算启动。不得据此改写原CPA INVALID或release claim。









更新（2026-09-30T06:02:26Z）：packagefix3 的2/2 smoke通过，18项screen已自动开始，3运行、15待调度、0失败；尚未闭环，无科学结论。继续按同一冻结合同与原6小时预算收尾。














### 2026-10-03 CPA-U0-R2 同Run最终验收









CPA-U0-R2 packagefix3 经ccmu跳板确认全部20任务完成、回拉清单核验、标准intake、原环境及本地CPU replay和独立数值包络审计通过，正式登记 CPA_U0_ADAPTER_SEED_STABILITY_SUPPORT。seed1/seed2/被试内均值收益分别7.0006/7.1637/7.0821pp，三组9/9正收益、clean逐位保留。仅支持9个固定B0锚点下的adapter随机性复核；目标历史暴露，无论文claim。单轮关闭；下一对照应检验独立主模型锚点依赖，但尚未授权启动。报告 ai4s/programs/dbconformer/research/cpa_u0_r2_packagefix3/REPORT.md。














### 2026-10-03 BDA-R1 独立B0性能与backbone依赖复核启动









用户授权新增6小时、仅一轮独立B0与配对U0；固定原source划分，9被试×backbone seeds1/2共18 B0，每个B0配固定adapter seed1的原U0，共36科学+2 source-only smoke。B0绝对clean/缺失性能与U0增量分别报告，不按目标表现筛锚。三组效用门使用各seed自己的新B0包络。25项测试、完整bundle与Lab10原环境CPU合成验收通过，Grok原BLOCK保留且必改项本地闭合。合同已冻结，ccmu跳板上传95文件SHA通过；同Run启动器已接受，当前smoke纯资源排队、尚未真实训练，无科学结果/claim。详见 ai4s/programs/dbconformer/research/bda_r1/REPORT.md。














### 2026-10-03 BDA-R1迁移至ccmu双卡









用户明确授权迁移，并将同campaign总预算从6小时扩至8小时、仍仅一轮，保留原起点与纯排队扣除。Lab10原Run已停止且0拟合/0checkpoint。原Python3.9.25、Torch1.13.1+cu116/CUDA11.6打包至ccmu独立环境，CPU及两张RTX3090的真实B0/U0合成验收通过。ccmu1在训练前被共享调度器完整范围保护拒绝；原失败Run/合同留存，ccmu2冻结显式B0/U0 phase IDs、SHA、命令和顺序，并采用私有phase执行入口。原9被试×B0 seeds1/2及各自配对U0 seed1矩阵与科研判定不变。实际启动状态与证据入口见 ai4s/programs/dbconformer/research/bda_r1_ccmu2/REPORT.md；不据提交或smoke宣称科学结论。












## D-182 SST-DPN 固定per-C的训练与推理参照因素研究







2026-10-04，用户明确选择train-reference × eval-reference方向。TPC verified诊断在固定per-C下的交互约+6.22pp含BPC下降，S05仍异质；TAI/BJT旧NO_SIGNAL保持。新增TRA-v0.1采用batch/trial训练、source-exact/trial推理，fresh seeds3/4、三开发被试配对从头训练，固定100+30日程与阶段末点。要求两方向各自绝对优势，不将相对反转视为普遍恢复。







这是一项有历史暴露的前瞻性开发筛查，不能称独立盲确认；没有独立算子因素，因此不能裁决“不匹配损害大于算子本身”。Grok只读设计外审为WARN，限制逐项纳入，未改判PASS。4.5 task GPUh是待批准新预算，当前零新科学fit、无Run派发；不得继承旧campaign余额。设计与处置见 ai4s/programs/sstdpn/research/tra-r01-v0.1/research_brief.md 和 REVIEW_DISPOSITION.md。













### 2026-10-04 NNC-R1 U0近邻去留对照









用户要求进行能够决定 U0 去留的近邻对照，并授权新设6小时仅本轮。复用已验收BDA的18个独立B0及18个配对U0，不重训；新拟合 source-only 零对角 RIDGE 与 frozen-backbone SSF-style 对照，各18项，加2个source-only smoke。U0相对两个近邻在两个backbone seed及逐被试均值组均须达到 +0.5pp均值、6/9正收益、最差不低于-3pp、全部LOO均值正，且保留U0-B0 +1pp门与cleanexact。完整失败则撤下独立方法候选；数值跨门则未决；无加种子或救援。目标群体已暴露，SSF容量不同，不释放论文claim。当前为设计/实现/验收准备，尚未启动或产生科学结果。权威入口：ai4s/programs/dbconformer/research/nnc_r1/research_brief.md及Program State。












### D-183 — TRA-v0.1 授权执行与启动失败（2026-10-04）







用户授权后冻结新合同并通过 ccmu 上传启动 Run `2026-10-04_sstdpn_tra_r01_v0_1-full-w1`；技术节点约 0.869 秒内在调度器前因 scope 先引用后赋值失败，两个技术任务及 12 个科学 fit 均未启动，目标预测为 0。已按 metadata-only 登记 INVALID（AI4S-SSTDPN-tra-r01-v0.1）；没有 scientific intake 或效应结论。原预注册与合同不变。最小修复补丁和两项入口回归测试已准备；保持 4.5 task GPUh、100+30、12 fits/24views/2technical、非独占和一次尝试，新增修复 Run 待明确授权，自动修复 0 次约束仍有效。











### D-184 — TRA repair1 启动失败与路径修复资格检查（2026-10-04）







用户授权原范围和预算的新修复 Run `2026-10-04_sstdpn_tra_r01_v0_1_repair1-full-w1`。修复 scope 赋值顺序及技术汇总 both_view 字段层级；14 项本地测试通过。已冻结上传启动，但因迁移执行目录后未绑定原 canonical DESIGN_CONFIG 路径，技术节点在调度前约7.427秒失败；0技术训练、0科学fit、0目标预测。已登记 AI4S-SSTDPN-tra-r01-v0.1-repair1 为 INVALID 工程失败。两行路径补丁已在真实Lab10只读CPU路径中通过71个源码绑定、data/split manifest、S02/S05/S08 split及4032×22×1000 source-only输入接口核验；没有训练或目标值读取，没有改写旧Run。repair2未授权或启动，保留原campaign时钟和4.5 taskGPUh等预算，进一步自动修复0。











### D-185 — TRA repair2 真实技术门通过与科学训练启动（2026-10-04）







用户授权原范围和剩余预算的新Run `2026-10-04_sstdpn_tra_r01_v0_1_repair2-full-w1`。修复canonical设计路径及bundle-root相对路径解析，保留之前入口修复；16项本地测试通过，实际上传包CPU核验73文件manifest/72源码绑定、source数据与split、4032输入、双公式梯度及launcher哈希通过，随后启动同一Run。真实BPC/TPC技术任务各1次、101步，两个视图/state/RNG/无目标读取均通过；完整进程峰值1393/1369MiB，technical ledger PASS且逐任务证据SHA已核对。科学节点RUNNING，10:07:40UTC快照：5running、7pending、0completed、0failed；12fits/24views、perC、S02/S05/S08、seed3/4、100+30不变，memory_only非独占，原campaign及数值预算不重置。只核验技术和资源状态，不读取科学中间效能；完成后仍需fetch/manifest verify/intake/replay/decision，尚无科学结果或paper claim。













### 2026-10-04 NNC-R1 smoke工程失败及repair1就绪









NNC-R1首Run已真实启动但source-only smoke因Torch1.13 weights_only读取Ridge checkpoint Python float失败，未进入screen；已登记INVALID工程记录，无科学结果，不说明U0失败。repair1保持原36+2任务和去留门，使用tensor-only checkpoint并绑定新不可变身份、源失败forensic SHA。原Torch实际loader验证、10项回归、整包资格及Grok终审PASS，controller有限路由就绪。18:29原6小时余额约4.68小时，低于冻结4.75小时启动预留；询问总预算7小时仅本次恢复，答复前不恢复启动。权威：ai4s/programs/dbconformer/research/nnc_r1_repair1/REPORT.md、STATE和EVIDENCE_INDEX。














### 2026-10-04 NNC-R1 repair1总7小时恢复启动









用户回复“增加”，批准先前提出的本轮campaign总预算7小时，仅完成本次近邻对照，起点仍17:10:18 CST。repair1冻结合同、原环境验收、297文件SHA上传闭包和真实启动回执通过；Run 2026-10-04_dbconformer_nnc_r1_ccmu_r2-full-w1。19:25两项smoke通过，36项screen RUNNING，快照5完成/6运行/25待执行/0失败，物理GPU0/1工作。此为执行进度，无科学结论或论文claim；不重训B0/U0、不加轮次，后续同Run关闭后回拉核验/intake/原CPU replay/固定去留门。权威：ai4s/programs/dbconformer/research/nnc_r1_repair1/REPORT.md及STATE。












### D-186 — TRA repair2 完整入库与参照交互正信号（2026-10-04）







Run `2026-10-04_sstdpn_tra_r01_v0_1_repair2-full-w1` 已完成2技术任务、12次100+30新训练和24views；固定perC、S02/S05/S08、seed3/4、非独占。完整回拉核验/重放通过，SCREEN_POSITIVE：gB +2.5463pp、gT +1.3600pp、I +3.90625pp、M +1.953125pp，五门均过。S02/S08交互双seed正；仅S08双向匹配均正，S05 I从−2.0833到+5.9028pp翻转。支持平均train/eval参照交互，尚非被试普适co-adaptation或独立盲确认；没有operator因素，不能比较不匹配与算子损害。SCP超时原文件保留，归档恢复同Run并核验；冻结分析器显存字段错层由单独本地adapter修正并独立复核，原产物/科研阈值未变、未补训。当前轮关闭，后续独立被试完整因素矩阵需另行设计授权，禁止按目标标签选参照。权威：ai4s/programs/sstdpn/research/tra-r01-v0.1-repair2/ANALYSIS_REPORT.md、ANALYSIS_RESULT.json、State/Evidence Index。











### TRA-C01 跨被试复核准备（2026-10-04）







TRA-C01-v0.1：用户选择独立被试确认，已完成暴露审查，范围S03/S04/S06/S07/S09，seed3/4，perC BPC/TPC×source/trial，20新fit/40views，100+30，S01封存。角色为跨被试固定方案复核，不能称盲法主确认。新5单元source-only split与纯分析器已准备，Grok设计PASS with WARN。五门：平均gB/gT各≥1pp、I≥2pp、4/5被试双seedI>0、每被试M≥−3pp；失败不补seed/选被试/调门。提议7taskGPUh、Transaction7.5h、新campaign8.5h、单轮、非独占、自动修复0，旧预算不继承；新增预算未批准，尚无Transaction/upload/训练或科学结果。权威：ai4s/programs/sstdpn/research/tra-c01-v0.1/research_brief.md、PREPARATION_STATUS.json。













### 2026-10-04 NNC-R1分析恢复闭环与U0去留









NNC repair1同一Run38/38原CPU replay通过，分析恢复v2只修复smoke身份谓词与已校验evidence解包，两轮Grok终审PASS，无重训或科学门变化。最终冻结去留门INSUFFICIENT_U0_NEAREST_NEIGHBOR_SUPPORT：U0相对B0配对均值+7.1430pp（9/9正），但相对同462参数RIDGE -4.9738pp（1/9正；两seed均失败）；SSF配对均值虽过门，seed1正收益不足、seed2最差低于-3pp。按预注册规则撤下U0独立创新候选、保留基线/问题证据。controller已登记EvidenceIndex exact_negative_boundary，Program COMPLETE_MAX_ROUNDS，本轮7小时授权内闭环，无自动下一轮、论文claim或RIDGE晋升授权。权威报告：ai4s/programs/dbconformer/research/nnc_r1_analysis_recovery2/REPORT.md。














### D-187 — TRA-C01 固定跨被试复验授权与执行资格（2026-10-05）









用户回复“批准”，授权TRA-C01跨被试固定复验：S03/S04/S06/S07/S09、seed3/4，20新训练/40视图及2 source-only技术epoch，固定perC BPC/TPC×source/trial，100+30。新campaign8.5h、Transaction7.5h、7 task-GPUh、单轮、非独占memory_only、自动修复0，历史campaign不重置。34项本地离线资格检查通过。首次预派发封包早于intake最后定稿，原contract/bundle完整保留且未登记/上传/训练；qualified1绑定最终代码，未扩大科学范围或预算。实际Run身份：2026-10-04_sstdpn_tra_c01_v0_1-qualified1-full-w1。此记录仅为授权与执行准备，实时状态以STATE及EXECUTION_REPORT为准；尚无新科学结论或论文claim。














### TRA-C01 qualified1 工程失败收尾（2026-10-05）









TRA-C01 qualified1 Run已实际上传并启动，但因包漏带已冻结DATA_MANIFEST.json在约1.36秒内技术节点调度前失败；实际技术/科学训练均0，目标预测0。此前34项离线测试与远端70源码/CPU检查未覆盖data_manifest真实入口，属于封包和验收遗漏。已按精确ledger/log/空evidence metadata核验登记INVALID工程失败，没有科学结论。已准备补齐既有manifest依赖及实际no-fit closure验收补丁；原包/失败证据保留，新immutable修复Run尚未启动或授权。保持原新campaign时钟和7 taskGPUh等冻结预算，自动修复0。权威：ai4s/programs/sstdpn/research/tra-c01-v0.1/EXECUTION_REPORT.json、tra-c01-v0.1-qualified1_decision.yaml。














### 2026-10-05 U0链收口与网络结构主线恢复









按用户明确指示：U0撤下独立创新候选，保留辅助baseline；RIDGE保留已知单通道缺失范围的强近邻/强baseline；EDR→CMN→CPA→adapter-seed→backbone-seed→NNC完整链保留为论文鲁棒性分析、辅助实验或讨论证据，不作为主创新已成立的证明。原INVALID、数值恢复和累计选择暴露保留，原冻结decision不变。下一轮主线恢复为网络结构创新，用户新设8小时仅一轮；当前正在准备池化前局部时间条件化空间聚合及同参数对照，未产生新科研结论。定位记录：ai4s/programs/dbconformer/research/architecture_next_20261005/CLOSEOUT.md。














### TRA-C01 manifest修复恢复与时间预算扩展（2026-10-05）









用户授权TRA-C01补齐manifest修复，并明确增加时间预算；campaign总时限8.5→9.5h，保留原起点，7 taskGPUh/Transaction7.5h/单轮及20fit40views+2技术epoch不变。旧INVALID Run保留；第一次修复包因共享runtime被封包工具替换为非绑定版本，被all-source检查在启动前拒绝，真实claim/ledger/receipt缺失证明确认0训练，已归档；新qualified1包完整93文件/92源码SHA及actual DATA/SPLIT/source/data-file-existence入口验收通过，经ccmu上传并真实启动。Run 2026-10-05_sstdpn_tra_c01_v0_1_repair1_qualified1-full-w1；当前RUNNING_WAIT_FOR_RESOURCES，任务计数见执行报告，尚无科学结论或论文claim。非独占memory_only；队列等待排除执行时间，不额外派发自动修复。权威：ai4s/programs/sstdpn/research/tra-c01-v0.1-repair1/EXECUTION_REPORT.json及STATE。














### 2026-10-05 LTA-R1 repair2 launch









结构探索 LTA-R1 repair2 已在 CCMU 双 RTX3090 真实启动。保留原模型 B0，比较同参数全局时间 query C0 与逐窗 query P1 的局部空间池化；3 臂×9 已暴露被试×seed0，100 epoch。两次工程停止均保留 INVALID，science 0/27，旧 partial 不复用。基于实际成本门仅将 screen/transaction 上限调整至9600/10200秒，总8小时单轮不重置；科学门、模型、训练与 replay 规则未改。source smoke 3/3通过，正式任务已出现训练 epoch；尚无本轮科学结论。详见 `ai4s/programs/dbconformer/research/lta_r1_repair2/REPORT.md`。














### 2026-10-05 LTA-R1 repair3 launch









结构探索 LTA-R1 repair3 已在 CCMU 双 RTX3090 真实启动。保留原模型 B0，比较同参数全局时间 query C0 与逐窗 query P1 的局部空间池化；3 臂×9 已暴露被试×seed0，100 epoch。前三次工程停止均保留 INVALID，不复用旧 partial；r3新query/key全部1800轮末批有限非零，宽正则误绑原模型冗余keys.bias导致误拒。本次只精确绑定新模块梯度对象和对应验收记录，总8小时单轮及600/9600/10200秒上限不重置；科学门、模型、训练、范数采样与 replay 规则未改。source smoke 3/3通过，正式任务已出现训练 epoch；尚无本轮科学结论。详见 `ai4s/programs/dbconformer/research/lta_r1_repair3/REPORT.md`。














### 2026-10-05 LTA-R1 repair3 closure









LTA-R1同一Run已完整回拉、SHA/manifest核验、intake及原环境CPU重放，并登记正式探索处置。B0/C0/P1 clean ACC 均值依次为57.6196/56.3079/57.0409%，冻结判定 `INSUFFICIENT_LOCAL_TEMPORAL_INCREMENT_SUPPORT`。 精确范围仅9名已暴露被试、seed0；不发布论文Claim，不自动续下一轮。完整门、数值区间及后续处置见 `ai4s/programs/dbconformer/research/lta_r1_repair3/REPORT.md`。














### 2026-10-05 RCC-R1 structure design









LTA-R1精确负结果已关闭，不复活其加权池化，也不恢复U0独立创新候选。完整12候选经实际Grok只读排序后，本轮只选择RCC-R1：在原DBConformer两支40维摘要后插入1280参数的跨支加性可逆耦合P1，以同四子网、同初始化的支内耦合C0及原B0为对照。可逆耦合已有NICE/RevNet/EEG-InvNet先例；只具探索资格，不宣称信息保存、首次交互或论文创新。用户新设8小时仅一轮，起点2026-10-05T06:02:02.994686Z，准备时间计入。证据、设计及双必要对照见ai4s/programs/dbconformer/research/rcc_r1/research_brief.md。














### 2026-10-05 RCC-R1 launch









RCC-R1同一Run `2026-10-05_dbconformer_rcc_r1_ccmu_r2-full-w1` 在CCMU双3090真实训练，source-only smoke3/3通过并已出现正式训练epoch。B0原结构、C0支内耦合、P1跨支耦合，27fits、9已暴露被试、seed0、原100epochs。8小时单轮起点不重置；等待完整闭环后才有科学结论。详见ai4s/programs/dbconformer/research/rcc_r1_native1/REPORT.md。














### 2026-10-05 RCC-R1 user requested stop after formal launch









用户明确要求正式运行后无需持续监控。本轮已核验正式启动，本地只读监控已停止，服务器冻结Run继续。后续仅应用户请求核验同一Run状态；完成后回拉核验、intake、原环境回放和分析。不改科学合同、预算起点或单轮上限。详见ai4s/programs/dbconformer/research/rcc_r1_native1/MONITORING_HANDOFF.json。














### 2026-10-05 RCC-R1 closure









RCC-R1同一Run `2026-10-05_dbconformer_rcc_r1_ccmu_r2-full-w1` 完整关闭、SHA/manifest核验、intake及原环境CPU replay完成。B0/C0/P1 cleanACC均值57.6196/57.8125/58.1404%，正式探索判定 `INSUFFICIENT_CROSS_BRANCH_COUPLING_INCREMENT_SUPPORT`。结果仅适用于9已暴露被试seed0；不发布论文Claim，不自动下一轮。详见ai4s/programs/dbconformer/research/rcc_r1_native1/REPORT.md。














### 2026-10-05 PAT-R1 structure design









RCC/LTA有效负结果已关闭，U0独立创新资格已撤下，不恢复这些对象。18候选经实际Grok只读排序，本轮仅选PAT-R1：保留原全局空间token与时间分支，在空间预池化CNN特征计算8点4维路径六个二阶面积，添加22辅助空间token；同304权重、同路由的对称增量积C0及原B0作对照。签名、学习轨迹与signature attention均有先例，只具探索资格，不声称首次或生理方向。用户新设8小时仅一轮，起点2026-10-05T11:31:35.903945+00:00，准备计入；正式训练启动后返回不持续监控。详见ai4s/programs/dbconformer/research/pat_r1/research_brief.md。














### 2026-10-05 PAT-R1 launch









PAT-R1同一Run `2026-10-05_dbconformer_pat_r1_ccmu_r1-full-w1` 在CCMU双3090真实训练，source-only smoke3/3通过并已出现正式训练epoch。B0原结构、C0对称增量积辅助token、P1二阶轨迹面积辅助token，27fits、9已暴露被试、seed0、原100epochs。8小时单轮起点不重置；正式启动后按用户要求返回不持续监控；完整闭环后才有科学结论。详见ai4s/programs/dbconformer/research/pat_r1/REPORT.md。














### 2026-10-05 PAT-R1 user requested stop after formal launch









用户明确要求正式运行后无需持续监控。本轮已核验正式启动，本地只读监控已停止，服务器冻结Run继续。后续仅应用户请求核验同一Run状态；完成后回拉核验、intake、原环境回放和分析。不改科学合同、预算起点或单轮上限。详见ai4s/programs/dbconformer/research/pat_r1/MONITORING_HANDOFF.json。














### 2026-10-05 PAT-R1 repair1 提交与资源排队









PAT-R1原失败保留为INVALID。新不可变修复Run `2026-10-05_dbconformer_pat_r1_ccmu_repair1-full-w1` 已登记、上传并实际启动；40项工程测试、Grok最终交叉审查、原环境CPU包与合成回放验收通过。仅改变extra梯度范数诊断的FP32实现，真实零/非有限仍拒绝；模型、训练、数据、选择和科学门不变。9项B0已独立资格核验并恢复，18项C0/P1补跑待执行；当前smoke等待双卡资源（约4GB空闲/92°C），尚无GPU训练或本轮科学结果。沿用原8小时单轮起点，不重置预算；纯资源排队按原规则排除。远端按冻结条件继续，本地不持续监控；后续应用户请求检查同Run，完整闭环后才回拉核验、intake、原环境回放与分析。详见 ai4s/programs/dbconformer/research/pat_r1_repair1/REPORT.md。














### 2026-10-06 PAT-R1 repair2 准备









用户授权卡空闲重启补跑，明确新设6小时仅完成PAT-R1。旧repair1 smoke失败已按元数据登记INVALID；两项已通过smoke在原CPU环境重新资格回放PASS，九B0来源保留。准备新不可变repair2：9B0恢复、2smoke恢复、1新P1 smoke与18原任务；模型/训练器/梯度实现字节不变，数据/split/seed/科学门不变。不修改旧ledger、不自动下一轮。新6h使用官方累计限额扩展，原epoch历史保留，不扣除失败停机。43项本地工程测试通过，上传启动前进行Grok只读审查；当前尚未提交新Run。详见ai4s/programs/dbconformer/research/pat_r1_repair2/REPORT.md。














### 2026-10-06 PAT-R1 repair2 正式启动









新Run `2026-10-06_dbconformer_pat_r1_ccmu_repair2-full-w1` 已真实启动：CPU恢复9B0与2smoke PASS，新P1 smoke一次PASS，18正式任务已进入双卡训练（2 running，0 failed），核验时C0/P1分别epoch16/14。43测试、Grok实际外审、101上传文件SHA、51共用代码/配置/数据/split SHA和原环境CPU合成回放通过。model/run_task/stable_gradient相对repair1字节不变。新6h仅完成PAT-R1，登记时剩余约5.54小时；旧失败/合同/ledger保留。现仅启动证据，无完整科学结果。按用户要求正式启动后不持续监控，服务器继续，下次按请求检查同Run完整闭环后回拉核验/回放/分析。详见ai4s/programs/dbconformer/research/pat_r1_repair2/REPORT.md。












### D-188 - MVCNet DISCOVER_NEXT SCMA design (2026-10-06)







根据用户“重新回到 DISCOVER_NEXT，设计下一轮研究”，完成 MVCNet v3.0 设计续接，run_action=DESIGN_ONLY。上一轮 source-class-relation R6 保持 NO_SIGNAL、精确实例关闭，SED 保持禁止救援；原24h campaign、轮数及运行终态不重置。下一候选 SCMA 直接在原有raw 512维分类特征上加入非负的源被试×类别中心距离辅助项，不新增参数、教师、head或forward，原生分类/CE/CVC/CMC/BN/Dropout/推理接口保持。S0原生、P0真实分组、N0源内伪类别、C0类内伪被试；拟fresh seed63/64×9任务，共72训练+72检查，效用P-S≥0.5pp，两个分组控制各≥0.25pp并要求seed/subject/LOO稳定。系数lambda_align=1.0独立于原损失系数。







第一次Grok as-written否决及保护验收未完成均保留；数学修正后真实专项外审ACCEPT_WITH_LIMITS，仅数学和对照，不是新颖性或效力PASS。3600代表性CPU批次只证明分组可用，不替代原生50-step采样器/GPU验收。类条件对齐已有EEG-DG/CCSA等先例，本轮定位为已知机制筛选。新预算建议24h单阶段，尚未登记或授权；当前没有新campaign、训练/远端派发或论文claim。设计、哈希绑定续接及外审原件：ai4s/programs/mvcnet/research/discover_next_20261006/RESEARCH_BRIEF.md；State仅添加discovery_transition，不改变旧运行字段。











### D-189 - 2026-10-06 MVCNet SCMA r1 formal launch







用户在收到SCMA设计后要求启动上传，建立独立24h/单阶段campaign（准备计时、资源排队排除）。新63/64 splits、S0/P0/N0/C0四臂72训练+72封存后检查；全部旧teacher/Q/checkpoint不复用，旧R6/SED精确负边界保持。21本地测试、18实际source-only采样器覆盖、隔离源入口、不可变168-unit合同及96文件依赖/哈希核验通过。共享控制器已真实上传并启动Run `2026-10-06_mvcnet_source_class_mean_alignment_ccmu_r1-full-w1`，远端96文件SHA一致；源环境1/1、覆盖18/18、GPU smoke4/4通过，正式训练进入CCMU双3090共6个worker。完整进程smoke峰值6778MiB，训练承诺7373MiB、每卡共享准入余量512MiB；memory_only不设固定并发上限，单项OOM至多3次任意合格卡重试。科学结果PENDING，未读取中间分数、不发布Claim。正式启动后停止本地持续监控，服务器按冻结合同继续；后续用户检查时同Run收尾回拉/verify/intake/replay/决策。记录：ai4s/programs/mvcnet/research/source_class_mean_alignment/EXECUTION_REPORT.json。













### 2026-10-06 PAT-R1 repair3 附加投影衰减修复与资源排队









用户授权修复补跑，追加新6小时仅完成PAT-R1。repair2已按失败元数据登记INVALID：18项完成100epoch后因附加原始梯度真零失败，selected投影权重约1e-40；没有科学效应结论。合成真实PAT统计复现支持衰减导致塌缩的充分机制，真实训练修复仍待全长度smoke。新训练profile显式仅将C0/P1精确304附加权重的Adam decay设0，核心仍lr.001/decay.0001，两臂对称；网络、初始化、正式训练/数据/选择/严格梯度/科学收益及回放门均保持。九原B0独立合格恢复，两项新source-only100epoch smoke PASS后才执行18项新正式训练，旧失败C0/P1不复用。









Run `2026-10-06_dbconformer_pat_r1_ccmu_repair3-full-w1` 已冻结、登记、上传101文件SHA及原环境CPU包验收通过，本地42测试及原环境4项optimizer回归通过。Grok原过期控制器计划哈希BLOCK保留；局部重绑定AST核验及frozen receipt继承路径回归修复已处置，不声称外审改判。后台执行器已接管，9B0恢复PASS；双卡约20GB占用/100%利用率/92°C，超过90°C准入，smoke WAIT_FOR_RESOURCES，正式训练尚未开始。资源满足后自动继续同Run，纯资源排队不计预算；不改热限、不杀其他进程、不重复提交。停止持续本地监控，后续按请求核验同Run并在完整封口后回拉/SHA/intake/原CPU回放/分析。详见 `ai4s/programs/dbconformer/research/pat_r1_repair3/REPORT.md`；权威状态仍为STATE/EVIDENCE_INDEX。














### D-190 - PAT-R1 repair5 prospective training-integrity repair (2026-10-07)









用户要求修复补跑并新增6小时仅PAT。repair4已按同Run失败元数据INVALID：完整smoke通过，18正式到100epoch后14成功/4技术失败，未读效果。原冻结source诊断显示部分selected附加作用低于数值容差，不能仅修probe来宣称结构有效。前瞻方案保持模型/实际训练/科学门，initial source接通+每个真实optimizer.step的存在/有限性、selectedepoch以前逐组数据梯度和FP32写回、selected相对actualinitial改变作为完整性证据；原末批严格正与selectedfreshAdam更新完整保留诊断，选中路径below-tolerance显式记录。至少一次更新不证明持续功能收益。4项新full-source smoke覆盖原失败，18新formal、9原B0独立恢复；待实现、外审、冻结和执行。State/EvidenceIndex/新合同为权威；本记录不授予后续研究或论文claim。












### D-191 - MVCNet SCMA r1 verified NO_SIGNAL closure (2026-10-07)







72/72训练、72/72检查、4/4 smoke零失败，完整封存包SHA、1072文件manifest、同Run verified intake/global seal和41,472行预测重放通过。P-S −2.073688pp（双seed −2.334105/−1.813272；2/9正向、全部LOO负、CE增加.030333、一人均值−5.295139pp），P-N +.250772pp不稳定，P-C −.781250pp。共享控制器登记NO_SIGNAL、exact_negative_boundary并结束旧Run，COMPLETE_MAX_ROUNDS；不改门/调lambda/分组/归一化或补seed救援，不提升C/N，VCN-P1 scoped anchor保留，claim_release=none。报告：ai4s/programs/mvcnet/research/source_class_mean_alignment/analysis_r1/REPORT.md；证据：AI4S-MVCNET-mvcnet-source-class-mean-alignment-screen-ccmu-r1。







### D-192 - MVCNet DISCOVER_NEXT shared-head update compatibility design (2026-10-07)







用户要求回到DISCOVER_NEXT。候选为已知MLDG(FC)/ANIL式训练机制：同批原raw特征上只虚拟更新共享线性头，真实源Q/S的跨源查询CE辅助原联合训练，推理仍原共享头；不新建教师/私有头/特征分支/BN路由。S0原生，P真实源，N类内伪源保cellcounts，C alpha0额外query CE；alpha.001/beta1、不搜索。原广义Grok triage NONE保留，专项固定材料外审仅数学/对照ACCEPT_WITH_LIMITS；无效用或原创性结论。







9项合成导数检查通过。18,000旧源训练ID代表性批次整体95.9%最低profile覆盖；126 profile×source角色中一项128/143=.8951未达预设.90，记录QUALIFICATION_INCOMPLETE_ROLE_UNIT，不降门、改采样或扩采样救援。未来正式同源新split/sampler严格资格仍待闭合，当前不适用直接启动72训练+72检查。State仅保存设计续接，旧状态、budget/round/campaign/暂停保持，不创建新campaign/预算/Run。设计：ai4s/programs/mvcnet/research/discover_next_20261007/RESEARCH_BRIEF.md。









### D-193 - SDC-v0.1 source-conditioned ICP design (2026-10-08)





用户要求关闭TRA精确路线并转向新结构机制。TRA-C01 repair2保持NO_REPLICATION_SUPPORT：I +1.631944pp、TPC匹配收益−0.486111pp、双seed交互均正2/5；已完整20fit/40view回传分析。精确per-C BPC/TPC×source/trial双向co-adaptation路线停止，不补seed、调门、挑被试或以单侧收益重包装。旧Run/campaign/22h预算/科研裁决保持终态；不扩大为所有normalization无效的结论。





选择SDC-v0.1：仅改变训练期ICP样本—中心连接；B0每类单中心、C0类内固定伪来源7中心、P1真实来源7中心。原生编码器/BN/MVP/共享ISP推理保留，C0/P1容量同为额外25,728参数。Huber归约及Norm组均值不变，复制初始中心；主判别P1−C0与P1−B0。来源可解码不是nuisance证明，不恢复SNPD正交化或DRPG暂停child；已知域/类原型机制不构成原创性主张。





合成数学与真实参考前向检查通过，零EEG训练/目标读取。Grok独立只读外审原裁决ACCEPT_WITH_LIMITS；来源代码到中心索引的缺口及1072维数学覆盖已本地修复检查，原报告保留且未声称外审重新改判；实际分组封存与完整训练资格仍待闭合。 拟三已暴露开发被试S02/S05/S08×seed3/4×三臂18新fit，固定100+30、三technical epoch；新预算提议7taskGPUh/Transaction7.5h/campaign9.5h、单轮非独占，尚未授权/冻结/上传。当前仅DISCOVER_NEXT设计登记，实际来源映射、完整训练入口/分析器/Bundle及真实GPU门仍待闭合。权威：ai4s/programs/sstdpn/research/sdc-r01-v0.1/research_brief.md、RESEARCH.json及State/Evidence Index；收口记录TRA_ROUTE_CLOSEOUT_20261008.md。








### D-194 - PAT-R1 repair5 verified negative closure (2026-10-08)





Same Run `2026-10-07_dbconformer_pat_r1_ccmu_repair5-full-w1` completed 9 qualified B0 recoveries, 4 full source-only smokes and 18 fresh formal fits. Exact manifest/intake and original-environment replay verified; 15,552 target predictions have zero argmax discrepancies. B0/C0/P1 mean ACC = 57.6196/56.5779/56.6165%; P1-B0 = -1.0031pp, P1-C0 = +0.0386pp, both fail every frozen increment subgate. Close this exact PAT instance; no result-driven rescue, next-round launch or paper claim. Eleven of 18 extra paths are below frozen tolerance on fixed source inputs, not evidence of global inactivity. Preserve old INVALID runs. Analysis recovery explicitly discloses two typed/scope corrections and original-GPU source-functional check; target/source-validation replay remains CPU, tolerances unchanged, 12 regressions and actual Grok COMPLETE/PASS. Authority: `ai4s/programs/dbconformer/research/dbconformer-pat-r1-repair5_decision.yaml`, `EVIDENCE_INDEX.yaml`, and `pat_r1_repair5/REPORT.md` / `ANALYSIS_RECOVERY_ACCEPTANCE.json`.





### D-195 - MVCNet source head meta r2 authorized launch (2026-10-08)





用户授权累计30小时实际工作、最多1科学阶段及CCMU双卡完整执行，纯资源排队不计时。真实默认sampler在本地与CCMU分别完成18 profiles×20×50资格，最小profile .972、最小profile/source .951049；不修改采样器或降低门。20项候选本地测试通过；可选共享控制器回归停滞后仅停止自身本地测试，未记PASS。实际Grok只读快照复核ACCEPT_WITH_LIMITS，原首次保护检查失败及并行文档变化保留；已知MLDG(FC)/ANIL式机制不作原创性或效用主张。





r1仅本地打包依赖闭包失败，原合同保留，无Run/GPU；r2包含原共享reservation helper，科学矩阵不变。Run 2026-10-08_mvcnet_source_head_meta_ccmu_r2-full-w1 已上传并REMOTE_ACCEPTED。18服务器资格及4/4 GPU smoke通过，峰值6778MiB，训练commitment7373MiB+512MiB余量。启动快照72训练中6运行、66待调度、0失败，GPU0/1各3任务；72检查须等待全训练seal。epoch20真实批次哈希门仍由正式训练执行；目前无科学结果。权威：State、冻结r2合同及source_head_meta/EXECUTION_STATUS.json。





### D-196 - DBConformer LRC-R1 DISCOVER_NEXT (2026-10-08)





用户要求回到DISCOVER_NEXT、设计下一轮。PAT repair5的有效负边界及LTA/RCC精确关闭保持；U0独立候选继续撤下。选择LRC-R1设计：空间Conv/ELU后、全局汇聚前，对8窗22电极特征计算共享局部关系A与内容V；P1为mean(AV)，C0为mean(A)mean(V)，原global token保留并加残差，原22token/Transformer/pool/concat80不变。C0/P1同1024附加参数，控制保留边际量、去掉特定配对；不检验时间箭头或生理因果。





11项CPU合成代数检查通过，Grok实际独立只读外审COMPLETE/ACCEPT_WITH_LIMITS；方法原创性LOW，DyST-GT已是直接近邻，完整方法/代码等价核验及真实runtime/full-source/GPU资格待补。拟三臂×9已暴露被试×seed0共27fresh100epoch+3source-only全寿命smoke，双必要对照均需mean≥.5pp、正≥6/9、worst≥−3pp、所有LOO>0，固定源selected配对作用另报。仅设计登记，旧COMPLETE_MAX_ROUNDS/暂停/campaign/预算/历史round evidence保留，无新Run、预算或启动授权，不发布claim。权威：ai4s/programs/dbconformer/research/discover_next_20261008/RESEARCH_BRIEF.md、DESIGN_TRANSITION.json及State.discovery_transition。






### SDC-v0.1 execution launch (2026-10-08)



用户明确要求上传启动，已授权并冻结新SDC单轮：B0/C0/P1×S02/S05/S08×seed3/4，共18科学fit与3来源技术epoch；7 task-GPUh、Transaction7.5h、campaign9.5h。合同ee44579c6f69139b2f4ef043af284add67d8e8a35494fc18ae4f454eeea1b472，Run 2026-10-08_sstdpn_sdc_r01_v0_1-full-w1。Lab10直连已上传及核验remote ledger，技术节点正在非独占容量排队；未开始科学训练，无新科学证据。旧TRA精确路线及22h历史预算保持关闭。



权威运行状态：ai4s/programs/sstdpn/research/STATE.yaml；执行快照：ai4s/programs/sstdpn/research/sdc-r01-v0.1/execution/EXECUTION_STATUS.json。





### SDC repair1 queue-clock fix (2026-10-08)



原SDC Run技术节点有效计时1000秒超时，B0来源技术epoch约29秒完成，C0/P1未派发、科学0/18；精确失败元数据已登记INVALID，无科学负结果。用户授权修复补跑。缺陷为无running任务时GPU资源扫描缺排队心跳；新runtime仅在空闲扫描期保活，提交worker前stop/join，保持5秒陈旧保护。原包/旧计时账本保留。repair1模型/训练/组映射字节及科学字段与原合同一致。



权威：ai4s/programs/sstdpn/research/STATE.yaml；repair1/execution/PREPARATION_STATUS.json。







### D-197 - MVCNet head-meta r4 engineering recovery (2026-10-08)





用户授权中断则修复补跑，保持30h累计单阶段。原r2的72/72训练成功，不重训。r2封存器把配置alpha和有效alpha混用；r3分离该字段后，检查入口因封存摘要遗漏operative/finite/shape/identity而72项技术失败，零EEG检查读取/零预测。原合同、回执、checkpoint与失败尝试保留；r4新不可变身份只补充实际验证过的摘要字段。





真实入口红绿回归、72完整验证及成对全局闭集、源596项哈希及R2训练原件lineage、科学合同不变和累计预算验收通过。Run 2026-10-08_mvcnet_source_head_meta_ccmu_r4-full-w1 已REMOTE_ACCEPTED：72/72检查成功、0失败，双卡空闲。168 task_evidence齐全，CPU仍核验约261MiB回执，最终artifact manifest尚未发布；未回拉intake或读取科学成绩，不作效用/原创性判断。权威为State、冻结r4合同、source_head_meta/recovery_r4/RECOVERY_REPORT.json和EXECUTION_STATUS.json。






### D-198 - LRC-R1 platform selection: Lab10 (2026-10-08)



用户要求改回Lab10实验，登记LRC-R1计划executor=lab10、校外经lab-codex-via-ccmu跳板，同一Lab10根/Python。只读连通核验成功，PyTorch1.13.1+cu116、10张2080Ti可见，当前有负载；不是候选GPU资格。科学结构、矩阵、门不变。按用户既有共卡/无额外预留偏好，候选计划allow_same_owner=true/memory_only/max_jobs=null/reserve0，任务峰值/预留/90°C/归属与OOM保护仍保留，不修改Program1024MiB默认或旧冻结合同。State.discovery_transition.executor_plan及Evidence Index已引用平台变更；旧campaign/budget/Run终态保持，无新预算、上传或启动。实际Lab10候选资格和新合同仍待闭合。计划：ai4s/programs/dbconformer/research/discover_next_20261008/LAB10_PLAN.md。





### D-199 - MVCNet shared-head meta verified closure (2026-10-08)



同一r4 Run完成标准回拉/哈希/intake与72检查、41,472行预测冻结复算。P0-S0=-0.318287pp（3/9正，seed -0.790895/+0.154321）；P0-N0=+0.038580pp（4/9正，跨seed反向）；P0-C0=-0.829475pp（两seed负）。三个冻结门均失败，正式NO_SIGNAL，State COMPLETE_MAX_ROUNDS；关闭alpha=.001,beta=1,head-only exact实例，不救援、不补seed、不升C0/N0。VCN-P1保留，无B0不扩大归因。七源developmental范围不等同八源LOSO或独立确认。



原训练不重跑；运输tar、CSafeLoader等价适配及分析输出缺失单位/Run/配对字段的接口修复均留回执，原分析保留且冻结预测/classify重算完全一致。报告：ai4s/programs/mvcnet/research/source_head_meta/analysis_r4/REPORT.md；后续处置PRECISE_CLOSURE.json，Evidence Index exact_instance_closed_no_rescue。不自动开下一阶段。



### SDC repair2 path repair and launch (2026-10-08)

用户授权修复补跑。repair1入口残留旧round路径导致3技术任务训练前失败，已按精确元数据登记INVALID，科学0/18。repair2仅从冻结合同解析组映射与资格文件，并加载runner同级training.py；模型、训练、分组字节与科学矩阵不变。隔离新包实际任务入口红/绿复现通过，远端原包同入口验收通过且fit未调用。新Run 2026-10-08_sstdpn_sdc_r01_v0_1_repair2-full-w1 已上传并实际启动；同campaign25小时保留原起点和成本，非独占memory_only/一次attempt。启动核验技术1/3完成、2运行、0失败（后续以State/远端回执为准）；技术门通过自动进入18科学fit，无新科学结论。

权威：ai4s/programs/sstdpn/research/STATE.yaml；sdc-r01-v0.1-repair2/execution/EXECUTION_STATUS.json。


### D-200 - AI4S v3.1 五 Program 新工作链启用 (2026-10-08)

用户明确授权启用 v3.1 并为每个 Program 更新接入。MVCNet、DSAINet、OTA、DBConformer、SST-DPN 的新工作默认链均为 L1/L2/L3 v3.1，Program 期望链与唯一索引一致。既有 v2/v2.1/v3.0 精确绑定及策略保留；旧 campaign、Run、operation 与冻结续接沿原规则，暂停、预算、执行权限和科学配置不因迁移改变。共享离线回归170项、迁移兼容26项通过；五 Program 实际只读入口及重复激活检查见接入报告。此项仅为提示词与接入治理更新，不新增实验或论文 Claim。权威入口：ai4s/PROMPT_INDEX.yaml；验收：ai4s/_work/prompt_v31_activation_20261008/REPORT.md。




## D-201 DBConformer LRC-R1 Lab10启动核验（2026-10-08）



用户授权8小时仅一轮，近邻全文与实现审查完成；唯一Run `2026-10-08_dbconformer_lrc_r1_lab10_r1-full-w1` 已启动。最后远端快照21:49：源训练验收1完成、2运行、0失败，科学27任务待完整源训练/冻结耗时资格，不是效果结论。LRC仅低创新度探索；原v3.0冻结链收尾，后续新研究采用v3.1，不持续监控。合同88e621c6…，详见 `ai4s/programs/dbconformer/research/lrc_r1/START_REPORT.md`。





### D-202 - AI4S v3.1 原位优化（2026-10-08）



用户明确要求直接更新现有v3.1，不新建小版本。L1/L2及五Program L3已补齐分用途判据、未来规则校准、初筛证据充分性和经验采用接口；版本、父绑定、chain_id保持。既有冻结实验按原合同及当时规则，实际执行数值仍由唯一冻结配置管理。五链兼容与五guard通过；Grok为ACCEPT_WITH_LIMITS、无阻断，两项非阻断表达已本地澄清。无新增实验授权或科学结论。原文、差异及验收：ai4s/_work/prompt_v31_inplace_20261008/REPORT.md。



### D-203 - MVCNet v3.1 design-only augmentation readout continuation (2026-10-09)

用户要求接入最新v3.1并继续MVCNet研究。唯一索引/Program/父绑定一致、guard通过、激活预览ALREADY_ACTIVE；旧head-meta campaign保持v3.0及COMPLETE_MAX_ROUNDS，无活动Run/operation，不继承剩余30h。SED/class-Q/SCMA/head-meta四项verified开发证据保留原NO_SIGNAL与精确关闭。旧discover_next_20261007设计已消费并关闭，存入discovery_history，禁止作为现行待执行候选；SCMA Evidence Index仅补齐既有REPORT的精确关闭指针。

新DESIGN_ONLY问题：保留VCN-P1四视图BN/CVC/CMC与原CR标签语义，把增强CE迁到训练期读出，推理仍raw单头。四臂S0共享、N0 raw/增强池分开、P0真实增强三头、C0同容量trial-wise混合三头；不是被试rank1残差、虚拟跨源更新或MLEV对称JS。13项合成CPU路由检查通过，不代表实际pipeline/GPU或效用。grok-4.6-build独立只读裁决ACCEPT_WITH_LIMITS，仅DESIGN准备；P−C包含CR标签约定、不能纯归因特征分工或梯度冲突，N非容量匹配。原trace、输入hash和处置完整保留，补核MLEV/mask来源未冒充外审。

新门/两随机重复×9subject×四臂/100epoch与30h仅草案，尚未分配seed/split、冻结配置或获准新执行；不启动、不调旧门、不放大Claim。权威：ai4s/programs/mvcnet/research/STATE.yaml及EVIDENCE_INDEX.yaml；设计与审查：ai4s/programs/mvcnet/research/discover_next_20261009/RESEARCH_BRIEF.md、REVIEW_DISPOSITION.json；新Run=0，新campaign=0。


### D-204 - SFP-v0.1 electrode-filter factorization design (2026-10-09)

用户要求接入最新v3.1并继续SST-DPN研究；只读入口确认sstdpn-transaction-v3.1已生效，guard通过，重复激活返回ALREADY_ACTIVE。旧SDC repair2已完整verified intake，18/18科学fit与18预测view，NO_SIGNAL保持；精确来源分组ICP不救援，旧v3.0 campaign仍COMPLETE_MAX_ROUNDS/paused，无活动Run/operation。

选择SFP-v0.1做DISCOVER_NEXT/DESIGN_ONLY：将SSA后198→48任意投影改为每输出电极×共享滤波器矩阵rank2，保留BN/ELU/MVP1072维与双原型。真实源码列号为filter*22+electrode；实际参考forward检查发现并修正初版轴顺序错误，旧合成回执/审查原文保留。B0/P/C/D分别是原生、真实轴因子化、固定混轴置乱因子化、展平rank12；只限缩解释适配包效用/轴条件增量，近似容量控制、初始化和因子衰减差异披露，不承诺计算加速或原创机制。

CPU合成算子19项检查通过，不是完整模型/GPU/效能验收。Grok原始裁决及逐项处置见REVIEW_DISPOSITION.json（当前原裁决ACCEPT_WITH_LIMITS）。未来效用、风险、轴归因门分开，严格全seed符号门改为描述仍待明确确认；不追改旧门。拟议四臂×三开发被试×双seed=24新科学fit、4技术epoch，单轮12小时仅预算提案。生产集成、实际DATA/SPLIT、封存与有限执行scope尚未完成；无新campaign/Run、上传或论文Claim。权威：ai4s/programs/sstdpn/research/sfp-v0.1/research_brief.md、DESIGN_CONFIG.json、RESEARCH.json；运行与证据仍分别以State/Evidence Index为准。



### SFP-v0.1 Lab10 execution authorization (2026-10-09)

用户明确确认“确认在lab10上继续实验”，据此授权新 SFP 单轮12h campaign，Transaction10h，B0/P/C/D × S02/S05/S08 × seeds3/4，24科学fit及4源域技术epoch，单次task尝试、无自动修复/救援。采用已交付简报中分开的效用(P-B0均值≥1pp)、风险(每subject平均≥-3pp)、轴归因(P-C均值≥1pp)判据；归因单列，严格逐seed全正只描述。该前瞻门不追改旧SDC。生产资格通过后冻结、上传、启动、probe与same-Run回传分析均属于该授权。新链v3.1，旧SDC v3.0 NO_SIGNAL关闭保留，累计记录不清空。权威授权为ai4s/programs/sstdpn/research/sfp-v0.1/EXECUTION_AUTHORIZATION.md/json；运行及证据仍以STATE/EVIDENCE_INDEX为准。


### D-205 - MVCNet augmentation readout Lab10 r1 execution (2026-10-09)

- Authorization: user replied “在lab10上运行” to four-arm, 30-hour, one-stage proposal. New v3.1 campaign `mvcnet-augmentation-readout-lab10-20261009-r1`; old v3.0 campaign and exact negative closures remain historical.
- Frozen Run: `2026-10-09_mvcnet_augmentation_readout_lab10_r1-full-w1`; contract SHA256 `54a8aa30ecfbc12442b989095b2a4d9bdda8c6f0dd77e6c6ebd53a4380e2714d`; Bundle source manifest SHA256 `74b07163dade1f50ac27fe5f6fdd2a0217b623c5d34f8b6f6cdb31677f718504`. Lab10 `[REDACTED_MACHINE]`, torch1.13.1+cu116, GPU0–9; capacity/memory_only/null job cap, reserve1024MiB, 90C, one task attempt, increase_only.
- S0/N0/P0/C0 × fresh seeds67/68 × 9outer: 72 fits, global72-student seal, 72 checks; source_import1 + smoke4 + fits72 + seal1 + checks72 = 150 units. 100×50/batch64, native four-view CE/CVC/CMC/BN/augmentation unchanged. P−S only utility gate; P−N/P−C descriptive; developmental selection-used screen, no claims.
- Local qualification: actual native CPU synthetic training/checkpoint/gradient tests; contract/runtime MODULE_SPEC fixed, all18 C0 maps unchanged; actual local source metadata entrypoint verified. Initial Grok review incomplete; follow-up `grok-4.6-build` session01a11f75-2bc7-7160-8355-aa655a504c7e REJECT preserved. Its C0 scatter autograd/empty-bucket objection was disproven with frozen module on target torch1.13.1 CPU (B64/B1 IndexPutBackward0, all3 heads finite nonzero gradients, all rows match). Main technical acceptance only; no external full-audit PASS claimed. Detailed disposition in augmentation_readout/IMPLEMENTATION_REVIEW_DISPOSITION.json.
- Remote launch verified by same-Run probe: source_import=PASS; smoke=RUNNING, four smoke tasks waiting for capacity, zero GPU jobs/failures at observation. 145 dependent units pending. Pure queue wait excluded from 30h campaign and26h Transaction; source_import/smoke must PASS before fits; no intermediate effect reading. Current status authority remains STATE and remote ledger; snapshot is not scientific evidence.


### SFP-v0.1 Lab10 first Run INVALID (2026-10-09)

精确Run 2026-10-09_sstdpn_sfp_r01_v0_1-full-w1 已实际启动后因 epoch_row_order.json / epoch_order.json 接口不一致失败。技术任务0/4完成、4失败，science未启动0/24，目标回执0。正式metadata-only登记INVALID，非科学NO_SIGNAL。原冻结合同单次尝试、automatic_repairs=0；准备science-identical修复候选不扩权，repair1冻结上传启动需明确一次修复授权，并保留失败成本在原12h campaign内核算。权威记录ai4s/programs/sstdpn/research/sfp-r01-v0.1_decision.yaml及STATE/EVIDENCE_INDEX。


### SFP-v0.1 repair1 approved and submitted on Lab10 (2026-10-09)

用户明确“批准”一次repair1。原INVALID现场及成本保留；科学矩阵与生产训练不改；原12h campaign/10h Transaction，28任务，每task一次，无后续自动修复。修复产物接口与不可变身份，未mock共享控制器资格/合成E2E通过，有界Grok纠正复审ACCEPT_WITH_LIMITS（首次复审max-turns incomplete保留）。新冻结合同SHA dfa95b6c537742f693f49369cb087c4d9d511a399529016a516f1b6c9ce1a521；精确Run 2026-10-09_sstdpn_sfp_r01_v0_1_repair1-full-w1 已上传提交且远端身份匹配，初始snapshot四技术任务capacity waiting，science未启动。权威状态STATE及sfp-v0.1-repair1/execution/CURRENT_STATUS.json。


### SFP repair1 checked terminal INVALID (2026-10-09)

用户要求检查状态。精确Run 2026-10-09_sstdpn_sfp_r01_v0_1_repair1-full-w1：技术task4/4完成、0失败，但节点汇总读取不存在的training_metadata.optimizer_steps，将实际epoch_metrics.optimizer_steps=202误记fit_steps=0，technical节点FAILED。科学0/24、目标回执0。已按metadata-only正式登记INVALID并暂停，不自动修复/重跑。原预算不重置；20:10检查时campaign剩约7.235h，低于新10h完整Transaction需求；如后续修复需明确执行授权和足够预算，保留原失败成本。权威STATE/EVIDENCE_INDEX及sfp-r01-v0.1-repair1_decision.yaml。


### SFP repair2 tested staged awaiting campaign time extension (2026-10-09)

用户要求“修复补跑”。repair2已修复技术节点优化步数聚合：严格取epoch_metrics.optimizer_steps，检查actual=2×batch steps、examples=source rows及副本一致，异常拒绝。完整四臂CPU合成technical_epoch→run_task→run_node→publisher→emit_node_result→technical_pass通过，12类负例拒绝；支持性只读复核发现并关闭重复键/同源交叉缺口。明确工程修复依EXTERNAL_REVIEW规则以本地回归验收，不伪造新的Grok PASS。训练/model/融合/科学分析不变，旧35/40项冻结源码闭合仍匹配。原campaign目前约剩7.057h不足10h Transaction，拟请求12h→16h（+4h）预算延期以容纳Transaction及处理余量，尚未批准；新合同仅candidate，未冻结/上传/派发。权威STATE的research_preparation及repair2/execution/PREPARATION_STATUS.json。


### SFP repair2 qualified1 Lab10 technical gate PASS (2026-10-09)

用户已明确批准同一campaign总预算12h→16h(+4h)及一次repair2 Lab10启动，原开始时间/两Run INVALID/累计成本保留；Transaction10h、原四臂24fit+4源域技术epoch，每task一次，零未来自动修复。原repair2未上传候选因并行验收写入导致freeze后sourceclosure不匹配被拦截，保存PRELAUNCH_CLOSURE_REJECTION；停止并行写入，以同次授权稳定独立资格包冻结新精确Run 2026-10-09_sstdpn_sfp_r01_v0_1_repair2_qualified1-full-w1，合同SHA47bf6b8862248520e5546e5b90ba0e539123fd9bc12209aa9fbe43cdd073fd24、30项源码闭合，正式授权登记/打包/上传启动及远端身份匹配。真实四臂技术task4/4完成、0失败，节点门PASS、808 optimizer updates、峰值1445MiB、checkpoint_reload=true、未评估target。科学节点已进入RUNNING；最新权威计数在CURRENT_STATUS.json，科学效果未评估/未intake，不支持claim。

#### D-205 工程显存修复状态更新（2026-10-09 20:57:01 +08:00）

- 原Run同一合同和114文件manifest重验不变；四项smoke通过，正式train零attempt。S0旧峰值导致统一准入11798MiB超过11264MiB；另核对canonical观测后上调规则。
- 用户明确授权“诊断并进行工程修复”。保存现场、仅停止精确零attempt调度器，transaction自然FAILED；标准failure metadata intake登记INVALID，非科学NO_SIGNAL。没有读科学效果或重启科学Run。
- saved_tensors_cpu只改保存位置；独立CPU checkpoint；按臂实际booking取max(initial/1.05测量/canonical1.1测量)，加原1024reserve并做物理容量fail-closed。批次、FP32、四view loss、BN、RNG、checkpoint选择、数据边界、矩阵和campaign预算不改。
- 7 runtime+4 contract回归PASS；目标torch1.13.1完整B64 CPU合成fit差分、四臂B8 CUDA两Adam步loss/grad/state/RNG exact PASS。Grok delta session01a120b1-d882-7db2-b0d9-597e4fa715d5 PASS_WITH_LIMITS/WARN原样保留，实际booking警告由主agent回归修正。
- QA1的四个B64 OOM（过低2048MiB技术预估）保留。QA2只提高技术预留到6144+1024，四项B64 synthetic技术检查等待容量；整体工程GPU验收尚未通过、新包尚未冻结、原72train未补跑。修复报告和收口入口：ai4s/programs/mvcnet/research/augmentation_readout/repair_memory_r1/DIAGNOSIS.md、ENGINEERING_STATUS.json、collect_qualification.py、REVIEW_DISPOSITION.json。

## 2026-10-09 v3.1 技术验收闭环提示词修订

用户要求直接修订现有v3.1。共享L2明确最终包产物至回执/消费者/汇总器的最小工程闭环，补检查器反例、具体根因报告和资源可行性；执行与接入说明引用同一规则。五活动链兼容检查通过；旧冻结门、授权及科学配置不变，不启动补跑。修改前快照和本次验收：ai4s/_work/prompt_v31_technical_20261009/REPORT.md。


### 2026-10-10 Zhou2016 frozen-P0 local supplement preparation

User requested unchanged P0 on the completed Zhou2016 local baseline protocol. Prepared 5 seeds x4 LOSO, 20 new P0 fits at100 epochs, reuse20 B0; proposed1 single-epoch technical fit, GPU0/two workers,2h cap,0 automatic retries. CPU synthetic model identity/forward/backward and zero-training interface/split checks passed. Actual GPU fit/full training not started; execution-scope confirmation pending. Prior001/004/PhysioNet results and old campaign closure unchanged. No new performance or mechanism Claim. Authoritative preparation: ai4s/programs/dsainet/research/dsa-pfc-zhou-v0.1/RESEARCH_PLAN.md and PREPARATION_STATUS.json.


### 2026-10-10 Zhou2016 P0 local supplement started

User confirmed the prepared scope. Experiment2026-10-10_dsainet_p0_zhou2016_loso_local_w2 launched (PID7920); single-epoch GPU technical artifact/gradient/update/replay gate passed. Formal20 fits:0 completed,2 running with18 epochs observed each,18 pending,0 failed at launch verification. Reuse20 B0, GPU0/two workers,2h cap,0 automatic retries; automatic fixed archive/replay/analysis after complete. Prior remote campaign and conclusions unchanged; no new scientific effect judgement. See ai4s/programs/dsainet/research/dsa-pfc-zhou-v0.1/START_REPORT.json and output/local/2026-10-10_dsainet_p0_zhou2016_loso_local_w2/STATUS.json.


### SFP repair2 INVALID and repair3 budget-gated preparation (2026-10-10)

repair2-qualified1精确Run的技术4/4 PASS、科学10完成/14失败，12×1200秒超时、2×cuDNN无可用算法，正式目标回执0；19原始日志/元数据SHA核验通过，按共享控制器登记工程INVALID，部分科学产物不可复用，不作NO_SIGNAL。用户明确“修复补跑”；新repair3落实已冻结cpu_threads=1到Python之前的节点环境、预封和真实worker，receipt存实际观测；fixed_count每卡1个登记任务，原1024余量/90度/同账号政策保留，未登记外部竞争和cuDNN根因仍未知。模型、训练、设计、分析6个源文件逐字节不变，原4臂24fit+4源域技术epoch、1200秒/100+30epoch/1attempt保留。CPU合成四臂闭环、真实execv观测交接、独立包资格和6分析/5边界反例通过，实际GPU门未运行。Grok原WARN保留，显式预算字段绑定增补本地回归。原同campaign16h开始时间及失败成本保留；剩余约7.56h<10hTransaction，未冻结/上传/启动。具体待批准16→20h(+4h)及一次Lab10 repair3；权威记录ai4s/programs/sstdpn/research/sfp-v0.1-repair3/execution/PREPARATION_STATUS.json。


### SFP repair3 actual Lab10 gate blocked by missing B0 telemetry (2026-10-10)

用户明确批准同campaign16→20h(+4h)和一次Lab10 repair3；正式延期保留原开始时间/所有失败成本。新合同f6f2b44361cf4d206b260230d0c11440d22814ee4b713cfbafc3df65827fbad8、30source绑定、预算准入11.42h≥10h、延期后资格包/6分析回归通过，精确Run 2026-10-10_sstdpn_sfp_r01_v0_1_repair3-full-w1已上传启动。真实源域4/4 task exit0、每臂202 optimizer updates、实测torch intra/inter-op及四env均1。B0调度peak_memory_mib=0/full_process_memory=false，其他3臂完整显存观测1443–1445MiB；共享technical_pass在full_process_memory拒绝，技术节点FAILED，scientific0/24未启动、target receipt0。原始5文件SHA核验并按控制器登记INVALID，部分产物不复用；真正采样遗漏根因尚未确定，不补写PASS、不改变科学配置、不继续自动修复。权威CURRENT_STATUS.json及sfp-r01-v0.1-repair3_decision.yaml。


### 2026-10-10 Zhou2016 P0 local supplement closure

Experiment2026-10-10_dsainet_p0_zhou2016_loso_local_w2:20/20 formal100epoch fits,1/1 technical fit,0 failed/pending/running; completion2026-10-10 00:53+08.40 B0/P0 checkpoints replayed with exact original prediction match. Final380-file manifest verified; original pre-terminal manifest preserved and only STATUS/launcher.stdout entries resealed (post-seal ordinary writes),378 files unchanged; no new fits or forward. B0 ACC75.442250%/NLL1.009456, P0 ACC75.186550%/NLL1.129542: ACC-.255701pp and NLL improvement-.120085nats,1/6 frozen gates. Close exact supplement with NO_STABLE_PERFORMANCE_SUPPORT, preserve baseline WARN and prior dataset conclusions; no automatic rescue or formal Claim release. Authority: ai4s/programs/dsainet/research/dsa-pfc-zhou-v0.1/CLOSURE_VERIFICATION.json; report results/archives/mieeg-zhou2016-loso-v1/dsainet-p0/RESULT_ANALYSIS.md.


### SFP repair4 driver telemetry recovery launched (2026-10-10)

用户“修复并重跑”授权一次 repair4。历史 repair3 仍 INVALID，B0 驱动观测缺失的具体历史根因未知。新修复隔离到专属采样器，通过异常日志、真实正显存原子 ack 和退出前最多15秒等待保持原技术门；共享冻结采样器已恢复原哈希，旧合同、失败成本、20小时累计预算和24科学fit+4技术epoch均保留。

Run `2026-10-10_sstdpn_sfp_r01_v0_1_repair4-full-w1` 已在 Lab10 启动。当前技术0/4完成、4等待容量，科学0/24启动；所有GPU暂不满足2048MiB任务承诺+1024MiB公共余量。排队按原规则不计执行预算。14项专属采样器测试、最终封装入口及观测反例检查通过；真实GPU验收待技术节点，不能作科学结论。当前权威状态见 `ai4s/programs/sstdpn/research/sfp-v0.1-repair4/execution/CURRENT_STATUS.json`。


### 2026-10-10 P0：关闭广泛优效主张，保留候选创新点（用户决定）

保留原样 P0（DSA-AEL-P0-FROZEN-20260927）作为历史性能候选、结构设计经验和候选创新点；关闭其广泛跨数据稳定优效主张。001正信号及004/PhysioNet/Zhou2016各自原判定和范围限制均保留，不能以候选保留代替创新验证。论文可将非对称统计编码双分支作为候选设计，尚不能声称Coarse特异性、A/E互补、删除inter独立收益、主创新已成立或通用稳定优势。已有Claim Ledger pending条目原样保留，此处是用户研究/写作处置，不冒充外审no。没有新增训练或诊断授权。权威取舍：[P0_CANDIDATE_RETENTION_20261010.md](ai4s/programs/dsainet/research/P0_CANDIDATE_RETENTION_20261010.md)；Program State/Evidence Index已同步。


### SFP repair5 replaces queued repair4 before any fit (2026-10-10)

repair4发现动态驱动采样日志会在worker产物清单生成后变化，已在technical=0complete/0running/4pending、科学0fit时终止调度器并按真实FAILED ledger登记INVALID。所有历史成本和原始元数据保留；该Run没有GPU技术验收或科学结果。

同一本轮用户“修复并重跑”指令下，repair5将调度器动态日志交由整Run最终清单封存，worker科学产物清单保持稳定。原intake验证的边界回归通过：日志变化不影响封存产物，封存产物损坏仍拒绝。旧共享采样器及历史所有合同源哈希保持；四臂24fit+4技术epoch、训练、数据、seed、阈值与20小时累计预算均未改变。

唯一活动Run为 `2026-10-10_sstdpn_sfp_r01_v0_1_repair5-full-w1`，合同SHA `bff325b338ad2af14ea5f724a1cbded3247d32595731f360f81e5fcf6662428e`，35源绑定已核验，Lab10已确认启动。2026-10-10 01:29技术4等待容量、0运行/完成/失败，科学0/24启动；各GPU暂不满足2048MiB承诺+1024MiB公共余量，排队按原规则排除，准入时预算剩10.669小时。真实GPU验收待原技术门，具体repair3历史漏采原因仍未知；无新增科学结论。状态与monitor：`ai4s/programs/sstdpn/research/sfp-v0.1-repair5/execution/CURRENT_STATUS.json`、`MONITOR.ps1`。


### SFP repair5 exact-Run technical timeout confirmed (2026-10-10)

2026-10-10检查确认Run `2026-10-10_sstdpn_sfp_r01_v0_1_repair5-full-w1` 于北京时间02:09:09技术节点超时FAILED。B0/P/C三个任务均exit124（各300秒任务期限）；D在旧调度快照仍running，但其两个PID现均不存在，且没有终态任务回执，登记为节点超时中断而非完成。技术0/4完成、当前0运行，科学0/24启动，目标回执0。

事务累计wall2405.745秒，其中资源排队1152.322秒排除，执行1253.424秒；技术节点1250秒上限触发。遥测中P/C/D取得真实正显存记录，B0无正观测，并出现ps/nvidia-smi 5秒查询超时；性能根因仍未确定，不判作OOM或科学负结果。4个原始失败控制/日志文件经SHA验证并官方登记INVALID，Program暂停、active_run清空，未重跑。原20小时累计预算保持，截至09:38控制器计算余2.817小时，不足以准入原10小时完整Transaction。权威状态：`ai4s/programs/sstdpn/research/sfp-v0.1-repair5/execution/CURRENT_STATUS.json`。


### SFP repair6 rerun prepared; budget extension pending (2026-10-10)

用户请求补跑后，保留repair5 INVALID终态、全部失败成本和原科学矩阵。Lab10当前实测loadavg约552、CPU PSI some avg10约91%，I/O PSI约0，资源争用明确但不声称唯一历史根因。repair6仅增加派发准入：CPU压力≤20%、load1/逻辑CPU≤2、GPU utilization≤20%，不合格或不可观测时继续资源排队，沿既有排队计时；真实分配前fresh recheck亦覆盖。原单线程、注册并发1、reserve1024MiB、任务300/1200秒期限与四臂24科学fit+4技术epoch不变。

8项准入回归在本地和独立资格封装各通过；CPU合成生产技术门、封装入口、移除guard反例、6个历史冻结合同全部源SHA核验通过。无新增科学数据或Run。当前20小时预算余额约2.7小时，原完整Transaction准入需10小时；提案追加8小时至28，尚未批准，不改State预算、不冻结、不上传或启动。可审阅候选：`ai4s/programs/sstdpn/research/sfp-v0.1-repair6/execution/REPAIR_PLAN.md`及`PREPARATION_STATUS.json`。


### SFP repair6 approved 28h recorded; residual budget still blocks dispatch (2026-10-10)

用户明确批准20→28小时，控制器已于北京时间12:04登记追加8小时，原campaign started_at与所有历史成本未重置。由于前次09:44预算快照到批准间隔超过2小时，原累计clock继续扣除审批等待，批准后实际余额约8.3小时，仍不足原10小时完整Transaction。没有缩短300/1200秒任务期限、裁剪科学矩阵或自动追加额外预算，尚未冻结/上传/启动。另有28→30小时追加2小时提案，尚待用户明确批准。

共享scripts正在其他工作中变动，未回滚共享文件。repair6固定复用repair5已核验冻结bundle共享runtime，36源绑定及独立source_snapshot全部SHA核验，真实CPU合成技术门、资源准入8项回归和snapshot入口通过，防止新合同混入无关实时runtime改动。既有真实Lab10验收仍待新Run技术节点。当前状态见`ai4s/programs/sstdpn/research/sfp-v0.1-repair6/execution/PREPARATION_STATUS.json`。


### SFP repair6 approved34 and started verified (2026-10-10)
用户明确追加4小时，campaign累计30→34小时，保留2026-10-09T07:10:24.886802+00:00原起点与全部失败成本。repair6科学矩阵24fit加4技术epoch、300/1200秒任务期限不变。36项源绑定、CPU合成技术链、8项资源准入检查通过；固定前驱已验证runtime，未采用其他工作中的共享源漂移。精确Run：2026-10-10_sstdpn_sfp_r01_v0_1_repair6-full-w1，合同SHA256：1c2719b92921855d217c22d2ac7a73bd67fa13ff682889cd52f1a1f2fe67269e。已冻结、上传、启动并probe核验；当前WAIT_FOR_RESOURCES，技术0完成/0运行/4容量等待/0失败，科学0完成/24待技术门。CPU压力avg10=28.45及load1/56=2.70超过准入阈值，GPU75–98%利用率；纯资源等待按原策略排除执行预算。无科学intake或claim。权威记录：ai4s/programs/sstdpn/research/STATE.yaml及sfp-v0.1-repair6/execution/CURRENT_STATUS.json。


### SFP new deployment contract repair7 (2026-10-11)
用户明确按新部署合同重部署。旧repair6零attempt、0科学fit已定向停止并验证无存活，原包/合同/账本/日志/成本保留，不记为主机故障或科学负结果。新Run 2026-10-11_sstdpn_sfp_r01_v0_1_repair7-full-w1；合同SHA256 db3ad419b36799bea8bd6d1c24864c57d95e820b8153d3937e00e962bb4946a1。采用lab_permissive_v1、memory_only、0额外余量、允许共卡、GPU利用率只排序、无CPU压力硬门、温度90；未知任务2048MiB需求仍保留。33项源码闭包/新runtime/CPU合成技术链/2项遥测ACK检查与预算准入通过；已上传启动并probe核对新合同。当前4技术任务等显存，24科学任务尚未开始，无科学intake/claim；累计34小时原起点与失败成本保留。详情 ai4s/programs/sstdpn/research/sfp-v0.1-repair7/execution/REDEPLOYMENT_REPORT.md 和CURRENT_STATUS.json。


### SFP repair8 backend remedy prepared; budget blocked (2026-10-11)
用户要求修复补跑。repair7已用SHA核验原失败metadata正式登记INVALID；B0/D任务退出0，P/C在共用temporal conv1d触发cuDNN algorithm error，无显式OOM，0/24科学fit，旧产物不可复用。当前约3.25GiB空闲GPU四臂原路径合成检查均通过，历史错误未复现，根因未确认。repair8只统一四臂时间卷积原生CUDA执行，其余层backend/初始化/参数/FP32 batch32/训练矩阵/判断门/原期限不变；GPU数值和梯度对照通过，前向差9.54e-7、权重梯度差1.55e-6；0优化器步、0科学fit。CPU后端3项、ACK2项、固定包技术链与35项源码绑定通过，完整真实GPU技术epoch未验。当前累计34h，已计28.19h、资源等待核验排除22.594h，剩余5.81h低于原10h Transaction准入。提出追加8h至42h，保留原起点和所有成本，尚未批准；候选未冻结/上传/创建Run。权威准备 ai4s/programs/sstdpn/research/sfp-v0.1-repair8/execution/PREPARATION_STATUS.json 与REPAIR_PLAN.md，无科学claim。


### SFP repair8 approved42 deployed; real GPU technical gate passed (2026-10-11)

用户批准追加8小时，累计预算34→42小时，原campaign起点2026-10-09T07:10:24.886802+00:00和全部已计成本保留。repair8统一四臂时间卷积原生CUDA执行，其余层backend、初始化、参数、数据、24fit科学矩阵、训练设置、判断门和任务期限不变。37项源码与证据绑定已核验、冻结、上传；精确Run：2026-10-11_sstdpn_sfp_r01_v0_1_repair8-full-w1；合同SHA256：0d6d5e6470d8e1bf4e73191b5e12ba6e7a09a62e371296b34024552cdce9d58a。北京时间2026-10-11T18:09:01.909018+08:00核验技术门PASS：4/4真实GPU技术任务完成，0失败；科学任务0完成、4运行、20等待、0失败。累计已计28.373小时、核验排除资源等待22.599小时、剩余13.627小时。没有已完成科学结果或verified scientific intake，不产生科学claim；历史cuDNN错误根因仍未确认。不得自动追加预算或开启下一轮修复。

权威状态：ai4s/programs/sstdpn/research/STATE.yaml；部署与实测快照：ai4s/programs/sstdpn/research/sfp-v0.1-repair8/execution/CURRENT_STATUS.json、REMOTE_ENGINEERING_SNAPSHOT.json、FREEZE_RECEIPT.json、PACKAGE_RECEIPT.json。


### SFP repair9 authorized 18-task reuse and six-task rerun (2026-10-11)

用户明确提高累计预算42→50小时，并批准“仅补6项：批准新恢复合同、核验并复用18项，将任务时限提高至2400秒”。原campaign起点2026-10-09T07:10:24.886802+00:00及全部成本保留。保留repair8失败Run及完整原始产物；18项成功任务324文件已真实拉回校验SHA、checkpoint/预测/参考及源身份；真实产物消费重放18项通过，无新训练；原收据原字节单独保存，派生消费凭证明确来源，不冒充新训练。

repair9科学矩阵仍24项，新增训练仅6项、技术门4项，100+30epoch、batch32 FP32、数据/种子/配对/判据/模型和backend不变。科学任务时限2400秒，300秒技术门、10小时Transaction准入、原9 GPU小时预算及单次attempt保持不变。新同科学恢复接口严格验证18/6分区、原合同/ledger/manifest/授权、真实源资格及预算；不使用将部分产物判无资格的旧metadata-only故障登记路径。6项资格负例、真实24凭证汇总消费闭环与4项消费负例、CPU真实训练技术链、冻结合同与controller入口5项负例通过；这不等于正式科学intake。

精确Run：2026-10-11_sstdpn_sfp_r01_v0_1_repair9-full-w1；合同SHA256：bb59ee9375df3936ec54ae881c28b93b2f43bbfbfbf8bc57c417bac2c71e72f3；50项源码与证据绑定、包完整闭包及上传已核验，已启动Lab10并probe核验。北京时间2026-10-11T23:01:11.758537+08:00，节点状态{'technical': {'status': 'PASS', 'started_at': 1791730776.2050447, 'result_sha256': '3cd46d9f9f44d6ab874fbab2998d17ab229633535cab3aa12b93a9dd026c13e1', 'report': {'target_evaluated': False, 'identity_pass': True, 'operative': True, 'peak_memory_mib': 1393, 'fit_steps': 808, 'full_process_memory': True, 'finite': True, 'shape_pass': True}, 'completed_at': 1791730861.1070182}, 'science': {'status': 'RUNNING', 'started_at': 1791730861.234473}}；新增任务计数{'total': 6, 'completed': None, 'failed': None, 'running': None, 'pending': None, 'observed': False}。当前累计预算50小时，剩余16.763小时；纯资源等待继续按原策略排除。无自动后续修复、额外budget或科学claim。

权威状态：ai4s/programs/sstdpn/research/STATE.yaml；当前实测：ai4s/programs/sstdpn/research/sfp-v0.1-repair9/execution/CURRENT_STATUS.json；完整资格与来源：REUSE_SOURCE_VERIFICATION.json、ACTUAL_SOURCE_CONSUMER_CHECK.json、RECOVERY_REPORT.json、FREEZE_RECEIPT.json、PACKAGE_RECEIPT.json。18复用＋6补跑闭集须在远端全部完成后fetch→verify→intake→分析，才能给出科学判断。


### SFP repair10 authorized 18-task reuse and six-task rerun (2026-10-11)

用户明确提高累计预算42→50小时，并批准“仅补6项：批准新恢复合同、核验并复用18项，将任务时限提高至2400秒”。原campaign起点2026-10-09T07:10:24.886802+00:00及全部成本保留。保留repair8失败Run及完整原始产物；18项成功任务324文件已真实拉回校验SHA、checkpoint/预测/参考及源身份；真实产物消费重放18项通过，无新训练；原收据原字节单独保存，派生消费凭证明确来源，不冒充新训练。

repair10科学矩阵仍24项，新增训练仅6项、技术门4项，100+30epoch、batch32 FP32、数据/种子/配对/判据/模型和backend不变。科学任务时限2400秒，300秒技术门、10小时Transaction准入、原9 GPU小时预算及单次attempt保持不变。新同科学恢复接口严格验证18/6分区、原合同/ledger/manifest/授权、真实源资格及预算；不使用将部分产物判无资格的旧metadata-only故障登记路径。6项资格负例、真实24凭证汇总消费闭环与4项消费负例、CPU真实训练技术链、冻结合同与controller入口5项负例通过；这不等于正式科学intake。

repair9技术门通过，但科学节点在训练前因调度器仍要求完整24项任务而拒绝6项恢复清单；科学任务零attempt，原失败部署及日志保留。repair10在同一已批准范围内修复该准入检查：严格核验完整授权分区、六项清单、源产物和身份，8项调度测试及真实18项源产物准入检查通过。远端六项科学任务是否进入调度，以后续实际回执为准。

精确Run：2026-10-11_sstdpn_sfp_r01_v0_1_repair10-full-w1；合同SHA256：2b99cb8bf94833f6f043b377e77780537bd4501f03097797b21e7d66aced64e9；57项源码与证据绑定、包完整闭包及上传已核验，已启动Lab10并probe核验。北京时间2026-10-11T23:15:11.285139+08:00，节点状态{'technical': {'status': 'RUNNING', 'started_at': 1791731529.749529}}；技术任务计数{'total': 4, 'completed': 0, 'failed': 0, 'running': 0, 'pending': 4, 'attempts_recorded': 0, 'observed': True}；新增科学任务计数{'total': 6, 'completed': 0, 'failed': 0, 'running': 0, 'pending': 6, 'observed': False, 'blocked_by_technical_gate': True}；调度动作WAIT_FOR_RESOURCES，资源等待原因insufficient_reserved_memory。当前累计预算50小时，剩余16.564小时；纯资源等待继续按原策略排除。无自动后续修复、额外budget或科学claim。

权威状态：ai4s/programs/sstdpn/research/STATE.yaml；当前实测：ai4s/programs/sstdpn/research/sfp-v0.1-repair10/execution/CURRENT_STATUS.json；完整资格与来源：REUSE_SOURCE_VERIFICATION.json、ACTUAL_SOURCE_CONSUMER_CHECK.json、RECOVERY_REPORT.json、FREEZE_RECEIPT.json、PACKAGE_RECEIPT.json。18复用＋6补跑闭集须在远端全部完成后fetch→verify→intake→分析，才能给出科学判断。


### D-206 - DBConformer WCR-R1 下一轮设计（2026-10-11）

用户要求“继续设计下一轮研究”。LRC last1fix1 已完成verified intake、原环境修复重放和精确负筛查关闭；P1−B0 −0.1157pp、P1−C0 −0.9645pp，配对作用1/9可测。旧campaign的COMPLETE_MAX_ROUNDS、暂停、累计预算/成本和科学记录保持。新设计按DBConformer活动v3.1登记DISCOVER_NEXT / DESIGN_ONLY。

选择WCR：时间embedding query读取同名义窗局部电极内容，将逐窗残差送入原时间Transformer，原空间池化/空间Transformer保留；C0仅把query固定循环错位4/8窗，参数和读取次数匹配。明确继承旧LTA的query/局部表征，区别在电极softmax、时间残差目的地和错位控制，不称首次时空attention或独立原创主方法。18项合成CPU检查及独立内部审查通过，不等于生产/GPU资格或EEG效果。提案18科学+2技术新fit，9 B0仅在身份完全匹配后复用；复用不合格即停止，不自动增加训练。

目前0新Run/预算/训练/Claim。真实宿主、RNG/optimizer、B0跨Run复用、设备资源及完整最近邻等价性待资格化，新SCREEN_NEW和预算未授权。权威记录：ai4s/programs/dbconformer/research/discover_next_20261011/DESIGN_TRANSITION.json；简报：ai4s/programs/dbconformer/research/discover_next_20261011/RESEARCH_BRIEF.md。本摘要不授予执行权限。


### SFP repair10 完整回拉与开发正筛查（2026-10-12）

精确Run 2026-10-11_sstdpn_sfp_r01_v0_1_repair10-full-w1，合同SHA 2b99cb8bf94833f6f043b377e77780537bd4501f03097797b21e7d66aced64e9。742项manifest文件校验和官方intake通过；18项repair8成功原产物复用、6项repair10补跑，完整24项矩阵通过来源/预测/标签/130epoch/配对初始化和顺序验收。两项分析兼容修复单独留痕：严格JSON解析；仅两项已批准预算字段差异的跨Run配对凭证科学身份。原全字节SHA一致门未通过，受限新增兼容路径通过；原合同、包和产物未改。Grok专项审查实际报告和限制见 GROK_REVIEW_DISPOSITION.json。

冻结结论 SCREEN_POSITIVE：P−B0 +1.504630 ACC百分点，P−C +1.562500，P−D +0.347222（只描述）；各被试P−B0均值≥−3门通过。只有S02两seed对B0/C都为正；S05一seed对B0为负，S08对C符号反转且大正差集中seed4。保留固定P候选，下一项建议是预登记同候选的稳定性复核，先准备合法独立证据/暴露边界及相应新授权；当前单轮结束，无新增训练、调参、对照晋升或论文claim。论文材料只能引用开发筛查支持，不能当作正式benchmark或纯机制因果证据。

证据：AI4S-SSTDPN-sfp-r01-v0.1-repair10；决策：ai4s/programs/sstdpn/research/sfp-r01-v0.1-repair10_decision.yaml；报告：ai4s/programs/sstdpn/research/sfp-v0.1-repair10/execution/ANALYSIS_REPORT.md；状态：ai4s/programs/sstdpn/research/sfp-v0.1-repair10/execution/CURRENT_STATUS.json。Program状态 COMPLETE_MAX_ROUNDS，paused=True，原预算和累计成本保留。


### 固定P稳定性复核部署（2026-10-12）

用户要求“保留P，进行稳定性复核实验”，并在平台对核心控制器变更拒绝后明确“批准”该具体有界补丁。保留P rank2、C原固定置乱seed20261009、100+30epoch、FP32 batch32、原DATA/SPLIT和模型/训练三文件原字节。Agent前瞻选择B0/P/C × S02/S05/S08 × seed0/1=18项从头训练、3项源域technicalepoch；D仅共同初始化封印不训练。旧seed3/4单列，新结果不靠旧新合并挽救。累计seed0/1/3/4=4≤原cap5。

原repair10 SCREEN_POSITIVE作为已暴露开发筛查证据保留。新主效用门为P−B0等subject平均≥1pp、每新seed跨subject平均>0、每subject两seed平均≥−3pp；P−C均值≥1pp且每新seed均值>0为独立轴复核，不决定效用标签。仅REPLICATION_SUPPORT/NO_REPLICATION_SUPPORT或INVALID；无因果、总体或论文claim。

已通过17项本地CPU检查、38项显式源SHA和实际打包消费检查，包40项文件SHA闭合。打包补齐原模型隐式temporal_backend依赖，其字节等于本轮显式冻结文件；合同与既有snapshot文件未改，补包记录IMPLICIT_DEPENDENCY_CHECK.json。外审Grok4.6-build完成，原verdict为WARN/BLOCK deploy；主Agent接受代码/边界核对，基于Transaction内technical→science合同驳回“新GPU/intake必须先于新Run”循环前置要求；原报告与采纳/驳回完整保留于GROK_REVIEW_REPORT.md/GROK_REVIEW_DISPOSITION.json，未改成PASS。前两次调用因turn上限无完整结论均记incomplete。新真实GPU资格必须在本轮technical门取得，未取得前science阻断；未宣称新科学intake通过。

精确Run：`2026-10-12_sstdpn_sfp_stability_r01_v0_1-full-w1`；Transaction：`2026-10-12_sstdpn_sfp_stability_r01_v0_1-tx`；合同SHA256：`634ec3f3452e49b4089f9beee2a594f19315788457869faa56a1cfe2cbd0467b`。已冻结、登记continuation、打包、上传、启动并probe核验精确身份。controller仅注册这一个stage/second-round/role；原campaign起点2026-10-09T07:10:24.886802+00:00、全部旧合同/Run/日志/成本保留，总预算仍50h、不新增小时，只max_rounds1→2。新Transaction13h，单科学任务2400s，技术300s，5s终止宽限，上界44205s；单attempt，无自动修复或下一轮。

北京时间2026-10-12T01:39:18.122887+08:00观察：技术门3项，完成0、失败0、运行0、待排3，attempt记录0；科学18项尚被technical门阻断。远端action=WAIT_FOR_RESOURCES；资源原因{'causes': ['insufficient_reserved_memory'], 'observed_free_mib_min': 51, 'observed_free_mib_max': 1778, 'initial_task_commitment_mib': 2048, 'fixed_memory_reserve_mib': 0}。累计已计成本35.463h、剩余14.537h，纯资源等待按原exclude_resource_wait策略排除；不是训练失败，也不是科学证据。后续同Run只读检查，完成后fetch→verify→intake→新seed分析→登记处置→停止。

权威State：ai4s/programs/sstdpn/research/STATE.yaml；冻结合同：ai4s/programs/sstdpn/research/sfp-stability-r01-v0.1.yaml；最新快照：execution/CURRENT_STATUS.json；前瞻设计：research_brief.md、DESIGN_CONFIG.json。旧筛查证据不被这份运行记录覆盖。


### SFP stability repair1：17项保留与单项补跑（2026-10-12）

用户明确要求仅补S05-P-seed0、核验保留其余17项并先对账停止后预算。旧稳定性Run科学17成功/1失败，失败为cuDNN convolution算法选择错误，非2400秒超时，根因尚未确定；旧Run、合同、日志和科学不完整状态保留。306个成功源文件已回拉、逐文件核验并经真实新消费者与回执桥重放；仅复用同一稳定性矩阵17项，不合并旧screen seed3/4。

新Run `2026-10-12_sstdpn_sfp_stability_r01_v0_1_repair1-full-w1`，合同SHA `619d943aad41d53041787704a99db90e6111ca758065fbf308c095dba988d0c0`。只新增1项科学fit及1项source-only technical-P一epoch；原训练、数据、seed、backend、配对seal和科学门不变。任务2400/300秒、节点3000/600秒、Transaction一小时、单attempt、无自动修复。4096MiB为初始资源承诺，不能证明旧故障原因。恢复入口与实际共享调度器检查通过；Grok4.6-build真实外审WARN，允许有界注册/启动，无科学claim。原始外审、首两次未完成记录和本地处置保留。

原50小时总额度、原起点及旧成本保持不变。独立核实停止区间10.158小时并按证据排除；部署前剩余13.133小时，本次一小时准入通过。Lab10唯一上传/launch/probe已核验精确身份，56个上传文件哈希通过。当前WAIT_FOR_RESOURCES：技术1待运行、零attempt；科学补跑被技术门阻挡。17项仅资格核验通过，尚非新Run正式intake或稳定性结论。

权威State与Evidence Index已指向repair1；报告 `ai4s/programs/sstdpn/research/sfp-stability-r01-v0.1-repair1/execution/DEPLOYMENT_REPORT.md`，最新快照CURRENT_STATUS.json，停止预算PREDEPLOY_BUDGET_RECONCILIATION.json。后续同Run只读probe，闭合18项后fetch→verify→intake→分析；不自动追加补跑或研究轮次。


### D-207 - DBConformer SGR-R1 下一轮训练研究设计（2026-10-12）

用户要求“进行下一轮研究”。WCR-R1保持INVALID，不把条件性数字计作科研负结果或用于调参；有效LRC、BPM、HDS精确比较未建立各自结构干预的clean净增益，CPA/BDA缺失场景支持保留。旧campaign暂停、预算、累计成本、last_decision及科学证据不变，新设计按v3.1登记DISCOVER_NEXT / DESIGN_ONLY。

SGR保留原DBConformer。B0为原配方的合格历史参照，C0为来源受试者/类别均衡批次的ERM，P1为同批次的来源风险GroupDRO。每批8来源×4类各1真实trial，加原32项同类重组增强；增强可能混来源，仅用ERM，不伪造来源标签。P1以固定eta0.01更新来源权重，本步使用且detach；这是已知方法的部分适配，无原创算法Claim。P1−C0检验风险权重增量，P1−B0检验整体配方，两项需同时过预定效用门。

18项离线metadata/代数检查通过，独立内部审阅PASS_WITH_LIMITS；生产梯度、11500步log权重稳定性、B0复用及完整新源码/消费者资格未完成。提议18科学+2技术新fit、有条件复用9项B0、未来新增10小时；均不是当前执行授权。0新Run/fit/预算/Claim。权威登记：ai4s/programs/dbconformer/research/discover_next_20261012/DESIGN_TRANSITION.json；设计：ai4s/programs/dbconformer/research/discover_next_20261012/RESEARCH_BRIEF.md。


### SFP 新seed稳定性复核完成：NO_REPLICATION_SUPPORT（2026-10-12）

精确Run `2026-10-12_sstdpn_sfp_stability_r01_v0_1_repair1-full-w1`，合同SHA `619d943aad41d53041787704a99db90e6111ca758065fbf308c095dba988d0c0`。官方fetch/manifest验证/intake通过，17项同稳定性矩阵原产物＋1项S05-P-seed0补跑完整闭合18项、10368条预测；来源桥、数据/标签reference、130epoch、checkpoint恢复、原始配对初始化和顺序seal及准确率重算均通过。旧screen seed3/4保持独立。

冻结估计量为subject内平均seed0/1，再对S02/S05/S08等权平均。P−B0为−0.7523pp，seed0为+0.6944pp、seed1为−2.1991pp：均值≥+1pp和每seed>0两个效用门未通过；每subject均值≥−3pp风险门通过。P−C为+1.2442pp，两seed均值分别+2.1412/+0.3472pp，轴对照门SUPPORTED；该门不决定效用，不挽救P相对B0的不稳定效用。判定NO_REPLICATION_SUPPORT，无总体/因果或论文claim。

判断变化：旧正screen证据保留，新seed复核不支持稳定效用优势；P保留为已有候选与来源，不合并旧seed来改变本轮判定、不升级正式评估。下一处置：按合同停止，本次不追加seed/rank/permutation/数据集/训练。未来重新启用须先有前瞻问题、对照与新授权。

控制器决策登记遗漏repair1角色映射已局部修复，真实结果与3项错误身份拒绝通过；仅精确标识适配，未改科学门或冻结包。决策 `ai4s/programs/sstdpn/research/sfp-stability-r01-v0.1-repair1_decision.yaml`；证据ID `AI4S-SSTDPN-sfp-stability-r01-v0.1-repair1`；报告 `ai4s/programs/sstdpn/research/sfp-stability-r01-v0.1-repair1/execution/ANALYSIS_REPORT.md`。State COMPLETE_MAX_ROUNDS/paused=True/无active_run；原50小时预算及旧成本保持，完成后的空闲抵扣未自动追加。


### 关闭SFP稳定性轮，准备ESF共享电极子空间设计（2026-10-12）

用户要求关闭当前轮并沿电极×滤波器结构分解设计下一轮。SFP稳定性精确Run及NO_REPLICATION_SUPPORT/轴对照SUPPORTED保持原结论；关闭记录CLOSURE_RECORD.json绑定verified decision与analysis，无active_run/operation，State仍COMPLETE_MAX_ROUNDS/paused。独立核实完成后的停止区间4.419h并按既有政策结账，对账时剩余12.924h；原50h cap、原起点和运行成本不变，不预先抵扣未来空闲。

后继为ESF-v0.1，状态DESIGN_ONLY。旧P每输出独立电极×滤波器rank2；新ESF所有输出/滤波器共享A[22,7]电极基，H[48,9,7]保留完整滤波器系数，W[o,f,e]=sum_k H[o,f,k]A[e,k]。仅替换原198→48投影，SSA/BN/ELU/方差pool/1072维/ISP/ICP/100+30训练接口保留。投影参数3226，对照平面rank13为3246；k/q用最近参数数规则定，不用效果搜索。电极mode rank≤7、每输出rank≤7，但全局flat rank可48；不能把它叫平面rank7或只将旧P调rank。

拟议B0/S/C/D×S02/S05/S08×已暴露seed0/1=24个fresh fits、4个source-only技术epoch。C为相同参数/初始化的原固定非轴置乱；D只匹配接近参数量与一般双线性瓶颈，函数类不同。主效用S−B0均值≥1pp、每seed均值>0、每subject均值≥−3pp；S−C/D结构解释单列，不能挽救效用失败。谱系已见{0,1,3,4}和cap5不重置，无新数据独立性、无额外seed/rank/置乱救援。

真实代数等价、参数数与秩检查通过，仅synthetic、零EEG/零优化；尚未实现新生产模型或GPU资格。Grok4.6-build有界外审READY_DESIGN，首次max-turns未完成保留，第二次完整stop=end_turn；该裁决只支持设计，不授予科学/执行资格。arXiv经典与近期定向检索、本地AMEEGNet正文已读取，最近邻BTTDA全文和完整新颖性比对仍缺，不宣称张量分解原创。旧rank2失败原因仍未确定。

准备目录 `ai4s/programs/sstdpn/research/esf-r01-v0.1/`：research_brief.md、DESIGN_CONFIG.json、REVIEW_DISPOSITION.json、LITERATURE_GROUNDING.md、DESIGN_HANDOFF_RECEIPT.json。Evidence Index记录后继准备及来源反馈；无新冻结Transaction、Run、训练、budget增额或原授权扩轮。以后执行须有精确新范围/操作授权、预算核验和实现闭环；当前工作完成到设计交接。


### D-208 - DSA-RCD-v0.1 下一轮研究设计（2026-10-12）

用户要求参考 Downloads/RESEARCH_BRIEF.md 完成下一轮设计。选定有边界的独立候选：同一合法 trial 的短时带功率持续性摘要，经81参数控制器生成一个共享尺度，只调四个原生depthwise时间卷积的采样间距。KShape改固定tap核系数、TKS改tokenizer核字典；已核对不是同一精确关闭实例。CRU的NO_SIGNAL保留，只提供“保留信息/结构差异不等于有效分工”的约束。

前瞻提案四臂B0/S0/N0/P0、9context、2seed，共72fit和72source audit，拟4技术fit/audit。采用独立cue后四秒DSA滤波资产与6train/1val/1audit/1excluded划分；旧trial窗口和SMANet无额外带通cue资产均不直接替用。新资产尚未生成。主ACC收益门+1pp，B0相对个体风险门−3pp，S0/N0归因参考门各+0.5pp，效用与归因分开；原CRU科学门不变。

36项离线设计算术/算子检查通过，不代表生产模型、真实数据或GPU资格。外审状态 COMPLETED_WITH_REVISE_AND_WRAPPER_PROTECTION_WARNING；原始 verdict REVISE，处置见 refine-logs/DISPOSITION.json。 当前是设计准备，0新Run/训练/预算；旧campaign及成本不转移。新颖性、正式性能、专业化与互补均未认证。

权威设计：ai4s/programs/dsainet/research/dsa-rcd-v0.1/research_brief.md；唯一数值草案 DESIGN_SPEC.yaml；登记 DESIGN_TRANSITION.json。


### D-209 - DSA-RCD-v0.1 获准启动准备（2026-10-12）

用户在审阅D-208设计后明确要求“启动实验”。绑定既定四臂、九context、两seed，72个100epoch训练和全训练封存后72源审计，前置四个1epoch技术训练/审计。代理选择独立单轮24h执行封顶，生产smoke后核对预算可行性；旧CRU原Run、NO_SIGNAL、起点/成本不变，不转移旧余量。新cue资产5184×22×1000、18rawSHA和九组3456/576/576/576隔离划分已核验，并已上传Lab10核对全文件SHA。当前为实施/生产验收准备，尚无RCD科学证据。权威授权与预算入口：ai4s/programs/dsainet/research/dsa-rcd-v0.1/AUTHORIZATION.md、BUDGET_LINEAGE.json；实际运行由STATE管理。

### D-210 - DBConformer SGR-R1授权启动与派发前不可变工程修复（2026-10-12）

SGR-R1已获明确材料上传与新增10小时授权，预算起点保留2026-10-12T11:35:22Z。原SGR冻结Run在上传前发现full64梯度探针接线错误，零尝试、无远端包/进程；原合同/源码保留，使用同campaign不可变repair1替代，无训练重试或额外fit。repair1通过Lab10原环境CPU训练接口、7消费者与9基线测试，三臂初始权重SHA一致；冻结合同SHA 5091b8cf174db750ee6f62917bd198a393624ebf14ce7330b9f04ef118302af7。实际上传/launch/probe确认同Run 2026-10-12_dbconformer_sgr_r1_repair1_lab10_r1-full-w1；启动快照技术2项中1运行、1等待、0完成、0失败，C0位于GPU9，18科研项受技术门阻挡。总限额20新fit（2技术+18科研），9项LRC B0独立复用；WCR INVALID与旧预算/成本完整保留。当前仅运行启动证据，无科研结论或Claim。

证据：`ai4s/programs/dbconformer/research/sgr_r1_repair1/STARTUP_RECEIPT.json`；原零尝试核验见同目录`SOURCE_ZERO_ATTEMPT_REPORT.json`。后续按同Run只读检查，完成后fetch/verify/intake/replay/decision，不自动扩轮。


### ESF-v0.1 启动准备：待预算增额（2026-10-12）

用户“启动实验”已授权既定Lab10 ESF四臂24项freshfit及4项源域技术epoch。实现、真实100+30代码的微型合成产物消费、34源隔离包、数据全SHA、限定controller及seed历史门已检查；Grok最终真实结论READY_IMPLEMENTATION_PENDING_BUDGET。原SFP稳定性NO_REPLICATION_SUPPORT保持关闭，累计起点、成本、seed0/1/3/4暴露不重置；新seed0/1为新方法重复初始化。当前50h上限对账剩约12.924h；串行任务上界58940s，拟17h Transaction，短缺约4.076h。具体提案仅累计增5h至55h并增加这一轮slot3，尚待用户预算批准。当前零真实ESF科学fit，无冻结合同/Run/上传/launch，真实GPU门与跨设备回放尚未验收。权威记录：ai4s/programs/sstdpn/research/esf-r01-v0.1/execution/LAUNCH_PREPARATION_REPORT.md、PREPARATION_HANDOFF.json及Program Evidence Index。

### ESF-v0.1 已部署：等待资源（2026-10-12）

用户批准累计50→55小时（+5小时）、仅第3轮ESF及17小时Transaction；保留原起点/已用成本/旧Run/暴露。已冻结合同、34源文件闭包并正式上传，在Lab10核验同Run `2026-10-12_sstdpn_esf_r01_v0_1-full-w1` / SHA `24fca4deb64de31bad1050b71aab698320f5cae2b4a66b10f81c422f7f709113`。21:20北京时间快照：4技术待排队、0尝试；24科学尚未开始，WAIT_FOR_RESOURCES（最高2947MiB低于4096MiB承诺）。技术门通过后才进入科学任务，资源等待不计执行预算。无科学结论/论文主张；SFP负稳定性结论保持。正式记录：`ai4s/programs/sstdpn/research/esf-r01-v0.1/execution/DEPLOYMENT_REPORT.md`。


### D-209 执行补记（2026-10-12）

RCD原Run在任何fit前因共享parser拒绝多余启动参数而失败，按metadata登记工程INVALID；在原启动授权及合同一次准备修复额度内，移除该参数并建立新不可变Run `2026-10-12_dsainet_rcd_v0_1_repair1-full-w1`。科学矩阵、模型/数据/拆分/seed/100 epoch/判定门和24小时campaign原起点均保留，修复准备额度已用完。Lab10精确probe验证 RUNNING / WAIT_FOR_RESOURCES；正式与技术训练尝试均为0。真实GPU四臂验收和实测时长预算门在科学派发前执行，当前没有科研证据。记录：ai4s/programs/dsainet/research/dsa-rcd-v0.1-repair1/LAUNCH_RECORD.md。

### ESF-v0.1 回拉分析：INVALID 数值重放门（2026-10-13）

精确Run `2026-10-12_sstdpn_esf_r01_v0_1-full-w1` / contractSHA `24fca4deb64de31bad1050b71aab698320f5cae2b4a66b10f81c422f7f709113`：4技术+24全新科学拟合均完成，1048manifest条目及34冻源哈希通过。完整100+30、配对seal、双优化器/RNG、48checkpoint身份核验；consumer union/list hash表示及PyTorch默认优化器字段兼容问题仅通过补充入口修复，冻源未改。24项CPU重放13项logits未过固定容差，13824条argmax零差异；不放宽门。正式冻结决策登记INVALID，角色invalid_non_scientific_record，第3轮COMPLETE_MAX_ROUNDS/paused=True/无active Run。

仅诊断：S−B0=0.000pp（seed0 +0.984、seed1 −0.984）；S−C=+1.157pp，S−D=+0.752pp。效用和完整结构门均不满足；不能作为验收通过的NO_SIGNAL、总体结论或论文Claim，也不能以C对照救效用。原SFP负稳定性边界保留。Grok专项适配审查READY_DIAGNOSTIC_PENDING_REPLAY、wrapper0；审查未读取全24长JSON，范围限制保留，不能称全矩阵科学外审通过。

累计55小时cap、原起点成本与暴露不重置；独立观测后仅抵扣已证实12.558小时停机，对账时余额14.911小时，不给未来停机信用。无新训练/seed/rank搜索/下一轮授权。记录 `ai4s/programs/sstdpn/research/esf-r01-v0.1/execution/ANALYSIS_REPORT.md`、`DIAGNOSTIC_SUMMARY.json` 与 `INTAKE_REVIEW_DISPOSITION.json`。下一步若处置数值门须明确新的验收范围并保留当前INVALID及原容差，当前不启动实验。


### D-209 执行补记（2026-10-13）

用户要求修复补跑，并明确同意只扣原repair1终止至本轮保守准备起点的54812.56449556351秒已核验停机区间。原24h累计上限、campaign起点、原执行/准备成本保留。repair2使用真实采样器到worker的单向ACK修复短GPU阶段失采，保留4技术fit/3合格audit，唯一B0技术审计一次补测成功（full-process峰1321MiB）。原receipt哈希均一致，新smoke节点PASS；原失败Run仍工程INVALID，不复活为科学证据。科学72fit/72audit尚未派发，等待>=4不同GPU满足保守3072MiB承诺。新预算门用已测技术时长的四worker预测，保持科学72000秒期限；仅剩技术scope缩为单audit900秒，合计含分析上界76500秒。原外审GPU未验收BLOCK原文保留，真实B0采样与新技术PASS已闭合该缺口。记录：ai4s/programs/dsainet/research/dsa-rcd-v0.1-repair2/REPAIR_CLOSURE.md。

### D-211 - SGR-R1校验修复与2技术导入/18科研续接准备（2026-10-13）

用户要求修复补跑SGR-R1。repair1两项技术fit退出0，产物校验因hashlib缺失失败；补入导入后又发现FP32均值与FP64复算的错误比较。repair2仅修复消费者：按四项FP32运算舍入界复验风险，未改训练或科学判据。两份真实产物共23000步全通过且篡改拒绝；source manifest235文件、完整snapshot272文件均逐SHA封存。新续接为CPU验证导入2技术、GPU只执行原18科研fit，累计仍20，独立复用原9LRC B0。Lab10五套CPU验收（训练接口、消费者12、B0九、校验器五、导入五）和三臂初始core资格PASS；整生产CPU节点入口PASS，511项声明依赖闭包通过。原10小时授权已到期，未改预算/起点/成本、未自行排除停止时间、未冻结/登记新Run或派发新fit。最终准备入口ai4s/programs/dbconformer/research/sgr_r1_repair2/REPAIR_PLAN.md；下一步需明确从确认起新增10小时可用时间，累计封顶为确认时已记账总时长加10h；只18新fit，无新技术fit/seed/候选/调参/自动重试/下一轮。

### ESF-v0.1 数值兼容补充复核完成（2026-10-13）

用户明确授权仅修复数值验收兼容性/复核已有产物，不重训24项，保留原冻结合同和INVALID。原Run `2026-10-12_sstdpn_esf_r01_v0_1-full-w1`、合同canonicalSHA `24fca4deb64de31bad1050b71aab698320f5cae2b4a66b10f81c422f7f709113` 及原INVALID记录逐字节保留；原CPU13失败仍保留。独立补充verification范围为原Lab10CUDA/RTX2080Ti FP32 batch32/native ISP renorm，原rtol1e-5/atol1e-6未放宽：24旧checkpoint各2次freshload，48次logits与原seal逐位相同，最大差0；13824条argmax完全一致。4技术/24既有训练/48阶段checkpoint与四组状态哈希、34冻源、1048manifest及数据/配对/100+30来源再次通过。新增训练/优化器步/反向传播=0，无新Run/Round、预算增额或暴露重置。

补充范围内接受的重分析：NO_SIGNAL / NOT_ESTABLISHED；S−B0=0.000pp（seed0 +0.984、seed1 −0.984），S−C=+1.157pp，S−D=+0.752pp。效用与完整结构门均不满足，不支持升级共享电极基路线。不是新独立复现、总体因果或paper claim。Grok专项外审READY_REVALIDATED_ARTIFACT_ANALYSIS、wrapper0，未独立执行binary哈希；其优化器/RNG明细风险已本地补存48checkpoint raw/loaded/stored等值证据，原报告和限制保留。V2中断推理debug与V3通过、native ISP状态性及补充合同元数据勘误都有记录，不掩盖失败。

Program仍COMPLETE_MAX_ROUNDS/paused/原last_decision INVALID，State字节不变；Evidence Index仅追加原round下的补充记录指针 `AI4S-SSTDPN-esf-r01-v0.1-numerical-revalidation-v1`，不覆盖原结论。报告 `ai4s/programs/sstdpn/research/esf-r01-v0.1/execution/numerical-revalidation-v1/REVALIDATION_REPORT.md`；补充决策 `SUPPLEMENTAL_DECISION.json`。本次修复关闭，不启动下一轮；当前没有依这些结果扩展rank/seed/permutation的授权或依据。


### D-212 - SGR-R1 repair3 原18项补跑启动核验（2026-10-13）

用户确认于2026-10-13 13:58:52北京时间新增10小时可用时间，只补原18项科研fit，复用2技术和9旧B0。repair2 CPU导入PASS，但source_import保留字段触发科研派发前拒绝，直接核验科学attempt目录为空、无scheduler产物、无存活进程。repair3将合同技术复用字段分离为technical_evidence_reuse，共享调度器未修改，原始科学矩阵、判据、3072MiB承诺、GPU0–9部署合同保持。Lab10六套隔离CPU回归和B0/C0/P1初始core匹配通过；旧23000技术步继续复用。已上传、单次启动并按Run及合同SHA核验：2026-10-13_dbconformer_sgr_r1_repair3_lab10_r1-full-w1，当前RUNNING，科研已完成0/18、运行2、待执行16、失败0。原起点2026-10-12T11:35:22Z、全部旧成本、累计封顶28.389022620386548h和唯一已登记预算扩展保留，未重新开始10小时计时。只排除核验纯资源排队，不增加重试/seed/候选/调参/下一轮。旧失败及WCR INVALID保留；未完成fetch/verify/intake，不支持科学claim。记录：ai4s/programs/dbconformer/research/sgr_r1_repair3/STARTUP_RECEIPT.json。


### ASR-v0.1 下一轮研究与Lab10准备（2026-10-13）

依据P稳定性NO_REPLICATION_SUPPORT和ESF匹配CUDA补充NO_SIGNAL，改为保留可训练dense，仅增加零H共享电极×滤波器残差；C仅置乱残差路径。这是同线性函数类的优化先验筛查，不能称表达能力增加、因果机制或独立确认。原ESF INVALID、旧成本与暴露完整保留。拟B0/R/C×S02/05/08×seed0/1=18freshfit+3技术，原100+30，13h Transaction，累计55h新增0，仅新增ASR第4轮。设计/工程准备授权已执行；具体数字与ASR执行范围尚待确认。隔离草案6组工程检查通过，Grok设计及收口实施审查已返回真实READY准备结论，均不代表真实GPU或科学结果。前次实施审查max-turn取消保留。记录 `ai4s/programs/sstdpn/research/asr-r01-v0.1/execution/PREPARATION_REPORT.md`。


## ASR 第4轮实际部署与入口失败（2026-10-13）

用户明确批准仅第4轮 ASR、18项科学训练＋3项技术检查、单轮13h/累计55h、无自动补跑。已冻结、上传并实际启动 Lab10 Run `2026-10-13_sstdpn_asr_r01_v0_1-full-w1`（合同 `55eec850b732bb904fe5da6e49af0b361f32b3025dc26df8dd123502fe9bab89`）。技术节点约2.564s后在 CLI 入口失败：共享执行器通过 AI4S_TRANSACTION_OUTPUT 传输出目录，而 ASR runner 只接受 --output。3项技术任务/18项科学任务均零尝试，无拟合产物及科学结论；登记工程 INVALID 并暂停，未补跑。原 ESF INVALID、起点、暴露和历史成本保留。预算在 2026-10-13 11:59:05 UTC 观测结算：已计费40.416619h，余额14.583381h；无未来抵扣。

具体回执与后续修复边界：[DEPLOYMENT_REPORT](ai4s/programs/sstdpn/research/asr-r01-v0.1/execution/DEPLOYMENT_REPORT.md)。后续仅修输出目录接口及真实冻结argv入口测试，新不可变修复Run需新的补跑授权；不得解释为 ASR 科学负结果或追加第5轮。


### RCD resume1 工程补跑 2026-10-13
用户授权“补跑”并单独允许扣除17:15:19.103664–19:51:02.389060这段9343.285395622253秒停机；原campaign起点、24小时累计上限与全部执行/准备成本保留。repair2外层nvidia-smi查询超时按官方metadata intake登记INVALID，无科学效果判断。
新Run `2026-10-13_dsainet_rcd_v0_1_resume1-full-w1`（合同SHA `5991469137ac958860e8363ddd79ad53a2d3d681da0c259aeaf4800e051c6b29`）已Lab10上传、启动及同Run probe核验。独立资格核验保留4个完整100epoch fit输入及4个技术fit/audit，只补68 fit，完成后封存完整72-fit新屏障并执行72 audits。修复沿成熟遥测重试路径，实施原冻结3600/900秒个体期限，不改变科研数学/数据/seed/gates。Linux实际字节/纳秒恢复及20项CPU回归PASS。启动检查技术恢复PASS，screen WAIT_FOR_RESOURCES，原3072 MiB承诺下1/4不同GPU可准入，尚未派发新fit；不是模型负结果或完成科学证据。
权威运行与证据入口：ai4s/programs/dsainet/research/STATE.yaml、EVIDENCE_INDEX.yaml；工程验收和启动快照：ai4s/programs/dsainet/research/dsa-rcd-v0.1-resume1/{SOURCE_INVENTORY.json,SOURCE_GPU_CHECK.json,BUNDLE_CHECK.json,REGISTRATION_CHECK.json,STARTED_CHECK.json}。不产生论文Claim。


## ASR 第4轮 repair1 补跑已启动（2026-10-13）

用户“修复补跑”明确授权的工程替换Run `2026-10-13_sstdpn_asr_r01_v0_1_repair1-full-w1` 已在Lab10上传/启动/probe，并核对远端manifest与合同 `25e6f73c56ee776576c412e1fb29a15d9b44c9ff09fccdf87e1c59d63cdf427c`。仅修输出目录环境接口及repair身份登记；科学DESIGN_CONFIG SHA保持0cd6e45ec79823e3e971e8a5fc8c60b0e84a187626a1b5baeb1f701dcfa9aff3，18+3/13h/累计55h/第4轮均保持，原ASR及ESF INVALID保留。当前3项技术任务等待容量，均零尝试；18项科学任务未释放，无科学结论。真实入口反例/回归、8项controller反例、最终隔离包校验通过；可选Grok增量review未返回final，保留未完成状态，不记外审通过。无自动补跑。

记录：[DEPLOYMENT_REPORT](ai4s/programs/sstdpn/research/asr-r01-v0.1-repair1/execution/DEPLOYMENT_REPORT.md)。


### D-213 - SGR-R1 repair3 回拉分析与处置（2026-10-13）

同Run `2026-10-13_dbconformer_sgr_r1_repair3_lab10_r1-full-w1` 已完成manifest验证、标准intake及原Lab10 CPU回放：18新科研fit、2旧技术导入、9独立旧LRC B0；本次新增fit=0。新旧源闭包/来源隔离/训练贡献/checkpoint选择/CPU-GPU logits按冻结规则通过。原回放推理前旧YAML合同被按JSON读取失败，独立SHA绑定读取桥接修复，原失败、原冻结源及桥接执行SHA保留；不是原脚本未经适配直接通过。

登记判定 `INSUFFICIENT_SOURCE_SUBJECT_RISK_DUAL_UTILITY_SUPPORT`。平均准确率B0=58.1211%，C0=56.8480%，P1=56.2114%；P1−B0=-1.9097pp、P1−C0=-0.6366pp，完整冻结双效用门见ANALYSIS.json。反馈按证据引用→判断变化→停止/设计处置→下一对照边界登记到RESEARCH_FEEDBACK.json。仅已暴露九受试者seed0探索筛查，不构成独立确认、统计显著性、普适优越性或论文Claim。没有追加seed/eta调参/候选/下一轮训练；旧WCR INVALID和repair失败记录、原campaign起点及全部成本、唯一10h扩展及累计28.389022620386548h保留。State=COMPLETE_MAX_ROUNDS，active Run已关闭。报告：ai4s/programs/dbconformer/research/sgr_r1_repair3/ANALYSIS_REPORT.md。

工程补充：YAML格式适配后又发现wrapper与base初始化哈希被混比。原Lab10 CPU诊断确认两层哈希分别匹配原来源记录；仅将core复算改为base.state_dict，完整wrapper/core/checkpoint校验仍保留。两次失败、原冻结源与实际桥接/覆盖函数SHA均保留。

配对身份补充：旧LRC B0 labels_digest属于source-valid，SGR同名字段属于target。原baseline validator保留，九组原始SHA绑定target索引/标签及train/valid/test split与字节SHA严格核验后，仅在分析副本中使用共同target摘要，旧摘要及角色另存，原B0指标/正确数不变，篡改拒绝。另一个子Agent已独立核验27行原始NPZ与18组配对，并按整数正确数重算两项四门，均一致；其复算未独立重跑完整analyzer，限制已记录。

最终核验：Grok实际模型grok-4.6-build完成限定的目标配对身份审查，结论READY_METADATA_COMPATIBILITY，范围及限制见GROK_IDENTITY_REVIEW_DISPOSITION.json；主Agent另用现有mieeg环境完整重执行冻结analyzer，输出与登记ANALYSIS逐字节一致，未新增推理或fit。最终登记仅补齐本轮证据角色路由及决策JSON日志科学计数浮点读取；原不可变决策日志与冻结分析/源保持不变，修复回执随CLOSEOUT_RECEIPT保留。


### D-214 - DBConformer SCR-R1 下一轮设计（2026-10-13）

SGR repair3的合格精确负结果关闭原eta=0.01风险重加权配方。用户要求进行下一轮研究后，按v3.1完成SCR-R1设计：原DBConformer/普通ERM保持，完整source-train供体池每位置用相同片段，P1同source连接、C0预定Latin跨source连接；分别检验P1−B0整体效用与P1−C0连接规则增量。SGR不证明增强是病因；subject一致不等于trial/session/相位连续，接缝与跨段统计尚未分离。历史精确关闭、WCR INVALID及已暴露九人seed0边界保留。

一手近期检索定位为已有重组增强的受控适配，原创性低到未定，不写论文主方法Claim。元数据与合成代数检查通过（17组），Grok专项设计审查READY_DESIGN；真实生产runner、最终Bundle消费者闭环及目标GPU资格仍待准备。本轮DISCOVER_NEXT/DESIGN_ONLY，不创建campaign、Run、预算或训练，SGR State/起点/成本/额度原字节保持。未来单轮20新fit（2技术+18科研）、复用九旧B0、10h均只是提案，须精确获准。简报：ai4s/programs/dbconformer/research/discover_next_20261013/RESEARCH_BRIEF.md；证据链：同目录DESIGN_TRANSITION.json。


## ASR 第4轮 repair2 目录接口修复补跑（2026-10-14）

用户“修复并补跑”授权的一次工程替换Run `2026-10-14_sstdpn_asr_r01_v0_1_repair2-full-w1` 已在Lab10上传/启动/probe，合同 `d06de9e74619f2a89a93eb2f2ccec38f840678549018c08c159630fd017ebb94` 与远端manifest核验一致。仅拆开日志/遥测transport目录与空artifacts，实际worker/发布/Transaction接收器回归及最终冻结合同的Lab10 Linux CPU验证通过（0 EEG/0 fits，不代替CUDA资格）。科学配置bytes、18+3/第4轮/13h/累计55h、旧INVALID与成本全部保留；停止后已观测预算对账，远端CPU验证成本保留。当前技术3项等待容量，科学18项未释放，无科学结论，无自动補跑。

回执：[DEPLOYMENT_REPORT](ai4s/programs/sstdpn/research/asr-r01-v0.1-repair2/execution/DEPLOYMENT_REPORT.md)。


## DBConformer SCR-R1 已启动（2026-10-14）

用户明确授权上传、新增10小时、单轮最多20项新fit（2技术＋18科研）及独立复用9项旧LRC B0。原环境CPU资格通过：未变化路径复用真实22项检查，路径修正后另验九折B0与初值；无新EEG fit。旧SGR完整成本、失败与精确负结果保留。唯一Run `2026-10-14_dbconformer_scr_r1_lab10_r1-full-w1`，canonical合同 `d837a5b38344cdfe0a50fc7bfc63d0b619d1d99002e43e920dc203415a68f425`，正式远端manifest全部239条SHA与本地一致。当前smoke_C0/P1首尝试分别在GPU1/6运行，18科研任务未释放；无科学效果或Claim。GPU0–9为候选，容量共卡/2048MiB初始估计/零额外余量/无重试；仅核验纯资源排队扣除。权威状态及启动证据见 ai4s/programs/dbconformer/research/STATE.yaml、EVIDENCE_INDEX.yaml、scr_r1/STARTUP_STATUS.json；不自动启动下一轮。


## ASR 第4轮 repair3 配对封印接口修复补跑（2026-10-14）

用户“修复并补跑”授权的一次工程替换Run `2026-10-14_sstdpn_asr_r01_v0_1_repair3-full-w1` 已在Lab10上传/启动/probe，合同 `c9fc214c1debc441e8b2965d48efe91478c7f76171f0bc8d614764e14b65f9dd` 与远端manifest核验一致。修复node封印索引相对路径/SHA/Run/contract/node/pair身份绑定，真实封印读取/init/行顺序、合成checkpoint与发布/Transaction消费及最终冻结合同Lab10 CPU验证通过（0真实EEG/0科学fits，不代替CUDA资格）。科学配置bytes、18+3/第4轮/13h/累计55h、旧INVALID与成本全部保留；停止后已观测预算对账，远端CPU验证成本保留。当前技术3项等待容量，科学18项未释放，无科学结论，无自动補跑。

回执：[DEPLOYMENT_REPORT](ai4s/programs/sstdpn/research/asr-r01-v0.1-repair3/execution/DEPLOYMENT_REPORT.md)。


### RCD resume2 动态容量部署 2026-10-14
用户授权取消四张不同GPU同时就绪门，按实际显存与剩余预算逐个派发和动态扩展。源resume1在零新fit尝试时按用户授权停止，operator receipt及原证据保留；官方登记USER_AUTHORIZED_REDEPLOYMENT，不将等待或操作者停止捏造成科学失败。
新Run `2026-10-14_dsainet_rcd_v0_1_resume2-full-w1`，canonical合同 `59596ca7eebaef7b74cb11009a35967282af2cf0def748ee2ae64b2178a4cee7`；原4个100epoch完整fit及4个技术fit/audit原字节核验后恢复，只派发68其余fit，再建立新完整72-fit屏障并执行72audit。原数据/模型数学/四臂/seeds/checkpoint规则/科学门保持。
预算原起点及24h上限不重置，carried verified queue=36480.237701416016秒，已单独授权的stopped=64155.84989118576秒，本次不新增停机扣除；源resume1累计执行11732.831010341644秒及所有准备/外审计时保留。新Transaction执行上界随冻结剩余预算与继承未用额度收紧，并留900秒运输/登记余量，analysis3600及fit3600/audit900秒个体期限不变。每次准入检查node/Transaction/campaign三时钟，预算不足不新增任务、回收在途future并释放未启动预留；全量并行预测仅advisory，不假设未来容量。
Linux真实输入bytes/mtime_ns恢复及27项不同CPU检查通过（含重复执行共32项）；Grok/xAI grok-4.6-build明确部署门PASS。wrapper因并行DBConformer对顶层三文档的修改返回73，独立原始session工具轨迹均为只读/哈希计算，保护差异及警告原样记录，不自动回滚或称包装器干净退出。此为工程部署外审，不是科学intake/Claim裁决。
08:16同Run启动核验：技术恢复PASS、screen RUNNING；全10GPU已评估，当前仅1槽可用就派发B0_s0_t1，67pending/1running/0failed，4源fit权重和收据SHA未变，正式科学审计0/72；初始ACK尚未产生，真实GPU启动证明以同目录STARTED_CHECK后续快照为准。
权威运行与证据入口：ai4s/programs/dsainet/research/STATE.yaml、EVIDENCE_INDEX.yaml；本轮工程证据：ai4s/programs/dsainet/research/dsa-rcd-v0.1-resume2/{REDEPLOYMENT_REPORT.json,BUNDLE_CHECK.json,REVIEW_DISPOSITION.json,PROTECTED_GUARD_CHECK.json,REGISTRATION_CHECK.json,STARTED_CHECK.json}。无科学效果判断或论文Claim。


## SCR-R1 repair1 补跑启动（2026-10-14）

原 Run 因技术产物缺少基模来源字段而登记 INVALID，原始字节、失败日志、原起点与全部旧成本保留。repair1 已通过本地实际产物及 Lab10 原环境 CPU 验收，保留并重新核验两项旧技术训练；正式 Run `2026-10-14_dbconformer_scr_r1_repair1_lab10_r1-full-w1` 的两项导入已 PASS，未新增技术 fit。仅补原 18 项科研 fit，独立复用九项旧 LRC B0；科学矩阵、seed0、100epoch、停止与判断规则未变。用户确认时追加10小时，累计预算上限为 19.281203823427 小时，原起点 2026-10-13T23:48:56+00:00 保留，仅排除核验的纯资源排队。远端381条manifest条目全部SHA一致，canonical合同 `5b1b2e3dfa9f9d6a0ee1c8ef111924a910f18a75b1d9541a07d93caff37198e7`。观测时科研待排队 18、运行 0、完成 0、失败 0；GPU0–9全部为候选，按冻结显存容量规则共卡接纳，无自动重试、额外seed、候选、调参或下一轮。本记录仅为工程启动证据，无科学效果或Claim。权威记录：ai4s/programs/dbconformer/research/STATE.yaml、EVIDENCE_INDEX.yaml、scr_r1_repair1/STARTUP_STATUS.json。


### 2026-10-14 DSAINet RCD resume3 修复补跑
用户明确增加24h至累计48h，原起点/成本保留。旧Run自然排空后保留30个完整训练（原29加B0_s1_t0），仅补42个，全部72fit后72audit；原科研协议不变，单fit工程期限10800s，增加计费的训练前显存复核。Linux恢复/最终包/parser与独立Grok部署审查通过；官方上传、启动、probe已完成。22:02快照技术恢复PASS、screen RUNNING，首个新fit尚未核验；后续SSH直连/跳板连接失败，保持同Run不重投。详见 ai4s/programs/dsainet/research/dsa-rcd-v0.1-resume3/LAUNCH_RECORD.md。科学审计0/72，无科学Claim。


DSAINet RCD resume3启动核验追加（2026-10-14 22:07）：连接恢复，同Run首项S0_s0_t7在GPU6完成2/100epoch，显存预检与正GPU ACK通过；1运行/41待派/0失败，30继承训练完整，累计48h余额约26.79h。72审计仍等待全部fit闭合，无科学Claim；证据ai4s/programs/dsainet/research/dsa-rcd-v0.1-resume3/LAUNCH_RECEIPT.json。未重复提交。


## SCR-R1 部署续接 deploy2（2026-10-14）

用户授权在现有预算内放宽筛查时限、优化部署、保留训练并完成原18项科研闭集。两项旧技术训练导入PASS；来源四科研任务不重训：观测时2项完成、2项保留原PID继续运行，仅原14未开始项由新不可变Run `2026-10-14_dbconformer_scr_r1_deploy2_lab10_r1-full-w1` 派发。观测UTC 2026-10-14T14:16:37.473232+00:00，合计完成2、运行8、待运行8、失败0。原预算上限19.281203823426864小时、原起点与全部旧成本保留，新增预算0；旧source运行时与新队列重叠不抵扣纯资源排队。GPU0–9候选，按已核验完整原技术训练1,381MiB全进程画像容量接纳，同family不重复一项一项爬坡；零额外预留，允许共卡，OOM/实际失败按冻结规则停止而不新增训练重试。新续接screen限时13745秒，从新Run实际执行计算；旧源已执行成本不重置，原预算watchdog约束整体。deploy1因生产deque与JSON列表比较接口在派发前失败，科学fit0，已登记metadata-only INVALID并保留全部日志/合同/成本；deploy2原环境验收明确覆盖生产read_tasks重排deque、14闭集及篡改拒绝、技术2导入、跨Run队列保护和已完成C0仅source-valid CPU回放。55项共享CPU回归通过。正式远端409条manifest SHA全部一致。科学数据/seed0/100epoch/判门均未改变，未做完整verified intake、效果分析或Claim，不新增下一轮。权威记录为ai4s/programs/dbconformer/research/STATE.yaml、EVIDENCE_INDEX.yaml及scr_r1_deploy2/STARTUP_RECEIPT.json。


### SST-DPN ASR repair5 身份修复补跑（2026-10-15）

用户明确批准原3技术＋18科学在不增加预算下补跑。包内容量包装器、任务入口与合同身份已统一；Windows与Lab10 Linux完整实际派发链均通过全部21个真实子进程的数据读取前检查，原生Linux timeout/env/execv保留。最终包与已测运行源码逐字节一致。Run `2026-10-15_sstdpn_asr_r01_v0_1_repair5-full-w1` 已经上传、启动并probe核验，当前技术3待资源/0失败，科学18未释放；GPU空闲显存不足原4096MiB门槛，保持同Run等待。原模型/训练/矩阵/seed/技术门不变，单轮13h、累计55h与原起点/成本保留；停止区间已对账，远端CPU资格154.994秒仍计费，无自动后继补跑。repair4原冻结合同与零任务身份失败INVALID记录保留。本次为工程启动证据，真实CUDA门尚未通过，无科学Claim。权威记录为ai4s/programs/sstdpn/research/STATE.yaml、EVIDENCE_INDEX.yaml；本轮报告为ai4s/programs/sstdpn/research/asr-r01-v0.1-repair5/execution/DEPLOYMENT_REPORT.md。

### 2026-10-15 DSA-RCD-v0.1-resume3 回拉与结论
72训练/72审计已完整回拉并 verified intake。原30训练保留，42补跑完成。按冻结source-only筛查，P0=49.6624%、B0=52.2955%，P0-B0=-2.6331pp，P0-S0=-1.6879pp，P0-N0=-1.3792pp；主收益及风险门均失败，登记NO_SIGNAL并结束本精确实例，不自动补seed或续跑。没有单分支/移除分支对照，互补与专业化未检验。发现冻结分析器macro-F1分母错误，原值无效；同预测修正值单列，不影响准确率/NLL/Brier/kappa及门判定。核心验收和Grok专项复核为PASS_CORE_WITH_SECONDARY_METRIC_CORRECTION，非正式Claim审计。证据 AI4S-DSAINET-dsa-rcd-v0.1-resume3；完整报告 ai4s/programs/dsainet/research/dsa-rcd-v0.1-resume3/analysis_20261015/REPORT.md。


### SST-DPN ASR repair6 行序封印修复与技术复用（2026-10-15）

repair5 技术3项PASS，科学18项在训练前行序封印校验失败，已登记INVALID并保留原冻结合同和失败记录。按用户授权先对账停止后的预算，再核验41个技术资产文件及原身份/checkpoint/封印，复用3项技术产物，新增技术训练0；仅原18项科学训练进入repair6。科学封印生产者排序与训练消费者一致，原模型、训练、矩阵、seed和科学门不变。Lab10行序回归、技术复用及18子进程完整启动链通过，最终包源码与已测字节一致；Grok 4.6针对性部署外审PASS，完整trace保留。Run `2026-10-15_sstdpn_asr_r01_v0_1_repair6-full-w1` 已上传、启动、probe及远端manifest核验，技术复用节点PASS；截至13:15科学18待资源、0运行/完成/失败，各卡648–783MiB不足原4096MiB接纳门槛。单轮13h、累计55h及原成本保留，对账后可覆盖预算，本次新增0h；排队按原规则排除，不自动补跑。尚无新科学结果或Claim。权威记录为ai4s/programs/sstdpn/research/STATE.yaml和EVIDENCE_INDEX.yaml；报告ai4s/programs/sstdpn/research/asr-r01-v0.1-repair6/execution/DEPLOYMENT_REPORT.md。


### 2026-10-15 DSA-ORD-v0.1 设计完成，停止于实施前

按用户本轮“先完成设计，不启动实验”要求，提出完整公共token保留至加性读出、无序共激活S与反对称lag-1关系A的双支方案；不恢复已闭合RNS/CRU/RCD。七臂B0/GG/SA/SS/AA/从头U+S/从头U+A，并预登记同checkpoint的分别移除/同时移除；分阶段54+72fit仅为提案，阶段B需另行明确执行授权。Grok外审READY_WITH_LIMITATIONS，四项文案规格已补齐；结果只可能支持暴露开发面板内固定模型族的操作性互补，不是生理方向或信息论协同。无模型实施、Run或训练，旧48h预算不转移；Program State保持原结束/暂停。设计入口：ai4s/programs/dsainet/research/dsa-ord-v0.1/research_brief.md。


### SST-DPN ASR repair6 回拉分析与关闭（2026-10-15）

repair6原683文件完整回拉并verified intake；新科学18项全完成，原技术3项核验复用，无新增拟合。原Lab10单线程CPU消费者完成精确3+18、初始化/行序、checkpoint/双优化器/RNG及36次已存CUDA重放校验，独立复算通过。B0/R/C等权ACC分别55.9896%/56.1921%/56.5104%；R−B0=+0.202546pp，未达+1pp且seed1负，风险门通过；R−C=−0.318287pp，物理轴条件支持未建立。A/H均实际参与更新，按冻结规则登记NO_SIGNAL / NOT_ESTABLISHED，关闭当前精确ASR，Program COMPLETE_MAX_ROUNDS（第4轮），不救援式搜索或自动新增训练。开发目标已反复暴露，结果不作论文级泛化Claim，不与旧P跨轮拼配对结论。默认28线程初始化复核差异、JSON换行及登记身份字段兼容性均留原失败日志，按原生产线程/精确字节/仅补round_id处理，冻结代码/合同/科学门未改。预算增加0，旧成本与分析成本保留。证据AI4S-SSTDPN-asr-r01-v0.1-repair6；报告ai4s/programs/sstdpn/research/asr-r01-v0.1-repair6/analysis_20261015/REPORT.md；权威State、Evidence Index及repair6_decision.yaml已登记。

### SST-DPN NIF-v0.1 下一轮设计，尚未启动（2026-10-15）

ASR精确对象继续以NO_SIGNAL / NOT_ESTABLISHED关闭。基于ASR R−B0 +0.202546pp、ESF S−B0 0pp及P稳定性未复现，下一问题收敛为电极投影A与滤波混合H之间加入ELU，形成H ELU(AᵀX)，无dense旁路；区别于ASR的可折叠线性残差及ESF的纯线性分解。四臂B0/L/N/C分别负责宿主效用、同路径移除非线性、唯一候选和固定置乱控制。拟S02/S05/S08×seed0/1×4=24科学训练，另4项source-only技术检查；rank7、原训练配方和开发数据边界保持。N−B0、N−L、N−C分别设总体≥+1pp且各seed>0，主效用另要求每subject≥−3pp；控制不能救主效用，未过即关闭该精确实例，不自动补跑。

预算仅提案：Transaction17h、本轮含准备/分析18h；按上一轮10.784h余额快照建议累计55→63h（+8h），将来授权准备前重新对账。Grok 4.6设计外审DESIGN_READY，技术验收规格意见已补齐；这不是实施、GPU资格或训练许可。当前State/Evidence Index及旧源证据SHA均未变，仍第4/4轮、55h、paused，无active Run/operation；没有模型实施、新Run或fit。新机制仅有限开发检验，单置乱与尺度/优化混淆保留，不作新颖性或论文Claim。设计与审查入口：ai4s/programs/sstdpn/research/nif-r01-v0.1/research_brief.md、review/DISPOSITION.md、DESIGN_STATUS.json。

### D-215 - DBConformer FSC-R1 频带—空间表示设计（2026-10-15）

本轮仅设计。核对13条有效精确历史边界及8项主来源方法；SVE早期log-variance低于B0约1.138pp，SCR合并18科研的P1−B0/−C0为−1.312/−0.174pp，均不能外推全部频带或融合无效。FBCNet、IFNet、Dual-TSST、SSTAF已覆盖频带/双域叙事，因此只提出宿主内归因问题：替换channel_embedding为4–40Hz九组log-energy→源训练标准化→Linear(9,40)，保留原时间路径、空间Transformer/注意力汇聚和拼接头，恢复原B0采样与batch-local增强。B0检验整体替换，C0用同144bin/9×16、同计算与容量的分散频率分组，P1用连续4Hz分组；P1−B0混有696参数减少，P1−C0仅解释这一个固定分组比较，不证明普遍局部性或生理机制。

Grok4.6只读审查原裁决REVISE、6.8/10保留；初始化律、非原地描述符、Torch精度/stats保存、技术任务身份已补规格，未重评分。低新颖性与论文准备度仍是实质限制。未来20新fit（2 source-only技术＋18科研）仅提案，9旧B0条件复用未合格；运行画像和预算未定。联合ACC不证明互补，未来从头T-only/F-only另立范围和授权。设计登记仅改State.discovery导航及Evidence Index处置；SCR结论、全部历史证据、旧campaign/成本/预算、COMPLETE_MAX_ROUNDS及paused均保留，无active Run/operation、新fit或Claim。权威设计：ai4s/programs/dbconformer/research/discover_next_20261015_frequency_spatial/RESEARCH_BRIEF.md；审查与登记见同目录REVIEW_DISPOSITION.json、DESIGN_TRANSITION.json、REGISTRATION_VERIFICATION.json。

### SST-DPN NIF 第5轮：实现与工程验收完成，预算阻断（2026-10-15）

用户已批准24项科学训练＋4项技术检查，执行17h、单轮18h、累计63h、不自动补跑。四臂实现与Lab10无数据读取的28真实子进程链已通过；技术产物消费者、包外封印、固定判门、隔离冻结Bundle双节点校验通过。共享控制器最小NIF接入已应用并保留并行修改；共享启动120项（1跳过）、NIF控制器12项回归通过。Grok原REVISE保留，两项确定性工程字段问题经修复及主Agent回归验收关闭，未声称外审改判。

最新只读对账已计46.0424h，63h上限剩16.9576h，不足完整18h单轮；原起点、历史成本与已核验抵扣保留，未新增停止抵扣。尚无正式冻结Run、上传或训练；State仍原关闭/暂停状态，旧ASR及INVALID边界不变。建议仅累计上限63→65h（再增2h），尚未批准或应用，启动前仍须重新对账并核验正式包。没有新增科学证据或论文Claim。权威准备记录：ai4s/programs/sstdpn/research/nif-r01-v0.1/execution/PREPARATION_STATUS.json；报告：同目录PREPARATION_REPORT.md。
### SST-DPN NIF 第5轮：65小时授权后正式启动（2026-10-15）

用户已批准累计上限65h；24科学＋4技术、执行17h、单轮18h、不自动补跑不变。重新对账累计46.378h、剩18.622h，保留历史起点、成本及已核验抵扣，无新增停止抵扣。正式冻结包40项源依赖/42项清单文件及双节点入口核验通过，Lab10逐项字节一致。唯一Run `2026-10-15_sstdpn_nif_r01_v0_1-full-w1` 已启动；截至2026-10-15 19:22北京时间，技术节点 WAIT_FOR_RESOURCES，同Run排队，科学训练尚未开始，须4技术通过后执行24科学。保留原63h授权、ASR与INVALID记录；无新增科学证据或Claim。最新权威快照：ai4s/programs/sstdpn/research/nif-r01-v0.1/execution/LAUNCH_STATUS_65H.json；报告：同目录LAUNCH_REPORT_65H.md。上一准备报告为历史预算阻断时点，不代表当前启动状态。
### SST-DPN NIF 第5轮回拉与分析完成（2026-10-16）

同Run `2026-10-15_sstdpn_nif_r01_v0_1-full-w1` 完整回拉约690MB，1020项manifest产物通过，4技术＋24科学闭集完整。原Lab10环境冻结消费者完整验收通过，48次既有CUDA重放记录核验，24项预测correct数独立复算一致。本地Windows初始化再生成不一致的验收日志保留；只适配读取位置，在原环境复核，无改包/改门/重训。

N−B0 −0.3472pp（seed0 +0.1157、seed1 −0.8102），N−L −1.3310pp，N−C +1.7940pp。主效用与非线性门失败，轴对应条件门通过不能救主效用；冻结结论NO_SIGNAL、机制NOT_ESTABLISHED，无论文Claim、无事后晋级L/C。已登记AI4S-SSTDPN-nif-r01-v0.1并关闭精确实例，State COMPLETE_MAX_ROUNDS/paused，无active Run。新抵扣已核验结束后停止1.0997h；09:18北京时间累计已计50.9036h，65h上限余14.0964h，分析成本保留，余款不授权新轮次或补跑。详见 ai4s/programs/sstdpn/research/nif-r01-v0.1/analysis_20261016/REPORT.md。
### SST-DPN NIF关闭确认与FES下一轮设计（2026-10-17）

NIF第5轮精确实例维持NO_SIGNAL / NOT_ESTABLISHED：24科学＋4技术已完整核验，N−B0为−0.3472pp；原冻结合同、INVALID边界、历史成本和已暴露开发数据保留。本次幂等确认关闭，不重复应用旧决策。

下一问FES-v0.1：将跨9学习滤波器共享的电极基A[e,k]改为独立A[f,e,k]，固定rank7纯线性。B0/S/F/C四臂分别检验整体效用、增加复杂度、固定错组比较；S与NIF-L/ESF-S同架构类，不是独立验证旧L。F−S包含多1232参数与优化器状态拆分，不能孤立归因于解共享；F−C仅对这一条已暴露π及初始化成立。拟议24科学＋4技术，F−B0主门≥1pp，F−S投入门≥0.5pp，F−C≥1pp，均需各seed正向，主门另有单subject≥−3pp风险线。主效用失败关闭精确实例，辅助门不能救回候选。

完成纯代数核验及一次Grok4.6只读设计外审；原REVISE保留，身份/种子/双π封印和判读规格已修订，未声称外审改判通过。已有空间过滤先例、低原创性、小开发样本与顺序选择仍限制论文贡献，无新科学证据或Claim。

仅登记设计：State.discovery与Evidence Index.research_preparations已追加FES，其余状态/旧证据逐项比对不变；仍COMPLETE_MAX_ROUNDS、paused、第5/5轮、65h，无active Run/operation。拟议第6轮执行17h、单轮18h、自动补跑0；累计新上限须按合法重新对账后已计成本+18h另行批准，70h仅在已计成本≤52h时的条件例。当前只读快照未补停止抵扣为66.7003h，包含未对账闲置而非GPU新耗时，不视为今天已有可用余款。未实施正式模型、未技术拟合、未训练、未创建Run或增加预算。

权威入口：ai4s/programs/sstdpn/research/fes-r01-v0.1/research_brief.md；审查处置REVIEW_DISPOSITION.md；登记核验REGISTRATION_VERIFICATION.json。若后续授权实施，先做独立参数/真实优化器/初始化/完整消费者与Lab10启动链核验，再按新范围冻结；技术任务亦属未来授权范围。

### SST-DPN FES 第6轮：预算对账、冻结与Lab10启动（2026-10-17）

用户批准24项科学训练＋4项技术检查；仅工程失败任务最多补跑2次（每任务最多3次尝试），成功产物及所有失败日志保留，全部尝试计入执行17小时/单轮18小时。累计上限按本轮准备开始时已核验成本51.186131h＋18h一次确定为69.186131h，保留原campaign起点及历史成本，不滚动续额。

唯一Run：`2026-10-17_sstdpn_fes_r01_v0_1-full-w1`，Lab10经已核实的`[REDACTED_MACHINE]`连接。正式包40项SHA全部匹配，主进程和scheduler存活，4项技术门全部通过，科学节点已RUNNING；最后快照2项运行、22项待调度、0项科学完成/失败。31项Linux工程测试、28真实子进程入口、正式包命令/manifest/资源摘要核验通过，共享启动回归120项通过（1跳过），控制器6项通过。新增工程重试路径Grok终审PASS；前两次未完成外审保留，原设计REVISE及处置不改写。

启动后真实输出目录核验发现新增历史消费者多拼了node目录。原冻结包/合同/日志不改动；兼容修复仅位于`execution/compatibility_v1/`，改为正式RunRoot/scope.stage并仍委托原历史/日志/预算校验。该适配3项Lab10合成测试通过，不补训、不改变科学门；后续完整intake仍须在Lab10原torch1.13.1+cu116环境完成。

当前仅启动记录，无科学结论或paper claim。权威启动记录：`ai4s/programs/sstdpn/research/fes-r01-v0.1/execution/LAUNCH_STATUS.json`、`LAUNCH_REPORT.md`；监控入口`MONITOR_SAME_RUN.ps1`。


### D-216 DBConformer FSC-R1 联合核验与精确负结果（2026-10-17）

FSC-R1已合并原15项科研、补跑3项科研并保留2项技术训练，另独立复用9项旧B0。20项原环境CPU回放全部PASS；原汇总器被单项指标覆盖来源布尔位的错误已在独立派生层修复，30处角色位修正、20份逐任务回放及全部科学数值不变，原失败记录和冻包保留。真实产物正向核验、两项篡改反例及独立只读复核通过。

平均ACC：B0 58.1211%、C0 56.6937%、P1 54.9383%；P1−B0为−3.1829pp、P1−C0为−1.7554pp，正向人数2/9、5/9，最差−9.8958pp、−17.1875pp；两个比较全部冻结效用子门失败，possible-winner界不跨门。判定INSUFFICIENT_FREQUENCY_GROUPING_DUAL_UTILITY_SUPPORT，关闭固定九组连续频带log-energy直接替换空间前端的精确配方。

证据范围仅为已暴露9人seed0探索，不证明所有频谱表示无效、信息丢失因果或时间—频谱互补。下一步仅建议设计审查：保留原可学习电极波形前端，检验频谱辅助增量，配同容量分散频率控制及原B0；不为当前失败配方追加单分支18fit，不扫频带/窗口/seed/损失。未创建下一研究、Run、预算或Claim。

权威证据：AI4S-DBCONFORMER-FSC-R1-JOINT-20261017；决策ai4s/programs/dbconformer/research/dbconformer-fsc-r1-joint-closeout_decision.yaml；完整报告ai4s/programs/dbconformer/research/fsc_r1_repair1/joint_closure_20261017/REPORT.md。State已COMPLETE_MAX_ROUNDS（1/1）；旧失败Run整体不标verified，所有旧成本保留。

### 2026-10-17 SST-DPN FES 第6轮收尾完成

同一 Run `2026-10-17_sstdpn_fes_r01_v0_1-full-w1` 完成收尾导入修复、Grok 工程审查、24项科学＋4项技术产物完整核验及回拉分析；本次新增训练0次，原冻结合同和 FAILED 记录保留。独立重算24组预测正确数与7项门限一致。

F−B0 +0.058个百分点，主效用门失败；F−S +0.550个百分点，辅助复杂度门通过；F−C +0.666个百分点，条件机制门失败且跨seed不一致。决策 NO_SIGNAL，机制 NOT_ESTABLISHED，无论文 Claim，不提升S/C，也不否定整个结构分解方向。6/6轮达到上限，COMPLETE_MAX_ROUNDS / PAUSED，无活动 Run/operation，无自动后继训练。

截至2026-10-17 13:00:36北京时间，累计已计57.937038小时／上限69.186131小时，剩余11.249093小时；FES本轮已计6.750907小时／18小时，原训练执行3.504960小时／17小时。未增预算。

权威证据：`AI4S-SSTDPN-fes-r01-v0.1`；决策：`ai4s/programs/sstdpn/research/fes-r01-v0.1_decision.yaml`；[最终报告](ai4s/programs/sstdpn/research/fes-r01-v0.1/execution/closeout_repair1/resume_20261017/REPORT.md)。

### 2026-10-17 SST-DPN：FES关闭后的EFR设计（不启动训练）

FES第6轮NO_SIGNAL及6/6轮暂停边界保留。下一候选EFR-v0.1拟将约束从FES的“每滤波器48×22电极权重rank≤7”改到“每电极48×9学习滤波器权重rank≤3”；它仍是线性投影，与FES/SFP函数约束不同，不能从旧负结果推断会有效。

拟议B0/E/固定错组C三臂，S02/S05/S08×seed0/1，共18项科学＋3项source-only技术检查。E−B0回答效用，E−C只回答固定置乱下的条件分组增量；不做跨轮E−F配对推断，不提升旧控制，不形成论文Claim。当前仅合成代数核验和设计阅读复核，无生产实现、冻结合同、Run或训练。

预算提案：执行13小时、单轮17小时（含4小时准备收尾）、自动补跑0次；拟议累计上限为重新对账的已计成本＋17小时，当前规划约75.036小时，但停止区间抵扣及新增预算均未写入账本。原累计上限69.186131小时、max_rounds=6及paused均不变。

[研究简报](ai4s/programs/sstdpn/research/efr-r01-v0.1/research_brief.md)；[设计草案](ai4s/programs/sstdpn/research/efr-r01-v0.1/DESIGN_CONFIG.json)；[只读预算快照](ai4s/programs/sstdpn/research/efr-r01-v0.1/BUDGET_DESIGN_SNAPSHOT.json)。用户本次仅授权设计；第7轮实施与启动须另行明确范围和预算。


### D-217 DBConformer：保留原前端的频谱辅助设计审查（2026-10-17）

主审结论保留有限问题、修改对照与贡献表述，不直接进入训练。保留原逐电极可学习前端，在空间位置编码/Transformer之前加入九维描述子到40维的零初始化残差；固定相加、无新gate/损失/注意力，各辅助臂增加400参数。拟议B0、连续频带P、分散频点C、同频段时间能量C四臂，分别区分净效用、固定频率分组及一般能量辅助视图；时间控制不是纯容量控制，逆FFT计算量另行披露。

FSC精确替换负结果和旧IER“on/off贡献不等于胜独立B0”的边界保留。已有FBCNet、IFNet、Dual-TSST等先例，不把新增频谱路径/残差当作算法原创或已证实互补。当前仅开发探索设计；未实现、上传、训练、建Run或增加预算，Program原COMPLETE_MAX_ROUNDS/PAUSED不变。

如采用9人seed0并合格复用9项B0，四臂提案名义为27科研＋3技术=30项新fit，超出旧20-fit授权；未冻结、未测时，不继承旧预算。外审状态COMPLETE，原verdict=REVISE，以原始trace与处置记录为准。完整报告：ai4s/programs/dbconformer/research/design_review_20261017_spectral_aux/REPORT.md；处置：ai4s/programs/dbconformer/research/design_review_20261017_spectral_aux/REVIEW_DISPOSITION.json。


### D-218 DSAINet：ORD负结果后的原生路径与分支功能设计（2026-10-17）

ORD repair6完整54训练/54审计，SA−B0 −4.1088 pp、SA−GG +1.0995 pp；原NO_SIGNAL与旧阶段B停止边界保留。代码确认ORD替换了原生ConvTime/intra/inter与80维融合，保留U不等于保留B0判别函数；损失具体来源仍需新配对诊断。

新NFI-v0.1仅设计：D四臂区分独立读出权重、编码器整体包及读出随机正则；候选保留原生模块拓扑，在细支intra注意力混入0.10局部高斯核（sigma=2token），粗支保持全局内容注意力。配GG/LL同功能双支、角色交换、四个独立单支和GL组成的两个容量匹配单支，明确inter删除的系统包混淆。局部/全局先验已有先例，不宣称原创或已证实互补。

计划D72项后停止；条件F1新增54、F2新增108，名义总234训练/234审计另加待定技术验收，不一次派发。Grok原verdict REVISE已逐项处置，未声称最终外审ACCEPT或技术通过。没有实施/Run/新预算；原State COMPLETE_MAX_ROUNDS、paused及60小时旧账本不变。用户本次仅授权设计。

[完整设计](ai4s/programs/dsainet/research/dsa-nfi-v0.1/research_brief.md)；[设计状态](ai4s/programs/dsainet/research/dsa-nfi-v0.1/DESIGN_STATUS.json)；[外审处置](ai4s/programs/dsainet/research/dsa-nfi-v0.1/review/DISPOSITION.json)。


### D-219 SST-DPN EFR第7轮授权实施并在Lab10启动（2026-10-17）

用户批准18项科学训练＋3项source-only技术检查，执行13小时、整轮17小时、0自动补跑。停止区间对账后准备起点已计成本58.05685219347477小时，累计上限一次性固定为75.05685219347477小时；原campaign起点、历史费用、FES冻结合同和失败记录保留，准备成本计入17小时。

EFR逐电极rank3滤波器分解与配对初始化/100+30训练链已实现。原Lab10环境的合成入口、产物消费及父进程分类器核验通过；Grok原verdict REVISE保留，两项意见经活授权核验及工程夹具生产拒绝校验处置，未改写为外审PASS。正式冻结包和实际命令复核通过。

唯一Run `2026-10-17_sstdpn_efr_r01_v0_1-full-w1` 已在Lab10启动；全Bundle manifest哈希核验通过，3/3真实技术检查通过，科学节点RUNNING。启动快照为3运行、15待调度、0完成/失败，零重试。该快照不代表完整科学结果；后续须同Run回拉、完整性核验与分析，不自动补跑。

[启动记录](ai4s/programs/sstdpn/research/efr-r01-v0.1/execution/DEPLOYMENT_REPORT.json)；[实施验收](ai4s/programs/sstdpn/research/efr-r01-v0.1/execution/PREPARATION_REPORT.md)；[监控入口](ai4s/programs/sstdpn/research/efr-r01-v0.1/execution/MONITOR.ps1)。


### D-220 DBConformer FSA-R1：四臂生产准备完成、预算待批准（2026-10-17）

按用户选择实现保留原前端的连续频带P1、分散频点C0和同频段时间能量C1；独立旧B0保持只读。原初始化/数据/增强/训练/选模不变，各新臂增加400参数。本地42项、Lab10原环境CPU35项通过；当前46文件hash闭合。9项旧B0完成本轮独立回放，148项旧证据与原件一致。实际控制器与截获launcher/parser/resource接口通过，共享启动回归119通过、1跳过。

原生产Grok REVISE/high真实保留；两次增量调用无终裁，外部复审保持pending。按EXTERNAL_REVIEW第33条，明确工程修复由针对性回归与主Agent验收关闭，不声称外审改判，不将CPU/合成链冒充CUDA完整fit。计划3项完整source-only技术＋27项科研=30项新fit，三技术全部通过后才放行科研。预算建议从确认时追加26小时（技术2＋科研21＋准备收尾3），依据约36.65 GPU-worker小时、2个有效并发及未实测15%余量，非十卡空闲假设。准备原起点与全部旧成本保留；当前未授权预算、未建正式Run、未训练、未改State/Claim。后续必须明确授权、冻结最终包并复核，再执行技术门。

报告：ai4s/programs/dbconformer/research/fsa_r1/PREPARATION_REPORT.md；核验：ai4s/programs/dbconformer/research/fsa_r1/PREPARATION_VERIFICATION.json；预算：ai4s/programs/dbconformer/research/fsa_r1/BUDGET_PROPOSAL.json。


### D-221 DBConformer FSA-R1：26小时授权与同Run启动（2026-10-17）

用户已明确授权单轮3项完整source-only技术训练＋27项科研训练，9项旧B0复用；seed0、0自动重试、无新候选/调参/下一轮。确认时间20:11:04，保留19:23:28准备起点和确认前2856秒成本，新增26小时，累计上限26.793333333333333小时。旧FSC及更早campaign的费用、失败、证据和完整状态快照均保留；仅核验的纯资源排队扣除。

唯一Run `2026-10-17_dbconformer_fsa_r1_lab10_r1-full-w1` 已通过ccmu跳板在既有Lab10上传并启动。226份远端源文件及冻结合同哈希一致，3项技术训练实际GPU进程已核对：C0/GPU5、C1/GPU1、P1/GPU6；快照3运行、0失败，27项科研尚未放行。全部三技术门通过后由同一Transaction自动放行原27项；当前瞬时显存不作完整生命周期画像，无科学结果或Claim。

最终包真实命令/解析/资源策略、B0消费者及共享启动回归119通过1跳过；原外审与工程修复边界保持。启动报告：ai4s/programs/dbconformer/research/fsa_r1/STARTUP_REPORT.md；精确回执：ai4s/programs/dbconformer/research/fsa_r1/STARTUP_RECEIPT.json；预算授权：ai4s/programs/dbconformer/research/fsa_r1/BUDGET_AUTHORIZATION.json。


#### D-218 执行补记：NFI D 启动（2026-10-17）

用户明确授权 D 阶段实施/启动并给出新累计72小时，按实测和余额准入，自2026-10-17T11:54:34.956056+00:00起计准备成本；旧60小时不转入，仅扣执行器核验纯资源等待。冻结合同 ai4s/programs/dsainet/research/dsa-nfi-v0.1-D.yaml；Run `2026-10-17_dsainet_nfi_v0_1_D-full-w1`。最终r4本地/Linux各23项CPU验收通过、源码一致，Grok实现与登记增量审查完成并处置。已经ccmu跳板上传和启动，同Run probe证实smoke RUNNING及4项技术任务进程。4项技术fit/4audit及实测预算门通过后才能放行72项正式fit，全部fit闭合后72audit；F1/F2/旧B、额外seed、自动训练重试均不授权。当前不产生解码收益或互补claim；技术状态不替代科学结果。权威预算、State和验收记录见 research/STATE.yaml 与 research/dsa-nfi-v0.1/execution/PRELAUNCH_ACCEPTANCE.json。


NFI D 启动验收更新（2026-10-17 20:56）：同Run 4技术fit+4audit全部成功，GPU技术门PASS，实测预算门PASS；72正式fit已释放，快照4运行/68待派发/0失败，正式audit尚未开始。允许同卡按容量派发，GPU6承载3任务、GPU9承载1任务；各家族先低并发校准，完整正式任务结束后动态扩展。仅为运行验收，无科学效能结论；F1/F2/旧B保持禁用。快照：`ai4s/programs/dsainet/research/dsa-nfi-v0.1/execution/CURRENT_STATUS.json`。


#### D-218 NFI D收尾：仅分析接口修复与诊断登记（2026-10-18）

原72训练/72审计和4技术训练/4技术审计完整保留；新增训练/审计均0。1925项原始清单哈希、配对身份、全fit屏障、100轮min-select-NLL选择与独立指标重算通过。兼容层仅修Transaction完成状态格式，原合同/冻结源码/原产物均未改；6项回归及Grok条件复核完成。已通过真实apply-decision登记AI4S-DSAINET-dsa-nfi-v0.1-D，状态COMPLETE_MAX_ROUNDS，active_run/operation为空。

B0/Ntie/Utie/U40 ACC为48.3603/51.3021/48.1578/48.7172%；h=+2.9417、e=-3.1443、q=+0.5594、u=+0.3569 pp。q两seed为-0.8873/+2.0062，冻结处置D_ATTRIBUTION_UNRESOLVED_METRIC_OR_SEED_CONFLICT；未事后放宽简报与代码在seed冲突范围上的差异。U40平均损失未复现不等于等效/无损；编码器整体包有条件贡献，独立融合权重缺失不是已确立损失根因；未验证有效互补。F1/F2/旧B不启动。72小时原起点累计计时，收尾快照剩余约55.91小时，无新增预算/扣除。详见 `ai4s/programs/dsainet/research/dsa-nfi-v0.1/analysis_repair/RESULTS_REPORT.md`。

### D-219 补记：EFR 第7轮核验分析与关闭（2026-10-18）

同一 Run `2026-10-17_sstdpn_efr_r01_v0_1-full-w1` 的18项科学训练与3项技术产物完整核验通过；780个文件的原清单哈希、原Lab10环境验收和本地独立NPZ正确数／五门复算一致。无新增训练或补跑。首次逐文件回拉超时及共享工作区源码变化导致的登记拒绝均保留；使用同Run完整压缩包与原冻结包验证器完成标准intake及决策登记，未改冻结合同或共享代码。

判定NO_SIGNAL：E−B0 −1.678241pp，两个seed均负、S02 −3.645833pp；E−C +0.057870pp且seed方向不一致，五门均未通过。关闭精确EFR rank3实例，不救援rank／seed、不晋级C、不作跨轮E−F配对主张。仅为已暴露开发视图的阴性证据，无论文Claim。

Program 为 COMPLETE_MAX_ROUNDS / PAUSED，第7/7轮结束，无活动Run或operation。先对账停止区间，累计上限保持75.056852小时；最终记录时累计已计59.893596小时，剩余15.163256小时，本轮含准备／训练／收尾约1.836744小时，未超17小时。余额不授权下一轮。

[完整报告](ai4s/programs/sstdpn/research/efr-r01-v0.1/analysis_20261018/REPORT.md)；[最终核验与预算](ai4s/programs/sstdpn/research/efr-r01-v0.1/analysis_20261018/FINAL_RECONCILIATION.json)。证据ID：AI4S-SSTDPN-efr-r01-v0.1。


### D-221 补记：FSA-R1 联合核验与关闭（2026-10-18）

同Run `2026-10-17_dbconformer_fsa_r1_lab10_r1-full-w1` 的27项科研训练、3项完整技术训练及9项旧B0全部保留。原产物583文件、226份冻结源码闭包、35份回放报告哈希核验通过；Lab10原环境联合CPU回放39个checkpoint，本地冻结消费者与独立36行NPZ整数指标/四门重算一致。技术训练未读target且不入效应分母，9项旧B0不计新fit；此次新增fit为0。

B0/P1/C0/C1准确率为58.121142/57.908951/57.812500/56.385031%；P1−B0 −0.212191pp（4/9正向、最差−4.861111pp），P1−C0 +0.096451pp（5/9、最差−7.986111pp），前两组四门均失败；P1−C1 +1.523920pp且四门通过，不能抵消净效用不足。已通过真实apply-decision登记 `AI4S-DBCONFORMER-dbconformer-fsa-r1`，冻结结论 `INSUFFICIENT_SPECTRAL_AUXILIARY_UTILITY`，utility/attribution均false。Program为COMPLETE_MAX_ROUNDS / paused，active_run与active_operation均空，无正式Claim。

关闭连续九频组静态能量残差辅助配方，不调频带、不挑seed/受试者、不晋级对照。若继续，仅先设计“保留原前端及双分支的频带条件跨电极空间学习”，与跨频带共享空间权重及容量/计算匹配对照区分，先核对FBCNet/IFNet近邻。尚未创建新研究、实现或训练；本结果不证明频谱冗余或互补机制。原Grok REVISE及未完成增量审查保留，工程回归验收未冒充外审改判。

原起点与准备/历史成本保留，累计上限26.793333小时不变；收尾记录已计16.755771小时，剩余10.037562小时，仅扣核验资源排队13.082891秒，停机扣除0。余额不授权下一轮。

报告：`ai4s/programs/dbconformer/research/fsa_r1/joint_closure_20261018/REPORT.md`；最终核验：`ai4s/programs/dbconformer/research/fsa_r1/joint_closure_20261018/FINAL_RECONCILIATION.json`。此前FSA启动/待办由本收尾记录更新，历史原文保留。


#### D-218 后继设计：NFI-v0.2 同期训练路径拆分与原生功能偏置（2026-10-18）

用户仅授权设计。已只读对齐D/ORD源码、18对B0回执和90份已有预测；两轮B0数据/批次/归一化/torch一致，初始化流不同，t0/seed0选模51→1轮、审计差−41.84pp；旧GG/SA与D U40不是同一模型，历史损失未复现不构成等效或旧负结论撤销。q有5/9被试跨seed反号；80维双独立dropout、40维单mask、W/V的Adam更新与不同head初值同时变化，贡献仍未定。

新设计先Q0..Q4五臂同期90正式fit/90audit，另8短技术fit/audit；旧D端点仅描述，不进入新效应分母。初稿54项加旧端点复用方案经Grok条件审查后撤回，原稿/外审/trace保留。后继K以完整原生B0及独立80头为宿主，渐进软局部偏置；K1四臂108项、K2六单支/容量臂162项均为条件设计，含同功能、槽位交换和消息移除。选中偏置暴露不足停K2，不更改最低select NLL选模。未启动Q/K/F1/F2/旧B，未建campaign/Run或新增预算/Claim，State仍暂停。设计：`ai4s/programs/dsainet/research/dsa-nfi-v0.2/research_brief.md`；状态及审查处置见同目录DESIGN_STATUS.json和review/。

### D-219 后继设计：ASG 第8轮草案（2026-10-18，不启动训练）

EFR第7轮NO_SIGNAL及7/7暂停边界保留。拟议ASG-v0.1转向原SSA的tanh前logit，将电极×学习滤波器的门控分解为总均值、滤波器主效应和电极主效应；删除logit交互项，完整dense投影保留。与已关闭SFP/ESF/ASR/NIF/FES/EFR的静态权重分解或残差对象不同；不认为旧阴性证明SSA存在缺陷或本方案有效。

四臂B0原SSA、A对齐加性投影、C同秩固定错位投影、I移除SSA；拟议S02/S05/S08×seed0/1，共24科学＋4技术，100+30epoch。七组门分别回答宿主效用、受试者风险、条件轴分组及保留注意力相对删除的效用。C/I不事后晋级，已暴露开发身份与无论文Claim边界不变。

预算建议为执行17小时、全轮21小时、0自动补跑，累计上限将来按重新对账成本＋21小时申请（当前示意约80.97小时，未批准）。原上限75.056852小时及原执行范围保持；没有冻结Transaction、Run、Bundle、生产实现或远端操作。已完成纯代数检查及有界本地设计复核，接口文字问题已修正，这不替代GPU与完整启动链验收。

[研究简报](ai4s/programs/sstdpn/research/asg-r01-v0.1/research_brief.md)；[唯一数值草案](ai4s/programs/sstdpn/research/asg-r01-v0.1/DESIGN_CONFIG.json)；[只读预算](ai4s/programs/sstdpn/research/asg-r01-v0.1/BUDGET_DESIGN_SNAPSHOT.json)；[设计复核](ai4s/programs/sstdpn/research/asg-r01-v0.1/DESIGN_REVIEW.md)。


### D-221 后继设计：频带专属空间学习与三角对照（2026-10-18）

用户要求围绕频带专属跨电极空间学习继续设计，已核对FBCNet原文/作者代码、IFNet作者代码及近期多视图/动态频率近邻，并复核SVE/RCC/LRC/IER/FSC/FSA边界。收敛为一个四臂开发筛查草案：原B0；九频组各两个空间方向P；跨频带共享两个空间方向S；18个活跃方向作用宽带平均矩阵的等容量控制K。三辅助臂共同采用实交叉谱二次能量、18→40零初始化投影，只加原S池化摘要，完整保留原前端和双分支，不修原attention。

P/S/K空间参数396/44/396，投影均760，总参数94969/94617/94969。P−S改变共享方式也增加参数；P−K控制活跃参数和主要前向算子，但改变频率解析组织，不能单独证明纯解绑效应。主要MAC对齐不等于实测等训练计算；真实前后向时间/显存尚待生产验收。合成代数通过，不作为生产资格。没有加入分散组、对角项或完整分支重训，因此不主张频带连续局部性、交叉项唯一因果或独立互补。

Grok/xAI grok-4.6-build实际外审认为有限screen可接受（原文READY），方法论文原创性不足，原综合评分5.85/10；没有把它记为论文READY。wrapper退出73保护告警保留，真实轨迹仅7次白名单读取、无写/shell调用；未恢复并行改动，未指定其他写入者。主审补清初态同分布、梯度开放、数值界与解释范围，未冒称二次外审。

名义未来成本27科研＋3完整source-only技术＝30新fit，另条件复用9旧B0；尚无新运行画像或预算。当前仅设计登记，不建新研究/合同/Run、不上传、不训练、不转用FSA余额/授权。原State保持COMPLETE_MAX_ROUNDS/paused、active_run/operation为空，历史决定与费用未改。下一步仅在另有具体授权后进行生产准备、B0复用核验与预算测量。

设计入口：`ai4s/programs/dbconformer/research/design_20261018_band_spatial/REPORT.md`；完整简报：同目录`research_brief.md`；设计登记`DESIGN_TRANSITION.json`，最终核验`FINAL_VERIFICATION.json`。本记录不是实验效果证据或论文Claim。


### 2026-10-18 DSAINet Q启动授权落实

Q设计已按用户启动授权实施，冻结合同 `ai4s/programs/dsainet/research/dsa-nfi-v0.2-Q.yaml`；48小时新预算从04:50 UTC准备起点累计，不转入旧D余额。单轮90正式fit/90audit及8技术fit/audit；预算门同时包含5400秒fit、待审计数×300秒、3600秒收尾，实测预测另行准入。技术节点已启动，正式训练尚待技术门，不把CPU验收或外审条件意见当作GPU资格或科学结论。后续功能阶段和旧F1/F2/B不启动。

### D-219 补记：ASG 第8轮授权实施及技术失败（2026-10-18）

用户批准ASG第8轮24项科学训练＋4项技术检查，执行17小时、单轮21小时、无自动补跑。先对账历史成本60.05247393296825小时，累计上限固定81.05247393296824小时；所有实现、资格和收尾成本计入。保留EFR NO_SIGNAL与全部历史冻结合同/失败记录。

实现完成并通过原Linux CPU合成模型/训练、产物消费者和28项子进程链核验；Grok限定材料实现外审PASS与覆盖缺口分别记录。两次部署前打包/注册元数据拒绝已保留原冻结包，最终正式合同SHA-256为18ee09471bae93365d86da201b29feedc26eb1e8a2ff40eadb995f5afb0c3bcb。唯一Run `2026-10-18_sstdpn_asg_r01_v0_1-full-w1` 已在Lab10实际启动，远端完整清单哈希通过。

实际4项技术任务均attempt1失败，报 `ASG sealed source row IDs mismatch`，在首个epoch前阻断；24项科学训练未释放。技术父节点保留原行序而训练端按排序行序核验；排序的合成fixture未覆盖该差异。显存遥测OBSERVED，无OOM/超时，进程已结束。已暂停未来提交，没有修复补跑或修改已冻结字节。该失败不构成ASG科学阴性或任何论文claim。

09:24:56 UTC对账累计已计60.8999477716049小时，剩余20.152526161363298小时；保留全部准备/收尾耗时，不按远端时钟倒扣本地成本。停止后的空闲区间需下一次继续前独立对账。权威证据：`ai4s/programs/sstdpn/research/asg-r01-v0.1/execution/DEPLOYMENT_REPORT.json`、`FAILURE_LOGS.json`、`BUDGET_AFTER_FAILURE.json`。后续修复需单独授权新修订，当前不补跑。


### 2026-10-18 Q固定顺序归因关闭

Q1−Q0 +0.0579pp，Q2−Q1 −1.9387pp，Q3−Q2 +0.7234pp，Q4−Q3 +1.7168pp；仅Q2−Q1满足冻结继续核验尺度，seed1的NLL仍与ACC反向。Q4−Q3平均NLL恶化，不判稳定改善。端点seed0 −0.88735/seed1 +2.00617pp由不同幅度条件效应抵消；Q端点36格数值复现旧D，不增加独立随机样本。历史ORD和D结构/初始化/选择路径不等价，Q没有原生B0/SA/GG正式矩阵，唯一历史原因未定。保留原生能力约束，Q结束，不自动新seed或后续阶段。报告：`ai4s/programs/dsainet/research/dsa-nfi-v0.2/analysis/RESULTS_REPORT.md`。


### D-221 补记：BSP-R1 生产准备与预算建议（2026-10-18）

四臂生产实现已完成：P1频带专属空间能量、C0共享空间权重、C1宽带等可学习参数量对照，独立复用旧B0九项。保留原可学习前端及时间/空间分支联合训练；seed0、100epoch、batch32/增强后64、FP32和原划分不变。

Lab10生产CPU31项通过，207项源闭包前后SHA一致，旧B0九项source-valid/target原环境回放通过；共享启动回归120项通过（1项跳过），离线候选bundle与smoke/screen实际argv捕获通过，30项CapacityPool家族绑定通过。当前真实新fit **0/30**，未注册正式Run。

GPU固定首quartet的训练步中位数B0/P1/C0/C1约49.56/42.55/50.20/43.90ms，进程峰值1383/1371/1371/1371MiB。C0有外部共卡进程污染，完整保留原始标记；计算匹配未确认，不据此主张相对加速或算力相同，完整训练生命周期显存仍待3项TECH。未调整科学矩阵来缩小开销差。

建议新增28小时可用预算：技术上限2.5小时、科研上限22.5小时、准备/回拉/分析预留3小时。原起点2026-10-18T08:34:33.405665+00:00保留，批准时累计上限按已记账耗时+新增量设置；旧FSA预算不转入，旧成本/失败记录保留，仅核验的纯资源排队可扣除。允许GPU0–9、memory_only共卡，未知家族保守起步；3项完整source-only TECH全部通过后放行原27项科研训练，0重试/新seed/候选/调参/续轮。尚缺用户明确新增小时数，现有启动意图与上传授权不重复询问。

报告：[BSP-R1生产准备与预算](ai4s/programs/dbconformer/research/bsp_r1/PREPARATION_REPORT.md)；机器证据：[准备状态](ai4s/programs/dbconformer/research/bsp_r1/PREPARATION_STATUS.json)、[预算建议](ai4s/programs/dbconformer/research/bsp_r1/BUDGET_PROPOSAL.json)。该记录仅为工程准备，不构成科学结果或论文Claim。


### D-221 补记：BSP-R1 新增28小时授权与同Run启动（2026-10-18）

用户于2026-10-18T09:58:54+00:00确认新增28小时并启动已准备的单轮BSP-R1。保留准备起点2026-10-18T08:34:33.405665+00:00，确认时已计5060.594335秒（约1.405721小时），本轮累计上限29.405720648611112小时；旧FSA成本、记录与关闭边界保留，旧预算未转入，核验的纯资源排队不计。

正式合同canonical SHA-256 `1712d2fc73d36daa63f2e5cff2426e5675dd268b173a3573595245d69b8f4e94`，Run `2026-10-18_dbconformer_bsp_r1_lab10_r1-full-w1`。经ccmu跳板完成同包上传与同Run启动，远端245文件哈希全匹配；独立冻结包检查通过。核验时三项完整source-only技术训练均为第1次尝试：C0/GPU5/PID738447，C1/GPU1/PID738488，P1/GPU8/PID738700；三PID均与nvidia进程证据匹配，0完成、0失败。27项科研训练尚未派发，必须三TECH完整通过后内部放行；独立复用旧B0九项，0自动重试，不增seed/候选/调参/续轮。

允许GPU0–9、memory_only、max_jobs_per_gpu=null、reserve0、90°C、共卡及未知家族保守渐进准入。短时GPU观测仍受共卡干扰，不声称计算匹配或完整生命周期显存已验收。启动前辅助脚本字段/局部变量与preflight绑定错误已在派发前修正留痕，未改变科学配置或已验收核心源码。

状态以[启动核验](ai4s/programs/dbconformer/research/bsp_r1/STARTUP_RECEIPT.json)及Program State为准；[只读看板](ai4s/programs/dbconformer/research/bsp_r1/MONITOR.ps1)不读取中间效应。此时没有科研结果或论文Claim。


### 2026-10-18 DSA-LCB设计（未启动）

Q已完成，条件效应不等于历史唯一因果或互补；不扩大Q归因。新LCB只在完整原生B0的intra后/inter前加入固定无随机局部算子R=I-eL_path/4，e从0渐进至0.10，保留真实kernels[11,15]/[3,7]、原生80头与dropout。单次算子满秩不代表全网信息无损。LC1预设NN/SN/SS/NS/HH五臂135fit；HH匹配总系数，NS不得替代主候选。LC2另108fit验证两组成单支及宽单支，复制pool保留80头且披露单信息自由度；两阶段均待另行授权。原K/F1/F2/B未启动。完整设计与两轮外审：`ai4s/programs/dsainet/research/dsa-lcb-v0.1/research_brief.md`。


### 2026-10-18 DSA-LCB LC1执行授权与技术资格

LC1科研设计不变。按用户新48小时上限和实测/余额准入启动，未转入Q预算；技术资格6fit＋6audit均PASS，正式135fit已放行。部署修复只涉及LC1别名登记、容量预测等待、RAW审计载体状态校验；旧未部署包保留，新Run前缀LC1r2。全部135fit完成前禁止正式audit；本阶段结束停止，LC2仍须单独授权。技术通过不是解码收益或互补结论。外审及修复验收：`ai4s/programs/dsainet/research/dsa-lcb-v0.1/execution/review/DISPOSITION.md`。


### D-219 补记：ASG 第8轮 repair1 行序修复并启动（2026-10-19）

用户授权本次行序封印修复与补跑，保留原冻结合同及4项首epoch前技术失败。先核实停止区间并对账：准备起点已计60.909298237429724小时，累计上限固定为81.90929823742972小时，比原上限增加0.8568243044615258小时。执行17小时、整轮21小时（含准备与收尾），每任务最多1次，不自动补跑；仍属第8轮。

统一封印生成和校验的sorted_unique_int64行序，并核验实际phase2集合；6组subject×seed的全部100＋30科学epoch行序与原科学producer一致。Lab10七组工程检查通过，新增未排序四臂真实子进程合成闭环通过；六项治理测试通过。Grok 4.6集中外审CONDITIONAL PASS，随后正式冻结Bundle、资格回执与受保护恢复均通过。前两次外审因工具轮数上限未完成，其trace原样保留。

新Run `2026-10-19_sstdpn_asg_r01_v0_1_repair1-full-w1` 已在Lab10执行。快照：技术4/4通过、各attempt1，404优化步骤、无target评估；其后科学24项已释放，4运行、20待调度、0完成、0失败。远端冻结包逐文件哈希一致。该快照不构成科学结论；原ASG失败记录及EFR NO_SIGNAL保留。

记录：`ai4s/programs/sstdpn/research/asg-r01-v0.1-repair1/execution/DEPLOYMENT_REPORT.json`；监控：同目录`MONITOR.ps1`。启动记录时已计61.451836小时、余20.457462小时。后续按同Run检查、回拉、完整性核验，不重复提交。


### 2026-10-19 DSA-LCB LC1精确候选包关闭

依据已验证证据AI4S-DSAINET-dsa-lcb-v0.1-LC1，保留SN均值+1.4660pp和总体NLL改善事实，但其受试者索引0/4退步−7.6389/−6.1921pp；SN低于SS 0.1286pp、低于HH 1.9290pp。选中偏置暴露充分，不能归因于未进入偏置阶段。两分支钳制降低准确率却改善NLL，功能方向不跨seed一致，不能确认有效互补或稳定专业化。按预设规则关闭当前包，不替换NS、不补seed/调参、不进入LC2及旧F1/F2/B。具体设计约束与完整性证据见`ai4s/programs/dsainet/research/dsa-lcb-v0.1/RESULT_ANALYSIS.md`；不发布论文Claim。


### 2026-10-19 DSA-NRC：LC1后的冻结原生增量互补设计

用户仅授权分析与设计。LC1保存预测135项重新验哈希/配对重算：审计被试0/4在三个seed均退步；HH较SN三个seed均更优，SS均值优势微弱且也有局部伤害。SN移除分支后NLL改善主要来自双错样本真类概率回升，不能把统计来源当唯一结构/校准因果。旧LC1精确包仍关闭，LC2/F1/F2/B不启动。

新设计DSA-NRC-v0.1保留27个NN原生checkpoint完整eval输出与权重，两个新增修正支共同读取完整pre-pos token，以整段其余token上下文G、邻接上下文L生成每类总幅度不超过0.5的加性修正。关闭修正恢复B不等于启用后无伤害，保留逐被试−3pp及ACC/NLL门。首轮拟GL/GG/LL/G/L/GW/LW七臂、189轻量fit及189audit，含独立单支与近等容量单支；新增支互补不改写为原生两支专业化。温度只在select拟合、只用于次要解释，不能救援主NLL门。

设计简报：ai4s/programs/dsainet/research/dsa-nrc-v0.1/research_brief.md。Grok专项外审原裁决REVISE；pre-pos布局、80统计量、4类输出与epoch0表述已本地修订，完整trace及处置保留，不声称外审重新改判。仅DESIGN_COMPLETE_NO_RUN：无模型实施、新forward/训练/审计、远端调用、campaign或新预算；State原字节与旧产物保留，Evidence Index仅追加准备记录。


### D-221 补记：BSP-R1 联合核验与关闭（2026-10-19）

原23项SCI与repair4补跑4项已合并核验，3项完整TECH和9项旧B0保留。27个SCI checkpoint实际完成原环境CPU回放；TECH/B0复用原环境资格，36行原始预测由独立脚本重算，本地冻结分析与原环境分析除路径外一致。原始产物/904项冻结源/31份最终报告验签通过，全部SCI为100 epochs、11500 steps；本次回拉分析新增fit和预算均为0。历史失败/成本保留。

四臂B0/P1/C0/C1平均准确率为58.121142/57.947531/57.542438/57.310957%。P1−B0为−0.173611pp，4/9正向、最差−6.944444pp，四门全失败；P1−C0为+0.405093pp，只有正向人数门通过；P1−C1为+0.636574pp，只有均值门通过。真实apply-decision已登记 `AI4S-DBCONFORMER-dbconformer-bsp-r1-repair4`，结论 `INSUFFICIENT_BAND_SPATIAL_UTILITY`，utility/control support均false，Program COMPLETE_MAX_ROUNDS / paused，活动Run/operation为空。

停止本套频带专属跨电极空间能量残差辅助，不调频带、不挑seed/受试者、不自动晋级C0/C1。C0较P1少352参数，P1/C1等参数；计算匹配仍未确认。不外推为所有频带—空间方法失效或互补机制成立。下一设计须提出实质不同的表征使用/融合假设及区分本次池化摘要方案的对照；尚未新建或启动下一轮，没有正式Claim。

派生汇总最初因repair4基线模块同目录缺B0_REUSE_LOCAL而失败；27份已完成真实推理报告保留并验签复用。独立sidecar加载包内字节相同的原BSP基线模块恢复正确证据路径，冻结包/科学配置不变，未重训或重复整轮推理。旧Grok REVISE未改判。原计时起点与累计上限36.405721h保留，收尾记账25.675588h，剩余10.730132h；仅扣已核验排队45.237729秒，停机扣除0。余额不授权新实验。

报告：`ai4s/programs/dbconformer/research/bsp_r1_repair4/joint_closure_20261019/REPORT.md`；结果及来源：同目录 `RESULT_SUMMARY.json`、`FINAL_CROSS_VERIFICATION.json`。此前BSP启动/待分析记录由本收尾更新，历史原文保留。


### D-222 DBConformer：结束能量摘要残差配方，设计局部空间关系条件化时间路由（2026-10-19）

<!-- DBCONFORMER-SRT-DESIGN-20261019 -->
用户明确要求停止继续调整“空间能量池化＋残差辅助”。保留BSP/FSA/FSC全部结果、成本、INVALID与关闭边界，不调频带、方向数、seed或弱对照救援。BSP仍COMPLETE_MAX_ROUNDS/paused，活动Run/operation为空；不转入旧余额。

下一方向仅设计：局部电极相关状态形成8×8时间边偏置，作用于原时间attention的softmax之前；原Q/K/V、前端、两分支、池化与分类头保留并按原方案联合训练，无新的最终摘要内容残差。五臂为B0/P1/Cpow/Cpair/Ctime：原模型、原配对关系路由、功率路由、逐窗电极重标记关系路由、时间错位关系路由。Cpair保留每窗全部相关值/矩阵性质，检验跨窗同名电极对应，避免把231维与22维padding当信息等价。允许有符号gamma，不预设相似状态必须相互增强。

核对LI-DSN、MAtt、CorAtt、GBWAtt及Graphormer后，只保留宿主归纳偏置问题；不声称新attention原语、功能连接、原双分支互补或论文贡献。Grok 4.6限定材料外审原判REVISE，主agent修订控制与措辞，17项合成代数检查通过；未声称修订版再次外审通过，生产/RNG/GPU资格仍未完成。

拟定四新臂×9SCI＋4完整source-only TECH=40项新fit，另9项旧B0待复用重核；这是规模草案，不是40项实验授权。当前模型实施/上传/新fit/新Run/新campaign/新预算均0。下一实际工作仍需近邻源码逐接口核对、生产实现/验收、B0复核与实测预算；本次到设计交付停止。

简报：`ai4s/programs/dbconformer/research/discover_next_20261019_post_bsp/research_brief.md`；审查处置与完整trace、设计状态/登记回执在同目录。Evidence Index仅追加DISCOVER_NEXT/DESIGN_ONLY记录，State原SHA保持7fab2908836c0070873ac5d6111d05e2543cf1ef8d1fae3dbd8085816c9489c3。


### D-222 补记：SRT-R1 生产准备完成，新增数值预算待确认（2026-10-19）

<!-- DBCONFORMER-SRT-PREPARATION-20261019 -->
用户已要求按五臂40项新训练启动SRT-R1，并明确授权必要源码/B0证据上传Lab10做CPU验收、回放及合成GPU观测。原环境20/20 CPU检查、9项旧B0 source-valid/target独立回放、五臂两轮共10次合成GPU观测完成；最终候选Bundle的真实node argv、packaged parser/read_tasks闭集及check_bundle_commands通过，未创建训练子进程。原实现外审REVISE的身份字段和历史初始化摘要两缺陷已修复，跟进原判READY_FOR_BOUNDED_TECH；原报告与源码/trace/工程失败均保留。

实际宿主为DSAINet-main DBConformer SHA141c9c64，固定B0/P1/Cpow/Cpair/Ctime、4完整source-only TECH+36SCI、新fit上限40、独立旧B0九项、seed0/100epochs/原Adam与增强/FP32、0自动重试。当前真实新fit0/40，未注册/启动新Run；四TECH全部通过后才可放行原36SCI，不能把CPU/合成观测当完整TECH。

自身进程显存峰值B0 1381MiB、四新臂1383MiB，暂定每任务2560MiB；GPU0–9允许按显存共卡，不保证十路并行。工具支持FLOP计数新臂约+13.98%，Cpair多1项eye事件及共卡计时边界保留，严格计算匹配和全寿命VRAM未获资格。近邻源码有限核对不证明新颖性，LI-DSN仍PENDING_SOURCE。

建议从确认时起新增36小时（TECH节点4h、SCI节点30h、Transaction34h、回拉分析2h）。保留准备起点2026-10-19T12:38:01+00:00，记录时已计1.0819h；仅核验的纯资源排队可排除，本次准备扣除0。旧BSP预算不转入。当前新增数值预算仍未授权，Program State保留BSP关闭/paused，active Run/operation均空。

报告：`ai4s/programs/dbconformer/research/srt_r1/PREPARATION_REPORT.md`；机器状态、预算、CPU/B0、GPU和外审证据同目录。这里只登记工程准备，不给科研效用或论文Claim。


### D-222 补记：SRT-R1 新增36小时授权并启动（2026-10-19）

<!-- DBCONFORMER-SRT-STARTED-20261019 -->
用户于2026-10-19T13:44:00.425Z确认新增36小时启动单轮SRT-R1。原准备起点2026-10-19T12:38:01+00:00与已计3959.425秒保留，累计上限37.099840278h；旧BSP成本/关闭/余额边界保留，不转旧额度。仅核验纯资源排队可排除。

Run `2026-10-19_dbconformer_srt_r1_lab10_r1-full-w1` 已上传并被Lab10接受；远端238项源文件验签一致。当前4项完整source-only TECH在GPU4/5/8/9并行，0完成、0失败，自身进程显存各1385MiB；36SCI尚未开始，四TECH全通过后才放行。九项旧B0复用核验保留。固定40项新fit上限、seed0/100epochs/原科学配置、0自动重试、不增候选/调参/下一轮/Claim。启动记录仅1次，不重复提交。

原环境20项CPU验收、9项B0实际回放和10次合成GPU观测通过；完整TECH/全寿命显存与严格算力匹配尚未获资格。当前仅工程运行状态，不读取中间科研效果、不作效用判断。

报告：`ai4s/programs/dbconformer/research/srt_r1/STARTUP_REPORT.md`；机器授权/冻结/提交/PID证据见同目录STARTUP_RECORD.json及其引用。此记录更新此前预算待确认的准备状态，历史记录及绑定哈希保留。


### SST-DPN IPR-R1：v3.2 新单轮启动（2026-10-21）

<!-- SSTDPN-IPR-R1-LAUNCHED-20261021 -->
用户在收到设计后明确要求“设计并启动实验”。已按 L1/L2/L3 v3.2 建立唯一新 campaign `sstdpn-ipr-screen-20261021`，Run `2026-10-21_sstdpn_ipr_r01_v0_1-full-w1` 已上传并由 Lab10 接受；启动 probe 为 RUNNING，technical 节点等待资源。旧 ASG-stability 的 NO_SIGNAL 与旧 campaign 费用、种子曝光和 v3.1 合同保持原义。

本轮仅比较全程DPL（B）、第二阶段移除ICP辅助损失（R）、全程CE-only（Z）；S02–S09×seeds0/1共48项独立科学拟合，先过3项源域1+1技术门，科学固定100+30。33h执行/40h全轮、单次尝试、零自动补跑；S01排除，完整verified intake前不读科学效果。R−B和R−Z均按固定效用门判断，不救援或晋级Z。

本地部署回归124通过/1跳过，Lab10 CPU合成22/22通过，真实Torch1.13非空checkpoint在Torch2.7 CPU读取的模型/两优化器/RNG哈希一致。Grok原始REVISE保留；明确工程缺陷经局部回归修复，非外部改判。CPU资格和启动均不是科学证据，尚无本轮效用或论文Claim。

权威运行状态在 `ai4s/programs/sstdpn/research/STATE.yaml`；合同 `ai4s/programs/sstdpn/research/ipr-r01-v0.1.yaml`；启动与只读监控命令见 `ai4s/programs/sstdpn/research/ipr-r01-v0.1/execution/DEPLOYMENT_REPORT.md`。顶层摘要不授予后续Run权限。


### SST-DPN IPR-R1：verified NO_SIGNAL 结案（2026-10-22）

<!-- SSTDPN-IPR-R1-CLOSED-20261022 -->

48/48科学任务和3/3源域技术任务完成；完整verified intake与原环境消费者通过，独立整数复算一致。B/R/Z平均准确率59.1797%/57.9319%/55.6641%。R−B为−1.2478pp，两个seed均负，S05−3.6458pp；R−Z虽+2.2678pp但S05−4.6875pp，均未过冻结完整门。正式决定NO_SIGNAL / NO_IPR_UTILITY_STOP，停止当前阶段释放方案；无新增训练/补跑/下一轮/论文Claim，不能用R−Z或B−Z均值救援主比较。

本机初始化校验的运行时差异已保留失败证据，并在原Torch1.13单线程环境运行未修改consumer；未跳过标签屏障。报告：`ai4s/programs/sstdpn/research/ipr-r01-v0.1/analysis_20261022/REPORT.md`；权威State/Evidence Index已登记，旧启动与历史证据原样保留。


### D-223 DBConformer：设计简单分支辅助监督的收益复核与分配对照（2026-10-22）

<!-- DBCONFORMER-BAS-DESIGN-20261022 -->
用户要求根据BGC-A正信号设计下一轮研究。已验收证据 `AI4S-DBCONFORMER-dbconformer-bgc-r1-repair2` 中，A−B0描述均值+1.466049pp，5/9为正、最差−1.5625pp；旧主比较P对A/N未支持投影额外收益，旧冻结判断不变。A是事后选中的seed0线索，当前仅设计，不能视为独立确认或主论文Claim。

拟议BAS-R1仅B0/A×9被试×seeds1/2，固定旧split与100epoch配方，36SCI+2完整source-only TECH，上限38新fit；新seed runner须单独实施和验收。平均增益≥0.5pp、每seed平均>0、全部18配对最差≥−3pp才建议下一阶段。BAS-R2仅条件建议，另需启动授权：新增T(.5,0)/S(0,.5)的36SCI+2TECH并复用R1已验收B0/A，对比A(.25,.25)的固定总系数分配，不声称梯度强度匹配或互补机制。

每阶段建议24小时累计计费墙钟上限（纯资源排队仅凭证据扣除）；当前新增预算授权0、训练0，旧18小时BGC预算及累计成本不改、不转余额。State继续旧BGC关闭/paused，active Run/operation为空；没有新campaign或正式Claim。MSVTNet已有分支辅助监督先例，本轮首先作为训练基线研究。

权威设计：[research brief](ai4s/programs/dbconformer/research/bas_r1_design_20261022/research_brief.md)；来源哈希/配对重算：[DESIGN_RECORD](ai4s/programs/dbconformer/research/bas_r1_design_20261022/DESIGN_RECORD.json)；设计审查与处置见同目录review。当前研究理解：[CURRENT_UNDERSTANDING](ai4s/programs/dbconformer/research/CURRENT_UNDERSTANDING.md)。顶层记录不授予执行权限。


### SST-DPN IPR后下一问：SGR-R1设计（2026-10-22）

<!-- SSTDPN-SGR-R1-DESIGN-20261022 -->

IPR负结果后，建议检验真实源被试身份是否能改善CE训练风险分配，保留完整DPL、网络、BN、batch序与100+30开发配方。三臂为B混池宿主、G真实来源风险分组、P类/分区/组规模匹配的固定伪分组；S02–S09×seeds0/1共48项完整拟合，另3项source-only技术任务。G−B与G−P均须平均≥1pp、两seed均正、每被试≥−3pp。它是已知Group DRO思路的适配，非原创或已获支持主张；不救援IPR/SDC/ASG、不自动晋级P。

仅DISCOVER_NEXT/DESIGN_ONLY；拟单轮12h执行/16h全轮，未批准新预算、未建campaign/Run、未实现或训练。旧State仍COMPLETE_MAX_ROUNDS/paused，无活动Run；旧费用及曝光保持。完整方案 `ai4s/programs/sstdpn/research/sgr-r01-v0.1/research_brief.md`；稳定认识入口 `ai4s/programs/sstdpn/research/NEXT_RESEARCH.md`；证据索引登记为research_design_only。


#### D-223 执行授权与工程状态更新（2026-10-22）

用户已明确授权 BAS-R1 新增24小时、先2项完整source-only TECH再36项SCI，BAS-R2暂不启动。已建立独立单轮campaign，累计计时从08:53 UTC计入准备时间，不转移旧BGC预算或结果。新seed runner、原A等价/零权重、产物闭环/TECH阻断、分析器计数接口及最终工程包实际argv本地验收通过；启动回归124项通过（1项不适用跳过）。Grok关键源码摘录复核给出条件通过，远端CPU兼容性仍待验收。

自动审批拒绝向已登记lab-codex上传源码、配置及固定划分索引；当前未发包、未远端验收、未冻结正式BAS合同、未登记Run、未启动TECH/SCI。请求具体目的地确认，不以概括授权绕过审批。旧证据与费用保留。权威当前状态与待办见[READINESS](ai4s/programs/dbconformer/research/bas_r1/READINESS.json)及[APPROVAL_BLOCK](ai4s/programs/dbconformer/research/bas_r1/engineering_transport/APPROVAL_BLOCK.json)。


#### D-223 BAS-R1 派发核验（2026-10-22）

用户对lab-codex具体目的地回复“允许”后，工程镜像上传与SHA核验成功，Python3.9/Torch1.13真实模型CPU等价性、checkpoint读回、合成产物/TECH门控及实际argv全部PASS；共享启动回归124项通过（1项跳过）。正式合同及Bundle已冻结、上传，唯一Run `2026-10-22_dbconformer_bas_r1_lab10_r1-full-w1` 已启动；同Run probe为RUNNING/WAIT_FOR_RESOURCES，Program为WAITING_REMOTE。当前2TECH待资源，36SCI待TECH门控，BAS-R2不启动。

保持24h原累计起点2026-10-22T08:53Z，审批等待不作纯资源排队扣除。冻结前仅将执行上限收紧为14h（TECH4h、SCI10h），另留2h收尾；38项科学设计、种子、训练配置、门限及零重试不变。已确认其他Program有效显存预约造成当前等待，不清理预约或干涉其他任务。详见[启动记录](ai4s/programs/dbconformer/research/bas_r1/STARTUP_REPORT.md)。无新增科学结论。


## SSTDPN-SGR-R1-LAUNCHED-20261022

SGR-R1 已按用户“设计并启动实验”授权冻结并提交。保留完整 DPL，以 pooled CE / 真实源身份风险 CE / 计数匹配伪分组风险 CE 三组检验源身份作用；8 个开发被试 × 2 seeds × 3 组 = 48 科学训练，另有 3 项源域技术检查。执行 12h / campaign 16h，排队时间按合同排除，零自动重试。IPR-R1 负结果不改判。

Run：`2026-10-22_sstdpn_sgr_r01_v0_1-full-w1`。权威运行状态以 Program State 为准；启动记录见 [LAUNCH_REPORT](ai4s/programs/sstdpn/research/sgr-r01-v0.1/LAUNCH_REPORT.md)，证据登记见 Program Evidence Index。


BAS-R1收尾（2026-10-23，D-223）：2TECH+36SCI完整verified intake，冻结分析与独立36份预测数组重算一致。B0 57.9572%，A 56.1535%，A−B0 −1.8036pp；seed1 −1.6011pp、seed2 −2.0062pp，最差配对−8.8542pp，3/9被试正向，四道冻结门全部失败。seed0选题正信号未复现，停止当前固定辅助监督配方；BAS-R2前置门未满足，不启动、不追加seed/lambda搜索救援。结果仅限定当前暴露数据及固定配方，不否定所有辅助监督。证据AI4S-DBCONFORMER-dbconformer-bas-r1，决策BAS_R1_FIXED_AUX_BENEFIT_NOT_SUPPORTED_STOP，State已COMPLETE_MAX_ROUNDS/paused，无活动Run/operation，无Claim释放。报告：[RESULTS_REPORT](ai4s/programs/dbconformer/research/bas_r1/RESULTS_REPORT.md)。


## SGR-R1-CLOSEOUT-20261023

SGR-R1 同一 Run 的 3 项技术检查和 48 项科学训练完整回拉验真，冻结消费者与独立整数复算一致：B 59.1797%，G 57.1289%，P 59.2448%；G−B −2.0508pp，G−P −2.1159pp，六项冻结门全部失败。结论 NO_SIGNAL / NO_SGR_UTILITY_STOP；关闭当前固定真实源分组 CE 风险适配，不调η、换seed、删被试或补跑救援。机制未建立，无新增论文 Claim。S05 局部改善不能救援跨被试退化。

报告：[SGR-R1 回拉分析](ai4s/programs/sstdpn/research/sgr-r01-v0.1/analysis_20261023/REPORT.md)。运行状态以 Program State、证据以 Evidence Index 为准。未启动后继实验。

## FTA-R1-DESIGN-20261023

SGR 完整负结果后，下一轮推荐固定训练尾段平均，作为强宿主基线检查：完整DPL训练不变，phase2 epochs21–30十快照；16条科学训练轨迹派生B原生末端、N同校准末端、A参数平均、E概率集成共64视图。A−B及A−N分别须均值≥1pp、两个seed均正、每被试≥−3pp，六门全过才继续。E和N只作控制，不单独晋级；不通过则关闭固定配方并暂停无新依据的模块搜索。已知SWA/SWAD思想的适配不作为原创主方法或论文Claim。

仅 DESIGN_ONLY；拟议1项source-only技术fit，执行8h/全轮12h，尚未批准或启动，无新campaign/Run。详见 [FTA研究设计](ai4s/programs/sstdpn/research/fta-r01-v0.1/research_brief.md)。Program State保持SGR结案终态，设计登记于Evidence Index。


### D-224 DBConformer：BAS后转向有限结构删减筛查（2026-10-23）

依据BAS-R1固定辅助监督复核失败、BGC归因不完整、频谱/关系路线精确负结果及U0被RIDGE近邻收窄的历史，停止将额外模块作为默认下一步。拟议BNS-R1只检验完整B0(时间/空间Transformer深度2/2)与P(2/0)：两路卷积前端、位置编码、原池化、融合头均保留。它是结构取舍和简化基线筛查，不是已成立的新算法。CPU合成输入核对P参数减少42.04%，限定Conv/Linear/attention矩阵乘MAC减少14.28%，没有训练、准确率或实测延迟证据。

建议36SCI（2臂×9被试×seeds3/4）+2TECH，新16h累计预算待授权；C(0/2)的18SCI+1TECH仅在P过门后另行决定和授权，单独Transaction，不自动续接。新前瞻保留门为被试等权均值及每seed均值≥−0.5pp，全部18配对≥−3pp，参数/MAC削减≥30%/10%；是探索筛查，不是统计非劣效，也不回写BAS旧门。Grok设计原判REVISE保留，已补宿主绑定、静态资源核对、收窄机制措辞并条件化C；生产实现仍待后续验收。当前DESIGN_ONLY，State/Evidence Index/冻结合同不改，BAS-R2继续关闭，无Claim。详见[research brief](ai4s/programs/dbconformer/research/direction_reset_20261023/research_brief.md)。


#### D-224 BNS-R1授权实施并启动（2026-10-23）

用户明确确认新增16h、先工程验收后36SCI、BNS-R2不启动。已完成B0/P结构适配、原宿主B0 forward/gradient/Adam等价、保留初始化与数据随机流配对、本地及服务器CPU资格、9项合成产物/汇总/argv检查，Grok明确工程意见已逐条修复并保留原BLOCK与处置。独立DataLoader和增强fork_rng落实相同输入配对；forward dropout RNG允许不同，不与BAS旧轨迹混用。

唯一Run `2026-10-23_dbconformer_bns_r1_lab10_r1-full-w1` 已冻结、上传、启动并probe核验。当前2项source-only完整TECH在GPU运行，0失败，36SCI须待两项全部通过后自动执行；零自动重试。16h从实施准备时点累计，执行上限10h（TECH2h+SCI8h）另留2h收尾，原成本不重置。BNS-R2保持未授权，无中间效果读取或Claim。详见[启动报告](ai4s/programs/dbconformer/research/bns_r1/STARTUP_REPORT.md)。


## FTA-R1-LAUNCH-20261023

用户“启动实验”已授权并实际启动 SST-DPN FTA-R1；Run `2026-10-23_sstdpn_fta_r01_v0_1-full-w1` 已由远端接受，2026-10-23 12:14北京时间观察 source-only technical_S03_seed0 在GPU2运行、第1次尝试、失败0，科学阶段等待技术门。批准范围固定16条100+30轨迹/64个B-N-A-E视图+1条source-only技术轨迹，执行8h/campaign12h、单轮、自动重试0。S01排除，已曝光S02–S09仅开发证据，无新Claim。

原环境5组合成测试17项通过；共享launch回归124项（1项按条件跳过），最终Bundle双节点argv和manifest通过。Grok原REVISE及真实trace保留，具体工程项定点回归关闭，未宣称最终字节外部PASS。首次合同的seed饱和键登记格式错误在上传前被拒，原合同/包归档；仅移除不合法身份字段，训练源码、seed矩阵及科学判据未改。权威运行与证据入口仍为Program State/Evidence Index，旧SGR/IPR结论和成本不变。详见 [启动记录](ai4s/programs/sstdpn/research/fta-r01-v0.1/LAUNCH_REPORT.md)。


BNS-R1收尾（2026-10-23，D-224）：完整2TECH+36SCI回拉、manifest核验及verified intake通过，封存分析器逐项核验与独立36份预测数组重算一致。B0 56.7805%、P 57.0698%，P−B0 +0.2894pp；seed3 +0.9259pp、seed4 −0.3472pp，均值保留门通过；3/18配对越过−3pp风险线，最差−4.5139pp。参数减少42.04%、限定MAC减少14.28%不能抵消个体风险失败。决策BNS_R1_SIMPLIFICATION_SCREEN_FAIL_STOP，Evidence AI4S-DBCONFORMER-dbconformer-bns-r1，State已COMPLETE_MAX_ROUNDS/paused，无活动Run/operation或Claim。关闭固定2/0删减包，BNS-R2不启动，不以新seed/深度/阈值救援。建议暂停DBConformer新模块搜索；不外推整个模型家族无效。报告：[BNS-R1结果](ai4s/programs/dbconformer/research/bns_r1/RESULTS_REPORT.md)。


## FTA-R1-CLOSEOUT-20261023

FTA-R1已完整回拉、1746项manifest核验、verified intake及冻结消费者17轨迹/64视图闭集通过，独立64概率数组重算与六门完全一致。B/N/A/E平均ACC分别59.1797/59.4184/60.8181/61.0786%；A−B +1.6385pp、A−N +1.3997pp，两比较六道冻结门全部通过。S03/S09仍负向，但未越过被试两seed均值−3pp线。E/N为描述性，不能自动成为新候选；A−N通过仅支持完整平均适配超出单独校准的开发效用，不证明平坦性或新颖性。

Grok独立结果复核原裁决ACCEPT_WITH_LIMITS，真实模型/trace和实际覆盖限制保留。包装器退出73来自并发BNS结案对保护文档的追加；FTA40冻结依赖和原始分析哈希无变化，未还原并发记录、未把73改成0。审查未从160快照重新构造平均或重新前向；原实验已有落盘模型两次新进程回放。

官方决策SCREEN_POSITIVE / FIXED_TAIL_AVERAGING_DEVELOPMENT_SUPPORT；证据AI4S-SSTDPN-fta-r01-v0.1，State为COMPLETE_MAX_ROUNDS/paused，无活动Run/operation。实际执行1.7217h/8h，结案campaign计费9.8385h/12h，预算未增加。保留FTA为待确认强宿主候选，后续主方法不应只与较弱原生B比较；下一项应先设计合法独立确认和基线比较边界。已曝光S02–S09/seed0/1不是最终验证，未读取S01或释放论文Claim，未启动后继实验。旧SGR/IPR精确负结果与成本不变。

详见[FTA回拉分析](ai4s/programs/sstdpn/research/fta-r01-v0.1/analysis_20261023/REPORT.md)；当前认识以[SST-DPN研究总览](ai4s/programs/sstdpn/research/NEXT_RESEARCH.md)为入口，原设计与启动摘要保留为历史时点。


## FTA-R2-DESIGN-20261023

根据用户进一步开发FTA的请求，已完成前瞻设计：固定R1的phase2 epoch21–30等权参数平均及source-only BN校准，S02–S09 × seed2/3/4，共24完整100+30训练、96个B/N/A/E视图，另1条source-only技术轨迹。唯一候选A；A−B/A−N各要求八人均值≥1pp、每seed均值>0、每人三seed均值≥−3pp，仅新批次判定，R1结果不合并救援。拟议执行8h/全轮12h、单轮、自动重试0，尚未授权或启动。

此轮检验固定配方的训练随机性，不是独立最终确认：seed2–4在其他研究中已曝光，S01继续排除，BNCI2014004开发/最终角色尚未核定。通过后才设计跨数据验证与强基线定位；失败停止固定配方升级，不追加seed/window/权重救援。FTA-R1正筛查、IPR/SGR负边界与累计成本保留，无正式Claim。方案 ai4s/programs/sstdpn/research/fta-r02-v0.1/research_brief.md；设计记录 SSTDPN-FTA-R2-DESIGN-20261023。State仍COMPLETE_MAX_ROUNDS/paused，无活动Run/operation。


## DBCONFORMER-SVS-DESIGN-20261023

用户要求综合历史重新规划、先不启动。BAS/BNS及其他精确关闭边界保持；继续暂停DBConformer新增模块搜索，完整2/2保留baseline。可选下一轮SVS-R1检验固定源被试验证配方：9名已曝光outer subjects×seeds3/4，共18条六源100epoch轨迹、R6/D6/F6三个checkpoint视图，另1条source-only TECH；建议新增12h预算，尚未授权。D6相对R6及固定epoch100均要求被试等权均值≥0.5pp、每seed均值>0、全部18对≥−3pp。任一不过停止，不加seed/验证排程救援。

只有R1完整核验且两比较同时通过，才另行决定SVS-R2完整八源B8的18SCI+1TECH及建议8h；R1单独不证明相对完整宿主净收益，R2不自动启动。验证池域组成/密度仍有混杂，结论限定固定配方，不称纯域隔离机制；源域选模已有先例，不包装主网络创新。九名被试未恢复独立最终评价资格。

Grok设计原判REVISE保留，已据意见分期、收窄解释并记录处置；本次没有训练、运行合同、上传、启动或Claim。State/Evidence Index/BNS冻结合同hash保持不变，仍paused且无活动Run/operation。完整方案：[SVS研究重评](ai4s/programs/dbconformer/research/reassessment_20261023_post_bns/research_brief.md)。

### D-225 DSAINet：激活v3.2，优先检验P0在当前开发协议的净效用（2026-10-23）

用户明确要求接入L1/L2/DSAINet L3 v3.2并设计下一轮。新工作默认链已激活为dsainet-transaction-v3.2；NRC1旧campaign维持v3.1及COMPLETED_WITH_BUDGET_DEVIATION，active_run/operation为空，旧预算不转入。现有激活测试17通过、1按条件跳过，激活阶段16个保护文件哈希不变。

本轮没有发现比既有P0更充分的新模块投入依据，优先P0-CUE-R1：原P0的Coarse-E/Fine-A DIRECT结构迁入当前cue后4秒、6fit/1select/1audit/1excluded开发协议，与原生B0及仅删inter的AA-DIRECT(S0)比较。拟三臂×seed0/1×九context，共54次100epoch完整拟合；不复用不同协议的旧P0/B0效果。待检验的是完整候选净效用，不是窗口因果效应、双支必要性或Coarse特异机制；AEL/BSU/CES/NRC1原判定及原样P0广泛跨数据稳定优效关闭边界保留。

当前仅DESIGN_ONLY，无新campaign、Run或实验授权。拟24小时总预算须先按实际生产成本确认再批准，不是耗时承诺。设计及限定外审处置见[research brief](ai4s/programs/dsainet/research/p0-cue-r1/research_brief.md)与[稳定研究总览](ai4s/programs/dsainet/research/CURRENT_UNDERSTANDING.md)；状态/证据以Program State/Evidence Index为准，无正式Claim。


## FTA-R2-LAUNCH-20261023

用户明确授权按照FTA-R2固定方案在lab10启动，执行8h、全轮12h。新campaign `sstdpn-fta-replication-20261023`、Run `2026-10-23_sstdpn_fta_r02_v0_1-full-w1`，S02–S09×seed2/3/4，24科学fit/96 B-N-A-E视图+1项source-only技术任务，单任务1次/自动重试0。冻结合同canonical SHA-256 `5731e6bf1c60d78f79c0c8d35cd9e0120e16eeffafa30af9f564cd3f20ab0105`。已上传并启动；首次probe为技术节点RUNNING、WAIT_FOR_RESOURCES，科学训练未开始。此为执行状态，不是科学效果。只读监控命令和预登记修复记录见 `ai4s/programs/sstdpn/research/fta-r02-v0.1/LAUNCH_REPORT.md`。R1与历史负结论及成本保持原边界。


## FTA-R2-TECHNICAL-FAILURE-20261023

同一Run `2026-10-23_sstdpn_fta_r02_v0_1-full-w1` 在技术节点第一次且唯一一次任务尝试后FAILED：冻结 `task_launcher.py` 保留R1阶段名，R2合同身份检查立即拒绝，子进程约0.234秒退出1；技术完成0、失败1，科学训练0。原始日志/调度记录已回拉至 `ai4s/programs/sstdpn/research/fta-r02-v0.1/execution/failed_run_remote/`，报告 `ai4s/programs/sstdpn/research/fta-r02-v0.1/TECHNICAL_FAILURE_20261023.md`。这是工程INVALID，不是FTA科学负结果。本地仅准备阶段常量修复候选并用同合同入口测试接受；冻结包、远端与原Run未改。一次尝试、自动重试0，未授权新修复Run，旧预算和成本保留。


## P0-CUE-R1-COST-STOP-20261023

用户已批准新增24小时及Lab10指定目录的源码/配置/固定划分上传启动。Run `2026-10-23_dsainet_p0_cue_r1-full-w1`已实际上传启动；B0/S0/P0三项单epoch源域TECH全部通过，峰值1739MiB。科学入口按冻结成本公式得到201495秒（55.971小时）保守串行等效上界，高于当时剩余83144秒（23.096小时）且高于科学节点72000秒上限，因此成本门BLOCK，54项科学fit及54项audit均未启动，自动重试0，无存活本Run进程。该上界不是预计实际墙钟耗时。

同Run停止元数据已回拉并核验哈希、独立重算成本。现有控制器登记`INVALID / verified_failure_metadata_only`、清除活动Run并暂停；准确原因是成本门拒绝派发，没有P0科学负结果或新Claim。保留原起点、累计成本、冻结包与历史边界。后续停止；继续须另行准备并授权新不可变执行修订，不能仅重发旧Run或追加预算绕过现有节点上限。详见[启动及停止记录](ai4s/programs/dsainet/research/p0-cue-r1/execution/STARTUP_REPORT.md)。本段更新此前D-225设计阶段状态。

## FTA-R2-REPAIR1-INTAKE-20261024
repair1 同一 Run 已完成并回拉，manifest 与 shared intake 验真通过；24/24科学 fit 执行成功。然而冻结技术证据 task_evidence 将 seed2 误记为 seed0，冻结分析在目标评分前触发身份硬门。已登记工程性 INVALID（AI4S-SSTDPN-fta-r02-v0.1-repair1），没有A−B/A−N结果、科学负结论或Claim；Program COMPLETE_MAX_ROUNDS/paused。见 ai4s/programs/sstdpn/research/fta-r02-v0.1-repair1/INTAKE_ANALYSIS_20261024.md。



## P0-CUE-R1-LIMIT72-COST-STOP-20261024

用户明确授权累计72h（新增48h）、科学节点60h、Lab10新目录和原起点保留。新Run `2026-10-24_dsainet_p0_cue_r1_limit72_r1-full-w1`已实际上传启动；3/3 TECH通过，首次尝试，峰值1733MiB。新的最慢单epoch完整进程耗时29.068783秒，冻结成本公式上界升至68.0588h，超过60h节点上限、约65.23h Transaction上限及当时剩余67.1410h，故成本门BLOCK，科学fit0/54、audit0/54、自动重试0。已回拉校验失败元数据、独立重算成本并登记INVALID/暂停，无存活本Run进程。72h累计上限、2026-10-23 21:28原起点、两个Run/成本及科学边界保留。不是P0科学负结果，无新Claim。停止后续派发；优先重新设计成本资格方法，不能靠反复加预算或重跑绕过门。详见[启动和停止报告](ai4s/programs/dsainet/research/p0-cue-r1-limit72-r1/execution/STARTUP_REPORT.md)。另纠正旧Run科学节点原合同为22h，前份摘要20h为叙述误差，旧冻结字节不改。

## FTA-R2-REPAIR2-LAUNCH-20261024

用户明确授权同一campaign累计16h、执行8h，原起点与日志/累计成本保留。已修复技术证据seed硬编码并通过实际CPU技术生产者/消费者闭环；新Run 2026-10-24_sstdpn_fta_r02_v0_1_repair2-full-w1 已在lab10启动。原24SCI/96视图+1TECH矩阵与判据不变，源INVALID产物不参与本轮决策。当前技术节点RUNNING，尚无新科学结论。详见 ai4s/programs/sstdpn/research/fta-r02-v0.1-repair2/LAUNCH_REPORT.md。



## P0-CUE-R1-COSTCAL-SCIENCE-LAUNCH-20261024

用户明确授权校准启动开销、每epoch和实际并发后修复并继续启动，保留72h、原起点、科学矩阵。新不可变Run `2026-10-24_dsainet_p0_cue_r1_costcal_r1-full-w1`已在Lab10上传启动。3臂各5epoch source-only TECH通过；完整进程固定项14.02–20.07秒，首epoch15.34–18.66秒，后续epoch最大12.43秒，技术引擎真实重叠3。新估计把固定项只计一次，保留1.5余量和2h收尾，未来并发收益抵扣0；串行等效保守上界31.423h，小于成本门时剩余66.855h和科学60h节点上限，成本门PASS。科学阶段RUNNING，已核实P0_s0_t4实际GPU4/PID154980/1735MiB；不称54项均已同时训练。54fit×100epoch、54屏障后audit、所有seed/划分/模型/科学门和0自动重试不变，累计72h及北京时间2026-10-23 21:28原起点、前两Run与成本全部保留。没有读取中间科学效果；须完整fetch/manifest核验/intake后再分析，无Claim。Grok原BLOCK与本地确定工程修复/验收分别保留，不伪造外审改判。报告及只读监控命令见[启动记录](ai4s/programs/dsainet/research/p0-cue-r1-costcal-r1/execution/LAUNCH_REPORT.md)。后续仅推进同一获准Run至冻结决策，不扩候选、seed或追加预算。

## FTA-R2-REPAIR2-NO-SIGNAL-20261024

同一repair2 Run已回拉，manifest/shared intake/25项生产者及96视图闭集全部验真，seed元数据修复通过。A−B=+1.3310pp、A−N=+1.2587pp；seed4分别−0.1519pp与−0.4557pp，两项均未通过各seed均值>0硬门，按冻结判据登记NO_SIGNAL（AI4S-SSTDPN-fta-r02-v0.1-repair2）。独立整数重算一致。保留FTA-R1正筛查，两个旧INVALID不纳入科学效果；不合并历史救援，不追加seed/窗口/权重或自动跨数据验证。Program COMPLETE_MAX_ROUNDS/paused，无活动Run；原起点和日志成本保留，决策时累计计入预算14.5626h/16h。完整报告 ai4s/programs/sstdpn/research/fta-r02-v0.1-repair2/INTAKE_ANALYSIS_20261024.md。


### D-226 MVCNet：激活v3.2，设计VCN-P1视图内归一化校正（2026-10-24）

按用户要求将新工作默认链切为mvcnet-transaction-v3.2。旧augmentation-readout campaign/repair2 Run保留v3.1精确绑定；远端NO_SIGNAL研究判定与标准本地intake未物化分别保留，State仍WAITING_REMOTE，未清空Run或启动新实验。

依据developmental历史和源码，下一辅助方向为VBR-R1：保留P1四bank，前瞻检验每bank内训练/推理统计差异的有界校正。B0/S0/N0/P0的2×2设计区分P1宿主增量与通用renorm效果，当前为known-mechanism adaptation，原创性和有效性未建立。拟72次完整拟合仅为设计，预算/seed/资产/执行与旧Run收尾待下一授权阶段处理，不继承旧余额。

权威入口：`ai4s/programs/mvcnet/research/CURRENT_UNDERSTANDING.md`、`ai4s/programs/mvcnet/research/vbr-r1/research_brief.md`；激活验证：`ai4s/_work/mvcnet_v32_activation_20261024/REPORT.md`。此摘要不授予训练、上传、启动或Claim权限。



## P0-CUE-R1-VERIFIED-NO-SIGNAL-20261024

用户要求回拉分析。当前Run `2026-10-24_dsainet_p0_cue_r1_costcal_r1-full-w1` 的1141文件manifest逐个核验、完整intake及54fit/54audit身份/100epoch/最小source-select NLL选模/全拟合屏障检查通过，独立54个NPZ重算一致。B0 ACC50.3665%、rawNLL1.456545；S0 ACC48.1964%、NLL1.374533；P0 ACC51.6590%、NLL1.526904。P0−B0 +1.2924pp（seed0/1 +2.1412/+0.4437pp），P0−S0 +3.4626pp（+4.5139/+2.4113pp）；均值与双seed方向门通过，但rawNLL差+0.070359/+0.152371均失败，最差受试者平均差−3.4722/−3.5590pp均低于−3pp。准确率收益保留，冻结投资规则必须两比较全部门同时通过，因此登记NO_SIGNAL，仅关闭该精确P0-CUE-R1当前开发协议净效用实例，不否认所有统计量/分支机制。已曝光开发数据，不作独立最终评价或正式Claim。

State已COMPLETE_MAX_ROUNDS/paused，无活动Run，72h/60h、北京时间2026-10-23 21:28原起点、前两次成本门停止和全部成本保留。没有补跑、阈值调整或新实验；不以追加seed、事后温度缩放、checkpoint改选或删除不利被试补救原判定。共享通用分类器不覆盖第二对照/NLL及inclusive harm边界，本研究精确适配器重放冻结分析后复用既有journal/index/state帮助函数登记，未修改共享控制器；五项边界反例检查通过。完整结果：[P0-CUE-R1回拉分析](ai4s/programs/dsainet/research/p0-cue-r1-costcal-r1/analysis/RESULTS_ZH.md)；认识变化见Program CURRENT_UNDERSTANDING。

## SST-DPN-FRR-R1-DESIGN-20261024

FTA-R2 repair2 已按冻结判据 NO_SIGNAL 收尾：平均正增益没有通过 seed4 门，FTA 固定配方停止升级，R1 正筛查和旧 INVALID/成本边界保留。下一轮完成 FRR-R1 设计：复用 repair2 的全部24个原生B末端模型（S02–S09×seed2/3/4），固定编码器及BN，仅比较原生ISP与一个固定源域ridge读出。拟议24科学+1技术轻量拟合、48科学视图、0新编码器训练，lab10执行2h/全轮6h，单轮零自动重试。三项R−B开发门为均值≥1pp、每seed>0、每被试三seed均值≥−3pp；失败关闭固定配置并暂停缺乏新依据的局部改造，成功只进入另立读出控制/合法验证方案。

本次 DESIGN_ONLY，未拟合/预测/上传/启动，State及旧合同不变；不形成正式Claim，旧预算不转用。方案：`ai4s/programs/sstdpn/research/frr-r01-v0.1/research_brief.md`；唯一未冻结配置：同目录 `DESIGN_CONFIG.json`；认识入口：`ai4s/programs/sstdpn/research/NEXT_RESEARCH.md`；Evidence Index登记 `SSTDPN-FRR-R1-DESIGN-20261024`。

## DBC-FCA-DESIGN-20261024

SVS-R1 repair2已完成核验，D6−R6 −3.3275pp、D6−F6 −2.7874pp，六门失败；SVS-R2关闭。综合BAS/BNS及历史边界，继续暂停DBConformer的clean局部模块/近邻配方搜索。当前无合格结构主方法。仅保留FCA-R1为有条件的基础性备选：接受每会话32个无标签目标校准trial的新任务后，完整2/2宿主比较无对齐/对角尺度/完整协方差，拟54 SCI+3 TECH、18h，均未授权或启动。它不是UEP零目标数据LOSO，也不填补结构原创性缺口。详见[重评与方案](ai4s/programs/dbconformer/research/reassessment_20261024_post_svs/research_brief.md)。旧14h及收尾超时记录保留；无新campaign/Run/Claim。


## P0-CUE-R2-LS010-DESIGN-20261024

用户要求根据本轮结果与历史证据继续改进P0并设计下一轮。新增只读预测分解核验54个NPZ：P0错误预测NLL及置信度较高，双方都错条目贡献较大的NLL恶化；这是描述性依据，未证明唯一原因。选择一次固定ε=0.10标签平滑训练适配，保留E/A-DIRECT结构；B0/S0同步使用LS，select/audit继续用硬标签raw NLL。逻辑矩阵3结构×2目标，资格成立时只读复用R1的54个CE单元，新训54个LS单元和54次audit，另3项5epoch技术拟合。四比较同时保留原ACC/seed/NLL/逐人风险门，不放宽R1规则。详见[研究方案](ai4s/programs/dsainet/research/p0-cue-r2/research_brief.md)。

当前仅设计和只读重分析：旧NO_SIGNAL、暂停State、72h累计上限及北京时间2026-10-23 21:28原起点保持；未创建campaign/Run、未上传或训练、未增加预算。设计的技术1h/科学36h/收尾4h为待实测及授权的阶段上限，不是新增41h额度，设计/实现成本另计。普通LS不构成原创创新，历史原样P0广泛优效主张继续关闭。

## SST-DPN-FRR-R1-STARTUP-FAILURE-20261024

FRR-R1已按用户授权建立单轮campaign并在lab10提交唯一Run `2026-10-24_sstdpn_frr_r01_v0_1-full-w1`，但technical节点在调度器动态capacity装载前失败；0技术/科学ridge拟合，0编码器训练，科学节点未启动。原日志、包、合同与成本保留，Program已暂停。另发现JSON/YAML指数数值装载导致合同canonical不一致，未伪造intake或科学决策。Grok第二次报告NO-GO，原始trace保留。隔离修复候选正完成针对性验收；原合同automatic_repairs=0，尚未重投，需新增一次工程修复授权并保留原2h执行/6h全轮起点和累计成本。报告：`ai4s/programs/sstdpn/research/frr-r01-v0.1/LAUNCH_REPORT.md`；这不是科学负结果或论文Claim。

#### D-226 VBR-R1实施与预算（2026-10-24）

用户要求完成实现资格、成本和旧Run收尾后启动完整训练，确认Lab10目的地，并委托主Agent判断预算。新独立累计上限200h（资格成本6h、科学与末端check188h、验收分析6h，纯资源等待不计）；拟194h Transaction预留，不转用旧余额。seed69/70四臂72fit+72check及18个七源开发划分已固定为草案；新合同/Bundle尚未冻结。

模块、原生runner、控制器独立家族已实现；局部/原生CPU、mock编排、本机GPU四臂非恒等BRN单步及9项控制器边界检查通过。限定Grok外审ACCEPT_WITH_LIMITS与本地处置分别保留。Lab10成本未测；旧222 checkpoint仍在逐文件补传，标准intake/原冻结重放/状态收尾的一次性续接器正在等待完整载荷。旧State仍WAITING_REMOTE，新科学fit0，未上传或启动VBR完整训练。权威进度：ai4s/programs/mvcnet/research/vbr-r1/execution/PROGRESS.md；不产生新Claim。


## DBC-FCA-R1-LAUNCH-20261024

用户明确接受有限无标签目标会话校准，授权FCA-R1新增18h，先可行性/工程验收和3项TECH，再54项SCI；FCA-R2不启动。完整2/2宿主B恒等/D对角/E完整协方差，9被试×seeds3/4，cal32/5%收缩、原100epochs及batch32固定。可行性、宿主等价、真实writer/validator/Transaction合成闭环和拒绝例通过；共享派发回归124通过1跳过。

唯一活动Run `2026-10-24_dbconformer_fca_r1_lab10_r1p2-full-w1` 已在既定lab-codex/ai4s-runs接收，启动快照3TECH排队、0真实拟合、0失败；54SCI尚未放行，须3TECH与实测成本门通过且保留2h收尾。原r1p1合同YAML/JSON数值身份不同，零attempt停止；新包仅序列化/运行身份变更，旧产物与成本保留，不解释为科学负结果。18h从北京时间2026-10-24 12:23:48计入准备及修复，零任务自动重试，不重置预算。Grok原判REVISE及逐项处置保留，不记外审READY。

这轮检验带校准强baseline价值，不建立结构原创性或正式Claim；旧BAS/BNS/SVS关闭边界保持。启动报告：`ai4s/programs/dbconformer/research/fca_r1/STARTUP_REPORT.md`；实际状态看Program STATE，同Run只读监控脚本：`ai4s/programs/dbconformer/research/fca_r1/MONITOR.ps1`。

## SST-DPN-FRR-R1-REPAIR-LAUNCH-20261024

用户明确授权工程修复后，FRR-R1补跑最终Run `2026-10-24_sstdpn_frr_r01_v0_1_repair1b-full-w1` 已在lab10启动，技术节点PASS，科学节点RUNNING。矩阵仍为S02–S09×seeds2/3/4的24次科学ridge拟合、48个B/R视图，另1次source-only技术ridge拟合，0编码器训练。原2h执行/6h全轮上限、2026-10-24T04:23:15Z起点、日志和累计成本均保留。repair1在通用capacity资源字段检查前退出（0任务、6.277914秒）；当前修订已用真实CapacityPool逐项验证25个冻结task。两次零任务启动故障不作科学负结果。本轮未查看中间效果、无科学Claim。报告：`ai4s/programs/sstdpn/research/frr-r01-v0.1-repair1b/LAUNCH_REPORT.md`。


## P0-CUE-R2-EXECUTION-20261024

用户明确授权实施并启动P0-CUE-R2，原72h累计及北京时间2026-10-23 21:28起点保留。旧CE54格的来源/数据/划分/批序/标准化及原Lab10环境初始化匹配通过。首次R2因封包授权SHA错配在训练前停止，登记INVALID并保留；packfix1纠正绑定，科学矩阵仍54 LS fit×100epoch及54屏障后audit、0自动科学重试。已上传启动TECH；科学由3项5epoch TECH、环境/损失身份及实测成本门自动控制。 记录：[执行状态](ai4s/programs/dsainet/research/p0-cue-r2-packfix1/execution/STARTUP_SNAPSHOT.json)。


2026-10-24 R2执行更新：旧CE54格资格及TECH3/3通过；packfix1在科学派发前因成本门停止，科学0/54。总保守上界40.100h含4h收尾，科学上界36.100h略超冻结36h。阶段预算消费者已在未部署packfix2修正并通过8项测试；科学37h/原72h原起点/41hTransaction提案待用户明确确认。失败按工程INVALID登记，未产生科学负结果。记录：ai4s/programs/dsainet/research/p0-cue-r2-packfix1/execution/LAUNCH_REPORT.md。


#### D-226 VBR-R1 首次派发与旧Run最终收尾（2026-10-24）

旧resume69-repair2的222 checkpoint及1137份manifest文件已完整校验，标准intake、原冻结分析重放和State/证据指针对齐完成，NO_SIGNAL保持不变；旧campaign在300h上限内以COMPLETE_MAX_ROUNDS归档。

VBR-R1按200h原起点完成冻结包与共享派发：唯一Run `2026-10-24_mvcnet_vbr_r1_lab10_r1-full-w1` 在source-import因缺少runtime导入路径而失败。已保留日志/合同/Bundle/成本并登记工程INVALID、暂停，无资格或科学拟合；Lab10成本仍未测，完整科学训练未启动。原离线接口PASS未覆盖真实source-import，不是目标机验收。

可变源码路径修复已通过真实CPU18划分回归，原失败包未改。一次修复Run草案保持矩阵/种子/科学门和200h累计起点，拟Transaction184h+分析6h；原合同automatic_retries=0，新增修复Run待一次明确授权及新包真实验收、预算复核，不自动重投。报告：`ai4s/programs/mvcnet/research/vbr-r1/execution/LAUNCH_REPORT.md`。不产生科学负结果或Claim。


## P0-CUE-R2-PACKFIX2-37H-AUTHORIZED-20261024

用户明确批准科学上限37h，保留原72h累计、北京时间2026-10-23 21:28起点、41h Transaction与实验矩阵。packfix2成本口径已修正并通过8项边界测试，最终载荷来源绑定通过，已在Lab10启动。当前TECH完成2/3、运行1、失败0；通过技术/成本门后自动开始54项100epoch科学fit及54屏障后audit。当前没有verified科学结果或Claim。旧Run/失败/成本均保留。记录：ai4s/programs/dsainet/research/p0-cue-r2-packfix2/execution/LAUNCH_REPORT.md。

## SST-DPN-FRR-R1-REPAIR1B-NO-SIGNAL-20261024

FRR-R1 repair1b完整回拉、manifest验真、verified intake和冻结分析已完成，按原判据登记NO_SIGNAL。24组B/R配对中，B准确率59.1291%、R为54.0943%，R−B=−5.0347pp；seed2/3/4均值−5.7943/−2.7344/−6.5755pp，最差S08三seed均值−9.4907pp，三门全部失败。独立保存数组重算、整数重算和控制器Fraction核对一致。关闭固定源域ridge完整读出包，暂停当前宿主缺乏新依据的局部改造；不外推为所有读出无效或编码器缺乏信息，历史FTA/IPR/SGR等边界保持。已曝光开发筛查，不形成正式论文Claim。

用户仅为同Run收尾追加预算6h至累计12h，2h执行、原2026-10-24T04:23:15Z起点、原失败日志/累计成本保留；本次新增拟合/实验均0。Program COMPLETE_MAX_ROUNDS/paused、无活动Run/operation，剩余额度不授权新Run。冻结合同、旧包和原分析不改；预算/FRR通用阈值注入兼容问题仅由有身份与反例检查的本地收尾适配器处理。结果和停止处置见 `ai4s/programs/sstdpn/research/frr-r01-v0.1-repair1b/INTAKE_ANALYSIS_20261024.md`，证据 `AI4S-SSTDPN-frr-r01-v0.1-repair1b`。


## VBR-R1-REPAIR1-AUTHORIZED-LAUNCHED-20261024

用户明确批准一次工程修复Run；实际已上传启动 `2026-10-24_mvcnet_vbr_r1_lab10_r1_repair1-full-w1`。目标Lab10真实source-import及18划分/数据/源码哈希通过；资格任务在GPU资源等待，0资格拟合、0科学fit，成本门待实测。四臂、seeds69/70、九outer、100epoch×50step/B64/FP32及科学门全部不变，原失败保持INVALID。200h累计起点2026-10-24T04:35:51Z不重置；实际180h Transaction+6h收尾预留，注册时余188.972h。当前同一远端Transaction仅在资格/成本PASS后继续72fit+seal+72check，无自动新Run。旧Run标准intake与NO_SIGNAL收尾已完成。报告：`ai4s/programs/mvcnet/research/vbr-r1/execution/REPAIR1_LAUNCH_REPORT.md`。当前没有科学结果或Claim。

## SST-DPN-HVR-R1-DESIGN-20261024

依据FRR-R1 repair1b三门失败和FTA/IPR/SGR/ASG/SFP等各自有效证据，暂停以SST-DPN为主创新载体的局部搜索，保留完整DPL原生B；不能从这些负结果推出所有读出/编码器无效或宿主已被别的方法淘汰。IPR已做全程CE-only Z，不再作为新方向重做。

完成HVR-R1条件性宿主价值复核设计：先核对合法开发资产身份，再在母项目确有宿主选择需求时，以固定DBConformer参考作唯一挑战者。S02–S09×seeds2/3/4，复用24个SST原生B单元，最多新增24科学D训练+1 source-only技术训练，两臂48视图，原7源成员/576目标行固定。新8h执行/12h全轮仅为提案，待成本准入及明确授权。D/S正反向三门决定转向建议、保留候选宿主或维持暂停，不自动加候选或救援；完整管线对照不作架构归因或正式Claim。

DBConformer当前另有活动fca_r1，须其合法收尾后重新核对；本次未切换Program、创建campaign、上传或启动实验，所有State及旧合同保持。研究方案：ai4s/programs/sstdpn/research/hvr-r01-v0.1/research_brief.md；证据SSTDPN-HVR-R1-DESIGN-20261024；Grok实际审查及处置见同目录review/REVIEW_DISPOSITION.md。


## SST-DPN-HOST-REASSESSMENT-20261025

用户明确不需要横向比较，其他模型 Program 并行推进。撤下 HVR-R1 下一步建议，原设计与外审仅作历史保留，不启动新比较或追加整理其他模型结果。仅按 SST-DPN 自身证据和实现重评：保留 Program/原生基线与已完成研究，暂停缺乏新依据的局部创新实验；尚无足以立即启动的下一轮方法，不推论所有研究空间已穷尽。 结构复核、原型阶段释放、源域风险适配、FTA 稳定性与固定 ridge 读出分别约束各自配置；未定位足以支撑新方法的因果瓶颈。重启须有实质不同且有新增依据的可证伪假设和能改变设计决定的对照，不以其他模型输赢为条件。

State 保持 COMPLETE_MAX_ROUNDS/paused，无活动 Run/operation；旧合同、起点、日志和累计成本不变，无新增拟合或预算。完整记录：`ai4s/programs/sstdpn/research/HOST_REASSESSMENT_20261025.md`；证据索引记录 `SSTDPN-HOST-REASSESSMENT-20261025`。


## SST-DPN-USER-PAUSE-20261025

用户已明确决定暂停 SST-DPN Program。共享控制器 stop 已登记 PAUSED_FOR_HUMAN/paused=true，next-action=PAUSED；无活动 Run、operation 或待续接任务。保留全部实验资产及历史科学/工程判定，不删除、移动或清理本地和远端产物，原起算点、运行控制、日志和累计成本不变。当前暂停局部创新投入，保留 Program 和原生基线；HVR 已撤下，不作横向比较。重启需有实质不同且有依据的可证伪问题、能改变决定的对照、合法数据角色及具体新执行授权，不依赖其他模型结果。

研究交接：`ai4s/programs/sstdpn/research/pause_20261025/REPORT.md`；资产导航：同目录 `ASSET_RETENTION_INDEX.json`；暂停回执：`PAUSE_RECEIPT.json`。外盘载荷未在本次重新验真，保留原归档清单与恢复入口。


## DBC-FCA-R1-REPAIR1-STARTUP-20261025

用户明确批准repair1新增24h、累计42h，原2026-10-24 12:23:48起点及全部成本保留；SCI8→24h、Transaction10→26h、guard120→1800s，TECH2h和收尾2h不变。源r1p2的B/D TECH完成，经修复validator按原合同和全部产物SHA核验可复用；只补1项TECH E及原54SCI，不重训B/D TECH。原E是CUDA分配前容量保护超时，未观察到OOM；另修复真实writer epochs整数与validator预期列表的读取兼容问题，原产物不改写。

Lab10 CPU完整混合来源闭环及最终122文件包/命令校验通过，0新真实拟合；Grok原判REVISE和逐项处置保留，不写外审READY。已先upload-only、最终检查，再独立启动Run `2026-10-24_dbconformer_fca_r1_repair1_lab10_r1-full-w1`。远端确认接收，启动快照新E排队1、运行/完成/失败均0，54SCI待E完整TECH、三臂配对和成本门放行。零自动重试，FCA-R2不启动。科学矩阵和判据不变，没有新科学效果或Claim；旧BAS/BNS/SVS关闭边界不变。

报告：`ai4s/programs/dbconformer/research/fca_r1_repair1/STARTUP_REPORT.md`；只读监控：同目录`MONITOR.ps1`。权威状态仍看Program STATE；收尾先检查累计预算，再verified intake及完整分析，不重置预算或追溯扣除停止成本。


## DBC-FCA-R1-REPAIR2-PROPOSAL-20261025

用户要求修复入场超时、保留结果并仅补失败/未执行；预算与时限变化先提方案。repair1在零活跃拟合时停止，原账本/资源时钟/结果及成本留存。由冻结清单、attempt历史、raw/checkpoint/预测等artifact SHA固定19项SCI保留、B_s3_seed3失败和34项未执行，补集35；3TECH复用，不新增TECH，不读效果作选择。入场DEFER原型4项回归通过，生产接入尚未完成，不把原型记为生产验收。

真实SCI最长7399.649s高于TECH2912.217s，35项按12波三并发、原1.25余量和120s附加成本的保守估计31.232h，超过原残余SCI17h23m34s。提出新增18h累计60h、补跑SCI34h/Transaction35h/收尾2h，原起点及旧成本不清零；当前42h授权仍原样，尚未批准扩额，未上传或启动repair2。科学矩阵/门槛不变，FCA-R2不启动，无新Claim。方案：ai4s/programs/dbconformer/research/fca_r1_repair2/RECOVERY_PLAN.md。


## P0-CUE-R2-PERFFIX1-QUEUED-20261025

packfix2三项TECH已完成但成本门阻断，科学fit/audit均0/54；已登记工程INVALID并保留旧日志/成本。新perffix1仅修复执行与观察：同卡默认线程/2线程各8批source-only数值资格→原三项5epoch TECH分段计时→原完整成本门→原54×100epoch科学fit及54屏障后audit。科学成本增加104.515h的96%来自稳态epoch项；现有历史遥测不足以断言资源竞争或线程为唯一原因。当前GPU空闲显存不足3072MiB，资格任务待资源，科学尚未开始。16项本地CPU检查及最终载荷/远端79文件manifest/源码绑定通过，不代表GPU数值资格通过。保留72h、2026-10-23 21:28+08原起点、SCI37h、Transaction41h、4h收尾、全部矩阵与旧CE54复用及旧Run；新包2h登记字段仅表示TECH准入，科学估计仍待实测。无新科学结果或Claim。记录：[诊断与启动报告](ai4s/programs/dsainet/research/p0-cue-r2-perffix1/LAUNCH_REPORT.md)。


## VBR-R1-REPAIR2-PACKFIX1-ENGINEERING-COST-STOP-20261025

repair1失败Run已正式INVALID收尾，保留并核验7项成功资格、OOM日志与全部累计成本。用户授权的独立Run `2026-10-25_mvcnet_vbr_r1_lab10_r1_repair2_packfix1-full-w1` 已在Lab10一次上传启动；目标source-import18/18与七项来源复用通过，只有P0-replica1待补测，当前GPU资源等待。新fit显存承诺8960MiB，B64/FP32/科学矩阵和门不变。200h原起点04:35:51Z不重置；当前约余179.391h。

按七项真实测量与冻结成本公式，完整矩阵的保守预测下界179.06544h，余额扣6h收尾约173.391h，科学阶段NO-GO。新Run用于完成唯一显存资格和真实成本记录；当前0完整科学fit，不能把工程启动说成完整训练启动。原未派发repair2候选因共享scheduler源码漂移被离线拦截并留档；packfix1已钉回原已核验调度器字节。报告：`ai4s/programs/mvcnet/research/vbr-r1/execution/REPAIR2_PACKFIX1_LAUNCH_REPORT.md`。本轮没有科学结果或Claim。


## FCA-R1-REPAIR2-STARTUP-20261025

FCA-R1 repair2已在lab-codex确认接收；生产来源复核22/22及真实成本门通过，35项SCI进入资源队列。启动快照pending/running/completed/failed=35/0/0/0。保留3TECH及19SCI，仅补失败B_s3_seed3与34项未执行；没有新效果分析或Claim，FCA-R2不启动。

按用户批准新增18小时，累计60小时，原2026-10-24T12:23:48.589375+08:00起点及全部历史成本保留，余额快照39.325小时；SCI34小时、Transaction35小时、收尾2小时。入场仍为3072MiB/5连续样本/1800秒；仅首CUDA前可核验容量不足允许最多3次零拟合退队，释放预约、冷却并避GPU120秒，训练开始后零自动重试。矩阵、seed、完整2/2宿主、训练配置、选模及效用门不变。

Lab10全量零拟合验收（真实来源22+合成35、完整54配对闭环）和最终499文件包检查通过；Grok原判REVISE及逐项处置/真实trace保留。修复fresh结果校验闭集和CPU重放线程环境，原始结果及数值SHA不改；初次回放失败、误归属诊断及其纠正记录均保留。报告：[FCA-R1 repair2启动记录](ai4s/programs/dbconformer/research/fca_r1_repair2/STARTUP_REPORT.md)。


## DSAINET-P0-CUE-R2-WAITFIX1-LAUNCH-20261025

按用户授权修复零GPU尝试资源等待仍超时的问题。perffix1已metadata-only登记工程INVALID，保留原5819.955s wall=2219.926s queue+3600.030s execution，不返还旧execution。新waitfix1对已确认纯资源等待的慢轮询保持真实队列心跳，未知/运行/派发边界关闭等待；同campaign旧2219.9257s合法queue以冻结合同/终止台账/hash验证后在科学预算消费者一致保留。原72h、2026-10-23 21:28+08起点、SCI37h、Tx41h、4h收尾、原54fit+54audit矩阵/判定/旧CE54复用/0科学重试保持。33项针对检查及共享launch124项（跳过1）通过；外审结果PASS，真实GPU资格/科学效果仍按实际Run记录，不能从离线检查推断。最新线程资格状态MISSING，科学成本状态MISSING，科学fit receipt 0/54、audit 0/54。记录：[waitfix1启动验收](ai4s/programs/dsainet/research/p0-cue-r2-waitfix1/LAUNCH_REPORT.md)。


## DSAINET-P0-CUE-R2-FINITEFIX1-LAUNCH-20261026

按用户“修复并补跑”授权，已将waitfix1成本阻断按工程INVALID保留，新finitefix1只合并梯度有限性诊断host同步，每参数bool改为统一bool，检查位置/范围及科学数学不变。旧49.663h仍BLOCK。CPU全runner数值回放、三条件资格/成本拒绝反例、双源queue及原等待时钟共41项检查通过，共享launch124项含1项条件跳过；限定Grok审查PASS，显式batched参数微调后4项相关回放复验通过。新Run已在Lab10启动并校验96文件/62绑定；当前资格状态MISSING，成本状态MISSING，科学fit/audit均0/54、0/54，当前前置pending1 running0。原72h/2026-10-23 21:28+08起点、37h SCI/41hTx/4h收尾、矩阵/旧CE54/0自动SCI重试保持，余额约21.96h。依次三条件同卡8批资格→3项5epoch TECH→原完整成本门；提速不够仍停止，无SCI结果或Claim。记录：[finitefix1启动报告](ai4s/programs/dsainet/research/p0-cue-r2-finitefix1/LAUNCH_REPORT.md)。


## DSAINET-P0-CUE-R2-FLATFIX1-LAUNCH-20261026

按用户“修复补跑”授权，finitefix1的TECH_S0反向cuDNN失败已用原始台账/日志登记工程INVALID，旧线程资格/B0/P0成功与所有费用保留；未证明原cuDNN根因为OOM。新flatfix1修复慢owner查询后健康值陈旧，并在CPU建模后、模型CUDA转移/训练前复核两次容量；仅当前dispatch真实短缺且无训练工件走既有资源延期，实际训练异常仍失败。梯度有限值诊断改同device/dtype flatten归约，科学数学/矩阵不变。55项定向CPU检查、launch124项（1项条件跳过）、实际技术门finite=False拒绝、最终三typed reader/1+3+54动态任务闭集与103文件69绑定验收通过。Grok完成限定审查并提出条件/风险，原报告未被改写为PASS；主Agent逐项以原冻结诊断行为及实际技术门核验处置，仅接受技术派发，SCI仍受原门。当前2026-10-26T11:21:06.382743+08:00：资格MISSING，TECH已完成0/3，成本MISSING，科学fit/audit 0/54、0/54；threadcheck pending1/running0/completed0/failed0。原72h/2026-10-23 21:28+08起点、SCI37h/Tx41h/4h收尾/0自动科学重试不变，快照余额约15.733h；三旧Run已验证queue20125.089646100998s保留，execution与停机无退款。后续同Run四条件各8批严格轨迹资格→原3×5epoch TECH→原完整成本门，全部通过才54×100fit及屏障后54audit，成本不足即停。记录：[flatfix1启动报告](ai4s/programs/dsainet/research/p0-cue-r2-flatfix1/LAUNCH_REPORT.md)。


## DBC-FCA-R1-REPAIR3-LAUNCH-20261026

2026-10-26T18:48:24.111432+08:00。FCA-R1 repair3 Run `2026-10-26_dbconformer_fca_r1_repair3_lab10_r1-full-w1` 已在lab-codex接收，启动核对状态`SOURCE_PASS_GPU_TECH_ACTIVE_OR_QUEUED`；节点{'smoke': 'PASS', 'qualification': 'RUNNING'}，SCI调度计数None。保留43项SCI和3项TECH，仅补失败1项及未执行10项SCI。用户批准新增5h、累计65h；原2026-10-24T12:23:48.589375+08:00起点和全部成本保留，SCI72469秒/Transaction75873秒/收尾2h不变。

真实GPU零优化器步数值TECH已PASS=False。该门使用gpu_training/3072MiB/2400秒，8项硬门通过前SCI保持阻断。源CPU完整性、最终接口及本地/服务器包核验通过；工程记录不释放科学Claim。完整54项verified intake后再分析，FCA-R2不启动。科学设计仍为原完整2/2宿主、B/D/E、seeds3/4、cal32/5%收缩、100epochs/batch32/FP32及原效用门。

权威状态与证据：[启动记录](ai4s/programs/dbconformer/research/fca_r1_repair3/STARTUP_REPORT.md)、[State](ai4s/programs/dbconformer/research/STATE.yaml)、[Evidence Index](ai4s/programs/dbconformer/research/EVIDENCE_INDEX.yaml)。


## DSAINET-P0-CUE-R2-TYPEFIX1-LAUNCH-20261026

按用户“修复并补跑”授权，已用父flatfix1真实Lab10资格记录复现GPU编号str/int误拒绝，严格解析0..9标准编号后通过；bool/float/越界/多卡/空白/别名、UUID/容量/温度/轨迹篡改继续拒绝。父四条件资格PASS和smoke前置失败原始台账保留并登记工程INVALID（TECH0/SCI0）。typefix1只改消费者类型规范与四源queue继承，训练代码/配置/矩阵/原72h与2026-10-23 21:28+08起点/SCI37h/Tx41h/4h收尾/0自动SCI重试不变。41项定向检查、实际driver动态1+3+54闭集、三typed reader、110文件76绑定通过并在Lab10启动；2026-10-26T23:09:06.629920+08:00资格MISSING、TECH0/3、成本MISSING、科学fit/audit 0/54/0/54，资格调度pending1/running0/completed0/failed0。快照余额4.702h含原4h收尾；四旧Run仅queue22884.703983783722s获核验排除，execution/stopped均0退款。新Run原资格→TECH→原完整成本门全部PASS才科学，余额不足即停；未扩大原外审覆盖或改写其风险意见。记录：[typefix1启动报告](ai4s/programs/dsainet/research/p0-cue-r2-typefix1/LAUNCH_REPORT.md)。


## DBC-FCA-R1-REPAIR4-LAUNCH-20261027

2026-10-27T01:30:57.202638+08:00：FCA-R1 repair4 已获lab-codex接收，状态 `SOURCE_INTEGRITY_RUNNING`，节点 `{'smoke': 'RUNNING'}`，真实GPU数值资格PASS=False，新SCI调度计数 `None`。原43 SCI与3 TECH保留，仅补原11 SCI；完整设计及训练计算路径未变。CPU源46项、最终包/启动命令/上传包核验通过；真实GPU资格仍由实际硬门判定，通过前SCI阻断，无新增科学结论。

用户批准新增6h累计71h，累计Transaction上限增加2400秒至128400秒；原起点与全部成本保留，历史执行52396.605188秒照扣，新Transaction仅76003秒、SCI72469秒、GPU TECH2400秒、收尾7200秒。仅old资格变体首CUDA前凭核验容量短缺凭证有限退队，第三次短缺终止、最多两次重排，总TECH时限不重置；CUDA后零自动重试。FCA-R2不启动。

依据：[启动与监控](ai4s/programs/dbconformer/research/fca_r1_repair4/STARTUP_REPORT.md)、[冻结合同](ai4s/programs/dbconformer/research/fca_r1_repair4/transaction_contract.yaml)。完整54项verified intake前不读取中途效果或释放Claim。


## DSAINET-S0-CUDNN-DIAGNOSIS-20261027

按用户要求完成S0 cuDNN诊断与未冻结执行修复候选，保留typefix1 B0/P0原成功checkpoint/receipt及旧Run，14文件4504876字节SHA逐一核验。旧S0确在backward失败，但原Lab10 Torch1.13/cuDNN8.3在空闲3230MiB时未改S0单batch前后向PASS；低显存小Conv1d同类错误与较高显存12小核PASS只支持资源敏感性，未唯一定位旧反向失败层。候选仅S0 fit使用无状态cuDNN canary预热→清理闲置缓存→原容量复核，不改参数/数据/batch/AMP/确定性，任何canary或live训练异常不转等待、不自动重试。6CPU分支及本地Torch2.7/cuDNN9两新进程原/新logits/66梯度/BN/CPU-CUDA RNG逐位一致；原环境严格A/B因NO_CAPACITY未验收。Grok外审未接受根因修复，原报告和后续本地意见处置保留，不写PASS。原72h/起点/37hSCI/41hTx/4h收尾/矩阵不变，未启动TECH/SCI或追加预算。截至2026-10-27T12:05:41.262049+08:00原时钟欠额6.908h；建议先追加14h总86h，仅S0资格/5epoch TECH和收尾，B0/P0不重训。完整54fit+54audit两臂下界40.717h含收尾；现时追加下界47.667h，50h仅规划且仍须S0完整成本及原37/41硬门。记录：[诊断报告](ai4s/programs/dsainet/research/p0-cue-r2-s0-cudnn-diagnosis/REPORT.md)。


## DSAINET-P0-CUE-R2-S0TECH1-LAUNCH-20261027

按用户追加14小时授权，总预算86h，原2026-10-23 21:28+08起点、B0/P0成功结果和所有旧Run保留。新不可变Run `2026-10-27_dsainet_p0_cue_r2_s0tech1-full-w1` 只允许原Lab10环境零更新独立进程A/B验收→S0资格（原/新各8步）→S0五epoch TECH→CPU完整成本核算；没有科学fit/audit入口，成本充足也不自动启动科学。旧54项科学矩阵仅作冻结参考。新合同canonical SHA `6f134af566aed6182fdf84eb92f4f1539ce0f32342c1b2c25ac4af1450b309eb`，远端148文件/114绑定与五旧Run queue27792.449894s核验通过；旧执行/停机退款0。最终打包原运行时85项CPU回归通过。本地验证不是原环境GPU验收。2026-10-27T13:33:38.098968+08:00验收MISSING、资格MISSING、S0 TECH完成epoch=None、成本MISSING，科学fit/audit=0/54与0/54；资源等待True，当时剩余5.662h含原4h收尾。首轮Grok外审完成但保留GPU/覆盖限制，补充审查cancelled未记通过；主Agent按实际代码/回归和显式用户范围批准工程硬门执行，不声称根因已证实或科研有效。详见[启动报告](ai4s/programs/dsainet/research/p0-cue-r2-s0tech1/LAUNCH_REPORT.md)。


## DSAINET-S0TECH1-TECHACCEPT1-CPU-RECOVERY-20261028

用户明确授权仅修TECH证据汇总、复用已完成S0并CPU成本核算；不重训/不启动科学。修复同时同步顶层与technical内full_process_memory/peak_memory_mib。原失败证据在原冻结runtime真实RED复现，修正派生副本通过task_evidence→emit_node_result→check_result，5项定向检查通过。原Run `2026-10-27_dsainet_p0_cue_r2_s0tech1-full-w1` 仍保持smoke FAILED，原记录/原证据/B0P0成功不改，另记TECH离线验收PASS。62文件4210677字节failed-Run forensic intake与远端逐项SHA闭合；148 Bundle文件/114绑定核验，S0 checkpoint、5epoch/540旧更新和B0P0各5epoch成功经来源/哈希验证，本次新增更新0。完整科学54fit×100epoch+54audit的原1.5倍保守上界为科学37.377498h，含4h收尾总41.377498h；独立CPU复算差0秒，SCI37h与Tx41h上限均超1358.994s；86h原预算及2026-10-23 21:28+08起点保持，核算时原时钟余额已负，不退款停机，不增加额度。成本状态BLOCK_NOT_AUTHORIZED，科学fit/audit仍0。证据：[CPU修复报告](ai4s/programs/dsainet/research/p0-cue-r2-s0tech1-techaccept1/REPORT.md)。

## DSAINET-P0-CUE-R2-SCIENCE1-DISPATCHFIX2-LAUNCH-20261028

按用户“核算后启动原矩阵”指令，累计预算86→140h（追加54h），科学阶段37→40h，Transaction 41→45h；保留2026-10-23 21:28+08原计时起点、旧Run和B0/P0/S0成功TECH/checkpoint，不重训TECH。原54fit×100epoch、全部fit封存后54audit保持。完整上界科学37.377498h、含原4h收尾41.377498h；远端成本门时最低累计134.142429h（至少追加48.142429h），140h方案余量5.857571h；未计未来并发折扣。旧7Run纯queue29156.063534s沿原规则排除，执行/停止退款0。新Run `2026-10-28_dsainet_p0_cue_r2_science1_dispatchfix2-full-w1` canonical `a1b78f460036d59ea71e8073b9b6116d6d7a25ccd03aee7a07ce10d990a0f7e4` 已上传启动；264 manifest/230源绑定核验、线程/TECH复用/profile/动态成本均PASS。2026-10-28 02:28+08科学节点RUNNING但等待GPU，pending54/running0/completed0/failed0，fit/audit receipt0，不声称已发生训练或取得科学结果。最终包CPU复用、真实预算消费者和54+54派发计划验收通过。先前packfix1因审计预留每项字段未包含1.5裕量、与总预留不一致，在首任务派发前失败；接口已修正，原总成本公式不变，旧52.038916秒执行照计。旧失败Run和本地元数据闭合失败包均保留，不更改历史。后续只核验同一Run，资源合格自动派发；门失败/到期停止。详见[启动与预算报告](ai4s/programs/dsainet/research/p0-cue-r2-science1-dispatchfix2/LAUNCH_REPORT.md)，本条仅工程状态，不增加论文科学claim。

## DSAINET-P0-CUE-R2-RECOVER53-LAUNCH-20261028

按用户明确授权修复资源等待退出码，只补B0_s0_t7并复用旧53项fit后54audit。旧dispatchfix2的FAILED/INVALID和旧Run全部保留；53项成功各100epoch/10800更新，原receipt/source identity/checkpoint字节、数据配置split与完整进程调度遥测分别核验，159项旧产物SHA闭合，checkpoint共110748600字节。原包装器75→1真实子进程RED已复现，改为0/75/普通错误码精确传递；审计等待同时修正为checkpoint.pt及hash验证，非法marker/篡改/真实错误仍失败。6项容量/预算反例与最终包真实CPU复用、53不通过54屏障、1fit+54audit实际argv与预算消费者验收通过。Grok首轮maxturns取消不记PASS；增量grok-4.6-build审查session01a18110-e88f-73c1-ab78-1e152b6d2d67无阻塞工程缺陷，非科学claim审计。

新不可变Run `2026-10-28_dsainet_p0_cue_r2_recover53-full-w1`，合同canonical SHA `1b19048a796f2a4366cc216c5d31b5c0145fc50af62c11b3ac31143464709006`，388 manifest/354源绑定远端核验通过。2026-10-28 14:00:58+08：旧TECH复用PASS、53fit复用PASS、实时成本PASS；唯一新fit B0_s0_t7在GPU5运行，pending0/running1/completed0/failed0；已物化53旧成功，audit0/54尚未启动，须54fit全成功屏障后执行。140h总预算、2026-10-23 21:28+08原起点、SCI40h/Tx45h/收尾4h保持；旧SCI10602.379933s及Tx10616.187847s显式carry扣减，8旧Run纯queue31049.708018s核验沿原规则排除，执行/停机退款0。当时总余额36.075324h；科学剩余37.029563h、Tx42.021429h（均含历史执行扣算）；剩余1fit+54audit成本上界2.115843h，含收尾6.115843h，CPU门另预留10min，无预算追加。后续仅probe同Run，硬门失败或到期停止，不自动重提或扩矩阵；此条仅工程恢复状态，不作科学效果结论。详见[修复与启动报告](ai4s/programs/dsainet/research/p0-cue-r2-recover53/LAUNCH_REPORT.md)。

## DSAINET-P0-CUE-R2-RECOVER53-REMOTE-ANALYSIS-CLOSEOUT-20261028

用户授权按最新规则完成远端分析与关键回拉。recover53冻结合同缺execution.result_transfer，沿原规则完成标准完整fetch→manifest verify→intake：788文件131312079字节，manifest SHA c0371f6c2a16f2c55a1b5e1851d00b39b6c6dcbbb0c91da39d0965a03658cc61；没有给旧合同补策略，也未把局部回传当全量intake。远端独立recover53-readout1目录CPU-only复算原四比较，复用53旧fit身份经receipt/checkpoint/原调度证明映射；未改旧回执、合同、checkpoint，不训练或forward。原R1 CE manifest 122b7739c8f0f2309c13e23867a589b0e939c06146fe0562e914f69d93144729保持只读。远端原规则适配结果与独立Numpy/Fraction一致，最大标量差2.78e-17；无checkpoint的关键证据集与完整输入全部判定完全一致。KEY_EVIDENCE.zip 5197032字节、486成员，SHA e55904ab15cdaf167aa9200c5838ed511d8a6ec5d1416e47d671e2199cb2cadb，含108份原预测、fit/audit回执、来源/屏障/manifest及核验回执、分析与独立复算脚本，原完整资产继续保留。

原冻结规则判定NO_SIGNAL：P0-LS相对B0-CE/S0-CE/B0-LS/S0-LS平均ACC差分别+5.2276/+7.3978/+4.2438/+1.6686pp、平均NLL均下降，但四比较在audit subject索引7均低于−3pp风险门；相对S0-LS另有seed0 −0.057870pp，未过严格正向门。P0-LS ACC55.5941%、NLL1.199346；自身LS−CE ACC+3.9352pp/NLL−0.327558；S0同配方ACC增益+5.7292pp，P0相对S0差中差−1.7940pp，不能将一般训练适配解释为P0结构机制。关闭当前固定ε=0.10实例，不改阈值、不删被试、不补seed挽救，不否定全部P0变体、不创建正式Claim。决定已写p0-cue-r2-recover53_decision.yaml/Evidence Index，State COMPLETE_MAX_ROUNDS、2/2、无活动Run；未自动启动后续实验。原140h/2026-10-23 21:28+08起点、40hSCI/45hTx/carry及旧Run保留，15:30核算总余额34.575928h，无预算增加。详见[中文分析](ai4s/programs/dsainet/research/p0-cue-r2-recover53/analysis_remote/RESULTS_ZH.md)和[关键产物包](ai4s/programs/dsainet/research/p0-cue-r2-recover53/analysis_remote/KEY_EVIDENCE.zip)。


## DSAINET-P0-CUE-R3-CVAR-DESIGN-20261028

按用户“评估P0后续方向、设计下一轮、先不启动”指令，仅完成设计。R1/R2的NO_SIGNAL保留：LS改善平均NLL但四锚点逐被试风险仍失败，P0对S0-LS的seed0方向失败。P0只保留一次有界结构检验的投入价值，不进入连续调参。建议唯一候选Coarse局部中心化方差/Fine原A，保持LS=.10及原训练/选择规则；旧CES的E对均值平方M不等于已测中心化方差。现有证据未定位均值漂移根因，方差层也不是新颖算子。拟18次100epoch新fit+18audit，旧R1/R2的90格须先核验复用资格；四锚点原门全部保持，再要求父模型平均ACC不降、NLL不升、逐人差不低于−3pp。任一投入约束失败则停止当前cue4谱系连续优化，所有历史关闭边界不变。详见[P0-CUE-R3-CVAR研究方案](ai4s/programs/dsainet/research/p0-cue-r3-cvar/research_brief.md)。

历史串行分项估计科学12.4592h，拟技术1h/科学13h/收尾4h，总18h为规划上限，尚非新模型实测或执行批准。原140h、2026-10-23 21:28+08起点、SCI40h/Tx45h/carry保留，不重置或追加预算。State仍COMPLETE_MAX_ROUNDS、暂停、2/2、无活动Run/operation；仅新增research preparation，无新campaign/合同/训练/远端实验调用。


## VBR-R1 repair3 授权与冻结准备（2026-10-28）

用户在275h具体预算/修复/8项资格复用/完整训练方案后明确“修复并补跑”。本轮据此承接同一campaign累计预算200→275h，原起点2026-10-24T04:35:51Z不变；修复attempt字段与真实单次历史核验，新增精确8TECH复用绑定，不重训资格，不用资格checkpoint初始化科学训练。原packfix1 INVALID及失败日志和累计成本保留。科学额度238h，因交接已计费31.10h，后继TX运行上限从建议最多239h下调237.25h，另留6h收尾，派发实时余额不足243.25h即停止；不增加275h总额。矩阵/seed/科学门/成本公式不变。后继计划round mvcnet-vbr-r1-screen-lab10-r1-repair3；授权ai4s/programs/mvcnet/research/vbr-r1/execution/repair3/AUTHORIZATION.json。本条是授权和准备，不代表完成验收或已启动。


## VBR-R1 repair3-packfix2 已启动（2026-10-28T18:41:55.184199+08:00）

用户“修复并补跑”授权下，同一campaign累计预算200→275h（+75h），起点2026-10-24T04:35:51Z保留。唯一新Run `2026-10-28_mvcnet_vbr_r1_lab10_r1_repair3_packfix2-full-w1` 已一次上传/启动并真实核验source18、8TECH只读复用及生产cost PASS。预测236.987060h，TX237.25h/科学额度238h/包外收尾6h；当前72train pending、0running/complete/failed，等待8960MiB；没有新资格GPU训练，没有科学结果。原矩阵/seed/科学门及所有INVALID/日志/成本保留。最终报告 `ai4s/programs/mvcnet/research/vbr-r1/execution/repair3/LAUNCH_REPORT.md`，看板同目录MONITOR.ps1。前两个本地候选保持未派发；登记路径错取旧合同及首次probe暂态均按同Run核对修复，无重复提交。


## DBC-CGB-R1-LAUNCH-20261028

用户明确“按CGB-R1设计并启动下一轮研究”。唯一Run `2026-10-28_dbconformer_cgb_r1_lab10_r1-full-w1` 已获lab-codex接收；2026-10-28 18:54+08快照为TECH节点源数据回放中，真实TECH0/3、SCI0/27。固定B/D/E×9、OAS切空间多类LR，复用FCA原54参照，零GPU训练。新增6h含准备、原起点18:00不重置、Transaction最多2h及收尾2h；3项真实CPU TECH及成本门通过后才运行27项SCI，零自动重试，FCA-R2/CGB-R2不启动。实际来源/数值/写出/标准core消费者与控制器拒绝例已验收；Grok原判READY_FOR_BOUNDED_EXECUTION，真实TECH不由合成夹具替代。FCA原FAIL_STOP、完整结果与82.67377071914012h成本保留。 详见[启动记录](ai4s/programs/dbconformer/research/cgb_r1/STARTUP_REPORT.md)。


## DSAINET-P0-CUE-R3-CVAR-LAUNCHED-20261028

用户随后明确要求设计并启动下一轮。按已交付唯一CVAR方案实施：只将P0的Coarse未中心化能量改为局部中心化方差，Fine A、DIRECT、LS=.10和科学判定门不变。新Run `2026-10-28_dsainet_p0_cue_r3_cvar-full-w1`，18项100epoch候选fit后18audit，复用90格合格旧对照。远端复用、新候选8batch资格、5epoch TECH和成本门全部PASS，科学训练已开始。原140h总预算、2026-10-23 21:28+08起点、旧40h/45h谱系及实际用量不变；新轮1h技术/13h科学/18h Transaction（含4h收尾），仅max_rounds2→3，不追加预算。Grok原CHANGES_REQUIRED及终态账本修复验收保留。旧NO_SIGNAL和所有旧Run不改，当前不作科学结论。详见[启动与验收报告](ai4s/programs/dsainet/research/p0-cue-r3-cvar/LAUNCH_REPORT.md)。


## DBC-CGB-R1-CLOSEOUT-20261028

CGB-R1已完成3CPU TECH+27SCI，失败/未执行0；analysis_v1核心回传、正式intake、27项预测独立复算及controller再次重算均通过。固定几何G_B/G_D/G_E ACC为33.7457/35.3516/41.2760%，相对同臂FCA两参照seed平均差−23.0143/−23.1988/−19.0538pp；54/54配对低于−3pp，全部冻结保留门失败。决策CGB_R1_FIXED_REFERENCE_INSUFFICIENT_STOP，证据AI4S-DBCONFORMER-dbconformer-cgb-r1；State暂停且活动Run/operation清空，CGB-R2/FCA-R2不启动。原起点18:00、6h上限保留，收尾wall-clock约4.3837h，未追加预算；FCA原FAIL_STOP及成本均保留。 直接来源：[结果与处置](ai4s/programs/dbconformer/research/cgb_r1/RESULTS_REPORT.md)。


## DSAINET-P0-CUE-R3-CVAR-RECOVERED-ANALYSIS-20261028

已按用户授权在独立收尾接口中改用原合同绝对data_asset_path并核对资产SHA，18fit/18audit复验通过，原Bundle与FAILED账本不改。313份关键证据回拉并核验，18候选+90历史对照在远端完整输入和本地精简输入按原冻结数值门重算一致（浮点差小于3e-16）。CVAR ACC53.780864%、NLL1.229086；相对父P0-LS为−1.813272pp/+0.029740，最差逐人−15.972222pp，四对照风险门及父保留门全部失败。判定NO_SIGNAL_STOP_CUE4_CONTINUOUS_TUNING，停止该cue4连续优化，无后继实验。此为原失败Run资产的独立恢复复验/开发结果，standard_verified_intake=false，无正式Claim，不伪装原Run PASS。原预算、计时起点和旧结果保持；State3/3完成并暂停。[完整收尾与判读](ai4s/programs/dsainet/research/p0-cue-r3-cvar/closeout/REPORT.md)。


## DBC-POST-CGB-BCU-DESIGN-20261028

按用户要求仅设计后续方向。CGB固定宽带几何替换失败不证明架构优越；SGR源平衡/GroupDRO、SCR同源拼接及BAS/BNS/SVS等旧精确负边界保留。唯一展开的条件候选BCU-R1检验源会话cal32 bootstrap校准矩阵训练，部署端cal32/5%/确定E、原完整2/2宿主、split/100epoch/选模不变；拟C0 CovMix-cal32适配/P两臂×9被试×seeds3/4共36新SCI，最多2source-only TECH，原E18及B/D36仅在资格验证后复用。主要P−E0/P−C0需平均≥+0.5pp、各seed平均>0、每配对≥−3pp；另P对原B/D个体风险都须≥−3pp才可晋级。48h只是总预算情景，未批准；CovMix来源配方、旧源复用/检查点、真实TECH与成本仍是缺口。Grok原判READY_WITH_LIMITS只认可条件设计，不授予执行或Claim。当前零拟合/推理/派发，State仍暂停、无活动Run/operation；不启动BCU/FCA-R2/CGB-R2。 [研究方案及来源](ai4s/programs/dbconformer/research/reassessment_20261028_post_cgb/research_brief.md)。


## DSAINET-P0-PF-R1-DESIGN-20261029

用户在R3收尾后明确提出E/A分支概率融合方向，本次仅规划，不启动。R1的NLL/风险失败、R2的逐人风险和匹配S0 seed失败、R3的均值损失及风险转移仍保留；旧停止边界、140h原预算、原计时起点与旧Run记录不改。

以R2 P0-LS为母体保留E/A-DIRECT，唯一候选将拼接线性读出改为共享bias、固定系数2的两支等权概率平均。几何融合在同一dropout掩码下恢复旧头；新PF从头训练，因此只固定表征来源/定义，不声称训练后特征不变。拟1候选+AA-PF/EE-PF及独立E/A单支共5臂×9context×2seed=90fit/90audit，旧R1/R2的90格先重验复用资格。保留原四锚点和父P0保留门，另分层检验非对称结构、独立单支与双向贡献，差中差只作受限交互线索。单支少参数，概率平均也非新算法；任何结果均停止本轮，不自动搜索融合权重、温度、辅助loss或控制臂择优。

方案与实施前检查见[唯一research brief](ai4s/programs/dsainet/research/p0-pf-r1/research_brief.md)及[计划追踪](ai4s/programs/dsainet/research/p0-pf-r1/EXPERIMENT_TRACKER.md)。历史串行量级约62.30h科学预算，五臂TECH/实际并发和新成本门均未执行；旧余额不是新授权。当前没有新Run、训练、远端实验调用或正式Claim，State保持暂停。


## DBC-BCU-R1-PACKFIX1-LAUNCH-20261029

用户“启动实验”承接BCU-R1方案并确认48h总预算；起点仍为2026-10-29 01:07+08，准备/排队计入，旧FCA/CGB全部结果和成本保留。仅P/C0两臂×9被试×seed3/4的36SCI，先两项source-only 100epoch GPU TECH并通过实测成本门，零自动重试；FCA-R2/CGB-R2/BCU-R2不启动。

实际Run `2026-10-29_dbconformer_bcu_r1_packfix1_lab10_r1-full-w1` 已在lab-codex接受，smoke RUNNING；TECH_C0/P均已通过3072MiB/5样本guard及cuDNN+cuBLAS初始化进入GPU阶段，尚未完成TECH，SCI尚未开始。原R1仅在预派发包验收失败、0注册/派发/拟合，原合同/包保留；packfix1只补执行器闭包/调度字段和精确新合同路径，不改科学设计。

[启动与验收](ai4s/programs/dbconformer/research/bcu_r1/STARTUP_REPORT_PACKFIX1.md)


## DSAINET-P0-PF-R1-TECH-AND-BUDGET-20261029

P0-PF-R1已实施，旧90格复用来源与五臂实际Lab10八batch资格/5epoch TECH通过。原工程汇总因缺json导入FAILED，保留成功产物和失败原记录，独立只读复验完成且没有重训。科学分析器、预算生产/消费/派发门、真实Transaction schema及证据闭环完成，独立复核READY_FOR_NUMERIC_APPROVAL。科学90fit/90audit尚未启动。

实测成本保守外推22.166h（无未来并发折扣），拟SCI23h、新Transaction27h含4h收尾；目前原140h累计预算不足该完整后继，拟追加4h至144h，等待明确数值批准。原2026-10-23 21:28+08起点、40h/45h阶段carry、R1–R3及本次TECH记录保留；不重跑TECH、不改变科学矩阵或阈值。见[实施与预算报告](ai4s/programs/dsainet/research/p0-pf-r1/IMPLEMENTATION_REPORT.md)。


## DBC-BCU-R1-CLOSEOUT-20261029

BCU-R1 packfix1已完成2 TECH+36 SCI，54旧参照复用；原合同、包、封存清单及全部结果保留，回传修复零训练/零模型前向。两份遗漏的原FCA来源元数据通过精确SHA绑定的独立补充索引回传，全部原include规则保留；实际约508MB核心已走标准controller正式intake，full_payload_local=false。独立全量、正式核心27行/4比较/决策一致，18,432条目标评分记录及独立整数复算通过。

E0/C0/P平均ACC为60.3299/60.4275/60.7313%；P−E0 +0.4015pp、P−C0 +0.3038pp，均低于0.5pp，最差配对−7.0313/−5.4688pp，且P−C0 seed3为负；P−B/P−D的个体风险门亦失败。决策BCU_R1_FIXED_SCREEN_GATE_NOT_MET_STOP，证据AI4S-DBCONFORMER-dbconformer-bcu-r1。关闭固定source-cal32 bootstrap bank32配方，不以加seed/调强度/换bank救援，不否定整个校准家族。九被试已暴露、两seed不构成独立确认；C0为CovMix-cal32适配，不是原生复现，无新Claim。

State=COMPLETE_MAX_ROUNDS且暂停，无活动Run/operation，BCU-R2不启动。原48h上限、2026-10-29 01:07+08起点及准备/等待/修复成本不重置，收尾累计14.2840h；旧FCA超限与CGB账本保留。Grok原终审BLOCKED及完整trace保留，确定性工程问题经实际transport/正式入口和62项接口回归闭合，由主Agent验收，不改写为Grok通过。

[正式收尾报告](ai4s/programs/dbconformer/research/bcu_r1/closeout_20261029/CLOSEOUT_REPORT.md)


## DBC-POST-BCU-RCS-DESIGN-20261029

BCU正式失败后重评：暂停DBConformer近邻模块、辅助loss和校准训练配方搜索，优先收束论文证据。下一轮唯一展开的低成本选项为RCS-R1：用已有B/D/E0/C0/P的90份预测，检查校准损失是否在同被试/会话跨两seed、跨配方重复；0新训练、0模型前向，规划2小时仅为待授权情景。共同模式不存在则停止以共有风险对象驱动新方法；存在也仅支持另行设计独立可识别性研究，不训练目标标签门控、不调阈值或加seed救援。九被试均已暴露，不构成独立确认，无新Claim。用户本轮明确先不启动，State/原预算/合同不改，BCU-R2不启动。

[研究方案与停止条件](ai4s/programs/dbconformer/research/reassessment_20261029_post_bcu/research_brief.md)。


### DSAINET-P0-PF-R1-PACKFIX1-SCIENCE-START-20261029

2026-10-29：按用户明确授权，P0-PF-R1 packfix1已在Lab10启动固定90fit/90audit科学矩阵，复用已完成五臂TECH和旧90格对照；source、TECH绑定、旧对照复验和成本门均PASS。16:03控制快照5完成、30运行、55待调度、0失败，审计待90fit全部成功封存。累计157小时，原2026-10-23 21:28+08起点、SCI23h/Transaction27h含4h收尾不变；不退还人工等待/修复/执行、不计未来并发折扣。原science1因proof依赖打包遗漏工程INVALID、0科学fit/audit，原Run/包/2.808s消耗、R1-R3及TECH记录保留。此项仅为执行进度，无中间效果分析或论文Claim；权威状态见ai4s/programs/dsainet/research/STATE.yaml、EVIDENCE_INDEX.yaml及p0-pf-r1/PACKFIX1_LAUNCH_REPORT.md。


## DBC-RCS-R1-CLOSEOUT-20261029

用户已批准2小时、仅已有预测的RCS-R1；现完成来源核验、风险一致性分析与收尾。FCA B/D/E0和BCU C0/P共90份封存预测、180个会话分数、288差值及144会话seed均值闭合；独立复算一致，原FCA/BCU被试层结果重现。0训练、0模型前向、0远端调用、无新Run，累计0.7596小时，旧预算和全部历史成本保留。

18个被试/会话中0个满足E0/C0/P对B/D在两个seed共12个差值严格全负的预定判据。决策NO_SHARED_HARM_PATTERN_STOP_TARGET，停止“共有受损对象驱动新方法”支路，不调阈值、不加seed救援、不训练门控。局部重复损失存在，共有集合为空不证明校准安全或随机性根因。九被试已暴露，seed与会话不是独立被试，无正式Claim。BCU-R2未启动，Program保持暂停，无活动Run/operation。

会话由合同绑定split和封存global trial索引确定；没有使用替代meta或猜测数组边界。本地缺合同版本meta，无法独立恢复原trial_in_run/onset，已披露。

证据AI4S-DBCONFORMER-RCS-R1-PREDICTION-REANALYSIS-20261029；[完整结果与风险图](ai4s/programs/dbconformer/research/rcs_r1/RESULTS_REPORT.md)。本条完成此前RCS设计待执行事项。


## DBC-POST-RCS-SBN-DESIGN-20261029

RCS后新方向筛选仅设计：首选有条件SBN-R1，固定原FCA无对齐B的18个checkpoint，比较原BN buffers、真实源数据重估、真实＋增强源数据重估，检验统计重估及数据组成的条件净效用。源码存在真实/增强混合前向及三个前端BN路径，但尚未证明有害统计偏移。此方向不依赖已关闭的共有风险对象门控，不是目标会话适配；旧FCA/BCU/RCS判决保留。

拟0新梯度训练、36份派生统计、54份评分（含18原B重放），需要新的源前向/目标评分授权。预算须经实际资格与资产核对后估计；本轮没有下载资产、执行前向、训练或新Run。其余候选为固定权重平均、SAM、短时长决策和相位一致性，均保留明确风险。BN重估与增强统计已有近邻及clean未必更好的反证，不能宣称原创机制或主论文资格。State暂停、BCU-R2不启动。

[条件方案、对照和停止点](ai4s/programs/dbconformer/research/reassessment_20261029_post_rcs/research_brief.md)。


## DBC-SBN-R1-PACKFIX1-LAUNCH-20261029

用户已批准启动SBN-R1及新增6小时，原准备起点2026-10-29T10:53:47.286204+00:00，准备/排队/执行/收尾计入；不挪用旧余额。实际Run `2026-10-29_dbconformer_sbn_r1_packfix1_lab10_r1-full-w1` 已通过标准controller登记上传启动。首个真实source-only GPU资格PASS，独立数值等价通过，完整进程峰值1189MiB≤3072MiB，target_evaluated=false，0梯度/优化器步骤；18项原B0重放运行中。新统计科学效用未读取，仍须全18重放与实测成本门通过后才派发。

固定18原权重，B0/Cmix/Preal三臂，37调度任务含1资格+18重放+18组合科学任务；科学36BN统计/总54评分，0新增梯度训练。原设计3BN描述按固定constructor radix1更正为实际2BN，不改网络或干预全部前端BN意图。原预派发冻结包因缺技术前置绑定零派发保留，packfix1仅工程补齐；shared默认排队策略覆盖已批准wall_clock的问题已恢复，预算起点和全部成本不重置。

来源四原包完整清单与18checkpoint/data SHA通过，CPU生产写者→analysis_v1→核验→分析合成闭环通过，87文件远端包SHA和CPU导入通过；这些与真实GPU技术资格分开记录。Grok原设计READY_WITH_LIMITS、一次生产INCOMPLETE和有效补审BLOCKED保留；缺compact报告/旧草案/过期SHA已按实际回归由主Agent确定性验收，不声称Grok改判或科学支持。无新Claim，BCU-R2/SBN-R2不启动，旧轮次/成本/结果保留。

[启动报告与只读看板](ai4s/programs/dbconformer/research/sbn_r1/STARTUP_REPORT.md)。


SBN-R1 packfix1启动补记：真实source-only资格PASS、18项原B0重放PASS、实测成本门PASS，science已RUNNING；科学保守估计2564.98s。0新增梯度训练，未读中间科学效果，6h原起点不变，BCU-R2/SBN-R2不启动。[凭证](ai4s/programs/dbconformer/research/sbn_r1/SCIENCE_START_GATES.json)。


## DSAINET-P0-PF-R1-PACKFIX1-REVALIDATED-ANALYSIS-20261029

P0-PF-R1 packfix1已完成90fit/90audit（0失败），远端全量2008项及本地682项关键文件核验，原分析器与独立NumPy复算一致。冻结判断G1失败、G2/G3通过、I=-0.5787pp，NO_SIGNAL_STOP_PF_R1；P ACC54.8997%、raw NLL1.223481，相对R2父体-0.6944pp、NLL+0.024135、最差逐人-14.6701pp。G2/G3仅支持本开发实例有限结构/联合预测线索，不能替代净效用门。原合同FIT_BARRIER缺项及checkpoint超限保留，本次为独立关键交付复验，非标准analysis_v1 intake；原Run COMPLETE与R1–R3记录不改。Grok外审无交付阻断，覆盖和限制见analysis_closeout/review。State关闭当前Run并暂停，轮数4/4；157h与原起点保持，无新实验或正式Claim。登记余额23.153h（2026-10-29T11:56:23.546781+00:00快照，不返还人工等待或暂停时间）。详见ai4s/programs/dsainet/research/p0-pf-r1/analysis_closeout/REPORT_ZH.md。


## DSAINET-P0-FD-R1-DESIGN-20261029

2026-10-29 v3.3设计：P0-FD-R1优先补齐固定检查点的训练来源×读出比较，拟36份R2原检查点前向、0新训练；当前未实施或启动。已验收logits事后重分析显示PF权重改几何读出仅ACC+0.3858pp、NLL+0.079746，被试6相对R2降15.8854pp；3/5/6两seed均退步，7两seed均改善。故关闭固定PF权重简单切回读出的救援，保留E/A有限结构线索，尚不把风险归为纯读出或单seed问题。R3 CVAR为中心化方差，不是风险CVaR。下一步若固定R2读出也失败则停止该简单融合修复；不自动转入辅助损失/Group-DRO。详见[p0-fd-r1研究方案](ai4s/programs/dsainet/research/p0-fd-r1/research_brief.md)。 原157h预算、起点、4/4轮及暂停保持，不创建正式Claim。


## DSAINET-P0-FD-R1-CROSSED-READOUT-20261029

P0-FD-R1已完成36份R2原检查点复用和恒等回退、TECH/成本门及144格交叉读出分析，标准analysis_v1验收通过，0新训练。R2固定E/A权重概率−几何：ACC-0.945216pp、NLL-0.008528、最差逐人-2.951389pp；相同概率读出E/A−A/A为+1.012731pp。冻结处置NO_SIGNAL_STOP_FIXED_READOUT_REPAIR。训练来源差异仍含优化/初始化/选模，不作纯梯度因果解释。两个工程失败原件及全部R1–R3/PF记录保留；157h原预算、起点及原4/4科学轮记录未变。无自动后续实验或Claim。详见ai4s/programs/dsainet/research/p0-fd-r1/RESULTS_ZH.md。


## DSAINET-P0-CUMULATIVE-POSTFD-REASSESSMENT-20261029

结合 R1–R3、PF-R1 与已完成 FD-R1，决定收束当前 BNCI2014001 cue4 P0 连续净效用优化，不推荐新一轮结构、loss 或融合修复。保留 E/A 的有限结构相对收益与历史冻结候选，不宣布整个 P0 家族无效。FD 同读出重整理显示，E/A−AA 平均间距在 R2→PF 间只变化 −0.0868 pp（G）/+0.0772 pp（P），但 audit 索引 6 的 E/A 相对 AA 额外退步约 12 pp；这限定了结构收益和风险迁移，未识别纯梯度、初始化或选模因果。逐支监督等剩余解释目前不足以支持新增训练投入，完整竞争解释与重新评估条件见 [累计研究取舍](ai4s/programs/dsainet/research/p0-cumulative-review/research_brief.md)。

本次仅已有证据与汇总值的只读复评、文档登记，0 新训练/前向、无新 Run 或正式 Claim；State、原 157h 上限、2026-10-23 21:28+08 起点、4/4 轮及所有旧记录不变。R3/PF 的非标准恢复复验边界、FD 标准 analysis_v1 与各原 NO_SIGNAL 均保留。此项是范围明确的研究投入收束，不是全局机制无效结论。



## DBCONFORMER-SBN-R1-CLOSEOUT-20261029

SBN-R1 packfix1已完成37任务、54评分、analysis_v1_recovery正式intake及独立复算。Preal−B0 −0.2604pp、Preal−Cmix −0.2713pp；两个主比较均值和逐seed门失败，前者另有2/18配对低于−3pp。冻结决策SBN_R1_FIXED_GATE_NOT_MET_STOP，关闭本固定两BN source-real-only顺序population重估实例；不推论整个BN校准家族无效，也不据此识别源增强致害机制。无新Claim，BCU-R2/SBN-R2不启动，State暂停且无活动Run/operation。

用户批准的37日志路径别名仅写独立派生层，原合同、全部include模式、封存清单及结果不变；本次修复0训练/新增推理，不追加预算，原6h准备起点和全部成本保留。正式记录见 [SBN收尾](ai4s/programs/dbconformer/research/sbn_r1/closeout_20261029/CLOSEOUT_REPORT.md)。


### 2026-10-29 MVCNet XSN-R1 一次性探索执行登记

用户选择XSN-R1一次性探索并授权独立36小时累计执行上限。新campaign按MVCNet v3.3运行，准备从2026-10-29 13:20 UTC保守窗口计时；旧VBR275小时/原起点和全部失败修复历史保留。五臂S0/P0/C0/N0/R0、seed71/72、九outer，90新fit+90check；无自动重试或调参救援。Run `2026-10-29_mvcnet_xsn_r1_lab10_r1-full-w1` 已在Lab10真实启动，source-import完成，当前资格阶段排队，完整训练尚未开始。资格与实测成本门PASS后由同一Transaction继续；只回拉analysis_v1核心，完整结果留服务器。科研HOLD/薄新颖性边界不变，无新Claim。权威进度：[执行记录](ai4s/programs/mvcnet/research/xsn-r1/execution/PROGRESS.md)、Program State/Evidence Index；摘要不授予额外实验权限。


## MVCNET-ACM-R1-DESIGN-20261029：XSN等待期间的下一辅助方向，仅设计

用户要求围绕VCN-P1并行准备下一方向，不启动新训练。静态核对确认当前本地分类/部署只走CNN/IFNet，Transformer是训练辅助，不能用论文v4融合分类图替代实际实现。结合VBR/增强读出的精确NO_SIGNAL、CVC×CMC整项诊断及VOGR的未充分支持，暂选ACM-R1固定单向CMC：仅对CMC中的CNN特征停止梯度，CE/CVC和原前向/正负集合保持；用双向、仅辅助更新、仅CNN更新、两侧关闭四臂区分职责与简单删损失。stop-gradient已有先例，效用/新颖性未建立；主Agent暂选不等于独立接受。详见[ACM设计备忘录](ai4s/programs/mvcnet/research/next_auxiliary_20261029/research_brief.md)及Evidence ID `MVCNET-VCN-NEXT-AUX-DESIGN-20261029`。本轮仅设计文档；未建campaign/Run、未占seed、未分配预算，不改变活动XSN的36h计时/冻结矩阵，也不转用旧VBR275h。


## DSAINET-P0-WMP-D1-DESIGN-20261029

按用户新提出的历史借鉴问题，保留P0-WMP-D1“全位置覆盖的局部加权矩”有界诊断草案，状态HOLD_CONDITIONAL_DIAGNOSTIC / DESIGN_ONLY；原cue4连续结构/loss/融合优化投入收束仍有效。核实TAPL/TAUD/SFTA是原生B0后端31-token汇聚，P0 Avg8是早期块内8位置，P0仍保留intra/token attention；正权重仅保证覆盖，不保证上下文信息完整保持。SCCD/C1/AAP/AEC等仅提供控制与解释约束，不继承正向资格。

拟先核验36份R2原工件的final_model固定epoch100（不是FD选中终点），做fit-only非退化检查；条件满足且成本许可才考虑最多396次线性probe拟合，0端到端网络重训。五类读出包括原均匀矩、加权矩、增量、7种错位与平方读出控制；AA去重且仅A估模板，统一U尺度防止放大微小扰动。正结果也仅为限定信息线索，不打开训练资格或自动追加诊断。Grok原判REVISE及修订处置保留，未冒记外审PASS；调用期间共享根文档变动导致wrapper73，只读trace与异常均存档。

本次0新拟合/前向、无Run/上传，TECH和成本门未运行。原157h、2026-10-23 21:28+08起点、4/4轮及全部历史记录保持；不创建正式Claim。详见[研究方案](ai4s/programs/dsainet/research/p0-wmp-d1/research_brief.md)及[外审处置](ai4s/programs/dsainet/research/p0-wmp-d1/review/REVIEW_DISPOSITION.md)。


## OTA-SIC-R1-LAB10-LAUNCH-20261029

用户完成 OTA v3.3 激活授权后，明确选择 U-only 首阶段并授权 Lab10 执行。方案固定为 U0 状态索引连续内容、C0 占据/内容均值拼接、T0 四组时间窗内容、M0 全局内容均值，4臂×2 seed×9固定source划分×100epoch（72正式拟合+4技术单epoch）。24小时上限、零自动训练重试/扩额、阶段结束停止，V/B不启动。

Run `2026-10-29_ota_sic_r1-full-w1` 已上传并真实启动后台执行器；2026-10-29 22:51核验为技术阶段WAIT_FOR_RESOURCES，4任务pending、0 running/completed/failed，尚未拟合。等待不计执行预算，同一Run在资源满足后继续。原SPAR INCOMPLETE与预算历史完整保留。外审确定性接口阻断已修复并通过实际产物/合成闭环；这些不是GPU资格或科学证据，无新Claim。方案、边界、精确身份、验证和只读看板见[启动记录](ai4s/programs/ota/research/sic-r1/LAUNCH_REPORT.md)，动态状态以Program State为准。


## MVCNET-ACM-R1-REVIEW-20261029：限定查新谨慎继续，暂缓完整训练

用户授权ACM-R1限定查新、独立科研反驳及对照/成本修订，明确不启动新训练、保持当前XSN Run。已按mvcnet-transaction-v3.3完成24条定向检索与Grok-4.6-build独立审查，原始意见PROCEED WITH CAUTION（5/10）、HOLD_TRAINING。ADM（ICML2025）已有单侧特征梯度保护，部署角色不对称也有近邻；潜在贡献须来自本地原生CMC/CVC职责干预的可归因效用，不能以detach本身为新算子。

采纳四臂S0/P0/R0/N0作为窄问题的最小核心：P0须先优于S0，再区分完全关闭N0和反向R0。当前三项均无新实测；先做零训练图资格更有价值，完整72fit暂不投入。第五固定0.5双侧衰减臂非精确范数匹配，未自动增加。四臂规划46.942process-h；有效并发4约20.67–23.60h、并发2约35.34–41.21h，含未实测倍率及6h准备/验收余量，不是ACM报价或上界。

原CCF/VOGR诊断不足与VBR/COC/SCVA/IPB/MPRF精确关闭不改写；XSN中间效果未读取，原36h授权与VBR275h历史/起点不转用。ACM预算UNASSIGNED、未实施、未forward、无新Run/Claim。权威设计登记：MVCNET-ACM-R1-NOVELTY-REBUTTAL-20261029；[完整报告](ai4s/programs/mvcnet/research/next_auxiliary_20261029/review_20261029/NOVELTY_AND_REBUTTAL.md)。


## MVCNET-ACM-R1-GRADIENT-AUDIT-20261029：限定合成梯度资格通过，科学效用待证

按用户授权在隔离副本完成零真实数据拟合的技术审计：53项主检查、8组首步因子配对及两个保存张量重放/断路实例全部通过。S0与原生参考一致；CMC接收端符合S0双侧、P0仅辅助、R0仅主干、N0均关闭；P0/N0首步F/C梯度、参数与Adam状态完全相等，而辅助更新通过原生CVC耦合可以改变后续F梯度，断开跨分支耦合则差异归零。实际执行10次合成临时模型单步Adam更新，0科学拟合。

据此将“先证明图可辨识”更新为“有条件保留一次四臂探索”，不是直接派发许可或分类收益证据。保留S0/P0/R0/N0及P0相对三项对照，不增臂、调权或叠加XSN；原外审HOLD原文不改判。实际batch64、生产增强链路、长期效用和Lab10容量/成本仍未验证。历史条件估计保持：有效并发4约20.67–23.60h，并发2约35.34–41.21h，非实测上界。ACM预算UNASSIGNED，不借用XSN36h/VBR275h及其起点。

当前XSN Run未操作或重复提交，未读取中间效果，无新Run或Claim。后续先结合XSN正式验收比较投入价值；若另行选择ACM，再完成生产接线、冻结判读、独立预算与Lab10成本门。详见[审计报告](ai4s/programs/mvcnet/research/next_auxiliary_20261029/gradient_audit_20261029/REPORT.md)；权威证据登记为同名ID。


## DSAINET-P0-WMP-D1-STAGE-A-LAUNCH-20261029

用户已明确批准冻结载荷上传至Lab10指定新目录并启动2026-10-29_dsainet_p0_wmp_d1_stagea-full-w1。包上传与逐文件SHA核验完成，已启动CPU串行双线程诊断；本次状态快照：复用节点PASS, TECH RUNNING, 科学格0/36。首阶段0次神经训练、0次线性探针；实际资格、TECH和成本门通过后才进入全部36格source-fit非退化分析。原157小时、2026-10-23T13:28:00+00:00计时起点、旧4/4训练轮及R1–R3/PF/FD全部记录保留；首阶段Transaction上限2小时、科学节点1小时。跳板超时后按现有规则使用同一Lab10的lab-codex直连，未换Run或环境。合成接口已验证完整/精简analysis_v1一致，限定外审只覆盖源隔离和矩计算；均非科学结果。本阶段结果不足6/9双seed配对context达到冻结干预线则停止此固定模板；不调强度、不自动神经训练。活动诊断由独立用户授权operation记录，不把旧通用部署NOT_READY改为PASS。详情见ai4s/programs/dsainet/research/p0-wmp-d1/EXECUTION_NOTE.md。


## DSAINET-P0-WMP-D1-STAGE-A-COMPLETE-20261029

2026-10-29_dsainet_p0_wmp_d1_stagea-full-w1已完成36/36原R2 epoch100 final_model资格、实际TECH/成本门及36/36 source-fit非退化诊断；标准analysis_v1回拉核验与独立局部复算通过。双seed同时非退化的E/A context为0/9，冻结要求至少6/9；处置NO_SIGNAL_STOP_FIXED_PHASE_TEMPLATE。0次神经训练、0次线性探针，0次select/audit/excluded前向。这只检验此固定八相位模板能否形成足够干预，不是模型准确率、校准或被试伤害的改善证据，也不否定所有池化方法或P0结构。下一动作：STOP_WMP_D1_NO_PROBES。保留原157小时与原计时起点及全部旧结果；关闭时预算余额18.803小时。报告：ai4s/programs/dsainet/research/p0-wmp-d1/stagea_analysis_local/REPORT_ZH.md。


## MVCNET-XSN-R1-REPAIR1-LAUNCH-20261030：原失败收尾，原预算内工程修复启动

用户明确授权XSN打包依赖修复、失败Run收尾与停机结算；同36h、2026-10-29 13:20UTC起点、五臂/seed71,72/科学门。原Run10项资格均在训练前因proposed初始化连带读取缺失DBConformer源码退出，已正式INVALID/元数据收尾；science0。核验并结算9.536963h闭合停机，独立保留3.808862h原资源排队，截止首次状态核对消息之后的观察与修复继续计费；未增加额度或重置起点。

仅在独立源码快照修复按需导入，并补精确修复授权/预算证据/验收身份兼容。原包、未派发prelaunch0和全部失败历史保持。28项限定检查、62项共享接口、实际Lab10 worker导入和103文件哈希通过。新Run `2026-10-30_mvcnet_xsn_r1_lab10_r1_repair1-full-w1` 已真实启动，source-import PASS，10项GPU资格待10/跑0/成0/败0，科学90fit+90check未启动；同Transaction在资格与冻结成本门PASS后继续，否则阻断。预算快照剩余34.523h，实时以State/probe为准。完整payload留服务器，只回analysis_v1核心。

限定Grok外审原文REVISE credits/READY lazy exports保留，当前冻结实数核验确认原wall结束=停机start且总额/预留固定，主Agent按精确实例接受；不把原外审改写为PASS或形成科学Claim。详见[启动记录](ai4s/programs/mvcnet/research/xsn-r1/execution/repair1/REPORT.md)和Evidence ID同标题。


## DSAINET-P0-POSTWMP-EXPLORATION-20261030

2026-10-30：DSAINet按v3.3完成WMP后10项方向构思与一次独立科研反驳，维持cue4 P0连续净效用修复收束。块内邻接摘要仅保留为未采纳假设，初稿180探针不执行；已完成固定读出、训练来源、context与WMP非退化的可识别性边界表。原生尺度/inter仅为未来具体问题入口，无新干预或实验授权。State暂停、原157h/原起点和全部历史记录保持，0新拟合/模型前向。详见[研究brief](ai4s/programs/dsainet/research/p0-postwmp-exploration-20261030/research_brief.md)。本条为暴露开发认识与设计处置，不是正式Claim或独立论文贡献。


## OTA-SIC-R1-BOUNDED-RECOVERY-20261030

用户明确授权保全核验66项，仅补原失败/未启动6项并完成本轮分析。原Run四技术PASS、screen FAILED，66项科学产物与540个初始参数张量核验通过；原3失败/3未启动、全部成本及24h起点保留。M0/s1/f1失败初始temporal权重全零，与原Lab10同种子CPU构造不一致，未唯一归因CUDA搬运。恢复保留原算法/种子/有效梯度门，增加初值保值守卫和资源余量。

首次repair包导入66+4后因72结果scope与6实际派发闭集接线失败，0拟合；原件/51.4s工程成本保留。packfix1补了真实执行器入口和来源篡改拒绝测试，已在Lab10启动并完成导入，12:50仍6项资源等待、0新增拟合/0失败。同一科学72矩阵由66原件+6新件闭合；原实际73次拟合尝试加本次最多6次，累计上界79，不重开budget/campaign，无自动追加训练或新Claim。动态进度见[恢复记录](ai4s/programs/ota/research/sic-r1/repair1/packfix1/PROGRESS.md)与Program State；源数据开发曝光边界不变。

## DSAINET-P0-ORD-EC-DESIGN-REVIEW-20261030

2026-10-30：评估用户P0-ORD-EC-R1新方案。端点条件化数学与源码静态可实现性通过；冻结父体+有界修正器补上旧ORD仅probe的主要缺口，主Agent及一次Grok增量反驳建议PROCEED_WITH_REVISIONS，仅继续设计，未授权或执行108拟合。运行前须检查固定rho=.25的纠错乐观上界、绑定36份R2 select-best、明确判定与求解/选择/控制细节、完成成本核算。旧风险audit subject7对应context5，四锚点最严要求净增46/1152正确预测；逐trial上界尚未计算，不能据此调rho。旧P0/WMP/ORD停止和原157h/起点、State及全部历史记录保持；0模型前向/拟合/远端操作。不是正式Claim。

完整意见：[方案评估](ai4s/programs/dsainet/research/p0-postwmp-exploration-20261030/ord_ec_review/ASSESSMENT.md)。
## DSAINET-P0-ORD-EC-R1-PREPARATION-20261030

2026-10-30：按用户授权完成ORD-EC修订、108原预测核验和rho=.25纠错必要上界、36父体资格、6次TECH小拟合及成本核算。subject7/context5理论可纠正63、需净增46，上界通过不代表共享W可学。科学108拟合0、新audit/excluded前向0；原157h与2026-10-23 21:28+08起点、旧4/4轮与全部记录保持。校准含收尾3.0778h，建议后续SCI3.25h/Tx4h；15:24余额3.68325h，提出追加1h至158方案，尚未批准/登记/派发。报告：[P0-ORD-EC准备](ai4s/programs/dsainet/research/p0-ord-ec-r1/PREPARATION_REPORT.md)。不是科学成功或Claim。

## DSAINET-P0-ORD-EC-BUDGET158-20261030

2026-10-30：用户批准追加1小时，总预算158小时；原计时起点、旧Run和排队记账保持。本次为预算批准，科学节点3.25h/Transaction4h仍为后续计划，108科学拟合未启动。15:29预算快照余4.60157h。回执：ai4s/programs/dsainet/research/p0-ord-ec-r1/preparation/BUDGET_AUTHORIZATION_158.json。

## 2026-10-30 P0-ORD-EC-R1 execution authorization (163h)

User approved cumulative 163h with original 2026-10-23 start, SCI 3.25h and Transaction 4h unchanged. Preserve R1-R3/PF/FD/WMP and original 158h frozen package. Reuse 36 qualified selected-model parents and completed six-arm TECH. New immutable package science_bundle163: 108 bounded convex readout fits, full fit/select barriers, then 108 audits; no neural training. Transport through [REDACTED_MACHINE] to the authorized 2026-10-30_dsainet_p0_ord_ec_r1_science1 directory. Offline controller/seal/compact-intake acceptance passed; upload/start remain conditional on external implementation review disposition and live final budget gate. Source of current execution state: ai4s/programs/dsainet/research/p0-ord-ec-r1/CONTINUATION_STATUS.json and research/STATE.yaml.

### P0-ORD-EC-R1 dispatched and remotely verified, 2026-10-30

Run 2026-10-30_dsainet_p0_ord_ec_r1_science1-full-w1 launched on Lab10 via [REDACTED_MACHINE] (PID565135), original continuous budget163h, SCI3.25h, Tx4h. Dispatch remaining17848.79 seconds. Reuse qualification PASS; scientific readout node RUNNING, queue_seconds0, no failure marker at first probe. Contract a12e54ae3ce0cf46bef48286ede40f6f1712d7dc231741e27922d71805a1dce5; archive eb976abdaf7e701e7c28c8216f3c10663accb2ba67cf86c9e08645f510eefa9d. No new neural training. All108 bounded fit solutions must seal before select; all108 choices must seal before108 audit tasks. External Grok implementation review PASS for data roles/seals only; no scientific result or Claim yet. Original campaign remains closed/paused; this separately authorized readout Run is tracked by active_run and its exact frozen contract. Evidence and current counters: ai4s/programs/dsainet/research/p0-ord-ec-r1/REMOTE_DISPATCH_RECEIPT.json and LATEST_PROBE.json.


### OTA-SIC-R1-CLOSEOUT-20261031

OTA完整72项source筛查已以analysis_v1精简包正式核验：66原件逐字节复用、6缺口补跑。U0/C0/T0/M0平均ACC为43.245/43.182/53.496/42.866%；U0-C0为+0.063pp且NLL变差、U0-T0为-10.251pp，冻结主门失败，登记NO_SIGNAL / U_INDEX_NOT_SUPPORTED / STOP，无论文Claim。关闭当前U实例、V/B不推进；不授权下一轮训练。完整载荷及权重留在Lab10，6份初值只在远端核验并回传摘要。权威证据AI4S-OTA-ota-sic-r1-repair1；决策ai4s/programs/ota/research/ota-sic-r1-repair1_decision.yaml；报告ai4s/programs/ota/research/sic-r1/repair1/resourcefix1/analysis/REPORT.md。source审计已暴露且重叠，不作target/因果/滞后机制主张。

## 2026-10-31 P0-ORD-EC-R1 verified closeout

Evidence DSAINET-P0-ORD-EC-R1-VERIFIED-ANALYSIS-20261031: exact Run 2026-10-30_dsainet_p0_ord_ec_r1_science1-full-w1 completed108 bounded convex fits/108 sealed choices/108 audits, zero failed nodes or new neural training. Reverified original full remote payload and sealed analysis via ccmu; standard analysis_v1 local intake PASS (373 selected files,13495094 uncompressed bytes,10774803-byte transport ZIP). Frozen analyzer replay and independent NumPy correct-count/NLL/gate recomputation agree.

Scientific disposition NO_SIGNAL_STOP_FIXED_ORD_EC: P vs R2 parent ACC+0.009645pp, rawNLL+0.000462,16/18 W0 fallbacks. Old risk context5/original subject index7 remains796/1152; all four old-anchor risk gates fail. P vs C_pi/C_bag/C_head ACC0/-0.009645/+0.221836pp; no control comparison clears the frozen0.5pp gate. A/B fail. Descriptive P-AA and D do not establish mechanism. Close this fixed adjacency/aggregation/bounded-linear-correction instance; no rho/lag/loss/threshold/seed rescue or new experiment. Combined R1-R3/PF/FD/WMP evidence supports continued restraint on cue4 P0 net-utility repair, without a universal impossibility claim.

State active Run cleared, paused preserved; original163h cap/start/queue credit and all old records retained. Science completed inside original limits with3.882719h remaining; continuous budget was-3.431081h at closeout, no refund or new authorization. Exposed development evidence only, no formal Claim. Full report ai4s/programs/dsainet/research/p0-ord-ec-r1/closeout_analysis/REPORT_ZH.md; exact provenance and decision in DECISION.json, LOCAL_INTAKE_VERIFICATION.json and Program Evidence Index.


## MVCNET-XSN-R1-BUDGET480-LAUNCH-20261031：原起点累计扩至480h，同科学完整训练入队

用户明确要求增加预算启动，并选择累计480h总上限（原36h+444h）；新Transaction432h，保留6h收尾、2026-10-29 13:20UTC原起点、五臂/seed71,72/原矩阵与科学门。repair1十资格全部成功但冻结成本门STOP，科学0，已按非科学INVALID收尾；其成本停止至下一次状态查询的闭合停机2.602477h经证据结算，旧9.536963h及排队计时完整保留，不重置或抹掉执行成本。

十资格在服务器重算checkpoint及源码SHA后只复用技术证据，不warm-start模型，不新做资格训练。原最慢epoch/K/1.25成本公式不变，约419.259h；最终新Run `2026-10-31_mvcnet_xsn_r1_lab10_r1_budget480-full-w1` 的source-import、CPU资格复用及成本门已实际PASS。完整训练节点已运行，90fit当前成0/跑0/待90/败0，GPU资源满足后同Run继续；90check在全局seal后启动。完整机器产物留服务器，只回analysis_v1核心。旧Run、未派发prelaunch0及外审REVISE/修订负例都保留，未新增科学Claim。详见[启动记录](ai4s/programs/mvcnet/research/xsn-r1/execution/budget480/REPORT.md)与同名Evidence ID。


## DSAINET-P0-POSTORD-REASSESSMENT-20261031

基于R1–R3/PF/FD/WMP/ORD完整证据继续复评，维持当前cue4 P0连续净效用修复收束，保留历史候选和有限EA相对AA平均收益。仅复用已验收144份fit/select文件做事后损失复算：固定P的18格fit目标均下降，但select raw NLL和原LS损失都仅同2格改善，0格出现CE变差而LS改善；不足以用选择损失不一致解释16/18回退，也不定位具体原因。动态池化/共享投影/上下文补充尚无新增优先投入依据。

若以后继续讨论，仅保留P0/AA接受同一种源被试训练约束后的结构交互问题；不是已选算法、矩阵或预算。完整效用、所有相关被试风险和简单控制均需前瞻保留；通用训练改善不升级为P0创新。本轮0前向/0拟合/0新选择/0Run，原163h、起点、State字节及全部历史判定保持。详见[复评与结果去向](ai4s/programs/dsainet/research/p0-postord-reassessment-20261031/research_brief.md)。无正式Claim。


## DSAINET-P0-SDRO-R1-DESIGN-20261031

按用户仅设计授权，选择源被试Group-DRO形成P0/AA×ERM/真组/伪组六臂配对（108完整训练的设计规模，实际0训练/0前向）。以净效用、I结构交互、J/伪组增量、全体逐人风险AND门区分一般训练收益和P0结构收益；AA退化不制造结构通过，旧四锚点保留。Grok独立原判DO_NOT_INVEST；主Agent补齐具体定义并纠正部分数学/泛化推断，最终DESIGN_ONLY/NOT_INVESTMENT_READY，不宣称外审通过。原163h、计时起点、State及历史记录保持，无新Run或启动授权。

[设计与停止分支](ai4s/programs/dsainet/research/p0-sdro-r1/EXPERIMENT_PLAN.md)；外审原判和处置在同目录REVIEW_DISPOSITION.md。无正式Claim。


## DSAINET-P0-SDRO-R1-DESIGN-CLOSURE-20261031

按用户修订请求，重新核对Group-DRO原文正则、选模与108完整训练的价值。R2固定正则有公平性依据，没有P0-SDRO适用强度证据；不能直接搬强λ，正则搜索也增加配对与选择成本。四臂72项未解决适用性，六臂两个正则水平216项仅为未采纳的规模反事实。关闭本SDRO实施/108训练提案，状态DESIGN_CLOSED_INSUFFICIENT_JUSTIFICATION；六臂、I/J、全部逐人风险、四旧锚点和停止条件完整保留。不是实验NO_SIGNAL，不普遍否定P0/E/A/跨被试训练。旧外审DO_NOT_INVEST复用，无新外审或自动后续。实际0TECH/0训练/0前向；原163h、起点、State和全部历史记录保持。

[修订与收束依据](ai4s/programs/dsainet/research/p0-sdro-r1/REVISION_ASSESSMENT.md)。


## DSAINET-P0-CUE-CLOSURE-AND-IF03-ASSESSMENT-20261101

按用户明确指令收束当前P0-CUE优化谱系（R1/R2/R3、PF/FD/WMP/ORD及未执行SDRO），保留旧科学判定、历史候选、原163h及起点；Program已暂停且无活动Run/operation，不新增运行。重新核对IF-20261029-03七条记录及三张card-v2哈希，原Foundry产物未改。DS-07逐token回返优先进入有界设计讨论，DS-03备用，DS-01暂缓；其他未选理由未改变，DS-04仅父控制。该排序不是科学收益/新颖性通过，用户未选择交接，无新研究身份、handoff或实验。

[谱系关闭](ai4s/programs/dsainet/research/P0_CUE_LINEAGE_CLOSURE_20261101.md)；[候选评估](ai4s/programs/dsainet/research/foundry_if20261029_03_review_20261101/ASSESSMENT.md)。


## DSAINET-DS07-R1-SELECTED-DESIGN-20261101

用户选择IF-20261029-03的IF-20261029-DS-07 card-v2进入既有DSAINet Program设计，已完成精确handoff，原卡不改，P0-CUE不重开。DS07-R1固定大核内容A与小核关系P的逐token2/3/4步回返B；先设计N/C/S/R四臂72项完整训练，只有净效用/风险全部通过才考虑36项B去PE训练及144项同P头拟合。Grok原判REVISE，主Agent补全全P全局对照等定义；当前DESIGN_COMPLETE / PREPARATION_CONDITIONALLY_WORTHWHILE / SCIENCE_INVESTMENT_NOT_READY。原163h、起点、State与旧记录保持，0实现/TECH/前向/拟合/训练/上传，无启动权限。

[方案](ai4s/programs/dsainet/research/ds07-r1/research_brief.md)；[外审与处置](ai4s/programs/dsainet/research/ds07-r1/REVIEW_DISPOSITION.md)。


## DSAINET-DS07-R1-PREPARATION-20261101

按用户准备授权完成DS07 N/C/S/R模型安装、CPU合成接口/配对检查及Lab10现有cue4七文件/九划分只读实核；无科学效能结论。四臂参数N75645/C62243/S=R54283，R/S头各2000。发现并修复N dropout计数偏差，旧模型不改。原163h及起点保持，当前余额约−24.6h，真实GPU TECH/成本因额度不足未执行，原P0-CUE仍关闭。拟新增28h至191，覆盖旧账并预留2h技术Transaction及交接余量，仅方案未登记；72项科学训练继续禁止，真实小时成本待TECH。不可派发技术准备快照18项35588字节，无EEG/凭据/检查点；完整遥测、调度汇总/intake及冻结门仍待接续。

[准备报告](ai4s/programs/dsainet/research/ds07-r1/preparation/PREPARATION_REPORT.md)；[预算方案](ai4s/programs/dsainet/research/ds07-r1/preparation/BUDGET_PLAN.md)。


## DSAINET-DS07-R1-BUDGET191-TECH-ADMISSION-20261101

用户“确认新增”已登记新增28h、累计191h，原起点/旧账/P0-CUE关闭保持。同目录TECH运输与4臂8batch+5epoch授权沿用，科学0。新增执行路径经6项CPU离线回归与29文件闭包核验；Grok增量只读原判READY_FOR_BUDGET_ONLY，未GPU验收。原时钟继续，最终余额约1.496h，低于固定2h技术预留，故未冻结/上传/启动，也未创建Run。最少再补1h可覆盖当时差额，但为给交接留余量建议再追加3h至194；该建议未应用。完整TECH成本与72项训练预算仍待真实执行和验收，不套用旧时长。

[额度登记与预算门](ai4s/programs/dsainet/research/ds07-r1/preparation/AUTHORIZATION191_REPORT.md)；[新增路径外审处置](ai4s/programs/dsainet/research/ds07-r1/preparation/RUNTIME_REVIEW_DISPOSITION.md)。


## DSAINET-DS07-R1-BUDGET194-BLOCKED-20261101

用户确认新增3h已登记至194，原起点、旧资源等待账及P0关闭保持。12:38实算余额−4.55h，实际driver在首道2h TECH预留门拒绝；未冻结/上传/启动、科学0。29文件候选包闭包通过，旧授权运输范围与目录沿用。为解决人工确认等待仍持续计时引起的重复追加，提出新增8h至202，并仅本次申请至确认期间、无远端任务的人工等待单独暂停；两项均未授权/未应用，不追溯此前等待，不重置起点。当前有效总额仍194，人工等待抵扣0。

[预算登记与限定等待方案](ai4s/programs/dsainet/research/ds07-r1/preparation/AUTHORIZATION194_REPORT.md)。


## DSAINET-DS07-R1-BUDGET202-TECH-WAIT-20261101

用户已明确批准追加8h、累计202h，保留2026-10-23T13:28:00+00:00原起点、此前耗时及全部历史记录。仅本次无任务人工审批等待115.93227秒获准暂停，结束后已恢复计时；此前人工等待不退款。四臂工程TECH冻结包34项源闭包与最终2h预留门通过，已上传既定Lab10目录并启动同Run `2026-11-01_dsainet_ds07_r1_tech1`，PID706689。当前仍在资源等待，四臂8batch资格及5epoch尚未开始，独立验收与72项训练成本核算待真实执行；未启动科学训练/审计。资源等待按冻结规则单独计时，不改4096MiB初始准入阈值，不重复派发。P0-CUE继续关闭，现有技术就绪不构成科学结论。

[预算及启动记录](ai4s/programs/dsainet/research/ds07-r1/preparation/AUTHORIZATION202_LAUNCH_REPORT.md)。


## DSAINET-DS07-R1-BUDGET212-PACKFIX1-TECH-LAUNCH-20261101

用户明确批准累计212h、原计时起点与此前耗时保留，并仅暂停本次无任务人工审批等待288.291875秒；与原115.93227秒暂停合计404.224145秒，确认后恢复计时。历史资源等待32898.104853630066秒独立核验保留，不退款失败后停机。

timezone导入与后继目录身份校验已修复。初始TECH和repair1启动失败记录/不可变包均保留；packfix1仅在已批准repair1父目录内新增不可变子目录。17项回归、39文件源闭包、Lab10真实预算消费者与完整启动到容量边界预验收通过，后继2026-11-01_dsainet_ds07_r1_tech1-repair1-packfix1已启动，PID1401399、只读分析后处理PID1402110。23:48:38北京时间仍等待N臂GPU，四臂资格和5epoch TECH完成0/4，余额约2.91848h；等待单独记账，不重复credit。72项科学训练/审计均未启动，TECH验收和完整成本仍待实测；P0-CUE仍关闭，没有科学Claim。

[修复与派发记录](ai4s/programs/dsainet/research/ds07-r1/repair1/LAUNCH_REPORT212.md)。


### MVCNET-XSN-R1-VERIFIED-NO-SIGNAL-20261104
XSN-R1同Run完成90fit+90check，0失败/0OOM；完整结果留Lab10，核心正式analysis_v1_recovery intake，原始logits两套独立复算一致NO_SIGNAL。P0−S0 −0.192901pp（seed71 −0.135031pp、seed72 −0.250772pp；5/9正向）。P0−C0 +0.096451pp、P0−N0 +0.212191pp未过门；P0−R0 +0.366512pp过门不能替代主门。关闭该固定开发配置，不新增训练或释放Claim。 原起点2026-10-29T13:20Z、480h预算和全部历史保持。权威记录：`ai4s/programs/mvcnet/research/xsn-r1/execution/budget480/analysis_20261104/REPORT.md`。


### MVCNET-ACM-R1-POST-XSN-REASSESSMENT-20261104
XSN-R1固定配置已NO_SIGNAL关闭，结论/原起点/480h及全部历史保持。ACM-R1重评为有条件值得一次四臂开发探索，但生产资格、冻结判读及独立预算尚未就绪；本轮不启动训练、无新Run/seed/Claim。P0须先胜同期S0，再区分完全关闭N0和反向R0；不追加D0/B0、不叠加XSN。近期XSN原生S0成本×4为37.512192process-h，有效并发4条件规划约18–24h，并发2约29–42h（含假设余量，非实测/上界）。36h仅为未来预算商议目标；ACM预算UNASSIGNED，不挪用XSN余额。论文层面补VCN主方法强近邻/归因/范围仍优先于默认增加辅助模块。权威依据与关键对照：`ai4s/programs/mvcnet/research/next_auxiliary_20261029/reassessment_20261104/REPORT.md`。


### DBCONFORMER-POST-SGP-RESEARCH-DESIGN-20261104

用户明确停止SGP直接性能优化；旧54SCI/3复用TECH、平均改善、个体风险失败、机制未知及原成本保留，不默认补投影/阈值/分组/Adam变体或方向遥测。下一优先为编码器未接触会话/被试的类别关系可识别性，不预先建新loss；同session匹配采样噪声、跨未拟合源被试和普通RKD/SupCon是必要反驳。五类备选均未达到论文核心资格，Grok原判NEEDS_REVISION保留，审后修订未再外审。0新拟合/forward/Run/预算/Claim，State及旧合同不变。

[下一轮问题与关键控制](ai4s/programs/dbconformer/research/reassessment_20261104_post_sgp/research_brief.md)；[继承约束](ai4s/programs/dbconformer/research/reassessment_20261104_post_sgp/SGP_DESIGN_CONSTRAINTS.md)。


### DBCONFORMER-SOURCE-IDENTIFICATION-PREPARATION-20261104

下一轮源内识别已完成元数据资格：固定排除subject0后8名source/16会话单元，整run互斥两半每类36条；旧预处理审计四SHA与冻结资产一致。提出互斥被试A/B×拟合会话交换的4编码器草案，仅source开发识别，不是4个性能方法臂；普通CE稳定几何不自动构成session配对增量。继续先核对对象，尚不选定主方法；SGP直接优化继续停止。0新拟合/forward/目标效果读取，预算UNASSIGNED，旧合同/State/预算不变。

[下一轮识别设计](ai4s/programs/dbconformer/research/reassessment_20261104_post_sgp/source_identification_design/PROTOCOL_DRAFT.md)。


### MVCNET-ACM-R1-ONCE42-FROZEN-PREPARATION-20261104
用户已授权ACM-R1一次性四臂探索，独立42h，准备起点2026-11-04T13:54:00Z，含准备耗时；32h Transaction上限和6h收尾预留，不挪用XSN预算。四臂S0/P0/N0/R0、seeds73/74、72fit+72check、8项全新资格及主门/两项关键对照冻结；不调参救援。CPU生产目标、合成真实Transaction intake/独立复算、最终103文件包闭集与哈希检查通过；这些不构成科学效果或Lab10资格通过。派发前controller接线验收进行中，真实Lab10资格与成本门通过后才自动进入完整训练。XSN NO_SIGNAL关闭结论、原480h起点/预算、全部历史保留；论文不增加Claim。权威状态与后续更新见 `ai4s/programs/mvcnet/research/STATE.yaml`、`ai4s/programs/mvcnet/research/acm-r1/execution/EXECUTION_REPORT.md`。


### MVCNET-ACM-R1-STARTUP-INVALID-20261104
ACM42独立campaign唯一初始Run真实启动后，在source-import证据发射阶段因缺identity_pass字段exit2，已正式metadata-only failure intake为INVALID，paused=true，active_run=null。8项GPU资格/72fit/72check均0启动，成本门未执行，无科学效果/Claim，不能将本次失败写为NO_SIGNAL。7个核心文件43,255字节已哈希核验，完整目录和日志留Lab10；原冻结合同和包保留。隔离工程修复与真实消费者回归准备中，不自动重提。42h原起点2026-11-04T13:54Z保持；截至15:03:29Z累计1.158160h，余额40.841840h，未扣任何排队/停机credit。XSN旧campaign完整快照、NO_SIGNAL关闭及原480h历史逐项比对一致。详见 `ai4s/programs/mvcnet/research/acm-r1/execution/EXECUTION_REPORT.md`、`FAILURE_CLOSEOUT.json`。


### MVCNET-ACM-R1-REPAIR1-QUALIFIED-FULL-TRAINING-20261104
用户批准一次工程修复Run，沿用独立42h与2026-11-04T13:54Z原起点，不抵扣旧失败/停机，不转移XSN预算。不可变后继 `2026-11-04_mvcnet_acm_r1_lab10_r1_repair1-full-w1` 只修source-import的identity_pass/shape_pass证据字段及必要身份接线，四臂/73-74种子/18 split/训练配置/科学门均保持。原失败Run的INVALID和原包不改。最终124文件/122依赖、真实接口回放、控制器真实恢复登记/拒绝重复、62项共享接口验收通过；Lab10源导入与8/8全新资格真实PASS，成本门及独立复算PASS（K=3.724604，训练+check冻结预测13.389569h，可用31.941565h，另预留6h收尾）。23:45进入完整训练，同Run唯一派发；截至23:46:11，72fit完成0/运行4/待68/失败0，72check全待模型全局封存。累计1.869065h、余额40.130935h，扣纯资源等待2.429977s，原起点不变。完整结果留服务器，最终核心正式intake与科学判读尚待；未读科学中间效果、无Claim。XSN NO_SIGNAL关闭及原480h/全部历史保持。权威更新：`ai4s/programs/mvcnet/research/acm-r1/execution/repair1/REPORT.md`、`LAUNCH_BINDING.json`与Program STATE。


### DBCONFORMER-SOURCE-GEOMETRY-R1-LAUNCH-20261105

用户已授权并启动4编码器源内识别：A/B互斥源组×拟合会话交换，seed3/100epoch固定final，fit-only标准化，query训练后eval提取80维；24h独立预算从2026-11-04T15:00Z计本轮准备，纯资源等待独立记账，SGP旧账不移用、直接优化保持停止。唯一Run 2026-11-04_dbconformer_source_geometry_r1_lab10-full-w1 已远端核实，现场1 SCI运行/3待调度，0完成/0 SCI失败。真实TECH前向一次exit0/零optimizer，首次publication缺Transaction ID的工程失败及成本完整保留，已通过原冻结消费者派生补齐父身份恢复同Run，未改raw/合同/Bundle或重复任务。21项本轮离线与62项共享接口核验、最终55文件闭包/argv通过；Grok原NEEDS_REVISION及具体修复单列，不伪称外审改判或新科研结论。4SCI及feature完整后才按原冻结核验/精简intake/N-E-C专用分析并STOP，无自动后继或Claim。

[启动、资格与封装恢复](ai4s/programs/dbconformer/research/source_geometry_r1/STARTUP_REPORT.md)。


### DBCONFORMER-SOURCE-GEOMETRY-R1-CLOSEOUT-20261105

源内识别4次SCI均完成100epoch/3600步、每项单次attempt，无重训；远端完整manifest验证、约2.89MB analysis_v1本地核验/intake、冻结分析、独立特征重算及标准apply-decision全部完成。原判INCONCLUSIVE/STOP：16个跨会话C均正，但仅11/16编码器×被试观测过噪声相对门，4/8人在两个encoder下均通过，未达到冻结全面一致要求。停止当前对象的方法投入，不挑子组/encoder、不加seed/模块或放宽门；不否定整个几何家族、不宣称session配对增量/独立确认/论文核心。原封装失败、元数据重放、登记映射修复和成本全部保留，原合同/源包不变。State COMPLETE_MAX_ROUNDS/paused、无活动Run/operation，SGP直接优化继续停止，无Claim或自动后继。

[冻结结果与处置](ai4s/programs/dbconformer/research/source_geometry_r1/FINAL_REPORT.md)。


### DBCONFORMER-POST-GEOMETRY-REASSESSMENT-20261105

几何R1 INCONCLUSIVE/STOP后完成仅设计重评：三视角六候选及限定一手前作比较后，当前不选论文核心方法。Grok独立原判NO_QUALIFIED_CORE_DIRECTION、备选NONE，主Agent接受。只将“可独立识别的测量迁移与神经/任务变化的区分”列为条件性资料/理论问题，不接受共享模板inverse＋loss直接作新方法。必须先有非平凡识别约束、不能被后层重参数化吸收的机制控制、区别成熟逆解/低秩/平滑的必要对照及真实测量隔离/独立评价资产；门不闭合则停止该实例及同信息等价改名扩展，不从余下候选递补核心。L1源参考仅低优先备选、L2拒判仅可靠性辅助。0新训练/前向/EEG特征目标重分析/合同/Run/预算/Claim；SGP直接优化继续STOPPED，原几何对象、旧结论、成本与State暂停保留。审后补充未二次外审，不改原判。详见 `ai4s/programs/dbconformer/research/reassessment_20261105_post_geometry/research_brief.md` 与 `DESIGN_RECORD.json`。


### MVCNET-ACM-R1-CHECKREPAIR2-CLOSED-20261105
用户授权“修复并补跑检查”，原repair1因epochs=0检查入口被误作训练配置而失败，已正式INVALID收尾，72个完整拟合/8项资格及全部失败历史保留。唯一checkrepair2 Run复用已哈希核验72模型，仅执行1项来源完整性门+72项check，新增拟合/资格拟合均0；Lab10来源/成本门及独立成本复算PASS，72/72检查完成0失败，22,225,398字节核心包已verify/intake，完整产物/checkpoint留服务器。冻结原始logit独立重放与共享判读：NO_SIGNAL。P0-S0 +0.733025pp主门通过，P0-N0 +0.868056pp通过；P0-R0 +0.761960pp但seed74 -0.115741pp，违反每seed严格正向，关键对照门失败。状态COMPLETE_MAX_ROUNDS，不调参、不救援、不追加训练，无论文Claim/等价结论。原独立42h及2026-11-04T13:54Z起点不变，停机/准备/回拉/分析均计入；最终成本见ai4s/programs/mvcnet/research/acm-r1/execution/checkrepair2/analysis_20261105/FINAL_COST.json。精确关闭见ai4s/programs/mvcnet/research/acm-r1/execution/checkrepair2/analysis_20261105/PRECISE_CLOSURE.json及REPORT.md。XSN NO_SIGNAL关闭、480h及全部历史保持。
