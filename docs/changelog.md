# Changelog

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
