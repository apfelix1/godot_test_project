# Project Status

最后核对日期：2026-03-18

## 当前真实状态

- 仓库目前是“文档先行、代码较少”的状态。
- `project.godot` 目前只有基础 `application` 配置。
- 当前未看到已配置的 `run/main_scene`。
- 当前未看到已配置的 `[autoload]`。
- `source/`、`assets/`、`addons/` 主要仍是目录骨架和占位文件。
- 游戏设计和技术设计方向已经明确，但运行时基础尚未真正落地。

## 已确认的稳定背景

- 项目方向：3D 俯视角合作探险
- 引擎：Godot 4.3
- 语言：GDScript
- 架构约定：`Main -> World / CameraRig / UI / Systems`
- 预期核心 Autoload：`GameState`、`EventBus`

## 已建立的协作基础设施

- `AGENTS.md`：仓库级权威规则入口
- `CLAUDE.md`：Claude 兼容入口
- `docs/tasks.md`：统一任务面板与 Sprint 状态机
- `docs/ai_handoff.md`：AI 交接记录
- `ai/context/web_brief.md`：给 web 模型的一页简报

## 尚未落地的关键内容

- 可运行的主场景
- 已注册的 Autoload
- 最小玩法闭环
- 测试脚手架

## 当前主要风险

- 设计文档容易被误读为“已实现事实”
- 3D 项目如果沿用旧的 2D 资源导入习惯，容易把资产流程带偏
- 如果不持续维护 `project_status.md`、`tasks.md` 和 `ai_handoff.md`，多 AI 接力很快会失真

## 推荐下一步

优先从 `docs/tasks.md` 中的 `minimal_runnable_baseline` 草案 Sprint 开始，补出：

- `source/main.tscn`
- `project.godot` 的 `run/main_scene`
- 最小玩家控制或占位角色移动
- 可复用的最小 smoke test 基线

## 快速核对方式

接手项目时，先做以下检查：

1. 查看 `project.godot` 是否已经配置主场景和 Autoload
2. 查看 `source/` 下是否已有可运行 `.tscn` / `.gd`
3. 查看 `docs/tasks.md` 当前哪个 Sprint 在 `in_progress`
4. 查看 `docs/ai_handoff.md` 最近一条记录
