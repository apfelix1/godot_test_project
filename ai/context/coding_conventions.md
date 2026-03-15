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
extends Node2D

# 信号
signal health_changed(new_value: int)

# 枚举
enum State { IDLE, RUNNING, JUMPING }

# 常量
const MAX_SPEED := 200.0

# @export 变量
@export var speed: float = 100.0

# @onready 变量
@onready var sprite: Sprite2D = $Sprite2D

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
func _on_area_entered(area: Area2D) -> void:
    pass
```

## 信号使用原则

- 子节点向父节点通信：用信号
- 父节点向子节点通信：直接调用方法
- 跨系统通信：通过 EventBus
- 信号命名用过去时态，表示"事件已发生"

## 类型标注

- 函数参数和返回值必须标注类型
- @export 变量必须标注类型
- 局部变量可省略（类型推断）

## 注释

- 只在逻辑不自明时添加注释
- 不注释显而易见的代码
- 复杂算法或 workaround 需要注释说明原因
