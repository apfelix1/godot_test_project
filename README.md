# godot_test_project

Godot 4.3 独立游戏项目。

## 开发环境
- Godot 4.3
- GDScript
- AI 辅助：Claude Code（参见 ai/ 目录）

## 快速开始
1. 用 Godot 4.3 打开 `project.godot`
2. F5 运行主场景

## 项目结构
```
source/     -- 场景+脚本（feature-oriented）
assets/     -- 原始资源（sprites, audio, fonts）
ai/         -- AI prompt 模板和上下文文档
docs/       -- 项目文档（GDD, TDD）
addons/     -- Godot 插件
```

## 文档
- [游戏设计文档](docs/gdd.md)
- [技术设计文档](docs/tdd.md)
- [AI Prompt 系统](ai/)
