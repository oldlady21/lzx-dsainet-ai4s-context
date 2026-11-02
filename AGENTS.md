# AGENTS.md

本文件用于约束 GPT / Codex / Claude Code 在本仓库中的默认协作方式。

## 仓库目标

本仓库服务于第一篇 MI-EEG 高水平论文，主要任务包括：

1. 文献整理与复现
2. 创新点与实验设计
3. 论文撰写与投稿准备

所有操作都应优先服务这三类任务。

## 项目背景

该论文属于整体 EEG 解码与 BCI 应用主线中的一个核心子项目。  
当前重点是先把这一篇 MI-EEG 论文推进完整，形成稳定的文献、实验与写作闭环。

## 默认协作原则

### 1. 先 baseline，后创新
默认先完成强 baseline 的复现与统一评估，再开展 proposed model 设计和改动。

### 2. 先收敛，后扩展
优先帮助用户收敛问题、模型和实验设计，围绕当前论文推进，不主动扩展到与本论文无关的更大范围任务。

### 3. 文档先行
涉及研究方向、实验协议、模型路线、写作结构的重要变化，优先同步到：
- `DECISIONS.md`
- `TASKS.md`
- `PAPER.md`

### 4. 保持轻量
不要主动引入复杂的项目管理层、自动化系统或大而全目录，除非用户明确要求。

### 5. 优先可复现
所有代码与实验修改应尽量可回溯、可解释、可复现。

## AI 助手分工

### GPT
默认负责：
- 论文方向分析
- 文献筛选与归纳
- 创新点讨论
- 实验设计审查
- 论文结构与写作
- 帮助维护 `DECISIONS.md`、`TASKS.md`、`PAPER.md`

### Codex
默认负责：
- baseline 代码搭建与修复
- 模型模块实现
- 训练与评估脚本编写
- 实验代码执行相关工作

### Codex 子 Agent

主 Agent 保持研究判断、实验授权、协议解释与最终验收。Astra、Sol 主 Agent 可按任务需要主动向下委派 Terra、Luna 子 Agent，无需用户逐次要求。对于输入范围明确、可独立验收且委派能节省时间或改善质量的任务，优先委派并回收简短结果；模型与推理强度以 `.codex/agents/` 配置为准：

- `explorer`：跨文件阅读、代码扫描、日志定位与支持性审查；
- `executor`：文件定位、指标摘取、格式修复与边界明确的小型实现。

每个子 Agent 使用精确输入与验收条件的短任务包；需要并行时按任务独立性拆分，避免重复读取同一长研究历史。子 Agent 的结果不单独决定研究结论、协议、实验授权或 claim。

### Claude Code
默认负责：
- 大范围代码阅读
- 多文件修改前的 plan
- 仓库结构理解与整理
- 复杂代码改动前的全局分析

## 代码约束

- 不要在未跑通 baseline 前大规模实现 proposed model
- 不要在没有明确记录的情况下修改关键实验协议
- 不要随意堆积临时 notebook 和废弃脚本
- 不要为了“看起来完整”而提前搭建庞大框架
- 所有新增目录和文件应有明确用途

## 实验约束

- 每个重要实验都应留下简要记录
- 实验命名尽量清楚，能反映目的
- baseline 与 proposed 的评估协议应尽量统一
- 图表和结果文件应尽量集中保存于 `results/`

## 按任务读取

- AI4S Program：从 `ai4s/README.md` 进入，读取唯一 Prompt Index、对应 L1/L2/L3、Program、State 与 Evidence Index。各 Program 的活动链以 `ai4s/PROMPT_INDEX.yaml` 为准；同时核对 active_operation 与 active_run。新研究读取唯一 Prompt Index 为该 Program 选定的 L1/L2/L3，按“证据引用 → 判断变化 → 设计变化或停止 → 下一项对照”形成研究记录；旧 campaign、Run、operation 和冻结续接按其绑定的旧链继续收尾，禁止静默切换。Transaction 实施见 `ai4s/_work/migration_20260905/IMPLEMENTATION.md`；2026-09-05 物理归档与验证见 `ai4s/_work/structure_20260905/REPORT.md`。历史内文旧路径按 `ai4s/archive/PATH_MAP.json` 解析。

- 新科研流程：按基模绑定 AI4S Program，同一 Program 容纳多个 research；Foundry 独立生成候选，用户选择后只交接到对应 Program，不自动建研究或启动实验；AI4S 也接受用户直接给定 idea。正式评估按活动链读取 `ai4s/prompts/EVALUATION_EVIDENCE.md`，普通探索无需评估计划或 Claim Ledger。新版规则要求诊断明确服务于设计取舍；筛查、诊断和负结果都必须登记后续处置，跨 Program 只共享证据与设计约束，不自动共享实验授权。
- 权威记录：State 管运行，Evidence Index 管证据，按需建立的 Program Claim Ledger 管逐 Claim 判断；顶层任务与论文摘要不替代这些记录，也不授予实验权限。
- 历史 proposed：仅按明确来源读取原 `research_cycle.md`、合同和证据；旧 Run 按冻结合同收尾，不新建或推进 cycle/family 流程。`_work/decisions/` 保留为历史结论入口。
- local experiment：读取 `experiments/LOCAL_WORKFLOW.md` 和手册的相关操作段；进入公开比较时读取 `experiments/UNIFIED_EVALUATION_PROTOCOL.md`（UEP）。
- remote execution：读取 `experiments/REMOTE_WORKFLOW.md` 与 `experiments/ENVIRONMENT.md` 的当前平台/执行级别段。
- [REDACTED_MACHINE] 上传、排队、拉回：读取 `experiments/REMOTE_CCMU_QUEUE_AGENT.md`。
- decision：先以 `D-xxx` 检索 `DECISIONS.md`；writing：只读取相关 `PAPER.md` 或 draft 段。

## 本地实验引导

当用户要求 Codex 进行本地实验、复现实验、训练/评估脚本修改、结果整理或实验记录维护时，默认先参考：

- `experiments/LOCAL_WORKFLOW.md`
- `experiments/LOCAL_EXPERIMENT_MANUAL.md`

Codex 应主动按手册引导或执行以下事项：

- 在项目根目录 `./` 下运行实验命令
- 使用 `conda activate mieeg` 作为默认本地环境
- 为每次实验创建清晰的 `exp_id`
- 将原始数据、预处理数据、第三方模型代码、checkpoint、runs 和机器产物放入手册约定目录
- 将完整本地机器产物保存在 `output/local/<exp_id>/`
- 将有保留价值的关键日志整理到 `results/logs/local/<exp_id>/`
- 将对论文判断有价值的实验记录到 `experiments/records/<model>/<exp_id>.md`
- 当本地 GPU 利用率长期偏低且显存占用很低时，优先按手册建议并行运行多个独立 subject 或 seed；不要优先通过静默修改 batch size、AMP、cudnn 等训练配置来提速
- 当实验规模超过本地电脑适合范围时，建议切换到服务器运行

除非用户明确要求临时试错，Codex 不应让重要实验只停留在终端输出中。

## 写作约束

- 论文草稿拆分保存在 `draft/`
- related work、method、experiments 可分文件维护
- 不要求一开始搭完整投稿模板，先积累内容
- 论文写作应与实验同步推进，而不是等所有实验结束后再开始

## 默认避免事项

- 在无记录情况下改变论文主问题
- 过度设计仓库结构，增加维护负担
- 引入与当前论文推进无关的大量新任务

## Skills 的项目调用规则

全局第三方 Skills 提供通用方法；本仓库的研究权限、对象身份和停止点由本文件及其链接的活动链/冻结合同决定。调用子技能时传递精确输入、允许输出位置、所需阶段和停止点，完成后返回调用方；子技能的 standalone 示例不扩张当前授权。`mieeg-ai4s` 与 `mieeg-idea-foundry` 位于本仓库 `.agents/skills/`，保留唯一名称并仅显式调用；AI4S 路由读取现有项目文档及唯一 Prompt Index。

- Foundry 调用 `idea-creator` 时，使用本轮 Host/证据/旧案包及本轮输出目录，只取视角发散、候选生成和机械合并；跳过 wiki rebuild、完整评审/查新链、pilot 设计或执行、独立排名报告、wiki 写入及自动后续阶段，除非本轮明确要求该具体阶段。子任务结果记录实际 `adapted` 范围。详细产物及调用边界沿用 Foundry 的 `references/evidence-and-host-contract.md`、`references/candidate-schemas.md` 和其“科研技能：按问题调用”段。
- `novelty-check` 的结论是初步查新，不证明首次、科学有效性或实验资格。`research-review`、完整性审计与主张判读的触发、复用及停止规则读取 [`ai4s/prompts/EXTERNAL_REVIEW.md`](ai4s/prompts/EXTERNAL_REVIEW.md)；持续材料授权不增加例行外审门，也不授权训练或协议变更。
- AI4S 调用 `experiment-audit` / `result-to-claim` 时，必须给出 Program ID、`EVALUATION_PLAN.yaml` 的路径/SHA-256、Claim ID、精确 evidence IDs、限定材料清单及 `output_dir`，并读取 [`ai4s/prompts/EVALUATION_EVIDENCE.md`](ai4s/prompts/EVALUATION_EVIDENCE.md)。只读取所给材料及核验必需的直接引用，保留原完整性/claim 清单与独立 Grok 审查。两项职责共用一次覆盖完整的联合外审和真实 trace，分别形成报告；已有有效覆盖直接复用，不再自动调用第二次 reviewer。
- 上述报告与完整 trace 只写提供的 `output_dir`，绑定同一 Program、Claim、计划 SHA 和 evidence IDs，并返回 AI4S。不得从审计子任务自动补实验、启动 pipeline、写 wiki/findings/知识库、修改 CLAUDE.md、Program State、Ledger 或论文。外审未完成、材料缺失或 trace 不可用时返回 `pending` 与缺口，不能改写为 `no` 或通过。
- 解释 AI4S 或历史 proposed 对象时，保持对象、冻结协议、假设和证据状态；解释不激活研究、不改合同、不授予实验权限。Foundry 卡片的解释及 provenance 继续按已有候选规范执行。调用通用 `wait-what` 前，读取 [`ai4s/prompts/MIEEG_AI4S_SKILL_ROUTER.md`](ai4s/prompts/MIEEG_AI4S_SKILL_ROUTER.md) 的“wait-what 项目解释规则”专节；该解释分支不调用 AI4S 运行入口。
- 本仓库实验、接入、resume、监控和停止仍从 `ai4s/README.md`、唯一 Prompt Index、精确 Program 及其活动链进入；通用 Skill 不启动另一条实验链，也不以 pilot 超时常量覆盖当前 Run 的停止授权。

AI4S 接入与续接保留原入口的边界：一个 Program 对应一个 baseline implementation，并承载其多个 research。已有精确匹配 Program 时绑定它，在其活动链内添加或继续 research，不重复 PROJECT_ADMISSION；不存在 Program 时，按现有 [`ai4s/prompts/PROJECT_ADMISSION.md`](ai4s/prompts/PROJECT_ADMISSION.md) 准备并等待用户确认，不自动创建 Program、campaign 或实验。Foundry 只提供 Program 指针，不修改其活动 operation/Run 或自主恢复规则；活动 operation 同样阻止 AI4S 项目切换。
