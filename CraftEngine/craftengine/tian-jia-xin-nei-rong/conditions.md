# ⚖️ Conditions

Adding `!` before a condition type inverts its logic. For instance:

Copy

```
type: "!permission"
permission: "craftengine.admin"
```

#### any\_of <a href="#any_of" id="any_of"></a>

Satisfy any one of the conditions.

Copy

```
type: any_of
terms:
  - type: xxx
  - type: xxx
```

#### all\_of <a href="#all_of" id="all_of"></a>

All conditions must be satisfied.

Copy

```
type: all_of
terms:
  - type: xxx
  - type: xxx
```

#### inverted <a href="#inverted" id="inverted"></a>

Negate the result value of the current condition.

Copy

```
type: inverted
term:
  type: xxx
```

#### falling\_block <a href="#falling_block" id="falling_block"></a>

Check whether the drop was caused by the block falling.

Copy

```
type: falling_block
```

#### survives\_explosion <a href="#survives_explosion" id="survives_explosion"></a>

Detect whether it is possible to survive the explosion.

Copy

```
type: survives_explosion
```

#### match\_item <a href="#match_item" id="match_item"></a>

Match the item in hand.

Copy

```
type: match_item
id: "minecraft:iron_pickaxe"
regex: false # whether to use regex matching
```

Copy

```
type: match_item
id: 
  - "minecraft:iron_pickaxe"
  - "minecraft:stone_pickaxe"
regex: false # whether to use regex matching
```

#### match\_block\_property <a href="#match_block_property" id="match_block_property"></a>

Match the block state property

Copy

```
type: match_block_property
properties:
  age: 3
```

#### enchantment <a href="#enchantment" id="enchantment"></a>

Detect the enchantments on the item in hand.

Copy

```
type: enchantment
predicate: minecraft:silk_touch>=1 # > >= = < <=
```

#### table\_bonus <a href="#table_bonus" id="table_bonus"></a>

Provide different success probabilities at various enchantment levels.

Copy

```
type: table_bonus
enchantment: minecraft:fortune
chances:
  - 0.1
  - 0.5
  - 0.8
  - 1
```

#### random <a href="#random" id="random"></a>

Provide different success probabilities at various enchantment levels.

Copy

```
type: random
value: 0.1 # 10%
```

#### permission <a href="#permission" id="permission"></a>

Checks if the player has the permission

Copy

```
type: permission
permission: "craftengine.admin"
```

#### expression <a href="#expression" id="expression"></a>

Checks if the expression returns `true`

Copy

```
type: expression
# https://ezylang.github.io/EvalEx/references/references.html
expression: "<papi:farming_level> >= 10"
```

#### string\_equals <a href="#string_equals" id="string_equals"></a>

Determines if the two values are equal

Copy

```
type: string_equals
value1: "<arg:player.name>"
value2: "Player_A"
```

#### string\_contains <a href="#string_contains" id="string_contains"></a>

Determines if value1 contains value2

Copy

```
type: string_contains
value1: "<arg:player.name>"
value2: "A"
```

#### string\_regex <a href="#string_regex" id="string_regex"></a>

Determines if value matches the pattern

Copy

```
type: string_regex
value: "<arg:player.name>"
regex: "[a-Z]"
```

#### is\_null <a href="#is_null" id="is_null"></a>

Checks if the argument is null

Copy

```
type: is_null
argument: "player.main_hand_item"
```

#### hand <a href="#hand" id="hand"></a>

Checks the interaction hand

Copy

```
type: hand
hand: main_hand # off_hand
```

#### on\_cooldown <a href="#on_cooldown" id="on_cooldown"></a>

Checks if player is on cooldown (use `set_cooldown` function to set cooldown for player)

Copy

```
type: on_cooldown
id: my_cooldown_id
```

Example usage

Copy

```
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

More conditions are coming...
