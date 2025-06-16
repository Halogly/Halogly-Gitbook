---
description: 本页面主要讲解如何配置掉落物
---

# 💎 Loot Table

# 介绍 <a href="#introduction" id="introduction"></a>

Under `loots`, there must be a `pools` list, which represents the loot pools. Each loot pool consists of four parts:

`rolls` determines how many times the pool is rolled `conditions` represent the conditions for the loot `entries` denote the actual loot items `functions` are the post-processing functions, such as modifying the quantity of the loot, NBT data, and so on

If you are well-acquainted with vanilla data packs, you will find this structure very familiar. The plugin employs this format and modifies it to facilitate a swift and smooth transition into the CraftEngine loot system.

```yaml
loot:
  functions: []
  pools:
    - rolls: 1
      conditions:
        - type: survives_explosion
      entries:
        - type: item
          item: "minecraft:apple"
      functions: []
```

# ☘️ Entry <a href="#entry" id="entry"></a>

The 'entry' specifies the actual contents of the drop, but in certain scenarios, it can also represent a choice among possible drops.

All `entry` sections are capable of using `functions` and `conditions`.

```yaml
type: item
item: "minecraft:apple"
functions: []
conditions: []
```

#### item <a href="#item" id="item"></a>

Set the type of the dropped item, which can be a custom item.

```yaml
type: item
item: "minecraft:apple"
```

#### 家具物品 furniture\_item <a href="#furniture_item" id="furniture_item"></a>

Sets the item to the original furniture item when placed, otherwise uses the fallback item.

```yaml
type: furniture_item
item: "default:fallback_item"
```

#### 经验值 exp <a href="#exp" id="exp"></a>

Drop a certain amount of experience.

```yaml
type: exp
count: 1
```

#### 替代方案 alternatives <a href="#alternatives" id="alternatives"></a>

Find the first `entry` from the given list that meets the `conditions`.

```yaml
type: alternatives
children:
  - type: item
    item: "{ore_block}"
    conditions:
      - type: enchantment
        predicate: minecraft:silk_touch>=1
  - type: item
    item: "{ore_drop}"
    functions:
      - type: apply_bonus
        enchantment: minecraft:fortune
        formula:
          type: ore_drops
      - type: explosion_decay
      - type: drop_exp
        count:
          type: uniform
          min: "{min_exp}"
          max: "{max_exp}"
```

### 🔧 函数 <a href="#function" id="function"></a>

The role of the `function` is to perform additional operations on the item after its type has been set, such as adjusting the quantity. It can also handle concurrent operations like dropping experience or other extras.

All `function` sections support the use of `conditions`.

```yaml
type: set_count
count: 10
conditions: []
```

#### apply\_bonus <a href="#apply_bonus" id="apply_bonus"></a>

Increase the quantity of the dropped items based on the given enchantments and formulas. Refer to [➕️ Formula](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/loot-table#formula) for more info.

```yaml
type: apply_bonus
enchantment: minecraft:fortune
formula:
  type: ore_drops
```

#### set\_count <a href="#set_count" id="set_count"></a>

Set the count of the item.

```yaml
type: set_count
count: 10
add: true  # add or set
```

#### explosion\_decay <a href="#explosion_decay" id="explosion_decay"></a>

Determines whether the quantity of this item diminishes upon explosion. In vanilla Minecraft, explosions often result in fewer blocks being dropped than originally present, which is due to the implementation of this function.

```yaml
type: explosion_decay
```

#### 经验掉落 drop\_exp <a href="#drop_exp" id="drop_exp"></a>

掉落一定数量的经验。

```yaml
type: drop_exp
count: 1
```

### ⚖️ 条件 <a href="#condition" id="condition"></a>

`condition` can provide prerequisites for both `entry` and `function`.

[⚖️ Conditions](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/conditions)

### ➕️ 配方 <a href="#formula" id="formula"></a>

#### 原版掉落 ore\_drops <a href="#ore_drops" id="ore_drops"></a>

在原版 Minecraft 中使用的相同掉落算法。

```yaml
type: ore_drops
```

#### binomial\_with\_bonus\_count <a href="#binomial_with_bonus_count" id="binomial_with_bonus_count"></a>

The same binomial drop algorithm used in vanilla Minecraft. `extra` means a few extra attempts to drop the item, and `probability` represents the probability of success each time. The enchantment level will increase the number of attempts.

```yaml
type: binomial_with_bonus_count
extra: 3
probability: 0.5
```
