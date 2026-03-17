# AGENTS.md

本文件是本仓库的 AI 协作总入口与唯一权威规则源。

如果 `AGENTS.md` 与 `CLAUDE.md`、`README.md`、`docs/dev_workflow.md`、`docs/manuals/*`、`ai/context/web_brief.md` 的表述冲突，以 `AGENTS.md` 为准。

## 项目定位

- 项目名：遗迹搬运队 / Ruin Crew
- 引擎：Godot 4.3
- 语言：GDScript
- 类型：3D 俯视角合作探险游戏
- 平台：PC（Windows）

## 这是一个多 AI 协作仓库

同一个仓库可能被以下协作者轮流接手：

- ChatGPT / Claude web：概念讨论、方案比较、文案、流程审阅
- Codex / Claude Code：仓库探索、实现、修复、测试、文档同步
- Kimi 或其他低成本模型：批量数据、模板、清洗、重复性文本生成
- 人类开发者：决策、整合、在 Godot 编辑器中搭场景和调手感

不要假设上一位 AI 和你使用的是同一种工具，也不要假设它已经读过与你相同的上下文。

## 文档职责分工

稳定规则、真实状态、当前任务、交接记录必须分开维护：

| 文件 | 作用 | 是否权威 |
|------|------|----------|
| `AGENTS.md` | 仓库级稳定规则、协作方式、接手顺序 | 是 |
| `CLAUDE.md` | Claude / Claude Code 兼容入口 | 否 |
| `docs/project_status.md` | 当前仓库的真实状态快照 | 是 |
| `docs/tasks.md` | 当前任务面板和 Sprint 状态机 | 是 |
| `docs/ai_handoff.md` | AI 交接记录 | 是 |
| `docs/gdd.md` | 设计意图与玩法目标 | 是 |
| `docs/tdd.md` | 技术设计意图与系统规划 | 是 |
| `ai/context/architecture.md` | 场景树、目录职责、通信约定 | 是 |
| `ai/context/coding_conventions.md` | GDScript 编码规范 | 是 |
| `ai/context/web_brief.md` | 给 web 模型复制粘贴的一页简报 | 否 |

## 接手顺序

能直接读仓库的 AI 接手时，按下面顺序读取：

1. `AGENTS.md`
2. `docs/project_status.md`
3. `docs/tasks.md`
4. `docs/ai_handoff.md`
5. 按需读取 `docs/gdd.md`、`docs/tdd.md`、`ai/context/architecture.md`、`ai/context/coding_conventions.md`

不能直接读仓库的 web 模型：

1. 使用 `ai/context/web_brief.md`
2. 再补当前 Sprint 卡片
3. 只补当前任务必需的 GDD/TDD 摘录

## 现实优先规则

- 不要把设计文档当成“已实现事实”。
- 在声称“项目可运行”前，先检查 `project.godot`、主场景文件和实际脚本。
- 当 `docs/gdd.md` / `docs/tdd.md` 与真实代码或配置不一致时，先以真实代码和配置为准，再决定是否同步文档。
- 当前项目是 3D 顶视角方向。不要在未确认前把资源流程按纯 2D 像素项目处理。

## 当前工作类型

所有工作都应能归入以下类型之一：

- `design`：方案比较、机制收束、文案、流程设计
- `code`：实现、修复、重构、测试
- `review`：代码审阅、文档审阅、一致性检查
- `docs`：规则、状态、任务、手册、交接文档
- `assets`：模型、贴图、材质、音频、UI 资源导入与集成
- `data`：配置表、数值表、批量数据

如果任务不在 `docs/tasks.md` 中，先补一个 `draft` 的 Sprint 或任务卡，再开始大改。

## Sprint 状态机

`docs/tasks.md` 中统一使用以下状态：

- `draft`：需求和规格已明确，尚未正式开工
- `in_progress`：正在实现或处理中
- `code_complete`：代码与本地验证已完成，待并入
- `merged`：已并入主线，并完成必要的记录

不要再使用含糊的“已完成”作为总状态。

## 统一执行闭环

每位 AI 默认按以下闭环工作：

1. Intake：读规则、状态、任务、交接
2. Scope：确认这次只做什么，不做什么
3. Execute：按允许修改的范围工作
4. Verify：执行任务卡要求的验证
5. Sync：更新 `docs/tasks.md`、`docs/project_status.md`、`docs/ai_handoff.md`
6. Handoff：为下一棒留下最小但足够的上下文

## 验证规则

- 文档改动：检查交叉引用、术语一致性、状态机一致性
- 代码改动：优先运行最小相关场景，再运行主场景；无法运行时必须明确说明原因
- 测试结果只能报告你真正执行过的验证，不能脑补

## 文档更新规则

- 项目级稳定规则变化：更新 `AGENTS.md`，必要时同步 `CLAUDE.md`
- 当前真实状态变化：更新 `docs/project_status.md`
- 当前任务状态变化：更新 `docs/tasks.md`
- 一次工作结束：追加 `docs/ai_handoff.md`
- 设计目标变化：更新 `docs/gdd.md`
- 技术设计变化：更新 `docs/tdd.md` 和相关 `ai/context/*`

## 详细流程入口

详细执行流程见：

- `docs/dev_workflow.md`
- `docs/manuals/phase0_project_init.md`
- `docs/manuals/track_a_system_code.md`
- `docs/manuals/iteration_add_feature.md`

这些文件是对 `AGENTS.md` 的展开说明，不是替代品。
