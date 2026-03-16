# godot_test_project

Godot 4.3 独立游戏项目，使用 GDScript。

## 项目结构
- source/         -- 场景+脚本（feature-oriented，.tscn 和 .gd 共置）
- source/autoload/ -- 全局单例（game_state.gd, event_bus.gd）
- source/features/ -- 按功能域组织（player/, enemies/, items/, levels/）
- source/ui/       -- UI 系统（common/, theme/, main_menu/, hud/）
- assets/         -- 原始资源（sprites/, audio/, fonts/）
- ai/context/    -- 架构和编码规范详情（Claude Code 按需读取）
- docs/           -- GDD, TDD, 任务清单, 工作流, changelog
- docs/manuals/   -- 各 Track 用户手册
- addons/         -- Godot 插件

## 编码规范
- GDScript，遵循 Godot 官方风格指南
- snake_case：文件名、变量、函数
- PascalCase：类名、节点名
- 信号命名：past_tense（如 health_changed, item_collected）
- 优先使用信号解耦，通过 autoload/event_bus.gd 做全局事件
- @export 变量用于编辑器可调参数
- 每个脚本顶部声明 class_name（如需要被其他脚本引用）

## 关键架构
- autoload/game_state.gd -- 全局游戏状态（存档、场景切换）
- autoload/event_bus.gd  -- 全局事件总线（跨系统通信）
- 入口场景：source/main.tscn

## 开发命令
- 无构建步骤，Godot 编辑器直接运行
- F5 运行主场景，F6 运行当前场景

## 详细文档（按需读取）
- docs/gdd.md                      -- 游戏设计文档（含美术风格、音频方向）
- docs/tdd.md                      -- 技术设计文档（含系统模板）
- docs/tasks.md                    -- 当前任务清单
- docs/changelog.md                -- 版本日志
- docs/dev_workflow.md             -- 开发工作流（4 工作线 + 16 个标准 prompt）
- ai/context/architecture.md       -- 架构详情（场景树、通信规则）
- ai/context/coding_conventions.md -- 编码规范详情
- docs/manuals/phase0_project_init.md  -- Phase 0 用户手册：项目初始化
- docs/manuals/track_a_system_code.md  -- Track A 用户手册：系统/代码
- docs/manuals/iteration_add_feature.md -- 迭代手册：新增功能/素材/并入
