---
description: https://zh.minecraft.wiki/w/物品模型映射#select
---

# ✅ 选择

## ✅ 选择

在使用“minecraft:select”时，需要指定一个 `property` 类型。`cases` 表示匹配场景的枚举值，而 `fallback` 表示如果没有找到有效枚举值时的物品模型对象。这是可选的，如果未指定，会渲染为“丢失”的错误模型。

```yaml
items:
  default:select_item:
    model:
      type: "minecraft:select"
      property: "minecraft:charge_type"
      cases:
        - when: arrow
          model:
            type: minecraft:model
            path: "minecraft:item/custom/model_1"
        - when: rocket
          model:
            type: minecraft:model
            path: "minecraft:item/custom/model_2"
      fallback:
        type: minecraft:model
        path: "minecraft:item/custom/model_3"
```

## 可用属性 <a href="#available-properties" id="available-properties"></a>

请参阅 [https://zh.minecraft.wiki/w/物品模型映射#select](https://zh.minecraft.wiki/w/%E7%89%A9%E5%93%81%E6%A8%A1%E5%9E%8B%E6%98%A0%E5%B0%84#select) 了解每个参数的用法。

### minecraft:**charge\_type** <a href="#minecraft-charge_type" id="minecraft-charge_type"></a>

> 返回存储在 `minecraft:charged_projectiles` 组件中的物品类型。

### minecraft:**context\_dimension** <a href="#minecraft-context_dimension" id="minecraft-context_dimension"></a>

> 如果存在，返回当前玩家所在维度的命名空间 ID。

### minecraft:**context\_entity\_type** <a href="#minecraft-context_entity_type" id="minecraft-context_entity_type"></a>

> 如果存在，返回持有物品实体的类型。

### minecraft:**display\_context** <a href="#minecraft-display_context" id="minecraft-display_context"></a>

> 返回当前物品的渲染位置。

### minecraft:**main\_hand** <a href="#minecraft-main_hand" id="minecraft-main_hand"></a>

> 返回持有物品的玩家主手是哪一只手。

### minecraft:**trim\_material** <a href="#minecraft-trim_material" id="minecraft-trim_material"></a>

> 如果存在，返回 `minecraft:trim` 组件的 `material` 字段值。

### minecraft:**block\_state** <a href="#minecraft-block_state" id="minecraft-block_state"></a>

> 从 `minecraft:block_state` 组件中返回某些属性的值。

```yaml
type: "minecraft:select"
property: "minecraft:block_state"
block-state-property: "facing"
```

### minecraft:**component** <a href="#minecraft-component" id="minecraft-component"></a>

> 从可持久化[组件](https://zh.minecraft.wiki/w/%E6%95%B0%E6%8D%AE%E7%BB%84%E4%BB%B6)中返回值。如果选定的值来自注册表，而当前的数据包并没有提供它，则该模型会被静默忽略。

```yaml
type: "minecraft:select"
property: "minecraft:component"
component: "minecraft:unbreakable"
```

### minecraft:**custom\_model\_data** <a href="#minecraft-custom_model_data" id="minecraft-custom_model_data"></a>

> 从 `minecraft:custom_model_data` 组件中的 `strings` 列表返回值。

```yaml
type: "minecraft:select"
property: "minecraft:custom_model_data"
index: 0
```

### minecraft:**local\_time** <a href="#minecraft-local_time" id="minecraft-local_time"></a>

> 返回当前时间，并根据给定格式进行格式化。该值每秒更新一次。有关区域设置、时区和格式的完整格式文档，请参阅 ICU（International Components for Unicode）文档。

```yaml
type: "minecraft:select"
property: "minecraft:local_time"
locale: "en_US"
time-zone: "GMT+0:45"
pattern: "HH:mm:ss"
```
