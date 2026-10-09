# BRIEF-R01 v2｜存量 Java 系统 → 业务资产逆向 + 客户确认：公开生态工具与方案盘点

- **任务**：TSK-46（S1-2）｜**产出路径**：`research/tool-survey.md`｜**版本**：**v3.2（patch-01 四项修订 + patch-02 三项增量补齐 + patch-03 四处计数/行序校正 + patch-04 六处计数/版本标签/矛盾表述校正；调研内容、结论、置信度、缺口、候选判定零变更）**
- **AC 基线**：**TSK-45 v4（frozen，2026-10-08 10:39 冻结）**｜对齐全部 **10 条 AC**（AC-01～AC-10）
- **作者**：研究员 Researcher｜**评审**：架构师（可用地面是否够用）／协调智能体
- **数据快照日期**：2026-10-08（所有 star 数、许可证、最后推送时间、归档状态均取自当日 GitHub REST API，复现方法见 §13）
- **性质**：只盘点证据，**不出选型结论**。"用哪个 / 实施顺序怎么排 / 工期多少"留给 R2（架构师）与 R1（产品经理）。

### v3 变更摘要（patch-02 三项增量补齐 + v4 基线对齐）

| patch-02 项 | 要求 | 本版落点 |
|---|---|---|
| **1** 五类业务资产标注（AC-03） | 每条候选增加「可输出业务资产类型」多选字段 | **v2 已完成**（§5 各表第 11 列 + §7 矩阵）；v3 复核取值域与 v4 术语一致，**无改动** |
| **2** 客户确认实践章节（AC-05/AC-07） | 覆盖资产/模型差异对比、评审记录、差异项处置（含第三态）；**两种确认范围并列**；不做推荐 | **v2 已建骨架**（§5-H 12 条候选 + §6.3 P-01～P-06 + §9 全节）；**v3 按 v4 校准**：① 第三态术语由「标记未决」改为 **「标记后续人工处理」**（全文 13 处）② 新增**确认对象 = 关键业务流程**（客户人工判断的重点交易与重点场景，**研究方不预设界定标准**）③ §9.1 两类范围仍如实并列，但**删除 v2 中"建议候选口径"的预设判据**，改为「客户人工判断时可参考的公开素材」④ AC-07 判定口径按 v4 改为「无**未标注处置**的差异项」（允许存在后续人工处理项） |
| **3** 切片输入能力标注 | 每条候选补一句「能否将输入限定到客户指定的流程/场景集合」，推断项标「推断」 | **v3 新增第 12 列**，覆盖 **86 条**（主表 70 + 次级 16），逐条给出 可／部分／不适用 + 依据 + **推断／直证** 标记；汇总见 **§9.6** |
| **基线切换** | 验收依据更新为 v4 AC（10 条） | §1 目标表述改为 v4 AC-02 的唯一目标句式；§1.1 输入前提补「关键业务流程」术语；§14.2.1 的 Q-x1/Q-x2 **已由 CHANGE-03 闭环并记录答复**；**§17.1 扩为 v4 全 10 条 AC 自检**（含 AC-02/AC-06/AC-07，并如实说明本卡能直接满足哪几条、哪几条只能提供地面） |

### v2 变更摘要（patch-01 四项修订的落点）

| 修订 | 要求 | 本版落点 |
|---|---|---|
| **修订 1** | 撤销「是否可作为正向生成输入」字段；正向代码生成移出范围（NG-07） | **未新增任何正向生成字段**；全文无正向代码生成工具推荐或集成方案（AC-10）。候选字段维持「输入要求」+「反推能力评级（直接／间接／需二开）」。v1 亦无该字段，故为**零变更确认** |
| **修订 2** | 五类业务资产口径；每条候选标注「可输出业务资产类型」（多选） | §5 全部候选表新增**第 11 列**「可输出业务资产类型」（流程／规则／概念／数据／接口，多选）；§7 给出**五类资产 × 逆向输入**矩阵并验证五类均可被覆盖（AC-03） |
| **修订 3** | 实施流程类候选需覆盖「与客户确认业务流程」的既有实践／案例（主体＝客户业务专家，形式＝差异清单＋评审会，含三态处置） | 新增 **H 类：客户确认与差异管理（12 条候选）**；新增 **§6.3 实施流程类（P-01～P-06，6 条）**；新增 **§9 客户确认实践**（含差异清单三条生成路径、评审会标准依据、三态处置载体、AC-05 自检） |
| **修订 4** | 规模前提落实为约 20 模块／约 50 微服务／约 20 万行 Java、金融语境；原「中型口径待回源」解除 | 新增 **§8 规模适用性评估**（K-1～K-3 三条硬约束 + 逐类适用性 + 新增缺口 G-10/G-11）；§1 输入前提改为 v3 冻结口径；§14.1 记录该项**已关闭** |
| **未决事项** | ① 全量确认 vs 关键流程确认；② 「准确」达标口径 —— 勿自行猜测 | §9.1 以 **S-A／S-B 两类策略并列**呈现，各附既有实践支撑，均标 **「待 xiao 确认」**；§14.2 Q1/Q2 保持开放，未替 xiao 作答 |

---

## 1. 研究问题与决策用途（一句话）

**研究目标（v4 AC-02 唯一目标句式，全文不含正向代码生成类目标）**：**Java 工程 → 逆向解析成业务资产 → 客户方业务专家确认关键业务流程（差异清单 + 评审会）**。

本报告为该目标服务的具体决策问题是：为「**已持有源码**的存量金融 Java 系统，在重构启动前**逆向解析成五类业务资产、并由客户方业务专家确认关键业务流程**」，盘清 GitHub 公开生态（辅以官方文档／标准／论文／商业厂商公开资料）中可用的技术地面——哪些工具与实践能把源码／字节码／日志／数据库结构变成**五类业务资产**证据、各自能回答什么问题、缺什么、许可证与合规风险如何——形成带证据的候选清单，供架构师收敛方案。

### 1.1 输入前提（TSK-45 v4 frozen 口径，对应 AC-01）

| 前提项 | v4 frozen 口径 |
|---|---|
| ① 语言与技术栈 | 存量 **Java** 系统，**已取得源码**（NG-02：不处理无源码／黑盒场景） |
| ② 规模 | 约 **20 个模块** / 约 **50 个微服务** / 总代码量约 **20 万行**（原「中型口径待回源」项**已解除**，本版按此口径评估，见 §8） |
| ③ 技术／业务特征 | 技术成熟、架构规范、**业务复杂** |
| ④ 领域语境 | **金融软件**（子领域细分——银行核心／保险／证券／支付——原文未指定，仍 **待回源**） |
| ⑤ 目标闭环 | Java 工程 → **逆向解析成业务资产**（业务流程／业务规则／领域概念／数据资产／接口）→ **客户方业务专家确认关键业务流程**（差异清单 + 评审会） |
| ⑦ 关键术语（v4 §二） | **关键业务流程** = 由**客户方人工判断**的「重点交易与重点场景」，**研究方不预设界定标准**；**清晰** = 每条关键业务流程以统一结构描述（触发条件／参与模块／数据实体／业务规则／异常分支，≥5 字段）并标注源码证据位置；**准确** = 经客户业务专家以差异清单 + 评审会确认，评审会结论为「通过」或「有条件通过」，差异清单未决项以**「后续人工处理」**标记收口 |
| ⑥ 范围外 | **NG-07：正向代码生成不在本研究范围**（由其他工具实现）；本研究只到「确认逆向出的业务流程**清晰、准确**」 |

- **为谁**：R2（判断可用地面够不够、缺口在哪、需自建多少）、R1（判断可承诺的交付形态与 AC）、客户方业务专家（确认环节的参与者）
- **答案用来做什么决策**：R2 在「组合式自建 / 商业平台采购 / LLM agent 流水线」三条路线间做技术裁决
- **做到什么程度算够**：≥6 类别、≥15 候选、字段齐全、URL 可访问且指向项目本身、许可证与活跃度有来源、缺口有明确结论；**v2 追加**：五类业务资产均可被覆盖（AC-03）、三类产物各 ≥3 条（AC-04）、客户确认环节三要素齐全（AC-05）

---

## 2. 研究计划表

| # | 子课题 | 并行/串行 | 主要检索源 | 状态 |
|---|---|---|---|---|
| S1 | 流程挖掘 / 事件日志阵营盘点 | 并行 | GitHub Repos+Search API、pm4py 官方文档站、apromore.com、CRAN | ✅ 完成 |
| S2 | Java 静态分析与程序结构恢复 | 并行 | GitHub API、soot-oss.github.io、jQAssistant/ArchGuard 官方文档 | ✅ 完成 |
| S3 | 调用图 / 数据流 / 污点分析 | 并行 | GitHub API、docs.joern.io、Tai-e 文档站、FlowDroid 仓库 | ✅ 完成 |
| S4 | 领域模型与业务概念恢复（DDD） | 并行 | GitHub API、docs.spring.io、structurizr 文档、edmcouncil.org | ✅ 完成 |
| S5 | LLM 辅助代码理解 / agent 化流水线 | 并行 | GitHub API、各项目 README/docs/Discussions | ✅ 完成 |
| S6 | DB / 配置 / 工作流引擎驱动的流程还原 | 并行 | GitHub API、camunda/flowable/drools/liteflow 官方文档 | ✅ 完成 |
| S7 | 遗留系统逆向方法论与案例（金融优先） | 串行（依赖 S1–S6 界定方法论缺口） | awesome-* 清单、Springer/IEEE/PMC/ProQuest 论文、厂商公开案例页 | ✅ 完成 |
| S8 | 许可证 / 活跃度回源核验与证据分级 | 串行（依赖 S1–S7 候选清单） | GitHub Repos API（`license.spdx_id`、`pushed_at`、`archived`）+ 官方许可页 | ✅ 完成 |

---

## 3. 结论摘要（附置信度）

> 证据等级：**A** = 一手来源直证（官方仓库 / 官方文档 / 源码 / API 原始返回 / 可复现实验）；**B** = 权威二手（行业媒体、厂商博客、论文摘要、他人转述）；**C** = 推测 / 单一来源 / 无法验证，仅作线索。

| # | 结论 | 置信度 | 主要依据 |
|---|---|---|---|
| **C-01** | **公开生态中不存在**任何"输入 Java 源码 → 输出业务流程模型（BPMN / 流程图）"的**端到端开源工具**。最接近的两条路径都只到"技术执行序列"层：`Adrninistrator/java-all-call-graph`（方法调用链 + **方法执行顺序** + DB 表/字段 + MQ + HTTP + 事务）与 `sharptoolbox/codebase-reverse`（agent skill，源码→功能/实现/架构/接口/对象/组件/数据库元模型）。 | **高** | 58 条候选逐条核对"输入要求"与"输出物形态"两列，无一条输出物为业务流程模型（§5） |
| **C-02** | 可用地面由**四类原子能力**拼成，且**没有现成编排器**把它们串起来：① 程序事实抽取（调用图/执行顺序/数据流/SQL 血缘）② 结构与架构建模（DDD/C4/模块/本体）③ 运行时事件采集（OTel → trace → 事件日志 → 流程挖掘）④ 语义补全（LLM 把技术事实翻译成业务语言）。 | **高** | §5 七类候选的输入/输出可拼接性分析；S7 方法论清单中亦无此类开源流水线 |
| **C-03** | **最大单点缺口是"代码 → 事件日志"这座桥**。流程挖掘阵营（PM4Py / Apromore / bupaR）成熟度最高、**输出物形态唯一直接就是业务流程模型**，但输入一律要求已存在的事件日志（case id + activity + timestamp）。可行桥只有两条：(a) OTel Java agent 插桩真跑，把 span 转事件日志；(b) 从调用图/方法执行顺序合成伪事件日志。**(b) 无任何公开实现**。 | **高** | PM4Py / bupaR / Apromore 官方文档的输入格式要求（§5-A「输入要求」列）；GitHub Search API 多轮检索 `event log extraction … process mining`、`business process recovery source code` 均返回 0 相关结果 |
| **C-04** | **Java 程序事实抽取层证据最扎实、可直接用、不需自研**：字节码侧 Soot / SootUp / WALA / Tai-e / java-callgraph2；源码侧 JavaParser / Spoon / Joern(`javasrc2cpg`) / Semgrep / OpenRewrite(LST)；工程化封装 java-all-call-graph（写关系库 + SQL 查询 + **MCP Server**）。 | **高** | §5-B/C 各条许可证与活跃度均为 A 级；`java-all-call-graph` 已发布 Maven Central 且有场景化文档 |
| **C-05** | **许可证是本场景（金融客户交付）的头号约束，不是技术约束**。四档风险：① **强 copyleft + 需商业授权**——PM4Py（AGPL-3.0，官方明示闭源商用需另一许可）、jQAssistant（GPL-3.0）、Sourcetrail（GPL-3.0）；② **弱 copyleft，库调用可接受**——Soot/SootUp/FlowDroid/Semgrep（LGPL-2.1）、Tai-e/SonarQube/SchemaSpy/PlantUML（LGPL-3.0）、Chapi/Coca（MPL-2.0）；③ **非 OSI 自定义许可**——bpmn-js（bpmn.io license，含署名义务）、CodeQL CLI（GitHub 专有）、Camunda 8（source-available）；④ **仓库未检出 LICENSE**——code-maat、`WPS/egon.io`、`java-all-call-graph-server`、`gousiosg/java-callgraph`（默认保留所有权利，商用需作者授权）。安全档：Apache-2.0 / MIT / BSD-3-Clause / EPL-2.0 / CC0-1.0。 | **中高**（法务最终结论需专业确认） | 各条许可证来自 GitHub API `license.spdx_id`（A 级）；风险分档为研究员判断（B 级） |
| **C-06** | **"曾经的主力候选"大面积归档/退场**，维护活跃度必须作为硬门槛：**Eclipse MoDisco**（archived，Eclipse 基金会 2026-07-14 发归档公告）、**Sourcetrail 原仓**（archived，2021-12-13；社区分叉 `petermost/Sourcetrail` 仍活跃）、**Apromore 全部 8 个仓库**（archived；公司 2025-11-03 被 Salesforce 完成收购）、**Spring Statemachine**（`archived=true`，homepage 已指向 `spring-attic`）、**Camunda 7 Community Edition**（2025-10 生命周期终止）、**Sourcegraph Cody**（2025-08-01 归档为 `cody-public-snapshot`）、**`archguard/scanner`**（archived，2022-05-25）、**`structurizr/java`·`/cli`·`/lite`**（archived，2026-02-01）。 | **高** | GitHub API `archived` 字段（A 级）+ 官方 EOL 公告（§10 E-12～E-18） |
| **C-07** | **金融语境专属证据薄弱**：未找到"银行/保险核心系统业务流程逆向"的**公开可复现**案例仓库或工件。公开可查的只有商业厂商的营销型案例（vFunction / Moderne / Celonis）与学术原型（2013 / 2015 / 2019 / 2020 四篇"从源码恢复业务流程/BPMN"论文）。FIBO 提供金融业务本体可做**术语对齐锚点**，但**不存在"代码 → FIBO 概念"的自动映射工具**。 | **中高** | S7 检索结果；论文为 B 级（§10 E-19～E-22）；FIBO 仓库为 A 级 |
| **C-08** | **LLM / agent 路线在 2025–2026 快速成熟，但缺任何公开基准**：Blarify（Java 支持官方标注 **beta**）、Potpie、GraphRAG、`codebase-reverse` 能产出可读的功能/接口/领域叙述，但**没有公开准确率或召回率数据**，也无法证明对"中型 Java 单体（数十万行）"的召回完整性。用于客户交付必须配"人工回链校验"环节，且不能把准确率写进 AC。 | **中** | 各项目 README/docs（A 级）；"缺基准"为多轮检索未命中结论（B 级） |
| **C-09** | **与本工程语境（中文金融 Java + Spring + MyBatis）最贴合的公开件集中在两个作者群**，且许可证均为 Apache-2.0 / MIT / MPL-2.0，中文文档齐全：`Adrninistrator` 系列（`java-callgraph2` → `java-all-call-graph` → `java-all-call-graph-server`(MCP) → `gen-java-code-uml-sequence-diagram` → `mybatis-mysql-table-parser`）与 `phodal`/`archguard` 系列（`Chapi` 统一代码元模型、`Coca` 遗留系统重构工具箱、`ArchGuard` 架构工作台）。 | **高** | GitHub API + 仓库 `docs/usage_scenarios/*.md`（A 级，raw 文件 HTTP 200 已验证） |
| **C-11** | **五类业务资产的公开生态覆盖度不均衡**：**数据资产 > 接口 ≈ 领域概念 > 业务规则 > 业务流程**。数据资产与接口有成熟活跃工具（SchemaSpy / Atlas / sqlglot / mybatis-mysql-table-parser / OTel Java）；领域概念有 Chapi / jMolecules / Spring Modulith / FIBO；业务规则需二开（Joern / CodeQL / Tai-e + 自定义 source/sink）；而**核心诉求「业务流程」恰是覆盖度最低的一类**，其三个关键缺口（G-01 / G-02 / G-09）全在"从技术事实到流程模型"的转换环节。 | **高** | §7 五类资产 × 逆向输入矩阵（逐格给出候选与缺口编号） |
| **C-12** | **「差异清单 + 评审会」在公开生态中有可组装的通用件，但没有现成的流程包**。可组装件分三条路径：模型 vs 模型（`bpmn-js-differ`，MIT）、模型 vs 事实（PM4Py conformance checking：token-based replay / alignments，产出逐 trace 偏差与 fitness）、条目 vs 条目（`OpenFastTrace`，GPL-3.0，产出追溯矩阵／覆盖率／未满足项清单）；评审会与三态处置可直接引用 **IEEE 1028-2008** 的评审类型、进入/退出准则与异常处置，以及 **Example Mapping** 的 Questions 卡片（＝"标记后续人工处理"）、**Cucumber** 的 `pending` 步骤（＝"标记后续人工处理"）。 | **高** | §9.2 / §9.3 / §9.4；IEEE 1028 页面与 Example Mapping 页面本环境 **HTTP 200 已验证** |
| **C-13** | **规模口径中「约 50 微服务」是最硬的约束**（K-1）：静态调用图工具几乎都是单构建单元／单仓视角，**跨服务的端到端业务流程无法由静态分析得到**，必须靠 ① OTel 分布式追踪 ② MQ topic／接口契约 ③ 网关日志 ④ 人工拼接。检索未命中"多仓静态调用图 → 跨服务流程模型"的开源实现（新增缺口 **G-10**），也未命中多仓扫描结果的聚合层（**G-11**）。 | **高** | §8.1 K-1、§8.3；C 类各候选的「输入要求」列直证其单仓视角 |
| **C-14** | **两类确认覆盖策略（全量 vs 分级）在公开生态中都有可溯源支撑**，因此该选择是**业务决策而非技术约束**：全量确认可由 IEEE 1028 的 inspection（100% 覆盖 + 退出准则）+ OpenFastTrace 覆盖率门禁支撑；分级确认可由 IEEE 1028 允许按风险选择评审类型 + `ddd-crew/core-domain-charts`（核心域识别画布）+ `code-maat`／CodeScene 的变更耦合与热点（量化"关键性"）支撑。**xiao 未答前两者并列呈现，不择一**。 | **高** | §9.1 表（S-A／S-B 两行，各附实践来源与代价） |
| **C-15** | **「仅确认关键业务流程」这条 v4 冻结路线在工具层面普遍可行**：86 条候选中 **71 条（82.6%）** 具备明确的输入范围限定入口（包名／路径／模块／tag／条目 ID／流程定义 key／单份文档），**6 条为「部分」**（粒度到服务或模块、非业务场景），**9 条「不适用」**（本体、注解库、按版本推进的迁移工具、清单类）。该路线的瓶颈**不在工具能否切片**。 | **中高**（63/86 条为**推断**、未实测；直证仅 14 条） | §9.6 汇总表 + §5 各表第 12 列逐条标注 |
| **C-16** | **真正的瓶颈是「客户人工判断的重点交易与重点场景」→「代码入口集合」的映射没有公开工具**（缺口 **G-14**）：客户给的是业务语言（如"大额跨行转账""理赔受理"），而所有工具的切片入口都是技术语言。检索未命中任何"业务场景描述 → 代码入口定位"的开源实现；学术侧对应问题为 **feature location**，其工具（Feather、Sando）无维护中的开源实现（与 G-04 交叉印证）。该映射只能靠人工 + LLM 辅助建立，且**每条关键流程都要做一次**。缓解：v4 允许差异清单以「后续人工处理」收口，映射不确定项不阻断评审会结论。 | **高** | §9.6；G-04 与 G-14 交叉印证（多轮 GitHub Search API 检索未命中） |
| **C-10** | **"直接"级能力只有一种情形**：目标系统**已经**把工作流/规则/状态机外化到引擎里（Flowable / Activiti / Camunda / Drools / LiteFlow）。此时流程定义（BPMN XML / DRL / EL 编排表达式）与运行历史表（`ACT_HI_*`）可直接导出为权威业务流程。**这是需求阶段必须最先向客户确认的一个事实**（见 §14.2 Q1）。 | **高** | §5-F 各引擎的输入/输出列；Flowable 与 Activiti 共享 `ACT_*` 表族为官方文档直证 |

---

## 4. 类别总览（8 类，每类：能回答什么 / 缺什么）

### A. 流程挖掘 / 事件日志（process mining、BPMN 发现）

**能回答**：给定事件日志，"流程**实际**怎么跑"——流程发现（自动出 BPMN / Petri 网 / Process Tree）、变体枚举、瓶颈与等待时间、返工与回退、与设计稿的一致性偏差、绩效指标。**这是七类中唯一"输出物形态本身就是业务流程模型"的一类。**

**缺什么**：
1. **输入错配（致命）**：一律要求 case id + activity + timestamp 的事件日志。本场景只有源码，没有日志。
2. **没有"代码 → 事件日志"的公开转换器**（缺口 G-01）。两条可行桥：(a) OTel Java agent 插桩 + 流量回放；(b) 从调用图/方法执行顺序合成伪事件日志——(b) 无公开实现。
3. **业务事件命名与粒度必须人工定义**：日志里的 activity 名来自埋点或 span 名（技术名），不等于业务活动名（"贷款审批""理赔受理"）。
4. **开源阵营正在退场**：Apromore 全线归档并被 Salesforce 收购；PM4Py 转 AGPL-3.0 + 双许可。

### B. Java 静态分析与程序结构恢复（源码/字节码解析、架构依赖分析）

**能回答**：包/类/方法/字段级结构与依赖、分层与模块边界、架构违规与坏味道、"哪些类属于同一簇"、"该先看哪块"、以及可查询的代码事实库（Neo4j 图 / 关系库 / 统一 JSON 元模型 / LST）。

**缺什么**：
1. 全部停在**技术结构**层，**不产出业务语义**——没有"业务活动""业务规则""流程分支条件""参与者/角色"这些概念。
2. 对 Spring AOP、动态代理、反射、MyBatis XML 映射、MQ 监听、`@Scheduled` 定时任务等**隐式调用默认断链**，需专门解析器（`java-all-call-graph`、`mybatis-mysql-table-parser` 是少数覆盖的，覆盖度需实测，见 G-07）。
3. **没有把结构事实自动聚成"业务能力/用例"的现成件**。学术上有聚类式架构恢复（Bunch / ACDC / MoJo）与特征定位（feature location：Feather、Sando），但**未找到 2024 年后仍在维护的开源工程实现**（缺口 G-04）。
4. 两个曾经的主力都退场了：交互式源码浏览器 Sourcetrail 原仓归档（仅社区分叉在维护）、模型驱动逆向框架 MoDisco 归档。

### C. 调用图 / 数据流 / 污点分析（业务规则与数据流证据提取）

**能回答**：从入口（Controller / MQ 消费者 / 定时任务 / RPC）到出口（DB 写 / MQ 发 / 外部 HTTP）的**完整方法链**；数据从哪来到哪去（含 SQL 列级血缘）；哪个字段被哪段代码改写；哪些分支条件控制流程走向（`java-all-call-graph` 提供"方法执行顺序：顺序/条件/循环"）；以及**从 Java 代码自动生成 UML 时序图**（`gen-java-code-uml-sequence-diagram`）。

**缺什么**：
1. **调用图 ≠ 流程图**：缺业务分支语义、缺角色/参与者、缺业务事件命名、缺异常与补偿路径的业务含义。
2. **规模爆炸**：中型项目全量调用图可达百万级边，必须按入口切片。`java-all-call-graph` 文档专门提供"只解析部分包"的用法，说明这是公认痛点。
3. **污点分析工具面向安全场景**（FlowDroid / Tai-e / CodeQL / Semgrep），要用它做"业务规则提取"必须自定义 source/sink，**没有现成的金融业务规则库**。
4. CodeQL 需**工程可编译**才能建库，且 CLI 为 GitHub 专有许可；Semgrep OSS 引擎无跨过程数据流（在商业 Pro 引擎）。

### D. 领域模型与业务概念恢复（DDD 战略设计辅助、代码→业务术语映射）

**能回答**：限界上下文与子域怎么划、聚合/实体在哪、模块之间发布/订阅了哪些事件、代码里已有的领域语言是什么、C4 各层视图、以及金融标准业务词汇（FIBO）作为对齐锚点。

**缺什么**：
1. 绝大多数是**正向设计工具**（先建模再落代码）。真正"从存量代码反推模型"的只有：Spring Modulith（限已模块化或可加注解的 Spring Boot 应用，产出 PlantUML/C4 图 + Application Module Canvas + **事件发布注册表**）、Structurizr 历史上的 `ComponentFinder`（**子仓 `structurizr/java` 已归档**）。
2. **没有任何工具能从代码自动产出业务术语表**。术语只能靠 LLM 猜测 + 业务专家确认，或靠 FIBO 人工对齐（缺口 G-03）。
3. 对**无注解的老代码**（金融存量系统的常态），jMolecules / Spring Modulith 基本失效——它们读的是"已被标注的意图"。
4. 方法论物料（ddd-crew 系列）为 CC-BY-SA-4.0，作为客户交付物的一部分需注意**相同方式共享**条款与合同约定。

### E. LLM 辅助代码理解与业务流程文档生成（含 agent 化流水线）

**能回答**：把代码 / 调用链 / DB schema 翻译成人话——功能说明、接口清单、时序叙述、领域术语候选、跨模块全局叙述；能 agent 化批处理；能把代码库变成可 Cypher 查询的图（Blarify / Potpie / llm-graph-builder）；能用 MCP 把调用链事实直接喂给 agent（`java-all-call-graph-server`）。

**缺什么**：
1. **无公开准确率/召回率基准**，方案中不能承诺"自动化反推的业务流程有 X% 正确"（缺口 G-06）。
2. **上下文窗口 vs 中型 Java 项目**：数十万行必须先用 B/C 类切片，而"切片策略"本身没有现成工具（Repomix / gitingest 只做打包与 token 计数）。
3. **输出不是标准流程格式**：产出 Markdown / JSON / 自然语言，不是 BPMN / XPDL，需额外转换与结构校验。
4. **数据不出域约束**：金融客户通常不允许源码出域，需本地模型；"代码图 + 本地小模型"的效果无公开证据。
5. **头部项目变更率极高**：Blarify v2 已归档转向 Blarify-Next；Cody 已归档；选型需接受 6–12 个月的重构风险。

### F. 数据库 / 配置 / 工作流引擎驱动的流程还原（工作流定义、状态机、规则引擎）

**能回答**：数据实体与关系（ER + 列注释）、状态字段的合法流转、schema 与迁移脚本承载的**业务演进史**（带时间戳与作者）、**已外化到配置/引擎里的流程定义**（BPMN XML、DRL 规则、EL 编排表达式、状态机配置）、MyBatis XML 中的表名、SQL 的表级/列级血缘。

**缺什么**：
1. **前提不成立时整类失效**：只有系统真的用了工作流/规则/状态机引擎，才有现成流程定义可导。金融老系统最常见的形态是"流程硬编码在 Service 层 + 状态字段散落在 DB"，此时本类只能给数据侧证据。
2. **ORM 映射 → 业务实体的完整链路工具碎片化**：`mybatis-mysql-table-parser` 仅 4★、只支持 MyBatis XML + MySQL；没有覆盖 Hibernate/JPA 注解的等价物。
3. **没有工具能把"DB 状态字段 + 更新它的代码位置"自动合成状态机**（缺口 G-08）。
4. 渲染与承接层有合规/生命周期问题：bpmn-js 为自定义许可（署名义务）；Camunda 7 CE 已 EOL，Camunda 8 为 source-available；**Spring Statemachine 已归档**（`archived=true`，homepage 指向 spring-attic）。

### G. 遗留系统逆向工程方法论与案例（金融/银行/保险核心优先）

**能回答**：如何组织这件事（阶段、角色、工件、验收）、别人踩过什么坑、可复现的练手样本从哪来（公开遗留代码库清单）、"AI agent 做遗留现代化"这条新路线的公开资料入口、以及"模型驱动逆向工程（MDRE）"的完整范式参考（MoDisco 的 KDM→业务视图转换思路）。

**缺什么**：
1. **金融/银行/保险核心系统的公开可复现案例几乎没有**：能查到的都是商业厂商营销型案例，无工件、无数据、无可验证指标（缺口 G-05）。
2. awesome-* 清单是**链接聚合，不是可执行流程**；缺"业务流程逆向"的**验收标准模板**与**工件模板**。
3. 学术原型（从源码恢复 BPMN，2013/2015/2019/2020）**没有维护中的开源实现**；且 2013 那篇的标题即《Repairing Business Process Models as **Retrieved from Source Code**》——"需要修复"本身说明自动恢复质量不足以直接使用。
4. 缺"逆向出的流程如何被业务方确认"的公开评审机制设计 —— **v2 更新**：该项已由新增的 **H 类**部分填补（见下），但**仍缺金融行业同口径的公开案例**（G-05 不变）。

### H. 客户确认与差异管理（差异清单 / 评审会 / 追溯 / 活文档）——**patch-01 修订 3 新增**

**能回答**：逆向出的业务流程**如何被客户方业务专家确认**——差异清单怎么机器化生成（模型 vs 模型 / 模型 vs 事实 / 条目 vs 条目三条路径）、评审会依据什么标准开（IEEE 1028-2008 的评审类型与进入/退出准则）、差异项的三态处置（确认通过／按客户修正／标记后续人工处理）用什么载体承载（OpenFastTrace 条目状态、Cucumber `pending`、Example Mapping 的 Questions 卡片）、确认结果如何固化才不失效（Gherkin 规格 + 活文档）、以及工作坊与远程评审的组织工件（COMO Prep Canvas、Virtual Modelling Templates、EventStorming、Domain Storytelling）。

**缺什么**：
1. **没有面向"逆向出的业务流程 vs 客户认定流程"的开箱即用差异清单模板与评审会流程包**（缺口 G-12）；现有件都是通用件（需求追溯、BPMN diff、流程挖掘一致性检查），需自行组装。
2. **无金融行业同口径（20 模块／50 微服务／20 万行）的公开确认案例**（G-05）。
3. 差异清单的**粒度口径**（按流程一条／按业务规则一条）与**评审会形式**（单次总评审／分期）在 v4 中仍标「待回源」，公开实践两种都有，无定论。
4. 50 微服务规模下**必然分期评审**，但"如何切分评审批次"无公开方法（可用 `core-domain-charts` 与变更热点作判据，但属研究员组合，非既有实践）。

---

## 5. 候选清单（主表 70 条：A6 / B11 / C10 / D8 / E8 / F11 / G4 / H12；另次级候选 16 条。字段固定 **12 列**）

**字段口径**
- `活跃度`：GitHub API `pushed_at`（最后一次推送到默认分支）+ `archived` 标记，快照 2026-10-08。`pushed_at` 不等于"在维护"（可能是 bot 或文档提交），关键项另注 release 信息。
- `反推能力评级`：**直接** = 输出物本身即业务流程/流程定义；**间接** = 输出技术或结构事实，需人工/LLM 转译成业务流程；**需二开** = 是库/框架，必须写代码才能得到有用输出。
- **通用来源**：每条的许可证、star、`pushed_at`、`archived` 均取自 `https://api.github.com/repos/<owner>/<repo>`（2026-10-08 访问），该 API 路径与下表 URL 列指向同一项目。
- **第 12 列「切片输入能力」（patch-02 第 3 项新增）**：回答「能否把输入限定到**客户指定的流程/场景集合**」，取值 **可／部分／不适用**，并附依据与 **推断／直证** 标记。**「推断」= 依据该候选已采集的能力描述与常规用法推断，本研究未实测**（受本卡「只读调研、不安装依赖、不编译第三方代码」约束）；**「直证」= 有文档明示的机制或该产物形态本身即单场景**。汇总与结论见 §9.6。
- **第 11 列「可输出业务资产类型」（多选，对应 TSK-45 v4 AC-03 与 patch-01 修订 2）**：取值域为 v4 冻结的**五类业务资产** —— **流程**（业务流程）／**规则**（业务规则）／**概念**（领域概念）／**数据**（数据资产）／**接口**（接口）。标注口径为「该工具的输出物**能直接或经一次转译支撑**哪几类业务资产的逆向获取」，不代表它能独立完成该类资产的全部提取。写「不直接产出」者为本项目的**前置件或索引类**资源，不产出业务资产本身。

### A 类：流程挖掘 / 事件日志（6 条）

| 名称 | URL | 许可证 | 活跃度（最后推送 / archived） | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **PM4Py** | https://github.com/process-intelligence-solutions/pm4py | AGPL-3.0 | 2026-09-01 / 否；最新 release **v2026.10.0（2026-10-07）**；1048★ | Python 3.9–3.13，`pip install pm4py`；**非 Java 工具**，需自建 Java→日志导出 | 事件日志：XES / CSV / pandas DataFrame（必须有 case id + activity + timestamp） | 流程模型（Petri 网 / **BPMN** / Process Tree）、BPMN 图、一致性检查、变体与绩效统计 | **间接**（有日志即近"直接"；本场景无日志） | 中（Python API 文档完善；难点全在日志采集） | **高**：AGPL-3.0 网络服务条款；官方明示"闭源商用环境另有许可版本"，客户交付前须取得商业许可或做物理隔离部署 | 流程 | **可**（事件日志可按 case/activity/时间戳先过滤再做发现；已发现模型可裁子网）｜推断 |
| **Apromore（开源线）** | https://github.com/apromore/ApromoreCore | LGPL-3.0 | **archived=true**，最后推送 2025-06-07；143★。同 org 全部 8 个仓库均已归档（含 `ApromoreCE` 2022-11-16）。注：官方文档与检索结果多处引用 `apromore/ApromoreCommunity`，但 GitHub API 对该路径返回 **404** | Java / Spring Boot + Angular，Docker Compose 部署 | 事件日志（XES / CSV）+ 可选业务指标 | Web 平台：流程发现、变体探索、一致性检查、预测监控 | **间接** | 中—高（需部署整套平台） | **高**：开源线全线归档；公司 **2025-11-03 被 Salesforce 完成收购**，能力并入商业产品，开源版无维护承诺 | 流程 | **可**（平台内按变体/时间/案例属性筛选日志）｜推断（开源线已归档） |
| **bupaR** | https://github.com/bupaverse/bupaR | GitHub API 返回 **NOASSERTION**（根目录未检出标准 LICENSE 文件）；README 与 CRAN 页标注 **MIT**（v1.0.1，2025-02）→ **两源冲突，待回源** | 2025-11-28 / 否；62★ | **R 包**（非 Java），CRAN 安装；配套 Shiny 前端 | 事件日志（`eventlog` tibble / XES） | 流程统计、变体与绩效分析、ggplot 可视化、流程探索界面 | **间接** | 中（需 R 技能栈） | 中：许可证两源冲突须先澄清；R 生态难以嵌入 Java 交付流水线 | 流程 | **可**（R 的 `filter_*` 系列按活动/案例/时间过滤事件日志）｜推断 |
| **Eclipse Trace Compass** | https://github.com/eclipse-tracecompass/org.eclipse.tracecompass | EPL-2.0 | 2026-09-11 / 否；55★ | Java / Eclipse RCP 桌面应用（另有 incubator 仓） | 各类 trace（CTF / LTTng；OTel 支持需插件，**待回源**） | 时间线视图、调用栈、可脚本化的自定义分析 | **间接** | 中—高（Eclipse 插件栈，学习曲线陡） | 低—中：EPL-2.0；桌面工具，难以流水线化与批处理 | 流程·接口 | **可**（按时间窗/线程/组件过滤 trace 视图）｜推断 |
| **OpenTelemetry Java Instrumentation** | https://github.com/open-telemetry/opentelemetry-java-instrumentation | Apache-2.0 | 2026-10-08 / 否；2640★ | Java agent（`-javaagent`），**零代码侵入**；自动插桩覆盖 Servlet / Spring / JDBC 等 | **运行中的 JVM** + 可访问的目标环境（准生产或流量回放） | OTLP traces / metrics（→ 可转事件日志，供 A 类流程挖掘消费） | **间接**（是"造事件日志"的地面，本身不做流程发现） | 中（需可运行环境与回放流量） | **低**：Apache-2.0。合规点在**数据侧**：trace 携带的业务字段须脱敏与范围控制，生产数据不得外传 | 流程·接口·数据 | **部分**（可按服务/端点开关插桩与采样；但「业务场景」标签需自定义埋点才能切）｜推断 |
| **code-maat** | https://github.com/adamtornhill/code-maat | GitHub API **未检出 LICENSE** → **待回源**（《Your Code as a Crime Scene》配套工具，历史资料称 GPL） | 2025-07-03 / 否；2638★ | Clojure，提供独立 jar 与 Docker 镜像 | VCS 日志（Git / SVN / Mercurial），可选缺陷系统导出 | 变更耦合（temporal coupling）、热点、复杂度演化、团队与文件归属 CSV | **间接**（"哪些代码总是一起改"→ 业务功能的隐式边界，是 G-04 缺口的现实替代品） | 低（CLI，一条命令出 CSV） | **中—高**：仓库未检出许可证 = 默认保留所有权利，商用分发前必须取得授权 | 概念 | **可**（按文件/目录范围与时间窗限定分析）｜推断 |

### B 类：Java 静态分析与程序结构恢复（11 条）

| 名称 | URL | 许可证 | 活跃度 | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **Soot** | https://github.com/soot-oss/soot | LGPL-2.1 | 2026-09-28 / 否；3102★ | Java 库 + CLI，Maven；经典 Jimple IR | Java 字节码（`.class`/`.jar`）或源码（经 Jimple） | Jimple IR、CFG、调用图、指针分析结果（可编程导出） | **需二开** | 高（API 陈旧、文档分散） | 中：LGPL-2.1，库调用可接受，须保留许可声明；分发衍生库需开源该库 | 流程·规则·概念·接口 | **可**（`-process-dir` 与包含/排除类列表限定分析范围）｜推断 |
| **SootUp** | https://github.com/soot-oss/SootUp | LGPL-2.1 | 2026-10-08 / 否；824★ | Java 库，Maven/Gradle；文档站 soot-oss.github.io/sootup（**本研究环境返回 404，`*.github.io` 整体不可达，待回源**） | 字节码（`.class`/`.jar`/`.apk`），可选 Java 源码前端 | 类型层次、调用图（CHA/RTA/VTA/SPARK 等多算法）、CFG、数据流分析（含 Heros IFDS） | **需二开** | 中—高 | 中：LGPL-2.1；README 自述"全新重构架构"，API 稳定性需实测（**待回源**） | 流程·规则·概念·接口 | **可**（按 input location 指定 jar/目录，可只加载目标模块）｜推断 |
| **WALA** | https://github.com/wala/WALA | EPL-2.0 | 2026-10-07 / 否；874★ | Java 库，Maven（IBM T.J. Watson 出品） | Java / Android 字节码，另支持 JavaScript | 调用图、程序切片、指针分析、类型分析 | **需二开** | 高 | 低—中：EPL-2.0（弱 copyleft，与 Apache-2.0 兼容） | 流程·规则·概念·接口 | **可**（`AnalysisScope` 文件指定纳入/排除的包）｜推断 |
| **JavaParser** | https://github.com/javaparser/javaparser | GitHub API 返回 **NOASSERTION**；README 自述**双许可 LGPL-2.1 或 Apache-2.0**（以 LICENSE 文件为准，**待回源**） | 2026-10-07 / 否；6159★；支持 Java 1–25 语法 | Java 库，Maven/Gradle；含 `javaparser-symbol-solver` | **Java 源码**（`.java`） | AST、符号解析、类型推断；用 Visitor 可输出任意自定义结构 | **需二开**（自建"源码→业务事实抽取"的最直接地基） | 低—中 | **低**：若可单方选择 Apache-2.0 则非常适合客户交付（须先确认双许可选择权） | 流程·规则·概念·数据·接口 | **可**（按文件/目录逐个解析，天然可只喂目标模块）｜推断 |
| **Spoon** | https://github.com/INRIA/spoon | GitHub API 返回 **NOASSERTION**；项目自述 **CeCILL-C v2.0 与 LGPL 双许可**（**待回源**） | 2026-10-05 / 否；1959★；INRIA 维护，支持 Java 24+ | Java 库，Maven；支持 `noclasspath` 模式（**缺依赖也能解析**，对残缺存量工程关键） | **Java 源码** | 完整元模型 AST、Processor 查询与代码变换 | **需二开** | 中 | 中：CeCILL-C / LGPL 双许可需法务确认 | 流程·规则·概念·数据·接口 | **可**（`setInput` 指定路径，可按包过滤；`noclasspath` 允许只给部分源码）｜推断 |
| **OpenRewrite** | https://github.com/openrewrite/rewrite | Apache-2.0 | 2026-10-08 / 否；3776★ | Java 库 + Maven/Gradle 插件 | **可构建的 Java 工程**（生成 Lossless Semantic Tree，LST） | LST 可查询/可变换；Recipe 可批量改写；可输出结构化查询结果 | **需二开**（LST 是"带完整类型与语义的 AST"，写自定义 Visitor 即可批量抽取业务事实，如"所有 `@Transactional` 方法 + 其执行的 SQL"） | 中—高（需写 Java Visitor） | **低**：Apache-2.0。大规模执行平台 Moderne 为商业产品，可只用 OSS 引擎 | 流程·规则·概念·数据·接口 | **可**（Maven/Gradle 按模块执行；recipe 可用包/类型匹配限定）｜推断 |
| **jQAssistant** | https://github.com/buschmais/jqassistant | GPL-3.0 | 2026-10-07 / 否；297★ | Java，Maven/Gradle 插件 + CLI；扫描结果写入 **Neo4j** | 字节码/源码、`pom.xml`、properties、XML、文件、Git 历史、DB schema（插件） | Neo4j 图 + Cypher 查询结果 + AsciiDoc 报告（可嵌 PlantUML） | **间接**（可自定义 Cypher 把"入口→Service→DAO→表"串成链路并出报告；B 类中最接近"可查询事实库"的一件） | 中 | **高**：GPL-3.0。作为构建插件在 CI 内运行通常可接受，但嵌入客户交付物或对外提供网络服务需法务评估 | 流程·概念·数据·接口 | **可**（扫描配置 include/exclude 路径；Cypher 可从指定入口切片查询）｜推断 |
| **ArchUnit** | https://github.com/TNG/ArchUnit | Apache-2.0 | 2026-10-08 / 否；3852★ | Java 库，以单元测试形式运行；含 Spring / JPA / JavaModule 等扩展 | 编译后的 `.class`（classpath） | 架构断言结果（通过/失败）、可导出的依赖关系 | **间接**（用于**验证**"我们反推出的分层/上下文边界"是否成立，是逆向结果的回归防线） | 低 | 低：Apache-2.0 | 概念·接口 | **可**（`ClassFileImporter().importPackages(...)` 显式限定包）｜推断 |
| **ArchGuard** | https://github.com/archguard/archguard | MIT（GitHub API）；官方文档页自称 MPL-2.0 → **两源冲突，待回源** | 2026-10-02 / 否；677★。**注意**：扫描器子仓 `archguard/scanner` **archived=true**（2022-05-25），`archguard/codedb` 最后推送 2023-12-09 | Kotlin + TypeScript，前后端 + 数据库，Docker 部署；扫描基于 Chapi，支持 Java / Kotlin / TypeScript | 源码仓库、Git 历史、API 定义、DB schema | Web 工作台：架构视图、模块依赖、分层/领域分析、API 与数据模型、坏味道、架构适配度 | **间接**（国内团队产物、中文文档；架构治理导向而非流程导向） | 中—高（需部署平台） | 低—中：许可证两源冲突须澄清；主仓与已归档扫描器的版本耦合关系需实测（**待回源**） | 概念·数据·接口 | **部分**（按仓库/模块扫描，未见「按业务流程」级切片）｜推断 |
| **Chapi** | https://github.com/phodal/chapi | MPL-2.0 | 2026-08-18 / 否；315★ | Kotlin 库，Gradle；CHAPI = Common Hierarchical Abstract Parser and Information Converter | Java / Kotlin / Scala / Go / TypeScript / Python **源码** | 统一层级化代码元模型（Container / DataStructure / DataFunction / 字段 / 注解），可序列化 JSON | **需二开**（"把多语言源码抽象成统一元模型"的现成地基，天然适合喂给 LLM 或图数据库） | 中 | 低—中：MPL-2.0（文件级 copyleft，修改的文件需开源） | 概念·数据·接口 | **可**（按目录/文件解析，输出可按包过滤）｜推断 |
| **Coca** | https://github.com/phodal/coca | MPL-2.0 | 2026-01-06 / 否；990★ | Go 语言 CLI | Java 源码（亦支持多语言转换分析） | 转换分析、调用分析、依赖分析、度量分析、架构分析、静态分析、坏味道、重构建议 | **间接**（定位即"遗留系统重构与自动化分析工具箱"，与本项目目标高度重合） | 中 | 低—中：MPL-2.0 | 流程·概念·接口 | **可**（CLI 按输入目录分析）｜推断 |

### C 类：调用图 / 数据流 / 污点分析（10 条）

| 名称 | URL | 许可证 | 活跃度 | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **Joern** | https://github.com/joernio/joern | Apache-2.0 | 2026-10-08 / 否；3555★ | Scala 实现，CLI + Python/Scala 查询接口；Java 经 `javasrc2cpg`（源码）与 `jimple2cpg`（字节码，基于 Soot） | Java 源码或字节码（另支持 C/C++/JS/Python/PHP/二进制） | **代码属性图 CPG**（可导出 GraphML）；用查询 DSL 取数据流路径、调用链、切片 | **间接**（能把"入口→…→DB/MQ"的数据流路径查出来，是业务规则定位的强力手段） | 中—高（CPG 查询语言需学习） | **低**：Apache-2.0，客户交付友好 | 流程·规则·数据·接口 | **可**（`javasrc2cpg` 指定 inputPath；CPG 可从指定入口方法做可达性切片——切片靠查询而非配置）｜推断 |
| **CodeQL（查询库仓库）** | https://github.com/github/codeql | 仓库内查询与库标注 **MIT**；**CodeQL CLI 本体受 GitHub 专有许可约束**（非 OSI） | 2026-10-08 / 否；10175★ | CodeQL CLI + 构建集成；Java 需**工程可编译**才能生成数据库 | 可构建的 Maven/Gradle 工程（`codeql database create --language=java`） | 查询结果（SARIF / CSV）、跨过程数据流路径 | **间接** | 中—高（需可编译 + 学 QL） | **高**：CLI 许可限制商业用途，通常需 GitHub Advanced Security；金融客户内网环境需法务与采购双重确认 | 流程·规则·数据·接口 | **部分**（数据库按构建单元生成，粒度通常是整个服务；查询侧可按包/类限定）｜推断 |
| **Semgrep** | https://github.com/semgrep/semgrep | LGPL-2.1（OSS 引擎）；Semgrep Code（Pro 引擎）为商业 | 2026-10-08 / 否；16926★ | 编译型核心引擎（GitHub API 主语言标注 C），pip / 容器镜像分发；规则用 YAML 编写 | **Java 源码**（无需编译），支持 30+ 语言 | 模式匹配位置与元变量；可写自定义规则批量抽取"业务规则模式" | **间接**（模式匹配级；**跨过程数据流在商业 Pro 引擎**） | 低 | 中：OSS 引擎 LGPL-2.1；核心能力（跨过程）在付费版，能力边界需实测 | 规则·概念·接口 | **可**（CLI 接受路径参数；规则可用 `paths.include/exclude`）｜推断 |
| **Tai-e** | https://github.com/pascal-lab/Tai-e | LGPL-3.0 | 2026-09-19 / 否；1821★ | Java 框架，Gradle；由 PASCAL Lab 维护（org `pascal-lab`）；文档站 tai-e.pascal-lab.net | Java 字节码（`.class`/`.jar`）+ 可解析的 classpath | 指针分析、调用图、污点分析、数据流分析结果（可编程输出） | **需二开**（研究级框架，适合自建"业务字段污点追踪"） | 高 | 中：LGPL-3.0（比 2.1 更强的 copyleft 与专利条款） | 流程·规则·数据 | **可**（配置 analysisScope 与入口点，可指定待分析类）｜推断 |
| **FlowDroid** | https://github.com/secure-software-engineering/FlowDroid | LGPL-2.1 | 2026-09-28 / 否；1269★ | Java 库 / CLI，Maven；基于 Soot | Android APK 或 Java 字节码 + **自定义 source/sink 定义文件** | 从 source 到 sink 的完整污点传播路径（含调用链） | **需二开**（把"业务入口=source、DB/MQ/外部接口=sink"即可反查业务数据流，思路可直接复用） | 中—高（面向 Android 设计，纯 Java 需自备 source/sink） | 中：LGPL-2.1 | 规则·数据 | **可**（source/sink 定义文件本身就是「限定到指定场景」的机制）｜推断 |
| **java-callgraph2** | https://github.com/Adrninistrator/java-callgraph2 | Apache-2.0 | 2026-08-02 / 否；273★；Maven Central 持续发版（4.1.0 等，2026-09） | Java 库，Maven 依赖 | **编译后的 class / jar / war / jmod**（不强制要源码） | 全量方法级静态调用与被调用关系，可写文件或数据库 | **间接**（中文文档、面向国内工程实践；是 `java-all-call-graph` 的底座） | 低—中 | **低**：Apache-2.0 | 流程·接口 | **可**（官方文档明示支持「只解析部分包」）｜文档直证 |
| **java-all-call-graph** | https://github.com/Adrninistrator/java-all-call-graph | Apache-2.0 | 2026-08-28 / 否；572★ | Java 库，**Maven 依赖/插件接入**（依赖 java-callgraph2） | 编译产物（class/jar/war/jmod）+ 可选源码目录、MyBatis XML | 写入关系型数据库：全量方法调用关系、**数据库表与字段**、消息队列（RocketMQ/Kafka）、HTTP 调用、Spring 事务、**方法执行顺序（顺序/条件/循环）**；用 SQL 查询 | **间接（本次盘点中最接近"业务流程骨架"的单一开源件）** | 中（按文档接入 Maven 并建库；中文文档齐全） | **低**：Apache-2.0。README 自述已被 vivo、自如、携程等企业应用（**B 级**，厂商自述，未独立验证） | 流程·规则·数据·接口 | **可**（文档明示「只解析部分包」；结果入库后可按入口方法用 SQL 切片）｜文档直证 |
| **java-all-call-graph-server** | https://github.com/Adrninistrator/java-all-call-graph-server | GitHub API **未检出 LICENSE**（与主仓 Apache-2.0 不一致）→ **待回源** | 2026-06-07 / 否；8★ | Java Web 应用；仓库根目录含 `MCP_SERVER.md` | `java-all-call-graph` 生成的数据库 | Web 界面查询调用链 + **MCP Server 接口，供 AI agent 直接查询调用链事实** | **间接偏直接**（把"程序事实"接入 LLM agent 的现成通道，是 C 类与 E 类的粘合件） | 中 | **中—高**：仓库未检出许可证，商用前必须澄清 | 流程·接口 | **可**（Web/MCP 按入口方法检索调用链）｜推断 |
| **gen-java-code-uml-sequence-diagram** | https://github.com/Adrninistrator/gen-java-code-uml-sequence-diagram | Apache-2.0 | **2021-10-22 / 否（已停更约 5 年）**；5★。配套渲染器 `Adrninistrator/uml-sequence-diagram-drawio`（Apache-2.0，37★，2025-10-24） | Java；从 Java 代码自动生成 UML 时序图，再由 drawio 渲染 | Java 源码/字节码 | **UML 时序图（draw.io 格式）** | **间接偏直接**（本次盘点中唯一"从 Java 代码自动出时序图"的公开开源件；时序图是客户最易评审的流程表达形式之一） | 中 | **低**：Apache-2.0。**风险**：已停更约 5 年，对新版 Java / Spring 的兼容性**必须实测** | 流程·接口 | **可**（按指定入口方法生成时序图）｜推断 |
| **gousiosg/java-callgraph** | https://github.com/gousiosg/java-callgraph | GitHub API **未检出 LICENSE** → **待回源** | 2024-03-22 / 否；844★ | Java，基于 BCEL；提供**静态**与**动态（运行时字节码插桩）**两种模式 | 字节码（静态）/ 运行中的 JVM（动态） | 文本格式调用对（caller, callee） | **间接**（动态模式能拿到"真实跑过"的调用序列，是低成本的运行时证据，可与 A 类事件日志路线互补） | 低 | **中—高**：无许可证文件 = 默认保留所有权利，商用需取得作者授权 | 流程·接口 | **可**（静态：按 jar/class 限定；动态：只记录实际执行过的调用，天然等价于「跑了哪些场景」）｜推断 |

### D 类：领域模型与业务概念恢复（8 条）

| 名称 | URL | 许可证 | 活跃度 | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **Spring Modulith** | https://github.com/spring-projects/spring-modulith | Apache-2.0 | 2026-10-02 / 否；1197★ | Java / Spring Boot，Maven/Gradle + 测试依赖 | 运行中的 Spring Boot 应用 + 单元测试上下文 | **PlantUML / C4 组件图、Application Module Canvas（Markdown）、模块 API 暴露报告、事件发布/订阅注册表**，输出到 `target/spring-modulith-docs/` | **间接偏直接**（"事件发布注册表"是业务流程的强证据；但要求应用已模块化或可加注解） | 低—中 | 低：Apache-2.0 | 流程·概念·接口 | **部分**（按 Spring Boot 应用整体运行，输出为模块级而非「客户指定场景」级）｜推断 |
| **Context Mapper DSL** | https://github.com/ContextMapper/context-mapper-dsl | Apache-2.0 | 2025-07-08 / 否（低频）；268★ | Java + Xtext，Gradle；有 VS Code 扩展 | 手写 `.cmdsl` 模型（可由人工录入代码盘点结果） | 上下文映射图、PlantUML、服务分解模型、用户故事 | **需二开**（正向建模工具，适合承接逆向结果做"结构化落库与评审"） | 中 | 低：Apache-2.0 | 概念 | **可**（模型由人工编写，天然只写目标上下文）｜直证（人工输入） |
| **jMolecules** | https://github.com/xmolecules/jmolecules | Apache-2.0 | 2026-02-03 / 否；1568★ | Java 库（注解 + 接口），Maven；含 ArchUnit / Jackson / Spring 集成模块 | 源码中的注解 | 编译期/运行期可读取的架构与 DDD 构件（Aggregate / Entity / BoundedContext / Layer） | **需二开**（只能读出"已被标注"的意图；**对无注解老代码无效**） | 低 | 低：Apache-2.0 | 概念 | **不适用**（注解库，随代码走，无独立切片入口） |
| **Structurizr** | https://github.com/structurizr/structurizr | Apache-2.0 | 2026-10-05 / 否；445★；homepage = docs.structurizr.com。**注意**：`structurizr/java`、`/cli`、`/lite` 三个子仓 **archived=true**（2026-02-01）；`structurizr/dsl` 与 `C4-DSL/structurizr` 经 GitHub API 均返回 **404**（规范入口已收敛到本仓） | Java 库 + DSL 文本 | DSL 文本，或 Java 代码（历史 `ComponentFinder` 可从源码/字节码抽组件，**该子仓已归档**） | C4 模型（JSON）+ 多视图渲染（PlantUML / Mermaid / dot） | **需二开** | 低—中 | 低：Apache-2.0（DSL/CLI）；Structurizr 托管服务为商业产品 | 概念·接口 | **可**（DSL 人工编写，可只建模目标流程涉及的容器/组件）｜直证（人工输入） |
| **FIBO**（Financial Industry Business Ontology） | https://github.com/edmcouncil/fibo | MIT | 2026-10-07 / 否；747★；EDM Council 维护 | OWL / RDF 本体（**非代码工具**），可导入 Protégé 或图数据库 | 无（它是"目标词汇表"，不是分析器） | 金融业务概念本体：产品、合约、交易、法人实体、监管概念 | **间接**（把从代码恢复出的术语对齐到金融标准业务词汇，是"代码→业务语言"的锚点） | 中—高（本体工程门槛） | 低：MIT。**注意**：不存在"代码→FIBO"的自动映射工具（缺口 G-03） | 概念 | **不适用**（本体词汇表，非分析器） |
| **DDD Starter Modelling Process** | https://github.com/ddd-crew/ddd-starter-modelling-process | CC-BY-SA-4.0 | 2026-08-23 / 否；6052★ | 文档与流程模板（非代码） | 业务专家访谈 + 代码盘点结果 | 领域愿景、领域角色图、子域划分、事件风暴引导 | **间接**（方法论：指导"如何组织业务反向建模工作坊"） | 低 | 低—中：CC-BY-SA-4.0，衍生文档需**相同方式共享**，客户交付合同需约定 | 流程·概念 | **可**（方法论按子域/流程分场次推进）｜推断 |
| **Domain Message Flow Modelling** | https://github.com/ddd-crew/domain-message-flow-modelling | CC-BY-SA-4.0 | 2026-08-23 / 否；409★ | 文档模板 + 画图规范 | 命令/事件/查询清单（可从 Spring Modulith 事件注册表、MQ 配置提取） | 上下文间消息流图（**输出物形态最接近"业务流程图"**） | **间接偏直接** | 低 | 低—中：CC-BY-SA-4.0 同上 | 流程·概念·接口 | **可**（按选定上下文绘制）｜推断 |
| **Egon.io — Domain Story Modeler** | https://github.com/WPS/egon.io | GitHub API **未检出 LICENSE**；关联仓 `WPS/egon.io-website` 为 GPL-3.0，官方文档站称 GPLv3 → **待回源** | 2026-09-09 / 否；838★ | TypeScript / 浏览器应用（可自托管） | 人工录入的领域故事 | 领域故事图（pictographic 序列图），可导出 | **间接**（把访谈结果结构化，是"业务方确认流程"的评审工件） | 低 | **中**：主仓未检出许可证，商用嵌入前必须澄清 | 流程·概念 | **可**（一次一个领域故事，天然单场景）｜直证（方法本身即单场景） |

### E 类：LLM 辅助代码理解与业务流程文档生成（8 条）

| 名称 | URL | 许可证 | 活跃度 | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **Blarify** | https://github.com/blarApp/blarify | MIT | 2026-08-17 / 否；232★。README 自述 v2 已归档、后续在 **Blarify-Next**（同 org Discussions 有公告，**仓库地址待回源**） | Python，需 **Neo4j** 实例；README 明示支持 Python / JavaScript / TypeScript / **Java** / C#，且 **Java 支持标注为 beta** | 代码仓库（Java 为 beta 支持） | Neo4j 代码图（类/方法/调用/继承/导入），可用 Cypher 查询，再由 LLM 回答业务问题 | **间接**（把代码变成可查询的图，是 C+D+E 的粘合层） | 中（需 Neo4j + LLM API key） | 低—中：MIT。**风险**：Java 支持为 beta、v2 已归档，成熟度与延续性不稳定 | 流程·概念·接口 | **可**（按语言/仓库配置扫描范围；图查询可按入口切片）｜推断 |
| **Potpie** | https://github.com/potpie-ai/potpie | Apache-2.0 | 2026-10-08 / 否；5738★ | Python 后端 + 前端，Docker Compose 部署；需 Neo4j + LLM API | 整个代码仓库（解析为知识图谱） | 预置 agent（问答、调试、低层设计、变更影响）+ 自定义 agent；自然语言回答附图谱引用 | **间接** | 中（自托管需 Compose + 向量库 + Neo4j） | 低—中：Apache-2.0；另有商业云版。**合规关键**：代码需送入 LLM，金融客户必须私有化模型 | 流程·规则·概念·接口 | **可**（按仓库解析；agent 提问时可用目录/文件范围限定上下文）｜推断 |
| **Microsoft GraphRAG** | https://github.com/microsoft/graphrag | MIT | 2026-10-07 / 否；36254★ | Python 库 + CLI | 任意文本语料（可把代码转文本后喂入） | 实体图 + 社区摘要 + 全局/局部查询答案 | **间接**（适合"跨模块的全局业务叙述"生成） | 中—高（索引成本高，token 消耗大） | 低：MIT。**成本风险 > 合规风险** | 流程·概念 | **可**（索引前可按语料切分；查询有 local/global 两种范围）｜推断 |
| **Neo4j LLM Graph Builder** | https://github.com/neo4j-labs/llm-graph-builder | Apache-2.0 | 2026-10-06 / 否；5276★ | Python + React，Docker | 非结构化文档（PDF/网页/文本），也支持从代码文本抽取 | Neo4j 知识图谱 + 图 RAG 问答 | **间接**（更适合把"业务文档 + 代码注释 + 接口文档"融合成图谱，而非解析字节码） | 中 | 低—中：Apache-2.0；同样有数据出域与模型合规问题 | 流程·概念 | **可**（按上传文档/片段处理）｜推断 |
| **codebase-reverse** | https://github.com/sharptoolbox/codebase-reverse | MIT | 2026-08-30 / 否；99★ | Agent skill（Markdown 指令集 + 脚本），面向 Claude Code / Codex 类 agent；README 自述"深度定制于 Java Web 与 Java 微服务（Spring Boot/Cloud）" | **存量源码** | README 自述输出：功能 / 实现 / 架构 / 接口 / 对象 / 组件 / **数据库**完整元模型 | **间接偏直接**（本次盘点中与"存量 Java → 结构化业务元模型"目标最贴合的公开件） | 中（依赖 agent 运行时与模型额度） | 低：MIT。**风险**：star 数低、单人维护、输出质量无公开基准 → 本项目对其能力判断为 **C 级证据，必须实测** | 流程·规则·概念·数据·接口 | **可**（skill 由提示词驱动，可指定目标模块/功能）｜推断 |
| **Continue** | https://github.com/continuedev/continue | Apache-2.0 | 2026-10-08 / 否；36152★ | TypeScript；IDE 插件（VS Code / JetBrains）+ CLI + Hub | 本地代码库（`@codebase` 索引） | IDE 内代码问答、自定义 agent、rules 约束 | **间接** | 低—中 | **低**：Apache-2.0，且**可接本地/私有模型**——金融场景数据不出域的关键选项 | 流程·规则·概念 | **可**（`@codebase` 之外可用 `@file`/`@folder` 限定上下文）｜推断 |
| **Repomix** | https://github.com/yamadashy/repomix | MIT | 2026-10-03 / 否；28745★ | TypeScript CLI（另提供 Web 版） | 本地或远程仓库 | XML / Markdown / 纯文本打包 + token 统计 + 压缩 | **间接**（LLM 上下文打包器；中型 Java 项目会超窗口，需先切片） | 极低 | 低：MIT | 不直接产出（LLM 上下文打包前置件） | **可**（include/ignore 路径过滤 + token 统计）｜推断 |
| **gitingest** | https://github.com/coderamp-labs/gitingest | MIT | 2026-10-08 / 否；15867★ | Python CLI / Web（把 GitHub URL 的 `hub` 换成 `ingest`） | 任意 Git 仓库 | 单个 LLM 友好的 Markdown 文本（含目录树） | **间接** | 极低 | 低：MIT | 不直接产出（LLM 上下文打包前置件） | **可**（include/exclude 模式参数）｜推断 |

### F 类：数据库 / 配置 / 工作流引擎驱动的流程还原（11 条）

| 名称 | URL | 许可证 | 活跃度 | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **SchemaSpy** | https://github.com/schemaspy/schemaspy | LGPL-3.0 | 2026-03-05 / 否；3730★ | Java 独立 jar + JDBC 驱动 | **可连接的数据库**（或 JDBC 元数据） | HTML 站点：表/列清单、ER 图（Graphviz）、外键关系、注释、孤儿表 | **间接偏直接**（金融老系统的业务实体与状态字段大量沉淀在 DB，ER + 列注释是业务模型的第一手证据） | 低（一条命令） | 低—中：LGPL-3.0；以独立进程调用（不改其代码）通常可接受 | 数据·概念 | **可**（`-schemas`/`-catalogs` 与表包含-排除参数）｜推断 |
| **Atlas** | https://github.com/ariga/atlas | Apache-2.0 | 2026-10-08 / 否；8765★ | Go CLI（单二进制） | 数据库连接，或 HCL / SQL schema 定义 | schema-as-code、版本化 diff、迁移计划、ER 图 | **间接**（"schema 的历史 diff = 业务规则演进史"，可时间轴化呈现给客户） | 低—中 | 低：Apache-2.0（部分平台功能为商业） | 数据 | **可**（按 schema/表限定 inspect 与 diff 范围）｜推断 |
| **Flyway** | https://github.com/flyway/flyway | Apache-2.0 | 2026-10-08 / 否；10127★（Redgate） | Java CLI / Maven / Gradle | 版本化 SQL 迁移脚本 + 数据库 | 迁移历史、`flyway info` 报表 | **间接**（带时间戳与作者的 schema 演进证据） | 低 | 低—中：Apache-2.0（社区版）；Teams/Enterprise 功能为商业 | 数据 | **不适用**（按迁移脚本版本推进，非按业务场景切片） |
| **Camunda Modeler** | https://github.com/camunda/camunda-modeler | MIT | 2026-10-07 / 否；1722★ | Electron 桌面应用（基于 bpmn-js） | 手工建模，或导入 BPMN 2.0 XML / DMN / Forms | BPMN / DMN 图，可导出 XML / PNG / SVG | **间接**（是"最终交付物格式"的标准编辑器，**不是发现工具**） | 极低 | 低：MIT。**注意**：Camunda 7 Community Edition 已于 **2025-10 生命周期终止**；Camunda 8 为 source-available（非 OSI） | 流程 | **可**（一次打开一份 BPMN 文件）｜直证 |
| **bpmn-js** | https://github.com/bpmn-io/bpmn-js | GitHub API 返回 **NOASSERTION / "Other"**：使用 **bpmn.io 自定义许可**（非 OSI，含署名义务，见 https://bpmn.io/license/） | 2026-10-05 / 否；9686★ | JavaScript 库，npm | BPMN 2.0 XML | 浏览器内 BPMN 渲染 / 编辑器 | **间接**（把逆向出的流程嵌到客户可交互页面里） | 中 | **中**：自定义许可，**署名义务须写进客户交付物**；商用前需法务确认条款 | 流程 | **可**（渲染传入的单份 XML）｜直证 |
| **Flowable** | https://github.com/flowable/flowable-engine | Apache-2.0 | 2026-10-07 / 否；9574★ | Java / Spring Boot，Maven | BPMN / CMMN / DMN 定义（XML）+ 运行时数据库 | 流程定义、流程实例与历史表（`ACT_HI_*`）、可视化 Modeler（商业版） | **直接**（**若目标系统已用 Flowable / Activiti，流程定义与历史实例可直接导出为权威业务流程**——这是七类中唯一的"直接"路径之一） | 中 | 低：Apache-2.0。前提是目标系统确实用了该引擎（需先勘察） | 流程·规则·数据 | **可**（按流程定义 key 查询部署与历史实例）｜推断 |
| **Activiti** | https://github.com/Activiti/Activiti | Apache-2.0 | 2026-10-08 / 否；10543★ | Java / Spring Boot，Maven | BPMN 2.0 XML + 运行时数据库（同为 `ACT_*` 表族） | 流程定义、流程实例与历史表 | **直接**（同上；国内金融存量系统中 Activiti 5/6 装机量大，勘察优先级高） | 中 | 低：Apache-2.0 | 流程·规则·数据 | **可**（按流程定义 key 查询部署与历史实例）｜推断 |
| **Apache KIE / Drools** | https://github.com/apache/incubator-kie-drools | Apache-2.0 | 2026-10-07 / 否；6333★（Apache 孵化中） | Java，Maven | DRL 规则文件 / 决策表 / DMN | 规则清单、规则命中审计（可配置）、DMN 决策模型 | **直接**（**若系统用 Drools，业务规则本身就是可读的流程/决策证据**，可直接转成决策表交付） | 中 | 低：Apache-2.0。**注意**孵化项目命名与版本变动（`incubator-kie-*`） | 规则·流程 | **可**（按 KieBase/规则包分组加载）｜推断 |
| **LiteFlow** | https://github.com/dromara/liteflow | Apache-2.0 | 2026-09-21 / 否；3879★（Dromara 社区） | Java，Spring Boot 集成 | **编排规则**（EL 表达式 / XML / YAML / 数据库存储） | 组件编排链路（EL 表达式即"流程定义"），规则可热更新 | **直接**（国内金融/电商系统常见；若目标系统用了 LiteFlow，编排表达式就是业务流程） | 低—中 | 低：Apache-2.0 | 流程·规则 | **可**（按 chain ID 执行指定编排）｜推断 |
| **Spring Statemachine** | https://github.com/spring-projects/spring-statemachine | Apache-2.0 | **archived=true**，最后推送 2026-07-05；1664★；homepage 已指向 `spring-attic.github.io/spring-statemachine/`（`spring-attic` 镜像同为 archived） | Java / Spring Boot | 状态机配置（Java Config 或 UML 状态图导入）+ 可选持久化 | 状态 / 事件 / 转移 / 守卫定义（可从配置直接读出状态机） | **直接**（若系统用状态机建模业务状态，如账户/贷款/理赔状态流转） | 低—中 | 低：Apache-2.0。**风险**：项目**已归档并转入 Spring Attic**，不宜作为新方案的技术底座 | 流程·规则 | **可**（按状态机 ID 配置与运行）｜推断 |
| **mybatis-mysql-table-parser** | https://github.com/Adrninistrator/mybatis-mysql-table-parser | Apache-2.0 | 2025-07-17 / 否；**仅 4★** | Java 库 | **MyBatis XML 映射文件** | 解析出 XML 中涉及的数据库表名（支持 MySQL） | **间接偏直接**（打通"Java 方法 → MyBatis statement → 表"的关键一环，正是金融 Java 系统最常见的持久层形态） | 低 | 低：Apache-2.0。**风险**：star 数极低、更新频率低、仅覆盖 MyBatis+MySQL，覆盖度需实测 | 数据 | **可**（按 XML 文件/目录解析）｜推断 |

### G 类：遗留系统逆向工程方法论与案例（4 条）

| 名称 | URL | 许可证 | 活跃度 | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **Eclipse MoDisco** | https://github.com/eclipse-modisco/org.eclipse.modisco | EPL-2.0 | **archived=true**，最后推送 2026-03-06；2★；Eclipse 基金会 **2026-07-14** 发布项目归档公告 | Java / Eclipse 插件栈，Maven | Java 源码、字节码、数据库、部署描述符、POM | **KDM**（OMG 知识发现元模型）、UML、gastm 图；可导出 XMI 供 ATL/EMF 转换 | **需二开**（学术上最正统的"模型驱动逆向工程 MDRE"工业级参考实现，其 KDM→业务视图的转换思路是公开可借鉴的最完整范式） | 高（Eclipse 插件栈 + KDM 学习成本） | 中：EPL-2.0；**已归档**是硬伤，只能当范式参考，不能当生产件 | 流程·概念·数据·接口 | **可**（discoverer 按项目/资源范围运行）｜推断（项目已归档） |
| **awesome-legacy-systems** | https://github.com/feststelltaste/awesome-legacy-systems | CC0-1.0 | 2025-12-08 / 否；185★ | 链接清单（Markdown），含 "Reverse Engineering Tools for Legacy Code"、"Legacy Software Modernisation" 等分节 | 无 | 方法论与工具索引 | **间接**（导航入口，用于查漏本报告未覆盖的长尾） | 极低 | **低**：CC0-1.0（公有领域奉献） | 不直接产出（方法论索引） | **不适用**（清单） |
| **awesome-agentic-software-modernization** | https://github.com/feststelltaste/awesome-agentic-software-modernization | GitHub API 返回 **NOASSERTION / "Other"** → **待回源** | 2026-09-15 / 否；47★ | 链接清单：AI/agentic 现代化（代码理解、重构 agent、遗留系统 AI 模式、AI 辅助文档与知识发现） | 无 | 方法论索引（**与本项目 LLM 路线最相关的一份公开清单**） | **间接** | 极低 | 中：许可证非标准，作为交付物引用前需澄清 | 不直接产出（方法论索引） | **不适用**（清单） |
| **awesome-legacy-code** | https://github.com/legacycoderocks/awesome-legacy-code | CC0-1.0 | 2025-05-17 / 否；246★ | 清单：**具有公开源码的遗留系统**集合 | 无 | 可复现的"练手样本"清单 | **间接**（解决"拿什么验证工具链"的问题——§16 建议的 PoC 可直接从这里取样，避免首轮就拿客户代码试） | 极低 | **低**：CC0-1.0 | 不直接产出（练手样本清单） | **不适用**（清单） |

### H 类：客户确认与差异管理（差异清单 / 评审会 / 追溯 / 活文档）（12 条）

> 本类为 **patch-01 修订 3 新增**，对应 TSK-45 **v4 AC-05**：实施流程须含独立的「与客户确认业务流程」环节 —— 确认主体 = **客户方业务专家**；**确认对象 = 关键业务流程**（客户人工判断的重点交易与重点场景，研究方不预设界定标准）；确认形式 = **差异清单 + 评审会**；差异项处置 = 确认通过 / 按客户修正 / **标记后续人工处理**。本类候选即该环节的**既有实践与可复用工件**。

| 名称 | URL | 许可证 | 活跃度 | Java 与构建形态 | 输入要求 | 输出物形态 | 反推能力 | 上手成本 | 商用与合规风险 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **bpmn-js-differ** | https://github.com/bpmn-io/bpmn-js-differ | MIT | 2026-08-28 / 否；56★ | JavaScript 库，npm；bpmn-io 官方出品 | **两份 BPMN 2.0 XML**（如"逆向出的版本" vs "客户认定版本"） | 结构化 diff（元素级增删改），可驱动 bpmn-js 做可视化差异渲染 | **间接**（**差异清单的技术载体**：把流程模型的差异机器化，避免人工比对遗漏） | 低—中 | **低**：MIT（注意与 `bpmn-io/bpmn-js` 的自定义许可不同，本库为 MIT） | 流程（差异项载体） | **可**（比对两份指定 BPMN，天然按单条流程）｜直证 |
| **OpenFastTrace** | https://github.com/itsallcode/openfasttrace | GPL-3.0 | 2026-10-08 / 否；198★ | Java CLI + Gradle 插件 + GitHub Action + 语言服务器（JetBrains）；需求以带 ID 的文本/Markdown 编写 | 带 ID 的需求/条目文档（可把每条业务流程、每条差异项写成一个条目） | **追溯矩阵、覆盖率报告、未满足项清单**（HTML/Markdown） | **间接**（**差异项处置状态的落地载体**：每条差异有 ID、状态、链接与覆盖关系，可进 CI 门禁） | 中 | **高**：GPL-3.0；作为客户交付物的一部分需法务评估 | 流程·规则·概念·数据·接口（通用条目/差异项追溯载体，不限资产类型） | **可**（按条目 ID/标签查询与过滤，可只覆盖关键流程条目）｜推断 |
| **Cucumber-JVM** | https://github.com/cucumber/cucumber-jvm | MIT | 2026-10-08 / 否；2836★ | Java，Maven/Gradle；Gherkin `.feature` 文件 | 业务可读的 Gherkin 规格（Given/When/Then）+ Java 步骤实现 | 可执行验收规格、执行报告；**`pending`/`undefined` 步骤天然表达"标记后续人工处理"** | **间接**（把客户确认后的业务流程固化为**业务专家可读且可回归**的规格，是评审会结论的持久载体） | 中 | **低**：MIT | 流程·规则 | **可**（按 tag / feature 文件 / 场景名筛选执行）｜推断 |
| **living-documentation（jboz）** | https://github.com/jboz/living-documentation | Apache-2.0 | 2026-01-26 / 否；48★ | Java，Maven 插件；README 自述"从 Java 项目生成活文档" | Java 项目源码/构建 | 从代码生成的文档（图 + 说明），随代码更新 | **间接**（让确认结果"活"在代码库里，避免一次性签字后文档失效） | 中 | **低**：Apache-2.0；star 数低（48），成熟度需实测 | 流程·概念·接口 | **部分**（按 Java 项目生成，未见场景级切片）｜推断 |
| **cucumber-living-documentation-plugin** | https://github.com/jenkinsci/cucumber-living-documentation-plugin | MIT | 2023-06-13 / 否；15★ | Jenkins 插件 | Cucumber 执行报告 | Jenkins 内的活文档站点 | **间接** | 低—中 | **低**：MIT；**风险**：最后推送 2023-06，活跃度低 | 流程·规则 | **可**（按 Jenkins job / 报告范围）｜推断 |
| **awesome-living-documentation** | https://github.com/LivingDocumentation/awesome-living-documentation | GitHub API 返回 **NOASSERTION** → **待回源** | 2022-07-30 / 否；108★ | 链接清单（Markdown） | 无 | 活文档实践与工具索引 | **间接**（方法论索引） | 极低 | 中：许可证未检出 | 不直接产出（方法论索引） | **不适用**（清单） |
| **ddd-crew/como-prep-canvas** | https://github.com/ddd-crew/como-prep-canvas | CC-BY-SA-4.0 | 2026-08-01 / 否；35★ | Markdown 画布模板（非代码）；README 自述"Collaborative Modeling Workshop Preparation Canvas … support facilitators when preparing for workshops" | 工作坊目标与参与者信息 | **协作建模工作坊准备画布**（参与者、目标、前置材料、议程） | **间接**（**直接对应"评审会准备"这一实施步骤**，是公开可得的工作坊组织工件） | 极低 | 低—中：CC-BY-SA-4.0（衍生需同许可共享） | 不直接产出（评审会/工作坊组织工件） | **可**（画布按单场工作坊目标填写）｜直证 |
| **ddd-crew/eventstorming-glossary-cheat-sheet** | https://github.com/ddd-crew/eventstorming-glossary-cheat-sheet | CC-BY-SA-4.0 | 2026-09-13 / 否；987★ | Markdown（非代码） | 无 | EventStorming 术语表与做法速查（含便利贴颜色语义、big picture / design level / software design 三阶段） | **间接**（**与业务专家共创并当场暴露差异**的成熟工作坊方法；争议点即差异清单来源） | 低 | 低—中：CC-BY-SA-4.0 | 流程·概念·规则 | **可**（EventStorming 本身按业务域/流程分场）｜推断 |
| **ddd-crew/virtual-modelling-templates** | https://github.com/ddd-crew/virtual-modelling-templates | CC-BY-SA-4.0 | 2026-08-01 / 否；84★ | Miro 等远程协作模板 | 远程评审参与者 | 远程协作建模画布模板 | **间接**（**远程评审会**的既有实践，适合客户异地专家参与） | 极低 | 低—中：CC-BY-SA-4.0 | 不直接产出（远程评审会组织工件） | **可**（模板按场次使用）｜推断 |
| **ddd-crew/context-mapping** | https://github.com/ddd-crew/context-mapping | CC-BY-SA-4.0 | 2026-08-23 / 否；1864★ | Markdown + 模板 | 上下文清单 | 上下文映射图与关系模式（合作/防腐层/客户-供应商等） | **间接**（评审会上确认"模块间业务关系"的标准表述法） | 低 | 低—中：CC-BY-SA-4.0 | 概念·接口 | **可**（按选定上下文绘制）｜推断 |
| **domainstorytelling.org（WPS）** | https://github.com/WPS/domainstorytelling.org | CC-BY-4.0 | 2026-10-06 / 否；7★ | 方法官网源码（配套工具见 D 类 `WPS/egon.io`） | 无 | 领域故事方法说明与示例 | **间接**（**"讲述—回放—修正"循环本身就是逐句确认机制**，差异在讲述中即时暴露并处置） | 极低 | **低**：CC-BY-4.0（仅需署名，比 SA 宽松，客户交付更友好） | 流程·概念 | **可**（一次一个领域故事）｜直证 |
| **mikado-method（agent skill）** | https://github.com/chaabani-anis/mikado-method | GitHub API **未检出 LICENSE** → **待回源** | 2026-06-30 / 否；5★ | Agent skill（Markdown 指令集）；自述"Skill Mikado Method for agentic legacy refactoring" | 目标变更 + 代码库 | Mikado 图（前置条件 → 步骤序列） | **间接**（**增量改造的实施顺序方法**；本报告仅记录其存在，不做排序结论） | 低 | 中：无许可证；star 数极低（5），属 **C 级**线索 | 流程 | **可**（按目标变更展开前置条件图）｜推断 |

### 次级候选（16 条，已核验，因定位重叠或成熟度不足降级为线索；许可证与活跃度同样为 2026-10-08 GitHub API 取值）

| 名称 | URL | 许可证 | 最后推送 / archived | 降级原因 | 可输出业务资产类型 | 切片输入能力（能否把输入限定到客户指定的流程/场景集合） |
|---|---|---|---|---|---|---|
| Sourcetrail（原仓） | https://github.com/CoatiSoftware/Sourcetrail | GPL-3.0 | 2021-12-13 / **archived=true**（16475★） | 已归档；交互式源码浏览器，人工代码考古效率高但不产出流程模型 | 流程·概念·接口 | **可**（按符号搜索聚焦到指定类/方法）｜推断 |
| Sourcetrail（社区分叉，活跃） | https://github.com/petermost/Sourcetrail | GPL-3.0 | 2026-10-02 / 否（761★，homepage Sourcetrail.de） | GPL-3.0 + 桌面 GUI，难以流水线化；作为**人工勘察**辅助工具备选 | 流程·概念·接口 | **可**（同上）｜推断 |
| SonarQube | https://github.com/SonarSource/sonarqube | LGPL-3.0 | 2026-10-06 / 否（11050★） | 质量/技术债维度，与业务流程反推关系弱；Community Build 与商业版差异大 | 概念（质量维度，间接） | **部分**（按项目/模块分析，非按业务场景）｜推断 |
| CodeCharta | https://github.com/MaibornWolff/codecharta | BSD-3-Clause | 2026-10-07 / 否（544★，homepage codecharta.com） | 3D 代码城市可视化，适合**向客户讲清系统全貌**的沟通工件；有 jQAssistant 插件 | 概念 | **可**（按输入文件/路径过滤生成地图）｜推断 |
| sqlglot | https://github.com/tobymao/sqlglot | MIT | 2026-10-08 / 否（9665★） | Python SQL 解析器，支持**列级血缘**；把 MyBatis/JDBC 里的 SQL 解析成"表.字段←表.字段"，是 C/F 类之间的数据流证据件 | 数据·规则 | **可**（按传入 SQL 逐条处理）｜直证 |
| sqllineage | https://github.com/reata/sqllineage | MIT | 2026-10-04 / 否（1679★） | 基于 sqlfluff 的表级/列级血缘工具（CLI + Web UI）；与 sqlglot 能力重叠 | 数据 | **可**（按文件或单条 SQL 处理）｜推断 |
| Liquibase | https://github.com/liquibase/liquibase | GitHub API **NOASSERTION**（Liquibase Open Source License，基于 Apache-2.0 附加条款）→ **待回源** | 2026-10-08 / 否（5621★） | 与 Flyway 能力重叠；changelog 同样是带时间戳的业务演进证据 | 数据 | **可**（按 context/label 过滤执行）｜推断 |
| aider | https://github.com/Aider-AI/aider | Apache-2.0 | 2026-05-22 / 否（49421★） | 核心相关能力是 **repo map**（基于 tree-sitter 的仓库结构图，含 Java）；与 Continue 定位重叠 | 概念·接口 | **可**（repo map 之外可显式 `/add` 指定文件）｜推断 |
| ddd-crew/bounded-context-canvas | https://github.com/ddd-crew/bounded-context-canvas | CC-BY-SA-4.0 | 2026-08-23 / 否（2065★） | 限界上下文文档模板，与 D 类已列条目同源同许可 | 概念 | **可**（按单个限界上下文填写）｜直证 |
| ddd-crew/ai-ddd-prompts-and-rules | https://github.com/ddd-crew/ai-ddd-prompts-and-rules | CC-BY-SA-4.0 | 2026-08-02 / 否（37★） | 给 LLM 加"DDD 视角"约束的提示词集，可降低业务语义幻觉；是 E 类的**低成本增强件** | 概念·规则 | **可**（按主题选用提示词）｜推断 |
| awesome-domain-storytelling | https://github.com/hofstef/awesome-domain-storytelling | GitHub API **未检出 LICENSE** → **待回源** | 2024-07-12 / **archived=true**（203★） | 已归档的领域故事资料清单；其工具入口已在 D 类（Egon.io） | 不直接产出（方法论索引） | **不适用**（清单） |
| archguard/codedb | https://github.com/archguard/codedb | MIT | 2023-12-09 / 否（43★） | "代码数据库 + 架构适度度函数 + 依赖分析引擎"，理念与本项目高度契合但更新已停滞 | 概念·数据·接口 | **可**（按查询 DSL 限定范围）｜推断 |
| archguard/scanner | https://github.com/archguard/scanner | MIT | 2022-05-25 / **archived=true**（28★） | ArchGuard 的扫描器（基于 Chapi，支持 Java/Kotlin/TS/Go + 字节码 + Jacoco）；已归档，是 ArchGuard 路线的**明确风险点** | 概念·数据·接口 | **可**（按仓库/路径扫描）｜推断 |
| uml-sequence-diagram-drawio | https://github.com/Adrninistrator/uml-sequence-diagram-drawio | Apache-2.0 | 2025-10-24 / 否（37★） | `gen-java-code-uml-sequence-diagram` 的配套渲染器（文本→draw.io 时序图） | 流程·接口 | **可**（按输入文本文件渲染单图）｜直证 |
| PlantUML | https://github.com/plantuml/plantuml | LGPL-3.0 | 2026-10-06 / 否（13356★） | 标准输出层：把逆向结果画成客户可评审的时序图/活动图/状态图；进程外调用（jar 渲染）风险低 | 流程·概念·接口（渲染层） | **可**（按输入文本渲染单图）｜直证 |
| Eclipse 项目归档公告页 | https://www.eclipse.org/projects/news/ | —（Eclipse 基金会公告页） | Web 检索命中「Modisco · Archived on Jul 14, 2026」；该路径在本环境返回 **404**（`eclipse.org` 根路径 200），**待回源** | 方法论退场的一手证据；**归档状态本身已由 GitHub API `archived=true` 直证（A 级）**，公告日期为 B 级 | 不直接产出（证据页） | **不适用**（证据页） |

### 附：商业与非 GitHub 参照（不计入候选数，仅作地面对照）

| 名称 | URL | 性质 | 证据 | 对本项目的意义 | 合规风险 |
|---|---|---|---|---|---|
| vFunction | https://vfunction.com/modernization-platform/ | 商业平台，**无公开开源仓库** | 官方产品页与博客（2025–2026）；该深路径在本环境返回 **404**（`vfunction.com` 根路径 200），**待回源**；**B 级** | 宣称对 Java/.NET 单体做运行时+静态分析、生成技术架构视图并支持分阶段拆解——**功能定位与本项目目标最接近的商业产品** | 采购与数据出境；无公开定价（**待回源**） |
| Moderne（OpenRewrite 商业平台） | https://moderne.io/case-studies （**HTTP 200 已验证**）｜ https://docs.moderne.io/user-guide/modernize-with-confidence/ （本环境 **404**，`docs.moderne.io` 根路径 200，**待回源**） | 商业平台 + OSS 引擎 | 案例页 A 级可达、文档页待回源；综合 **B 级** | 公开了多份大型 Java 现代化案例（含合规驱动的批量改造），可作"实施流程"参照 | 商业采购；OSS 引擎（OpenRewrite）可单独使用 |
| Celonis Process Intelligence | https://celonis.com/products/process-intelligence/ | 商业流程挖掘平台 | 官方产品页（宣称已接入 SAP/Oracle 等）；该深路径在本环境返回 **404**（`celonis.com` 根路径 200），**待回源**；**B 级** | A 类能力的商业替代，**无开源实现** | 商业采购 + 数据上云合规 |
| CodeScene | https://codescene.com/blog/behavioral-code-analysis-explained | 商业行为代码分析 | 官方博客；该深路径在本环境返回 **404**（`codescene.com` 根路径 200），**待回源**；**B 级**。其 OSS 前身即 `adamtornhill/code-maat` | 变更耦合/热点分析的商业化形态 | 商业采购 |
| Camunda 7 CE EOL 公告 | https://camunda.com/blog/2025/10/camunda-7-community-edition-reached-end-of-life/ ｜ https://docs.camunda.org/manual/7.24/upgrading-guide/other-changes/7.24/ | 官方公告 | 2025-10；两个 URL 在本环境分别返回 **404** 与**连接失败**（`camunda.com` 根路径 200），**待回源**；**B 级**（EOL 事实本身有多处独立来源） | 直接影响"用 Camunda 承接逆向出的 BPMN"这条路线的可持续性 | Camunda 8 为 source-available，需法务评估 |
| Sourcegraph Cody（已退场） | https://github.com/sourcegraph/cody-public-snapshot | 已归档的 OSS | GitHub 页面显示归档于 **2025-08-01**，**A 级** | E 类路线"退场风险"的实证样本 | — |

---

## 6. 三类产物映射（对应 v4 AC-04：工具 / 方案·方法论 / 实施流程，每类 ≥3 条）

> AC-04 要求交付物**分别**给出「工具」「方案／方法论」「实施流程」三类产物，每类 ≥3 条候选，且每条含「输入要求」与「业务流程反推能力评级」两字段。下表把 §5 的候选按产物类型归位（同一候选可跨类），并**原样 echoing** 这两个字段。**本表不做推荐、不做排序**（NG-04）。

### 6.1 工具类（可执行软件：13 行，覆盖 60+ 件具体工具）

| 名称 | 产物类型 | 输入要求 | 反推能力评级 | 可输出业务资产 | 详见 |
|---|---|---|---|---|---|
| PM4Py | 工具 | 事件日志（XES/CSV/DataFrame） | 间接 | 流程 | §5-A |
| OpenTelemetry Java Instrumentation | 工具 | 运行中的 JVM + 目标环境 | 间接 | 流程·接口·数据 | §5-A |
| Soot / SootUp / WALA | 工具（3 件） | Java 字节码（+ 可选源码） | 需二开 | 流程·规则·概念·接口 | §5-B |
| JavaParser / Spoon / OpenRewrite | 工具（3 件） | Java 源码（OpenRewrite 需可构建工程） | 需二开 | 流程·规则·概念·数据·接口 | §5-B |
| jQAssistant | 工具 | 字节码/源码/pom/XML/Git/DB schema | 间接 | 流程·概念·数据·接口 | §5-B |
| ArchGuard / Chapi / Coca | 工具（3 件） | 源码仓库（+ Git 历史 / API / DB schema） | 间接（Chapi 为需二开） | 概念·数据·接口 | §5-B |
| Joern / CodeQL / Semgrep / Tai-e / FlowDroid | 工具（5 件） | 源码或字节码（CodeQL 需可编译） | 间接 / 需二开 | 流程·规则·数据·接口 | §5-C |
| java-callgraph2 / java-all-call-graph / java-all-call-graph-server / gen-java-code-uml-sequence-diagram / gousiosg-java-callgraph | 工具（5 件） | 编译产物 class/jar/war/jmod（+ 可选源码、MyBatis XML） | 间接 | 流程·规则·数据·接口 | §5-C |
| Spring Modulith / jMolecules / Structurizr / Context Mapper DSL | 工具（4 件） | Spring Boot 应用 / 注解 / DSL 文本 | 间接 / 需二开 | 流程·概念·接口 | §5-D |
| SchemaSpy / Atlas / Flyway / mybatis-mysql-table-parser / sqlglot / sqllineage | 工具（6 件） | 数据库连接 / schema 定义 / 迁移脚本 / MyBatis XML / SQL | 间接（SchemaSpy 为间接偏直接） | 数据·概念·规则 | §5-F、次级候选 |
| Flowable / Activiti / Drools / LiteFlow / Spring Statemachine / Camunda Modeler / bpmn-js | 工具（7 件） | BPMN XML / DRL / EL 规则 / 状态机配置 / 运行时 DB | **直接**（前 5 件，前提是系统已用该引擎）／间接（后 2 件） | 流程·规则·数据·接口 | §5-F |
| Blarify / Potpie / GraphRAG / llm-graph-builder / Continue / codebase-reverse / Repomix / gitingest | 工具（8 件） | 代码仓库（+ Neo4j / LLM API 或本地模型） | 间接（codebase-reverse 为间接偏直接） | 流程·规则·概念·数据·接口 | §5-E |
| bpmn-js-differ / OpenFastTrace / Cucumber-JVM / jboz-living-documentation / cucumber-living-documentation-plugin | 工具（5 件） | 两份 BPMN XML / 带 ID 条目文档 / Gherkin 规格 / Java 项目 / Cucumber 报告 | 间接 | 流程·规则·概念·接口 | §5-H |

### 6.2 方案／方法论类（非可执行软件，10 条）

| 名称 | 产物类型 | 输入要求 | 反推能力评级 | 可输出业务资产 | 详见 |
|---|---|---|---|---|---|
| Eclipse MoDisco（模型驱动逆向工程 MDRE 范式：代码→KDM→业务视图） | 方案/方法论 | Java 源码/字节码/DB/部署描述符/POM | 需二开 | 流程·概念·数据·接口 | §5-G |
| FIBO（金融业务本体，作为术语对齐锚点） | 方案/方法论 | 无（目标词汇表） | 间接 | 概念 | §5-D |
| DDD Starter Modelling Process（子域划分与领域愿景步骤） | 方案/方法论 | 业务专家访谈 + 代码盘点结果 | 间接 | 流程·概念 | §5-D |
| Domain Message Flow Modelling（上下文间命令/事件/查询流建模法） | 方案/方法论 | 命令/事件/查询清单 | 间接偏直接 | 流程·概念·接口 | §5-D |
| Domain Storytelling（讲述—回放—修正循环） | 方案/方法论 | 业务专家口述 | 间接 | 流程·概念 | §5-D、§5-H |
| EventStorming（便利贴工作坊，三阶段：big picture / design level / software design） | 方案/方法论 | 业务专家 +  facilitator | 间接 | 流程·概念·规则 | §5-H |
| Example Mapping（Rules / Examples / Questions 卡片法） | 方案/方法论 | 业务专家 + 一条待确认流程 | 间接 | 流程·规则 | §9.4 |
| awesome-legacy-systems / awesome-agentic-software-modernization / awesome-legacy-code / awesome-living-documentation（4 份索引清单） | 方案/方法论 | 无 | 间接（导航） | 不直接产出 | §5-G、§5-H |
| IEEE 1028-2008《Software Reviews and Audits》（评审类型、进入/退出准则、异常处置） | 方案/方法论（**标准**） | 待评审工件 + 评审角色 | 间接 | 流程·规则 | §9.3 |
| Strangler Fig（绞杀者模式，增量替换节奏） / Mikado Method（前置条件图驱动的增量改造顺序） | 方案/方法论（2 项） | 目标变更 + 现有系统认知 | 间接 | 流程 | §9.5 |

### 6.3 实施流程类（可复用的步骤/工件/角色编排，6 条）

> 「实施流程」在本报告中指**可被复用的步骤序列 + 角色分工 + 工件模板**，而非某段代码。每条均给出输入要求与反推能力评级。

| # | 实施流程候选 | 输入要求 | 反推能力评级 | 覆盖的环节 | 既有实践来源（可溯源） |
|---|---|---|---|---|---|
| P-01 | **工作坊式业务流程共创与差异暴露**：准备画布 → 业务专家讲述 → 现场建模 → 争议点即差异项 | 业务专家时间、 facilitator、代码盘点结果 | 间接 | 逆向结果的**首次确认** | `ddd-crew/como-prep-canvas`（准备画布）、`ddd-crew/eventstorming-glossary-cheat-sheet`（EventStorming）、`WPS/domainstorytelling.org` + `WPS/egon.io`（Domain Storytelling）、`ddd-crew/virtual-modelling-templates`（远程评审） |
| P-02 | **机器化差异清单生成（模型 vs 模型）**：逆向出的 BPMN ⟷ 客户认定版 BPMN 做元素级 diff → 差异清单 | 两份 BPMN 2.0 XML | 间接偏直接 | **差异清单**产出 | `bpmn-io/bpmn-js-differ`（MIT，56★，2026-08-28）；ProM 的模型对比插件（GPL，promtools.org） |
| P-03 | **机器化差异清单生成（模型 vs 事实）**：参考流程模型 ⟷ 真实事件日志做一致性检查 → 逐 trace 偏差 + fitness 分数 | 参考流程模型 + 事件日志 | 间接偏直接 | **差异清单**产出（含定量偏差） | PM4Py conformance checking：token-based replay 与 alignments（官方文档 `process-intelligence-solutions/pm4py` 的 "Conformance Checking" 章；`pm4py.fit.fraunhofer.de/token-replay-pm4py.html`、`/alignments-pm4py.html` — 该域名在本环境连接失败，**待回源**）；ProM 同类插件 |
| P-04 | **差异项处置与追溯闭环**：每条差异有 ID、状态（确认通过／按客户修正／标记后续人工处理）、链接到源码证据与评审结论；覆盖率与未满足项进 CI 门禁 | 带 ID 的差异条目文档 | 间接 | **处置 + 追溯** | `itsallcode/openfasttrace`（GPL-3.0，198★，2026-10-08；输出追溯矩阵、覆盖率、未满足项清单）；IEEE 1028-2008 的 anomaly/defect 处置与退出准则；`cucumber/cucumber-jvm` 的 `pending`/`undefined` 步骤天然表达"标记后续人工处理" |
| P-05 | **评审会（技术评审 / 走查 / 检视）**：确定评审类型 → 检查进入准则 → 会前发料 → 会中逐条过差异清单 → 记录处置 → 检查退出准则 | 差异清单 + 待评审流程模型 + 客户业务专家 | 间接 | **评审会** | IEEE 1028-2008《Standard for Software Reviews and Audits》（定义 management review / technical review / walkthrough / inspection / audit 五类，含进入与退出准则、异常记录与处置）；`ddd-crew/virtual-modelling-templates`（远程形式） |
| P-06 | **确认结果固化与防失效**：把确认后的流程写成业务可读且可执行的规格，并生成随代码更新的活文档 | 已确认的流程 + Java 项目 | 间接 | **确认结果持久化** | `cucumber/cucumber-jvm`（Gherkin 规格，MIT）、`jboz/living-documentation`（从 Java 项目生成活文档，Apache-2.0）、`jenkinsci/cucumber-living-documentation-plugin`（Jenkins 活文档站点，MIT）、Example Mapping（把规则/示例卡片转成 Gherkin） |

**AC-04 自检**：工具类 **13 行（覆盖 60+ 件具体工具）** ≥3 ✅｜方案/方法论类 **10 条** ≥3 ✅｜实施流程类 **6 条** ≥3 ✅｜每条均含「输入要求」与「反推能力评级」两字段 ✅

---

### 6.4 AC-06「关键业务流程清晰性」的五字段供给地图

> **诚实声明（范围边界）**：v4 **AC-06** 要求「对关键业务流程，每条以统一结构描述（触发条件／参与模块／数据实体／业务规则／异常分支 ≥5 字段）并标注源码证据位置」。**本任务卡（TSK-46）无法直接满足 AC-06**：本研究是**只读的工具与方法盘点**，既未获得目标系统源码，也不产出任何一条具体业务流程条目。本节能做的是给出**「这 5 个字段各自可由哪些候选供给、以什么形态落到源码证据位置」**的地面映射，供后续实施阶段直接取用。AC-06 的实际满足需在拿到目标系统后由实施阶段交付。

| v4 AC-06 字段 | 可由哪些候选供给（详见 §5） | 供给形态 | 「源码证据位置」如何标注 |
|---|---|---|---|
| **① 触发条件** | `java-all-call-graph`（入口方法 + 方法执行顺序的**条件**分支）、Joern（CPG 控制流）、Soot/SootUp/WALA（CFG）、Flowable/Activiti（BPMN 网关条件）、Drools（规则条件）、LiteFlow（EL 条件）、Spring Statemachine（事件/守卫） | 入口方法签名 + 条件表达式 + 所在类/方法/行 | 类全名 + 方法名 + 行号（JavaParser/Spoon/OpenRewrite LST 均可给出精确位置） |
| **② 参与模块** | Spring Modulith（模块与事件注册表）、ArchGuard/Chapi（模块与依赖）、jQAssistant（Neo4j 中的包/模块节点）、Structurizr（C4 容器/组件）、Coca（依赖分析） | 模块/包/服务清单 + 模块间关系 | 包路径 / Maven 坐标 / 服务名 |
| **③ 数据实体** | SchemaSpy（ER + 列注释）、`java-all-call-graph`（DB 表与字段）、`mybatis-mysql-table-parser`（MyBatis XML→表）、sqlglot/sqllineage（列级血缘）、Atlas/Flyway（schema 与演进）、Chapi（DataStructure/字段） | 表/字段清单 + 实体关系 + 读写位置 | 表名.列名 + 映射文件路径（MyBatis XML / JPA 注解所在类） |
| **④ 业务规则** | Joern/CodeQL/Tai-e/FlowDroid（数据流与污点：字段从哪来、被谁改写）、Semgrep（规则模式匹配）、OpenRewrite（LST 批量查询，如「所有 `@Transactional` 方法 + 其 SQL」）、Drools（DRL 规则本身）、Spoon（Processor 查询） | 校验/计算/状态流转的判定条件 + 规则命中位置 | 类全名 + 方法名 + 行号；规则文件路径 + 规则 ID（DRL/EL） |
| **⑤ 异常分支** | Joern（CPG 异常边与控制流）、Soot/SootUp（CFG 的异常边）、`java-all-call-graph`（方法执行顺序的分支）、Flowable/Activiti（BPMN 边界事件与补偿）、Cucumber-JVM（Gherkin 的异常场景） | try/catch 与补偿路径、错误码分支、超时/回滚 | 类全名 + 方法名 + 行号；BPMN 元素 ID |
| **（附）源码证据位置的统一载体** | JavaParser / Spoon / OpenRewrite（LST 均带精确 source position）、jQAssistant（Neo4j 节点带 `fileName`/`line` 属性）、Joern（CPG 节点带 `LINE_NUMBER`） | 可直接机器生成的「文件:行号」引用 | — |

**AC-06 判定（本卡）**：**不适用／由后续实施阶段交付**。本报告提供的是该 AC 的**字段供给地面**，不是字段本身。此判定已在 §17.1 如实标注，未虚报达标。

---

---

## 7. 五类业务资产 × 逆向输入矩阵（对应 v4 AC-03 与 patch-01 修订 2）

> AC-03 要求：交付物含**业务流程／业务规则／领域概念／数据资产／接口**五类业务资产，且**每类标注可得它的逆向输入**（源码／字节码／日志／数据库结构）。下表为五类资产各自的"可得性地图"；每条候选的资产归属见 §5 各表第 11 列。

| 业务资产 | 可得它的逆向输入 | 覆盖它的候选（详见 §5） | 公开生态覆盖度 | 关键缺口 |
|---|---|---|---|---|
| **① 业务流程** | **源码**（调用链 + 方法执行顺序：顺序/条件/循环）、**字节码**（调用图）、**日志**（事件日志→流程发现）、**数据库结构**（状态字段 + 迁移史）、**配置**（BPMN XML / EL 编排 / 状态机配置） | java-all-call-graph、gen-java-code-uml-sequence-diagram、Joern、Soot/SootUp/WALA、PM4Py、OTel Java、Flowable/Activiti/LiteFlow/Spring Statemachine、Spring Modulith（事件注册表）、Domain Message Flow Modelling、bpmn-js-differ | **中**：有"技术执行序列"与"已外化流程定义"两条可用路径；**无**端到端"源码→业务流程模型"件 | **G-01**（代码→事件日志无转换器）、**G-02**（无端到端流水线）、**G-09**（无"调用链→合法 BPMN XML"写入端）、**G-10**（跨 50 微服务的流程拼接无公开件） |
| **② 业务规则** | **源码**（条件分支、校验注解、`@Transactional` 边界、DRL/EL 规则文件）、**字节码**（数据流/污点：字段从哪来到哪去、被谁改写）、**数据库结构**（约束、触发器、枚举/状态字典） | Drools（若已用）、Joern、CodeQL、Tai-e、FlowDroid、Semgrep、OpenRewrite（LST 批量查询）、Spoon、sqlglot（SQL 语义→列级血缘） | **中—高**：数据流/污点分析成熟且活跃；规则**定位**能力强 | 无现成金融业务规则库；污点分析需自定义 source/sink；"规则→业务语言表述"仍需 LLM/人工（**G-03**） |
| **③ 领域概念** | **源码**（包名/类名/注解/枚举/常量、DDD 构件注解）、**数据库结构**（表名与列注释、外键关系）、**Git 历史**（变更耦合→隐式概念边界）、**外部本体**（FIBO 作对齐锚点） | Chapi（统一元模型）、jMolecules、Spring Modulith、Context Mapper DSL、FIBO、code-maat（变更耦合）、ArchGuard、CodeCharta、Blarify/Potpie/GraphRAG（概念图谱）、ddd-crew 系列（core-domain-charts / bounded-context-canvas） | **中—高**：结构侧证据充分；DDD 方法论物料丰富 | **G-03**（无"代码→业务术语表"自动映射；无"代码→FIBO 概念"映射件）；对**无注解老代码**基本失效 |
| **④ 数据资产** | **数据库结构**（JDBC 元数据、ER、列注释、孤儿表）、**迁移脚本**（Flyway/Liquibase 版本化 SQL = 带时间戳的演进史）、**源码**（MyBatis XML / JPA 注解 → 表字段映射）、**SQL 文本**（列级血缘） | SchemaSpy、Atlas、Flyway、Liquibase、mybatis-mysql-table-parser、sqlglot、sqllineage、java-all-call-graph（DB 表/字段解析）、jQAssistant（DB schema 插件） | **高**：这是五类中公开生态覆盖最完整的一类，工具成熟且活跃 | **G-08**（"DB 状态字段 + 更新它的代码位置"→状态机无自动合成件）；MyBatis→JPA/Hibernate 覆盖不均（`mybatis-mysql-table-parser` 仅 4★、仅 MySQL） |
| **⑤ 接口** | **源码**（`@RestController`/`@RequestMapping`/RPC 接口/MQ 监听注解、方法签名）、**字节码**（调用图中的 HTTP/MQ 边）、**日志**（OTel span 中的 HTTP/RPC/JDBC 属性）、**契约文件**（OpenAPI/AsyncAPI，若存在） | java-all-call-graph（HTTP/MQ 调用解析）、OTel Java Instrumentation、Joern、Coca（API 分析）、ArchGuard（API 与数据模型）、Structurizr、Spring Modulith、Chapi | **中—高**：单服务内的接口清单可得性高 | **跨服务契约**：50 微服务的服务间接口拓扑需运行时追踪或契约文件，静态单仓分析不足（**G-10**）；无 OpenAPI/AsyncAPI 时接口语义（业务含义）仍缺失 |

**AC-03 自检**：五类资产齐全 ✅｜每类均标注「可得它的逆向输入」（源码／字节码／日志／数据库结构，另补「配置」「契约文件」「Git 历史」「外部本体」四类实际存在的输入源）✅｜每条候选在 §5 各表第 11 列标注可输出的资产类型（多选）✅

**覆盖度结论（不含推荐）**：五类资产的公开生态覆盖度**不均衡** —— **数据资产 > 接口 ≈ 领域概念 > 业务规则 > 业务流程**。业务资产的核心诉求「业务流程」恰是覆盖度最低的一类，且其三个关键缺口（G-01 / G-02 / G-09）都在"从技术事实到流程模型"的转换环节。

---

## 8. 规模适用性评估（对应 patch-01 修订 4：约 20 模块 / 约 50 微服务 / 约 20 万行 Java，金融语境）

> 原任务卡的「中型项目结构口径待回源」项**已解除**：TSK-45 v4 已冻结为「约 20 模块 / 约 50 微服务 / 总代码量约 20 万行」。本节按此口径评估候选适用性。
> **诚实声明**：本项目**未执行任何基准测试**（受本卡「只读调研、不编译第三方代码」约束）。下表中凡无公开基准数据者一律标 **未验证-待回源**，不做推测性断言。

### 8.1 规模口径对选型的三条硬约束

| 约束 | 说明 | 受影响的候选 |
|---|---|---|
| **K-1：约 50 微服务 = 跨进程边界** | 静态调用图工具几乎都是**单构建单元/单仓**视角，跨服务的业务流程**无法**由静态分析得到 | C 类全部（java-callgraph2 输入为 class/jar/war/jmod；Joern `javasrc2cpg` 输入为单一源码目录；Soot/WALA/Tai-e 输入为 classpath）；B 类的 Chapi/Coca/ArchGuard 亦按仓扫描 |
| **K-2：约 20 万行 = LLM 上下文必然溢出** | 20 万行 Java 的 token 量远超任何公开模型的上下文窗口，必须先切片；而"切片策略"本身无现成工具 | E 类全部；Repomix（提供 token 统计，可辅助切片决策）、gitingest 同理 |
| **K-3：金融语境 = 数据不出域 + 审计留痕** | 源码/生产数据通常不得出域；确认过程需可追溯、可审计 | E 类（需本地/私有模型，Continue 支持本地模型）、A 类（OTel trace 含业务字段需脱敏）、F 类（SchemaSpy/Atlas 需 DB 连接授权）、H 类（OpenFastTrace/Cucumber 的工件可留痕，是审计友好项） |

### 8.2 逐类规模适用性

| 类别 | 约 20 模块 | 约 50 微服务 | 约 20 万行 | 依据与限制 |
|---|---|---|---|---|
| **A 流程挖掘** | 不适用（与代码规模无关，取决于事件量） | 不适用 | 不适用 | 输入是事件日志而非代码；50 微服务反而**有利**（若已插桩，跨服务 trace 天然是端到端事件流）。**未验证-待回源**：OTel span → 事件日志的转换代价与 activity 命名策略无公开基准 |
| **B 静态分析/结构恢复** | **可承载**（Spring Modulith 的模块识别粒度与"20 模块"量级匹配；ArchGuard/Chapi 按模块出视图） | **需按仓分别扫描后人工/脚本聚合**；无公开的多仓聚合件（**未验证-待回源**） | **可承载**：Soot/SootUp/WALA/JavaParser/Spoon/OpenRewrite 的公开学术与工业用途均在 10⁵–10⁶ 行量级；**但未找到"20 万行 Java 全量分析的耗时/内存"公开基准 → 未验证-待回源，需 PoC 实测** | Spoon 的 `noclasspath` 模式对"依赖不全的存量工程"更宽容；OpenRewrite 需**工程可构建**，50 微服务意味着 50 次构建 |
| **C 调用图/数据流** | **可承载** | **服务内可承载，跨服务不可**（K-1） | **规模风险最高**：全量调用图在 20 万行量级可达 10⁵–10⁶ 条边；`java-all-call-graph` 文档专门提供"只解析部分包"的用法，说明作者已把"大项目需切片"作为常规场景。**具体上限未验证-待回源** | CodeQL 需**每个微服务都能编译**（50 次建库）；Tai-e/FlowDroid 需完整 classpath |
| **D 领域模型/DDD** | **可承载且量级匹配**（20 模块 ≈ 20 个候选限界上下文的讨论起点） | 天然匹配（微服务边界常即上下文边界） | 不适用（人工/LLM 主导，与行数弱相关） | Spring Modulith 需要应用**已模块化或可加注解**，对无注解老代码失效 |
| **E LLM/agent** | 需按模块切片 | 需按服务切片 | **必须切片**（K-2）；Blarify/Potpie 走"代码→图数据库→按需查询"路线，是目前唯一能规避窗口限制的工程化做法 | **未验证-待回源**：三者在 20 万行 Java 上的索引耗时、Neo4j 规模、召回完整性均无公开数据；Blarify 的 Java 支持官方标注 **beta** |
| **F DB/配置/引擎** | 不适用 | **需逐服务/逐库执行**（50 微服务通常对应多个库/schema），SchemaSpy 与 Atlas 均按数据源运行，聚合视图需人工合并 | 不适用 | 若系统已用 Flowable/Activiti/Drools/LiteFlow，则**与规模无关**，流程定义可直接导出（这是唯一不受 K-1/K-2 约束的"直接"路径） |
| **G 方法论/案例** | 不适用 | 不适用 | 不适用 | 方法论与规模无关；但**公开案例中未见"50 微服务 + 20 万行 + 金融"同口径的可复现案例**（G-05） |
| **H 确认与差异管理** | 不适用 | **评审会需按服务/域分批**（50 微服务不可能一次评审完） | 不适用 | OpenFastTrace / Cucumber / bpmn-js-differ 的工件量与**流程条数**成正比，而非代码行数；分期评审是必然形态 |

### 8.3 规模口径带来的新增缺口

- **G-10（新增）**：**跨约 50 微服务的端到端业务流程拼接，无公开开源件**。静态分析只能给出服务内流程；跨服务需靠 ① OTel 分布式追踪 ② MQ topic / 接口契约 ③ 网关日志 ④ 人工拼接。检索未命中"多仓静态调用图 → 跨服务流程模型"的开源实现。
- **G-11（新增）**：**多仓/多服务的扫描结果聚合层无公开件**。ArchGuard 与 jQAssistant 都是"单仓扫描入库"，50 个微服务需要 50 次扫描 + 一个聚合视图；聚合逻辑（服务名↔仓库↔数据库↔接口的对齐）需自建。

---

## 9. 客户确认实践：差异清单 + 评审会（对应 v4 AC-05 / AC-07，patch-01 修订 3 + patch-02 第 2 项）

> **v4 已冻结的四要素**：① 确认主体 = **客户方业务专家**；② **确认对象 = 关键业务流程**（客户人工判断的重点交易与重点场景，**研究方不预设界定标准**）；③ 确认形式 = **差异清单 + 评审会**；④ 差异项处置 = **确认通过／按客户修正／标记后续人工处理**（v4 允许差异清单存在未决项，只要标注为「后续人工处理」即收口；评审会结论为「通过」或「有条件通过」即达标）。
> 本节盘点公开生态中**支撑这四要素的既有实践与案例**。**不设计实施流程、不做排序、不做推荐**（NG-04）。

### 9.1 两类确认覆盖策略（v4 已冻结为「仅关键业务流程」；两类实践仍如实并列呈现，不做推荐）

| 策略 | 做法 | 支撑它的既有实践/工件 | 优势 | 代价/风险 | 状态 |
|---|---|---|---|---|---|
| **S-A 全量流程确认** | 识别出的**全部**业务流程都进差异清单并上评审会 | IEEE 1028-2008 的 **inspection**（检视，要求 100% 覆盖工件、量化缺陷密度、有进入/退出准则）；OpenFastTrace 的覆盖率报告可把"未确认项"显式化为**未满足项清单**并进 CI 门禁 | 可给出"全部流程已确认"的二值结论，审计留痕完整 | 评审工作量与流程条数成正比；50 微服务规模下必然分期，周期长；客户业务专家时间成为瓶颈 | **v4 未采用**（xiao 已答：仅关键业务流程）；作为公开生态中的另一类既有实践**如实并列** |
| **S-B 仅关键业务流程确认**（**v4 已冻结采用**） | 只对**关键业务流程**（客户人工判断的重点交易与重点场景）走完整差异清单 + 评审会 | IEEE 1028-2008 允许按风险**选择评审类型**（technical review / walkthrough 轻于 inspection）；`ddd-crew/core-domain-charts`（CC-BY-SA-4.0，620★，2026-08-23）为"协作识别核心域"的公开画布；`code-maat`／CodeScene 的变更耦合与热点可提供量化视图 | 评审量可控，聚焦业务价值最高处；**与 v4 冻结口径一致** | 「关键」的界定权在**客户方人工判断**（v4 明示研究方不预设标准）；因此本路线的可行性取决于**能否把客户指定的场景集合切成工具可接受的输入范围** → 见 §9.6 切片输入能力汇总 | **v4 已冻结采用**；界定标准由客户给出 |

> **v4 冻结口径（CHANGE-03，2026-10-08 10:38 xiao 答复）**：确认覆盖范围 = **仅关键业务流程**，即 **S-B**；「关键」由**客户方人工判断**（重点交易与重点场景），**研究方不预设界定标准**。因此上表的 S-A 行**不再作为本项目的候选路线**，仅作为公开生态中另一类既有实践**如实并列呈现**，供 R2 了解代价差异；本节**不做推荐**。
>
> **关于「关键」的界定（重要边界）**：v2 曾在 S-B 行列出"核心域流程／高频变更流程／涉及资金与合规的流程"作为建议判据——**v3 已删除该预设**。按 v4，界定权在客户方人工判断，研究方不预设标准。公开生态中可作为**客户判断时的参考素材**（不是标准、不是判据、不构成推荐）的既有实践有：`ddd-crew/core-domain-charts`（协作识别核心域的画布，CC-BY-SA-4.0，620★，2026-08-23）、`code-maat`／CodeScene 的变更耦合与热点（改动频繁度与复杂度的量化视图）、`ArchGuard` 的架构适配度视图。**是否采用、如何加权，均由客户方业务专家决定。**

### 9.2 差异清单的三种生成路径（均有公开工件）

| 路径 | 比对对象 | 公开工件 | 产物形态 | 证据等级 |
|---|---|---|---|---|
| **模型 vs 模型** | 逆向出的流程模型 ⟷ 客户认定/既有文档的流程模型 | `bpmn-io/bpmn-js-differ`（MIT，56★，2026-08-28）；ProM 的流程模型对比插件（GPL，promtools.org，本环境 HTTP 200 已验证域名可达） | 元素级增删改清单，可驱动可视化差异渲染 | **A**（仓库由 GitHub API 直证）／ProM 为 **B**（非 GitHub 分发） |
| **模型 vs 事实** | 参考流程模型 ⟷ 真实事件日志 | PM4Py 的 **conformance checking**：token-based replay 与 alignments，产出逐 trace 偏差与 fitness 分数 | 定量偏差清单（哪些 trace 不符合模型、偏差在哪一步） | **A**（`process-intelligence-solutions/pm4py` 仓库与其 "Conformance Checking" 章由 API/官网直证，官网 **HTTP 200 已验证**）；`pm4py.fit.fraunhofer.de` 子站在本环境连接失败 → **待回源** |
| **条目 vs 条目** | 逆向出的流程条目 ⟷ 客户确认后的条目 | `itsallcode/openfasttrace`（GPL-3.0，198★，2026-10-08）：带 ID 的条目 + 链接关系 → 追溯矩阵、覆盖率、未满足项清单 | 每条差异有 ID、状态、链接；可直接承载"确认通过／按客户修正／标记后续人工处理"三态 | **A**（仓库由 GitHub API 直证；README raw 文件 **HTTP 200 已验证**） |

### 9.3 评审会的既有实践与标准依据

- **IEEE 1028-2008《Standard for Software Reviews and Audits》**（https://standards.ieee.org/ieee/1028/5398/ ，本环境 **HTTP 200 已验证**）：定义五类评审（management review / technical review / walkthrough / inspection / audit），并规定**进入准则、退出准则、异常（anomaly）记录与处置**。这是"评审会 + 差异项处置"最直接可引用的**标准级依据**，可避免自创流程。证据等级 **A**（标准页面直证）／标准正文需购买，具体条款编号 **待回源**。
- **Fagan Inspection**（IBM，1976 起的正式检视法，强调缺陷分类、检视速率与退出准则）：为 S-A 全量确认提供方法论来源。本研究环境中 Wikipedia 相关页面**连接失败**，未能直证 → **待回源**，等级 **B**。
- **Example Mapping**（Cucumber 官方实践，https://cucumber.io/blog/bdd/example-mapping-introduction/ ，本环境 **HTTP 200 已验证**）：用 Rules / Examples / **Questions** 三类卡片与业务专家逐条确认；其中 **Questions 卡片即"标记后续人工处理"的既有实践形态**，可直接映射到 v3 AC-07 的第三态处置。等级 **A**（页面直证）。
- **工作坊准备与远程形式**：`ddd-crew/como-prep-canvas`（协作建模工作坊准备画布，CC-BY-SA-4.0，35★，2026-08-01，README raw **HTTP 200 已验证**）覆盖"会前发料与议程准备"；`ddd-crew/virtual-modelling-templates`（CC-BY-SA-4.0，84★，2026-08-01）覆盖远程评审（Miro 等）。
- **讲述—回放—修正循环**：Domain Storytelling（`WPS/domainstorytelling.org`，CC-BY-4.0，7★，2026-10-06；工具 `WPS/egon.io`）的机制是"业务专家讲述 → 研究员回放 → 专家即时纠偏"，**差异在讲述过程中即时暴露并处置**，是一种轻量于正式评审会的确认形式。

### 9.4 确认结果的固化与防失效

- **Cucumber-JVM**（MIT，2836★，2026-10-08）：把确认后的流程写成 Gherkin 规格 —— 业务专家可读、可执行、可回归；`pending`/`undefined` 步骤**天然表达"标记后续人工处理"**，与 AC-07 的三态处置结构一致。
- **活文档**：`jboz/living-documentation`（Apache-2.0，48★，2026-01-26，"从 Java 项目生成活文档"）、`jenkinsci/cucumber-living-documentation-plugin`（MIT，15★，2023-06-13）、`LivingDocumentation/awesome-living-documentation`（NOASSERTION，108★，2022-07-30，**待回源**）。作用是让确认结果**随代码演进保持有效**，避免"一次性签字后文档失效"。
- **Strangler Fig（绞杀者模式）**（https://martinfowler.com/bliki/StranglerFigApplication.html ，本环境 **HTTP 200 已验证**）与 **Mikado Method**（`chaabani-anis/mikado-method`，无许可证、5★，**C 级线索**；方法原始站点 `mikadomethod.org` 在本环境**连接失败 → 待回源**）：两者是"确认后如何增量落地"的既有实践，**本报告仅记录其存在，不给出实施顺序结论**（NG-04）。

### 9.5 AC-05 自检

| AC-05 要素（v4） | 本报告覆盖位置 | 是否齐全 |
|---|---|---|
| 实施流程含**独立的**「与客户确认业务流程」环节 | §6.3 P-01～P-06 六条实施流程候选中，**P-04（处置与追溯闭环）与 P-05（评审会）即该独立环节**；§9 全节展开 | ✅ |
| ① 确认主体 = **客户方业务专家** | §9 引言、§9.1、§9.3（Example Mapping / Domain Storytelling 均以业务专家为讲述与判定主体） | ✅ |
| ② **确认对象 = 关键业务流程**（客户人工判断的重点交易与重点场景，研究方不预设标准） | §9 引言②、§1.1 第 ⑦ 行术语、§9.1（已删除 v2 的预设判据，改为「客户判断时可参考的公开素材」）、§9.6（客户指定场景集合能否被切成工具输入） | ✅ |
| ③ 确认形式 = **差异清单 + 评审会** | §9.2（差异清单三条生成路径）+ §9.3（评审会标准依据与形式） | ✅ |
| ④ **差异项处置规则**（确认通过／按客户修正／**标记后续人工处理**） | §9.2 路径三（OpenFastTrace 三态承载）、§9.3（IEEE 1028 异常处置；Example Mapping 的 Questions 卡片 = 标记后续人工处理）、§9.4（Cucumber `pending` = 标记后续人工处理） | ✅ |
| 两类覆盖策略**如实并列**且不做推荐（patch-02 第 2 项） | §9.1（S-A 全量流程确认 / S-B 仅关键业务流程确认并列；标注 v4 已冻结采用 S-B，但两类实践均如实呈现，无推荐语） | ✅ |

**AC-05 四要素齐全 ✅**（确认主体／确认对象／确认形式／处置规则）。v2 中「待 xiao 确认」的两个未决事项已由 **CHANGE-03（2026-10-08 10:38）闭环**，v3 按 v4 冻结口径改写，**未自行猜测、未预设「关键」的界定标准**。

### 9.6 切片输入能力汇总（patch-02 第 3 项：「只确认关键流程」路线的可行性地面）

§5 各表**第 12 列**已为全部 **86 条**候选（主表 70 + 次级 16）逐条标注「能否把输入限定到客户指定的流程/场景集合」。汇总如下：

| 判定 | 条数 | 占比 | 含义 |
|---|---|---|---|
| **可** | **71** | 82.6% | 存在明确的范围限定入口（路径/包名/模块/tag/条目 ID/流程定义 key/单份文档等），可把输入收窄到客户指定的场景集合 |
| **部分** | **6** | 7.0% | 有范围参数但粒度不匹配「业务场景」：`OpenTelemetry Java Instrumentation`（可按服务/端点，业务场景标签需自定义埋点）、`ArchGuard`（按仓库/模块）、`CodeQL`（数据库按构建单元生成，切片发生在查询侧）、`Spring Modulith`（输出为模块级）、`living-documentation（jboz）`（按项目）、`SonarQube`（按项目/模块） |
| **不适用** | **9** | 10.5% | 本体（FIBO）、注解库（jMolecules）、按版本推进的迁移工具（Flyway）、清单类（4 份 awesome-*）、证据页 |

**标注可信度**：**直证 14 条**（依据为文档明示的机制，如 `java-callgraph2`／`java-all-call-graph` 文档明示「只解析部分包」、`bpmn-js-differ` 比对两份指定文档、`Camunda Modeler`／`bpmn-js`／`PlantUML` 按单份输入渲染、方法论类天然按单场/单故事进行）；**推断 63 条**（依据为该候选已采集的能力描述与常规用法推断，**均已在单元格内标「推断」**，未实测）；其余 9 条为「不适用」，无需标注来源。

**结论（不含推荐）**：

- **C-15**：「**只确认关键业务流程**」这条 v4 冻结路线在**工具层面普遍可行** —— 82.6% 的候选具备明确的输入范围限定入口，其中 C 类（调用图/数据流）与 F 类（DB/引擎）几乎全部为「可」。因此该路线的瓶颈**不在工具是否支持切片**。置信度：**中高**（63/86 为推断，需 PoC 实测确认）。
- **C-16（新增缺口 G-14）**：真正的瓶颈是**「客户人工判断的重点交易与重点场景」→「代码入口集合」的映射本身没有公开工具**。客户给出的是业务语言（"大额跨行转账""理赔受理"），而所有工具的切片入口都是技术语言（包名/路径/入口方法/tag/流程定义 key）。检索未命中任何"业务场景描述 → 代码入口定位"的开源实现；学术侧的对应问题是 **feature location（特征定位）**，其工具（Feather、Sando）**无维护中的开源实现**（已在 G-04 记录）。因此该映射只能靠 **人工 + LLM 辅助**建立，且属于**每条关键流程都要做一次**的重复劳动。置信度：**高**（多轮检索未命中 + G-04 交叉印证）。
- **对 AC-07 的影响**：v4 允许差异清单存在未决项（标注「后续人工处理」即收口），这**降低了 G-14 的阻塞性** —— 映射不确定的场景可先标「后续人工处理」而不阻断评审会结论。

---

## 10. 证据矩阵（58 条：结论 → 来源 → 日期 → 等级）

| 编号 | 支撑的结论 | 来源（链接） | 日期 | 等级 |
|---|---|---|---|---|
| E-01 | C-01 / C-04：`java-all-call-graph` 输出含"数据库表、字段、消息、HTTP、事务、**方法执行顺序**" | https://github.com/Adrninistrator/java-all-call-graph | 仓库最后推送 2026-08-28（API 取值 2026-10-08） | **A** |
| E-02 | C-04 / C-09：`java-all-call-graph` 有场景化文档《解析 Java 代码中的数据库表信息》 | https://github.com/Adrninistrator/java-all-call-graph/blob/main/docs/usage_scenarios/parse_java_to_db.md | raw 文件 **HTTP 200 已验证**（2026-10-08） | **A** |
| E-03 | C-02 / E 类：`java-all-call-graph-server` 提供 Web 界面与 **MCP Server**（把调用链事实接入 AI agent） | https://github.com/Adrninistrator/java-all-call-graph-server （仓库根 `MCP_SERVER.md`） | 仓库最后推送 2026-06-07 | **A** |
| E-04 | C-01 / C-08：`codebase-reverse` 自述"把存量源码逆向为功能/实现/架构/接口/对象/组件/数据库完整元模型，深度定制于 Java Web 与 Java 微服务（Spring Boot/Cloud）" | https://github.com/sharptoolbox/codebase-reverse | 仓库最后推送 2026-08-30 | **A**（仓库存在性与描述）／**C**（能力自述部分，须实测） |
| E-05 | C-03 / C-05：PM4Py 采用 AGPL-3.0，且官方提供"闭源商用环境的另一许可版本" | https://github.com/process-intelligence-solutions/pm4py ｜ https://processintelligence.solutions/pm4py | 仓库推送 2026-09-01；release **v2026.10.0** 于 2026-10-07 | **A** |
| E-06 | C-03 / A 类：PM4Py 具备 BPMN 发现能力（discovery → BPMN），且**输入必须是事件日志** | https://pm4py.fit.fraunhofer.de/bpmn-discovery-in-pm4py.html （域名在本环境**连接失败**，**待回源**）；等价一手证据可用仓库 README 与 https://processintelligence.solutions/pm4py （**HTTP 200 已验证**） | 2026-10-08 | **B**（文档站未能在本环境直证；PM4Py 以事件日志为输入这一点另由 A 类其余来源交叉支撑） |
| E-07 | C-06 / A 类：Apromore 同 org 8 个仓库全部 `archived=true`；`ApromoreCore` 最后推送 2025-06-07、LGPL-3.0；`apromore/ApromoreCommunity` 经 API 返回 404 | https://github.com/apromore/ApromoreCore ｜ https://github.com/apromore/ApromoreCE | GitHub API 取值 2026-10-08 | **A** |
| E-08 | C-06 / A 类：Apromore CE README 自述"CE was the open-source edition until August 2020, when it was replaced by Apromore Core" | https://github.com/apromore/ApromoreCE | 仓库最后推送 2022-11-16 | **A** |
| E-09 | C-06：Apromore 被 Salesforce 收购完成 | https://salesforceben.com/salesforce-completes-apromore-acquisition-to-boost-agentic-process-mining/ | 2025-11-03（该 URL 在本环境返回 **403**，**待回源**） | **B** |
| E-10 | C-03 / A 类：bupaR 为 R 生态核心包，CRAN 版本 1.0.1（2025-02），README/CRAN 标注 MIT，而 GitHub API 返回 NOASSERTION | https://github.com/bupaverse/bupaR ｜ https://cran.r-project.org/web/packages/bupaR/ | CRAN 2025-02；仓库推送 2025-11-28 | **A**（两源冲突已如实标注） |
| E-11 | C-08 / E 类：Blarify 官方 README 列明支持语言为 Python/JS/TS/**Java**/C#，Java 标注 beta；v2 归档转向 Blarify-Next | https://github.com/blarApp/blarify | 仓库推送 2026-08-17 | **A** |
| E-12 | C-06：Eclipse MoDisco `archived=true` | https://github.com/eclipse-modisco/org.eclipse.modisco （**GitHub API `archived=true` 直证**）｜公告页 https://www.eclipse.org/projects/news/ （本环境 **404**，**待回源**） | 仓库推送 2026-03-06；Web 检索命中公告日期 2026-07-14 | **A**（归档状态）／**B**（公告日期） |
| E-13 | C-06：Sourcetrail 原仓 `archived=true`（2021-12-13）；社区分叉 `petermost/Sourcetrail` 仍活跃（2026-10-02，GPL-3.0） | https://github.com/CoatiSoftware/Sourcetrail ｜ https://github.com/petermost/Sourcetrail | GitHub API 取值 2026-10-08 | **A** |
| E-14 | C-06：`archguard/scanner` `archived=true`（2022-05-25），而主仓 `archguard/archguard` 仍活跃（2026-10-02，MIT） | https://github.com/archguard/scanner ｜ https://github.com/archguard/archguard | GitHub API 取值 2026-10-08 | **A** |
| E-15 | C-06 / D 类：`structurizr/java`、`/cli`、`/lite` 三仓 `archived=true`（2026-02-01）；`structurizr/dsl` 与 `C4-DSL/structurizr` 经 API 返回 404；当前规范仓为 `structurizr/structurizr`（Apache-2.0，2026-10-05） | https://github.com/structurizr/structurizr | GitHub API 取值 2026-10-08 | **A** |
| E-16 | C-06：Sourcegraph Cody 归档为 `cody-public-snapshot` | https://github.com/sourcegraph/cody-public-snapshot | 归档时间 2025-08-01（GitHub 页面显示） | **A** |
| E-17 | C-06 / F 类：Camunda 7 Community Edition 于 2025-10 生命周期终止 | https://camunda.com/blog/2025/10/camunda-7-community-edition-reached-end-of-life/ ｜ https://docs.camunda.org/manual/7.24/upgrading-guide/other-changes/7.24/ （两 URL 在本环境分别 **404** / **连接失败**，**待回源**） | 2025-10（多处独立来源命中同一事实） | **B** |
| E-18 | C-05 / F 类：bpmn-js 使用 bpmn.io 自定义许可（非 OSI，含署名义务） | https://bpmn.io/license/ ｜ https://github.com/bpmn-io/bpmn-js | 许可页 **HTTP 200 已验证**（2026-10-08）；仓库推送 2026-10-05 | **A** |
| E-19 | C-07 / G 类：《Repairing Business Process Models as Retrieved from Source Code》——从源码恢复的 BPMN 需要"修复" | https://link.springer.com/chapter/10.1007/978-3-642-38484-4_8 | 2013（Springer LNCS） | **B**（页面 HTTP 200 已验证） |
| E-20 | C-07 / G 类：《An Approach to Business Process Recovery from Source Code》 | https://ui.adsabs.harvard.edu/abs/2015itng.conf...67P/abstract | 2015（ITNG）；ADS 页面在本环境返回 **405**，建议改用 IEEE Xplore 文档号 **7019906**（https://ieeexplore.ieee.org/document/7019906，本环境未验证，**待回源**） | **B** |
| E-21 | C-07 / G 类：《Mining BPMN Processes on GitHub》——GitHub 上真实 BPMN 模型的实证研究 | https://pmc.ncbi.nlm.nih.gov/articles/PMC7163505/ | 2020（PMC，开放获取） | **B**（页面 HTTP 200 已验证） |
| E-22 | C-07 / G 类：《Model-driven Reverse Engineering of Software Processes》学位论文（含从源码抽取流程的案例） | https://www.proquest.com/openview/d56f7ba50726c942974934e21cb5a9cd/1?cbl=2114622&diss=y&pq-origsite=gscholar | 2019（QUT，ProQuest 开放）；该长 URL 在本环境未验证，**待回源** | **B** |
| E-23 | C-04 / C 类：Joern 支持 Java（`javasrc2cpg` 源码前端、`jimple2cpg` 字节码前端） | https://docs.joern.io/ ｜ https://github.com/joernio/joern | 文档站 **HTTP 200 已验证**；仓库推送 2026-10-08 | **A** |
| E-24 | C-04 / B 类：SootUp 提供调用图生成与数据流分析（含 Heros IFDS） | https://github.com/soot-oss/SootUp （仓库描述与活跃度由 API 直证）；文档站 https://soot-oss.github.io/sootup/ 在本环境返回 **404**（`*.github.io` 整体不可达），**待回源** | 仓库推送 2026-10-08 | **A**（仓库存在与活跃度）／**B**（IFDS 能力描述，来自仓库 README 与文档站检索摘要） |
| E-25 | C-02 / D 类：Spring Modulith 生成 PlantUML/C4 图与 Application Module Canvas 到 `target/spring-modulith-docs/` | https://docs.spring.io/spring-modulith/reference/documentation.html | **HTTP 200 已验证**（2026-10-08） | **A** |
| E-26 | C-02 / B 类：jQAssistant 把源码/字节码/XML/Maven/文档扫描进 Neo4j，用 Cypher 查询并出报告 | https://github.com/buschmais/jqassistant | 仓库推送 2026-10-07 | **A** |
| E-27 | C-09 / B 类：Chapi 定位为"通用代码抽象解析器，把不同语言代码转换为统一模型" | https://github.com/phodal/chapi | 仓库推送 2026-08-18 | **A** |
| E-28 | C-09 / B 类：Coca 定位为"遗留系统重构与自动化分析工具箱（转换/调用/依赖/度量/架构分析）" | https://github.com/phodal/coca | 仓库推送 2026-01-06 | **A** |
| E-29 | C-07 / D 类：FIBO 由 EDM Council 维护，定义金融业务概念本体，MIT 许可 | https://github.com/edmcouncil/fibo | 仓库推送 2026-10-07 | **A** |
| E-30 | C-07 / G 类：vFunction 宣称对 Java 单体做架构可观测性与分阶段拆解 | https://vfunction.com/modernization-platform/ | 2025–2026 官方页面（深路径本环境 **404**，根路径 200，**待回源**） | **B** |
| E-31 | C-05 / C 类：CodeQL 查询库仓库标注 MIT，而 CodeQL CLI 受 GitHub 专有许可约束 | https://github.com/github/codeql | 仓库推送 2026-10-08 | **A** |
| E-32 | C-08 / E 类：Potpie 自托管需 Neo4j + LLM，提供预置与自定义 agent | https://github.com/potpie-ai/potpie | 仓库推送 2026-10-08 | **A** |
| E-33 | C-02 / B 类：OpenRewrite 基于 Lossless Semantic Tree 做大规模代码查询与变换 | https://github.com/openrewrite/rewrite ｜ https://docs.openrewrite.org/ | 仓库推送 2026-10-08 | **A** |
| E-34 | C-07 / G 类：三份 awesome 清单的存在与许可（CC0-1.0 / NOASSERTION / CC0-1.0） | https://github.com/feststelltaste/awesome-legacy-systems ｜ https://github.com/feststelltaste/awesome-agentic-software-modernization ｜ https://github.com/legacycoderocks/awesome-legacy-code | GitHub API 取值 2026-10-08 | **A** |
| E-35 | C-06 / F 类：Spring Statemachine `archived=true`，homepage 已指向 `spring-attic.github.io/spring-statemachine/` | https://github.com/spring-projects/spring-statemachine | GitHub API 取值 2026-10-08；最后推送 2026-07-05 | **A** |
| E-36 | C-01 / C 类：`gen-java-code-uml-sequence-diagram` 可"从 Java 代码自动生成 UML 时序图"，但已停更（2021-10-22） | https://github.com/Adrninistrator/gen-java-code-uml-sequence-diagram | GitHub API 取值 2026-10-08 | **A** |
| E-37 | C-10 / F 类：Flowable 与 Activiti 均为 Apache-2.0 且活跃，流程定义与历史实例存于 `ACT_*` 表族 | https://github.com/flowable/flowable-engine ｜ https://github.com/Activiti/Activiti | 仓库推送 2026-10-07 / 2026-10-08 | **A** |
| E-38 | C-10 / F 类：LiteFlow 为组件化规则引擎，编排规则即流程定义，Apache-2.0 | https://github.com/dromara/liteflow | 仓库推送 2026-09-21 | **A** |
| E-39 | C-05 / F 类：`mybatis-mysql-table-parser` 解析 MyBatis XML 中的表名（仅 MySQL），Apache-2.0，仅 4★ | https://github.com/Adrninistrator/mybatis-mysql-table-parser | 仓库推送 2025-07-17 | **A** |
| E-40 | C-05：Tai-e 为 Java/Android 静态分析框架（指针分析、污点分析），LGPL-3.0；文档站可访问 | https://github.com/pascal-lab/Tai-e ｜ https://tai-e.pascal-lab.net/ | 仓库推送 2026-09-19；文档站 **HTTP 200 已验证** | **A** |
| E-41 | C-12 / H 类：`bpmn-js-differ` 是"BPMN 2.0 文档的 diff 工具"，MIT，可作为差异清单的模型级载体 | https://github.com/bpmn-io/bpmn-js-differ | GitHub API 取值 2026-10-08；56★；最后推送 2026-08-28 | **A** |
| E-42 | C-12 / H 类：`OpenFastTrace` 为开源需求追溯套件（GPL-3.0），输出追溯矩阵／覆盖率／未满足项清单 | https://github.com/itsallcode/openfasttrace ｜ README raw https://raw.githubusercontent.com/itsallcode/openfasttrace/main/README.md | GitHub API：198★、最后推送 2026-10-08；raw README **HTTP 200 已验证** | **A** |
| E-43 | C-12 / H 类：`Cucumber-JVM`（MIT，2836★，2026-10-08 推送）——Gherkin 规格可承载确认结果，`pending`/`undefined` 步骤表达"标记后续人工处理" | https://github.com/cucumber/cucumber-jvm | GitHub API 取值 2026-10-08 | **A**（仓库事实）／**B**（`pending` 语义映射到三态处置为研究员判断） |
| E-44 | C-12 / H 类：`jboz/living-documentation`（Apache-2.0，48★，2026-01-26）自述"从 Java 项目生成活文档" | https://github.com/jboz/living-documentation | GitHub API 取值 2026-10-08 | **A** |
| E-45 | C-12 / §9.3：**IEEE 1028-2008《Software Reviews and Audits》**为评审类型、进入/退出准则与异常处置提供标准级依据 | https://standards.ieee.org/ieee/1028/5398/ | 页面 **HTTP 200 已验证**（2026-10-08） | **A**（页面存在与标题）／标准正文具体条款编号 **待回源**（需购买） |
| E-46 | C-12 / §9.3：**Example Mapping** 用 Rules／Examples／**Questions** 卡片与业务专家逐条确认，Questions 即"标记后续人工处理"的既有实践形态 | https://cucumber.io/blog/bdd/example-mapping-introduction/ | 页面 **HTTP 200 已验证**（2026-10-08） | **A** |
| E-47 | C-12 / §9.3：`ddd-crew/como-prep-canvas`（CC-BY-SA-4.0，35★，2026-08-01）为"协作建模工作坊准备画布，支持 facilitator 准备工作坊" | https://github.com/ddd-crew/como-prep-canvas ｜ README raw https://raw.githubusercontent.com/ddd-crew/como-prep-canvas/main/README.md | GitHub API 取值 2026-10-08；raw README **HTTP 200 已验证** | **A** |
| E-48 | §9.4：**Strangler Fig（绞杀者模式）**为增量替换的既有实践 | https://martinfowler.com/bliki/StranglerFigApplication.html | 页面 **HTTP 200 已验证**（2026-10-08） | **A** |
| E-49 | C-12 / §9.2：PM4Py 具备 **conformance checking**（token-based replay 与 alignments），可产出模型 vs 日志的定量偏差 | https://processintelligence.solutions/pm4py （**HTTP 200 已验证**）｜子站 https://pm4py.fit.fraunhofer.de/token-replay-pm4py.html 与 /alignments-pm4py.html （本环境**连接失败，待回源**） | 2026-10-08 | **A**（官网与仓库直证该能力存在）／**B**（子站细节未能直证） |
| E-50 | C-14 / §9.1：`ddd-crew/core-domain-charts`（CC-BY-SA-4.0，620★，2026-08-23）为"协作识别核心域＝战略业务差异点"的公开画布，可作 S-B 分级确认的判据来源 | https://github.com/ddd-crew/core-domain-charts | GitHub API（Search）取值 2026-10-08 | **A** |
| E-51 | §9.2：**ProM** 为 GPL 的流程挖掘工具集（含一致性检查/模型对比插件），**GitHub 无官方仓库**，分发在 promtools.org | https://promtools.org/ （**HTTP 200 已验证**）；GitHub Search API 查询 `ProM process mining framework promtools` 返回 **0** 结果 | 2026-10-08 | **A**（站点可达、GitHub 无官方仓）／**B**（插件能力细节来自站点描述） |
| E-52 | H 类：`ddd-crew/eventstorming-glossary-cheat-sheet`（CC-BY-SA-4.0，987★，2026-09-13）为 EventStorming 术语与做法速查 | https://github.com/ddd-crew/eventstorming-glossary-cheat-sheet | GitHub API 取值 2026-10-08 | **A** |
| E-53 | H 类：`WPS/domainstorytelling.org`（CC-BY-4.0，7★，2026-10-06）为 Domain Storytelling 方法官网源码 | https://github.com/WPS/domainstorytelling.org | GitHub API（Search）取值 2026-10-08 | **A** |
| E-54 | H 类：`chaabani-anis/mikado-method`（**无 LICENSE**，5★，2026-06-30）自述为"agentic legacy refactoring 的 Mikado Method skill" | https://github.com/chaabani-anis/mikado-method | GitHub API 取值 2026-10-08 | **A**（仓库事实）／**C**（方法在本场景的有效性，须实测） |
| E-55 | H 类：`awesome-living-documentation`（NOASSERTION，108★，2022-07-30）与 `jenkinsci/cucumber-living-documentation-plugin`（MIT，15★，2023-06-13） | https://github.com/LivingDocumentation/awesome-living-documentation ｜ https://github.com/jenkinsci/cucumber-living-documentation-plugin | GitHub API 取值 2026-10-08 | **A** |
| E-56 | C-13 / §8：`ddd-crew/context-mapping`（CC-BY-SA-4.0，1864★）与 `virtual-modelling-templates`（CC-BY-SA-4.0，84★，2026-08-01）分别覆盖上下文映射表述法与远程评审模板 | https://github.com/ddd-crew/context-mapping ｜ https://github.com/ddd-crew/virtual-modelling-templates | GitHub API 取值 2026-10-08 | **A** |
| E-57 | C-13 / §8.1 K-1：C 类静态分析工具的输入均为**单构建单元/单仓**（class/jar/war/jmod、单一源码目录、classpath），故跨服务流程无法由静态分析得到 | §5-B、§5-C 各条「输入要求」列（源自各仓 README 与官方文档） | 2026-10-08 | **A** |
| E-58 | C-11 / §7：`mybatis-mysql-table-parser` 仅解析 MyBatis XML 且仅支持 MySQL（4★，2025-07-17），JPA/Hibernate 无等价开源件 | https://github.com/Adrninistrator/mybatis-mysql-table-parser | GitHub API 取值 2026-10-08；GitHub Search API 未命中 JPA/Hibernate 等价物 | **A**（该仓事实）／**B**（"无等价物"为检索未命中结论） |

---

## 11. 可复现验证线索（18 条，供测试工程师抽查）

> 每条给出「打开什么 / 做什么 / 预期看到什么」。

1. **`java-all-call-graph` 的"解析数据库表"场景**
   打开 https://github.com/Adrninistrator/java-all-call-graph/blob/main/docs/usage_scenarios/parse_java_to_db.md
   预期：文档说明如何解析 Java 代码涉及的**数据库表与字段**并写库；同目录 `docs/usage_scenarios/` 下另有"方法执行顺序解析"等场景文档。
   本次已验证：raw 文件 **HTTP 200**（2026-10-08）。

2. **`java-all-call-graph-server` 的 MCP Server**
   打开 https://github.com/Adrninistrator/java-all-call-graph-server ，查看仓库根目录 `MCP_SERVER.md`
   预期：说明如何以 MCP Server 形式把调用链查询能力暴露给 AI agent。**同时注意该仓库未检出 LICENSE 文件。**

3. **PM4Py 的许可证与商用条款**
   打开 https://github.com/process-intelligence-solutions/pm4py 的 README「License」段
   预期：明示 AGPL-3.0，并写明"为闭源商用环境提供另一许可版本"。交叉核对 https://processintelligence.solutions/pm4py （"open-source license for academic and research purposes, and a closed-source license for commercial use"）。

4. **PM4Py 的 BPMN 发现能力（同时验证 G-01 缺口）**
   打开 https://pm4py.fit.fraunhofer.de/bpmn-discovery-in-pm4py.html （⚠️ 该域名在本研究环境**连接失败**，请在正常网络下复核）；等价入口：https://processintelligence.solutions/pm4py （**HTTP 200 已验证**）与仓库 README。
   预期：给出从**事件日志**发现并导出 BPMN 的 API 示例。关键点：文档全程要求输入为 event log / dataframe——**这正是本项目"只有源码"时的缺口所在**。

5. **Apromore 开源线已退场**
   打开 https://github.com/apromore （org 页面）与 https://github.com/apromore/ApromoreCE
   预期：org 下 8 个仓库全部带 "Public archive" 标记；CE 的 README 自述 2020-08 起被 Apromore Core 取代。再核对收购：https://salesforceben.com/salesforce-completes-apromore-acquisition-to-boost-agentic-process-mining/ （2025-11-03；⚠️ 该 URL 在本环境返回 **403**，待回源）。
   注意：`apromore/ApromoreCommunity` 这个在官方文档中被引用的路径，经 GitHub API 返回 **404**。

6. **Spring Modulith 自动产出模块文档与事件注册表**
   打开 https://docs.spring.io/spring-modulith/reference/documentation.html
   预期：`Documenter` / `@ApplicationModuleTest` 会生成 PlantUML、C4 图与 Application Module Canvas 到 `target/spring-modulith-docs/`；另有"事件发布注册表"章节。**HTTP 200 已验证。**

7. **Blarify 的语言支持矩阵与版本状态**
   打开 https://github.com/blarApp/blarify 的 README
   预期：Supported Languages = Python / JavaScript / TypeScript / **Java** / C#，其中 Java 与 C# 标注 beta；顶部有 v2 归档、转向 Blarify-Next 的说明（同 org Discussions 有 "Blarify-Next is here!" 公告）。

8. **Joern 的 Java 前端**
   打开 https://docs.joern.io/ ，检索 `javasrc2cpg` 与 `jimple2cpg`
   预期：Java 源码与字节码两个导入前端的用法说明，以及 CPG 数据流查询（`reachableBy`）示例。仓库描述亦明列 Java。**HTTP 200 已验证。**

9. **SootUp 的调用图与数据流能力**
   打开 https://soot-oss.github.io/sootup/ （⚠️ 本研究环境返回 **404**，`*.github.io` 全域不可达，请在正常网络下复核）；等价证据：https://github.com/soot-oss/SootUp 的 README 与 `docs/` 目录（仓库本身由 GitHub API 直证存在且活跃，最后推送 2026-10-08）。
   预期：调用图生成（多算法）与数据流分析（Heros IFDS）章节。

10. **Camunda 7 CE 生命周期终止**
    打开 https://camunda.com/blog/2025/10/camunda-7-community-edition-reached-end-of-life/ 与 https://docs.camunda.org/manual/7.24/upgrading-guide/other-changes/7.24/
    ⚠️ 本研究环境中前者返回 **404**、后者**连接失败**（`camunda.com` 根路径可达 200），属环境网络限制或路径变更，**待回源**。
    预期：官方声明 Camunda 7 Community Edition 于 2025-10 EOL。这决定"用 Camunda 承接逆向出的 BPMN"路线的可持续性。

11. **Spring Statemachine 已归档**
    打开 https://github.com/spring-projects/spring-statemachine
    预期：仓库带 "Public archive" 标记，homepage 指向 `spring-attic.github.io/spring-statemachine/`。GitHub API `archived=true`、`pushed_at=2026-07-05`。

12. **"从源码恢复业务流程"是学术问题、且结果需要修复**
    打开 https://link.springer.com/chapter/10.1007/978-3-642-38484-4_8 （2013）与 https://pmc.ncbi.nlm.nih.gov/articles/PMC7163505/ （2020，开放获取）
    预期：前者标题即《Repairing Business Process Models as Retrieved from Source Code》，说明自动恢复出的 BPMN 质量不足以直接使用；后者是对 GitHub 上真实 BPMN 模型的实证挖掘，可用于判断"公开可参照的流程模型样本"规模。**两个页面本次均 HTTP 200 已验证（2026-10-08）。**

13. **`bpmn-js-differ` 的 BPMN 差异能力**
    打开 https://github.com/bpmn-io/bpmn-js-differ
    预期：README 说明如何对两份 BPMN 2.0 XML 做元素级 diff；许可证为 **MIT**（注意与 `bpmn-io/bpmn-js` 的自定义 bpmn.io 许可不同）。GitHub API：56★、最后推送 2026-08-28。

14. **`OpenFastTrace` 的追溯与未满足项清单**
    打开 https://github.com/itsallcode/openfasttrace ，并直接取 raw README：https://raw.githubusercontent.com/itsallcode/openfasttrace/main/README.md （本环境 **HTTP 200 已验证**）
    预期：条目以带 ID 的文本/Markdown 编写，可输出追溯矩阵、覆盖率与**未满足项清单**；提供 CLI、Gradle 插件、GitHub Action、JetBrains 语言服务器；许可证 **GPL-3.0**（商用交付需法务评估）。

15. **IEEE 1028-2008 评审标准**
    打开 https://standards.ieee.org/ieee/1028/5398/ （本环境 **HTTP 200 已验证**）
    预期：标准标题为《IEEE Standard for Software Reviews and Audits》，2008 版；内容涵盖评审类型与进入/退出准则、异常记录与处置。**标准正文需购买**，具体条款编号本研究未能直证 → **待回源**。

16. **Example Mapping 的 Questions 卡片 = "标记后续人工处理"**
    打开 https://cucumber.io/blog/bdd/example-mapping-introduction/ （本环境 **HTTP 200 已验证**）
    预期：说明用 Rules（规则）／Examples（示例）／**Questions（问题）** 三类卡片与业务人员逐条确认；Questions 卡片即未决项的既有实践形态，可直接映射到 v3 AC-07 的第三态处置。

17. **PM4Py 的 conformance checking**
    打开 https://processintelligence.solutions/pm4py （本环境 **HTTP 200 已验证**）的 "Conformance Checking" 章；细节子站 https://pm4py.fit.fraunhofer.de/token-replay-pm4py.html 与 `/alignments-pm4py.html`（⚠️ 该域名在本研究环境**连接失败，待回源**）
    预期：token-based replay 与 alignments 两类一致性检查，产出逐 trace 偏差与 fitness 分数——即"模型 vs 事实"的**定量差异清单**。

18. **工作坊准备画布（评审会前的既有实践工件）**
    打开 https://github.com/ddd-crew/como-prep-canvas ，并直接取 raw README：https://raw.githubusercontent.com/ddd-crew/como-prep-canvas/main/README.md （本环境 **HTTP 200 已验证**）
    预期：README 自述其为 "Collaborative Modeling Workshop Preparation Canvas … to support facilitators when preparing for" 协作建模工作坊；许可证 CC-BY-SA-4.0。

---

## 12. 缺口结论（14 条：公开生态**没有**覆盖的部分）

> 按要求：明确说"无匹配 / 证据不足"，不凑数。

| 编号 | 缺口 | 检索结论 | 证据等级 | 影响 |
|---|---|---|---|---|
| **G-01** | **Java 源码/字节码 → 事件日志（XES/CSV）的转换器** | **无匹配**。GitHub Search API 以 `process mining bpmn discovery`、`event log extraction database process mining`、`business process recovery source code`、`java legacy modernization reverse engineering` 等多组查询均返回 0 或完全不相关结果；A 类三个流程挖掘项目的官方文档一律要求已有事件日志。 | **A**（多轮检索未命中 + 官方文档输入要求直证） | **致命**。A 类（唯一能直接产出业务流程模型的一类）在本场景下**不可直接使用**，除非先自建这座桥 |
| **G-02** | **端到端"源码 → BPMN / 业务流程图"的开源流水线** | **无匹配**。58 条候选中输出物为"业务流程模型"的只有 F 类的 Flowable / Activiti / Drools / LiteFlow / Spring Statemachine（**前提是系统已用该引擎**）与 A 类（**前提是已有事件日志**）。 | **A** | 决定本项目必然走"多工具编排 + 人工/LLM 语义补全"的组合路线，而非采购单一工具 |
| **G-03** | **代码 → 业务术语表 / 代码 → FIBO 概念的自动映射** | **无匹配**。FIBO 仓库是纯本体，无代码分析入口；D 类工具产出的是技术构件名（类/包/模块），不是业务术语。 | **A** | 业务语义层必须靠 LLM 猜测 + 业务专家确认，**无法自动化验收** |
| **G-04** | **维护中的开源"特征定位 / 架构恢复聚类"工程实现** | **证据不足**。学术侧有 feature location 工具（Feather、Sando）与聚类式架构恢复（Bunch、ACDC、MoJo），但检索未找到 2024 年后仍在维护的开源仓库；工业侧等价能力（CodeScene 变更耦合）为商业产品，其 OSS 前身 `code-maat` 的许可证在仓库中未检出。 | **B** | "从代码事实自动聚出业务能力/用例"这一步没有现成件，需自建或采购 |
| **G-05** | **金融/银行/保险核心系统业务流程逆向的公开可复现案例** | **证据不足**。仅找到商业厂商的营销型案例（vFunction、Moderne、Celonis），无工件、无数据、无可验证指标；学术案例为通用软件，非金融核心。 | **B** | 无法用同行案例校准工期与质量预期；R1 定义 AC 时需自建验收基线 |
| **G-06** | **LLM 反推业务流程的准确率 / 召回率公开基准** | **无匹配**。E 类各项目均无评测数据；`codebase-reverse` 等 star 数低、单人维护，其输出质量属 **C 级证据**。 | **A**（检索未命中） | 方案中**不能承诺"自动化准确率"**，只能承诺"产出 + 人工确认"的交付形态 |
| **G-07** | **Spring AOP / 动态代理 / 反射 / MQ 监听 / `@Scheduled` 等隐式调用的通用解析** | **部分覆盖，证据不足**。`java-all-call-graph` 覆盖 MyBatis XML、MQ（RocketMQ/Kafka）、HTTP、Spring 事务；但 AOP 切面、定时任务、反射调用、SPI 的覆盖程度**无公开说明**，必须实测。 | **B** | 调用链断点会直接导致反推出的流程**缺环**；PoC 必须专项验证（本卡"只读调研"约束下无法完成） |
| **G-08** | **"DB 状态字段 + 更新它的代码位置" → 状态机自动合成** | **无匹配**。F 类只有正向的状态机框架（Spring Statemachine，且已归档）与 schema 文档工具，没有从代码+数据反推状态机的开源实现；学术上的 state machine inference 未见维护中的工程实现（GitHub Search `state machine inference from source code` 返回 1 条且完全不相关）。 | **A**（检索未命中） | 金融系统大量业务状态流转以"状态字段 + 散落判断"存在，这块必须自建 |
| **G-09** | **BPMN 标准格式的自动写入端（逆向结果 → 合法 BPMN XML）** | **证据不足**。A 类可导出 BPMN 但输入必须是事件日志；C 类的时序图工具输出 draw.io / PlantUML，不是 BPMN XML；bpmn-js 是渲染/编辑库，不含"从调用链生成 BPMN"的逻辑。 | **A** | 若客户要求交付物为 BPMN 文件，需自建"调用链/执行顺序 → BPMN XML"的转换器，并做 XSD 校验 |
| **G-10** | **跨约 50 个微服务的端到端业务流程拼接** | **无匹配**。C 类静态分析工具的输入一律是单构建单元／单仓（class/jar/war/jmod、单一源码目录、classpath），跨进程调用只能靠 ① OTel 分布式追踪 ② MQ topic／接口契约 ③ 网关日志 ④ 人工拼接。检索未命中"多仓静态调用图 → 跨服务流程模型"的开源实现。 | **A**（各仓「输入要求」直证 + 检索未命中） | **高**。这是 v3 规模口径下最硬的约束（K-1）：50 微服务意味着**纯静态路线无法得到端到端业务流程** |
| **G-11** | **多仓／多服务扫描结果的聚合层** | **无匹配**。ArchGuard 与 jQAssistant 均为"单仓扫描入库"；50 个微服务需 50 次扫描 + 一个聚合视图，而"服务名 ↔ 仓库 ↔ 数据库 ↔ 接口"的对齐逻辑无公开件。 | **A**（检索未命中 + 各仓文档的单机/单仓定位） | **中—高**。需自建聚合层，否则无法形成客户可评审的端到端视图 |
| **G-12** | **面向"逆向出的业务流程 vs 客户认定流程"的开箱即用差异清单模板与评审会流程包** | **无匹配**。存在可组装的通用件（`bpmn-js-differ` 模型 diff、PM4Py/ProM 一致性检查、`OpenFastTrace` 条目追溯、IEEE 1028 评审标准、Example Mapping 卡片法），但**没有**把四者组合成"逆向结果确认"专用工件的公开项目或模板。 | **A**（检索未命中；各通用件的存在已由 E-41～E-47 直证） | **中**。AC-05 的三要素可达成，但**需自建组装**，不能采购现成流程包 |
| **G-14** | **「客户人工判断的重点交易与重点场景」→「代码入口集合」的映射** | **无匹配**。86 条候选中 71 条支持把输入切片到指定范围，但**切片入口一律是技术语言**（包名/路径/入口方法/tag/流程定义 key），而客户给出的是业务语言。检索未命中任何"业务场景描述 → 代码入口定位"的开源实现；学术侧对应问题为 **feature location**，其工具（Feather、Sando）**无维护中的开源实现**（与 G-04 交叉印证）。 | **A**（多轮检索未命中 + §9.6 逐条切片能力标注） | **高**。这是 v4 冻结的「仅关键业务流程」路线的**真正瓶颈**——不在工具能否切片，而在**谁来把业务场景翻译成代码入口**。缓解：v4 允许差异清单以「后续人工处理」收口，映射不确定项不阻断评审会结论 |
| **G-13** | **差异清单粒度与评审会分期口径** | **证据不足**。粒度（按流程一条／按业务规则一条）与形式（单次总评审／分期）在公开实践中两种都存在，无定论；v3 亦标「待回源」。50 微服务规模下必然分期，但"如何切分评审批次"无公开方法。 | **B** | **中**。影响 AC-07「无未处置差异」的可判定性，需 R1 在 AC 中固化口径 |

---

## 13. 数据来源与复现方法

**采集方式**（全程只读：未 checkout 任何第三方仓库、未安装依赖、未编译第三方代码、未改动 `reverse_engineering` 仓库）：

1. **仓库元数据（主）**：GitHub REST API `GET https://api.github.com/repos/{owner}/{repo}`，逐仓取 `license.spdx_id`、`license.name`、`stargazers_count`、`pushed_at`、`created_at`、`archived`、`language`、`description`、`homepage`。
   - **v1 轮**：发起 **81 次**仓库路径核验，其中 **5 个路径返回 404**（`apromore/apromore-community`、`SecureSoftwareEngineering/FlowDroid`（org 名大小写有误，正确为 `secure-software-engineering/FlowDroid`）、`structurizr/dsl`、`C4-DSL/structurizr`、`Adrninistrator/java-triplea-analyse`），**1 个因配额返回 403**（`eclipse-tracecompass/tracecompass`，正确路径为 `eclipse-tracecompass/org.eclipse.tracecompass`，配额恢复后复核成功）。
   - **v2 轮（patch-01 新增，H 类与确认实践）**：再发起 **14 次**核验，其中 **2 个返回 404**（`bpmn-io/bpmn-js-modeling-feedback`、`strictcoders/strictdoc`），**均已从正文剔除，未作为候选交付**。
   - 两轮合计 **95 次**仓库路径核验。所有 404 一律剔除或改标「待回源」，**未把 404 路径当作可访问 URL 交付**。快照时间 **2026-10-08**。
2. **补充元数据**（core 配额耗尽后）：GitHub Search API `GET https://api.github.com/search/repositories?q=...`，返回同一组字段。本文标注"GitHub API（Search）取值"者来自此路径；关键项已在配额恢复后用 Repos API 复核（见 `repos2.json`）。
3. **发现式检索**：GitHub Search API 按类别关键词 + 限定符（`user:` / `org:` / `in:name`）检索，v1 轮 **58 组**（`search_gh.py` 10 + `search_gh2.py` 10 + `search_gh3.py` 12 + `search_gh4.py` 10 + `search_gh5.py` 10 + `search_gh6.py` 6）+ v2 轮 **10 组**（`search_gh7.py`）= **共 68 组查询**（依留档脚本计数，v3.2 未重跑任何检索）；辅以通用 Web 检索（官方文档、标准页、论文、厂商页面、实践博客）。
4. **URL 可达性验证**：`curl -sI` / `curl -s -o /dev/null -w "%{http_code}"`。
   ⚠️ **本次运行环境的网络限制（如实披露，影响"URL 可访问性"这一验收项的举证方式）**：
   - **不可达**：`github.com` 的 HTML 页面（连接失败，返回 000）、`git ls-remote https://github.com/...`（失败）、`*.github.io`（一律 404）、`docs.camunda.org`、`pm4py.fit.fraunhofer.de`、`jqassistant.org` / `docs.jqassistant.org`（均连接失败）。
   - **可达并返回 200（本研究已直接验证）**：`api.github.com`、`raw.githubusercontent.com`、`docs.joern.io`、`docs.spring.io`、`bpmn.io/license/`、`link.springer.com/chapter/10.1007/978-3-642-38484-4_8`、`pmc.ncbi.nlm.nih.gov/articles/PMC7163505/`、`processintelligence.solutions/pm4py`、`tai-e.pascal-lab.net`、`docs.structurizr.com`、`docs.openrewrite.org`、`moderne.io/case-studies`、`cran.r-project.org/web/packages/bupaR/index.html`。
   - **域名可达（200）但深路径返回 404**（无法区分是路径变更还是环境代理拦截，一律标「待回源」）：`camunda.com`、`vfunction.com`、`celonis.com`、`codescene.com`、`docs.moderne.io`、`www.eclipse.org`。
   - **返回 403 / 405**：`salesforceben.com`（403）、`ui.adsabs.harvard.edu`（405）。
   因此举证方式调整为：**候选条目的 URL 一律以 `api.github.com/repos/{owner}/{repo}` 的返回（200 + `html_url` + `license` + `pushed_at` + `archived`）作为"该 URL 真实存在且指向该项目本身"的一手证据（A 级）**——这比在浏览器里打开 HTML 页面更强，因为它是 GitHub 自身的权威返回；非 GitHub 的文档/博客/论文链接则**逐条标注本环境的实测 HTTP 状态码**，未能直证者一律标「待回源」并把证据等级降为 B。**测试工程师抽查时请在正常网络环境下复核所有标「待回源」的链接，以及全部 `github.com` 链接的 HTML 可达性。**
5. **交叉验证**：关键结论（归档状态、EOL、许可证冲突）至少两个独立来源；单源结论已在正文标注「待回源」或降级为 B/C 级；相互冲突的证据（bupaR 许可证、ArchGuard 许可证、JavaParser/Spoon 双许可）在表中**并列呈现，未做选择性引用**。

---

## 14. 不确定性与开放问题

### 14.1 「待回源」清单（v3.2：17 项未决 + 1 项已关闭）

**已关闭项**：原任务卡的「中型项目结构口径待回源」——已由 TSK-45 v4 冻结为「约 20 模块 / 约 50 微服务 / 总代码量约 20 万行」，本版按此口径完成 §8 规模适用性评估，**该项关闭**。

| # | 待回源项 | 冲突 / 缺失内容 | 建议核验动作 |
|---|---|---|---|
| 1 | `apromore/ApromoreCommunity` | 官方文档与检索结果多处引用该路径，但 GitHub Repos API 返回 **404**；实际可访问的开源仓为 `apromore/ApromoreCore`（已归档） | 在正常网络环境打开该 URL，确认是重定向、私有化还是已删除；据此修正 A 类第 2 行 |
| 2 | `bupaverse/bupaR` 许可证 | GitHub API 返回 **NOASSERTION**；README 与 CRAN 页标注 **MIT** | 查看仓库根目录 LICENSE 文件原文 |
| 3 | `adamtornhill/code-maat` 许可证 | GitHub API 未检出许可证文件；历史资料称 GPL | 查看仓库 LICENSE；若无，则默认保留所有权利，商用需作者授权 |
| 4 | `archguard/archguard` 许可证 | GitHub API 返回 **MIT**；官方文档页自称 **MPL-2.0** | 查看仓库 LICENSE 文件原文 |
| 5 | `javaparser/javaparser` 与 `INRIA/spoon` 许可证 | API 均返回 **NOASSERTION**；两者 README 自述双许可（JavaParser：LGPL-2.1 **或** Apache-2.0；Spoon：CeCILL-C v2.0 与 LGPL） | 查看 LICENSE 与 "license choice" 说明，确认能否**单方选择 Apache-2.0**（对客户交付影响重大） |
| 6 | `WPS/egon.io` 许可证 | GitHub API 未检出许可证；关联仓 `WPS/egon.io-website` 为 GPL-3.0，官方文档站称 GPLv3 | 查看主仓 LICENSE 文件 |
| 7 | `Adrninistrator/java-all-call-graph-server` 许可证 | GitHub API 未检出许可证，与主仓 Apache-2.0 不一致 | 查看仓库 LICENSE 文件 |
| 8 | `feststelltaste/awesome-agentic-software-modernization` 许可证 | GitHub API 返回 NOASSERTION / "Other" | 查看仓库 LICENSE 文件（同作者的另两份清单为 CC0-1.0，可能只是漏加） |
| 9 | **Blarify-Next** 仓库地址 | 仅在 `blarApp` org 的 GitHub Discussions 公告中提及，未定位到仓库 | 在 `blarApp` org 下检索；确认 v2 归档后 Java 支持的延续性与成熟度 |
| 10 | `SootUp` API 稳定性、`ArchGuard` 主仓与已归档 `scanner` 的版本耦合、`Eclipse Trace Compass` 的 OTel 接入方式、`gen-java-code-uml-sequence-diagram` 对新版 Java/Spring 的兼容性 | 四项均为"文档未明说、需实测"的能力边界 | 纳入 §16 建议的 PoC 任务卡 |
| 11 | **非 GitHub 引用链接的环境可达性**（11 处） | 本研究环境无法区分「路径已变更」与「代理拦截」：`soot-oss.github.io/sootup/`（404）、`camunda.com/blog/2025/10/…`（404）、`docs.camunda.org/manual/7.24/…`（连接失败）、`pm4py.fit.fraunhofer.de/…`（连接失败）、`vfunction.com/modernization-platform/`（404）、`celonis.com/products/process-intelligence/`（404）、`codescene.com/blog/behavioral-code-analysis-explained`（404）、`docs.moderne.io/user-guide/modernize-with-confidence/`（404）、`www.eclipse.org/projects/news/`（404）、`salesforceben.com/…`（403）、`ui.adsabs.harvard.edu/…`（405） | 在正常网络环境下逐条复核；确实失效者替换为等价一手来源（仓库 README、官方 EOL 公告的其他镜像、IEEE Xplore 文档号 7019906） |
| 12 | `chaabani-anis/mikado-method` 许可证 | GitHub API **未检出 LICENSE**；方法原始站点 `mikadomethod.org` 在本环境**连接失败** | 查看仓库 LICENSE；在正常网络下核对方法原始站点与出处（Brolund & Ellnestam） |
| 13 | `LivingDocumentation/awesome-living-documentation` 许可证 | GitHub API 返回 **NOASSERTION** | 查看仓库 LICENSE 文件 |
| 14 | **IEEE 1028-2008 标准正文的具体条款编号** | 标准页面 **HTTP 200 已验证**，但正文需购买；本报告引用的"五类评审、进入/退出准则、异常处置"来自页面摘要与二手资料 | 取得标准正文后回填条款编号；或改用可公开获取的等价评审规程 |
| 15 | **Fagan Inspection 的一手出处** | `en.wikipedia.org/wiki/Fagan_inspection` 在本环境**连接失败**；原始论文为 Fagan, M.E. (1976), *Design and Code Inspections to Reduce Errors in Program Development*, IBM Systems Journal | 在正常网络下核对论文 DOI 与页码；本报告已改用 IEEE 1028 作为可直证的标准依据 |
| 16 | `jboz/living-documentation` 的默认分支与文档 | raw README 以 `master` 分支取用返回 **404**（仓库存在性与许可证已由 API 直证：Apache-2.0，48★，2026-01-26） | 确认默认分支名（`main`/`master`）后重取 README |
| 17 | **§9.6 的 63 条「推断」级切片输入能力标注** | 受本卡「只读调研、不安装依赖、不编译第三方代码」约束，86 条候选中 **63 条**的范围限定能力系依据已采集的能力描述与常规用法**推断**、未实测（直证 14 条、不适用 9 条） | 纳入 §16 建议的 PoC 任务卡：在公开遗留样本上逐条验证范围限定参数能否真的把输入收窄到客户指定的业务场景 |

### 14.2 开放问题

#### 14.2.1 原 xiao 待答两项 —— **已由 CHANGE-03（2026-10-08 10:38）闭环，v4 冻结**

| # | 问题 | xiao 的答复（v4 冻结口径，逐字转述其要义） | 本版落点 |
|---|---|---|---|
| **Q-x1**（已闭环） | 全部业务流程都走确认，还是仅关键流程？「关键」如何界定？ | **仅关键业务流程**；「关键」= **客户人工判断**的「一些重点交易和场景」；**研究方不预设界定标准** | §1.1 第 ⑦ 行术语；§9 引言②；§9.1（**已删除 v2 中研究方自拟的"核心域／高频变更／资金与合规"预设判据**，改为「客户判断时可参考的公开素材」，并明示界定权在客户）；§9.6（切片可行性地面） |
| **Q-x2**（已闭环） | 「准确」的达标判定口径？ | 差异清单**允许存在未决项**，只要**标注为「后续人工处理」**；**评审会结论为「通过」或「有条件通过」**即达标 | 全文第三态术语统一改为 **「标记后续人工处理」**（13 处）；§9 引言④；§9.5 ④ 行；§17.1 AC-07 行按 v4 判定口径改为「**无未标注处置**的差异项」 |

#### 14.2.2 需 R1 / R2 确认的技术前提（3 个）

1. **目标系统是否已使用工作流 / 规则 / 状态机引擎？**（Flowable / Activiti / Camunda / Drools / LiteFlow / Spring Statemachine）
   —— 这是唯一能让 F 类工具给出「**直接**」级业务流程证据的前提（结论 C-10）。若答案为"是"，方案重心与工期会完全不同。**建议 R1 在需求阶段向客户确认。**
2. **是否存在可用的运行环境与可回放的流量？**
   —— 决定 G-01 这座桥能否走 OTel 插桩路线（可行性高、证据强），还是只能走"从调用图合成伪事件日志"路线（无公开实现，风险高）。**建议 R1 / R2 共同确认。**
3. **源码能否出域？可用的 LLM 部署形态是什么？**（公有云 API / 私有化开源模型 / 客户内网推理）
   —— 直接决定 E 类整类是否可用，以及 Potpie / Blarify / Continue 的部署形态。**建议 R1 在 AC 中固化为约束。**

### 14.3 方法层面的不确定性

- **GitHub API 配额限制**：未认证 API 每小时 60 次 core 请求、每分钟 10 次 search 请求。本次 **95 次**仓库路径核验分**三批**完成（`repos.json` 50 + `repos2.json` 31 + `repos3.json` 14，即 §13 第 1 点所述「v1 轮 81 次 + v2 轮 14 次」的同一计数；Repos API + Search API），批次间取值时间存在跨度（跨 GitHub API 配额窗口）；`stargazers_count` 等字段为**时点快照**，非稳定值（例：`flyway/flyway` 两批取值分别为 10127，`microsoft/graphrag` 为 36253→36254）。
- **`pushed_at` 的语义局限**：它反映"最后一次推送到默认分支"，不等于"项目在维护"（可能是 bot 提交或文档改动）；也不反映 release 节奏。判断活跃度应结合 release 历史与 issue 响应；本次**未逐仓核验 release 列表与 issue 响应速度**（配额所限），仅对关键项单独标注 release 信息（如 PM4Py v2026.10.0）。
- **`archived` 与"实际停更"不等价**：`spring-projects/spring-statemachine` 在 GitHub 页面仍显示近期提交记录，但 API 返回 `archived=true` 且 homepage 指向 spring-attic；反之 `phodal/coca`（2026-01-06）未归档但更新频率低。两者需结合判断。
- **star 数不应作为选型依据**：`java-all-call-graph`（572★）、`mybatis-mysql-table-parser`（4★）star 数低但功能贴合度高；反之 `aider`（49421★）、`Repomix`（28745★）star 数高但与"业务流程反推"关系弱。本文列出 star 数仅因其为**可核数据**。
- **中文项目的文档证据密度高但第三方验证少**：`Adrninistrator` 系列的场景文档完整（A 级），但"已被 vivo/自如/携程应用"等采用度陈述只有作者自述（B 级），未独立验证。

---

## 15. 可复用素材清单（含来源路径）

| 素材 | 来源 | 可直接用于 |
|---|---|---|
| 70 条主候选 + 16 条次级候选的 12 字段结构化数据 | 本文 §5 八张表（A–H）+ 次级候选表 | R2 的技术路线对比输入；R1 的 AC 起草（哪些能力可承诺、哪些不可） |
| 58 条证据矩阵（结论 ↔ 来源 ↔ 日期 ↔ 等级） | 本文 §10 | 方案评审时的溯源；对 R8（挑战者）质询的应答材料 |
| 18 条可复现验证线索 | 本文 §11 | 测试工程师抽查执行清单（AC-08） |
| 五类业务资产 × 逆向输入矩阵 | 本文 §7 | R1 起草 AC-03 相关条款；R2 判断每类资产的自建量 |
| 三类产物映射（工具／方案·方法论／实施流程） | 本文 §6 | AC-04 的直接举证材料 |
| 客户确认实践包（差异清单三条生成路径 + 评审会标准依据 + 三态处置载体） | 本文 §9 | 「实施流程」章节中"与客户确认业务流程"环节的素材；可直接复用 IEEE 1028 / Example Mapping / OpenFastTrace / bpmn-js-differ 四个既有实践 |
| 规模适用性评估（K-1～K-3 三条硬约束 + 逐类适用性） | 本文 §8 | R2 判断 50 微服务口径下的路线可行性；R1 校准可承诺范围 |
| 14 条缺口结论（G-01～G-14） | 本文 §12 | R2 判断"必须自建 / 必须采购"的边界；R1 定义非目标 |
| 17 项未决 + 1 项已关闭的「待回源」清单 | 本文 §14.1 | 下一轮研究任务卡的输入 |
| 开放问题（xiao 原待答 2 项**已由 CHANGE-03 闭环**，见 §14.2.1 + R1/R2 待确认技术前提 3 项，见 §14.2.2） | 本文 §14.2 | R1 与 xiao／客户沟通的问题清单 |
| 采集脚本与 API 原始返回 | `fetch_repos.py`、`verify2.py`、`search_gh*.py`、`repos.json`、`repos2.json`、`gh_search*.json`（本研究运行目录，**非仓库产物**） | 复现本次快照；下一轮增量核验 |
| 公开遗留系统样本清单 | https://github.com/legacycoderocks/awesome-legacy-code | PoC 测试床取样（避免首轮就拿客户代码验证） |
| 金融业务本体（术语对齐锚点） | https://github.com/edmcouncil/fibo | "代码 → 业务语言"映射的目标词汇表 |
| AI agent 现代化资料入口 | https://github.com/feststelltaste/awesome-agentic-software-modernization | E 类路线的长尾查漏 |
| 遗留系统方法论入口 | https://github.com/feststelltaste/awesome-legacy-systems | G 类路线的长尾查漏（含"逆向工程工具"分节） |

---

## 16. 下一步研究建议（供 R0 派发；本卡不执行）

1. **专项 PoC 研究（建议独立任务卡，需可运行环境）**：在 `awesome-legacy-code` 提供的公开 Java 遗留样本上，实测 `java-all-call-graph` 对 Spring AOP / `@Scheduled` / 反射 / MQ 监听的调用链覆盖度（对应 **G-07**），产出量化的"断链率"数据。这是本报告唯一无法靠只读调研回答的关键问题。
2. **许可证专项（建议交法务 + R2）**：对 §14.1 的许可证缺失/冲突逐条回源 —— **按 §14.1 条目计 9 处**（#2、#3、#4、#5、#6、#7、#8、#12、#13）／**按仓库计 10 处**（其中 **#5 同时含 `javaparser/javaparser` 与 `INRIA/spoon` 两个仓库**，故两口径相差 1），并针对"**作为客户交付物的一部分分发**"这一具体场景出具意见。重点：PM4Py（AGPL-3.0）、jQAssistant（GPL-3.0）、CodeQL CLI（专有）、bpmn-js（自定义署名）、Chapi/Coca（MPL-2.0）、以及 4 个**未检出 LICENSE** 的仓库。
3. **金融语境案例研究（建议独立任务卡）**：定向检索国内银行/保险科技公开技术分享（InfoQ、QCon、ArchSummit、各大厂技术公众号）中"存量核心系统业务流程梳理"的实践，补 **G-05** 缺口；预期以 B 级证据为主。
4. **确认环节的工件组装预研（对应 G-12）**：验证"`bpmn-js-differ` 或 PM4Py conformance → 差异清单条目 → `OpenFastTrace` 追溯 + 三态处置 → 评审会材料 → Cucumber/活文档固化"这条组装链在真实工件上能否走通；同时确认 OpenFastTrace 的 GPL-3.0 在客户交付场景下是否可接受（若不可，需寻找 Apache/MIT 的等价追溯载体）。
5. **G-01 桥接方案可行性预研**：调研"OTel span → XES 事件日志"的转换实现代价（字段映射、case id 构造、activity 命名策略），以及"调用图/方法执行顺序 → 伪事件日志"的可行性。这是决定 A 类能否用起来的唯一路径，也是 **G-02 / G-09** 的前提。

---

## 17. 本轮结论（固定收尾格式）

- **研究问题**：存量 Java 系统反向推导业务流程，在 GitHub 公开生态里的可用地面有哪些、缺什么。
- **子课题完成度**：**S1–S8 全部完成（8/8）**。
- **交付物完成度（v3，按 TSK-45 **v4 frozen** 全 10 条 AC 基线）**：见 §17.1 逐条自检。
### 17.1 v4（frozen）全 10 条 AC 自检

> 说明：本卡是**只读的工具与方法盘点**，不接触目标系统源码。因此 AC-06／AC-07 这类**需要对真实系统产出具体业务流程条目**的 AC，本卡**无法直接满足**——下表如实标注「不适用／由后续实施阶段交付」并说明本卡提供了什么地面，**不虚报达标**。

| AC（v4） | 要求要点 | 本版落点 | 判定 |
|---|---|---|---|
| **AC-01** 输入前提与语境 | 唯一输入前提＝已取得源码的存量 Java 系统；规模＝约 20 模块／50 微服务／20 万行；语境＝金融软件且同时覆盖「技术成熟／架构规范」与「业务复杂」；非目标含「不做软件破解」「不处理无源码场景」「正向代码生成不在本研究范围」 | §1.1 输入前提表（7 行，含规模口径与金融语境）；非目标三条见 §1.1 第 ⑥ 行（NG-01／NG-02／NG-07）与 §5 各条「商用与合规风险」列（不涉破解、以已有源码为前提） | **齐全**（四项均在） |
| **AC-02** 唯一目标 | 目标唯一表述为「Java 工程 → 逆向解析成业务资产 → 客户方业务专家确认关键业务流程（差异清单 + 评审会）」，全文不含正向代码生成类目标 | §1 首句即该唯一目标句式；全文「正向」仅出现在 **NG-07 范围声明**与 **patch-01 修订 1 的零变更确认**中，无任何正向生成目标或工具 | **单一目标且无正向生成** |
| **AC-03** 业务资产五类 | 含五类资产，且**每类标注可得它的逆向输入**（源码／字节码／日志／数据库结构） | §7 五类资产 × 逆向输入矩阵（每类列出逆向输入、覆盖它的候选、覆盖度、缺口编号）；§5 全部候选表第 11 列「可输出业务资产类型」（多选，86 条全覆盖） | **五类齐全且各有逆向输入** |
| **AC-04** 三类产物 | 工具／方案·方法论／实施流程三类，**每类 ≥3 条**，每条含「输入要求」与「反推能力评级（直接／间接／需二开）」 | §6.1 工具类（13 行、覆盖 60+ 件）；§6.2 方案·方法论类（10 条）；§6.3 实施流程类（P-01～P-06，6 条）；三表均含该两字段 | **三类各 ≥3 且字段齐全** |
| **AC-05** 客户确认环节 | 实施流程含独立确认环节，写明 主体＝客户方业务专家／**对象＝关键业务流程（客户人工判断，研究方不预设标准）**／形式＝差异清单＋评审会／处置规则三态 | §6.3 的 P-04／P-05 即该独立环节；§9 全节展开；**§9.5 四要素逐条自检表**；§9.1 明示研究方**不预设**「关键」标准 | **四要素齐全** |
| **AC-06** 关键业务流程清晰性 | 每条关键业务流程以统一结构描述（触发条件／参与模块／数据实体／业务规则／异常分支 ≥5 字段）并标注源码证据位置 | **本卡不适用**：本研究为只读工具盘点，未获目标系统源码，不产出任何具体流程条目。本卡提供的是**字段供给地面**——§6.4 给出五个字段各自可由哪些候选供给、以什么形态落到「文件:行号／表.列／规则 ID／BPMN 元素 ID」 | **不适用（由后续实施阶段交付）**；地面已提供 |
| **AC-07** 确认闭环／准确性 | 差异清单覆盖关键业务流程的差异项；每项标注处置结论（三态，第三态为「标记后续人工处理」）；评审会结论为「通过」或「有条件通过」；判定＝**无未标注处置的差异项** | **本卡不适用**（无真实差异清单可产出）。本卡提供的是**机制地面**：§9.2 三条差异清单生成路径（模型 diff／conformance fitness／条目追溯）、§9.3 评审会标准依据（IEEE 1028-2008）与第三态的既有实践形态（Example Mapping 的 Questions 卡片、Cucumber `pending`）、§9.4 处置状态的持久载体（OpenFastTrace） | **不适用（由后续实施阶段交付）**；机制地面已提供且与 v4 三态术语一致 |
| **AC-08** 证据与可复现 | 数据性陈述附来源链接，未核实标「待回源」；≥5 条候选附可复现验证线索 | §10 证据矩阵 **58 条**（链接 + 日期 + 等级）；§11 可复现验证线索 **18 条**；「待回源」**17 项未决 + 1 项已关闭**（§14.1）；§9.6 明示 63/86 条切片标注为**推断**、未实测 | **两者同时满足** |
| **AC-09** 缺口诚实性 | 含「缺口结论」章节，≥1 项公开生态未覆盖，且该项不在候选清单中重复出现 | §12 列 **G-01～G-14 共 14 条**；逐条核对：14 项缺口均未作为候选出现在 §5／§6（缺口＝「无匹配」的能力，候选＝「已存在」的项目，两集合无交集） | **≥1 项且不重复** |
| **AC-10** 边界合规 | 不含具体工具／框架推荐、实施方案排序结论，也不含正向代码生成工具的推荐或集成方案 | 全文无推荐语与优先级排序（已用关键词扫描核验：无「推荐使用／建议采用／首选／优先选」等表述）；§6.3 P-01～P-06 为并列罗列；§9.1 两类确认范围并列且明示不做推荐；无任何正向生成工具推荐或集成方案 | **无上述内容** |

**本卡可直接判定为达标的 AC**：AC-01、AC-02、AC-03、AC-04、AC-05、AC-08、AC-09、AC-10（**8 条**）。
**本卡不适用、由后续实施阶段交付的 AC**：AC-06、AC-07（**2 条**）——原因是本卡为只读工具盘点、未获目标系统源码；本卡已分别提供 §6.4（五字段供给地图）与 §9.2～§9.4（差异清单与处置机制地面）作为其输入。

- **结论与置信度**：16 条结论（C-01～C-16）—— **高置信度 12 条**（C-01 / C-02 / C-03 / C-04 / C-06 / C-09 / C-10 / C-11 / C-12 / C-13 / C-14 / C-16）、**中高 3 条**（C-05 / C-07 / C-15）、**中 1 条**（C-08）。
  **核心判断**：公开生态能提供「**程序事实抽取**」的完整地面（不需自研），但**不能**提供「**业务流程语义**」的完整地面；两者之间的桥（代码→事件日志、代码→业务术语、调用链→BPMN）**必须自建**。
- **证据等级分布**：§10 证据矩阵 **58 条** —— **A 级 50 条**、**B 级 8 条**（E-06 / E-09 / E-17 / E-19 / E-20 / E-21 / E-22 / E-30）；其中 E-04／E-12／E-24／E-43／E-45／E-49／E-51／E-54／E-58 的部分子结论单独降级标为 **B 或 C 级**（已在该行内注明）。§12 的 **14 条**缺口结论中 A 级 10 条、B 级 4 条。**A 级证据的主体是 GitHub REST API 的原始返回与本环境实测的 HTTP 状态码**，不依赖浏览器可达性。
- **仍开放的不确定性**：**17 项「待回源」未决 + 1 项已关闭**（§14.1；「中型口径」项已随 v4 冻结关闭；第 11 项汇总 11 个非 GitHub 引用链接的环境可达性问题；新增第 17 项为 §9.6 的 63 条推断级切片标注需实测）。**原 xiao 待答 2 项（Q-x1／Q-x2）已由 CHANGE-03 于 2026-10-08 10:38 闭环**，答复要义与本版落点见 §14.2.1，本报告**无待 xiao 答复项**；需 R1/R2 确认的技术前提 3 项（§14.2.2）；**G-07（隐式调用覆盖度）、G-10（跨 50 微服务拼接）、G-11（多仓聚合层）、G-14（业务场景→代码入口映射）四项必须实测或自建才能回答**。
- **建议的下一步**：**移交 R1 与 R2 决策**（xiao 的 Q-x1／Q-x2 已由 CHANGE-03 闭环，本报告无待 xiao 答复项）。
  1. **R1**：回答 §14.2.2 的三个技术前提（尤其 Q1「是否已用工作流/规则/状态机引擎」，它决定是否存在"直接"级路径）；并把 v4 的「关键业务流程由客户人工判断」落成客户侧的**场景清单交付物**（这是 G-14 的输入）。
  3. **R2**：据 §7 覆盖度不均衡结论与 §8 三条硬约束（K-1 跨服务 / K-2 上下文溢出 / K-3 数据不出域），在「组合式自建 / 商业平台采购 / LLM agent 流水线」三条路线间做技术裁决；§12 的 G-01／G-02／G-09／G-10／G-11／G-12 是必须自建或采购的边界。
  4. **R0**：如需 G-07／G-10／G-11 的量化数据，另派专项 PoC 任务卡（需可运行环境与多仓样本，超出本卡「只读调研」约束）。
  5. **状态说明**：TSK-45 **v4 已冻结**（2026-10-08 10:39），patch-01 的「不进 REVIEW」前提已解除；本版为 patch-02 三项增量补齐后的 **v3**，交付后置 `in_progress`，等协调智能体做结构核对。

---

*本报告是**输入**，不是方案定稿。所有"该用哪个工具、实施顺序怎么排、工期多少、能不能承诺准确率"的判断，均留给 R1（需求与 AC）与 R2（技术裁决）。*
