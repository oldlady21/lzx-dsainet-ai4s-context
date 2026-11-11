# AI4S 工作入口

当前 Program 的唯一活动链见 `PROMPT_INDEX.yaml`。模型入口：

历史 staging、Run 或机器载荷若在本地缺失，查 [外盘归档资产指南](../docs/ASSET_ARCHIVE.md) 和精确归档索引；五个 Program 均有历史资产迁移。旧结构路径仍先按 `archive/PATH_MAP.json` 解析。资产恢复不改变 State、Evidence Index、冻结合同或实验授权。

| Program | v3.4 项目提示词（生效以索引为准） | 当前状态入口 |
|---|---|---|
| MVCNet | `programs/mvcnet/PROJECT_PROMPT_v3.4.md` | `programs/mvcnet/research/STATE.yaml` |
| DSAINet | `programs/dsainet/PROJECT_PROMPT_v3.4.md` | `programs/dsainet/research/STATE.yaml` |
| OTA | `programs/ota/PROJECT_PROMPT_v3.4.md` | `programs/ota/research/STATE.yaml` |
| DBConformer | `programs/dbconformer/PROJECT_PROMPT_v3.4.md` | `programs/dbconformer/research/STATE.yaml` |
| SST-DPN | `programs/sstdpn/PROJECT_PROMPT_v3.4.md` | `programs/sstdpn/research/STATE.yaml` |

2026-09-19：DBConformer、SST-DPN 已按用户选择接入 v2.1。历史基模与研究边界随各自 Evidence Index 引用，初始未创建 campaign 或启动实验。接入验证见 `_work/baseline_program_admission_20260919/REPORT.md`。

外审触发、联合审查与复用按 `ai4s/prompts/EXTERNAL_REVIEW.md`：普通探索不例行外审；高风险设计/实现按需复核；正式 Claim 联合审计一次，保留两份职责报告及真实 trace。已有冻结合同的明确要求保持有效。

AI4S 是新科研流程的唯一编排入口：一个基模一个 Program，内部容纳多个 research。Foundry 由用户独立调用，候选选中后只交接对应 Program；AI4S 也接受用户直接给定的方向，原有自主研究循环不依赖 Foundry。母项目负责论文问题、统一协议与写作；Program 在已授权范围内研究，正式主张以 Program Claim Ledger 为唯一判定源，论文材料引用它，不自动改写 PAPER.md。历史 proposed 只作为来源，不继承其状态机或运行权限。

## 每次任务的读取顺序

1. 从 `PROMPT_INDEX.yaml` 找到 Program 条目，结合 State 中所选对象的身份选链：新设计用 active_chain；已有 Run／operation／冻结续接用其精确旧工作绑定。共享 L1/L2 本轮只读适用版本，模型差异查对应 L3。
2. 查运行时读取 `PROGRAM.yaml` 与 `research/STATE.yaml` 的 active_run、active_operation、campaign/续接身份；查结果时用 `research/EVIDENCE_INDEX.yaml` 的精确 evidence ID。由这些引用定位合同、准备记录、staging 或 intake，不从目录新旧或标题猜当前对象。
3. 只读取所选对象的文件及核验所需直接引用。旧路径按 `archive/PATH_MAP.json` 解析；仅在缺少明确路径时做该 Program 内的窄文件名检索，避免递归扫描所有 research、staging、intake 与第三方代码。
4. 部署准备按 `prompts/TRANSACTION_RUNTIME.md` 的“包内资源策略摘要”与“新启动接口的离线验收”；查新包实际资源字段及源码身份先读包内 `RESOURCE_POLICY_SUMMARY.json`，异常再核对冻结合同与所列 runtime。摘要缺失的旧包沿其原合同/源码读取，不现场改包补摘要。
   各 Program 新合同冻结前运行 `python scripts/ai4s/transaction.py validate-new --contract <合同路径>`；缺少精简回传策略会阻断冻结续接、打包和新 Run 登记。按该文档“精简回传”填写实际分析依赖；全 Program 历史实验归档/本地清理使用 [全库执行提示词](prompts/ALL_PROGRAMS_HISTORICAL_CLEANUP_AGENT_PROMPT.md)。覆盖实际目录与索引外实验，不限 checkpoint、大文件或 Lab10 匹配项；盘点清单仅作定位，保留端及消费者仍逐项核验。
   字段、返回结构、遥测补写或来源子清单发生变化时，按 runtime“字段接口与产物闭环”验证实际生产者到消费者，运行原统一入口的 `--suite interfaces`；通用接口通过不替代 Program 专属分析／复用分支覆盖。近期案例与修复见 [_work/retro_field_contract_20261028/REPORT.md](_work/retro_field_contract_20261028/REPORT.md)。
5. 用 `python scripts/ai4s/program_controller.py --program <program> next-action` 查动作。摘要、日志和解释均不授予执行权限；按原授权及冻结规则推进。

MVCNet 和 DSAINet 均已接入 Transaction v2。接入不启动实验；当前状态仍以 State 为准。旧 VOGD operation 已按用户授权关闭，未记为 verified intake 或科学负结果。

## 正式评估与版本激活

五个 Program 的新工作默认链已激活 v3.4。既有 campaign、冻结 Run 和执行授权沿用原绑定。见[激活验收](_work/prompt_v34_implementation_20261111/ACTIVATION.md)。

2026-10-29：L1/L2 与五 Program L3 v3.3 已交付。MVCNet、DSAINet、SST-DPN 的新工作链已激活；OTA 后经用户明确授权、旧 SPAR 本地完整性复核与历史收尾，亦已激活 v3.3，继续暂停。DBConformer 在 SBN-R1 收尾后，依用户明确指令完成空闲边界检查并激活 v3.3，继续暂停，本轮仅下一方向设计。旧工作、合同及预算保持原绑定，没有新实验授权。当前详情以 Prompt Index 和 State 为准；[初始实施与验收](_work/prompt_v33_implementation_20261029/REPORT.md)、[OTA 后续激活](_work/ota_v33_activation_20261029/REPORT.md)、[DBConformer 接入与研究设计](programs/dbconformer/research/reassessment_v33_20261029/research_brief.md)。

新工作读取索引指定的 L1/L2/L3。已有工作按其精确旧绑定收尾；普通探索不建立正式评估台账，正式候选的选择审计、benchmark 与 Claim 确认按 `prompts/EVALUATION_EVIDENCE.md`。

用 `python scripts/ai4s/activate_evaluation_governance.py --program <program> --target-version 3.4` 只读预览。v3.4 要求空闲边界、就绪检查及完整父绑定；已有活动 Run／operation／待续接或未收尾 campaign 时阻断。`--apply` 才切换获准 Program 的新工作默认链，不改 State、历史合同或实验权限。后续切换时重新核对状态与授权。

基模理解、可用的历史认识、反例与未决问题从各 L3 的唯一研究总览入口读取。新方向构思按活动 L2 和 `prompts/MIEEG_AI4S_SKILL_ROUTER.md`；明确的高价值下一步直接推进，Foundry 仍独立调用。

历史版本仅在追溯相应工作时读取：[MVCNet v3.2](_work/mvcnet_v32_activation_20261024/REPORT.md)、[DSAINet v3.2](_work/dsainet_v32_activation_20261023/REPORT.md)、[DBConformer／SST-DPN v3.2](_work/prompt_v32_activation_20261020/REPORT.md)、[v3.1](_work/prompt_v31_activation_20261008/REPORT.md)。历史部署与验收依据继续见 [启动接口](_work/launch_interface_20261014/REPORT.md)、[资源摘要](_work/resource_summary_20261014/REPORT.md)、[调度](_work/deployment_optimization_20261010/REPORT.md)；不把这些记录里的旧状态当作当前状态。

## 从研究准备到结果回交

新项目先按 `prompts/PROJECT_ADMISSION.md` 将用户需求与已有证据生成独立 L3，并确认接入。已有项目先读取冻结边界，在明确 campaign 目标、预算、执行器与授权后设计候选。v3 新候选使用单份 `research_brief`（问题、文献、实施、对照）和唯一冻结 Transaction v2 科学配置；`SCREEN_NEW` 只核对 research_brief 路径与 SHA-256，旧链继续要求三卡。DISCOVER_NEXT 只设计。

按时长自主推进时，agent 在授权内持续完成“累计证据综合 → 下一问 → research_brief 与科学配置 → 冻结合同 → 执行 → 决策”。尚缺 research_brief、配置或合同意味着继续准备；一轮 NO_SIGNAL 不自动停止整个 campaign。准备器只从已冻结 contract 生成 Bundle/manifest，不自动把 research_brief 展开为完整科学合同。新合同的 governance_binding 使用 `chain_id`、`continuation_policy_version`、`campaign_id`、`question_id`、`data_scope_id`。完整的停止条件与默认监测节奏见 L2“按时长自主推进”。ccmu 专用 GPU0 的后台短暂占用按共享资源策略等待，不采用其他 PID 一出现就退出的门。

填完整共享 `prompts/TRANSACTION_CONTRACT.template.yaml`，通过科学与 Transaction 校验，生成不可变 Bundle、登记 Run。技术 smoke 在同一 Transaction 内按依赖执行；科学 pilot 在决策边界停止。随后 fetch → manifest verify → intake → 身份/闭集核验 → Codex 分析 → 决策登记。后续 Transaction 沿用研究预算与 seed 上限；新 campaign 不能洗掉历史关闭边界。

[REDACTED_MACHINE]/lab10 的连接信息在 Program.executors；Lab10 容量规则见 `experiments/REMOTE_LAB10_AI4S.md`。自动与手动运输使用相同合同与启动器；授权中包含相应操作即可自动推进，不逐项要求用户报 PASS。真实服务器/GPU 验收状态单列，不以离线测试替代。

Lab10 校内用 `[REDACTED_MACHINE]`，校外用 `[REDACTED_MACHINE]` 经 `[REDACTED_MACHINE]` 跳板。完整 SSH 配置集中在 `experiments/REMOTE_LAB10_AI4S.md`；切换连接链路时继续核对同一 Run，不重新提交实验。

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


2026-10-24 后续状态（VBR-R1 首次派发与旧Run最终收尾）：旧Run已完成标准intake并以NO_SIGNAL收尾。新VBR-R1首次Run在source-import工程失败，0资格/科学拟合，Program已登记INVALID并暂停；路径修复已过真实CPU18划分验收，一次修复Run仍待授权。见 [派发报告](programs/mvcnet/research/vbr-r1/execution/LAUNCH_REPORT.md)。上文设计/准备记录保留当时状态。
