# 独立开发者 AI 辅助工作流

> Godot 4.3 + GDScript | 主力：ChatGPT + Claude (Claude Code) | 辅助：Kimi
> 美术：ComfyUI / SD / Midjourney | 音频：Suno / Udio

---

## 一、总览

### 模型 & 工具分工

| 角色 | 工具 | 负责什么 |
|------|------|----------|
| 创意大脑 | ChatGPT | 发散讨论、设计决策、概念定义、文案审校 |
| 工程核心 | Claude / Claude Code | 收束结构化、架构设计、核心代码、review、测试修复 |
| 低成本劳力 | Kimi | 批量配置、工具脚本、模板代码、文档清洗、批量 prompt |
| 视觉生产 | ComfyUI / SD / MJ | 概念图、角色立绘、场景图、UI 素材生成 |
| 音频生产 | Suno / Udio | 背景音乐、音效生成 |

### 一句话路由

```
想不清楚 → ChatGPT
想清楚了要落地 → Claude / Claude Code
重复/批量/便宜活 → Kimi
要图 → ComfyUI / SD / MJ
要声音 → Suno / Udio
```

### 开发阶段

```
Phase 0: 项目初始化  ──  生成 gdd.md / tdd.md 全部基础 context（一次性）
                         详见 docs/manuals/phase0_project_init.md

Phase 0 完成后，进入四条并行工作线：

Track A: 系统/代码  ──  ChatGPT → Claude Code → Kimi
Track B: UI/UX      ──  ChatGPT/Claude → Claude Code → 你在 Godot 搭
Track C: 视觉美术   ──  ChatGPT → ComfyUI/SD/MJ → Kimi 批量
Track D: 音频       ──  ChatGPT → Suno/Udio

迭代开发（新增功能/素材/并入）详见 docs/manuals/iteration_add_feature.md
```

> **重要**：所有 Track 的 prompt 都引用 gdd.md / tdd.md 的上下文。
> 如果这些文件还有"待定"，prompt 的效果会大打折扣。
> 务必先完成 Phase 0。

---

## 二、Prompt 复用系统

### 设计原则

所有 prompt 使用 **三块结构**，保证稳定性和复用性：

```
┌─────────────────────────────┐
│ 🔒 固定上下文（Context）      │  ← 从 gdd.md / tdd.md 对应章节复制
│    改了源文件，所有 prompt    │     自动跟着更新
│    自动更新                  │
├─────────────────────────────┤
│ ✏️ 可变输入（Input）          │  ← 用 {{槽位}} 标记，每次只填这部分
├─────────────────────────────┤
│ 📋 输出规范（Output Spec）    │  ← 固定的输出格式要求
└─────────────────────────────┘
```

### 上下文的唯一来源（Source of Truth）

| 上下文类型 | 来源文件 | 章节 |
|-----------|----------|------|
| 项目概览 | docs/gdd.md | 概览 |
| 核心机制 | docs/gdd.md | 核心机制 |
| 美术风格 | docs/gdd.md | 美术风格 |
| 音频方向 | docs/gdd.md | 音频 |
| 技术架构 | docs/tdd.md | 架构概览 + 核心系统 |
| 编码规范 | ai/context/coding_conventions.md | 全文 |
| 场景树结构 | ai/context/architecture.md | 全文 |

**规则：prompt 里只写"复制 gdd.md 的 XX 章节"，不要把内容抄进 prompt。**

---

## 三、Track 详细流程（见各手册）

> 以下 Track 的完整 prompt 模板和操作步骤已移至独立手册，
> dev_workflow.md 只做总览和路由，避免两处维护不同步。

### Track A — 系统/代码

```
A1 设计讨论(ChatGPT) → A2 架构收束(Claude) → A3 任务拆解(CC)
→ A4 代码实现(CC/Kimi) → A5 Code Review(CC)
```

详细操作 → [Track A 用户手册](manuals/track_a_system_code.md)

### Track B — UI/UX

```
B1 交互流程设计(ChatGPT) → B2 节点树 & 布局(CC)
→ B3 UI 脚本生成(CC)
```

详细操作 → Track B 用户手册（待编写）

### Track C — 视觉美术

```
C1 风格定义(ChatGPT) → C2 概念图生成(ComfyUI/SD/MJ)
→ C3 批量 Prompt 生成(Kimi) → C4 Godot 资产集成(CC)
```

详细操作 → Track C 用户手册（待编写）

### Track D — 音频

```
D1 音频方向定义(ChatGPT) → D2 音乐生成(Suno/Udio)
→ D3 音效生成(Suno/专用工具)
```

详细操作 → Track D 用户手册（待编写）

### 迭代开发（新增 / 素材 / Bug / 并入）

```
新功能 → 路径 A    新素材 → 路径 B    修 Bug → 路径 D    并入 → 路径 C
```

详细操作 → [迭代手册](manuals/iteration_add_feature.md)

---

## 四、Meta — 项目变更协议

当项目级信息发生实质变更时（改了核心玩法、换了美术风格、架构重构等），
使用以下协议确保所有文件保持一致。

### M1: 项目变更传播

| 项目 | 内容 |
|------|------|
| **目标** | 变更后扫描所有文件，批量更新受影响的内容 |
| **模型** | Claude Code |
| **使用时机** | gdd.md 或 tdd.md 的核心章节发生实质修改后 |
| **Input** | 变更描述 + 变更前后的 diff |
| **Output** | 受影响文件清单 + 更新 diff |
| **完成标准** | 所有文件中的旧信息已更新，无矛盾 |

**Prompt**：
```
## 变更说明
我刚刚修改了 {{docs/gdd.md 或 docs/tdd.md}}。

变更内容：
{{描述改了什么，或直接粘贴 diff}}

变更原因：
{{为什么改}}

## 任务
请扫描以下文件，找出所有引用了旧信息的位置，并提出更新方案：

必查文件：
- CLAUDE.md
- docs/gdd.md（如果改的是 tdd.md）
- docs/tdd.md（如果改的是 gdd.md）
- ai/context/architecture.md
- ai/context/coding_conventions.md
- docs/tasks.md

## 要求
1. 列出每个受影响的文件和具体位置
2. 给出更新建议（旧内容 → 新内容）
3. 标注影响级别：
   - 🔴 必须立即改（信息矛盾）
   - 🟡 建议改（描述过时）
   - 🟢 可选（措辞优化）
4. 如果变更影响到进行中的任务（tasks.md），特别标注

## 输出格式
### 影响分析
| 文件 | 位置 | 旧内容 | 新内容 | 级别 |
|------|------|--------|--------|------|

### 进行中任务影响
[如果 tasks.md 中有受影响的任务，列出]

### 建议执行顺序
1. ...
2. ...
```

### 变更协议执行流程

```
1. 修改源文件（gdd.md 或 tdd.md）
2. 运行 M1 prompt → Claude Code 输出影响分析
3. Review 影响分析，确认更新方案
4. 让 Claude Code 批量执行更新
5. git diff 检查所有改动
6. git commit
```

---

## 五、集成点 & 合流规则

四条工作线不是完全独立的，以下是合流点：

```
Track C (美术完成) ──→ C4 资产集成 ──→ Track A (代码引用资产)
Track D (音频完成) ──→ 放入 assets/audio/ ──→ Track A (代码播放音频)
Track B (UI 方案)  ──→ B3 脚本生成 ──→ Track A (系统连接 UI 信号)
```

### 合流检查清单

**美术 → 代码**：
- [ ] 资产放在正确的 assets/ 子目录
- [ ] 导入设置正确（按 gdd.md 美术风格章节的技术参数）
- [ ] 代码中使用 `res://assets/...` 引用
- [ ] 3D 模型/贴图/动画配置正确

**音频 → 代码**：
- [ ] 音乐文件为 .ogg，音效为 .wav
- [ ] 放在 assets/audio/music/ 或 assets/audio/sfx/
- [ ] AudioStreamPlayer3D 节点配置正确（3D 游戏用 3D 版本）
- [ ] 通过 EventBus 触发播放

**UI → 系统**：
- [ ] UI 信号通过 EventBus 传递给游戏系统
- [ ] 游戏状态变化通过 EventBus 通知 UI 更新
- [ ] UI 不直接引用游戏系统节点

---

## 六、日常工作节奏

```
每天开工：
  1. 看 docs/tasks.md，确认今天做什么
  2. 进入对应 Track 开始工作

每个任务完成：
  3. 运行 A5 Review
  4. F5/F6 在 Godot 里验证

每周末 / 里程碑：
  5. 更新 docs/changelog.md
  6. 检查 gdd.md / tdd.md 是否需要更新
  7. 如果更新了，运行 M1 变更协议

开新功能时：
  → 走迭代手册路径 A（docs/manuals/iteration_add_feature.md）
  → 不同 Track 可以并行推进
```

### Track 间的推荐节奏

```
Phase 1-2（设计）：Track A + Track C 的 C1 同时进行
                  先确定"做什么"和"长什么样"
Phase 3（架构）：  Track A 为主，Track B 开始 B1
Phase 4（开发）：  Track A 为主，Track B/C/D 并行推进
Phase 5（验证）：  所有 Track 合流，集成测试
Phase 6（发布）：  打版本
```

---

## 七、避坑清单

1. **AI 给方案，你来选。** 不要让 AI 替你做设计决策。
2. **一次一个功能。** 做完再开下一个，不要并行多个功能。
3. **不要跳过测试。** 每个任务完成后立刻 F5 跑一遍。
4. **文档要准确。** 文档和代码不一致比没有文档更糟。宁可少写，但要准确。
5. **核心逻辑用 Claude。** Kimi 只做批量活，核心代码不能省。
6. **每次对话聚焦一个任务。** 用 CLAUDE.md 和 ai/context/ 提供背景，不要一次塞太多。
7. **先跑通最小闭环。** 先做一个能玩的原型，再考虑优化和扩展。
8. **美术风格先定后做。** 不要没定风格就开始生图，否则后期风格不统一。
9. **改了项目信息就跑 M1。** 不要偷懒手动改一个文件，用变更协议保持一致性。
10. **Prompt 只引用不复制。** 上下文写在 gdd.md/tdd.md 里，prompt 里写"复制 XX 章节"。
