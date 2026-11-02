# DSAINet 基线研究 Evidence Map

更新：2026-08-26  
用途：汇总 DSAINet 当前本地/已回拉的冻结实验记录，作为后续诊断或新 family 准入时的证据边界索引。本文不创建新 cycle、不改变既有状态，也不释放性能、机制、新颖性或论文 claim。

## 0. 先读结论

当前最简洁的基线图景是：

1. 在 **BNCI2014001 official-preproc LOSO** 的冻结 45-checkpoint 面板中，两个 branch 的实际时间影响尺度可分，且 branch index 与实际功能身份跨 seed 稳定。
2. coarse branch 对 source-only temporal support 有位置特异性依赖；但 support 本身不足，非 support context 仍是必要组成。
3. 已经关闭的是几条**精确实现路线**，而不是更宽泛的问题：hard routing、support modulation、以及以 index/function mismatch 为前提的 permutation-invariant set fusion。
4. 001 的稳定尺度身份不能外推到 004。004 中 scale-specific learned residual，尤其 branch2，常近 identity 或不可观测；CSRPA 已定位其 downstream slot path，SCPRA 则关闭了当前 scope 的 performance-repair anchor。因此这是已刻画的条件依赖现象，而不是可直接训练的修复方向或仍待准入的候选入口。
5. 001 上 B0 的 pooled branches 确有强、稳定的 classwise same-trial dependence；但 RACR-v0.1 的 54-unit paired screen、其 source-only residual pairing audit，以及后续固定 interaction probe 均未给出稳定的 joint discriminative utility。因此“native additive readout 漏掉可用 conjunction”的窄命题目前没有证据锚点。

所有“已证明”均指通过冻结完整性门的**范围受限 machine diagnostic**。现有 records 的外部 `experiment-audit` / `result-to-claim` 均为 `REVIEW_UNAVAILABLE`，因此 `claim_release=none`。

## 1. Evidence map

| 层级 | 当前状态 | 冻结证据与范围 | 可以保留的结论 | 不可扩写为 |
|---|---|---|---|---|
| scale separation | 已被支持 | RBIA-v0.1：BNCI2014001 official-preproc LOSO、45 checkpoints、每 checkpoint 64 held-out trials；两支 learned residual 均可观测 | `[11,15]` branch 相对 `[3,7]` branch 的 empirical effective-scale ratio 中位数为 `2.1556`，9/9 targets、5/5 seeds 通过预冻结方向门 | 固定生理时间尺度、fine/coarse 生理语义，或跨 dataset 恒定的尺度身份 |
| branch stability | 已被支持 | 同一 RBIA 面板的 activation、pooled、contribution 三个 same-vs-swap CKA 诊断 | 三个 panel 均达到 same-index stable；两支 contribution RMS 与 true-class margin 均为实质、非单支退化 | 所有任务/数据集/训练条件下都稳定，或两支必然低相似、完全独立 |
| support/context relation | 已被支持 | SCCD-v0.1：BNCI2014001 LR22、9 targets x 2 seeds、126-row zero-training factorial | support 相对等占用 shifted support 有稳定优势（`+15.567–17.303 pp`）；hard support-only 的 `2.141 pp` 损失中，non-support content 删除占 `63.96%`，position scaffold 删除占 `36.04%` | support 足以替代全上下文、support conditioning 必然带来收益，或 support 是精确生理中心 |
| hard routing | 已关闭 | SAFSS-v0.1 的 coarse-only support projection（54 evaluations）与 ESFS-v0.1 的 fixed event-subsequence fine specialization（54 predictions） | SAFSS P1-B0=`-2.141 pp`；ESFS P1-B1=`-0.309 pp`、P1-B0 虽 `+0.212 pp` 但跨 seed 不同向；固定 support/event route 没有在各自 frozen scope 形成稳定净效用 | 所有 event/full 或所有跨 branch routing 都无效；可通过换 window、seed、mask、branch 再救援 |
| support modulation | 已关闭 | FCPSM-v0.1：BNCI2014001 LR22、18 tasks、90 arm evaluations、72 source-only scalar fits、90 predictions | 保留 full context 的单标量 coarse support modulation 未通过四个 stable-positive contrast；P1-B0=`+0.174 pp`，但 seed0/1=`-0.116/+0.463 pp`；P1/B1 15/18 单元预测相同 | support 无价值、coarse 对 support 不敏感，或可用当前剂量/标量作后验 rescue |
| permutation fusion | 已停止，缺失前提锚点 | DCBS-v0.1 仅证明 ordered-concat classifier 对 slot order 敏感；其后 RBIA-v0.1 得到 `aligned_stable`，index/function mismatch=`no_signal` | slot dependence 不是 function mismatch 的证据；原 descriptor-conditioned permutation-invariant set-fusion child 不再 ready，budget 仍 `0/1` | set fusion 已被性能反证。该 child 没有创建、训练或作 exact-paired performance 测试 |
| branch interaction | 未知 | CBLR-v0.1 关闭 stable non-zero lag/local-response anchor；BSRA-v0.1 显示 inter-attention 放大 final similarity，但 learned-delta use 不双向可替代 | 现有证据不支持以稳定 lag/equalizer 为起点，也不支持以高 CKA 为由直接做 decorrelation/diversity/fusion child | interaction 不存在、inter-attention 无用，或任何新 interaction 都不可能有效 |
| same-trial conjunctive readout | 已在固定 RACR/readout scope 关闭；广义 interaction 仍未知 | RACR-v0.1：001 LOSO，B0/P1/M1 × 2 seeds × 9 targets 共54 units；r5 source-only pairing audit、18-checkpoint B0 CKA diagnostic 与18-unit fixed logistic interaction-probe diagnostic | P1−B0 overall `+0.000 pp`，P1−M1 seed1 为负，P1 residual pairing drop 为0；B0 CKA drop `+0.607858`（两 seed 正、9/9 target过门），但 `[p1;p2;p1⊙p2]` held-out source probe 相对 additive 的 true-pair NLL 为 `-0.056406` nats，未形成稳定 label utility | stable dependence 即可转化为可用类别联合信息、RACR interface 有可修复缺陷、或应创建 RACR child |
| adaptive realization | 路径已定位；当前 repair 路线 no-go | CRBRA + CSRPA + SCPRA：004 45 checkpoints；零训练 path audit + 原始 full-test performance link | branch2 有 active/collapsed 双态，collapsed slot use 由 downstream attention 承载；但 source-only alpha 与 target-controlled accuracy rho=`-0.0621`，active−collapsed accuracy=`-0.246 pp`，没有 stable harm anchor | optimization lock-in 已被因果证明、collapse 有害，或 alpha/init/regularizer/module/branch weighting 会改善性能 |

## 1.5 Potential intervention link：从证据事实到研究问题

本表是后续 idea generation 的输入层：它只把已有事实翻译为**待验证的研究问题**，不登记 family、不给出方法结论，也不继承已关闭路线的预算、信号或执行授权。

| Evidence 事实 | 当前可保留的解释 | Potential intervention link：可形成的研究问题 | 已知边界 |
|---|---|---|---|
| scale separation | 001 的两支实现了可观测、方向一致的不同 effective temporal scale | **如何利用已经真实存在的 scale interaction，而不是先验强制分离？** 需要先问：interaction 在何层、何种样本或何种 decision condition 下具有独立效用 | 不把 nominal kernel 或尺度方向解释为生理事件；不能直接训练 scale regularizer、强制 alpha floor 或 branch reweighting |
| branch stability | 001 中 branch index 与 realized identity 稳定对齐，两支都对决策有实质贡献 | “readout 是否充分使用两支差异化贡献”已由 RACR-v0.1 作过一个窄的 ordered low-rank product 检验；其结果无稳定 utility。若未来另提问题，必须改变 baseline defect，并独立给出直接 falsifier | 不得把稳定 role、B0 CKA dependence 或 RACR 的 inactive residual 改写成接口 bug；RACR 不得以 rank/gate/seed/child 救援 |
| support/context relation | support 位置有用，但 non-support context 与 positional scaffold 共同构成有效处理 | **能否在不删除 context 的前提下，按条件分配或调度 evidence？** 关键不是找更窄 support，而是识别“何时、为何、以何种因果方式”需要不同的 evidence allocation | SAFSS hard routing 与 FCPSM 简单 scalar modulation 均已关闭；不得以 window、mask、gain 或 seed 作路线内救援 |
| branch interaction | stable non-zero lag/equalizer 无锚点；inter-attention 放大相似性，但两支不双向可替代 | **哪些 cross-branch interaction 是有因果效用的，哪些只是在放大相似性？** 应先锁定 interaction 的层级、条件与直接 falsifier | 不得从高 CKA 直接推出 decorrelation、diversity regularization 或 complementary fusion；也不能把 CBLR 解释成“所有 interaction 无效” |
| 004 instability | 001 的稳定 realized identity 不可外推；004 的 scale-specific learned residual 部分近 identity，但两支最终 slot 仍被使用 | CSRPA 已回答其路径层问题：collapsed residual 不承担最终 slot use；SCPRA 已检验并否定当前 scope 内的稳定 performance-harm relation | `dsainet-condition-dependent-scale-realization` 已为 `exploratory/no_go`；不得以 alpha、轨迹、window、seed、dataset 或 adaptive module 重开 repair 路线 |

可把每一行进一步写成 idea card 时，固定保留四个字段：`evidence fact`、`causal question`、`direct falsifier`、`negative scope`。这样 candidate 的起点是一个可被证伪的缺口，而不是对已有负面路线的改名救援。

## 2. 三个已被支持的 baseline facts

### 2.1 Scale separation：001 上是实际可观测的，不只是名义 kernel 标签

RBIA 的 31-token occlusion descriptor 显示，001 上 `[11,15]` branch 的 effective mean absolute lag 中位数为 `4.219`，`[3,7]` branch 为 `1.939`；相应 r90 为 `7/3`。这支持“本 scope 的方向性尺度分离”。

它回答的是“冻结模型实际实现了不同的时间影响范围吗”，不是“两个 branch 分别编码了哪个生理事件”。

### 2.2 Branch stability：001 上 slot 与 realized identity 是稳定对齐的

RBIA 的 activation、pooled representation、contribution pattern 三个 panel 都通过 same-index 稳定门：median same-minus-swap CKA margin 分别为 `+0.065893`、`+0.024684`、`+0.037996`。branch1/branch2 的 contribution RMS 中位数为 `1.327/1.230`，两支 true-class margin 在 45/45 checkpoint 均为正。

因此，001 当前不支持“branch index 与实际功能普遍错配”的 defect，也不支持把 branch2 当作退化支路直接剪掉。

### 2.3 Support/context relation：support 有信息，但不是充分条件

SCCD 把 hard support-only 的性能损失拆开：位置骨架被删解释 `36.04%`，真正删去 non-support content 解释 `63.96%`。与此同时，support 与 equal-occupancy shift 的差异稳定为 `+15.567–17.303 pp`。

这两件事必须同时保留：support 位置有用，且完整 context 也有不可替代的贡献。它直接否定“只留下 support 即可”的简单叙事，但不否定 support 的存在价值。

## 3. 三个已关闭路线的精确停止边界

### 3.1 Hard routing

- **SAFSS-v0.1**：coarse-only checkpoint support projection 对 native 的结果为 `-2.141 pp`，exact cycle=`negative_boundary / completed_not_promoted`，family=`no_go`。
- **ESFS-v0.1**：把 fixed event subsequence 持续送入 fine path 仍未跨 seed 稳定超过 parent/native；family `dsainet-efsr` 的唯一 child budget 已用尽。

因此，不再使用固定 `[2,3)`、fine=event reader、support-only coarse path，也不以 window、mask、seed、branch 调整做路线内救援。

### 3.2 Support modulation

FCPSM 已保留所有 context 与 position，只在 coarse support content 上施加 source-only 单标量调制。尽管平均方向小正，四个对照关系均未通过 stable-positive 门，且 checkpoint-specific transfer 极弱。该 family 的唯一 child budget `1/1` 已消耗，不能将其改造成第二个同 thesis child。

SCCD 的 diagnostic finding 仍有效：FCPSM 的失败说明“避免硬删除损失”不等于“调制 support 会产生稳定增益”。

### 3.3 Permutation fusion

DCBS 的成功结论只到 ordered-concat head 的 slot sensitivity；它并不等于 slot 语义错配。随后 RBIA 在同一 001 scope 支持稳定 same-index identity，故 descriptor-conditioned permutation-invariant set-fusion child 失去必要的 mismatch evidence anchor。

这里的“关闭”是**前提不足导致不创建 child**，不是一次已经完成的 fusion 训练失败。未来若出现独立的新 defect，必须按新 family 重新建立锚点，不能从 DCBS 继承 ready 状态、预算或信号。

## 4. 一个未知问题与一条已关闭的 adaptive 路线

### 4.1 Branch interaction：多个窄入口已关闭，但广义问题仍未知

- CBLR 的 45-checkpoint zero-training diagnostic 没有找到 stable non-zero lag 或 nonlinear local-response anchor，故不能从 lag alignment/equalizer 出发。
- BSRA 发现 learned delta 高相似（median CKA=`0.7384`），且 inter-attention 是 final similarity 的主要放大路径；但 branch removal/roll 的作用高度不对称，bilateral replaceability 为 `0/9` targets、`0/5` seeds。

RACR-v0.1 进一步直接测试了“稳定 role 的 native additive readout 是否遗漏 same-trial conjunction”。r5 的
54-unit B0/P1/M1 screen 完整性通过，但 P1−B0 overall 为 `+0.000 pp`、P1−M1 的 seed1 为负，故精确候选为
`no_signal`；36 个 P1 source-validation checkpoint 的 class-preserving pairing residual margin drop 均为0。

两个 B0 后续诊断把“有配对依赖”与“有分类增益”分开：18 checkpoint 上 classwise true-vs-shuffled pooled
linear CKA drop 为 `+0.607858`，两个 seed 均正且9/9 target过门，说明 representation 中存在稳定 paired
dependence；但以 source-train 拟合、held-out source-validation 评分的固定 `[p1;p2;p1⊙p2]` multinomial
logistic probe 在 true pair 上相对 additive 读出的 NLL 为 `-0.056406` nats，三个冻结稳定性门均未通过。

所以当前不能把 CKA dependence 写成“联合 label information”或“additive head 未充分利用的可用信息”，也不能把
RACR inactive residual 写成接口 bug。这里关闭的是 native B0 上 fixed product-probe / RACR-v0.1 的窄路径，
不是所有 cross-branch interaction 的普遍否定。现有证据仍不允许直接训练 equalizer、decorrelation/diversity
regularizer、complementary fusion 或分支重配比。

RAIA-v0.1 进一步但**独立地**检验了另一处窄问题：原生 `InterAttnBlock` 对两个有序方向复用同一 MHA/FFN
消息变换，是否漏掉了 direction-indexed residual adapter 的稳定效用。冻结 54 个 B0/P1/C1 训练单元与 18 个
同 checkpoint、无重训的 A1 direction-label swap 已完整回拉并逐预测复算。P1−A1 overall=`0.0000 pp`，因而
触发 `no_signal`；P1−B0=`+0.5401 pp`、P1−C1=`+0.4823 pp` 也均在 seed-1 与一项 LOTO 稳定门失败。
RAIA exact cycle 已 S9 `negative_boundary / completed_not_promoted`，family=`exploratory/no_go`。这关闭的
只是该 frozen adapter signature；不证明共享 MHA/FFN 无害，不否定所有 cross-branch interaction，也不为
RACR、BSRA、SAFSS 或其它 family 转移 signal、budget、授权或 claim。

### 4.2 Adaptive realization：路径已定位，性能修复路线已关闭

CRBRA 显示 004 不能被概括为“同样稳定的 long/short identity，只是 allocation 改了”。CSRPA 进一步回答了路径层问题：scale-specific learned residual 可由 active 转为 collapsed，而 collapsed branch slot 仍主要经 downstream attention/readout path 被使用。

CSRPA 建立了 residual formation/downstream path anchor；SCPRA 随后以 checkpoint alpha 作为 source-only
observable，检验其与 untouched full-test performance 的 target-controlled 关系。该关系没有通过预冻结 harm
门，target-exposed residual/transform 也没有补出信号。因此性能锚点在当前 scope 内已关闭，因果修复命题不再
具备准入前提。

当前 family=`exploratory/no_go`、child not applicable。不得再用 alpha 阈值、descriptor、seed、window、dataset、
trajectory 或直接训练 scale regularizer 进行结果驱动救援。训练轨迹只剩 characterization 价值，不能恢复 repair route。

## 5. 当前可复用的叙述与禁语

可复用的研究叙述是：

> DSAINet 的双 branch 在 001 的冻结 baseline 中实现了方向性时间尺度分离和稳定的 same-index identity；temporal support 具有位置特异性，但完整 context 对 coarse processing 仍是必要的。固定 hard routing、简单 support modulation、fixed same-trial conjunctive readout，以及 RAIA 的 frozen direction-indexed message adapter，均未形成稳定效用。跨条件下，realized scale identity 不可假定恒定；004 的 active/collapsed realization 已被定位，但没有形成稳定 performance bottleneck。branch interaction 的更宽问题仍未解决，但不能从 representation dependence 或一次 shared-operator negative screen 直接跳到训练模块。

不得写成：

- 已证明 fine/coarse 的生理语义；
- DSAINet 普遍存在冗余、dead branch 或 branch mismatch；
- 任一已关闭路线证明所有 routing、modulation、fusion 或 interaction 都无效；
- B0 paired CKA dependence 等于超出 marginals 的 label information，或等于 RACR 可修复接口缺陷；
- RAIA `P1-A1=0` 等于 shared MHA/FFN 已被证明无害，或等于所有 direction-specific interaction 都无效；
- 001 的结论已在 004 或其它条件下复现；
- 当前材料支持性能、机制、新颖性、泛化或论文 claim。

## 6. 权威证据入口

- 线路总交接与当前状态：`docs/notes/SAFSS_CYCLE_HANDOFF_2026-08-26.md` 第 11–16 节。
- 001 scale separation / branch stability：`experiments/records/2026-08-23_dsainet_realized_branch_identity_audit/RESULT.md`。
- support/context relation：`experiments/records/2026-08-21_dsainet_support_context_complementarity_decomposition/_work/results/S6D_RESULT.md`。
- hard routing：`experiments/records/2026-08-21_dsainet_support_aware_functional_scale_specialization/research_cycle.md` 与 `experiments/records/2026-08-19_dsainet_event_subsequence_fine_specialization/research_cycle.md`。
- support modulation：`experiments/records/2026-08-21_dsainet_full_context_preserving_support_modulation/RESULT.md`。
- permutation fusion 前提关闭：`experiments/records/2026-08-21_dsainet_descriptor_conditioned_branch_set/research_cycle.md` 与 RBIA result。
- branch interaction 边界：`experiments/records/2026-08-20_dsainet_cross_branch_local_response/_work/results/findings.md`、`experiments/records/2026-08-23_dsainet_branch_similarity_replaceability_audit/RESULT.md`。
- same-trial conjunctive readout 边界：`experiments/records/2026-08-24_dsainet_role_anchored_conjunctive_readout/research_cycle.md`、`_work/results/S6D_AUDIT.json`、`_work/results/S6D_SOURCE_ONLY_PAIRING_AUDIT.json`、`_work/results/B0_SOURCE_ONLY_JOINT_DEPENDENCE_AUDIT.json`、`_work/results/B0_SOURCE_ONLY_JOINT_DISCRIMINATIVE_UTILITY_AUDIT.json`。
- shared directional message-adapter 边界：`experiments/records/2026-08-27_dsainet_role_asymmetric_interaction_adapter/research_cycle.md`、`_work/results/RAIA_V0_1_S6D_INTAKE_AUDIT.json`、`_work/decisions/S6D_DISCOVERY_DECISION.md`、`_work/decisions/S6M_FAMILY_MATURATION_DECISION.md`、`_work/decisions/S9_CYCLE_CLOSE_DECISION.md`。
- adaptive realization 跨条件边界：`experiments/records/2026-08-24_dsainet_cross_condition_realized_branch_regime_audit/RESULT.md`。
- adaptive realization path：`experiments/records/2026-08-24_dsainet_condition_dependent_scale_realization_audit/RESULT.md`。
- adaptive realization performance boundary：`experiments/records/2026-08-24_dsainet_scale_collapse_performance_relevance_audit/RESULT.md`。

## 7. 状态汇总

```yaml
scope_status:
  scale_separation_001: supported_by_frozen_self_verified_diagnostic
  branch_stability_001: supported_by_frozen_self_verified_diagnostic
  support_context_relation_001: supported_by_frozen_self_verified_diagnostic
  hard_routing: closed_in_exact_scopes
  support_modulation: closed_in_exact_scope
  permutation_fusion_child: not_created_due_to_missing_mismatch_anchor
  branch_interaction: broad_question_unknown; lag_euqalizer_and_fixed_racr_product_readout_closed_in_exact_scopes
  b0_same_trial_dependence_001: supported_source_only_representation_anchor
  b0_joint_discriminative_utility_001: no_anchor_under_fixed_product_probe
  racr_v0_1: no_signal_no_child_rescue
  raia_v0_1: closed_negative_boundary_no_direction_specific_signature_in_frozen_shared_operator_screen
  adaptive_realization: localized_but_no_stable_performance_relation_family_no_go
claim_status:
  performance: none
  mechanism: none
  novelty: none
  generalization: none
  physiology: none
  claim_release: none
```
