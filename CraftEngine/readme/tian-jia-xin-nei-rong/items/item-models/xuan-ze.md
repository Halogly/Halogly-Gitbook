---
description: https://minecraft.wiki/w/Items_model_definition#select
---

# ✅ 选择

When using "minecraft:select," you need to specify a `property` type. `cases` represent a list of scenarios to match against, while `fallback` represents the item model object that will be used if no valid entry is found. It is optional, but if not provided, a "missing" error model will be rendered.\
在使用"minecraft:select"时，需要指定一个 `property` 类型。 `cases` 表示匹配场景的列表，而 `fallback` 表示如果没有找到有效条目将使用的物品模型对象。它是可选的，如果未提供，将渲染"missing"错误模型。

Copy  复制

```
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

### Available Properties  可用属性 <a href="#available-properties" id="available-properties"></a>

check [https://minecraft.wiki/w/Items\_model\_definition#select](https://minecraft.wiki/w/Items_model_definition#select) for the usage of each argument\
请查看 https://minecraft.wiki/w/Items\_model\_definition#select 了解每个参数的用法。

#### minecraft:**charge\_type** <a href="#minecraft-charge_type" id="minecraft-charge_type"></a>

> Return charge type stored in `minecraft:charged_projectiles` component.\
> 返回存储在 `minecraft:charged_projectiles` 组件中的充电类型。

#### minecraft:**context\_dimension** <a href="#minecraft-context_dimension" id="minecraft-context_dimension"></a>

> Return the ID of the dimension in context, if any.\
> 返回上下文维度（如果有）的 ID。

#### minecraft:**context\_entity\_type** <a href="#minecraft-context_entity_type" id="minecraft-context_entity_type"></a>

> Return the holding entity type, if present.\
> 返回持有实体类型，如果存在。

#### minecraft:**display\_context** <a href="#minecraft-display_context" id="minecraft-display_context"></a>

> Return context this item is rendered in.\
> 返回该物品渲染的上下文。

#### minecraft:**main\_hand** <a href="#minecraft-main_hand" id="minecraft-main_hand"></a>

> Return main hand of holding player.\
> 返回持有玩家的主手。

#### minecraft:**trim\_material** <a href="#minecraft-trim_material" id="minecraft-trim_material"></a>

> Return value of `material` field from `minecraft:trim` component, if present.\
> 如果存在，返回 `minecraft:trim` 组件的 `material` 字段值。

#### minecraft:**block\_state** <a href="#minecraft-block_state" id="minecraft-block_state"></a>

> Return value for some property from `minecraft:block_state` component.\
> 从 `minecraft:block_state` 组件中返回某些属性的值。

Copy  复制

```
type: "minecraft:select"
property: "minecraft:block_state"
block-state-property: "facing"
```

#### minecraft:**component** <a href="#minecraft-component" id="minecraft-component"></a>

> Return value from a [component](https://minecraft.wiki/w/Data_component_format). If the selected value comes from a registry and the current datapacks does not provide it, the entry will be silently ignored.\
> 从组件中返回值。如果选定的值来自注册表，而当前的 datapacks 没有提供它，该条目将被静默忽略。

Copy  复制

```
type: "minecraft:select"
property: "minecraft:component"
component: "minecraft:unbreakable"
```

#### minecraft:**custom\_model\_data** <a href="#minecraft-custom_model_data" id="minecraft-custom_model_data"></a>

> Return value from `strings` list in `minecraft:custom_model_data` component.\
> 从 `minecraft:custom_model_data` 组件中的 `strings` 列表返回值。

Copy  复制

```
type: "minecraft:select"
property: "minecraft:custom_model_data"
index: 0
```

#### minecraft:**local\_time** <a href="#minecraft-local_time" id="minecraft-local_time"></a>

> Returns the current time formatted according to a given pattern. The value is updated every second. For full format documentation for locale, time zone and pattern, see ICU (International Components for Unicode) documentation.\
> 返回当前时间，并根据给定格式进行格式化。该值每秒更新一次。有关区域设置、时区和格式的完整格式文档，请参阅 ICU（International Components for Unicode）文档。

Copy  复制

```
type: "minecraft:select"
property: "minecraft:local_time"
locale: "en_US"
time-zone: "GMT+0:45"
pattern: "HH:mm:ss"
```
