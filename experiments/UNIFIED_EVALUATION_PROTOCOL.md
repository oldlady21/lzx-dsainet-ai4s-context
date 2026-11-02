# MI-EEG 统一评估协议

## `mieeg-uep-v1.0`

**状态：冻结。** 本协议服务于本仓库公开 MI-EEG 的横向比较，优先吸收已完成的
DBConformer、DSAINet、SST-DPN 及同数据路径迁移 baseline 结果。它固定共同的
**评估合同**，不要求不同模型放弃其已冻结且无泄漏的原生训练日程。

本协议不是原论文复现协议。原论文数据路径、训练日程和报告口径仍应单独标为
`paper-aligned`，不得与本协议主表混用。

## 1. 每个实验的必填标签

每次 `check`、`smoke`、`pilot`、`full`、`diagnostic` 或 `ablation` 开始前，在
实际配置、`command.txt`、实验记录和 SwanLab config 中写入：

```text
protocol_id: mieeg-uep-v1.0
training_profile: <profile-id>
compatibility_label: exact-paired | eval-compatible | paper-aligned | diagnostic
```

- `exact-paired`：数据、外层索引、公共 seeds、训练 profile 与汇总规则均一致；可作
  架构级配对比较。
- `eval-compatible`：共同评估合同一致，但训练 profile 不同；只作完整模型管线比较。
- `paper-aligned`：为对齐原论文而保留的独立数据路径或日程；不进入 UEP 主表。
- `diagnostic`：用于链路、test-best、消融或敏感性诊断；不进入正式性能主表。

## 2. 共同评估合同（硬约束）

| 维度 | 固定设置 |
| --- | --- |
| 数据版本 | `data/processed/dsainet/BNCI2014001_official_preproc` 或 `BNCI2014004_official_preproc`；运行前记录 `X.npy`、`labels.npy`、`subject_ids.npy`、`meta.csv` 与预处理配置的哈希。 |
| BNCI2014001 | 9 被试、双 session、22 EEG 通道、四分类、250 Hz、`[0, 4)` s、1000 samples、0.5–40 Hz。 |
| BNCI2014004 | 9 被试、全 5 sessions、3 EEG 通道、左右手二分类、250 Hz、`[0, 4)` s、1000 samples、0.5–40 Hz。 |
| EA | 禁用；启用 EA 的原生或探索性运行另行标记，不得混入 UEP 主表。 |
| CO | 使用 `meta.csv` 的固定 `split_role=train/test`（或等价 session 角色），不改为 chronological 80/20。 |
| CV | 每被试 `StratifiedKFold(n_splits=5, shuffle=True, random_state=seed)`；保存或核对 split fingerprint。 |
| LOSO | 8 个 source subjects 训练、1 个 held-out target subject 最终测试；target 标签不得参与任何训练、统计或选择。 |
| 内层验证 | 只能从当前 outer-training/source 范围生成；验证索引及 random state 必须记录。具体拆分可由 training profile 冻结。 |
| 测试使用 | 只允许在 checkpoint 与训练设置已冻结后评价；测试指标不得参与 epoch、模型、超参数或数据处理选择。`test-best` 永不进入正式结果。 |
| 主指标 | ACC、Cohen's Kappa；F1 必须注明 `macro` 或 `weighted`。跨模型 F1 主表仅使用从相同 checkpoint/预测统一重算的同一 averaging。 |
| CV 汇总 | 为兼容存量结果，先对 5 个 fold 指标等权平均为一个 `(subject, seed)` 行；新运行同时保存 fold 预测，供后续 OOF 重算但不得与旧口径混写。 |
| 完整性 | 每个数据集、模型、协议均须核对唯一键、split fingerprint、checkpoint、结果 CSV、状态与缺失/重复数。CO/LOSO 为 45 行；CV 为 225 fold 行及 45 subject-seed 汇总行。 |

## 3. 训练 profile（允许差异，但必须冻结）

### `tp-dsainet100-v1`

适用于 DBConformer、DSAINet，以及明确迁移到 DSAINet 100-epoch 训练日程的模型：

```text
seeds: [0, 1, 2, 3, 4]
epochs: 100
batch_size: 32
optimizer: Adam(lr=1e-3, weight_decay=1e-4)
scheduler: none
normalization: inner-train-only Z-score
augmentation: classwise_segments=8
model_selection: maximum validation accuracy; validation loss breaks ties
test_best: false
```

同一 profile、相同外层索引和相同 seeds 的 DBConformer 与 DSAINet 可标记为
`exact-paired`。

### `tp-sstdpn-native-v1`

适用于已完成的 SST-DPN 项目 processed-data 结果：

```text
seeds: [1, 2, 3, 4, 5]
batch_size: 32
optimizer: AdamW(feature extractor) + independent Adam(ISP/ICP)
schedule: Dataset I/II 已冻结的 phase-1 + phase-2 日程
validation: source/train-only stratified split, random_state=42
model_selection: minimum validation loss checkpoint before phase-2
test_best: false
```

它在 UEP 中标记为 `eval-compatible`：可与其他模型在相同数据和 outer-test 单元上
比较完整模型管线，但不得表述为仅网络结构差异导致的结果。

### `tp-stgmfm-dsainet100-v1`

适用于已完成的 STGMFM 统一迁移结果：`seeds=[0,1,2,3,4]`、`100` epochs、batch size
`32`、Adam `lr=1e-3`、weight decay `1e-4`、无 scheduler、训练集派生 Z-score、
`validation-best`、无 EA、`test-best=false`。它与 `tp-dsainet100-v1` 的唯一冻结差异是
`classwise_segments=0`，因此使用同一数据和 outer split，但标记为 `eval-compatible`，而非
`exact-paired`。

### `tp-smanet100-v1`

适用于 SMANet-100 的已完成 LOSO/CO/CV 结果：`seeds=[0,1,2,3,4]`、单阶段 `100` epochs、
batch size `16`、Adam `lr=1e-4`、CenterLoss、source-only validation、validation accuracy
checkpoint、stage 2 disabled、无 EA、`test-best=false`。它可作为 `eval-compatible` 的
统一协议扩展，不得作架构级 `exact-paired` 归因或补写为原文原生日程结果。BNCI2014001
CO/CV 的已完成分片在服务器重启后经只读恢复与归档核验；BNCI2014004 CO/CV 以独立新
RunId 完成，因此四个 CO/CV 阶段必须保留其分阶段 provenance，而不得叙述为同一原始
RunId 的原子完成套件。

### `tp-mvcnet-uep-v1`

适用于 MVCNet 重新进入统一协议的训练：`seeds=[0,1,2,3,4]`、`100` epochs、batch size
`64`、Adam `lr=1e-3`、weight decay `0`、无 scheduler、inner-train-only Z-score、
source-only `validation-best`、无 EA、`test-best=false`。保留 MVCNet 的 IFNet、
Transformer/projector、flip/frequency-shift/channel-reflection 三视图及 CVC/CMC 目标；
BNCI2014001 四分类的 channel reflection 固定为左右手 `0<->1`，feet/tongue 两个中线类
`2/3` 不变。统一数据已是 `[0,4)` 的 `1000` samples，因此不再执行原脚本针对 `1001`
samples 的末样本裁除。

该 profile 与 `tp-dsainet100-v1` 在 batch size、weight decay 和模型专属增强/损失上不同，
故只标记为 `eval-compatible`，支持相同 outer-test 合同下的完整管线比较，不支持
`exact-paired` 架构归因，也不等同 MVCNet 原论文复现。

其他模型若进入 UEP，必须沿用已存在的冻结 profile，或建立新的
`tp-<model>-<version>` 并说明其与现有 profile 的差异；不得为了追求表面一致性重写
已经完成模型的训练日程。

## 4. 存量结果的正式使用方式

| 目的 | 使用规则 |
| --- | --- |
| DBConformer vs DSAINet 架构比较 | 使用 `tp-dsainet100-v1` 的完整 seeds `[0,1,2,3,4]` 与同一 `(subject, seed[, fold])` 行。 |
| 含 SST-DPN 的零重跑横向比较 | 使用共同 seeds `[1,2,3,4]`；CO/LOSO 为 36 个 subject-seed 行，CV 为 180 个 fold 行及 36 个汇总行。 |
| 模型自身稳定性 | 保留各模型已完成的 5-seed 全量汇总；seed 集不同的结果不得冒充严格配对。 |
| 将来需要 5 个公共 seeds | 优先只为最终入表的 `tp-dsainet100-v1` 模型补 seed 5；不重跑已有 seeds。 |
| F1 统一 | 从保存的 checkpoint 对固定测试索引做只读推理，保存 `y_true/y_pred` 后统一补算 Macro-F1 与 Weighted-F1；这不是重新训练或重新选模型。 |

## 5. 汇总与显著性检验

性能描述沿用已有可复现口径：每个 seed 先平均 9 个被试，再报告这些 seed means 的
均值与标准差，并明确表头为 `mean ± SD across seed-level subject means`。

显著性检验以 subject 为单位。对每个 subject，先在共同 paired seeds 上平均模型差值，
再在 9 个 subject-level 差值上进行 paired Wilcoxon 或配对置换检验。不得把 36 或 45 个
subject-seed 行当作独立样本。多模型或多主指标比较时，预先指定主指标，并进行 Holm
校正或明确其为探索性分析。

## 6. 运行前与汇总前门禁

### 运行前

- [ ] `protocol_id`、`training_profile`、`compatibility_label` 已写入实际配置。
- [ ] 数据与 metadata 哈希、外层/内层 split fingerprint 已生成或已核对。
- [ ] EA、测试使用边界、F1 averaging 与模型选择规则符合本协议或对应 profile。
- [ ] 若不是 `exact-paired`，实验记录已说明其只能支持 pipeline-level 比较。

### 正式汇总前

- [ ] 实验已完成真实阶段；`check`、`smoke`、`pilot`、`interrupted` 不汇总为性能。
- [ ] 所有预期 `(subject, seed[, fold])` 键、checkpoint 和状态均完整，无缺失或重复。
- [ ] 所有待比较模型使用相同数据哈希、outer split 和共同 seeds。
- [ ] F1 的 averaging 一致；否则只比较 ACC/Kappa，并将 F1 分列标注。
- [ ] 主表、显著性检验和文字结论的兼容性标签一致。

## 7. 变更规则

以下任一变化必须创建新 protocol ID，不能修改 `mieeg-uep-v1.0`：数据版本、通道或
任务空间、外层划分、EA、测试使用边界、指标定义、CV 聚合方式或统计单位。

只补充日志字段、修正不改变结果的文档表述，或为已有 frozen training profile 增加审计
信息，不改变 protocol ID；若新增训练日程，则新增 training profile ID。

## 8. 存量结果归档

`results/archives/mieeg-uep-v1.0/` 是本协议存量结果的只读审计索引：其中保存统一
processed data 的 SHA-256、可复算的 split fingerprint、结果 CSV 的来源和兼容性标签。
它不替代原始机器产物，也不将缺失的预测或 checkpoint 推断为已存在。汇总主表前应以该
目录的 `result_registry.csv` 和 `integrity_summary.json` 为准核对完整性；F1 averaging 不同
时，仍仅比较 ACC/Kappa，直到能从 validation-best checkpoint 的固定测试推理补齐两种 F1。
