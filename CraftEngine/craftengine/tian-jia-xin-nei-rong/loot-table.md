---
description: 本页面主要讲解如何配置战利品
---

# 💎 Loot Table

# 介绍 <a href="#introduction" id="introduction"></a>

在 `loots` 下，必须有一个 `pools` 列表，它是战利品表的随机池的列表。每个战利品随机池由四部分组成：

`rolls` 指定随机池的抽取次数
`conditions` 指定战利品的条件
`entries` 定义随机池中的抽取项，即实际的战利品
`functions` 是后端处理函数，例如修改战利品的数量、NBT 数据等

如果你很熟悉原版数据包，你应该会对这个结构非常了解。本插件采用相同格式并加以改良，以确保向 CraftEngine 战利品系统的过渡又快又丝滑。

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

# ☘️ Entry 抽取项 <a href="#entry" id="entry"></a>

`entry` 指定掉落的实际物品，但在某些情况下，但在一些情况下也可表示从多个可能的掉落物中选择一个。

所有 `entry` 部分都可以使用 `functions` 和 `conditions`。

```yaml
type: item
item: "minecraft:apple"
functions: []
conditions: []
```

## item 物品 <a href="#item" id="item"></a>

设置掉落物的类型，可以是自定义物品。

```yaml
type: item
item: "minecraft:apple"
```

## furniture\_item 家具物品 <a href="#furniture_item" id="furniture_item"></a>

当放置为家具时使用原始家具物品，否则回退为备用物品（fallback_item）。

```yaml
type: furniture_item
item: "default:fallback_item"
```

## exp 经验值 <a href="#exp" id="exp"></a>

掉落一定数量的经验值。

```yaml
type: exp
count: 1
```

## alternatives 替代方案 <a href="#alternatives" id="alternatives"></a>

从给定列表中找到第一个符合 `conditions` 的 `entry`。

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

# 🔧 Function 函数 <a href="#function" id="function"></a>

`function` 的作用是在设置物品类型后对其进行额外操作，例如调整数量。它还可以处理并发操作，如掉落经验值或其他额外奖励。

所有 `function` 部分都支持使用 `conditions`。

```yaml
type: set_count
count: 10
conditions: []
```

## apply\_bonus 奖励 <a href="#apply_bonus" id="apply_bonus"></a>

根据提供的附魔属性和合成配方增加掉落物的数量。更多信息请参阅[➕️ Formula 计算公式](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/loot-table#formula)。

```yaml
type: apply_bonus
enchantment: minecraft:fortune
formula:
  type: ore_drops
```

## set\_count 设置数量 <a href="#set_count" id="set_count"></a>

设置物品的数量。

```yaml
type: set_count
count: 10
add: true  # `true` 为添加，`false` 为设置
```

## explosion\_decay 爆炸衰减 <a href="#explosion_decay" id="explosion_decay"></a>

确定物品在爆炸时数量是否减少。在原版 Minecraft 中，爆炸通常会导致掉落的方块数量少于原本数量的情况，这是由该功能的导致的。

```yaml
type: explosion_decay
```

## drop\_exp 经验掉落 <a href="#drop_exp" id="drop_exp"></a>

掉落一定数量的经验值。

```yaml
type: drop_exp
count: 1
```

# ⚖️ Condition 条件 <a href="#condition" id="condition"></a>

`condition` can provide prerequisites for both `entry` and `function`.

[⚖️ Conditions](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/conditions)

# ➕️ Formula 计算公式 <a href="#formula" id="formula"></a>

## ore\_drops 矿物掉落随机算法 <a href="#ore_drops" id="ore_drops"></a>

与原版 Minecraft 使用相同的掉落算法。

```yaml
type: ore_drops
```

## binomial\_with\_bonus\_count 二项分布随机数 <a href="#binomial_with_bonus_count" id="binomial_with_bonus_count"></a>

与原版 Minecraft 相同的二项式掉落算法。`extra` 表示尝试掉落物品的额外次数，`probability` 代表每次成功的概率。附魔等级会增加尝试次数。

```yaml
type: binomial_with_bonus_count
extra: 3
probability: 0.5
```
