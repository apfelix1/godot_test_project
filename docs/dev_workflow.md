# 多 AI 协作工作流

> 本文件是多 AI 协作的总览，不替代 `AGENTS.md`。
> 仓库级规则以 `AGENTS.md` 为准，详细步骤见 `docs/manuals/*`。

## 一、协作目标

本项目不是单一 AI 的工作流，而是一个可被多个 AI 轮流接手的仓库。

目标不是“让每个 AI 都读完所有文档”，而是：

1. 让任何 AI 都知道项目背景
2. 让任何 AI 都知道当前真实状态
3. 让任何 AI 都知道当前轮到它接什么工作
4. 让不同 AI 之间可以低损耗交接

## 二、核心文件分工

| 文件 | 作用 |
|------|------|
| `AGENTS.md` | 唯一权威规则入口 |
| `CLAUDE.md` | Claude / Claude Code 兼容入口 |
| `docs/project_status.md` | 当前真实状态 |
| `docs/tasks.md` | 当前任务面板 |
| `docs/ai_handoff.md` | 交接记录 |
| `ai/context/web_brief.md` | 给 web 模型的一页简报 |
| `docs/gdd.md` | 设计意图 |
| `docs/tdd.md` | 技术设计意图 |
| `ai/context/architecture.md` | 场景树、目录、通信约定 |
| `ai/context/coding_conventions.md` | 编码规范 |

## 三、接手顺序

### 能直接读仓库的 agent

1. `AGENTS.md`
2. `docs/project_status.md`
3. `docs/tasks.md`
4. `docs/ai_handoff.md`
5. 再按需读取设计与实现文档

### 不能直接读仓库的 web 模型

1. `ai/context/web_brief.md`
2. 当前 Sprint 卡片
3. 当前任务必需的 GDD/TDD 摘录

## 四、AI 角色矩阵

| 角色 | 典型工具 | 适合做什么 |
|------|----------|------------|
| 方案与设计 | ChatGPT / Claude web | 方案比较、机制讨论、流程设计、文案 |
| 仓库实现 | Codex / Claude Code | 读仓库、实现、修复、测试、review、文档同步 |
| 批量生产 | Kimi 等 | 数据表、模板、清洗、批量文本 |
| 人类开发者 | Godot 编辑器 + Git | 最终决策、场景搭建、参数和手感调优 |

## 五、统一执行闭环

每位 AI 默认遵循以下闭环：

1. Intake：读规则、状态、任务、交接
2. Scope：确认本轮只做什么，不做什么
3. Execute：按任务卡要求工作
4. Verify：执行验证，不能虚报
5. Sync：更新状态、交接和必要文档
6. Handoff：把下一棒需要的最小上下文留下

## 六、任务状态机

`docs/tasks.md` 统一使用：

- `draft`
- `in_progress`
- `code_complete`
- `merged`

建议语义：

- 设计和规格清晰但未开始：`draft`
- 正在做：`in_progress`
- 代码和本地验证完成、等并入：`code_complete`
- 已并入主线并完成记录：`merged`

## 七、文档更新规则

- 稳定规则变化：更新 `AGENTS.md`
- Claude 兼容说明变化：同步 `CLAUDE.md`
- 当前真实状态变化：更新 `docs/project_status.md`
- 当前任务状态变化：更新 `docs/tasks.md`
- 本轮工作结束：追加 `docs/ai_handoff.md`
- 设计目标变化：更新 `docs/gdd.md`
- 技术设计变化：更新 `docs/tdd.md` 与相关 `ai/context/*`

## 八、工作流入口

- 新项目初始化：`docs/manuals/phase0_project_init.md`
- 系统 / 代码实现：`docs/manuals/track_a_system_code.md`
- 迭代开发 / 素材 / 并入：`docs/manuals/iteration_add_feature.md`

## 九、关键原则

1. 不要把设计文档当成已实现事实。
2. 不要在未验证前声称项目可运行。
3. 多 AI 协作时，状态文件比长 prompt 更重要。
4. 任何重大改动都应留下可供下一棒直接使用的交接记录。
