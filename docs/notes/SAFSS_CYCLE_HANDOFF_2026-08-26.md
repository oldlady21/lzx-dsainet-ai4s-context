# SAFSS → SCCD → FCPSM 研究路线记录与交接

建立日期：2026-08-21  
最近更新：2026-08-26  
原始目标：供新会话建立 SAFSS 精确 cycle 使用。本文现已扩展为该研究主线的连续路线记录。

> **状态提示（2026-08-26）**：第 1–10 节保留 2026-08-21 的前置研究历史，不再代表当前状态。
> SAFSS 已正式建立并以 `no_signal` 关闭；随后完成 SCCD 因果诊断与唯一 child FCPSM-v0.1。
> 当前权威状态、会话新增证据和后续边界以第 11–15 节为准；其中第 15.7–15.12 节依次记录
> RBIA、BSRA、CRBRA、CSRPA、SCPRA 证据及当前路线总判断。第16节记录 RACR-v0.1 对 001 same-trial
> conjunctive readout 的后续检验。`condition-dependent scale realization` 已在第 15.12 节以 `exploratory/no_go`
> 收束；RACR-v0.1 也已在固定 scope 内 `no_signal`，两者都不是待准入的 repair candidate。本文是交接索引，不替代各 exact
> `research_cycle.md`、冻结合同或 machine artifact。

## 1. 历史前置快照：当时新会话应绑定的状态源

不要从 `TASKS.md`、文件时间或队列状态推断 SAFSS 状态。新会话首先应读取：

1. `./experiments\records\PROPOSED_FAMILIES.md`
2. `./experiments\records\2026-08-21_dsainet_source_only_functional_calibration\research_cycle.md`
3. `./experiments\records\2026-08-21_dsainet_source_only_functional_calibration\RESULT.md`
4. `./experiments\records\2026-08-21_dsainet_branch_balanced_temporal_support\_work\results\NEW_FAMILY_CANDIDATE.md`

当时的状态是：SAFSS 仍是新的 family candidate，尚未建立或准入正式 cycle。该状态现已被第 11 节列出的
SAFSS/SCCD/FCPSM exact cycles 取代。SOFC 当时已完成本地机械证据，但独立 reviewer 不可用，因此其
claim gate 为 `REVIEW_UNAVAILABLE`；这不妨碍把机械验证结果作为新 cycle 的前置设计证据，但不能宣称
已获得独立审计或论文级结论。

## 2. 前置研究主线与已获得结论

### 2.1 EFSR / ESFS：固定 event→fine 的硬专门化失败

最初假设是 coarse branch 读取 full context，fine branch 读取固定 `[2,3)` event。已有实验表明：

- event 对象可以在 fine branch 输入处形成，但这种专门化不能稳定穿过完整 fine branch。
- intra-attention 中的 attention residual 与 LayerNorm 都会破坏专门化，贡献约为 54.42% 与 45.58%，且不同 seed 的主导项会翻转。
- 即使让 event routing 贯穿整个 fine path，ESFS 仍无稳定信号。

因此，SAFSS 不应继承“fine 天然等于 event reader”这一语义，也不应继续救援固定 `[2,3)` 或硬 event-support routing。

### 2.2 CBLR：稳定 lag/equalizer 交互机制没有锚点

CBLR 没有发现可支持稳定 cross-branch lag alignment 或 equalizer 的证据。该结果只关闭这一窄机制，不证明所有 event–full 交互都无效。SAFSS 可以研究新的交互，但不能把 CBLR 当作现成正锚点，也不应继续做 equalizer/lag rescue。

### 2.3 BBTS：存在稳定的 whole-model temporal support，但跨数据集不共享同一平台

精确 cycle：
`./experiments\records\2026-08-21_dsainet_branch_balanced_temporal_support\research_cycle.md`

关键证据：

- BNCI2014001 与 BNCI2014004 内部都存在 checkpoint 级稳定的 shared temporal support。
- 两个数据集的平台位置不同，不能用统一固定 `[2,3)` 代表二者。
- 004 的 shared support 主要与 coarse branch 对齐：shared–coarse 中位相关约 0.913，shared–fine 约 0.602，45 个 checkpoint 中 33 个更偏 coarse。
- nominal fine/coarse 名称不足以保证固定的功能语义。

由此形成 SAFSS 的核心前提：应协调“source-calibrated whole-model temporal support”和“实证可识别的 functional branch allocation”，而不是把固定事件窗强塞给名义 fine branch。

### 2.4 EBID：004 的 0–4 s 右边界饱和是 crop censoring

精确 cycle：
`./experiments\records\2026-08-21_dsainet_004_epoch_boundary_identifiability\research_cycle.md`

在原生 0–5 s DSAINet baseline 的 45-checkpoint 诊断中：

- grand peak / platform 为 `start26 / start24..27`；
- 边界 peak 为 0/45；
- all-pair、within、discovery–audit 的 profile 相关约为 0.768、0.789、0.880。

所以 004 原 0–4 s 结果确实受到右边界截断。SAFSS 若使用 temporal support，应使用按数据集和 epoch contract 校准的宽平台，并按物理时间解释；不应硬编码一个精确生理中心。004 的当前合格证据对应原生 0–5 s contract。

### 2.5 BACL：通道压缩不能解释 coarse 倾向

精确 cycle：
`./experiments\records\2026-08-21_dsainet_branch_allocation_controlled_ladder\research_cycle.md`

在 L0 四分类 22ch、L1 左右手二分类 22ch、L2 左右手二分类 3ch、L3 004 左右手二分类 3ch 的控制梯中：

- L1→L2 后 shared/coarse temporal profile 仍较稳定，相关约 0.816/0.821。
- fine-share 的方向只有 8/18 一致。
- L1/L2 的 fine contribution 接近零，使 fine-positive-share 容易受小分母影响。

结论是：3-channel compression 不是 coarse dominance 的充分解释；fine-share 也不适合作为 SAFSS 的可靠校准量。

### 2.6 TBCD：任务差异的总位移存在，但不能归因于单一可路由因素

精确 cycle：
`./experiments\records\2026-08-21_dsainet_l0_l1_task_branch_causal_decomposition\research_cycle.md`

L0→L1 的 coarse-dominance 总位移中位数约 +0.419，但只有 12/18 checkpoint 同方向，未达到预设 14/18 稳定门。分量中位数为：

- trial composition：−0.058；
- normalization：−0.004；
- decision set：+0.150；
- retraining：+0.237。

没有单一分量达到稳定解释标准，最终路由为 `total_shift_not_stable`。因此不能根据“数据集/任务类别”直接映射 branch routing，也不能把 normalization 当作主因。

### 2.7 SOFC：source-only functional calibration 有效，但只有 coarse 合格

精确 cycle：
`./experiments\records\2026-08-21_dsainet_source_only_functional_calibration\research_cycle.md`

最终在 54 个冻结 checkpoint 上完成 source-only discovery/audit：001 L0 18、001 L1 18、004 原生 0–5 s 18。全流程不访问 target 数据，artifact 绑定 checkpoint、配置、split 和 epoch contract。

冻结门槛包括：`epsilon_ce=0.01`、source-subject positive fraction 75%、shared internal rho ≥0.5、shared discovery–audit rho ≥0.5、pooled precision ≥0.80、每 stratum precision ≥0.70、candidate count ≥10；明确不使用 fine-positive-share gate。

结果：

| 对象 | discovery candidate / audit valid | pooled precision | 分层结果 | 资格 |
|---|---:|---:|---|---|
| shared | 54 / 54 | 1.000 | 各层 18/18 | 合格 |
| fine | 39 / 35 | 0.897 | L0 17/17；L1 6/9=0.667；004 12/13 | 不合格 |
| coarse | 53 / 51 | 0.962 | L0 18/18；L1 16/18；004 17/17 | 合格 |

最终 route 为 `calibration_valid`，但 `qualified_branches=[coarse]`。

必须注意：artifact 中出现的 `fine_candidate` 仅是 discovery 过程记录，不是获准供后续模型消费的接口。未来 SAFSS 的首个版本若另行准入，只能读取：

1. 数据集/epoch-specific 的 shared temporal platform；
2. coarse-qualified 状态。

fine specialization 当前被禁止。artifact 缺失、hash/config/split/epoch/lattice 不匹配，或 shared 校准失败时，必须回退到 exact native DSAINet。某分支不合格不代表可以在 native baseline 中将其清零或降权；只表示不能对它做专门化。

SOFC 的机器事实与审计入口：

- `./output\local\2026-08-21_dsainet_source_only_functional_calibration_local_diagnostic\final_calibration\sofc_summary.json`
- `./experiments\records\2026-08-21_dsainet_source_only_functional_calibration\MECHANICAL_AUDIT.md`
- `./experiments\records\2026-08-21_dsainet_source_only_functional_calibration\RESULT.md`

机械审计确认 54 个唯一 checkpoint hash 与 split digest、target access=0、identity violation=0；004 shared profile 与 EBID 重算最大差异为 0。独立 reviewer 当前不可用，因此不能写成独立审计通过。

## 3. SAFSS 的建议核心命题

候选全称可暂定为 **Support-Aware Functional Scale Specialization**，但正式名称、family admission 和 cycle_id 应由新会话按 proposed-research 流程冻结。

建议核心问题：

> 在完全 source-only、artifact 与数据合同可验证、失效时精确回退 native DSAINet 的前提下，能否利用数据集/epoch-specific 的 whole-model shared temporal support，只对已通过功能校准的 coarse branch 施加最小支持条件化，使模型更有效或更稳定地利用该时间证据，同时不改变 fine branch、不假设 fine=event reader，也不依赖 target 数据？

这比“event 与 full 如何融合”更精确：当前问题不是给两个输入对象找一个复杂融合器，而是验证一个经 source calibration 许可的 support-conditioned coarse specialization 是否具有超出 native processing 的因果价值。

## 4. 建议在新 cycle 中冻结的子问题

1. **机会是否真实存在**：native coarse branch 对 shared platform 的高相关，究竟表示它已经充分利用证据，还是仍存在可被 support conditioning 改善的 residual opportunity？
2. **最小机制是什么**：首个 child 应在零/极少新增参数的 mask、弱 residual modulation、轻量 auxiliary coarse path 中只选一个；不要同时堆 continuous gate、cross-attention 和多条旁路。
3. **怎样保持公平**：必须有 exact-paired native B0，以及参数量/计算量匹配但不使用校准 support 的控制，区分“额外容量”与“support conditioning”效应。
4. **怎样保证 native-preserving**：artifact 缺失、失配或 coarse 不合格时，输出路径必须与 native DSAINet 精确等价；这应先作为工程门验证。
5. **平台怎样进入模型**：只使用冻结的宽 shared platform；不使用 exact center，不重新搜索窗口，不在 target 上校准，不读取 fine candidate。
6. **证伪条件是什么**：跨 seed/subject 效果不稳定、不能胜过匹配控制、机制路径实际未被使用、或 fallback identity 失败，任何一项都应阻止晋级，而不是触发阈值/window/seed rescue。

## 5. 建议的首轮研究边界

### 允许

- 读取经过 SOFC 验证并与当前 checkpoint/config/split/epoch 绑定的 shared platform。
- 读取 coarse-qualified 布尔状态。
- 在 coarse branch 内测试一个最小、可隔离、可回退的 support-conditioned 机制。
- 保持 fine branch 及其 native 输入/计算逻辑不变。
- 建立参数/计算匹配控制和 exact native fallback 测试。

### 禁止

- 固定 `[2,3)`、统一跨数据集窗口或精确中心 prior。
- 把 nominal fine/coarse 名称直接解释成 event/full 功能。
- 使用 SOFC artifact 中未合格的 fine candidate。
- target-aware discovery、target normalization、target labels 或 target 调参。
- equalizer/lag rescue、fine routing rescue、阈值/seed/window rescue。
- 在新 family 未准入前实现 proposed model、启动训练、上传服务器或释放性能/机制 claim。

## 6. 建议的首个公平比较

新会话应先做 family admission 和方法冻结，之后再形成实验合同。一个合适的最小比较骨架是：

- **B0**：完全原生 DSAINet。
- **C-capacity**：与 proposed 路径参数量/计算量匹配，但不使用 SOFC support 的控制。
- **P1**：只消费 shared platform + coarse-qualified 状态的最小 coarse specialization。
- **Fallback test**：artifact 缺失/篡改/contract mismatch 时 P1 与 B0 exact identity。

首轮主张应限制为：“source-calibrated support conditioning 是否提供超出 native 与 matched-capacity control 的稳定增益或机制证据”。不要预先主张跨数据集泛化、神经生理定位、动态个体事件发现或 fine/coarse 生理分工。

## 7. 建议停止规则

- 若 P1 不能稳定优于 B0 和匹配控制，则关闭该最小机制，不做就地复杂化救援。
- 若作用只在单 seed、少数 target 或单一 dataset 出现，保留为 heterogeneity 证据，不晋级性能主张。
- 若 fallback identity 或 artifact provenance 失败，结果只算工程失败，不进入科学解释。
- 若机制依赖未获准的 fine candidate 才出现信号，应停止；这不是当前 SAFSS 合同允许的结果。

## 8. 历史建议执行顺序（已完成，不得按当前状态重跑）

1. 使用 `$proposed-research`，绑定精确 SAFSS candidate，完成 family admission、cycle_id、核心命题、负面继承边界和授权边界。
2. 在不实现模型前，用 `$research-refine` 收敛一个最小 child 机制，并明确 matched control 与 falsifier。
3. 使用 `$novelty-check` / `$research-lit` 做针对性查新；本地论文库显式传入 `./refs\papers`。查新不能替代当前机制证据。
4. 方法被明确选定后再用 `$experiment-plan` 冻结比较、顺序、门槛和停止规则。
5. 实现时可用 `$ponytail` 控制机制规模。
6. 实验完成后再使用 `$experiment-audit` 与 `$result-to-claim`；当前 reviewer 不可用时必须保留 `REVIEW_UNAVAILABLE`，不能冒充独立审阅。
7. 若需要向用户解释当前冻结想法而不改变合同，使用 `$wait-what`。

## 9. 历史启动语（不得按当前状态直接复用）

> 请基于 SAFSS 前置研究交接，先读取 SOFC-v0.1、BBTS-v0.1、EBID-v0.1、BACL-v0.1、TBCD-v0.1 的精确 cycle 与 `PROPOSED_FAMILIES.md`，不要从 TASKS 或文件新旧推断状态。按 `$proposed-research` 建立 SAFSS family/cycle，但暂不实现和训练。核心候选问题是：能否在 source-only、native-preserving 条件下，只使用 dataset/epoch-specific shared temporal platform 和 coarse-qualified 状态，构建一个最小的 support-conditioned coarse specialization，并以 native B0 和 matched-capacity control 判断其是否具有独立价值。不得使用 fine candidate、固定 `[2,3)`、target 信息或 equalizer/lag/fine-routing rescue。中间人工审阅可由你自行审查，但独立 reviewer 不可用时必须标记 REVIEW_UNAVAILABLE。

## 10. 非结论

现有证据尚未证明：

- SAFSS 会提高分类性能；
- coarse specialization 能跨数据集泛化；
- shared platform 是固定生理事件或精确神经生理中心；
- fine branch 没有价值；
- 所有 event–full interaction 都无效；
- SOFC 已通过独立 reviewer 或可直接释放论文 claim。

当前最强、也最安全的起点只有：稳定 temporal support 的确存在且依赖 dataset/epoch contract；功能校准目前只允许 coarse specialization；因此 SAFSS 的首个 child 应是 source-only、coarse-only、最小化且 native-preserving 的受控验证。

## 11. 2026-08-21 至 2026-08-22 会话增量：研究路线记录表

以下内容记录本会话在原前置研究基础上实际推进的对象。旧 handoff 中“SAFSS 尚未建立”的状态已被
这些 exact-cycle 记录取代。

| 顺序 | 对象/阶段 | 核心问题与科学改动 | 关键证据 | 冻结路线与当前状态 |
|---:|---|---|---|---|
| 1 | SAFSS-v0.1 S0–S5 | 只让 coarse branch 读取 source-only SOFC support；fine 保持 native；以 static support 和 native 作控制 | 合同、实现、D0、Bundle 逐级冻结；正式 r3 修复只涉及 asset verifier 与外部输出路径 | 正式进入 S6D；工程门不作性能证据 |
| 2 | SAFSS-v0.1 S6D/S6M/S9 | checkpoint support-only 是否同时胜过 static support 与 native full | r3-full 18/18 task、54/54 arm/prediction、293/293 manifest；P1-B1 `+0.502 pp` 但仅 4/9 targets 正；P1-B0 `-2.141 pp` | `no_signal`；exact cycle=`negative_boundary / completed_not_promoted`；原 SAFSS family=`no_go`；不得窗口、seed、mask、branch rescue |
| 3 | SCCD-v0.1 因果诊断 | SAFSS 损失主要来自删除 non-support context，还是 support conditioning 无效 | 七臂、18-pair、126-row zero-training factorial；position deletion 占 `36.04%`，non-support content deletion 占 `63.96%`；support 相对等占用 shift `+15.567–17.303 pp` | `supporting_evidence / diagnostic_complete`；结论为 support 有位置特异性但 support-only 不充分；不重开 SAFSS |
| 4 | FCPSM-v0.1 S0–S5/Bundle | 保留所有 context/position，只以 `g=0.5*tanh(theta)` 对 coarse support content 作单标量调制 | 唯一 child；B0/U1/B1/P1/N1 五臂；D0 13/13、unit 4/4；accepted Bundle r4 SHA-256 `c2ac1884…861f4` | family child budget `1/1`；r1/r2/r3 为历史冻结版本，正式执行只认 r4 |
| 5 | FCPSM-v0.1 r4-full/S6D | full-context-preserving support modulation 能否形成 support-specific 稳定增益 | 18/18 task、90/90 arm、72/72 scalar fit、90/90 prediction；archive SHA-256 `6cc69756…5b8331`；预测级复算通过 | `ambiguous`：exact cycle=`prototype_archive / completed_not_promoted`；family=`exploratory / exhausted` |
| 6 | FCPSM read-only opportunity diagnostic | native coarse 对 support/non-support 是否已经饱和，重点检查 support-enhancement sensitivity | 18 checkpoint×seed 固定增益扫描；不训练、不写 artifact、不改状态；target label 仅用于 post-hoc diagnostic | support 已被利用但排序效用接近单侧饱和；保留一个“moderate global coarse dose”机会信号，不形成 claim、child 或 FCPSM rescue |

### 11.1 当前权威入口

- SAFSS exact cycle：`experiments/records/2026-08-21_dsainet_support_aware_functional_scale_specialization/research_cycle.md`
- SAFSS S6D：`experiments/records/2026-08-21_dsainet_support_aware_functional_scale_specialization/_work/decisions/S6D_DISCOVERY_DECISION.md`
- SCCD exact cycle：`experiments/records/2026-08-21_dsainet_support_context_complementarity_decomposition/research_cycle.md`
- SCCD result：`experiments/records/2026-08-21_dsainet_support_context_complementarity_decomposition/RESULT.md`
- FCPSM exact cycle：`experiments/records/2026-08-21_dsainet_full_context_preserving_support_modulation/research_cycle.md`
- FCPSM result：`experiments/records/2026-08-21_dsainet_full_context_preserving_support_modulation/RESULT.md`
- FCPSM deterministic audit：`experiments/records/2026-08-21_dsainet_full_context_preserving_support_modulation/_work/results/S6D_AUDIT.json`
- FCPSM S6M：`experiments/records/2026-08-21_dsainet_full_context_preserving_support_modulation/_work/decisions/S6M_FAMILY_MATURATION_DECISION.md`
- Family 状态源：`experiments/records/PROPOSED_FAMILIES.md#family-dsainet-support-context-complementarity`

## 12. FCPSM 正式结果：证据与解释边界

### 12.1 完整性

- Remote RunId：`2026-08-21_fcpsm_v0_1_ccmu_r4-full-w1`。
- Controller 重新验证 390 个安全 tar member、348/348 Bundle manifest 文件。
- 18/18 task、90/90 arm evaluation、72/72 source-only scalar fit 完成，无 scheduler failure。
- 90 个 prediction NPZ 的 indices、labels、logits、predictions、theta/gain、行级 SHA-256 与
  ACC/Kappa/weighted-F1/NLL/margin 全部可复算。
- 五臂在每个 target×seed 内的 split、label、checkpoint、SOFC artifact provenance 完全配对。
- 独立 experiment-audit/result-to-claim backend 不可用；正式状态为 `REVIEW_UNAVAILABLE`，只能称
  deterministic self-audit，claim release=`none`。

### 12.2 五臂结果

| Arm | Mean ACC | 相对 P1 的冻结关系 |
|---|---:|---|
| B0 native full | 84.568% | `G_native=P1-B0=+0.174 pp` |
| U1 uniform full modulation | 84.722% | `G_uniform=P1-U1=+0.019 pp` |
| B1 static support modulation | 84.664% | `G_static=P1-B1=+0.077 pp` |
| P1 checkpoint support modulation | 84.742% | proposed child |
| N1 shifted support modulation | 84.471% | `G_shift=P1-N1=+0.270 pp` |

四个 contrast 均未通过完整 stable-positive 门。最先失败的是 `G_native`：总体虽为 `+0.174 pp`，
seed0/1 却为 `-0.116/+0.463 pp`。P1 在 18/18 单元降低 source-train CE，但相对 B1 只改变
`8/5,184` 个 target 判决，净增加 4 个正确；P1/B1 在 15/18 单元预测完全相同。因此不能声称
support-specific、checkpoint-conditioned、location-specific 或 generic coarse-rescaling utility 已成立。

### 12.3 对 SCCD 的影响

FCPSM 不推翻 SCCD：保留 full context 后没有重现 SAFSS 的 `-2.141 pp` 大幅下降，说明删除侧诊断
仍然合理；但 FCPSM 的小正方向跨 seed 不稳定，说明“避免删除造成的损失”并不自动等于“support
conditioning 能创造稳定增益”。SCCD 保留为范围受限 diagnostic finding，FCPSM 作为唯一 performance
child 已完成且未晋升。

## 13. Read-only opportunity diagnostic：native coarse saturation

### 13.1 范围与方法

本会话随后对 18 个 FCPSM checkpoint×seed 做了一次纯内存、固定剂量扫描：只改变 coarse content
multiplier，fine branch、position、context、checkpoint 与 split 不变；分别扫描 checkpoint support、其
non-support 补集与 uniform full mask。增益固定为 `-0.2/-0.1/0/+0.1/+0.2/+0.4`，没有训练、文件写入、
target-time 选择或 cycle 状态变化。Target labels 只用于事后计算 ACC/NLL/margin，因此结果属于
selection-exposed opportunity diagnostic，不是 confirmation 或性能证据。

### 13.2 Support-enhancement sensitivity

| Coarse 调制 | Target ACC delta | seed0 / seed1 | NLL delta | true-class margin delta |
|---|---:|---:|---:|---:|
| support −20% | −0.347 pp | −0.193 / −0.502 pp | −0.0057 | −0.197 |
| support +10% | +0.096 pp | −0.154 / +0.347 pp | +0.0058 | +0.068 |
| support +20% | +0.039 pp | −0.077 / +0.154 pp | +0.0132 | +0.119 |
| support +40% | +0.039 pp | +0.077 / ≈0 pp | +0.0324 | +0.180 |
| non-support +20% | −0.058 pp | −0.154 / +0.039 pp | −0.0032 | −0.029 |
| uniform +20% | +0.193 pp | +0.077 / +0.309 pp | +0.0098 | +0.086 |

补充观察：

- support mask 只覆盖 9–13 tokens（均值约 10.44），non-support 覆盖 18–22 tokens；但 +10% support
  的 target logit RMS=`0.0978`，约为 non-support 的 `0.0480` 两倍。按 modulated token 粗略归一后，
  support sensitivity 约高四倍。
- support −20% 使两颗 seed 的 ACC 都下降，说明 native coarse 确实使用 support；不能解释为 support
  已被忽略或 branch 完全不敏感。
- support 从 +10% 增到 +40% 时 margin 持续增加，但 ACC 不再单调提高，NLL 持续恶化；source CE 在
  +10%/+20% 改善，到 +40% 已反转。最符合“排序效用单侧饱和并开始过置信”，而不是 representation
  完全饱和。
- non-support enhancement 对 ACC 没有稳定方向。结合 SCCD，更合理的定位是其存在/结构对互补上下文
  重要，但额外振幅不是明显机会。
- fixed uniform +20% 在这次 post-hoc 扫描中呈同形 stable-positive：overall `+0.193 pp`、seed0/1
  `+0.077/+0.309 pp`、5/9 positive targets、9/9 LOO positive；但 NLL 恶化，且剂量来自结果暴露后的
  扫描，不能释放 claim。正式 U1 的 gain 往往更大，提示的只是 moderate global coarse dose
  stabilization 机会，不是 support-specific FCPSM rescue。

### 13.3 当前机会判断

```yaml
support_usage: active_and_selectively_sensitive
support_enhancement_headroom: low_for_decision_ranking
support_saturation_type: one_sided_ranking_plateau_with_overconfidence
non_support_role: necessary_context_presence_but_weak_amplitude_headroom
retained_opportunity: moderate_global_coarse_dose_stabilization
evidence_status: read_only_post_hoc_selection_exposed
state_change: none
claim_release: none
```

如果未来明确授权继续，这个机会必须改写为新的因果问题：为什么 source-only final-epoch scalar fitting
容易把 coarse gain 推得过大，温和、预先冻结的 global dose stabilization 是否能稳定校准 coarse amplitude。
它改变了 FCPSM 的 support-specific thesis，应作为 `new_family_candidate` 重新查新、refine 与授权；不得
重开 FCPSM、继承其 signal、复用当前 post-hoc `+0.2` 作为确认超参或直接运行实验。

## 14. 当前停止边界与 suggested skills

### 当前状态

- SAFSS-v0.1：closed / `no_signal` / negative boundary。
- SCCD-v0.1：closed / `supporting_evidence / diagnostic_complete`。
- FCPSM-v0.1：closed / `ambiguous / prototype_archive / completed_not_promoted`。
- `dsainet-support-context-complementarity`：`exploratory / exhausted`，child budget `1/1`。
- benchmark、confirmation、第二个同 thesis child、训练和 claim：均未由本记录授权。

### Suggested skills

- `$wait-what`：只在需要重新解释当前冻结结论时使用，不改变合同或证据状态。
- `$proposed-research`：仅在用户明确授权把 global coarse dose stabilization 建成新 family/cycle 时使用。
- `$research-refine`：新问题获准后，先收敛单一因果机制与 native/matched controls。
- `$novelty-check` / `$research-lit`：核对 activation scaling、temperature/dose calibration 与 coarse-path
  gain stabilization 的邻近工作；不得把查新替代机制证据。
- `$experiment-plan`：仅在方法明确选择后冻结 source-only dose、controls、稳定门和停止规则。
- `$experiment-audit` / `$result-to-claim`：任何新实验完成后使用；reviewer 不可用时继续 fail-closed 为
  `REVIEW_UNAVAILABLE`。

新会话默认应先读取第 11.1 节的 exact-cycle 状态源。除非用户明确建立新 family，否则最安全的动作是
解释或审阅现有 evidence snapshot，而不是实现、训练、上传、创建 child 或更新论文 claim。

## 15. 2026-08-23 增量：DCBS 证据与 branch identity / functional role alignment 入口

本节只补充当前研究路线，不覆盖第 1–14 节的历史事实与既有结论。DCBS-v0.1 在正式
`proposed-research` 账本中仍是独立、隔离的 exact cycle/family；但在本 handoff 的跨阶段研究解释中，
它不是另起一条与 temporal support 无关的新方向，而是为以下连续路线增加一项新的结构诊断证据：

```text
EFSR → BBTS / EBID / BACL / TBCD → SOFC → SAFSS → SCCD → FCPSM
                                                        ↓
                         branch identity / functional role alignment
```

这项联系只发生在研究问题的综合与后续入口层。DCBS 不继承 SAFSS/SCCD/FCPSM 的 signal、child budget、
执行授权或 claim；原 family 也不吸收 DCBS 的 evidence ledger。

### 15.1 temporal support 主线的当前解释

SAFSS、SCCD 与 FCPSM 的结论保持不变：

- `support-aware intervention` 路线已基本关闭。SAFSS 的 support-only specialization 为
  `no_signal`；FCPSM 在保留 full context 后只得到跨 seed 不稳定的小正方向，唯一 child 已完成且 family
  exhausted。
- SCCD 仍支持一个范围受限的诊断结论：temporal support 具有功能相关性与位置特异性，但 support-only
  不充分，不能把 support 简单当作一个可独立交给某个 branch 的 specialization target。
- 第 13 节的 FCPSM read-only opportunity diagnostic 仍是 post-hoc、selection-exposed 参数观察；它不因
  DCBS 结果而升级为正式 evidence，也不构成 FCPSM rescue 或新路线的正信号。

DCBS 改变的是下一步问题的重心。现在不应继续优先追问“哪个 temporal support 应该交给哪个 branch”，
而应先问：**实际学到的 branch 功能角色，是否与 classifier 使用的固定 slot identity 对齐。**

### 15.2 DCBS-v0.1 正式 evidence

DCBS 对 45 个冻结 DSAINet BNCI2014001 official-preproc LOSO checkpoints 做零训练、只读 slot-swap
diagnostic：对每个 checkpoint 的 held-out subject 固定前 64 trials，交换 classifier 输入中两个 pooled
branch halves，再经过同一个 linear head。

| 项目 | 正式结果 |
|---|---|
| 覆盖 | 9 subjects × 5 seeds = 45/45 checkpoints；组合唯一，无缺失或重复 |
| 完整性 | full archive、27/27 Bundle manifest、45/45 checkpoint SHA-256、config/baseline/analyzer 指纹全部复核一致 |
| median mean-abs logit shift | `1.857546329498291`；冻结门为 `1e-3` |
| median prediction disagreement | `0.375` |
| 稳定性 | `9/9` subjects、`5/5` seeds 通过；冻结最低要求为 `6/9`、`3/5` |
| S6D | `screen_positive`；machine outcome=`slot_identity_anchor` |
| S6M | `diagnosis_driven_child`，以 `S6D_direct_exception` 完成；S7Q eligibility=`false` |
| S9 | exact cycle=`supporting_evidence / diagnostic_complete`；benchmark=`not_required`；claim release=`none` |

这份 evidence 的 claim boundary 必须保持精确：

- **已证明**：当前 DSAINet classifier 使用 fixed slot identity；交换 branch slot 会在全部预声明
  subject/seed 稳定性维度上使 logit shift 远高于冻结阈值，并频繁改变预测。
- **未证明**：branch1/branch2 已形成跨训练条件稳定的 coarse/fine 或其它 semantic identity。
- **未证明**：fixed slot 与 realized branch function 已发生 mismatch。
- **未证明**：permutation-invariant、descriptor-conditioned 或其它 slot-agnostic fusion 一定有效或能够
  改善泛化。
- 外部 result-to-claim reviewer 不可用，正式 verdict=`REVIEW_UNAVAILABLE`；上述正项只作为
  selection-used diagnostic anchor，不释放论文 claim。

### 15.3 新研究入口：Branch Identity / Functional Role Alignment

候选研究问题记录为：

> DSAINet 当前 classifier 是否依赖固定 branch index，而实际 branch functional role 是否可能随训练条件变化？

当前 evidence 与 hypothesis 必须分开：

| 层级 | 当前内容 | 证据边界 |
|---|---|---|
| 已确认 evidence | **slot dependence**：DCBS 证明 ordered-concat classifier 稳定使用 branch index | 只说明 readout 对 slot 顺序敏感，不说明 slot 语义正确 |
| 已有结构线索 | **branch allocation instability**：BBTS/BACL/TBCD 与前序诊断表明 nominal fine/coarse 名称不足以保证固定功能语义，allocation/贡献会随 dataset、task、seed 或训练条件表现出不稳定和异质性 | 这些是既有、各自范围受限的线索；不能与 DCBS 合并成一个已证实 mismatch 结论 |
| 尚未确认 hypothesis | fixed slot identity 与 realized branch function 之间存在系统性 mismatch | 需要直接的 realized-function 审计；当前没有对应 gate evidence |
| 尚未确认 hypothesis | declared descriptor 能正确标识 learned branch role，且 descriptor-conditioned readout 可改善泛化 | 需要后续独立诊断与另行授权的 exact-paired performance evidence |

因此，新的研究入口不是“直接训练 slot-agnostic fusion”，而是先确认 classifier 的 index-defined identity
与 branch 的 realized functional identity 是否真的不一致。

### 15.4 下一阶段优先诊断：Realized Branch Identity Audit

下一步建议登记为一个独立候选 diagnostic：`Realized Branch Identity Audit`。本 handoff 只记录其目标与
边界；**不创建 cycle、不冻结公式、不实现、不运行，也不消耗 DCBS 或 SAFSS 路线的 child budget。**

诊断目标：

1. 检验 declared branch descriptor（例如冻结的 kernel / receptive-field / scale 声明）是否对应实际
   learned function，而不是把结构名称直接当作功能事实。
2. 检验 realized branch role 在 seed、subject 与允许的训练条件之间是否稳定。
3. 直接检验 index-defined identity 与 functional identity 是否一致；避免只用 slot swap 的输出敏感性
   代替功能身份测量。

建议的最小判别路线是：

- 若 declared descriptor 与 realized function 对齐且跨 seed/subject 稳定，则不存在当前设想的 mismatch
  anchor；不应仅凭 DCBS 继续 slot-agnostic fusion。
- 若发现可复现的 index/function mismatch，才把它作为后续 readout/fusion candidate 的本地 evidence
  anchor；创建 child、方法选择和预算消耗仍须另行授权。
- 若结果异质或不可观测，则记录为 evidence gap 并停止，不以阈值、descriptor、seed、window 或 fusion
  搜索作结果驱动救援。

虽然 DCBS family ledger 当前把一个 descriptor-conditioned permutation-invariant set-fusion child 标为
`ready / decision_pending`，本 handoff 的最新研究优先级是：**先做 Realized Branch Identity Audit，暂不直接
进入该 child。** 这是一条后续研究建议，不回写或改造已关闭的 DCBS exact cycle，也不把建议本身当成授权。

### 15.5 流程与解释边界

- 不把 DCBS 解释为 slot-agnostic fusion、set fusion 或 descriptor-conditioned readout 已被证明有效。
- 不把 branch1/branch2 写成稳定的 coarse/fine、event/full 或其它生理/功能语义。
- 不让新的 diagnostic 继承 SAFSS/SCCD/FCPSM 的 child budget、signal、confirmation、执行授权或 claim。
- 不让 DCBS family 继承 temporal-support family 的负面或正面 signal；两边只在 handoff 的研究问题综合层关联。
- 不将第 13 节 target-exposed read-only 参数扫描、1-checkpoint smoke、check/pilot 或其它工程观察升级为
  Realized Branch Identity Audit 的正式 evidence。
- 未经用户明确授权，不创建 diagnostic cycle，不改模型，不训练，不上传，不进入 benchmark 或 claim release。

### 15.6 权威入口与 suggested skills

- DCBS exact cycle：`experiments/records/2026-08-21_dsainet_descriptor_conditioned_branch_set/research_cycle.md`
- DCBS integrity：`experiments/records/2026-08-21_dsainet_descriptor_conditioned_branch_set/_work/verification/S6D_INTEGRITY_RECONCILIATION.md`
- DCBS S6D：`experiments/records/2026-08-21_dsainet_descriptor_conditioned_branch_set/_work/decisions/S6D_DISCOVERY_DECISION.md`
- DCBS S6M：`experiments/records/2026-08-21_dsainet_descriptor_conditioned_branch_set/_work/decisions/S6M_FAMILY_MATURATION_DECISION.md`
- DCBS S9：`experiments/records/2026-08-21_dsainet_descriptor_conditioned_branch_set/_work/decisions/S9_CYCLE_CLOSE_DECISION.md`
- 原 temporal-support 路线状态源：第 11.1 节列出的 SAFSS/SCCD/FCPSM exact-cycle artifacts。

下一会话建议按以下技能边界继续：

- `$wait-what`：仅用于解释“slot dependence”与“functional identity mismatch”的区别，不改变 evidence。
- `$proposed-research`：只有用户明确授权建立 `Realized Branch Identity Audit` exact cycle 时才调用；不得把
  handoff 中的候选名称当作已准入 cycle。
- `$research-refine`：cycle 获准后，先冻结 realized function 的可观测定义、descriptor、对照与 falsifier。
- `$experiment-plan`：仅在诊断问题和方法明确后冻结跨 seed/subject scope、D0、判定门与停止规则。
- `$experiment-audit` / `$result-to-claim`：只在正式诊断完成后使用；reviewer 不可用时继续 fail-closed 为
  `REVIEW_UNAVAILABLE`。

### 15.7 2026-08-23 RBIA-v0.1 正式结果与 DCBS child 决定

用户已明确授权建立并运行 `2026-08-23_dsainet_realized_branch_identity_audit`。该 cycle 是 DCBS family 的
零训练 `diagnostic_probe`，不消耗 `1/1` trainable child budget。formal r2 对同一 45 个 verified DSAINet
checkpoints、每 checkpoint 固定 64 held-out trials 完成：

| Panel | Median same−swap CKA margin | target gate | seed-pair gate | 结果 |
|---|---:|---:|---:|---|
| activation descriptor | `+0.065893` | `8/9` | `10/10` | same-index stable |
| pooled representation | `+0.024684` | `6/9` | `9/10` | same-index stable |
| contribution pattern | `+0.037996` | `7/9` | `8/10` | same-index stable |

三个 panel 没有形成 stable swapped correspondence。ConvTime learned-residual occlusion 中，声明长 kernel
`[11,15]` 相对短 kernel `[3,7]` 的 empirical mean-lag ratio 中位数为 `2.1556`，9/9 target 与 5/5 seed
均通过冻结方向门；median r90=`7/3`。这只验证当前 scope 的方向性 effective temporal scale，不把 branch
命名升级为生理语义。

冻结 outcome=`aligned_stable`，因此 index/function mismatch hypothesis=`no_signal`。DCBS 已确认的 slot
dependence 不变，但当前证据更符合 classifier 使用稳定分工，而不是固定 slot 与 realized function 已错配。
现有 descriptor-conditioned permutation-invariant set-fusion child 不再 ready；family 转为
`promising / paused(evidence_gap)`，blocking gap=`missing_evidence_anchor`，budget 仍 `0/1`。不换 descriptor、
seed、threshold、window、dataset 或 fusion 作结果后救援。

RBIA exact cycle 以 `negative_boundary / diagnostic_complete` 关闭。外部 experiment-audit/result-to-claim
backend 仍不可用，正式状态=`REVIEW_UNAVAILABLE`，claim release=`none`。机器产物与确定性复核入口：

- `results/logs/local/2026-08-23_rbia_v0_1_dsainet_bnci2014001_formal_r2/`
- `experiments/records/2026-08-23_dsainet_realized_branch_identity_audit/RESULT.md`
- `experiments/records/2026-08-23_dsainet_realized_branch_identity_audit/_work/verification/S6D_INTEGRITY_RECONCILIATION.md`

### 15.8 2026-08-23 BSRA-v0.1：高相似存在，但不构成双向功能冗余

RBIA 后的 post-hoc 高 CKA 改变了 baseline defect，因此没有重开 DCBS，而是经 re-entry review 登记独立
`dsainet-branch-functional-redundancy` family。用户明确授权后建立并运行
`2026-08-23_dsainet_branch_similarity_replaceability_audit`，复用同一 45 checkpoints × 64 trials，零训练。

native learned-delta/pooled/contribution CKA median 分别为 `0.7384/0.8491/0.7643`；learned delta 高相似门
通过（7/9 targets、5/5 seeds）。但 final similarity 主要由 inter-attention 放大：big-residual-off 的
pooled CKA 仍为 `0.8483`，inter-off 降至 `0.3805`；contribution 对应 `0.7507/0.2838`。

冻结 bilateral replaceability 门没有通过：delta1-off/joint=`0.8338`，delta2-off/joint=`0.3844`；roll panel
为 `0.8287/0.3061`，0/9 targets、0/5 seeds 过门。joint-off 改变 673 个 native decisions，其中两个
single-off 都保留 native decision 的只有 133 个（`0.1976`）。因此 outcome=`similar_but_not_replaceable`。

BSRA exact cycle 以 `negative_boundary / diagnostic_complete` 关闭；新 family=`exploratory /
paused(evidence_gap)`，child=`not_ready/missing_evidence_anchor`，budget=`0/1`。不创建 decorrelation、negative
correlation、diversity 或 complementary-fusion child，也不转为 branch2 pruning/weighting rescue。external
experiment-audit/result-to-claim=`REVIEW_UNAVAILABLE`，claim release=`none`。

机器证据：`results/logs/local/2026-08-23_bsra_v0_1_dsainet_bnci2014001_formal_r2/`。formal r1 与 r2 的
logits/predictions/stage CKA byte-exact，但 r2 才补齐无-hooks native replay identity 门，正式判读只认 r2。

### 15.9 2026-08-24 CRBRA-v0.1：001 的稳定尺度身份不能外推到 004

基于 BSRA re-entry review 形成的新问题，用户已授权建立并运行独立 family
`dsainet-cross-condition-realized-branch-regime` 与 exact cycle
`2026-08-24_dsainet_cross_condition_realized_branch_regime_audit`。CRBRA 完全复用 RBIA 的 descriptor、gate、
45-checkpoint/64-trial scope，只把数据与 checkpoint 等构迁移到 BNCI2014004 official-preproc LOSO。

formal integrity 与独立确定性重算通过：45/45 checkpoint、270/270 correspondence、checkpoint/config/analyzer
hash、NPZ shape/finite、native/additive identity 与 frozen outcome 均一致。004 activation/pooled/contribution
margin 分别为 `-0.009980/+0.018965/+0.017318`；只有 contribution 达到 `6/9 target + 7/10 seed-pair`
same-index 门。kernel learned residual 只有 `13/45` checkpoints 双支同时可观测，declared direction invalid；
frozen outcome=`heterogeneous_or_unobservable`。

只读 post-hoc 定位显示 branch2 learned residual ratio median=`1.04e-5`，26/45 低于 `1e-4`；但两支最终
true-class margin 仍均为45/45正。因此 004 不是简单 dead branch，也不能解释为与001相同稳定尺度只重新配比；
更接近 scale-specific ConvTime transformation 经常近 identity、后续共享/交互路径仍使用该 slot。

CRBRA exact cycle 以 `negative_boundary / diagnostic_complete` 关闭，family=`exploratory/no_go`，不创建 child。
`condition-dependent scale realization` 仅为改变 baseline defect 的新 family candidate；未获新 family/cycle、
training 或 claim 授权。External experiment-audit/result-to-claim=`REVIEW_UNAVAILABLE`，claim release=`none`。

权威入口：

- `experiments/records/2026-08-24_dsainet_cross_condition_realized_branch_regime_audit/research_cycle.md`
- `experiments/records/2026-08-24_dsainet_cross_condition_realized_branch_regime_audit/RESULT.md`
- `experiments/records/2026-08-24_dsainet_cross_condition_realized_branch_regime_audit/_work/verification/S6D_INTEGRITY_RECONCILIATION.md`
- `results/logs/local/2026-08-24_crbra_v0_1_dsainet_bnci2014004_formal/`

### 15.10 CRBRA 后的阶段性判断（已由 CSRPA / SCPRA 更新）

以下记录的是 CRBRA 结束时的阶段性入口判断；其后该 candidate 已在第 15.11 节通过 CSRPA 进入路径审计，
并在第 15.12 节由 SCPRA 以 `exploratory/no_go` 收束。它保留为路线演化史，不是当前待执行建议。

截至 CRBRA 结束时，DSAINet 双分支不能再用一个跨条件不变的简单故事概括：

- 在 BNCI2014001 official-preproc LOSO 上，RBIA 支持 branch index 的 realized identity 跨 seed 稳定，
  declared kernel direction 对应可观测的 effective temporal scale；两支均有实质贡献。这里没有支持
  “分支角色错配”或“名义双尺度未兑现”。
- 在同一 001 scope 上，BSRA 虽观察到高表示相似，但双支不具备冻结合同要求的 bilateral replaceability；
  因而没有支持“可通过简单去冗余、剪枝或互补性正则修复”的结构瓶颈。
- 在 BNCI2014004 official-preproc LOSO 上，CRBRA 只支持 contribution slot 的部分 same-index correspondence；
  activation/pooled regime 异质，且 scale-specific learned residual 尤其 branch2 经常近 identity 或不可观测。
  这既不是稳定 swapped role，也不是可以直接宣称的 dead branch。

因此，当前已关闭或不应继续救援的方向包括：DCBS set-fusion child、BSRA decorrelation/diversity child、
CRBRA 的稳定跨条件 branch-regime 命题，以及 SAFSS/SCCD/FCPSM 已关闭的 support-only routing、简单 modulation
与分支重配比路线。上述结论均只在各自冻结 scope 内成立；尤其不得把 001 的稳定 scale identity 外推到 004，
也不得把 004 的 near-identity learned residual 外推为普遍结构缺陷、性能损害或生理机制。

目前唯一值得保留但尚未准入的科学问题是 `condition-dependent scale realization`：不同数据条件下，
scale-specific transformation 为什么会从稳定可观测变为部分近 identity，而最终 branch slot 仍被后续路径使用。
它是 baseline defect 改变后出现的新 candidate，不是 DCBS、BSRA、CRBRA、SAFSS 或 SCCD 的 rescue，也不继承
任何 child budget、signal、paused 状态或执行授权。建立新 family 前至少还缺三个 evidence anchor：

1. learned-residual observability 是否具有 source-only、跨 seed/subject 稳定性，而非 checkpoint 特异现象；
2. 该 observability 是否与 held-out attribution/decision behavior 存在预先冻结的关联；
3. 即使关联成立，是否存在可证伪的因果修复命题，而不只是 alpha-floor、强制尺度分离或分支重加权。

若低成本 read-only diagnosis 显示 residual observability 不稳定、无法 source-only 识别，或与 held-out branch
attribution/decision behavior 无冻结关联，应直接关闭该 candidate。不得以 post-hoc alpha 阈值、换 descriptor、
换 seed/window/dataset，或直接训练 scale regularizer 作结果驱动救援。任何性能收益、机制或论文 claim 仍需独立
训练证据与可用的 experiment-audit/result-to-claim review；当前 claim release 仍为 `none`。

下一会话若继续研究，建议按以下顺序读取，而不要仅从本 handoff 推断状态：

1. `experiments/records/PROPOSED_FAMILIES.md` 中 CRBRA 与相邻 family 的最新行；
2. CRBRA exact `research_cycle.md`、`RESULT.md` 与 `S6D_INTEGRITY_RECONCILIATION.md`；
3. RBIA、BSRA 的 exact `RESULT.md`，用于区分 001 identity、001 replaceability 与 004 regime；
4. CRBRA formal machine artifacts；post-hoc alpha/observability diagnosis 只作为 selection-exposed 次级材料。

Suggested skills：

- `$wait-what`：只在需要重新解释当前结论时使用，不改变合同或 evidence status。
- `$proposed-research`：仅在用户明确授权对 `condition-dependent scale realization` 做新 family re-entry/admission
  时使用；不得把本节 candidate 自动登记为 family 或 cycle。
- `$research-refine`：获准后先冻结新的 causal question、source-only observable、关联门与直接 falsifier。
- `$experiment-plan`：仅在诊断方法已被明确选择后制定最小充分审计，不提前进入模块或训练设计。
- `$experiment-audit` / `$result-to-claim`：正式证据完成后再调用；review backend 不可用时维持
  `REVIEW_UNAVAILABLE`，不得释放 claim。

### 15.11 2026-08-24 CSRPA-v0.1：004 temporal residual 与 final slot use 分属不同路径

用户明确要求继续研究 `condition-dependent scale realization` 后，建立独立 family
`dsainet-condition-dependent-scale-realization` 与 exact cycle
`2026-08-24_dsainet_condition_dependent_scale_realization_audit`。CSRPA 是 45-checkpoint × 64-trial、零训练、
只读的 residual-formation 与 downstream-path 审计，不重开 CRBRA/BSRA/DCBS/SAFSS。

formal r2 与独立确定性复核通过，frozen outcome=`transform_collapse_with_downstream_slot_use`。004 branch2
形成明显 active/collapsed 双态：26/45 residual ratio `<1e-4`，collapsed/active 的 max inside-layer
`|alpha|` 中位数为 `0.000194/1.0418`，unscaled post-BN transform/input 为 `0.000194/0.2740`；cancellation
median=`1.040/1.140`，不支持层间抵消解释。branch1 也有 9/45 collapsed，故它是 zero-gated ConvTime 的
一般优化风险，但 branch2 更频繁。

collapsed 26 checkpoints 中，强制 delta2-off 的 relative logit change median=`7.52e-8`、slot2 contribution
CKA=`1.0`、true-margin positive=`26/26`；non-collapsed 19 checkpoints 中相同量为 `0.2788/0.7258/18/19`。
因此只有 collapsed regime 支持 residual/slot decoupling，不能写成 branch2 temporal residual 普遍无用。

collapsed subset 的顺序路径分解显示：delta2-off 后再去 big residual2 只带来 `0.0147` median relative logit
change；继续 bypass intra2 后为 `0.1218`，再 bypass inter2 后为 `0.4251`，slot2 contribution CKA 依次为
`0.9980/0.8763/0.0594`。最终 slot contribution 主要由 shared `a0` 进入独立 intra/inter attention 后形成，
不是 nominal temporal-scale residual 的延续，也不能简化为 classifier 直接重复读取 base。

released ConvTime 的 `alpha=0` 初始化使 transform parameters 首步梯度被乘零；004 collapsed checkpoints 的
alpha、unscaled transform 与 residual 同时极小，而 001 branch2 max alpha 中位数=`0.8727`、45/45 可观测。
这与 early escape/optimization lock-in 一致，但缺少训练轨迹，尚不能把它写成 001/004 差异的根因。

更重要的是，additive true-margin positive 不等于净 CE utility：native slot2-off CE contrast 只有 6/45 为正，
collapsed subset 只有 1/26。这一 target-exposed secondary finding 不授权剪枝、重加权、alpha-floor、改初始化或
scale regularizer。CSRPA exact cycle 以 `supporting_evidence / diagnostic_complete` 关闭；family=
`exploratory/paused(evidence_gap)`，child not ready，budget=`0/1`。缺口为 source-only predictor、与性能/稳健性的
预冻结关系、训练早期 trajectory 以及单变量因果修复。External reviews=`REVIEW_UNAVAILABLE`，claim none。

权威入口：

- `experiments/records/2026-08-24_dsainet_condition_dependent_scale_realization_audit/research_cycle.md`
- `experiments/records/2026-08-24_dsainet_condition_dependent_scale_realization_audit/RESULT.md`
- `experiments/records/2026-08-24_dsainet_condition_dependent_scale_realization_audit/_work/verification/CSRPA_R2_DETERMINISTIC_VERIFICATION.json`
- `results/logs/local/2026-08-24_csrpa_v0_1_dsainet_bnci2014004_formal_r2/`

### 15.12 2026-08-24 SCPRA-v0.1：collapse 没有形成 performance bottleneck anchor

用户授权按计划执行第一项 Performance-Relevance Audit 后，在同一
`dsainet-condition-dependent-scale-realization` family 下建立
`2026-08-24_dsainet_scale_collapse_performance_relevance_audit`。SCPRA 零训练合并 CSRPA 45-row state
metrics 与三个原始 004 full-test shards；主 observable 为 source-only checkpoint 参数
`log10(max |alpha_b2|+1e-12)`，主 outcome 为 untouched full-test accuracy。统计先在 target 内中心化，
100000 次 permutation 只在同 target seeds 内交换。

45/45 join、input hash 与独立统计重算通过，frozen outcome=`no_stable_performance_relation`：

- alpha vs accuracy within-target rho=`-0.0621`，positive-direction p=`0.6345`；
- target direction=`3 positive / 6 negative`；LOTO rho range=`[-0.1444,+0.0078]`；
- 8 个同时含 active/collapsed 的 targets 中，active−collapsed accuracy median=`-0.002465`（`-0.246 pp`），
  没有达到预冻结 `+1 pp` harm 门；
- alpha vs F1 rho=`-0.1074`；residual ratio vs accuracy=`-0.00475`；unscaled transform vs accuracy=`-0.0750`。

因此 CSRPA 的 active/collapsed 双态是真实现象，但在当前 004 scope 内不是有证据支持的性能缺陷。略负方向也
没有通过对称 benefit 门，不得写成 collapse 有益。SCPRA exact 以 `negative_boundary / diagnostic_complete`
关闭；family=`exploratory/no_go`，child not applicable，budget=`0/1`。

本结果直接关闭为了恢复 nominal temporal transform 而做的 alpha-floor、改初始化、scale regularization、
新模块、pruning 或 branch reweighting。Early trajectory audit 只剩纯机制刻画价值；在 performance anchor 缺失后，
不再是当前结构创新主线的必要投入，也不得作为 repair pretext。External reviews=`REVIEW_UNAVAILABLE`，claim none。

权威入口：

- `experiments/records/2026-08-24_dsainet_scale_collapse_performance_relevance_audit/research_cycle.md`
- `experiments/records/2026-08-24_dsainet_scale_collapse_performance_relevance_audit/RESULT.md`
- `experiments/records/2026-08-24_dsainet_scale_collapse_performance_relevance_audit/_work/verification/SCPRA_DETERMINISTIC_VERIFICATION.json`
- `results/logs/local/2026-08-24_scpra_v0_1_dsainet_bnci2014004_formal/`

## 16. 2026-08-26 RACR-v0.1：stable paired dependence 未形成 joint discriminative utility

RACR 是独立 family `dsainet-role-anchored-conjunctive-readout` 的 exact core test：
`2026-08-24_dsainet_role_anchored_conjunctive_readout`。它不属于 SAFSS/SCCD/FCPSM、DCBS、BSRA 或
004 scale-realization 的 child，也不继承这些路线的 signal、budget 或执行授权。问题被严格限定为：在
BNCI2014001 的 stable、nonreplaceable pooled roles 上，native linear concat readout 是否漏掉同一 trial 的
低维 conjunction utility。

### 16.1 r5 discovery screen 与 source-only residual falsifier

完整回拉的 r5 具有 B0/P1/M1 × 2 seeds × 9 targets = 54 个唯一 unit；predictions、checkpoints、splits 与
exact paired split signatures均已闭合。P1 是固定 rank-4、337 参数、zero-start signed Hadamard residual；
M1 是同参数 generic MLP control。

- B1：P1−B0 overall=`+0.000 pp`；seed0/1=`+1.389/-1.389 pp`，只有5/9 target 的 two-seed mean 为正；
- B2：P1−M1 overall=`+0.569 pp`，但 seed1=`-1.138 pp`，specificity gate 失败；
- 36 个 P1/M1 source-validation checkpoint 的 class-preserving pairing audit 中，P1 residual margin drop
  每个 unit 都为0，虽然 branch marginals、split 与 checkpoint provenance 均已验证。

冻结 outcome=`no_signal`。不进入 S6R，不增加 seed，不调 rank/gate/threshold/window/optimizer，不重训，也不创建
RACR child、benchmark 或 claim。此性能/机制失败不等于“所有 cross-branch interaction 无效”，只关闭 exact
RACR-v0.1 readout 路径。

### 16.2 B0 representation dependence 与 label-utility 区分

为避免把 “P1 inactive” 误读为 “representation 没有任何同试次结构”，在同一18个 B0 checkpoint 上进行两项
用户授权、只读 source-only diagnostic。

第一项在每个 source-validation class 内循环置换 branch-2，并保持 branch marginals 不变。true-vs-shuffled
linear CKA drop overall=`+0.607858`，seed0/1=`+0.639905/+0.575812`，9/9 target 的 two-seed mean 均超过
`0.01`。它只证明 B0 pooled representations 存在强、稳定的 conditional paired dependence。

第二项直接测试该 dependence 是否有额外 label utility：每个 unit 只在 source-train 标签上拟合一次性
multinomial logistic probes，比较 additive `[p1;p2]` 与 interaction `[p1;p2;p1⊙p2]`，只在 held-out
source-validation true/shuffled pair 上评分。18/18 的 checkpoint、split、identity、class marginals 与 probe
convergence 门均通过；未读取 target EEG/labels，也未更新 B0/RACR 权重。结果为
`no_anchor_under_fixed_probe`：

| 冻结主读数（nats） | Overall | Seed 0 | Seed 1 | 通过情况 |
|---|---:|---:|---:|---|
| true-pair interaction 增益 | `-0.056406` | `-0.067179` | `-0.045633` | fail，0/9 target |
| joint probe shuffle loss | `-0.241202` | `-0.291841` | `-0.190563` | fail，0/9 target |
| pairing-sensitive gain | `+0.019110` | `-0.001621` | `+0.039841` | fail，仅4/9 target |

因此应同时保存两个事实：**paired dependence 存在**，但它没有在本冻结、held-out product probe 中转化为
稳定 incremental label utility。不能据此声称 native additive readout 忽略了可用联合信息，也不能称 RACR
learning interface 有可修复 bug。

### 16.3 当前路由与下一会话入口

- RACR-v0.1 保持 `no_signal`；其 exact contract 禁止 rank/gate/seed/child rescue。
- 如果未来要讨论不同问题，只能在单独授权的 S6M direct-exception 后，作为不继承 RACR signal/budget/参数的
  independent new-family candidate；必须先冻结不同的 baseline defect、直接 label-relevance falsifier 与方法合同。
- 外部 `experiment-audit` / `result-to-claim` reviewer 不可用，所有 RACR claim 继续 `REVIEW_UNAVAILABLE`，
  `claim_release=none`。

权威入口：

- `experiments/records/2026-08-24_dsainet_role_anchored_conjunctive_readout/research_cycle.md`
- `experiments/records/2026-08-24_dsainet_role_anchored_conjunctive_readout/_work/results/S6D_AUDIT.json`
- `experiments/records/2026-08-24_dsainet_role_anchored_conjunctive_readout/_work/results/S6D_SOURCE_ONLY_PAIRING_AUDIT.json`
- `experiments/records/2026-08-24_dsainet_role_anchored_conjunctive_readout/_work/results/B0_SOURCE_ONLY_JOINT_DEPENDENCE_AUDIT.json`
- `experiments/records/2026-08-24_dsainet_role_anchored_conjunctive_readout/_work/results/B0_SOURCE_ONLY_JOINT_DISCRIMINATIVE_UTILITY_AUDIT.json`

Suggested skills for a later, separately authorized continuation:

- `$wait-what`：只解释 “paired dependence” 与 “incremental label utility” 的区别，不改变状态；
- `$proposed-research`：仅在用户明确要求 S6M direct-exception 或独立 new-family admission 时使用；
- `$research-refine` / `$experiment-plan`：仅在新问题获准后冻结 direct falsifier、scope 与停止规则；
- `$experiment-audit` / `$result-to-claim`：只在新正式结果出现后使用；reviewer 不可用时保持 fail-closed。

## 17. 2026-08-29 RAIA-v0.1：共享方向消息变换未形成 direction-specific signature

RAIA 是独立 family `dsainet-role-asymmetric-interaction-adapter` 的 initial core test：
`2026-08-27_dsainet_role_asymmetric_interaction_adapter`。它把问题限定在 DSAINet 原生
`InterAttnBlock` 对两个有序跨 branch 方向复用同一 MHA/FFN 的消息变换。该代码事实只构成待检验缺口，
不证明 sharing 有害；RAIA 不属于 SAFSS/SCCD/FCPSM、RACR、BSRA、RBIA/DCBS 或 004 scale-realization
的 child，也不继承它们的 signal、budget、执行授权或 claim。

### 17.1 已证明、已关闭与未知

| 状态 | 本轮能保留的结论 | 严格边界 |
|---|---|---|
| 已证明 | r4 的 54 个 B0/P1/C1 full training units、18 个 A1 evaluation-only units、54 份预测重算与跨 arm 配对均完整；A1 使用相同 P1 checkpoint、同 test index、无重训。 | 这是完整性与可复算性证据，不是性能或机制 claim。 |
| 已证明 | 在该 frozen screen，A1 direction-label swap 的 P1−A1 overall ACC 差为 `0.0000 pp`。 | 只说明预声明的 direction-specific loss 没有出现；A1 不是第二个训练模型。 |
| 已关闭 | RAIA-v0.1 的 pre-frozen signature：P1 同时稳定超过 B0、同参数 shared C1、并在 A1 下出现方向标签损失。P1−B0=`+0.5401 pp`、P1−C1=`+0.4823 pp` 还分别在 seed-1 与一项 LOTO 上失败。 | exact cycle 已 S9 `negative_boundary / completed_not_promoted`；不得 rank/init/gate/seed/target/dataset/A1 rescue、child、same-snapshot re-entry、benchmark、confirmation 或 claim。 |
| 未知 | 其它独立定义的 baseline defect 是否会支持不同的 cross-branch method。 | 这不是 RAIA 的延伸授权；必须以新 evidence anchor、独立 family 和新的明确授权处理。 |

### 17.2 对 DSAINet interaction 叙述的影响

RACR 与 RAIA 都是 negative boundary，但测试的对象不同。RACR 关闭的是 stable pooled roles 上 fixed
same-trial product readout 的 label-utility 路径；RAIA 关闭的是 native inter-attention message 后、同参数
direction-indexed residual adapter 的 frozen signature。二者都不能被改写为“所有 interaction 无效”，也不能把
BSRA 的方向不对称功能响应反推成“shared parameters 已被证明有害”。

因此当前 map 中关于 branch interaction 的正确表述是：多个具体入口已关闭，广义问题仍未知；不得以
representation dependence、局部不对称或这次小的 overall 正方向作为训练新模块的充分前提。

### 17.3 权威入口与关闭状态

- exact state：`experiments/records/2026-08-27_dsainet_role_asymmetric_interaction_adapter/research_cycle.md`
- deterministic intake：`experiments/records/2026-08-27_dsainet_role_asymmetric_interaction_adapter/_work/results/RAIA_V0_1_S6D_INTAKE_AUDIT.json`
- S6D / S6M / S9：`experiments/records/2026-08-27_dsainet_role_asymmetric_interaction_adapter/_work/decisions/`
- family registry：`experiments/records/PROPOSED_FAMILIES.md`

外部 `experiment-audit` 与 `result-to-claim` favourable verdict 均未运行；`claim_release=none`。后续会话应将
RAIA 视为已关闭的 exact negative boundary，而不是可继续调参或可合并进 SAFSS/RACR 的证据池。
