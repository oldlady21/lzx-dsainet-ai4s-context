# AI4S 工作入口

AI4S 按基模设置 Program，每个 Program 可以容纳多个 research。母项目维护论文问题、共享评估协议和写作，Program 在各自的活动链与授权范围内推进研究。当前 L1/L2/L3 组合以 [Prompt Index](PROMPT_INDEX.yaml) 为准，具体运行看 State，证据看 Evidence Index，需要正式判断某项 Claim 时再查适用的 Claim Ledger。

Foundry 独立生成候选，由用户选择后交接给相应 Program。用户也可以直接提出研究方向。Foundry 的交接不会自动创建 research 或启动实验，历史 proposed 流程只用于追溯原有记录。

| Program | 配置 | 运行状态 | 证据 |
|---|---|---|---|
| MVCNet | [PROGRAM](programs/mvcnet/PROGRAM.yaml) | [State](programs/mvcnet/research/STATE.yaml) | [Evidence Index](programs/mvcnet/research/EVIDENCE_INDEX.yaml) |
| DSAINet | [PROGRAM](programs/dsainet/PROGRAM.yaml) | [State](programs/dsainet/research/STATE.yaml) | [Evidence Index](programs/dsainet/research/EVIDENCE_INDEX.yaml) |
| OTA | [PROGRAM](programs/ota/PROGRAM.yaml) | [State](programs/ota/research/STATE.yaml) | [Evidence Index](programs/ota/research/EVIDENCE_INDEX.yaml) |
| DBConformer | [PROGRAM](programs/dbconformer/PROGRAM.yaml) | [State](programs/dbconformer/research/STATE.yaml) | [Evidence Index](programs/dbconformer/research/EVIDENCE_INDEX.yaml) |
| SST-DPN | [PROGRAM](programs/sstdpn/PROGRAM.yaml) | [State](programs/sstdpn/research/STATE.yaml) | [Evidence Index](programs/sstdpn/research/EVIDENCE_INDEX.yaml) |

## 每次任务的读取顺序

1. 从 `PROMPT_INDEX.yaml` 找到 Program 条目，结合 State 中所选对象的身份选链：新设计用 active_chain；已有 Run／operation／冻结续接用其精确旧工作绑定。共享 L1/L2 本轮只读适用版本，模型差异查对应 L3。
2. 查运行时读取 `PROGRAM.yaml` 与 `research/STATE.yaml` 的 active_run、active_operation、campaign/续接身份；查结果时用 `research/EVIDENCE_INDEX.yaml` 的精确 evidence ID。由这些引用定位合同、准备记录、staging 或 intake，不从目录新旧或标题猜当前对象。
3. 只读取所选对象及核验所需的直接引用。先用 [历史路径映射](archive/PATH_MAP.json) 解析旧路径。历史 staging、Run 或其他机器产物在本地缺失时，按[外盘归档资产指南](../docs/ASSET_ARCHIVE.md)查对应索引、清单和批次回执。缺少明确路径时，在该 Program 内按文件名查找。
4. 部署准备按 `prompts/TRANSACTION_RUNTIME.md` 的“包内资源策略摘要”与“新启动接口的离线验收”；查新包实际资源字段及源码身份先读包内 `RESOURCE_POLICY_SUMMARY.json`，异常再核对冻结合同与所列 runtime。摘要缺失的旧包沿其原合同/源码读取，不现场改包补摘要。
   各 Program 新合同冻结前运行 `python scripts/ai4s/transaction.py validate-new --contract <合同路径>`；缺少精简回传策略会阻断冻结续接、打包和新 Run 登记。按该文档“精简回传”填写实际分析依赖；全 Program 历史实验归档/本地清理使用 [全库执行提示词](prompts/ALL_PROGRAMS_HISTORICAL_CLEANUP_AGENT_PROMPT.md)。覆盖实际目录与索引外实验，不限 checkpoint、大文件或 Lab10 匹配项；盘点清单仅作定位，保留端及消费者仍逐项核验。
   字段、返回结构、遥测补写或来源子清单发生变化时，按 runtime“字段接口与产物闭环”验证实际生产者到消费者，运行原统一入口的 `--suite interfaces`；通用接口通过不替代 Program 专属分析／复用分支覆盖。近期案例与修复见 [_work/retro_field_contract_20261028/REPORT.md](_work/retro_field_contract_20261028/REPORT.md)。
5. 用 `python scripts/ai4s/program_controller.py --program <program> next-action` 查动作。摘要、日志和解释均不授予执行权限；按原授权及冻结规则推进。

### v4 追加核验与阶段汇报

本节用于绑定 v4 共享执行规则的新工作和未冻结研究复盘。冻结工作按精确原链、合同和授权执行。

- **追加核验前先说明它会改变哪个决定。** 在现有 brief、分析记录或进度汇报中，写明待决问题、要补齐的证据缺口，以及不同结果各自会怎样改变去留、设计、主张范围或原定资格判定。能用既有证据决定就直接收尾。正反结果都不会改变决定时，保留已有认识并停止追查。
- **有明确决策价值时完成整组必要核验。** 在现有授权、数据角色、预算及冻结边界内，自主完成足以作出该决定的检查和复算。用已有覆盖排除重复工作。达到预定证据或停止条件后，直接登记决定，并进入已获准的下一项行动。新异常只有会改变决定才继续查；确缺数据、权限或额度时，说明具体阻塞和停点。
- **阶段汇报先给四项。** 当前研究问题、所在阶段、已做决定及其依据、当前停点。若继续，注明唯一下一项行动和完成条件；若暂停或结束，注明恢复条件或已关闭的范围。技术细节放在四项之后，复用原 brief、结果或交接记录。

MVCNet 和 DSAINet 均已接入 Transaction v2。接入不启动实验；当前状态仍以 State 为准。旧 VOGD operation 已按用户授权关闭，未记为 verified intake 或科学负结果。

### MVCNet 与 DSAINet 的新研究委托

本节从下一次新委托起，适用于索引中绑定 L3 v4.1 的 MVCNet 与 DSAINet。按当次任务确定可做的阶段、数据、预算与交回点。仅设计、仅核查、暂停或只上传均按用户指定范围执行。已有委托和冻结工作沿用原约定。

- **选下一项。** 在选案时用现有 brief 说明：哪条论文判断仍未解决，候选与最强简单解释在哪个条件下预测不同，结果将改变什么取舍。MVCNet 对照其 L3 中的跨人类别线索与利用条件；DSAINet 对照其 L3 中的线索保留、共享与尺度分工问题。优先选能解决重要未知的方案，再选足以区分解释的最低成本验证。关键对照和适用边界补证也可优先；仅改善局部近似或少量参数的方案，按它能回答的问题或可实测的效用与成本确定优先级。
- **选验证方式。** 冻结保真直接检验候选的预测时，才用它决定科学去留，例如检验低成本替换能否保住某条判别信息。效应依赖共同学习时，零训练只核查必要前提，如输入线索可观测、干预生效、对照匹配。数据合格、有可证伪预测和必要对照后，按 [L2 的有限联合训练规则](prompts/LEVEL2_EXECUTION_v4.0.md#2-用现有-brief-完成一页决策)设计最小比较，训练规模随问题确定。零步接线、梯度或恒等回退通过只说明技术可行。
- **串行续接。** 在获准自主寻找候选时，一次推进一项。候选失败就登记其关闭范围；只要仍有可区分的新预测，实际开始下一项，续接限于已获准的阶段。例如仅授权构思时只推进设计。若只是换算子却仍在检验同一个预测，先结合历史反例换一个解释。允许的证据和资源已无法区分剩余解释时，说明试过什么、缺什么以及重新推进的条件；连续失败次数本身不决定整项委托的去留。
- **模型分工。** GPT-6.2 Sol High 负责日常构思（提出备选、整理历史反例）、执行已定核查、判读结果并给出去留建议。进入具体 idea 设计、选定关键对照或决定候选去留时，由 GPT-6.2 Astra High 担任主 Agent，依据证据作决定。定案后的日常工作交回 Sol High，出现下一个研究决策时再由 Astra High 主持。
- **执行方式。** 宿主支持切换主模型时按上述阶段切换。主模型在会话内固定时，可用 Astra High 主会话串行委派 Sol High 完成日常工作并回收证据，沿同一委托推进。若当前是 Sol 主会话且无法切换主模型，到决策点时带着待决问题、关键证据和备选对照交接给 Astra High 主会话；按实际执行者记录。外部第二意见及机制反复或关键证据冲突时的定向复核仍由 Neon High 承担，见[科研交叉思考](prompts/EXTERNAL_REVIEW.md#科研交叉思考)。
- **按授权交回。** 首个达到有限训练资格的候选，按当次授权推进。若停点是训练前，交回证据、关键对照与最小训练方案。仅授权上传时核实上传回执即交回。授权到派发时，完成冻结、资格与派发；若只有上传回执或远端状态未知，继续核对同一 Run。核验已运行或按合同合法等待资源后，交回 Run ID、实际状态和只读监测入口；核验确实受阻时报告最后已知状态及缺口。若已授权到结果判读，则继续到约定停点。

## 正式评估与版本激活

当前活动链以 Prompt Index 为准。正式候选的选择审计、benchmark 和 Claim 判断按 `prompts/EVALUATION_EVIDENCE.md` 执行，普通探索不建立正式评估台账。外审何时触发、如何联合审查及复用，见 [`prompts/EXTERNAL_REVIEW.md`](prompts/EXTERNAL_REVIEW.md)。普通探索不例行外审，高风险设计或实现按需复核；正式 Claim 采用一次覆盖完整的联合审查，并保留两份职责报告和真实 trace。冻结合同已有的审查要求继续有效。

2026-11-19（北京时间）：MVCNet 新工作启用 L3 v4.1。2026-11-21（北京时间）：DSAINet 新工作启用 L3 v4.1。两者沿用 L1/L2 v4.0，精确激活依据和历史绑定见 [Prompt Index](PROMPT_INDEX.yaml)。

2026-11-17：DSAINet、MVCNet 与 DBConformer 的新工作默认链先后激活 v4.0。各 Program 的当前版本查 [Prompt Index](PROMPT_INDEX.yaml)，既有 campaign、冻结 Run 和执行授权按精确绑定读取。见 [v4.0 离线验收](_work/prompt_v4_design_20261116/REPORT.md)与 [v3.4 激活验收](_work/prompt_v34_implementation_20261111/ACTIVATION.md)。

2026-10-29：L1/L2 与五 Program L3 v3.3 已交付。MVCNet、DSAINet、SST-DPN 的新工作链已激活；OTA 后经用户明确授权、旧 SPAR 本地完整性复核与历史收尾，亦已激活 v3.3，继续暂停。DBConformer 在 SBN-R1 收尾后，依用户明确指令完成空闲边界检查并激活 v3.3，继续暂停，本轮仅下一方向设计。旧工作、合同及预算保持原绑定，没有新实验授权。当前详情以 Prompt Index 和 State 为准；[初始实施与验收](_work/prompt_v33_implementation_20261029/REPORT.md)、[OTA 后续激活](_work/ota_v33_activation_20261029/REPORT.md)、[DBConformer 接入与研究设计](programs/dbconformer/research/reassessment_v33_20261029/research_brief.md)。

新工作读取索引指定的 L1/L2/L3，已有工作按精确旧绑定收尾。

2026-09-19：DBConformer、SST-DPN 已按用户选择接入 v2.1。历史基模与研究边界随各自 Evidence Index 引用，初始未创建 campaign 或启动实验。接入验证见 `_work/baseline_program_admission_20260919/REPORT.md`。

### v4.0 激活检查

`python scripts/ai4s/activate_evaluation_governance.py --program <program> --target-version 4.0` 生成只读预览。激活前须满足空闲边界、就绪检查及完整父绑定；存在活动 Run、operation、待续接或未收尾 campaign 时，检查会阻断。获准时使用 `--apply` 切换该 Program 的新工作默认链。激活不改 State、历史合同或实验权限。再次切换前重新核对状态和授权。

基模理解、可用的历史认识、反例与未决问题从各 L3 的唯一研究总览入口读取。新方向构思按活动 L2 和 `prompts/MIEEG_AI4S_SKILL_ROUTER.md`；明确的高价值下一步直接推进，Foundry 仍独立调用。

[正式文献库](../refs/papers/_index/README.md)是各 Program 共享的外部研究依据。Program 的历史记录说明本地已经试过什么、哪些解释仍然成立；文献库补充其他研究提出过的机制、区分这些机制的对照，以及结论成立的实验条件。构思时可以从其他领域借来一个能产生不同预测的解释，也可以用最近邻工作检验候选的创新之处。迁移到当前基模后是否有效，由本地实验判断。具体问题按[共享检索规则](prompts/MIEEG_AI4S_SKILL_ROUTER.md#新方向构思的限定调用)按需查证。

实验室发来新 PDF 时，按[增量入库手册与可复用提示词](references/LITERATURE_INTAKE.md)整理收件箱、更新正式库并验证新增条目的检索结果。

历史版本仅在追溯相应工作时读取：[MVCNet v3.2](_work/mvcnet_v32_activation_20261024/REPORT.md)、[DSAINet v3.2](_work/dsainet_v32_activation_20261023/REPORT.md)、[DBConformer／SST-DPN v3.2](_work/prompt_v32_activation_20261020/REPORT.md)、[v3.1](_work/prompt_v31_activation_20261008/REPORT.md)。历史部署与验收依据继续见 [启动接口](_work/launch_interface_20261014/REPORT.md)、[资源摘要](_work/resource_summary_20261014/REPORT.md)、[调度](_work/deployment_optimization_20261010/REPORT.md)；不把这些记录里的旧状态当作当前状态。

## 从研究准备到结果回交

新项目先按 `prompts/PROJECT_ADMISSION.md` 结合用户需求和已有证据准备独立 L3，再确认接入。已有项目则先核对冻结边界、campaign 目标、预算、执行器和授权。适用 v3 链的新候选用一份 `research_brief` 说明问题、文献、实施和对照，并使用唯一冻结 Transaction v2 科学配置；`SCREEN_NEW` 核对 brief 路径及 SHA-256，旧链仍按绑定要求使用三卡。`DISCOVER_NEXT` 阶段只形成设计。

按时长自主推进时，agent 在授权内持续完成“累计证据综合 → 下一问 → research_brief 与科学配置 → 冻结合同 → 执行 → 决策”。尚缺 research_brief、配置或合同意味着继续准备；一轮 NO_SIGNAL 不自动停止整个 campaign。准备器只从已冻结 contract 生成 Bundle/manifest，不自动把 research_brief 展开为完整科学合同。新合同的 governance_binding 使用 `chain_id`、`continuation_policy_version`、`campaign_id`、`question_id`、`data_scope_id`。完整的停止条件与默认监测节奏见 L2“按时长自主推进”。ccmu 专用 GPU0 的后台短暂占用按共享资源策略等待，不采用其他 PID 一出现就退出的门。

填完整共享 `prompts/TRANSACTION_CONTRACT.template.yaml`，通过科学与 Transaction 校验，生成不可变 Bundle、登记 Run。技术 smoke 在同一 Transaction 内按依赖执行；科学 pilot 在决策边界停止。随后 fetch → manifest verify → intake → 身份/闭集核验 → Codex 分析 → 决策登记。后续 Transaction 沿用研究预算与 seed 上限；新 campaign 不能洗掉历史关闭边界。

[REDACTED_MACHINE]/lab10 的连接信息在 Program.executors；Lab10 容量规则见 `experiments/REMOTE_LAB10_AI4S.md`。自动与手动运输使用相同合同与启动器；授权中包含相应操作即可自动推进，不逐项要求用户报 PASS。真实服务器/GPU 验收状态单列，不以离线测试替代。

Lab10 校内用 `[REDACTED_MACHINE]`，校外默认用 `[REDACTED_MACHINE]` 经 `[REDACTED_MACHINE]` 跳板。完整 SSH 配置集中在 `experiments/REMOTE_LAB10_AI4S.md`；切换连接链路时继续核对同一 Run，不重新提交实验。

2026-11-12 用户确定执行地点。各 Program 的新长时实验默认绑定 Lab10，包括完整训练、跨折或跨 seed 批量拟合、长时审计和持续占用本机计算资源的诊断。本机执行短时低负载的源码核对、单批 smoke、小样本 TECH 与精简结果复算。选址以实际耗时和持续资源占用判断。已有 Run 按冻结执行器收尾。需迁移的未完任务先核对已封存资产、继续或复用资格以及目标端成本，并按该 Run 的授权和预算门推进。

## 目录职责

| 路径 | 用途与编辑边界 |
|---|---|
| `prompts/` | 当前共享 L1/L2、接入规范和唯一新合同模板；各版本提示词以独立文件保存 |
| `programs/<program>/PROGRAM.yaml`、`PROJECT_PROMPT_*` | 当前配置与项目 L3；有效版本由索引指定 |
| `programs/<program>/research/` | 当前 State、Evidence Index 和本轮工作；已关闭内容归档 |
| `archive/programs/<program>/research/` | 已关闭合同、决策、失败、operation、交接与研究资料，按原文件名检索 |
| `archive/programs/<program>/bundles/` | 历史不可变 Bundle，每个 Bundle 保持完整内部目录 |
| `archive/programs/<program>/tools/`、`templates/`、`configs/` | 仅用于历史复核的工具、诊断源码和配置 |
| `references/` | 共用参考资料；资料不是执行授权 |
| `archive/pre_transaction_v2/` | 旧可变规则、提示词、模板和生成器的完整原文；只供追溯 |
| `archive/engineering/` | 历史回传来源、tmp 检查与工程诊断 |
| `_work/` | 本地治理记录和审计快照 |

旧 controller、模板和生成器已从日常目录删除，完整原文仅在 archive。历史文件迁移保持字节不变；当前索引已改用新路径。旧不可变记录中的原路径由 `archive/PATH_MAP.json` 精确映射，读取历史路径不授予执行权限。最新治理验收见 `_work/structure_20260905/REPORT.md`；Transaction 实现范围见 `_work/migration_20260905/IMPLEMENTATION.md`。


AI4S Transaction 新合同的资源排队不计入实验预算；上传并启动服务器后台执行器后，同一 Run 自动等资源并执行，不因排队时长失败。实际执行超时仍生效；旧冻结 Bundle 保留原规则。计时字段和恢复方式见 `ai4s/prompts/TRANSACTION_RUNTIME.md` 的“排队与执行分别计时”。


上传/启动后必须交付只读终端看板命令 `monitor_powershell`，由共享 transaction-handoff/advance 自动生成。详见 `ai4s/prompts/TRANSACTION_RUNTIME.md` 的用户只读终端看板段。


2026-09-16：用户要求上传实验时默认自动衔接同一冻结Run的启动与probe；明确只上传时用 --upload-only。执行规则见 ai4s/prompts/TRANSACTION_RUNTIME.md。


## 历史运行记录

以下为当时的交接记录。MVCNet 的现行状态查 [State](programs/mvcnet/research/STATE.yaml)。

2026-10-24 后续状态（VBR-R1 首次派发与旧Run最终收尾）：旧Run已完成标准intake并以NO_SIGNAL收尾。新VBR-R1首次Run在source-import工程失败，0资格/科学拟合，Program已登记INVALID并暂停；路径修复已过真实CPU18划分验收，一次修复Run仍待授权。见 [派发报告](programs/mvcnet/research/vbr-r1/execution/LAUNCH_REPORT.md)。上文设计/准备记录保留当时状态。
