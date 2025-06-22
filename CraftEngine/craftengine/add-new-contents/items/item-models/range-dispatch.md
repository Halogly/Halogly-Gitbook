---
description: https://zh.minecraft.wiki/w/物品模型映射#range_dispatch
---

# 📡 范围调配

> 根据数值属性渲染物品模型。游戏会按照给定阈值从小到大排序，找到数值属性第一个超过或等于的阈值，并使用对应物品模型映射。

在使用“minecraft:range\_dispatch”时，需要指定数值类型 `property`。 `scale` 表示与属性值相乘的因子，`entries` 表示不同数值下的模型，`fallback` 表示如果没有找到有效阈值时的物品模型对象。这是可选的，如果未指定，会渲染为“丢失”的错误模型。

```yaml
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

# Available Properties 可用属性 <a href="#available-properties" id="available-properties"></a>

请参阅 [https://zh.minecraft.wiki/w/物品模型映射#range\_dispatch](https://zh.minecraft.wiki/w/物品模型映射#range_dispatch) 了解每个参数的用法

## minecraft:**crossbow/pull** 弩 <a href="#minecraft-crossbow-pull" id="minecraft-crossbow-pull"></a>

> 返回弩的拉伸程度。

## minecraft:**bundle/fullness** 收纳袋 <a href="#minecraft-bundle-fullness" id="minecraft-bundle-fullness"></a>

> 返回 `minecraft:bundle_contents` 组件的容量，如果不存在则返回 `0`。

## minecraft:**cooldown** 冷却 <a href="#minecraft-cooldown" id="minecraft-cooldown"></a>

> 返回物品的剩余冷却时间，范围在 `0.0` 到 `1.0` 之间。

## minecraft:**compass** 指南针 <a href="#minecraft-compass" id="minecraft-compass"></a>

> 返回一个角度值，范围在 `0.0` 到 `1.0` 之间，表示持有者位置和目标在 x-z 平面上的方向。如果目标无效（不存在、在其他维度或离持有者位置太近），则返回随机值。

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:compass"
target: spawn
wobble: true
```

## minecraft:**count** 数量 <a href="#minecraft-count" id="minecraft-count"></a>

> 返回物品数量。

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:count"
normalize: true
```

## minecraft:**damage** 损坏程度 <a href="#minecraft-damage" id="minecraft-damage"></a>

> 返回 `minecraft:damage` 组件的值，如果不存在则返回 `0`。

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:damage"
normalize: true
```

## minecraft:**time** 时间 <a href="#minecraft-time" id="minecraft-time"></a>

> 游戏内时间的返回值，范围在 `0.0` 到 `1.0` 之间。

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:time"
source: daytime
wobble: true
```

## minecraft:**use\_cycle** 使用周期 <a href="#minecraft-use_cycle" id="minecraft-use_cycle"></a>

> 返回剩余使用时间 `period`。

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:use_cycle"
period: 1.0
```

## minecraft:**use\_duration** 使用进度 <a href="#minecraft-use_duration" id="minecraft-use_duration"></a>

> 返回物品使用进度。

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:use_duration"
remaining: false
```

## minecraft:**custom\_model\_data** 自定义模型数据 <a href="#minecraft-custom_model_data" id="minecraft-custom_model_data"></a>

> 从 `floats` 列表中返回 `minecraft:custom_model_data` 组件的值，如果不存在则返回 `0`。

```yaml
type: "minecraft:range_dispatch"
property: "minecraft:custom_model_data"
index: 0
```
