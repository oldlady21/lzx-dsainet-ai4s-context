# AI4S 正式评估与证据解释规范

本规范只服务于已由活动链选定的正式候选：选择审计、benchmark 或 claim 确认。它不新建 Program、cycle、family、campaign 或阶段机，也不替代 Program 的 `STATE.yaml`、活动链、预算和授权。

普通探索、问题定位、研究卡片、screen 和未选候选不需要 `EVALUATION_PLAN.yaml`、`CLAIM_LEDGER.yaml` 或本规范的报告。它们仍按当前 Program 的活动链推进。Program 有活动旧链、冻结续接、活动 Run/operation 或未收尾 campaign 时，继续使用其原链；不得把本规范倒灌为旧记录的新要求。

在 v3.0／v3.1 中，Prompt Index 的活动链只决定新工作的默认规则；旧工作的精确身份和旧策略快照决定其续接规则。进入正式评估须另有冻结计划及明确授权，诊断支持或 `SCREEN_POSITIVE` 的设计准备状态不自动成为正式候选。

`scripts/ai4s/evaluation.py` 是校验 API，不提供独立 CLI。命令入口是 `scripts/ai4s/program_controller.py`。

## 1. 何时冻结评估计划

仅当活动链已要求对精确 research 做正式选择审计、benchmark 或 claim 确认时，才在对应 Program 的 `research/` 下冻结 `EVALUATION_PLAN.yaml`。计划一旦变更，必须使用新文件版本；旧计划、其 SHA-256 和 selection exposure 保留原样。

计划 schema 固定为 `ai4s-evaluation-plan-v1`，至少包含：

```yaml
schema_version: ai4s-evaluation-plan-v1
program_id: <Program ID>
evaluation_plan_id: <immutable ID>
frozen_at: <timestamp>
candidate:
  research_id: <exact research ID>
  code_ref: {path: <repo-relative path>, sha256: <64-hex>}
  config_ref: {path: <repo-relative path>, sha256: <64-hex>}
  training_rules_ref: {path: <repo-relative path>, sha256: <64-hex>}
selection_audit:
  candidate_refs: [<exact candidate or research refs>]
  decision_reason: <why this candidate is formally evaluated>
  source_refs:
    - {path: <repo-relative path>, sha256: <64-hex>}
  exposures:
    - evidence_id: <authoritative Evidence Index ID>
      outcome_exposure: untouched | seen_not_selected | selection_used | unknown
scopes: []
claims: []
```

选择审计只覆盖与本次选择相关的候选、失败、取舍和结果暴露，引用原始记录而不复制 Program 全部历史。独立审计须检查是否遗漏相关失败或选择使用，以及历史适用性映射是否得到原始资料支持；引用存在和哈希一致本身不能证明这些语义。

所有 `path`/`sha256` 引用均须指向仓库内存在文件并与实际 SHA-256 一致。候选代码、配置、训练规则和选择审计来源缺任一项，计划不成立；不能用文件名、布尔值或事后描述代替。

## 2. 精确 scope 与用途角色

每个 `scopes[]` 都须有唯一 `scope_id`，并完整冻结下列字段：

```yaml
scope_id: <unique ID>
benchmark_role: primary | secondary | stress_test | null
confirmation_role: primary_confirmation | frozen_replication | auxiliary_stress_test | null
outcome_exposure: untouched | seen_not_selected | selection_used | unknown
candidate_version: <exact implementation revision>
baseline_version: <exact implementation revision>
data: <dataset and identity>
split: <outer split identity>
preprocess: <preprocessing identity>
profile: <training profile>
seeds: [<unique non-negative integers>]
subjects: [<unique non-negative integers>]
denominator: <paired denominator>
unit: <metric unit>
selection_rule: <checkpoint or model-selection rule>
protocol: <protocol ID>
metric: <metric name>
required_result_keys: [<required finite metric keys>]
task_bindings:
  <exact frozen scientific task ID>:
    artifact: <path relative to this Run's verified intake>
    units:
      - {seed: <integer>, subject: <integer>, arm: <enabled arm ID>, implementation_revision: <exact revision>}
metric_sources:
  <required_result_key>:
    artifact: <path relative to this Run's verified intake>
    field_path: [<JSON key>, <nested JSON key>]
claim_ids: [<declared claim IDs>]
```

对新增冻结的 formal evaluation，`task_bindings` 的非空 task ID 键集必须与 Transaction 的全部科学节点 `task_scopes.*.task_ids` 精确相同，绑定 artifact 也必须与其 `task_evidence_files` 精确相同；每个科学节点的 `stage` 必须为 `full`。不得以 smoke、pilot、计划外任务或任务子集充当 formal scope；既有冻结合同不倒改为此结构。

所有 bindings 的 `units` 合并后，必须无重复并精确覆盖该 scope 的 `seeds × subjects ×` 所有声明 `arm`；同一 arm 不得有冲突 revision，且 `candidate_version` 与 `baseline_version` 都必须出现在 units 的 `implementation_revision` 中。Controller 还会将 arm/revision 精确匹配合同的 enabled arms。`EVALUATION_COMPLETE` 时，每个绑定 artifact 都必须在已核验 manifest 的 `result_files` 中，且其内容的 `task_id` 相同、`status: complete`、`operative: true`、`evaluation_units` 与该 binding 的 units 列表精确相等。

`metric_sources` 的键集合必须与 `required_result_keys` 精确相同；每个 artifact 都是该 Run 已核验 intake 内的相对 `result_files`，`field_path` 是其 JSON 键路径。分析记录的每个 required metric 必须逐值等于该冻结来源字段，不能手填、重算替换或从未纳入 manifest 的文件读取。

Benchmark 覆盖由具体 Claim 决定，不设置两个数据集、六格或五 seeds 的统一门槛；覆盖完整也不要求每格都正提升。

每个 scope 至少声明一个用途角色。`primary_confirmation` 只接受 `untouched` outcome exposure。一个真实、合格的 artifact 可以同时承担 benchmark 与确认角色，但在 Ledger 中按同一 evidence/artifact 去重，不能累加成独立重复。`yes` 必须覆盖该 claim 全部 scope 的全部冻结用途角色。`selection_used`、`unknown` 或来源不完整的证据不能经改名、补 seed 或移动文件变成独立 primary confirmation；它们最多按冻结的较窄角色解释。

每个 `claims[]` 使用唯一 `claim_id`，并包含 `statement`、`scope_ids`、`decision_rule`、`negative_consequence`。claim 与 scope 的双向绑定必须一致：scope 只能列已声明 claim，claim 只能引用已声明 scope。

## 3. 合同、结果与 intake 绑定

新 Transaction 若冻结 `execution.result_transfer.mode=analysis_v1`，已核验 intake 指本地完整的分析证据集及其绑定的远端全量核验回执，不表示本地保存全部 checkpoint。`metric_sources`、`result_files`、计划/实现/划分与必要审计来源仍须在所选范围内可访问并通过原有核验；缺少模型行为复核证据不能用汇总回执替代。原完整 manifest 保留，范围校验统一调用 `transaction.verify_intake`；旧合同及下述 legacy archive 验证要求不变。

`research_stage: formal_evaluation` 的冻结 Transaction 合同必须以 `evaluation_plan` 绑定精确计划：

```yaml
evaluation_plan:
  path: ai4s/programs/<program>/research/EVALUATION_PLAN.yaml
  sha256: <plan SHA-256>
  scope_id: <one declared scope_id>
```

合同 Program、计划 Program 和 `scope_id` 必须一致。评估授权还须显式允许 `EVALUATE_FROZEN` 并列出同一计划 SHA-256 与允许的 `scope_ids`；计划或 scope 不匹配不运行。

执行 Bundle 须通过依赖关系纳入计划中带 path/SHA-256 的候选 `code_ref`、`config_ref`、`training_rules_ref` 及选择审计 `source_refs`，并保留相同路径与 SHA-256；它们是 Bundle 的冻结输入，不能在打包、上传或 intake 时以同名文件替换。`candidate_refs` 是选择审计的标识引用，本身不构成无哈希 Bundle 依赖。

正式结果只可为 `EVALUATION_COMPLETE` 或 `INVALID`，且必须绑定：`run_id`、`scope_id`、完整 `scope_identity`、`claim_release: false|none`、`artifact_manifest` 的 path/SHA-256，以及实际 intake 中的 `result_files`。`EVALUATION_COMPLETE` 另须包含 scope 所有 `required_result_keys` 的有限数值；`INVALID` 须写 `invalid_reason`。完成只说明该 scope 的产物可判读，不释放 claim，也不自动套用 screen 的门或阈值。

## 4. 已有证据复用与历史补审

复用 Evidence Index 中的已有结果时，校验器要求：

1. `intake_status` 为 `verified_ai4s_round` 或 `verified_upstream_reference`，且不是 `INVALID`；
2. 精确 `run_id`、已核验 intake、verification marker、round contract 和 decision record 可访问且相互一致；
3. candidate/baseline revision、data、split、preprocess、profile、seeds、subjects、denominator、unit、selection rule、protocol 与 metric 全部匹配目标 scope；
4. 历史 exposure 与计划 exposure 合并后仍符合目标角色，尤其 primary confirmation 必须保持 `untouched`。同一 `run_id` 的全部 Evidence Index 别名都按最不利 exposure 合并；Ledger 既往记录中相同 evidence ID、Run 或 artifact manifest 的不利 exposure 也持续生效。

对历史结果补做审计、报告或 Ledger 解释，只能记录其已存在的证据与边界。它不等于当时已经事前冻结计划，不补造 selection audit、不会授权新运行，也不会自动把历史结果升级为 benchmark、confirmation 或论文 claim。

### Legacy archive 的按需 applicability assessment

普通新评估不填写 `historical_reuse`。只有 scope 需要复用没有当前 Transaction 合同的既有 upstream archive 时，才在该 scope 内写入一项或多项 retrospective applicability assessment；它不是新台账，也不改变原 Evidence Index 的 `evidence_id`：

```yaml
historical_reuse:
  - evidence_id: <existing authoritative Evidence Index ID>
    scope_identity: # exact values for every frozen SCOPE_FIELDS field
      candidate_version: <exact value>
      baseline_version: <exact value>
      data: <exact value>
      split: <exact value>
      preprocess: <exact value>
      profile: <exact value>
      seeds: [<exact values>]
      subjects: [<exact values>]
      denominator: <exact value>
      unit: <exact value>
      selection_rule: <exact value>
      protocol: <exact value>
      metric: <exact value>
    source_refs:
      - {path: <repo-relative original-source path>, sha256: <64-hex>}
```

每个 assessment 只对应一个既有 evidence ID，并且 `scope_identity` 必须逐字段等于该 scope；`source_refs` 必须实际存在且哈希匹配。真实独立 audit 仍须核对该 identity、原始来源引用与报告 trace，不能由 applicability 自评代替。校验器还须验证 verification marker 的同一 `run_id`、`verified_at` 和 archive SHA-256，archive 内的 `bundle_manifest.sha256` 与 intake 副本逐字相同，并逐文件以 manifest SHA-256 验证 intake；manifest 必须覆盖 `run_status.json` 与 `artifact_manifest.json`，且 Run 状态为 `complete`。

该分支只读取和解释既有 archive：不新建 Transaction、Run、Bundle、State 或 campaign。默认或别名合并后为 `unknown` 的 exposure 不能洗成 `primary_confirmation`；它仍按最不利 exposure 和冻结角色受限。

## 5. Claim review、审计与 result-to-claim trace

`CLAIM_LEDGER.yaml` 位于精确 Program 的 `research/` 下，schema 为 `ai4s-claim-ledger-v1`。每次 review 至少包含：

```yaml
program_id: <Program ID>
claim_id: <declared claim ID>
revision: <immutable review revision>
judgement: yes | partial | no | pending
evaluation_plan: {path: <repo-relative path>, sha256: <plan SHA-256>}
evidence_refs:
  - evidence_id: <Evidence Index ID>
    scope_id: <declared scope ID>
    roles: [benchmark | primary_confirmation | frozen_replication | auxiliary_stress_test]
limitations: []
gaps: []
audit_ref: {path: <repo-relative path>, sha256: <report SHA-256>}
result_to_claim_ref: {path: <repo-relative path>, sha256: <report SHA-256>}
```

每个 evidence ref 的 scope 与 roles 必须在计划中声明。`yes` 覆盖该 claim 的全部 scope 且不得保留 gaps；`partial` 必须显式列 limitations 或 gaps。`pending` 可以没有 evidence/report，用于审查未完成或输入缺失，不能被自动改写为 `no`。

除 `pending` 外，审计报告与 result-to-claim 报告都必须可读、哈希匹配，并含有：

```yaml
program_id: <same Program ID>
claim_id: <same claim ID>
evaluation_plan_sha256: <same plan SHA-256>
evidence_ids: [<the exact unique evidence IDs reviewed>]
trace_ref: {path: <repo-relative path>, sha256: <trace SHA-256>}
outcome: pass                 # audit
# or outcome: yes|partial|no  # result-to-claim, equal to judgement
```

审计必须 `outcome: pass`；result-to-claim 的 outcome 必须等于 review judgement。缺失独立审查、报告或 trace 时保留 `pending`/缺口，不能用自评替代。Ledger 的同一 `claim_id + revision` 只接受内容哈希相同的重复提交；不同内容会被拒绝。Ledger 不修改 State、轮次、预算或 active Run，也不自动写入知识库、wiki、findings、`CLAUDE.md` 或论文。

## 6. 最小命令

计划仅做只读格式与归属校验：

```powershell
conda run -n mieeg python scripts/ai4s/program_controller.py `
  --program <program_id> validate-evaluation `
  --plan ai4s/programs/<program_id>/research/EVALUATION_PLAN.yaml
```

在真实 intake、独立审计、result-to-claim 报告和 trace 都已就绪后，才记录 claim review：

```powershell
conda run -n mieeg python scripts/ai4s/program_controller.py `
  --program <program_id> record-claim-review `
  --review ai4s/programs/<program_id>/research/<claim-review>.yaml
```

第二条命令会写入该 Program 的 `CLAIM_LEDGER.yaml`，但不运行实验、不创建 campaign，也不扩张执行授权。需要执行 formal scope 时仍须遵从活动链、冻结合同与 `EVALUATE_FROZEN` 授权。

## 7. 外部审查与边界

正式完整性审计与 result-to-claim 默认由一次独立于执行者的 agy/Gemini 联合外审完成；已有冻结合同明确指定 Grok 的保持原绑定。先审完整性，再解释主张，保留两项原有清单。两份结构化报告可引用同一真实原始 trace；不要求两次调用或两个外部审查者。触发、复用及增量复审按 `ai4s/prompts/EXTERNAL_REVIEW.md`。调用方只交付精确材料、计划哈希、claim ID、evidence IDs 和指定输出位置；审查返回给 AI4S 作为 report/trace，不自行补实验、启动 pipeline、更新知识库或改变 Program 状态。审查不可用时如实写 pending/缺口；不能把缺审当成不支持结论，也不能当成支持性结论。
