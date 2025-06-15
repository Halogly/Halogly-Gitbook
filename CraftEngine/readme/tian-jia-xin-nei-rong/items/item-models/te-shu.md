---
description: https://minecraft.wiki/w/Items_model_definition#special
---

# 👻 特殊

> Render a special model.  渲染一个特殊模型。

When using "minecraft:special," you need to specify a `speical mode` type. `path` argument is required for the base model rendering.\
使用"minecraft:special"时，需要指定一个 `speical mode` 类型。 `path` 参数是用于基础模型渲染的。

Copy  复制

```
default:gui_head_size_1:
  model:
    type: minecraft:special
    path: minecraft:item/custom/gui_head_size_1
    model:
      type: minecraft:head
      kind: player
```

### Available Special Model Types 可用特殊模型类型 <a href="#available-special-model-types" id="available-special-model-types"></a>

check [https://minecraft.wiki/w/Items\_model\_definition#special](https://minecraft.wiki/w/Items_model_definition#special) for the usage of each argument\
参考 https://minecraft.wiki/w/Items\_model\_definition#special 了解每个参数的用法

#### minecraft:trident <a href="#minecraft-trident" id="minecraft-trident"></a>

> Render a trident.  渲染三叉戟。

#### minecraft:conduit <a href="#minecraft-conduit" id="minecraft-conduit"></a>

> Render conduit.  渲染导流器。

#### minecraft:shield <a href="#minecraft-shield" id="minecraft-shield"></a>

> Render a shield. Uses patterns from `minecraft:banner_patterns` component and color from `minecraft:base_color` component.\
> 渲染盾牌。使用 `minecraft:banner_patterns` 组件的图案和 `minecraft:base_color` 组件的颜色。

#### minecraft:decorated\_pot  minecraft:装饰花盆 <a href="#minecraft-decorated_pot" id="minecraft-decorated_pot"></a>

> Render a decorated pot. Uses values from `minecraft:pot_decorations` component.\
> 渲染一个装饰花盆。使用 `minecraft:pot_decorations` 组件的值。

#### minecraft:hanging\_sign  minecraft:悬挂式标志 <a href="#minecraft-hanging_sign" id="minecraft-hanging_sign"></a>

> Renders a hanging sign.  渲染一个悬挂式标志。

Copy  复制

```
model:
  type: "minecraft:hanging_sign"
  wood-type: "oak"
  texture: ...
```

#### minecraft:standing\_sign <a href="#minecraft-standing_sign" id="minecraft-standing_sign"></a>

> Renders a standing sign.  渲染一个立式标志。

Copy  复制

```
model:
  type: "minecraft:standing_sign"
  wood-type: "oak"
  texture: ...
```

#### minecraft:head <a href="#minecraft-head" id="minecraft-head"></a>

> Render a head. Uses profile from `minecraft:profile` component when applicable.\
> 渲染一个头部。在适用情况下，使用 `minecraft:profile` 组件的资料。

Copy  复制

```
model:
  type: "minecraft:head"
  kind: player
  texture: ...
  animation: 0.0
```

#### minecraft:chest <a href="#minecraft-chest" id="minecraft-chest"></a>

> Render a single chest.  渲染单个箱子。

Copy  复制

```
model:
  type: "minecraft:chest"
  openness: 0.0
  texture: ...
```

#### minecraft:**shulker\_box** <a href="#minecraft-shulker_box" id="minecraft-shulker_box"></a>

> Render a shulker box.  渲染一个潜影盒。

Copy  复制

```
model:
  type: "minecraft:shulker_box"
  openness: 0.0
  orientation: up
  texture: ...
```

#### minecraft:**bed** <a href="#minecraft-bed" id="minecraft-bed"></a>

> Render a whole bed.  渲染一张完整的床。

Copy  复制

```
model:
  type: "minecraft:bed"
  texture: ...
```

#### minecraft:**banner** <a href="#minecraft-banner" id="minecraft-banner"></a>

> Render a banner with patterns from `minecraft:banner_patterns` component.\
> 渲染一个带有 `minecraft:banner_patterns` 组件图案的横幅。

Copy  复制

```
model:
  type: "minecraft:bed"
  color: white
```
