# 项目架构概览

> 本项目为 3D 俯视角合作探险游戏，使用 Godot 4.3 的 3D 节点体系。

## 场景树结构

```
Main (Node3D)
├── World (Node3D)         -- 游戏世界容器
│   ├── Level (Node3D)     -- 当前关卡（地形、机关、装饰）
│   ├── Entities (Node3D)  -- 动态实体（玩家、敌人、物品）
│   └── Navigation (NavigationRegion3D) -- 寻路区域（如需要）
├── CameraRig (Node3D)     -- 俯视角相机
│   └── Camera3D
├── UI (CanvasLayer)       -- UI 层（2D 覆盖在 3D 之上）
│   ├── HUD                -- 游戏内 HUD
│   └── Menus              -- 菜单系统
└── Systems (Node)         -- 纯逻辑系统节点（不需要 3D 变换）
```

> Phase 0 完成后，此场景树会根据 tdd.md 的系统设计进一步细化。

## Autoload 单例

| 名称 | 文件 | 职责 |
|------|------|------|
| GameState | source/autoload/game_state.gd | 全局状态、存档、场景切换 |
| EventBus | source/autoload/event_bus.gd | 全局事件总线、跨系统信号 |

> 合作多人相关的 Autoload（如 NetworkManager）待 Phase 0 Step 8 确定网络方案后补充。

## 系统间通信

- 同一场景内：直接信号连接（node.signal.connect）
- 跨系统通信：通过 EventBus 全局信号
- 父子节点：直接方法调用（向下）/ 信号（向上）
- 网络同步：待定（Phase 0 Step 8 确定）

## 目录与职责

| 目录 | 职责 |
|------|------|
| source/autoload/ | 全局单例，引擎启动时自动加载 |
| source/features/ | 游戏功能模块，每个子目录包含 .tscn + .gd |
| source/ui/ | UI 场景和脚本 |
| source/utils/ | 通用工具函数 |
| source/shaders/ | 着色器文件 |
| assets/ | 非代码资源（模型、贴图、音频、字体） |

## 资源引用约定

- 场景内引用：`res://source/features/player/player.tscn`
- 3D 模型引用：`res://assets/models/player.glb`
- 贴图引用：`res://assets/textures/player_albedo.png`
- 音频引用：`res://assets/audio/music/main_theme.ogg`
- Autoload 引用：直接用单例名（如 `EventBus.emit_signal(...)`）
