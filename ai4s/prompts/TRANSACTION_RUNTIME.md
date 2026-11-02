# Transaction v2 本地执行接口

本接口供 Prompt Index 已激活的 Transaction v2 科学合同使用；v3.0／v3.1 提示词仍沿用此合同。活动提示词与既有工作的适用规则按唯一索引及精确旧工作绑定核对。

## 合同与任务产物

### 字段接口与产物闭环（v3.2 原版内维护，2026-10-28）

共用整数、身份与技术门仍由 `scripts/ai4s/transaction.py` 校验。JSON 类型敏感的新消费者使用 `read_typed`；冻结身份计算沿原读取/规范化规则，不全局替换旧 `read`。数值等价转换仅按明确字段语义进行，布尔、缺值、非有限值、分数 epoch、单位或数据角色冲突不靠宽松解析通过。

新生产路径的调度结果读取使用 `scripts/ai4s/execution_observations.py::read_scheduler_task(record, source=...)`：来源明确选 `lab10_capacity`（`attempt`）或 `lab10_shared_executor`（`attempts`），返回 `attempt_count` 等共用观测。两者是不同生产接口，不互猜字段名；此投影不授予重试或改变原 attempts 限制。真实时间/显存未知保持未知，不补造观测。

该适配覆盖实际 worker 行，以及带完整 family-blocked 标志的 capacity 零次尝试占位行（`NOT_EXECUTED`，进程耗时/退出未知，调度占位码单列）。FCA 最终 admission-deferral 行有另一套标志和子进程时间，当前 NOT_COVERED，不套用上述普通投影；保留原记录，由该路径实际写入者与消费者完成专用闭环后才接入。适配拒绝不自动证明训练失败。

新写入者补充完整进程遥测时用 `transaction.attach_execution_observations`，只更新允许的实测字段，并同步已存在的顶层镜像和嵌套 `technical`；不补 `operative`、`finite` 或 PASS。旧原件有冲突先保留失败，不通过取一边掩盖。汇总异常保留首因，附 node/task/证据路径；验证函数返回的上下文不能再当 raw JSON 消费，科研专属字段继续由实际 Program 消费者定义。

新合同模板显式 `execution.artifact_manifest_policy=root_reserved_v1`：只有根层的生成清单/运行锁等保留文件不进入自身清单，来源目录内的 `artifact_manifest.json` 必须封存并可进入精简选集。生成与校验共用同一枚举策略；字段缺失保留历史按文件名排除的语义，未知值拒绝。旧 Bundle/manifest 不补字段或重封，新字段不追溯改变旧 Run。

准备器对最终选用的 runtime 做选择器能力探针并绑定复制前后 SHA；该探针仅证明纯选择器行为和封存/核验的静态引用，不执行模块顶层或模型。新规则与精简回传并用时，最终包仍须验证 full seal → compact export → verify，样例同时含子 manifest 和子 dispatch 回执；自定义／钉住中间版本不能仅凭 selector 探针就声称完整回传闭环通过。

准备记录只补实际变化涉及的“字段 → 写入/补写函数 → 消费函数 → 样例/失败反例”，可直接放现有 CPU 验收记录。至少经真实生产函数、实际调度补写、node 汇总与相应分析/复用入口；受影响的回传选集也须覆盖嵌套来源清单。分析函数无 CPU 安全入口时如实列未覆盖并补其最小无训练夹具，不用通用假 worker 冒充。共享检查运行 `python tests/run_ai4s_transaction_regression.py --suite interfaces`；完整最终包 argv 验收继续原 `check_bundle_commands.py`，接口测试不替代 GPU/科学资格。

新共享测试使用真实调度生产函数的 CPU 子进程输出，保留缺字段、来源混用、重复镜像冲突和子清单遗漏的反例。检查器和写入方共同修改时，反例至少有一个来自原始失败形状，避免双方共同迎合错误 fixture。现有活动科研路径只按原权限修复，此规则本身不派发、补训或放宽门。

### 精简回传（新合同 `analysis_v1`）

**新合同冻结前检查（所有 Program，2026-10-29 起的新创建动作）**：从项目根目录运行 `python scripts/ai4s/transaction.py validate-new --contract <合同路径>`，草案可先检查，再按原规则冻结。成功返回 `intake_scope=analysis_v1`、清单模式数与包上限；此命令只读，不改合同或授权。现有 `freeze-continuation`、`prepare_transaction_bundle.py` 与 `record-run` 共用 `require_new_result_transfer`，新 Transaction v2 身份缺少／置空策略即拒绝，不再静默退到全量；修改前已冻结但未打包／登记的合同由 `FROZEN_FULL_INTAKE_CONTRACTS.json` 固定精确 canonical SHA 保留原行为，运行入口不会自动扩充该表，换 Run／Bundle 等字段后不再匹配；空清单、占位符、非正整数上限／超时及未知模式沿现有语义校验拒绝。新身份／新修复包从历史合同复制时同样填写实际依赖，不能以复制旧合同代替新合同检查。

检查只验证明确策略及字段合法性；冻结前仍沿下文核对真实分析／复用依赖与预计体积，最终包继续已有 full seal → compact export → verify 验收，不据此新增训练或重复实验。分析确需模型文件时显式列入，或在已有授权内远端分析后回传绑定输出；不自动扩大上限或删减关键证据。

已有冻结 Run／Bundle 的 `validate`、核验、fetch 和恢复保持原路径，不补字段或重打包；字段缺失仍按原全量规则。新创建入口的拒绝不能作为修改旧对象的理由，旧对象的运输修复另按精确授权处理。表外历史冻结合同重新打包／登记受阻时，核对原冻结来源及旧入口，按精确授权补兼容；不为过新门改写旧合同。该边界与提示词版本无关，OTA 也对后续新 Transaction 合同默认启用，但不切换其活动链。

已完成旧 Run 的只读工程验收可在独立目录显式调用共享导出/核验函数的 `snapshot_policy` 参数；此路径保留原合同和身份，使用独立 `engineering_snapshot_v1` 回执，标准 intake 必须拒绝。仅用于验证选择集、真实运输和分析依赖，不给旧 Run 补写策略，不登记为正式 intake，不调用其 controller 改写状态。实际验收记录见 `_work/compact_acceptance_20261027/REPORT.md`。

新合同使用模板中的 `execution.result_transfer`：`mode=analysis_v1`、`include` 为相对产物路径模式列表、`max_bytes` 为本地包上限、`remote_verify_timeout_seconds` 为远端完整核验和运输的有界超时。模板的 100 MiB 是回传包上限，不是科研门或资源预算；冻结前按实际依赖估算，超限时报告待调整，不静默删证据或改冻结值。每个模式至少匹配一个原 manifest 条目，使用 `/`；匹配采用区分大小写的 fnmatch，`*` 可跨路径段。填写精确子目录和文件名，避免把所有 JSON、NPZ 或非 checkpoint 文件都纳入。

回传必备集自动包含 Run/Transaction 状态、所有节点结果、任务证据、复用证据回执及排队计时文件（供 controller 保持原预算记账）。`include` 另外覆盖分析器实际读取的预测、样本/划分身份、标签来源、seal、必要日志及分析输出。仅保留汇总指标而丢失判读所需证据不合格；依赖 checkpoint 的分析须在授权范围内远端完成并回传绑定输入哈希的输出，或把所需 checkpoint 显式纳入回传。精简接口本身不运行分析器、不启动模型、不增加科学节点。准备时用完整输入与所选证据分别验证拟用分析入口，确认结论一致；未知依赖应先查清，不用形式上的 intake PASS 代替科学判读。

运输仍从 controller `advance --operation fetch` 进入。Bundle 内 `transaction.py export-analysis` 先在服务器执行完整原 manifest/身份/任务闭集核验，再在原 Run 目录之外发布 `<remote_output>.analysis-v1`。它保存原完整 `artifact_manifest.json` 和带选择清单、核验时间、核验器 SHA、原产物路径的 `ANALYSIS_INTAKE.json`；原载荷和 manifest 保持不变。已发布包与同一原 manifest 绑定后可复用，回执时间表示当时核验，不宣称后来每次都重新验过远端载荷。

自动 fetch 先核对包字节数与本地可用空间，再只取这个包，通过 SSH 回执、冻结 Bundle 核验器 SHA、本地逐文件哈希与集合闭合检查后才发布下载目录。小包传输中断可重新取包；不会把未验收的部分下载登记为 intake。手动 handoff 同样提供 `prepare_analysis_export` 和精简 fetch 命令，先导出再下载；统一 materialize 和 controller/正式评估的 `verify_intake` 读取同一范围校验。

精简 marker 显式记录 `intake_scope=analysis_v1`、`full_payload_local=false` 和回执哈希。`verified` 仅表示冻结分析证据集通过，不表示本地拥有全量资产，也不释放 Claim；正式评估继续要求冻结结果文件与其所有既有科学门。恢复训练、重放推理及完整归档另按原清单按需取件。

2026-10-28 用户明确授权的 FCA-R1 packfix80 回传修复为单 Run 兼容例外，见 `programs/dbconformer/research/fca_r1_repair5_packfix80/intake_recovery_v1/ADDENDUM.json` 及同目录验收记录。其原合同、Bundle 和完整 manifest 均不改写；原全部 include 模式在“原 manifest 加 58 份独立绑定子清单”的补充索引上执行，每个子清单文件项仍须锚定原完整 manifest 的同一 SHA。新增独立回执 `ai4s-analysis-intake-recovery-v1`，正式验收范围显式为 `analysis_v1_recovery`、`full_payload_local=false`；本地入口同时固定精确 Run、原合同 canonical、补充记录和验收实现 SHA。完整远端核验、原数据资产、完整科学分析绑定、核心闭集与 54 项独立复算仍为必需；原工程快照不能直接改标签进入正式 intake。此兼容不适用于其他 Run，不授予训练或 FCA-R2 权限，不释放 Claim。

字段缺失的旧冻结合同保持完整本地验收，不能修改旧 Bundle 或补写该字段使已有 Run 静默迁移。已结束历史实验的归档和本地清理按 [全 Program 执行提示词](ALL_PROGRAMS_HISTORICAL_CLEANUP_AGENT_PROMPT.md)另行核对当前消费者与存储保留事实；历史完整验收不改写为局部验收，当前仍要求全量本地载荷的步骤继续保护。远端目录存在、精简包验收通过均不构成删除历史唯一副本的依据。

`scripts/ai4s/transaction.py validate` 是必需的语义校验器；共享模板为 `TRANSACTION_CONTRACT.template.yaml`。在 Program 原有科学合同上加入完整 transaction、task_scopes、technical_pass_rules、execution.transaction_timeout_seconds 和 campaign_id。冻结身份、矩阵、科学阈值与预算仍须通过 Program 校验。

每个 scope 冻结 task_ids、task_evidence_files、argv、依赖、结果位置和超时。每个实际任务写独立 JSON：transaction_id、contract_sha256、run_id、node_id、task_id、status=complete、operative=true；技术任务另含真实 technical 观测。operative 必须来自实际路径检查，不能由包装器默认填 true。科学任务保留原指标、单位及来源。节点结果必须绑定逐任务文件哈希，单独提交汇总 JSON 不足以通过。

任务 launcher 完成后可调用 `transaction.py emit-result --contract <合同> --output <任务产物根> --run-id <Run> --node-id <节点>`，聚合器核对原始任务产物后生成节点结果。它不运行模型、不生成科学判断、不从退出码推断候选生效。Lab10 capacity 的任务输出在 `task_attempts/<task_id>/<attempt>/`，launcher 按冻结 task_evidence_files 汇集成功尝试，保留所有失败日志。不得将 smoke checkpoint 自动作为科学任务初值。

`prepare_transaction_bundle.py --contract <合同> --source <源码根> --destination <新Bundle>` 只接受 frozen 合同，递归收集可静态解析的本地 Python import，复制未修改依赖并生成 source_manifest。配置文件、动态 import、插件和数据入口仍须显式列在 requirements，并由实际 smoke 检查。静态闭包不等价于完整环境可运行证明。模板不是可直接提交的科学合同。

v3.1 新建或修改执行路径的验收按 `LEVEL2_EXECUTION_v3.1.md` 第4节完成产物闭环：真实写入端、下游读取端和实际节点汇总器一起检查。准备器只负责校验与封包，不自动完成这项验收；工程样本不代替正式任务闭集。遇到汇总失败，按同节报告具体 task、字段／路径和原异常，不只复述节点失败。旧工作仍按其绑定规则执行。

共享 `transaction.py` 的技术报告消费者接受无 `technical` 对象的既有扁平报告；已有该对象时以其为权威，外层字段只核对一致性、不补缺项，尤其不能用任务外层 `operative` 补造技术检查。整数计数字段作严格等价解析后再汇总，原文件哈希不变。混合层级旧产物需另有明确来源与语义核验的项目适配记录；兼容不改变必需字段和门限。

## 授权与自动推进

以仓库根目录、mieeg 环境运行共享控制器。`authorize-transaction --authorization <文件>` 的输入精确包含 campaign_id、executor_id、allowed_operations、allowed_transitions、authorization_ref；最后一项指向用户授权的仓库记录。命令不创建 campaign，不重置轮数或预算。没有明确授权时不能自行生成授权记录。

`record-run` 和 `freeze-continuation` 保留原入口，但 v2 会核对 Program、合同、executor、run_prefix、bundle_id 和科学转换。

旧策略的 SCREEN_NEW candidate_qualification 分别绑定问题、文献和实现检查工件及其 SHA-256。v3.0 新候选只绑定一份含问题、文献、实施和对照的 `research_brief` 及其 SHA-256；科学参数仍由唯一冻结 Transaction v2 合同保存。现有 Bundle 准备器从冻结合同生成依赖闭包与 manifest，不从 research_brief 自动生成科学合同。record-run 的 planned_units 必须等于科学任务与本 Transaction 内技术任务总数，复用旧技术证据不重复计入。

### v3.0 治理绑定与续接

五个 Program 的新 campaign 在创建时记录 `continuation_policy_version: evidence_to_design_v1` 与生效链 ID；原 campaign、Run、operation 和冻结续接按 Prompt Index 中的精确旧工作绑定读取原策略。新执行授权除原有字段外，必须有 `research_scope`，精确列出 `question_id`、`data_scope_id`、`allowed_stages`、`allowed_module_ids` 与布尔值 `allow_new_module`。新合同的 `governance_binding` 冻结链、策略版本、campaign、问题及数据范围；控制器登记前逐项核对。

结果后的处理先看 verified intake 与科学后继资格，再看授权范围、暂停和预算。支持性诊断或筛查只有在结果记录提出具体 `next_design`（干预 ID、对照、阶段、精确 transition、证据引用）且符合已授权 scope 时，才进入下一轮设计准备；该状态不直接启动新 Run。没有具体干预时记录设计约束与缺口，PROMISING_INCOMPLETE 先辨明完整性或科学门不足。单轮、暂停、预算耗尽、无效实验及缺授权均停止后续派发。`next-action` 返回精确机器剩余秒数，同时提供易读时间；底层预算判界不取整。

手动运输使用 `program_controller.py --program <program> transaction-handoff` 获取已登记 Run 的命令；与自动运输共用远端领取和启动身份。旧 upload-instructions 不接受 v2 Run。手动交接不会增加节点或绕过 scientific_stop_boundary。

`next-action` 只读。`advance` 默认选择一个确定性运输步骤；可以显式指定 `--operation upload|launch|probe|fetch|intake`。Codex 在授权内循环推进并间隔监控：上传 → 启动 → 核对远端 ledger → 拉回 → 文件/manifest verify → intake → 身份/闭集核验 → Codex 分析 → apply-decision。进入 ANALYZING 后 advance 不会继续 full，也不会自动编写科研结论。

`apply-decision` 核验真实 intake，并要求分析绑定当前 round、Run、Transaction。决策文件为不可覆盖的恢复记录；证据索引与 State 可以据此补齐。同一分析重复登记不重复计轮，不同分析不能覆盖已登记结果。

## 恢复与失败

Lab10 校外可使用 `[REDACTED_MACHINE]` 经 `[REDACTED_MACHINE]` 跳板，校内直连为 `[REDACTED_MACHINE]`。配置和命令见 `experiments/REMOTE_LAB10_AI4S.md`“校内直连与校外跳板”。这是同一目标的连接改道，保留原 RunId、路径与 executor；自动运输使用 Program.executors.lab10.host，不能假定已自动切换。断线先从可达链路核对原 Run，不能以直连失败为由新建任务。

运输脚本的远端目录领取、节点运行锁与 Program 锁防止重复派发。未知远端状态保留同一 Run，不能用“没有回执”推断从未启动。重复 fetch 复核已有下载；一致的部分 intake 可以补齐；冲突文件拒绝合并。最终 PASS 后 manifest 写入中断可恢复封存，不重跑节点。

进程超时终止同组子进程；失败节点阻断科学后继。进程在 RUNNING 时发生宿主崩溃，当前实现返回 RECONCILE_SAME_NODE，不自动重训。上传中断或启动领取后未落 ledger，同样保留现场，核对后再恢复；这些不能声称已实现无人干预恢复。

Lab10 的 max_attempts_per_task 默认 1，合同可明确设为 2 或 3。只对检测到的 OOM 自动重试；保持相同 task/Run、独立尝试目录，累计墙钟，增大家族预留并退到低并发。耗尽次数阻断该家族。新 Transaction 不会由重试自动创建。

## 容量与旧证据

ccmu_lab GPU0 按用户 2026-09-06 授权作为个人专用卡管理。新 Bundle 必须冻结 execution.ccmu_resource_policy；从 Program.executors.ccmu_lab.resource_policy_defaults 复制并按本次技术画像调整。共享 runtime 在实际节点启动前检查资源，允许后台程序存在，仅按可用显存、温度和剩余预算准入；不会因为其他 PID 或残留 PID 立即失败，也不杀其他程序。显存不足或温度高时每 15 秒重采样，新合同 `execution.queue_time_policy: exclude_resource_wait` 下持续等待，不受 900 秒资源等待上限截断，也不消耗节点/Transaction 的实际执行预算。历史 `wall_clock` 合同仍保留原等待上限。温度上限为 90°C。

无画像时 minimum_free_mib 默认 12288，是候选 smoke 的初始准入值，不是已验证峰值或任意模型的容量保证。有适用完整进程峰值时，新合同冻结适用完整进程需求，不再统一额外加 1024 MiB；超出默认容量的新候选先检查再安排科学任务。该策略不扩展至 Lab10，不改 batch/AMP，也不提高任务并发。

新多任务 launcher 每次训练启动前调用 `transaction.guard_ccmu_task(task_id)`；该适配器核对冻结节点与任务身份，从合同读取同一策略，按冻结计时策略扣除纯资源等待，并记录逐任务资源观测。取消候选脚本内另写的 20480 MiB、发现外来 PID 立即退出等重复门；节点级门不能替代任务间准入。资源等待不读取效能。历史冻结 launcher 保持原样，不能将新策略回写旧 Bundle 后重启。

next-action/advance 无活动 Run 时会给出剩余时间、授权转换和四项研究准备义务。agent 必须实际完成这些工作，再冻结登记下一 Run；脚本本身不会调用语言模型生成卡片。预算到期返回 CLOSE_CAMPAIGN_BUDGET_EXHAUSTED，不能仍把过期 campaign 显示成可研究授权。

普通准确率的新容量合同按用户 2026-10-11 授权采用实验室宽松共卡：从 Program.capacity_defaults 冻结 `admission_mode=capacity`、`allow_same_owner=true`、`allow_external_compute=true`、`concurrency_policy=memory_only`、`max_jobs_per_gpu=null`、`memory_headroom_policy=lab_permissive_v1`、`memory_reserve_mib=0`。适用于五 Program 的 Lab10，以及已接入共享容量调度的 DBConformer CCMU。外部进程及无法解析其归属不单独否决准入；GPU 利用率只排序，不干预或终止其他任务。准入仍核对可信实时空闲显存、未实体化启动承诺与 90°C 温度上限。科学耗时测量继续按 isolated 合同隔离，不继承这些共卡默认。

`lab_permissive_v1` 取消需求之外的统一 10% 系数、512 MiB 固定附加与公共余量；合格完整进程峰值直接作为测量需求，适用的既有需求估计和真实失败约束仍保留。零余量不等于零需求：未知需求继续使用有依据的正数估计，沿用未知家族渐进放量与有界 OOM 恢复。尚未体现在驱动空闲值中的本项目启动承诺仍原子登记并扣除，已实体化显存不重复扣减。共享执行器的独立只读 `preflight` 须显式传 `--memory-headroom-policy lab_permissive_v1`，此时推导零余量，显式非零余量视为参数冲突；不传仍按旧预检默认，不能用旧模式的拒绝判定新策略。该政策只随新冻结合同及包含实现的新 Bundle 生效；缺字段的旧合同、legacy_per_task 和 shared_gpu_reserve_v1 保持原语义，不能原地改旧包续跑。

未知家族从并发 1 开始，以 launcher 及后代进程的驱动显存观测逐步放量。verified_profiles 绑定 evidence_ref/sha256、VERIFIED_INTAKE、family、完整进程峰值及硬件/驱动身份；配置、形状、精度或源码变化须使用不同 family。普通准确率任务可共卡，耗时比较使用 measurement_mode=isolated；尚不支持自动证明“匹配负载”条件。

旧 B0/P1 operation 从 State/Evidence 指向的归档路径读取；历史内文中的旧路径使用 `ai4s/archive/PATH_MAP.json` 解析。复用需逐项审查输入、源码、环境、度量含义与有效期，引用实际产物。旧 JSON 缺少新检查字段时不能填造 True，也不能把旧 PID 差值标记直接升级成新遥测证明。适用证据可制作带来源哈希的审核记录；不因迁移强制重跑整段 100 epoch。

## 执行可靠性与设置校准

本节用于 v3.1 新准备工作及已授权的工程修复。使用共享验收、调度与资源模块；研究目录中的旧副本不会随共享源码更新自动升级。准备新 Bundle 时核对实际依赖闭包及源码哈希。旧 Run、冻结合同、已封存 Bundle 与原始证据保持原身份；不能直接替换远端文件后续跑。

- **时间预算**：分别记录资源等待、任务实际执行、节点收尾。先定位数据加载、设备初始化、首步、训练与产物写出的耗时；阶段尚无观测时写未知，不用节点总耗时猜训练瓶颈。节点限额须容纳可实现并发下的任务波次及调度、验收和收尾；四个 300 秒任务可能串行时，1250 秒仅剩 50 秒余量，不能按四卡同时结束估算。任务达到上限不自动证明上限不合理；已有相同形状快速完成的对照时先查性能回退。新限额须在既有预算内明确冻结，不自动延长旧 Run。
- **线程与并发**：已冻结线程数在 Python 数值库导入前设置，并核对实际 intra/inter-op 线程和相关环境变量。未知家族先低并发，取得生产形状完整进程观测后再渐进放量；OOM、CUDA 资源错误或明显吞吐下降时停止扩张。不静默修改 batch、AMP 或科学训练参数。
- **显存画像**：区分初始估计、适用的实测峰值和 OOM 后的保守重试估计。调整估计须绑定 family、源码、形状、精度、设备与完整进程证据，并遵循冻结策略；`increase_only` 不允许运行中擅自下调。B0/C0 的画像不能直接代替 P1，小 batch 不能代替生产 batch。需求超过物理容量时报告不可行，不无限等待；不通过降低安全余量掩盖 OOM。
- **遥测与状态**：采样应在训练主流程之外，有查询超时、停止等待上限及开销记录，避免各层重复查询。采样频率按覆盖需求和实测开销选择，不能把降低频率当作已证明峰值覆盖。缺失或过期观测记 UNKNOWN，不写作真实零显存或直接改训练退出状态；冻结技术门要求的全进程证据仍须满足。监控断线不触发重发、杀进程或重试。
- **封存与恢复**：任务清单只包含已停止写入的稳定产物；仍更新的调度／遥测日志在 Run 收尾时封存。只改消费者时优先重放原产物，保留原始哈希、修复代码身份及派生校验记录。已完成任务只有满足原合同的逐任务复用资格才可接收；缺少恢复接口或原规则禁止部分复用时，保留缺口，不自动跳过任务，也不默认整套补跑。

上述规则是准备与验收义务，不声明所有历史 launcher 已具备阶段探针、画像下调或任务级恢复能力。每次修复记录真实实现入口、离线回归范围和未完成的目标设备验证。

2026-10-10 的共享 Lab10 实现保留 1 秒采样间隔，将进程显存查询放入独立线程并设置查询截止时间；失败观测不阻断正在运行的任务，准入观测未知则暂停新派发。`memory_only` 模式按调度器内的同一 family 跨 GPU 从一个任务起步，成功且取得正向完整进程观测后逐步增加；`fixed_count` 保留原有单 GPU 上限。此处并发作用域不代表已实现多个独立调度器间的全局家族资格协调。具体离线验收及未覆盖范围见 `ai4s/_work/execution_reliability_20261010/REPORT.md`。

## 新工作的部署、预算与恢复

本节只用于后续准备的新工作及明确授权的新修复包；不修改旧 Run 的资源门、计时、画像策略或恢复资格。

1. **部署前一次预检**：从项目根目录执行 `python scripts/ai4s/program_controller.py --program <program> deployment-preflight --operation launch`，汇总状态、轮次、预算和授权等可判定阻断（上传检查用 `--operation upload`）。报告“具体原因 → 受影响操作 → 最小补齐项”，不要把不同拒绝统一称为预算耗尽。未知远端状态仍须核对同一 Run；本地预检不联网、不派发；`ready` 只表示其覆盖的本地检查通过，完整部署验收与远端资源仍须按原执行路径核对。
2. **预算一次说明白**：列出累计上限、原起点、已耗、已核验排队／停机扣除、剩余、估算来源与缺口；申请追加时同时列新增量和新累计上限，并在登记／派发前刷新。没有适用运行画像时保留冻结超时推导的保守估计，明确它不是预计实际训练时长。不能为了准入缩短真实期限、清空历史成本或把等待批准自动抵扣；需改变未来计时策略时另行明确范围，旧账不追改。
3. **普通训练按容量调度**：新 Lab10 合同从 Program 的 `capacity_defaults` 复制再冻结。五 Program 的新默认允许 `verified_profile` 校准；只有来源哈希、family、设备／驱动、生产形状及完整路径均合格时才可替换初始估计。无画像继续使用原估计，OOM 后不凭较低单次读数下调。既有 `increase_only` 合同保持原策略；新宽松政策的余量与共卡按上文显式字段冻结，GPU 利用率只排序；CPU 负载不设统一硬门，耗时比较按 isolated 契约执行。
4. **扫描全部可派发任务**：一次资源扫描检查依赖已满足的全部 pending；一个任务暂时放不下不阻断独立任务。只有完整、可信的允许设备总容量均不足时才登记永久不可容纳；快照缺失／未知、暂时空闲不足和温度超限继续保留为等待。无法容纳的家族不伪造训练失败尝试，不消耗额外重试；最终任务闭集仍完整记录。
5. **最小工程恢复**：先核对真实失败位置及既有资产，再选离线消费重放、同 Run 运输核对或原合同允许的任务恢复。生产代码变更必须有新源码身份，旧包不原地替换。包准备记录所用共享模块版本哈希与已验输入；打包器保留源码闭包中明确声明的 runtime，仅在未声明时注入当前共享 runtime；固定旧 runtime 时明确哪些新修复未进入该包。没有实现或没有授权的恢复保持待准备，不承诺通用自动续跑。

部署优化与科学判定分开：当前门服务初筛、确认还是归因须在新设计冻结前明确；完整性不合格不是科学负结果，有效科学负结果也不是工程重试理由。已有授权内的准备、检查和传输衔接不额外增加人工审批，真正缺少的阶段、额度或范围一次说明。

## 激活边界

v3.0 激活时核对 active_run、active_operation、pending_continuation 与 campaign，并将精确身份和原研究策略保存到 Prompt Index 的旧工作绑定。Program 新工作入口切换后，旧对象仍用原策略收尾；绑定不完整时阻断控制动作。各 Program 独立激活；新链只从索引进入本接口，不因校验失败降级。

当前尚未执行真实 GPU 验收。离线测试仅证明相应合同与控制路径，不证明 MVCNet 新候选性能、容量峰值或远端端到端成功。


## 排队与执行分别计时（2026-09-07）

新 campaign 从 Program.defaults 继承 `queue_time_policy: exclude_resource_wait`，合同必须冻结同名 execution 字段并与 campaign 一致。研究设计、上传、技术检查实际执行、训练、拉回与分析照常计时；只扣除共享 runtime 记录的纯资源等待，不重置轮数、seed 或修复预算。

Lab10 调度器在没有运行任务而等待容量/温度/账号锁时，持续更新绑定 Run、Transaction 和节点的 queue clock；已有任务运行时不会扣除其他任务排队时间。ccmu 在节点及任务准入时使用同一时钟。服务器后台执行器持续排队，不需要本地 agent 不断 SSH 才能启动。`probe` 返回 `WAIT_FOR_RESOURCES` 和独立的 wall_seconds、queue_seconds、execution_seconds；排队状态不是技术失败，不能重发 Run。

控制器在身份校验后的 probe、verified intake 和失败元数据登记时累计每个 Run 的排队时间，重复读取只取最大累计值，修复 Run 不清空原 campaign 账本。实际执行超时、进程崩溃、SSH/服务器故障仍需按原恢复流程处理。心跳停止后不无限增加排队抵扣。

本策略只适用于携带新共享 runtime 的新冻结 Bundle。旧合同缺字段仍按原 wall_clock 策略恢复；不能修改其哈希或自行给旧 campaign 增加时间。生成新 launcher 时必须使用共享资源门/调度器；不要额外套一个将排队计入其中的 shell timeout 或固定墙钟截止时间。训练任务本身的超时从实际启动算起。


## 用户只读终端看板（2026-09-10）

共享入口 `scripts/ai4s/monitor.py` 在本地 PowerShell 运行，通过 SSH 读取远端控制状态及 nvidia-smi，不上传代码、不写实验目录。每次 transaction-handoff、advance upload/launch 返回 `monitor_powershell`；agent 必须将这条精确命令交给用户。命令绑定 Run、远端输出目录和执行环境 Python，并沿用实际 host（包括 [REDACTED_MACHINE]）。

默认每 15 秒刷新；追加 `--once` 只看一次。Ctrl+C 仅停止观察。目录尚不存在、断线、部分 JSON 或陈旧快照是观察未知，不等于实验失败。表中的容量承诺不是未实体化预留，不能混为一项。旧执行器未提供的计数/进度显示未知；没有调度快照的 ccmu launcher 仍可显示 Transaction、排队时钟与 GPU 状态。无需修改旧冻结 Bundle。

看板不读取预测、准确率或 loss，不承担科研判断。实际启动交付命令并不等于已核验远端运行，仍需原 probe 流程。实现验证与原版差异清单见 `ai4s/_work/monitor_20260910/REPORT.md`。


## 上传后自动启动（用户持续规则，2026-09-16）

用户要求“上传实验/上传这个包/部署实验”时，默认包含对该明确选定、已冻结实验的上传后启动和启动状态核对。准备→合同/依赖校验→登记 upload、launch、probe 授权→上传→自动启动同一Run→probe核对→交付监控命令，不能只完成上传便结束或再询问是否启动。不因此扩展科学矩阵、预算或后续研究阶段。

“只准备/只打包/给我命令”不授权实际上传启动；“只上传/不要启动/先上传等我通知”显式覆盖自动衔接，此时使用 advance --operation upload --upload-only。用户手动上传时交付启动及监控命令，不擅自执行远控；用户确认已上传后，若已授权agent继续执行，则核对同包完整性后衔接启动。

advance 的上传成功回执先持久化，再自动调用同一控制器launch（重新校验暂停、预算及身份）。已有历史机器授权缺launch时不篡改合同或静默越权：agent依据本持续规则及当前上传请求记录授权补充，继续同一Run；若原请求明确仅上传，则保持原限制。上传失败不得启动；启动回执不等于运行成功，必须probe。断线或启动状态未知先核对远端领取/ledger，不重复提交。


## 2026-09-23 温度与分阶段资源策略

用户授权新任务默认最高温度90°C（超过90仍等待）。Program与模板显式冻结90；历史缺字段合同的兼容默认80不改写，已有Run不可静默修改源码/合同后重启。

每个task_scope可声明resource_profile：gpu_training（兼容默认）、gpu_light、cpu_analysis。准备每个节点时按实际算子/设备选择，不能直接从full复制资源计划，也不能只凭audit/diagnostic名称假定轻量。

- 文件校验、指标重算、统计、报告等无需GPU的步骤：cpu_analysis，直接用CPU launcher，显式CPU设备；runtime隐藏CUDA并跳过GPU温度/显存准入，误入GPU调度器时报配置错误，不排队等卡。
- checkpoint前向、轻量特征提取等仍用GPU：gpu_light，必须冻结该节点自己的memory_commitment_mib（包含合理余量），独立任务家族；不继承full峰值画像。Lab10 新普通容量工作沿用上述 lab_permissive_v1 共卡及 memory_only、启动预留/温度保护；ccmu节点与任务准入使用该节点显存承诺。设备访问和实际容量边界不因名称放宽。
- 含训练/完整反向或真正科学效率比较：保留对应训练或isolated策略。不得为了提速改变batch、AMP、矩阵或读取中间效能。

full结束不等于自动授权新科学诊断；既有verified intake与分析边界不变。CPU分析的线程/内存预算仍应按实际负载安排，资源类别不授予无限并行。


## 新启动接口的离线验收（2026-10-14）

新普通容量 launcher 使用包内共享 `build_contract_run_command` 生成 `run` 命令。资源政策只从冻结 `execution.capacity` 读取；`--contract-resources` 选择该路径，运行参数不复制 `preflight` 的 `--memory-headroom-policy`，不另填余量、温度或利用率阈值。旧入口未选择此路径时保留旧 CLI 语义，不能重写旧 Run。

准备时从实际 launcher 捕获每个节点的完整 argv（拦截派发，不调用 GPU），用最终 Bundle 的实际 parser 校验。调用 `scripts/ai4s/check_bundle_commands.py --bundle <final_bundle> --commands <captured_commands.json>`；命令记录包含 node_id、包内 launcher/executor 路径、launcher SHA-256 和完整 argv。检查冻结源码 manifest、全部节点覆盖、任务闭集、包内执行器与 cwd、Run 身份、包外产物目录。报告保存到准备记录目录，不写入冻结 Bundle。该检查只解析受检查 parser 定义，不运行模型、任务或模块顶层初始化；无法提取 parser 的定制执行器须明确未覆盖，并补该真实入口的离线检查，不能用共享 parser 冒充。

再用准备目录内的合成任务验证输出目录、证据格式和实际消费者；只验证工程接口，不读科学效果、不启动生产任务。最终包解析成功与合成消费成功分别记录。准备检查完成后运行 `python tests/run_ai4s_transaction_regression.py --suite launch`；统一完整回归沿用不带 --suite 的入口。缺失检查保持待准备，不增加实验授权或人工审批。


## 包内资源策略摘要

新 `prepare_transaction_bundle.py` 在最终源码与冻结合同复制完成后生成 `RESOURCE_POLICY_SUMMARY.json`，并将其纳入 source_manifest。摘要是派生产物，唯一执行配置仍是冻结合同；不能编辑摘要改变策略，也不为旧冻结 Bundle 原地补文件。

先读摘要定位实际 executor/runtime哈希、逐节点GPU/CPU资源类别、GPU允许列表、共卡/并发、需求与公共余量、温度、画像引用、总尝试数和超时/排队策略。合同明确声明的值与静态可确认的实现兼容分列；缺源码、固定旧runtime或定制实现的未知能力保持 UNKNOWN/NOT_VERIFIED，不用工作区最新默认替代。CPU分析不继承GPU准入；节点专属GPU/轻量需求按该节点合同覆盖说明。

上传前最终包检查复核摘要与合同、包内源码和manifest一致，并在准备记录中保存摘要哈希。源码静态兼容不等于真实GPU容量或服务器验收；运行期间真实预留、峰值与排队状态仍读该Run的运行产物。摘要缺失的旧包只读原合同/源码。检索步骤以 README“每次任务的读取顺序”为唯一入口，不另建活动索引或参数表。
