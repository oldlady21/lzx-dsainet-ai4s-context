---
name: mieeg-ai4s
description: 在 MI-EEG 仓库中启动、恢复或审阅已登记的 AI4S Program，按唯一 Prompt Index 路由。
---

# MI-EEG AI4S

外审触发、联合审查与复用按 `ai4s/prompts/EXTERNAL_REVIEW.md`：普通探索不例行外审；高风险设计/实现按需复核；正式 Claim 联合审计一次，保留两份职责报告及真实 trace。已有冻结合同的明确要求保持有效。

## 外部审查后端与材料授权

需要外部 agent 审查时，新任务默认读取 [agy-cli-collab]([REDACTED_MACHINE])，以 `review` 模式调用 Gemini；遵循全局 AGENTS.md 与项目授权，只发送本次必需且允许的材料。既有冻结合同的 reviewer 绑定、用户明确指定的后端及平台审批仍然有效。保持原审查清单、轮次、输出结构、独立性、科学门和执行权限；审查失败或证据未读取时不得标记通过。


只在用户明确调用 `$mieeg-ai4s` 时使用。工作根目录为 `./`。这是入口路由；研究与执行规则由仓库中的活动提示词链、Program 和冻结合同维护。

1. 读取 `ai4s/PROMPT_INDEX.yaml`、对应 Program 的 `PROGRAM.yaml`、`research/STATE.yaml` 和 `research/EVIDENCE_INDEX.yaml`。绑定精确 Program、活动 operation/Run 与合同。历史 imports 和当前 round_evidence 都是证据入口；不只读取 anchor 或 last_decision。
2. 只使用该 Program 的 `active_chain`；草案不授予执行权限。新工作读取唯一 Prompt Index 所指向的活动链 L1/L2/L3；旧 campaign、Run、operation 和冻结续接读取其显式版本绑定，核对保留的单条及追加历史绑定。新链读取其 L1/L2/L3、runtime_controller；索引与 Program 不一致则阻断。控制器路径从 Program 读取，不固定旧版本。
3. 所有 Program 均使用 `scripts/ai4s/program_controller.py --program <program> guard`；原 MVCNet/DSAINet CLI 只作为共享控制器路由。目录入口与历史内容处置先读 `ai4s/README.md`。不调用已退休的旧 Bundle 生成器。
4. 查询用 `next-action`（旧 DSAINet 用 `status`）。`resume-plan` 可能写状态，不能作为纯查询。除非用户明确要求，不创建 Goal 或 heartbeat。
5. 新 v3 链依 `ai4s/prompts/TRANSACTION_RUNTIME.md` 执行。研究入口遵循“论文问题→可证伪干预→最小配对检验→结果去向”；已有 campaign 授权内的技术检查、运输与 intake 不增加人工确认门。科学 pilot 完成后必须 verified intake、分析、登记决策，才可冻结下一 Transaction；DISCOVER_NEXT 不授权实验。
6. 旧活动 operation/Run 不补写 Transaction 字段。断线先核对同一 Run，按原路径 fetch → verify → intake。提示词升级保留活动 operation/Run 的精确原绑定。旧行为参考归档 `ai4s/_work/migration_20260905/before/external/mieeg-ai4s-SKILL.md`，其中旧常量不得覆盖当前合同与用户授权。
7. start/resume 不扩张权限。远端上传和启动须有明确授权；“继续”只续接已有授权。新 campaign 使用 `continuation_policy_version=evidence_to_design_v1`，新执行授权需要完整 `research_scope`（`question_id`、`data_scope_id`、`allowed_stages`、`allowed_module_ids`、`allow_new_module`），新合同的 `governance_binding` 绑定 chain/policy/campaign/question/data。缺字段的旧对象保持旧规则；后继候选还必须给出 intervention_id、contrast、next_stage 和 source_evidence_ids，字段存在不等于获得训练权限。暂停只阻止后续派发，不杀现有任务。结果、技术证据、科研决策和论文主张分开记录。

治理与迁移状态见 `ai4s/_work/migration_20260905/IMPLEMENTATION.md`。报告已实现、已验证、已激活、真实 GPU 验收分别是什么，不将提示词草案称为已运行流程。

## 新方向构思的限定调用

按活动链 L2 的具体构思触发条件与直接推进例外选路，默认使用 `idea-creator` 的构思部分；先完整读取其 SKILL.md，再传精确 Program／实现、总览相关的基模理解、允许用于选型的本地认识、相关反例与旧案、未决问题、来源指针、输出目录及停止点。关键基模事实依 L2 首次核对规则处理，已有适用核对直接复用。原论文的问题列表是启发，允许质疑作者解释和当前拟议主张，不作为候选白名单。

调用方已准备的上下文替代 Phase 0/1 的重复准备，采用 Phase 1.5 多视角、Phase 2 构思及 Phase 3 合并。跳过 standalone 的 wiki rebuild、pilot、完整评审／报告、wiki 写入和自动后续阶段。输出回原 research 目录／brief，记录实际 `adapted` 范围与产物引用；技能不可用时主 Agent 可完成等价构思并如实注明，不假称已调用。

Foundry 继续仅由用户独立调用，使用同一来源入口；用户选择后才交接 Program，不自动创建研究或获得实验权限。同问题、来源及范围已覆盖的构思复用，新证据或问题实质变化时只补变化部分。贡献核对、限定查新及独立科研反驳按 L1／EXTERNAL_REVIEW 的条件触发，不串成每轮必经技能链。

## wait-what 项目解释规则

本节只约束通用 wait-what 的项目解释任务；不调用 AI4S 运行入口，不启动或恢复任何 Run。

Re-pitch the current object without changing it. Stay in the current conversation. Do not open a task, delegate review, score the idea, alter a contract, authorize an experiment, or upgrade evidence.

### Build the context bundle

For an AI4S research object, bind the exact Program and its baseline implementation first. Read context in this order:

1. `ai4s/PROMPT_INDEX.yaml`, the exact Program `PROGRAM.yaml`, `research/STATE.yaml`, and `research/EVIDENCE_INDEX.yaml`;
2. the exact frozen Transaction, EVALUATION_PLAN.yaml, research card, decision, evidence, round, or Run cited by the user; for a Claim ID, read its Program research/CLAIM_LEDGER.yaml revision when present;
3. applicable `AGENTS.md` for terminology and boundaries; only for a formal candidate's selection audit, benchmark, or claim confirmation, also read `ai4s/prompts/EVALUATION_EVIDENCE.md`;
4. only directly cited supporting artifacts, such as the relevant contract, verification record, analysis, protocol, or decision entry.

An AI4S Program is one baseline implementation with multiple research objects. Do not infer an object from recency, switch Program, or import unrelated project documents. Prefer targeted sections over loading whole large files when the needed section is explicitly identified.

Use this precedence when explaining the object:

```text
exact Program object and frozen contract
> Program state and evidence index
> evaluation-evidence and protocol rules
> directly cited supporting artifacts
> conversational shorthand
```

The frozen contract fixes what is being explained. The active chain and current authorization govern permitted actions; `STATE.yaml` governs runtime, the frozen contract/plan governs scope, and `CLAIM_LEDGER.yaml` is the sole authority for per-Claim judgement. A runtime or benchmark-completion status cannot replace Claim review; explanation does not activate an object or grant an action. When an old chain is active, use its frozen records and do not apply newer evaluation rules.

For a historical proposed object, use its exact `research_cycle.md`, frozen contract, and directly cited historical artifacts. It is explanation-only: do not invoke the retired skill, bind a new cycle, or revise historical state. Do not silently repair a conflict; explain the frozen meaning and name the discrepancy.

### Explain the idea

Write the explanation in the user's language; use Chinese for MI-EEG user-facing output. Use plain, concrete wording and preserve exact identifiers, formulas, paths, metrics, and protocol names when they matter.

Cover these seven points:

1. what problem remains in the baseline;
2. the one module-level change being proposed;
3. why that change might help;
4. the first fair, discriminating comparison;
5. the largest risk or confounder;
6. the exact scope that a negative result would close;
7. what is not yet claimed.

Separate established context, frozen hypotheses, and untested expectations. Do not turn literature inspiration, diagnostics, check/smoke output, or discovery evidence into a confirmed claim.

### Return provenance

Include a compact context manifest with:

```yaml
context_primary: <frozen-contract-path-and-version>
context_supporting: []
context_excluded: []
context_gaps: []
```

For AI4S, set `context_primary` to the exact Program object and frozen contract when applicable. For historical proposed explanation, set it to the exact historical object. Mark `degraded` only when a source needed to explain one of the seven points is actually missing or contradictory; mark `blocked` only when the exact object cannot be resolved safely.

For a standalone conversational re-pitch with no frozen research contract, use the last user-visible answer and the directly relevant current-conversation context, state any missing context briefly, and explain the same object more simply.

