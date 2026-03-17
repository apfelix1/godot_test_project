# CLAUDE.md

本文件是 Claude / Claude Code 的兼容入口。

项目通用规则以 `AGENTS.md` 为准；如果本文件与 `AGENTS.md` 冲突，以 `AGENTS.md` 为准。

## Claude 接手顺序

1. 先读 `AGENTS.md`
2. 再读 `docs/project_status.md`
3. 再读 `docs/tasks.md`
4. 再读 `docs/ai_handoff.md`
5. 最后按需读 `docs/gdd.md`、`docs/tdd.md`、`ai/context/architecture.md`、`ai/context/coding_conventions.md`

## Claude 适合接手的工作

- 架构收束
- 核心代码实现
- 代码 review
- 文档一致性检查
- 文档同步和交接整理

## Claude 工作注意事项

- 不要在未验证前声称项目可运行。
- 不要把 GDD/TDD 中的设想当作已提交代码事实。
- 结束工作前应更新 `docs/ai_handoff.md`，并在状态变化时更新 `docs/tasks.md`。

## 相关文件

- 仓库总规则：`AGENTS.md`
- 当前状态：`docs/project_status.md`
- 当前任务：`docs/tasks.md`
- 交接记录：`docs/ai_handoff.md`
- web 模型简报：`ai/context/web_brief.md`
