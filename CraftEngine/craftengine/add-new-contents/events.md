# 🪇 事件

介绍

`events`部分决定在特定事件期间哪个物品/家具/方块将执行预定义行为。在`events`部分中，你需要指定一个事件触发器，例如`"right_click"`是右键点击操作。在事件触发器下方，必须传递一个包含相应类型的操作列表。例如，`command`执行指定的命令。

```yaml
# 格式1
events:
  right_click:
    - type: command
      command: say 1
      conditions:
        - type: permission
          permission: "craftengine.admin"
    - type: command
      command: say 2
      conditions: []
# 格式2
events:
  - on: right_click
    functions:
      - type: command
        command: say 1
        conditions:
          - type: permission
            permission: "craftengine.admin"
      - type: command
        command: say 2
        conditions: []
```

<details>

<summary><a href="items/item-models/condition.md#tiao-jian">⚖️ 条件</a></summary>



</details>

## 🧨 事件触发器 <a href="#event-triggers" id="event-triggers"></a>

### 物品 <a href="#items" id="items"></a>

* break
* right\_click
* left\_click
* consume

### 方块 <a href="#blocks" id="blocks"></a>

* break
* place
* right\_click
* left\_click
* step

### 家具 <a href="#furniture" id="furniture"></a>

* break
* place
* right\_click

{% hint style="danger" %}
请注意，相应的事件应该放置在适当的配置区域。例如，如果你希望在交互某件家具时执行命令，正确的方法是将`events`放在`furniture`区域下，而不是放在你的物品区域下。

<pre class="language-yaml"><code class="lang-yaml"><strong>items:
</strong>  default:bench:
    events: # ❌️
      right_click:
       - type: command
    behavior:
      type: furniture_item
      furniture:
        events: # ✅️
          right_click:
           - type: command
</code></pre>
{% endhint %}

## 🔧 函数 <a href="#functions" id="functions"></a>

### cancel\_event <a href="#cancel_event" id="cancel_event"></a>

取消原先的事件。

```yaml
type: cancel_event
```

### run <a href="#run" id="run"></a>

按顺序运行一系列函数。这对于具有相同条件的函数来说非常有用。

```yaml
type: run
delay: 0 # 可选; 数字; [默认: 0]
functions: # 必需; 映射列表
  - type: command
  - type: message
```

### command <a href="#command" id="command"></a>

以玩家或控制台的身份执行命令。

```yaml
type: command
command: "say 你好<arg:player.name>" # 必需; 字符串列表/字符串
target: "self" # 可选; 枚举[all,self]/玩家选择器; [默认: self]
as-player: false # 可选; [默认: false]
```

### message <a href="#message" id="message"></a>

发送消息或系统动作栏消息。

```yaml
type: message
message: "你好<papi:player_name>" # 必需; 字符串列表/字符串
target: "self" # 可选; 枚举[all,self]/玩家选择器
overlay: false # 可选; [默认: false]; false = 聊天栏 / true = 动作栏
```

### actionbar <a href="#actionbar" id="actionbar"></a>

发送动作栏消息。

```yaml
type: actionbar
actionbar: "这是一条动作栏文本"  # 必需; 字符串
target: "self" # 可选; 枚举[all,self]/玩家选择器; [默认: self]
```

### title

发送标题。

```yaml
type: title
title: "<red>标题</red>"  # 必需; 字符串
subtitle: "<Yellow>副标题</yellow>" # 必需; 字符串
fade-in: 20 # 可选; 数字; [默认: 10]
stay: 10 # 可选; 数字; [默认: 20]
fade-out: 10 # 可选; 数字; [默认: 5]
```

### open\_window <a href="#open_window" id="open_window"></a>

打开GUI界面。

```yaml
type: open_window #
gui-type: anvil # 必需; 枚举[anvil, enchantment, grindstone, loom, smithing, crafting, cartography];
title: "超级无敌大铁砧"  # 可选; 字符串
target: "self" # 可选; 枚举[all,self]/玩家选择器; [默认: self]
```

### place\_block <a href="#place_block" id="place_block"></a>

放置一个方块。

```yaml
type: place_block
block-state: "default:chinese_lantern"
x: <arg:block.block_x>
y: <arg:block.block_y>
z: <arg:block.block_z>
```

### drop\_loot <a href="#drop_loot" id="drop_loot"></a>

根据指定的战利品表掉落物品。

```yaml
type: drop_loot
x: <arg:block.block_x> + 0.5
y: <arg:block.block_y> + 0.5
z: <arg:block.block_z> + 0.5
loot:
  pools: ...
```

### update\_interaction\_tick <a href="#update_interaction_tick" id="update_interaction_tick"></a>

在最后一次交互结束时更新刻。

```yaml
type: update_interaction_tick
```

### set\_count <a href="#set_count" id="set_count"></a>

设置此事件中当前物品的数量。

```yaml
type: set_count
add: true # 默认: false
count: -1
target: "self" # 可选; 枚举[all,self]/玩家选择器
```

### set\_food <a href="#set_food" id="set_food"></a>

设置玩家的饥饿值（0\~20）。

```yaml
type: set_food
add: true
food: 4
target: "self" # 可选; 枚举[all,self]/玩家选择器
```

### set\_saturation <a href="#set_saturation" id="set_saturation"></a>

设置玩家的饱和度（0\~10）。

```yaml
type: set_saturation
add: true
saturation: 2.5
target: "self" # 可选; 枚举[all,self]/玩家选择器
```

### swing\_hand <a href="#swing_hand" id="swing_hand"></a>

挥动与此事件相关的手或配置中指定的手臂。

```yaml
type: swing_hand
hand: main_hand # 可选参数
```

### particle <a href="#particle" id="particle"></a>

生成粒子。

```yaml
type: particle
particle: minecraft:end_rod
x: "<arg:position.x>"
y: "<arg:position.y>"
z: "<arg:position.z>"
count: 5
offset-x: 0.3
offset-y: 0.3
offset-z: 0.3
speed: 0

# 以下参数仅在粒子属于某种类型时有效。
# 参数详情：
# https://zh.minecraft.wiki/w/Java版粒子/#类型

# item
item: default:chinese_lantern

# block/falling_dust/dust_pillar/block_crumble/block_marker
block-state: default:plam_log[axis=y]

# charge
charge: 1.5

# shriek
shriek: 1

# dust
color: 255,255,255
scale: 1.0

# dust_color_transition
from: 255,255,255
to: 0,0,0
scale: 4.0

# vibration
target-x: 0
target-y: 1
target-z: 0
arrival-time: 10

# trail
target-x: 0
target-y: 1
target-z: 0
duration: 10
```

### potion\_effect <a href="#potion_effect" id="potion_effect"></a>

添加药水效果。

```yaml
type: potion_effect
potion-effect: minecraft:blindness
duration: 20  # 默认: 20
amplifier: 0   # 默认: 0
ambient: false # 来自信标
particles: true
```

### remove\_potion\_effect <a href="#remove_potion_effect" id="remove_potion_effect"></a>

移除药水效果。

```yaml
type: remove_potion_effect
potion-effect: minecraft:blindness # 'all' 为true时可选
all: false  # 默认: false
```

### leveler\_exp <a href="#leveler_exp" id="leveler_exp"></a>

增加技能或工作经验值。

<details>

<summary><a href="https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/supported-levelers">👔 Supported Levelers</a></summary>



</details>

```yaml
type: leveler_exp
plugin: AuraSkills  # leveler 插件
leveler: fishing  # 工作/技能的 ID
count: 10  # 要给予的经验值
```

### set\_cooldown <a href="#set_cooldown" id="set_cooldown"></a>

设置玩家的冷却时间。

```yaml
type: set_cooldown
time: 1m30s
id: my_cooldown_id
add: false  # 默认: false（是否累积冷却时间）
```

### remove\_cooldown <a href="#remove_cooldown" id="remove_cooldown"></a>

移除玩家的冷却时间。

```yaml
type: remove_cooldown
id: my_cooldown_id  # 'all' 为 true 时可选
all: false  # 默认: false
```

### play\_sound <a href="#play_sound" id="play_sound"></a>

播放声音。

```yaml
type: play_sound
sound: minecraft:xxxx.xxx
x: <arg:position.x>
y: <arg:position.y>
z: <arg:position.z>
pitch: 1
volume: 1
source: master
```

{% hint style="warning" %}
更多功能即将推出...
{% endhint %}
