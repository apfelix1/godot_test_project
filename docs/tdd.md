# 技术设计文档 (TDD)

## 技术栈

- 引擎：Godot 4.3
- 语言：GDScript
- 版本控制：Git
- AI 辅助：Claude Code（核心）、ChatGPT（设计）、Kimi（批量）
- 美术工具：ComfyUI / Stable Diffusion / Midjourney
- 音频工具：Suno / Udio

## 架构概览

采用 feature-oriented 目录结构，场景和脚本共置。

核心 Autoload：
- `game_state.gd` -- 全局游戏状态、存档、场景切换
- `event_bus.gd` -- 全局事件总线、跨系统信号通信

入口：`source/main.tscn`

## 核心系统

（随开发推进更新，每个系统按以下模板记录）

### [系统名称模板]
- 职责：一句话说明这个系统干什么
- 入口脚本：source/features/xxx/xxx.gd
- 关键信号：
  - signal_name(params) -- 何时触发、谁监听
- 依赖：[列出依赖的其他系统或 Autoload]
- 被依赖：[列出谁依赖这个系统]
- 关键数据：[这个系统管理哪些数据]

## 网络架构（按需）

> 本章节仅适用于多人联机游戏。单机游戏写"N/A — 单机游戏"即可跳过。

- 网络模式：（待定，如 P2P / 专用服务器 / Steam Relay）
- 同步策略：（待定，如 状态同步 / 帧同步）
- 网络 Autoload：（待定，如 NetworkManager）
- 延迟补偿：（待定）

> 多人游戏需优先确定网络方案，因为网络架构会影响大部分游戏系统的设计。

## 数据管理

- 存档方式：（待定，如 JSON / Resource）
- 配置存储：（待定）
- 资源加载策略：（待定，如预加载 / 延迟加载）

## 性能考量

- 目标帧率：60 FPS
- 已知瓶颈：（待定）
- 优化策略：（待定）

## 第三方依赖

（使用的 addons 列表及用途，暂无）
