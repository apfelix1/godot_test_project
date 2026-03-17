# 任务清单

> 本文件是当前任务面板，不负责记录长期规则。
> 项目规则看 `AGENTS.md`，当前真实状态看 `docs/project_status.md`，上一棒交接看 `docs/ai_handoff.md`。

## Sprint 状态机

- `draft`：需求和规格已明确，尚未正式开工
- `in_progress`：正在开发或处理中
- `code_complete`：代码与本地验证完成，待并入
- `merged`：已并入主线，并完成必要记录

## 使用规则

- 同一时间优先只有一个 `in_progress` 的主功能 Sprint
- 如果没有 `in_progress`，从 Backlog 顶部挑选下一个 `draft`
- 代码类 Sprint 在进入实现前应有明确的“目标 / 不做什么 / 允许修改文件 / 完成标准 / 验证方式”
- 结束一轮工作后，如状态变化，立即更新本文件

## MVP 进度总览

目标：建立第一个可运行的原型闭环
状态：draft

| 工作项 | 来源 | 状态 | 阻塞项 |
|------|------|------|--------|
| 多 AI 协作文档基础 | `AGENTS.md` / `docs/project_status.md` / `docs/tasks.md` / `docs/ai_handoff.md` | merged | |
| 最小可运行基线 | `docs/project_status.md` | draft | 尚无主场景与 `run/main_scene` |
| 玩家控制原型 | `docs/gdd.md` / `docs/tdd.md` | draft | 先完成最小可运行基线 |

## 当前 Sprint

当前没有 `in_progress` 的 Sprint。

开始新 Sprint 时，优先从 Backlog 选择一个 `draft`，将其状态改为 `in_progress`。

## Backlog

### Sprint: minimal_runnable_baseline

- 状态：`draft`
- 类型：`code`
- 建议执行者：Codex / Claude Code
- 目标：补出第一个可运行主场景和最小闭环，让项目进入“可以验证运行”的状态
- 不做什么：
  - 不做正式美术
  - 不做联网
  - 不做完整 UI
  - 不做存档和完整游戏循环
- 允许修改文件：
  - `project.godot`
  - `source/`
  - `tests/`
  - `docs/project_status.md`
  - `docs/ai_handoff.md`
- 完成标准：
  - 存在可运行主场景
  - `project.godot` 已配置 `run/main_scene`
  - 有最小玩家或占位实体移动
  - F5/F6 运行无明显启动错误
- 验证方式：
  - 在 Godot 中运行主场景
  - 如已补测试脚手架，则执行最小 headless smoke test

## 试玩反馈

当前暂无灰盒试玩记录。

## 已完成归档

### Sprint: multi_ai_collaboration_foundation

- 状态：`merged`
- 类型：`docs`
- 目标：把仓库升级为可被多个 AI 工具稳定接手的协作结构
- 已完成：
  - 建立 `AGENTS.md` 权威入口
  - 建立 `project_status.md` / `ai_handoff.md` / `web_brief.md`
  - 将 `tasks.md` 升级为统一状态机
  - 对齐 workflow 与 manuals 的主要入口和术语
