---
description: 本页面主要讲解如何配置战利品。
---

# 💎 战利品表

介绍

在`loot`下，必须有一个`pools`列表，它是战利品表的随机池列表。每个战利品随机池由四个部分组成：

`rolls`指定随机池的抽取次数`conditions`指定战利品的条件`entries`定义随机池中的抽取项，即实际的战利品`functions`是后端处理函数，例如修改战利品的数量、NBT数据等

{% hint style="info" %}
如果你很熟悉原版数据包，你应该会对这个结构非常了解。本插件采用了相同的格式并加以改良，确保向CraftEngine战利品系统的过渡会很顺滑。
{% endhint %}

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

## ☘️ 抽取项 <a href="#entry" id="entry"></a>

抽取项指定掉落的实际物品，但在某些情况下，也可表示从多个可能的掉落物中选取一个。

{% hint style="success" %}
所有`entry`部分都可以使用`functions`和`conditions`。

```yaml
type: item
item: "minecraft:apple"
functions: []
conditions: []
```
{% endhint %}

### item <a href="#item" id="item"></a>

设置掉落物的类型，可以是自定义物品。

```yaml
type: item
item: "minecraft:apple"
```

### furniture\_item <a href="#furniture_item" id="furniture_item"></a>

当放置为家具时使用原始家具物品，否则使用回退物品。

```yaml
type: furniture_item
item: "default:fallback_item"
```

### exp <a href="#exp" id="exp"></a>

掉落一定数量的经验值。

```yaml
type: exp
count: 1
```

### alternatives <a href="#alternatives" id="alternatives"></a>

从给定列表中找到第一个符合条件的抽取项。

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

## 🔧 函数 <a href="#function" id="function"></a>

函数的作用是在设置物品类型后对其进行额外操作，例如调整数量。它还可以处理并发操作，如掉落经验值或其他额外奖励。

{% hint style="success" %}
所有`function`部分都支持使用`conditions`。

```yaml
type: set_count
count: 10
conditions: []
```
{% endhint %}

### apply\_bonus <a href="#apply_bonus" id="apply_bonus"></a>

根据提供的魔咒属性与合成配方增加掉落物的数量。更多信息请参考[➕️ 计算公式](loot-table.md#formula)。

```yaml
type: apply_bonus
enchantment: minecraft:fortune
formula:
  type: ore_drops
```

### set\_count <a href="#set_count" id="set_count"></a>

设置物品的数量。

```yaml
type: set_count
count: 10
add: true  # `true`为添加数量，`false`为设置数量
```

### explosion\_decay <a href="#explosion_decay" id="explosion_decay"></a>

指定物品受到爆炸后数量是否减少。在原版Minecraft中，爆炸通常会导致掉落的方块数量少于原本的数量，正是由该功能控制的。

```yaml
type: explosion_decay
```

### drop\_exp <a href="#drop_exp" id="drop_exp"></a>

掉落一定数量的经验值。

```yaml
type: drop_exp
count: 1
```

## ⚖️ 条件 <a href="#condition" id="condition"></a>

条件可为抽取项和函数提供先决条件。

<details>

<summary>⚖️ 条件</summary>



</details>

## ➕️ 计算公式 <a href="#formula" id="formula"></a>

### ore\_drops <a href="#ore_drops" id="ore_drops"></a>

与原版Minecraft使用相同的掉落算法（矿物掉落随机算法）。

```yaml
type: ore_drops
```

### binomial\_with\_bonus\_count <a href="#binomial_with_bonus_count" id="binomial_with_bonus_count"></a>

与原版Minecraft相同的二项式掉落算法（二项分布随机数）。`extra`表示尝试掉落物品的额外次数，`probability`代表每次成功的概率。魔咒等级会增加尝试次数。

```yaml
type: binomial_with_bonus_count
extra: 3
probability: 0.5
```
