---
description: https://minecraft.wiki/w/Items_model_definition#range_dispatch
---

# 📡 范围分配

> Render an item model based on numeric property. Will select last entry with threshold less or equal to property value.\
> 根据数值属性渲染物品模型。将选择最后一个阈值小于或等于属性值的条目。

When using "minecraft:range\_dispatch," you need to specify the numeric `property` type. `scale` represents the factor to multiply the property value with, `entries` represent the models under different numerical values, and `fallback` represents the item model object if no valid entry was found. It is optional, but if not specified, it will render a "missing" error model.\
在使用"minecraft:range\_dispatch"时，需要指定数值类型 `property` 。 `scale` 表示与属性值相乘的因子， `entries` 表示不同数值下的模型， `fallback` 表示如果没有找到有效条目时的物品模型对象。这是可选的，如果未指定，将渲染一个"缺失"的错误模型。

Copy  复制

```
items:
  default:range_dispatch_item:
    model:
      type: "minecraft:range_dispatch"
      property: "minecraft:crossbow/pull"
      entries:
        - model:
            type: minecraft:model
            path: "minecraft:item/custom/model_1"
          threshold: 0.58
        - model:
            type: minecraft:model
            path: "minecraft:item/custom/model_2"
          threshold: 1.0
      fallback:
        type: minecraft:model
        path: "minecraft:item/custom/model_3"
```

### Available Properties  可用属性 <a href="#available-properties" id="available-properties"></a>

check [https://minecraft.wiki/w/Items\_model\_definition#range\_dispatch](https://minecraft.wiki/w/Items_model_definition#range_dispatch) for the usage of each argument\
请查看 https://minecraft.wiki/w/Items\_model\_definition#range\_dispatch 了解每个参数的用法

#### minecraft:**crossbow/pull** <a href="#minecraft-crossbow-pull" id="minecraft-crossbow-pull"></a>

> Return crossbow-specific use time.\
> 返回弓弩特有的使用时间。

#### minecraft:**bundle/fullness** <a href="#minecraft-bundle-fullness" id="minecraft-bundle-fullness"></a>

> Return weight of `minecraft:bundle_contents` component or `0` if not present.\
> 返回 `minecraft:bundle_contents` 组件的重量，如果不存在则返回 `0` 。

#### minecraft:**cooldown** <a href="#minecraft-cooldown" id="minecraft-cooldown"></a>

> Return remaining cooldown for item, scaled between `0.0` to `1.0`.\
> 返回物品的剩余冷却时间，范围在 `0.0` 到 `1.0` 之间。

#### minecraft:**compass** <a href="#minecraft-compass" id="minecraft-compass"></a>

> Return an angle, scaled from `0.0` to `1.0` in x-z plane between holder position and target. If target is not valid (not present, in other dimension or too close to holder position) random value will be returned.\
> 返回一个角度值，范围在 `0.0` 到 `1.0` 之间，表示持有者位置和目标在 x-z 平面上的方向。如果目标无效（不存在、在其他维度或离持有者位置太近），将返回随机值。

Copy  复制

```
type: "minecraft:range_dispatch"
property: "minecraft:compass"
target: spawn
wobble: true
```

#### minecraft:**count** <a href="#minecraft-count" id="minecraft-count"></a>

> Return stack size.  返回堆栈大小。

Copy  复制

```
type: "minecraft:range_dispatch"
property: "minecraft:count"
normalize: true
```

#### minecraft:**damage** <a href="#minecraft-damage" id="minecraft-damage"></a>

> Return value for `minecraft:damage` component or `0` if not present.\
> 返回 `minecraft:damage` 组件的值，如果不存在则返回 `0` 。

Copy  复制

```
type: "minecraft:range_dispatch"
property: "minecraft:damage"
normalize: true
```

#### minecraft:**time** <a href="#minecraft-time" id="minecraft-time"></a>

> Return value of a in-game time, scaled betewen `0.0` to `1.0`.\
> 游戏内时间的返回值，在 `0.0` 到 `1.0` 之间缩放。

Copy  复制

```
type: "minecraft:range_dispatch"
property: "minecraft:time"
source: daytime
wobble: true
```

#### minecraft:**use\_cycle**  minecraft:使用循环 <a href="#minecraft-use_cycle" id="minecraft-use_cycle"></a>

> Return remaining use ticks modulo `period`.\
> 返回剩余使用次数模 `period` 。

Copy  复制

```
type: "minecraft:range_dispatch"
property: "minecraft:use_cycle"
period: 1.0
```

#### minecraft:**use\_duration** <a href="#minecraft-use_duration" id="minecraft-use_duration"></a>

> Return item use ticks.  返回物品使用刻。

Copy  复制

```
type: "minecraft:range_dispatch"
property: "minecraft:use_duration"
remaining: false
```

#### minecraft:**custom\_model\_data** <a href="#minecraft-custom_model_data" id="minecraft-custom_model_data"></a>

> Return value from `floats` list in `minecraft:custom_model_data` component or `0` if not present.\
> 从 `floats` 列表中返回 `minecraft:custom_model_data` 组件的值，如果不存在则返回 `0` 。

Copy  复制

```
type: "minecraft:range_dispatch"
property: "minecraft:custom_model_data"
index: 0
```
