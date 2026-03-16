# GDScript 编码规范

基于 Godot 官方风格指南，补充项目约定。

## 命名规则

| 类型 | 风格 | 示例 |
|------|------|------|
| 文件名 | snake_case | player_controller.gd |
| 变量/函数 | snake_case | move_speed, get_health() |
| 常量 | UPPER_SNAKE | MAX_HEALTH, TILE_SIZE |
| 类名 | PascalCase | PlayerController |
| 节点名 | PascalCase | PlayerSprite, HealthBar |
| 信号 | past_tense snake_case | health_changed, item_collected |
| 枚举 | PascalCase.UPPER_SNAKE | State.IDLE, Direction.LEFT |

## 脚本结构顺序

```gdscript
class_name MyClass
extends Node3D  # 本项目为 3D 游戏，根据节点类型选择 Node3D / CharacterBody3D 等

# 信号
signal health_changed(new_value: int)

# 枚举
enum State { IDLE, RUNNING, JUMPING }

# 常量
const MAX_SPEED := 200.0

# @export 变量
@export var speed: float = 100.0

# @onready 变量
@onready var mesh: MeshInstance3D = $MeshInstance3D

# 普通变量
var current_state: State = State.IDLE

# 生命周期函数
func _ready() -> void:
    pass

func _process(delta: float) -> void:
    pass

func _physics_process(delta: float) -> void:
    pass

# 公共方法
func take_damage(amount: int) -> void:
    pass

# 私有方法
func _update_animation() -> void:
    pass

# 信号回调
func _on_area_entered(area: Area3D) -> void:
    pass
```

## 信号使用原则

- 子节点向父节点通信：用信号
- 父节点向子节点通信：直接调用方法
- 跨系统通信：通过 EventBus
- 信号命名用过去时态，表示"事件已发生"

### EventBus 事件分类规则

当 event_bus.gd 中信号超过 8 个时，按域分组管理：

```gdscript
# event_bus.gd
extends Node

# ── player ──
signal player_damaged(amount: int, source: String)
signal player_died(player_id: int)

# ── loot ──
signal loot_picked_up(loot_id: String, carrier_id: int)
signal loot_dropped(loot_id: String, position: Vector3)

# ── level ──
signal level_completed(score: int)

# ── ui ──
signal ui_notification_requested(text: String, duration: float)
```

命名规则：`域_动作_past_tense`（如 `player_damaged`、`loot_picked_up`）。

> 如果事件超过 30 个，可考虑拆成多个 Autoload（PlayerEvents、LevelEvents），
> 但对独立开发者来说大概率不需要。

## 类型标注

- 函数参数和返回值必须标注类型
- @export 变量必须标注类型
- 局部变量可省略（类型推断）

## 注释

- 只在逻辑不自明时添加注释
- 不注释显而易见的代码
- 复杂算法或 workaround 需要注释说明原因
