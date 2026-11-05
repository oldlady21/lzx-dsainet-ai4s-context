# DSAINet 当前研究认识

## 2026-11-01 194小时已登记；提出仅本次审批等待暂停方案

本次确认新增3h已登记至194，原起点及旧账不变。12:38实际driver预算门余额−4.55h，低于2h固定TECH预留，未上传/启动。29项候选闭包仍通过，无新科学结果。为避免原时钟继续计人工确认等待造成反复小额追加，提出再增8h至202并仅本次申请至确认的无任务人工等待单独暂停；两项均未批准/未应用，此前等待不退款。当前仍194、人工等待抵扣0，P0关闭保持。[登记与方案](ds07-r1/preparation/AUTHORIZATION194_REPORT.md)。


## 2026-11-01 DS07技术额度191已登记；固定2h预留仍未满足

用户确认后新增28h至191，原时钟/旧队列/关闭记录保持，P0-CUE不恢复。DS07技术候选包29文件闭包及6条离线测试通过；Grok执行路径增量原判READY_FOR_BUDGET_ONLY，不是GPU验收。因审批间隔与继续计时，191h余额仍低于固定2h技术预留；未冻结、上传、注册或启动任何TECH/科学Run。提出再加3h至194的方案但未应用。同一载荷/目录授权沿用，不重复要运输确认。[登记和准入报告](ds07-r1/preparation/AUTHORIZATION191_REPORT.md)。这些只是工程与授权信息，不改变DS07科学收益未知或旧P0判定。


## 2026-11-01 DS07四臂实现与数据核验；真实TECH因旧额度不足待续

用户授权准备后已安装N/C/S/R模型，CPU合成恒等/配对/概率/梯度检查通过，并修复N臂dropout forward计数；远端现有cue4资产7文件及9划分本次只读重核通过。此为工程证据，无DS07效能数据。原163h/起点继续，余额约−24.6h；未派发真实GPU TECH或科学训练。提出新增28h至191、仅2h技术窗口的方案但未应用；72项真实成本待TECH，不套用PF/ORD吞吐。准备代码、数据/预算记录与明确缺口见[准备报告](ds07-r1/preparation/PREPARATION_REPORT.md)。P0-CUE仍关闭，State与旧Run不变；不能把离线PASS记为TECH通过。


## 2026-11-01 DS-07用户选中并完成设计交接

用户明确选择`IF-20261029-03 / IF-20261029-DS-07 / card-v2`进入设计，已创建[设计交接](ds07-r1/HANDOFF.json)，原卡不改；这更新上一个“尚未选择”快照。P0-CUE谱系仍关闭，原State/163h/起点/旧Run不变。

[DS07-R1方案](ds07-r1/research_brief.md)固定A大核内容读出、B小核QK的2/3/4步回返，无V旁路/无inter，先以N完整原生、C同删inter双内容、S联合自环/行熵/集中度、R回返候选四臂判断系统净效用。拟72完整训练，实际0；仅首阶段通过才考虑36项B去PE训练及144项双来源同P头拟合。明确cue后4秒source6/select1/audit1为已暴露开发资产，不冒称旧trial起点窗口的规范增强baseline。

Grok原判REVISE，主Agent修订全P全局读出、固定A/头拟合边界和判定语义；原报告、trace和[处置](ds07-r1/REVIEW_DISPOSITION.md)保留。最终DESIGN_COMPLETE / PREPARATION_CONDITIONALLY_WORTHWHILE / SCIENCE_INVESTMENT_NOT_READY：值得考虑有界四臂技术/成本准备，当前不投入72科学训练。R对N/C/S均需+.5pp、双seed同向、均值NLL不恶化、逐人−3pp与单seed−5pp风险界；失败停止，不移植P0四锚点、调阶数或改推S。没有已证实的内容/关系互补、位置独立性、新颖性或正式Claim；无实现、前向、TECH、拟合、上传或新Run。


## 2026-11-01 用户收束P0-CUE谱系；Foundry DS-07仅列设计讨论首选

用户明确关闭当前cue4 P0连续优化谱系，覆盖R1/R2/R3、PF/FD/WMP/ORD及未执行SDRO设计；无自动修复、调参或后续训练待办。旧科学判定、历史P0候选及平均结构线索保持，Program已暂停且无活动Run/operation，State和原预算起点保持。[关闭记录](P0_CUE_LINEAGE_CLOSURE_20261101.md)。

对Foundry IF-20261029-03七项及三张card-v2重新核验：推荐DS-07逐token多步回返进入有界设计讨论，DS-03备用，DS-01暂缓，DS-02/05/06不重开，DS-04只作父控制。DS-07有可定位接口和强反证，不代表收益或新颖性通过；须面对自环/熵/相似度、trace、完整P、位置与删inter控制。P0的新负边界不是其直接实验否定。用户尚未选择卡片交接，无新研究身份/handoff/实验；完整取舍见[候选复评](foundry_if20261029_03_review_20261101/ASSESSMENT.md)。

## 2026-10-31 SDRO修订结论：关闭设计实施提案

按用户要求重审固定正则与108项训练价值。复用R2正则支持公平比较，却没有P0-SDRO适用强度的证据；原论文的正则/学习率与选模具有模型数据依赖性，不能搬大λ替代论证。六臂对照可识别结果，但当前干预没有足够的P0特异预测；缩为72项或增加正则搜索都未提供优先于停止的价值。处置从NOT_INVESTMENT_READY更新为DESIGN_CLOSED_INSUFFICIENT_JUSTIFICATION，关闭本SDRO实施/训练提案，无自动TECH/预算待办。配对、I/J、全部逐人风险、四旧锚点与停止条件原文保留；不是实验NO_SIGNAL，不普遍否定Group-DRO或E/A。[修订复评](p0-sdro-r1/REVISION_ASSESSMENT.md)。原163h/起点、State和旧Run不变。

## 2026-10-31 源被试训练适配设计：SDRO配对，尚不具投入资格

按用户设计请求选择源被试Group-DRO作为具体检验工具，保留E/A和R2读出/LS配方，形成P0/AA×ERM/真实组DRO/固定伪组DRO六臂设计（9context×2seed=108完整训练，当前0执行）。用I差中差区分通用改善与结构交互，用J及伪组约束一般重加权；要求P0自身改善、AA不退化、原四锚点与全体逐人风险通过。具体方法、阈值、单seed保护和停止分支见[设计](p0-sdro-r1/EXPERIMENT_PLAN.md)。

Grok独立原判DO_NOT_INVEST：认可配对骨架但质疑固定正则与投入价值；主Agent保留此顾虑，补齐hash/指代/AA退化保护，并澄清“未见对象不可能改善”和重要性估计有偏的过强推断。[处置](p0-sdro-r1/REVIEW_DISPOSITION.md)。最终DESIGN_ONLY / NOT_INVESTMENT_READY，不登记新Run、不启动TECH/训练、不更改原预算或计时，不把方法选择当新结构创新。原连续修复收束保持。

## 2026-10-31 ORD后复评：保留平均结构线索，尚无优先修复实例

新增事后复算仅复用ORD已验收的108份fit/36份select文件，无新前向/拟合/选解或audit重放。固定P修正器18/18格fit目标下降，但select raw NLL及原epsilon=.10平滑损失均仅同两格改善，0格出现raw NLL变差而平滑损失改善；平均分别+0.0226014/+0.0225573。因此“训练与选择损失不一致误拒有用解”不足以解释这批16/18回退。该观察不定位特征/优化/组成原因，也不支持调loss或rho重开旧ORD。fit目标含正则，不能与无正则select损失直接作泛化差距。

取舍仍为收束当前cue4 P0连续净效用修复；R2/FD有限EA相对AA均值收益保留。动态池化、拆共享投影、更多时序/上下文均未被普遍排除，但没有新的P0特异收益依据。若继续讨论，保留“同一种源被试训练约束在P0上能否比AA带来额外、无风险转移的收益”这个条件性问题；它是旧训练适配问题的重审，不是已选算法或新结构创新。最低P0/AA×原/新训练规则的2×2仍不能独自证明被试分组特异机制，当前不选择矩阵或申请预算。State、原163h/起点、旧记录与候选保留决定不变。[完整复评](p0-postord-reassessment-20261031/research_brief.md)、[复算及SHA](p0-postord-reassessment-20261031/EXISTING_SELECTION_RECOMPUTE.json)。

## 2026-10-31 当前结论：ORD-EC完整验收后关闭固定修正实例

`DSAINET-P0-ORD-EC-R1-VERIFIED-ANALYSIS-20261031`：108凸读出fit/108选择/108audit完整，远端全量重新核验、本地373项标准analysis_v1验收、冻结分析器重放和独立预测复算均通过；0新增神经训练。P相对R2 P0-LS只多1/10368个正确预测（+0.009645pp），raw NLL+0.000462；P的18格中16格回退W0，原风险context5/被试索引7仍796/1152，对四旧锚点最差−5.816至−6.944pp。P−C_pi=0pp、P−C_bag=−0.009645pp、P−C_head=+0.221836pp，均未通过原控制门；A/B均失败，处置`NO_SIGNAL_STOP_FIXED_ORD_EC`。

设计后果：关闭当前端点条件化邻接摘要、固定聚合与L1有界线性修正，不调rho/lag/tau/loss/seed/门槛，不改选AA。结合R1–R3/PF/FD/WMP继续收束cue4 P0连续净效用修复；保留原平均结构线索和全部负边界，不把本轮扩张为所有时序或P0结构无效。P−A_P及D仅描述，不证明E/A特异机制。未来须有实质不同、可区分关键竞争解释的新问题后再评估投入，当前不指定或启动新矩阵。

State已关闭当前Run并保持暂停；163h、原2026-10-23T13:28:00+00:00起点、原排队抵扣与4/4旧记录保持。完工时余3.882719h，收尾登记余额−3.431081h，不退款、不增加预算。本轮均为已暴露源开发证据，非独立目标集确认、非正式Claim。[完整报告](p0-ord-ec-r1/closeout_analysis/REPORT_ZH.md)、[标准验收](p0-ord-ec-r1/LOCAL_INTAKE_VERIFICATION.json)、[停止记录](p0-ord-ec-r1/closeout_analysis/DECISION.json)。下方“准备完成、待预算/授权”等段落为当时快照，已由本段更新。


2026-10-30 15:29预算更新：用户已批准追加1小时，累计158小时；原起点、排队记账及历史记录保持。该批准仅为预算，108项科学拟合仍暂停，当前待科学执行授权。[授权回执](p0-ord-ec-r1/preparation/BUDGET_AUTHORIZATION_158.json)。下方157小时为原准备快照。

### 2026-10-30 ORD-EC准备已完成，尚无科学拟合

按用户明确的条件性准备授权，修订P0-ORD-EC-R1并核验复用108份R2/R1原开发预测；rho=.25的逐trial乐观必要上界通过。audit subject7/context5理论最多纠正63个错误，对最严格旧风险门需净增46个，余量17；这不是共享W可实现性或效用证据。36份R2 select-best当前字节/严格载入/归一化/原FD恒等重放绑定通过，六臂各一次TECH完整小求解均收敛；新audit/excluded前向0、108科学拟合0。原157h与起点保留；校准估计含收尾3.0778h，建议未来SCI3.25h/Tx4h，截至15:24原余额3.68325h，提出追加1h至158的预算方案但未登记批准。详见[准备报告](p0-ord-ec-r1/PREPARATION_REPORT.md)。旧研究停止仍保持，当前仅准备完成待科学授权/预算。

### 2026-10-30 用户ORD-EC方案评估补充

用户后续提供的P0-ORD-EC-R1以端点条件化邻接残差、冻结R2 select-best父体和行L1有界线性增量直接组成最终分类器，实质补上旧ORD缺少部署路径的问题。主Agent独立合成复算与源码静态核对通过，一次Grok增量反驳为PROCEED_WITH_REVISIONS：建议继续设计定稿，不直接执行108拟合。固定rho=.25下真实类落后>.5的旧错误不能纠正，需先用合格既有父预测检查乐观上界；尚未取得逐trial预测，未算上界。完整旧四锚点要求audit subject7/context5净增至少46/1152个正确预测，不能把subject7误作context7。具体主张、C门、控制/求解/选择规则与成本仍需冻结；不声称E/A特异或域不变性。见[用户方案评估](p0-postwmp-exploration-20261030/ord_ec_review/ASSESSMENT.md)。这改变了对新设计的讨论优先级，不取消旧P0/WMP/ORD停止、不新建运行候选；State、原预算/起点与历史记录保持。

## 2026-10-30：WMP后探索的当前取舍

已完成WMP Stage A后对10项行动的多视角构思和一次独立Grok科研反驳，当前仍**维持cue4 P0连续净效用修复的实验收束**。WMP是共享8相位固定模板非退化门失败（EA双seed context 0/9），不是分类负结果，也不证明所有动态/顺序信息不存在；旧Stage B不恢复。早先本文中WMP“待定/未执行”段仅是历史快照。

实质不同的“块内邻接关系摘要”保留为未采纳假设P0-ORD-D1：给定H的E/A对块内置换不变，但H已过时间卷积，P0仍有尺度卷积/intra/token attention，因此不能据摘要压缩推断网络缺时序信息。初稿粗糙度残差仍有幅值/平滑/端点与读出控制问题，且正probe尚无唯一原生结构和风险修复路径；不执行所讨论的180probe，不改强度/lag挽救。31token线性差分在保留原U的线性probe下不增加无约束函数类，无需再跑一轮“信息增量”。

现有证据可识别性表已完成：固定读出作用已被FD隔离，训练来源仍混合初始化/优化/选模，context仍混合被试与fit/select组成，不能把风险迁移直接归为统计量/梯度冲突。原生DSAINet尺度/inter仅保留为未来具体问题入口，未选干预、未新建执行。直接报告与source IDs、全部候选、近邻核对、审查原判及主Agent对审计角色混淆等意见的处置见[WMP后研究brief](p0-postwmp-exploration-20261030/research_brief.md)。State、预算、时钟及全部历史判定不变；不释放Claim。

## 基模来源与认识边界

同一论文的加工材料不作独立证据计数。路径从本文件位置解析：

| 材料 | 用途 |
|---|---|
| [DSAINet-paper.md](../../../../refs/paper-cards/dsainet/DSAINet-paper.md) | 原文读取材料 |
| [DSAINet-paper-card.md](../../../../refs/paper-cards/dsainet/DSAINet-paper-card.md) | 贡献与证据边界 |
| [DSAINet-paper-xray.md](../../../../refs/paper-cards/dsainet/DSAINet-paper-xray.md) | 设计推演 |
| [DSAINet-note.md](../../../../refs/paper-cards/dsainet/DSAINet-note.md) | 综合理解 |

### 基模设计理解

作者报告：DSAINet 先将 EEG 压成 token，再以不同时间感受野构造双尺度分支，分支内 self-attention 后用 cross-attention 交换信息并聚合分类（X-Ray §2–5；Note §3–4）。阅读解释：小/大卷积核改变时间上下文，不自动等于不同生理功能；架构在多个任务分别训练可复用，不代表一套权重跨任务迁移。当前本地代码和 P0 定义须查具体实现，如 `src/models/diagnostics/sccd_dsainet.py` 与对应候选源码；结构名称本身不证明 E/A 互补。作者报告的基准表现不能替代本 Program 协议结果。

### 当前综合、反例与未决问题

2026-10-29追加讨论：用户提出借鉴TAPL/TAUD/SFTA与SCCD的局部非均匀汇聚，形成[P0-WMP-D1条件诊断设计](p0-wmp-d1/research_brief.md)，仍为DESIGN_ONLY、无实验。源码确认旧研究操作后端31-token，而拟议改动是前端Avg8块内相位；P0仍有intra/token attention，正权重覆盖不等于完整上下文保持。拟先核验36份R2的固定epoch100 final_model并做fit-only干预非退化检查，再有条件考虑最多396个线性读出；AA去重、七错位及原U尺度用于约束容量/正则混淆。正诊断也不打开训练资格，原连续优化投入收束仍保持。Grok原判REVISE及主Agent修订见[审查处置](p0-wmp-d1/review/REVIEW_DISPOSITION.md)，不记已证实收益或外审PASS。

截至2026-10-29，FD-R1已完成36份R2原检查点恒等回退与144格交叉读出，0新训练，标准analysis_v1通过；固定R2权重改概率读出仍为−0.9452pp，原父体保留与同读出AA门均失败。结合R1–R3/PF，本轮决定收束当前cue4 P0连续净效用优化，不推荐下一轮结构、loss或融合修复。E/A局部相对收益与历史冻结候选保留，不普遍否定P0、双尺度或交互家族。见[FD结果](p0-fd-r1/RESULTS_ZH.md)及[累计投入复评](p0-cumulative-review/research_brief.md)。PF仍是原产物关键交付复验、standard_analysis_v1_intake=false；R3的FAILED恢复复验及所有原冻结判定不改。

新增事后整理：固定同一种读出时，E/A−AA的平均间距在R2→PF间只变化−0.0868pp（G）/+0.0772pp（P）；原PF的I=−0.5787pp混合了读出与训练来源，不能单独解释为PF训练特异性破坏平均结构收益。但索引6的E/A相对AA额外变化为−12.1528/−11.8924pp，风险迁移并未因控制读出而消失。均值点估计接近零不证明等效，训练来源仍混合初始化、优化与选模，audit被试也绑定不同fit/select组合。没有唯一机制归因，不能按已见索引设计门控。直接依据为[原FD汇总](p0-fd-r1/RESULTS.json)与[可复算代数整理](p0-cumulative-review/CROSSED_SUMMARY.json)。

下文区分作者报告、阅读推断、当前实现和本地筛查；适用条件、依据和改变判断的证据随判断记录。不同窗口/协议的结果不可混用。历史运行和候选处置回链原报告，动态状态仅以 STATE.yaml 为准；新筛查不会改判冻结负结果，也不会把架构结构直接升级为互补机制证据。

### 历史记录索引（以下保留当时快照）

2026-10-29 初始设计快照曾将 P0-PF-R1 记为未执行；该描述已被上方实际收尾报告取代。以下轮次材料保留为历史证据，不能当作当前状态。

## 拟议主张与当前选择

当前选择为收束BNCI2014001 cue4 P0连续优化，不登记下一候选或训练矩阵。已有证据可形成范围明确的设计经验：同统计/单支比较的有限均值优势不能替代匹配父体保留、NLL和逐人风险。它尚不足以支撑可靠泛化或纯梯度机制的论文主张，局部负结果本身也不自动构成独立贡献。FD原[设计稿](p0-fd-r1/research_brief.md)保留当时状态；当前取舍与竞争解释以[累计复评](p0-cumulative-review/research_brief.md)为准。

WMP-D1是用户新问题下的待定源侧诊断草案，不是重新激活P0训练候选。其最近可证伪问题是“单一8相位模板是否构成非退化且超过简单控制的可读增量”，并非已找到P0风险来源；没有提出或授予完整网络训练矩阵。

## 关键缺口

固定R2读出这个最小缺口已经补齐并关闭，不能继续当成待办。尚未区分训练目标、初始化、共享前端/优化轨迹、select选模与对象异质性；这些未知目前没有指定一个优先修复方向。未来若出现实质不同且可证伪的新机制设计、能区分强替代解释的简单控制及合理成本，可重新评估；不要求先另做一轮缺陷诊断，也不因尚未试过某loss而继续投入。原风险标准和证据边界保留，以下均为历史来源。

## 历史认识与当时设计（原文保留）

### P0-PF-R1已完成实施与真实五臂TECH，尚待追加数值预算

2026-10-29用户授权按方案实施后，旧90格来源重新核验，五臂模型CPU数值检查及Lab10原环境每臂8batch资格+5epoch均完成。原工程包收尾缺json导入而FAILED，五份训练成功产物保留；独立只读恢复消费者在原环境复验PASS，无重训。该证据只属于工程资格与成本，不支持P0结构或净效用判断。完整进程固定开销、首epoch、稳态epoch与并发分开核算，科学90fit/90audit按无并发折扣的1.5余量为22.166h；拟SCI23h、Transaction27h含4h收尾，拟总额144h仍待用户批准。原140h、原起点、R1–R3和本次FAILED原记录均保留。科学入口、115项依赖闭包和真实产物接口验收完成，独立Grok复核READY_FOR_NUMERIC_APPROVAL；科学训练尚未登记或启动。见[p0-pf-r1实施报告](p0-pf-r1/IMPLEMENTATION_REPORT.md)与[科学准备状态](p0-pf-r1/SCIENTIFIC_READINESS.json)。

### R3未修复整体风险；PF仅作为用户新提出的一次融合设计

`DSAINET-P0-CUE-R3-CVAR-RECOVERED-ANALYSIS-20261028`，[独立收尾复验](p0-cue-r3-cvar/closeout/REPORT.md)：18fit/18audit已有产物验收与远端/本地复算一致，CVAR较父P0-LS ACC−1.8133pp、raw NLL+0.029740、最差逐人−15.9722pp；四风险门与父保留门失败。原Run FAILED保留，standard_verified_intake=false；它是恢复的暴露开发证据，不是标准成功intake。旧风险被试7改善而索引6大幅退步，说明不能靠修好一个旧差点宣称整体成功。设计后果：不沿用CVAR、不以其低分作新主基线；原STOP_CUE4_CONTINUOUS_TUNING仍有效。

2026-10-29用户要求规划[P0-PF-R1](p0-pf-r1/research_brief.md)，这是停止之后明确提出的新设计请求，尚不授权实验。源码核对确认R2的E/A-DIRECT是一次拼接dropout后线性头，S0为A/A-DIRECT；可定义共享bias、固定系数2的两支logits，使几何融合恢复旧头、算术概率平均成为唯一变化。拟90fit/90audit，唯一候选配AA-PF/EE-PF及真正独立训练的两单支；保留旧四锚点与父保留门，再检验非对称优势、独立单支和双向贡献。概率平均与联合集成均是已有方法，不能预设解决风险，差中差仅作受限交互线索。旧预算不自动可用，不自动训练、调温度、融合权重或追加辅助损失。

### 错误预测上的损失增加支持一次固定训练适配检验，原因仍未确定

2026-10-24对R1已核验54个预测NPZ作[只读损失分解](p0-cue-r2/diagnostics/P0_RAW_NLL_DIAGNOSTIC.md)，没有新拟合、forward或温度校准。P0错误预测的平均NLL为2.9089，高于B0的2.6332和S0的2.3114；错误top1置信度为69.05%，亦较高；正确时NLL则更低。P0−B0双方都错的条目贡献+0.108284 NLL，P0−S0对应+0.234298；所有贡献使用固定全分母并精确加和。条件集合不同和表示共同适应限制因果解释，不能说已证明是E幅度或过度自信造成失败。

设计后果：提出[固定ε=0.10标签平滑的R2](p0-cue-r2/research_brief.md)，保持P0结构，B0/S0同步给予同配方，select/audit仍用硬标签raw NLL；保留原对照门，并要求优于同配方控制。只在身份资格成立时显式引用R1的CE格，新训LS格54次。该设计由已见开发结果驱动，不能称独立确认；R1 NO_SIGNAL、旧72h原计时起点及关闭状态不变。当前仅设计，不授予后继Run或自动调参。

### P0-CUE-R1有平均准确率收益，但冻结净效用门失败

`AI4S-DSAINET-p0-cue-r1-costcal-r1`，完整1141文件manifest核验与intake、54fit/54audit闭集及独立NPZ重算已完成。P0 ACC51.6590%，B0为50.3665%、S0为48.1964%。P0−B0 +1.2924pp，P0−S0 +3.4626pp，两seed方向均正；但raw NLL分别增加0.070359/0.152371，最差受试者平均差−3.4722/−3.5590pp，均触发原非劣/风险门，登记NO_SIGNAL。设计后果：停止精确P0-CUE-R1，不用追加seed、温度缩放、checkpoint改选或删不利被试补救，不自动搜索第二模块。该负边界不否认所有P0变体、所有能量统计或分支机制。当前无活动Run，72h、原起点和历史成本保留。详见[完整结果](p0-cue-r1-costcal-r1/analysis/RESULTS_ZH.md)。


### P0有方向性开发信号，但AEL整体假设未成立

`AI4S-DSAINET-dsa-ael-v0.1-repair2`，`dsa-ael-v0.1-repair2/analysis/ANALYSIS.md`：P0−B0为+1.554609 pp，P0−AA-DIRECT为+1.081124 pp，P0−EE-DIRECT为+1.625631 pp，三项原门通过；反向C0未满足全部原门，整体仍是NO_SIGNAL。适用范围仅为当时两seed、九个源内开发划分，不是独立目标被试确认。设计后果：保留定向P0，不再要求把反向也包装成成功，不把历史对照收益搬到新协议。

精确身份为 `DSA-AEL-P0-FROZEN-20260927`；`P0_FROZEN_PERFORMANCE_CANDIDATE.json` 冻结全部18个旧checkpoint。E=log1p(Avg8(H²))、A=Avg8(ELU(H))，H为第二patch BN后、最终ELU前；E不是中心化方差，A也不是原始H均值。未来实例保留这个数学定义，不改旧候选文件。

### 现有证据不能把P0写成双支必要性或Coarse特异机制

`AI4S-DSAINET-dsa-bsu-v0.1-repair3` 及其 decision/brief：CE、CA、FA、FE单支已从头训练，双支保留门未全部成立；不同容量/训练路径仍限制解释，未过优效门不证明单支等效。`AI4S-DSAINET-dsa-ces-v0.1-repair3` 比较E与均值平方M，不支持预定Coarse特异诊断。设计后果：不重复单支筛查、E对M或换名机制救援；新三臂只回答候选整体价值，不能证明早期统计分工替代后期交互。

### NRC1的局部收益不足以支持继续开发该双上下文包

`dsainet-nrc1-repair3-complete-20261023`，`dsa-nrc-v0.1/execution/recovery_audit3_96/RESULTS_ZH.md`：来源brief明确是已暴露source开发数据。完整验收后GL−B为+0.9066 pp，低于原1pp门；同功能/宽单支及移除对照没有建立有效互补。保留原生路径精确回退和有限改善，关闭该精确包，不调rho、width、seed或改选LL。预算收尾超限记录不抹去，产物完整性与预算合规分开。此认识使新投入从增加分支/修正器转向已有P0候选；它不证明所有双分支机制无效。

### 当前窗口与划分不同，已有结果不能直接复用为新对照

`dsa-rcd-v0.1/research_brief.md` 第5节、`dsa-lcb-v0.1-LC1.yaml` 的comparison_key、旧预处理脚本直接定义：旧trial-start裁剪与cue后裁剪有500采样点偏移。当前资产 `BNCI2014001_rcd_cue4_v1` 使用连续run 0.5–40Hz后取cue[0,4)，LC1/NRC1使用被试隔离开发划分。设计后果：P0-CUE-R1直接复用当前合法数据与split身份，所有三臂按同新配置训练；不拿旧P0/B0指标拼表，也不声称比较隔离了“窗口变化”这一单因果因素。

### 原创性与历史关闭边界

FBCNet已有方差聚合；DSAINet已有双尺度intra/inter；EEGNeX已有纯卷积简化路线。2026-10-23核对作者论文： [FBCNet](https://arxiv.org/abs/2104.01233)、[DSAINet](https://arxiv.org/abs/2604.18095)、[EEGNeX](https://arxiv.org/abs/2207.12369)。这些近邻限制新颖性表述，不提供本项目效用证据。当前未发现足够依据优先投入新的统计重写、动态核或残差分支；这是本轮取舍，不是穷尽搜索或断言再无好方向。

历史评价与用户关闭指令只用于保持既有候选/主张边界，见 `P0_CANDIDATE_RETENTION_20261010.md`。本轮主agent从记忆和该保留记录已见部分最终评价摘要，因此不能声称选择过程未暴露；不把这些效果用于窗口、模型、seed或门槛选择，不将任何后继称作未接触的确认。此总览有意不转录最终评价分数。

R1已收尾。2026-10-28，原[P0-CUE-R2研究设计](p0-cue-r2/research_brief.md)已完成固定LS ε=0.10训练适配与匹配对照；以下是原设计执行后的证据更新，不恢复R1或自动进入第二模块搜索。

### P0-CUE-R2改善平均NLL，但逐被试风险和同配方seed门仍未通过

`AI4S-DSAINET-p0-cue-r2-recover53`：原53项成功训练经来源核验复用，仅补B0_s0_t7，54fit成功屏障和54audit通过；旧失败、原回执/checkpoint身份与字节保留。正式完整intake、远端CPU分析、独立Numpy/Fraction复算以及关键证据包复算均完成。P0-LS ACC55.5941%、raw NLL1.199346，相对旧P0-CE平均ACC +3.9352pp、NLL −0.327558；但四项原比较（B0-CE/S0-CE/B0-LS/S0-LS）在被试索引7的两seed均值均低于−3pp，P0-LS vs S0-LS还有seed0 −0.057870pp。原四比较规则登记NO_SIGNAL，关闭该固定ε=0.10实例，不补seed、改阈值/ε/temperature/epoch或删被试挽救。

设计约束：平均NLL缺口得到改善并不等于跨被试净效用成立；S0的同配方ACC增益+5.7292pp大于P0的+3.9352pp，P0相对S0差中差为−1.7940pp，不能将一般训练适配收益归因为P0结构必要性。该结果只限制当前已暴露开发协议和固定实例，不否定所有正则化/P0变体。State现为COMPLETE_MAX_ROUNDS、无活动Run，140h总预算与原起点保留，不自动开启下一轮。详见[远端分析报告](p0-cue-r2-recover53/analysis_remote/RESULTS_ZH.md)和[关键证据包](p0-cue-r2-recover53/analysis_remote/KEY_EVIDENCE.zip)。

### P0仅值得一次有界的局部中心化检验，不进入连续模块搜索

2026-10-28设计判断，非新实验结果。综合AEL/BSU/CES及R1/R2，尚有一个实质不同、可低成本辨别的问题：原Coarse摘要为log1p(v+μ²)，改为同8点局部窗口的log1p(v)能否满足原风险限值并保留父模型均值。CES比较E与M，并未直接检验该中心化替换；原BN也不保证每窗口均值为零。现有证据没有证明被试7损失由局部均值漂移引起，中心化还可能丢失判别信息；不能把假设写成诊断结论或把V叫尺度归一化。

设计后果：唯一CVAR候选沿固定LS=.10及原数据/选模，拟18次100epoch新fit+18audit，资格成立才引用R1/R2的90格对照。保留四锚点原ACC/NLL/seed/逐人门，再要求相对P0-LS平均ACC不降、NLL不升、逐人差不低于−3pp。通过只暂留开发候选；失败停止当前cue4谱系连续调参，不自动调窗口、强度、loss、增加seed或恢复门控。Group-DRO等暂缓，以免再次主要获得一般训练收益。方差聚合已有[FBCNet](https://arxiv.org/abs/2104.01233)、[varEEGNet](https://eusipco2025.org/wp-content/uploads/pdfs/0001477.pdf)及近期统计池化近邻，单点替换不足以成立主创新。具体方法、前瞻规则、原预算与仅设计边界见[唯一brief](p0-cue-r3-cvar/research_brief.md)，源码/历史结果绑定见[SOURCE_BINDING.json](p0-cue-r3-cvar/SOURCE_BINDING.json)。


## DSAINET-P0-PF-R1-PACKFIX1-SCIENCE-START-20261029

2026-10-29：P0-PF-R1 packfix1已在Lab10启动科学训练；旧90格复用、五臂原TECH、source及成本门PASS。快照5运行/85待调度/0完成/0失败，审计未开始，90fit成功封存后90audit。累计157h、原2026-10-23 21:28+08起点、SCI23h/Tx27h含4h收尾保留。原science1因proof依赖遗漏工程INVALID、0科学拟合，原Run/包/2.808s成本及R1-R3/TECH记录保留。仅为执行证据，无中间效果判断或Claim。详见p0-pf-r1/PACKFIX1_LAUNCH_REPORT.md及Program State/Evidence Index。


## DSAINET-P0-PF-R1-PACKFIX1-SCIENCE-START-20261029 / 2026-10-29T08:04:05.085232+00:00

P0-PF-R1 packfix1已在Lab10启动科学训练；旧90格复用、五臂原TECH、source及成本门PASS。快照30运行/55待调度/5完成/0失败，审计未开始，90fit成功封存后90audit。累计157h、原2026-10-23 21:28+08起点、SCI23h/Tx27h含4h收尾保留。原science1因proof依赖遗漏工程INVALID、0科学拟合，原Run/包/2.808s成本及R1-R3/TECH记录保留。仅为执行证据，无中间效果判断或Claim。详见p0-pf-r1/PACKFIX1_LAUNCH_REPORT.md及Program State/Evidence Index。


## DSAINET-P0-PF-R1-PACKFIX1-REVALIDATED-ANALYSIS-20261029

P0-PF-R1 packfix1已完成90fit/90audit（0失败），远端全量2008项及本地682项关键文件核验，原分析器与独立NumPy复算一致。冻结判断G1失败、G2/G3通过、I=-0.5787pp，NO_SIGNAL_STOP_PF_R1；P ACC54.8997%、raw NLL1.223481，相对R2父体-0.6944pp、NLL+0.024135、最差逐人-14.6701pp。G2/G3仅支持本开发实例有限结构/联合预测线索，不能替代净效用门。原合同FIT_BARRIER缺项及checkpoint超限保留，本次为独立关键交付复验，非标准analysis_v1 intake；原Run COMPLETE与R1–R3记录不改。Grok外审无交付阻断，覆盖和限制见analysis_closeout/review。State关闭当前Run并暂停，轮数4/4；157h与原起点保持，无新实验或正式Claim。登记余额23.153h（2026-10-29T11:56:23.546781+00:00快照，不返还人工等待或暂停时间）。详见ai4s/programs/dsainet/research/p0-pf-r1/analysis_closeout/REPORT_ZH.md。





## P0-FD-R1 固定检查点证据更新

P0-FD-R1已完成36份R2原检查点复用和恒等回退、TECH/成本门及144格交叉读出分析，标准analysis_v1验收通过，0新训练。R2固定E/A权重概率−几何：ACC-0.945216pp、NLL-0.008528、最差逐人-2.951389pp；相同概率读出E/A−A/A为+1.012731pp。冻结处置NO_SIGNAL_STOP_FIXED_READOUT_REPAIR。训练来源差异仍含优化/初始化/选模，不作纯梯度因果解释。两个工程失败原件及全部R1–R3/PF记录保留；157h原预算、起点及原4/4科学轮记录未变。无自动后续实验或Claim。详见ai4s/programs/dsainet/research/p0-fd-r1/RESULTS_ZH.md。


## DSAINET-P0-WMP-D1-STAGE-A-LAUNCH-20261029

用户已明确批准冻结载荷上传至Lab10指定新目录并启动2026-10-29_dsainet_p0_wmp_d1_stagea-full-w1。包上传与逐文件SHA核验完成，已启动CPU串行双线程诊断；本次状态快照：复用节点PASS, TECH RUNNING, 科学格0/36。首阶段0次神经训练、0次线性探针；实际资格、TECH和成本门通过后才进入全部36格source-fit非退化分析。原157小时、2026-10-23T13:28:00+00:00计时起点、旧4/4训练轮及R1–R3/PF/FD全部记录保留；首阶段Transaction上限2小时、科学节点1小时。跳板超时后按现有规则使用同一Lab10的lab-codex直连，未换Run或环境。合成接口已验证完整/精简analysis_v1一致，限定外审只覆盖源隔离和矩计算；均非科学结果。本阶段结果不足6/9双seed配对context达到冻结干预线则停止此固定模板；不调强度、不自动神经训练。活动诊断由独立用户授权operation记录，不把旧通用部署NOT_READY改为PASS。详情见ai4s/programs/dsainet/research/p0-wmp-d1/EXECUTION_NOTE.md。


## DSAINET-P0-WMP-D1-STAGE-A-COMPLETE-20261029

2026-10-29_dsainet_p0_wmp_d1_stagea-full-w1已完成36/36原R2 epoch100 final_model资格、实际TECH/成本门及36/36 source-fit非退化诊断；标准analysis_v1回拉核验与独立局部复算通过。双seed同时非退化的E/A context为0/9，冻结要求至少6/9；处置NO_SIGNAL_STOP_FIXED_PHASE_TEMPLATE。0次神经训练、0次线性探针，0次select/audit/excluded前向。这只检验此固定八相位模板能否形成足够干预，不是模型准确率、校准或被试伤害的改善证据，也不否定所有池化方法或P0结构。下一动作：STOP_WMP_D1_NO_PROBES。保留原157小时与原计时起点及全部旧结果；关闭时预算余额18.803小时。报告：ai4s/programs/dsainet/research/p0-wmp-d1/stagea_analysis_local/REPORT_ZH.md。

### DS07-R1工程 Run 已派发，仍在等待资源

2026-11-01 用户授权累计预算202小时并只暂停本次申请至确认之间的115.93227秒人工等待；沿用`2026-10-23T13:28:00+00:00`原起点，确认时恢复计时。冻结包通过34项本地文件闭包后上传至授权Lab10目录，Run `2026-11-01_dsainet_ds07_r1_tech1` 已启动，PID 706689。派发门PASS时余额3.23744小时，固定工程Transaction预留2小时；探针显示driver处于资源等待，尚为TECH 0/4、science 0、audit 0。独立远端验收和72项科学矩阵成本核算仍待完成，预算门PASS不构成TECH或科学PASS；当前不授权科学训练。详见[授权与派发报告](ds07-r1/preparation/AUTHORIZATION202_LAUNCH_REPORT.md)。

### DS07-R1 packfix1 派发通过，仍等待N臂资源

在原repair1授权父目录内派发了immutable child `2026-11-01_dsainet_ds07_r1_tech1-repair1-packfix1`；累计预算212小时，原起点保持。两笔获准人工等待暂停合计404.224145秒。已核实资源等待总额32898.10485秒，其中此前累计31055.86243秒，另1842.24242秒来自最初`2026-11-01_dsainet_ds07_r1_tech1` Run；repair1旧Run在queue前退出，贡献0秒资源等待、0训练且原记录保留。packfix1通过timezone与目录守卫修复、本地17项回归、39项源SHA闭包、真实预算消费者及启动到容量等待阶段。最近探针显示driver和postprocess均存活，等待N臂资源；预算余额2.91848小时、0/4 TECH开始、science 0、audit 0。独立远端验收与72项矩阵成本仍待完成；上述工程PASS不构成TECH或科学PASS。资源等待来源由原tech1队列证据核验；本次preflight intake只证明工程启动接口。详见[packfix1派发报告](ds07-r1/repair1/LAUNCH_REPORT212.md)。


## DS07-R1 packfix1 状态更新（2026-11-02）

四臂真实资格8batch及5epoch均完成、退出码全0。全局TECH收尾因N进程显存尾部覆盖16.47秒超过冻结10秒而失败；C/S/R遥测完整。后台已退出，科学训练0；20份关键证据SHA和4份SELECT replay NLL独立核验通过，但不构成正式TECH PASS。72项临时SCI成本约30.91h、SCI31h/Tx35h仅作规划，尚无派发资格。212h原起点、两笔人工暂停和原记录保留，当前预算为负，未追加预算或重训。详见[状态核验与成本](ds07-r1/repair1/STATUS_REPORT_20261102.md)。


## DS07-R1 合并四臂净效用筛查收束 / 2026-11-05

72份devicefix1拟合、54份N/C/S审计与R18的18份R审计及无拟合诊断完成合并验收，保留父Run工程FAILED与补跑PASS的混合来源。R ACC49.5949%、raw NLL1.408873；R−N/C/S分别−0.4147/−1.7458/−1.1285pp，三项必要比较均失败，逐人风险越界。冻结处置STOP_FIXED_DS07_R1_NO_AUTOMATIC_EXPANSION：停止固定实例及条件性PE/同P阶段，不改推C/S，不启动新实验。C虽均值最高，相对N最差人−9.2882pp。R干预只有有限select敏感性，不证明拓扑/PE/压缩因果或目标效用。9人重复暴露开发证据，不作独立泛化；不否定所有关系读出，P0-CUE保持关闭。312小时原预算、起点和全部账本保留，无新增暂停或额度。详见[合并分析报告](ds07-r1/analysis_20261105/REPORT_ZH.md)及State/Evidence Index。
