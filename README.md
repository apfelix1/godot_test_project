# godot_test_project

Godot 4.3 独立游戏项目，方向为 3D 俯视角合作探险游戏，使用 GDScript。

## 当前状态

- 当前仓库以文档和目录骨架为主，设计文档明显领先于运行时代码。
- 在假设项目“可直接 F5 运行”之前，请先检查 `project.godot`、`docs/project_status.md` 和实际场景文件。

## 开发环境

- Godot 4.3
- GDScript

## AI 协作入口

- 仓库级规则：`AGENTS.md`
- Claude 兼容入口：`CLAUDE.md`
- 当前真实状态：`docs/project_status.md`
- 当前任务面板：`docs/tasks.md`
- 最近交接记录：`docs/ai_handoff.md`
- web 模型简报：`ai/context/web_brief.md`

## 项目结构

```text
source/     -- 场景和脚本（feature-oriented）
assets/     -- 运行时资源（models, textures, materials, audio, fonts, data）
ai/         -- AI 协作上下文与简报
docs/       -- GDD, TDD, 工作流、任务、状态、交接
addons/     -- Godot 插件
```

## 重要文档

- `docs/gdd.md`：游戏设计目标
- `docs/tdd.md`：技术设计目标
- `docs/dev_workflow.md`：多 AI 协作工作流总览
- `docs/manuals/phase0_project_init.md`：Phase 0 手册
- `docs/manuals/track_a_system_code.md`：系统 / 代码手册
- `docs/manuals/iteration_add_feature.md`：迭代手册
