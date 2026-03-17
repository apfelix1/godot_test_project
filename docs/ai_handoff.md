# AI Handoff

本文件用于多 AI 协作时的最小交接记录。

## 使用规则

- 每次 AI 完成一轮实际工作后，追加一条记录
- 只写事实，不重复大段背景
- 记录“做了什么、没做什么、下一棒该看什么”
- 最新记录放在最上方

## 当前交接

### 2026-03-18 — Codex

- 本次目标：建立多 AI 协作所需的统一文档结构，并把旧 workflow/manuals 对齐到这套结构
- 已完成：
  - 建立 `AGENTS.md` 作为唯一权威规则入口
  - 将 `CLAUDE.md` 改为 Claude 兼容入口
  - 新增 `docs/project_status.md`
  - 新增 `docs/ai_handoff.md`
  - 新增 `ai/context/web_brief.md`
  - 将 `docs/tasks.md` 升级为 `draft / in_progress / code_complete / merged` 状态机
  - 对齐 `README.md`、`docs/dev_workflow.md` 和主要 manuals 的入口与任务状态语义
  - 将 `docs/gdd.md` 中美术章节的示例占位从旧的 2D 像素模板同步为 3D 项目方向
- 未完成：
  - 运行时代码基础仍未补出
  - `gdd.md` / `tdd.md` 中仍有大量待补章节
- 推荐下一棒：
  - 从 `docs/tasks.md` 的 `minimal_runnable_baseline` 草案 Sprint 开始
  - 先补主场景与最小可运行闭环，再继续实现系统
- 建议下一棒执行者：Codex 或 Claude Code
- 下一棒先读：
  - `AGENTS.md`
  - `docs/project_status.md`
  - `docs/tasks.md`
  - `docs/manuals/iteration_add_feature.md`

## 追加模板

```md
### YYYY-MM-DD — [AI / 工具名]

- 本次目标：
- 已完成：
- 未完成：
- 关键修改文件：
- 风险 / 阻塞：
- 推荐下一棒：
- 建议下一棒执行者：
- 下一棒先读：
```
