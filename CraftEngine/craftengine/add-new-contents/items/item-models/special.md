---
description: https://zh.minecraft.wiki/w/物品模型映射#special
---

# 👻 特殊

> 渲染一个特殊模型。

使用“minecraft:special”时，需要指定一个 `speical mode` 类型。`path` 参数是用于基础模型渲染。

```yaml
default:gui_head_size_1:
  model:
    type: minecraft:special
    path: minecraft:item/custom/gui_head_size_1
    model:
      type: minecraft:head
      kind: player
```

# 可用特殊模型类型 <a href="#available-special-model-types" id="available-special-model-types"></a>

请参阅 [https://zh.minecraft.wiki/w/物品模型映射#special](https://zh.minecraft.wiki/w/%E7%89%A9%E5%93%81%E6%A8%A1%E5%9E%8B%E6%98%A0%E5%B0%84#special) 了解每个参数的用法。

## minecraft:trident <a href="#minecraft-trident" id="minecraft-trident"></a>

> 渲染三叉戟。

## minecraft:conduit <a href="#minecraft-conduit" id="minecraft-conduit"></a>

> 渲染潮涌核心。

## minecraft:shield <a href="#minecraft-shield" id="minecraft-shield"></a>

> 渲染盾牌。底色和图案取决于 `minecraft:base_color` 和 `minecraft:banner_patterns` 组件。

## minecraft:decorated\_pot <a href="#minecraft-decorated_pot" id="minecraft-decorated_pot"></a>

> 渲染饰纹陶罐。四个面取决于 `minecraft:pot_decorations` 组件。

## minecraft:hanging\_sign <a href="#minecraft-hanging_sign" id="minecraft-hanging_sign"></a>

> 渲染悬挂式告示牌。

```yaml
model:
  type: "minecraft:hanging_sign"
  wood-type: "oak"
  texture: ...
```

## minecraft:standing\_sign <a href="#minecraft-standing_sign" id="minecraft-standing_sign"></a>

> 渲染告示牌。

```yaml
model:
  type: "minecraft:standing_sign"
  wood-type: "oak"
  texture: ...
```

## minecraft:head <a href="#minecraft-head" id="minecraft-head"></a>

> 渲染生物头颅。如果是玩家的头，皮肤取决于 `minecraft:profile` 组件。

```yaml
model:
  type: "minecraft:head"
  kind: player
  texture: ...
  animation: 0.0
```

## minecraft:chest <a href="#minecraft-chest" id="minecraft-chest"></a>

> 渲染箱子。

```yaml
model:
  type: "minecraft:chest"
  openness: 0.0
  texture: ...
```

## minecraft:**shulker\_box** <a href="#minecraft-shulker_box" id="minecraft-shulker_box"></a>

> 渲染潜影盒。

```yaml
model:
  type: "minecraft:shulker_box"
  openness: 0.0
  orientation: up
  texture: ...
```

## minecraft:**bed** <a href="#minecraft-bed" id="minecraft-bed"></a>

> 渲染床。

```yaml
model:
  type: "minecraft:bed"
  texture: ...
```

## minecraft:**banner** <a href="#minecraft-banner" id="minecraft-banner"></a>

> 渲染带有 `minecraft:banner_patterns` 组件图案的旗帜。

```yaml
model:
  type: "minecraft:bed"
  color: white
```
