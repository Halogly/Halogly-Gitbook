# ⚖️ Conditions

在条件类型前添加 `!` 可反转逻辑。例如：

```yaml
type: "!permission"
permission: "craftengine.admin"
```

# 任一 any\_of <a href="#any_of" id="any_of"></a>

满足其中一个条件。

```yaml
type: any_of
terms:
  - type: xxx
  - type: xxx
```

# 所有 all\_of <a href="#all_of" id="all_of"></a>

所有条件必须满足。

```yaml
type: all_of
terms:
  - type: xxx
  - type: xxx
```

# 反相 inverted <a href="#inverted" id="inverted"></a>

否定当前条件的结果。

```yaml
type: inverted
term:
  type: xxx
```

# 下落的方块 falling\_block <a href="#falling_block" id="falling_block"></a>

判断掉落是否由下落的方块造成。

```yaml
type: falling_block
```

# 爆炸幸存 survives\_explosion <a href="#survives_explosion" id="survives_explosion"></a>

判断是否在爆炸中幸存了下来。

```yaml
type: survives_explosion
```

# 匹配物品 match\_item <a href="#match_item" id="match_item"></a>

匹配手上的物品。

```yaml
type: match_item
id: "minecraft:iron_pickaxe"
regex: false # 是否使用正则匹配
```

```yaml
type: match_item
id: 
  - "minecraft:iron_pickaxe"
  - "minecraft:stone_pickaxe"
regex: false # 是否使用正则匹配
```

# 匹配方块属性 match\_block\_property <a href="#match_block_property" id="match_block_property"></a>

匹配方块状态属性

```yaml
type: match_block_property
properties:
  age: 3
```

# 附魔 enchantment <a href="#enchantment" id="enchantment"></a>

判断手持物品的附魔属性。

```yaml
type: enchantment
predicate: minecraft:silk_touch>=1 # > >= = < <=
```

# 附魔概率 table\_bonus <a href="#table_bonus" id="table_bonus"></a>

在不同的附魔等级提供不同的成功概率。

```yaml
type: table_bonus
enchantment: minecraft:fortune
chances:
  - 0.1
  - 0.5
  - 0.8
  - 1
```

# 随机 random <a href="#random" id="random"></a>

在不同的附魔等级提供不同的成功概率。

```yaml
type: random
value: 0.1 # 10%
```

# 权限 permission <a href="#permission" id="permission"></a>

判断玩家是否拥有权限

```yaml
type: permission
permission: "craftengine.admin"
```

# 表达式 expression <a href="#expression" id="expression"></a>

判断表达式是否返回 `true`

```yaml
type: expression
# https://ezylang.github.io/EvalEx/references/references.html
expression: "<papi:farming_level> >= 10"
```

# 字符串相等 string\_equals <a href="#string_equals" id="string_equals"></a>

判断两个值是否相等

```yaml
type: string_equals
value1: "<arg:player.name>"
value2: "Player_A"
```

# 字符串包含 string\_contains <a href="#string_contains" id="string_contains"></a>

判断 value1 是否包含 value2

```yaml
type: string_contains
value1: "<arg:player.name>"
value2: "A"
```

# 字符串匹配 string\_regex <a href="#string_regex" id="string_regex"></a>

判断值是否与模式匹配

```yaml
type: string_regex
value: "<arg:player.name>"
regex: "[a-Z]"
```

# 是否为空 is\_null <a href="#is_null" id="is_null"></a>

参数是否为空

```yaml
type: is_null
argument: "player.main_hand_item"
```

# 手 hand <a href="#hand" id="hand"></a>

交互手

```yaml
type: hand
hand: main_hand # off_hand
```

# 冷却状态 on\_cooldown <a href="#on_cooldown" id="on_cooldown"></a>

玩家是否处于冷却状态（使用 `set_cooldown` 函数设置玩家的冷却状态）

```yaml
type: on_cooldown
id: my_cooldown_id
```

示例用法

```yaml
events:
  - on: right_click
    functions:
      - type: set_cooldown
        id: test
        time: 30s
      - type: command
        command: give <arg:player.name> minecraft:apple
    conditions:
      - type: "!on_cooldown"
        id: test
```

更多条件即将推出...
