# 项目架构概览

## 场景树结构

```
Main (Node2D)
├── World          -- 游戏世界容器
│   ├── Level      -- 当前关卡
│   └── Entities   -- 动态实体（玩家、敌人、物品）
├── UI             -- UI 层
│   ├── HUD        -- 游戏内 HUD
│   └── Menus      -- 菜单系统
└── Systems        -- 游戏系统节点
```

## Autoload 单例

| 名称 | 文件 | 职责 |
|------|------|------|
| GameState | source/autoload/game_state.gd | 全局状态、存档、场景切换 |
| EventBus | source/autoload/event_bus.gd | 全局事件总线、跨系统信号 |

## 系统间通信

- 同一场景内：直接信号连接（node.signal.connect）
- 跨系统通信：通过 EventBus 全局信号
- 父子节点：直接方法调用（向下）/ 信号（向上）

## 目录与职责

| 目录 | 职责 |
|------|------|
| source/autoload/ | 全局单例，引擎启动时自动加载 |
| source/features/ | 游戏功能模块，每个子目录包含 .tscn + .gd |
| source/ui/ | UI 场景和脚本 |
| source/utils/ | 通用工具函数 |
| source/shaders/ | 着色器文件 |
| assets/ | 非代码资源（图片、音频、字体） |

## 资源引用约定

- 场景内引用：`res://source/features/player/player.tscn`
- 资源引用：`res://assets/sprites/player.png`
- Autoload 引用：直接用单例名（如 `EventBus.emit_signal(...)`）
