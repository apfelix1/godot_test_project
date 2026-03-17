# Changelog

## v0.0.6 — 2026-03-18
### 新增
- `AGENTS.md` 作为仓库级唯一权威规则入口，明确多 AI 协作模式、接手顺序、任务类型、Sprint 状态机和统一执行闭环
- `docs/project_status.md` 作为“当前真实状态”快照，区分设计设想与已落地事实
- `docs/ai_handoff.md` 作为 AI 交接记录，支持多工具低损耗接力
- `ai/context/web_brief.md` 作为给 ChatGPT / Claude web 等不能直接读仓库模型的一页简报

### 改进
- `CLAUDE.md` 降级为 Claude / Claude Code 兼容入口，并明确以 `AGENTS.md` 为准，避免双 source of truth
- `README.md` 改为指向多 AI 协作入口：`AGENTS.md`、`project_status.md`、`tasks.md`、`ai_handoff.md`
- `docs/tasks.md` 升级为统一 Sprint 状态机：`draft / in_progress / code_complete / merged`
- `docs/dev_workflow.md` 重写为多 AI 协作总览，明确文档职责分工、角色矩阵、接手顺序和文档更新规则
- Phase 0 手册对齐新协作结构，并修正 Step 7 / Step 8 的顺序问题：MVP 进度总览改为在 Step 8 之后生成
- Track A 手册改为基于 `AGENTS.md`、`project_status.md`、`tasks.md`、`ai_handoff.md` 的接手模型
- 迭代手册统一接入新状态机和交接模型
- 迭代手册 Path B 从旧的 2D 资源导入思路重写为 3D 资源流程（models / textures / materials / audio / fonts / data）
- Phase 0 美术方向示例从 2D 像素项目措辞调整为更符合当前 3D 项目方向的示例

### 修复
- 清理 manuals 中把 `CLAUDE.md` 当唯一主入口的旧表述
- 清理 manuals 和 workflow 中旧的任务状态示例（如“已完成”/emoji 状态）与新状态机不一致的问题
- 补齐多 AI 协作文档之间的引用关系，减少不同工具接手时的上下文漂移风险
- 同步 `docs/gdd.md` 中美术章节的旧 2D / 像素风示例占位，避免与当前 3D 项目方向继续冲突

## v0.0.5 — 2026-03-17
### 修复
- Track B/C 可用时机对齐：Track A 0a 后正式执行，Track B 0a 后可预研（正式执行需 0b），Track C 的 C1（风格预研）可在 0a 后开始、C2-C4 需 0b
- Step 7 prompt "复制 gdd.md 全文"改为按章节引用（0a: 概览/核心机制/游戏循环/P0/HUD；0b: 全部已完成章节），与总纲上下文规则一致
- tasks.md 模板与手册输出格式同步：MVP 总览补上"目标"和"来源"列，Sprint 模板补上"状态"字段
- 跨文档占位措辞统一：Track B/C/D 导航标注改为含前置条件的一致格式
- Phase 0b 总览图去向从"Track C/D 可开始"改为"Track B/C/D 可正式执行"
- 迭代手册 MVP 进度总览示例从旧格式（系统/状态/备注）改为新格式（系统/来源/状态/阻塞项）
- C-4 和 D-4 的 git push 命令加 MVP 阶段限定注释，避免扩容阶段误推 main
- 灰盒试玩复盘编号补回缺失的 2.

## v0.0.4 — 2026-03-17
### 改进
- Step 3/4 prompt 拆为 0a/0b 两套，0a 版限定只做 P0 最小集，不再推向完整设计
- Step 7/8 "你需要准备"拆为 0a/0b，消除 0a 跳过 Step 5/6 却要求其产出的矛盾
- Step 8 质量门拆为 0a/0b，0a 只要求 MVP 系统完整，允许非 MVP 待定
- Step 9 prompt 拆为 0a/0b，0a 版明确"美术/音频/非 MVP 的待定不计入问题"
- git commit 责任收口：迭代模式下 A5 只做 review，commit 统一在 Path C；独立模式保留完整能力
- Track A 必读文件表从 3 行扩充到 7 行，与 Phase 0 入口矩阵完全对齐
- Track B/C/D 从"待编写"改为"暂未启用，Phase 0b 完成后编写"
- dev_workflow 日常节奏区分"任务完成后 F5 验证"和"提交前走 A5 全流程"
- dev_workflow 避坑清单第 10 条从绝对化"只引用不复制"改为区分 agent/web 模型
- 灰盒试玩时机从 Path C 并入后前移到 Path A 完成后、Path C 之前
- Phase 0 开头和完成状态统一为 Track A/B 都只需 0a

### 新增
- Track A 使用模式说明（独立模式 vs 迭代模式）
- docs/tasks.md 五段固定结构：MVP 进度总览、当前 Sprint、试玩反馈、Backlog、已完成归档

## v0.0.3 — 2026-03-17
### 改进
- Phase 0 拆分为 0a（原型初始化）+ 0b（生产初始化），0a 完成即可开始 Track A
- 灰盒试玩移到第一个 P0 功能完成后（需要可运行场景，不能在纯文档阶段做）
- Track 入口条件改为必需章节矩阵，消除 0a "允许待定"与 Track A "不能有待定"的冲突
- Step 7/8 prompt 拆为 0a/0b 独立版本，防止模型过度生成
- 工具链简化：MVP 阶段推荐 ChatGPT + Claude Code 双模型制，Kimi 降为可选
- prompt 引用规则细化：能读文件的 agent 禁止复制，web 模型只复制最小必要章节
- 文档更新精简为 2 次：设计冻结 + 实现偏差，消除 3 次重复更新
- EventBus 通信规则改为决策树：广播→EventBus / 命令→直调 / 父子→信号
- 迭代手册串行规则改为三车道并行：主功能 / 素材调参 / 紧急修复
- 迭代手册路径 A 从 7 步精简为 6 步（合并文档更新到设计冻结）
- Path B 判断规则区分静态素材和行为型数据，后者要求回归验证
- 网络架构改为按需章节，单机游戏可跳过

### 新增
- 灰盒试玩复盘步骤（第一个 P0 功能完成后 + 迭代 A-5 集成验证后）
- Track 入口必需章节矩阵（Phase 0 完成后章节）
- 测试脚手架初始化步骤（第一个 Path A 前创建 tests/ 目录和 smoke_test.gd）
- headless smoke test 推荐（Path C 合流检查清单）
- git 命令 PowerShell 替代版本
- dev_workflow.md 合流检查清单 EventBus 措辞更新

### 修复
- EventBus 分组阈值不一致：迭代手册从 10 修正为 8（与 coding_conventions.md 一致）
- dev_workflow.md 表格渲染问题：MVP 简化注释移到表格外部

## v0.0.2 — 2026-03-16
### 新增
- 迭代手册（docs/manuals/iteration_add_feature.md）：路径 A 新增系统、路径 B 新增素材、路径 C 并入主线、路径 D Bug 修复
- MVP 阶段简化规则和扩容阶段补充规则（含 git 分支策略）
- Phase 0 Step 7 附加步骤：MVP 进度总览表生成
- Phase 0 完成后"第一个功能怎么开始"衔接指引
- tdd.md 网络架构章节占位（合作多人游戏）
- EventBus 事件分类规则（coding_conventions.md）

### 修复
- architecture.md 场景树从 Node2D 修正为 Node3D（匹配 3D 俯视角游戏）
- coding_conventions.md 脚本模板从 2D 节点修正为 3D 节点
- dev_workflow.md 合流检查清单从像素风/2D 修正为 3D 资产

### 改进
- dev_workflow.md 精简为路由中心，Track 详细 prompt 移至各手册，消除重复维护
- 迭代手册与 Track A 手册职责边界明确（项目管理层 vs 执行层）
- Phase 0 产出清单新增 tdd.md 网络架构项

## v0.0.1 — 2026-03-16
### 新增
- Phase 0 用户手册（docs/manuals/phase0_project_init.md）：9 步标准化项目初始化流程
- Track A 用户手册（docs/manuals/track_a_system_code.md）：系统/代码开发完整操作指南

## v0.0.0 — 2026-03-15
### 新增
- 项目初始化：Godot 4.3 项目结构搭建
- 开发工作流文档（docs/dev_workflow.md）
- GDD 模板（docs/gdd.md）
- TDD 模板（docs/tdd.md）
- 架构文档（ai/context/architecture.md）
- 编码规范文档（ai/context/coding_conventions.md）
- CLAUDE.md 项目规则配置
