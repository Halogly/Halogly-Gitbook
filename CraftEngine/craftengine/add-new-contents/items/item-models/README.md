---
description: 本页面主要讲解如何为物品配置模型。
---

# 🟰 物品模型

## 🟰 Item Models

自 1.21.4 版本起，Minecraft 开始支持更复杂的物品模型。因此你可以为物品创建更多动态变体。本教程适用于 1.21.4 及以上版本。对于旧版本，插件会降级相应的模型文件（注意：这并非表明与旧版本完全兼容，因为许多条件和模型类型在旧版本中是不存在的）。

如果你发现 CraftEngine 在最新版的 Minecraft 中缺少了某些功能，你可以在 GitHub 上提交 issue，让开发者注意到这个问题。

## 介绍 <a href="#introduction" id="introduction"></a>

以最简单的 `minecraft:model` [📐 模型](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/model)类型为例。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FwSGX7wtV4qUdSwqNGm6Z%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=49fa69ce\&sv=2)

```yaml
items:
  default:topaz_pickaxe:
    model:
      type: minecraft:model
      path: minecraft:item/custom/topaz_pickaxe
      generation:
        parent: "minecraft:item/handheld"
        textures:
          "layer0": "minecraft:item/custom/topaz_pickaxe"
```

如果没有指定 `type`，插件会默认使用 `minecraft:model`。因此，上面的配置与下面的配置相同。

```yaml
items:
  default:topaz_pickaxe:
    model:
      path: minecraft:item/custom/topaz_pickaxe
      generation:
        parent: "minecraft:item/handheld"
        textures:
          "layer0": "minecraft:item/custom/topaz_pickaxe"
```

如果你不确定如何指定 `generation` 模型和 `path` 模型，请阅读[🏭️ 模型生成](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/model-generation)。

从上述配置中，我们可以看到在模型部分，你需要填写模型的类型及其对应的参数。以下是所有可用模型类型的列表。一些模型（如范围分配、选择、组合和条件）支持嵌套模型使用。你可以点击下面的链接跳转到相应的模型类型。只有阅读完所有的内容后，我们才能继续讨论更复杂的示例。

[📐 模型](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/model)[🧩 组合](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/composite)[⚖️ 条件](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/condition)[📡 范围调配](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/range-dispatch)[✅ 选择](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/select)[👻 特殊](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/special)

## 示例 <a href="#examples" id="examples"></a>

在以下示例中，通过组合 `condition`、`model` 和 `range_dispatch` 创建了一个自动生成 2D 的弩的模板。

```yaml
templates:
  default:model/crossbow_2d:
    type: "minecraft:condition"
    property: "minecraft:using_item"
    on-false:
      type: "minecraft:select"
      property: "minecraft:charge_type"
      cases:
        - when: arrow
          model:
            type: minecraft:model
            path: "${arrow_model}"
            generation:
              parent: "minecraft:item/crossbow_arrow"
              textures:
                "layer0": "${arrow_texture}"
        - when: rocket
          model:
            type: minecraft:model
            path: "${firework_model}"
            generation:
              parent: "minecraft:item/crossbow_firework"
              textures:
                "layer0": "${firework_texture}"
      fallback:
        type: minecraft:model
        path: "${model}"
        generation:
          parent: "minecraft:item/crossbow"
          textures:
            "layer0": "${texture}"
    on-true:
      type: "minecraft:range_dispatch"
      property: "minecraft:crossbow/pull"
      entries:
        - model:
            type: minecraft:model
            path: "${pulling_1_model}"
            generation:
              parent: "minecraft:item/crossbow_pulling_1"
              textures:
                "layer0": "${pulling_1_texture}"
          threshold: 0.58
        - model:
            type: minecraft:model
            path: "${pulling_2_model}"
            generation:
              parent: "minecraft:item/crossbow_pulling_2"
              textures:
                "layer0": "${pulling_2_texture}"
          threshold: 1.0
      fallback:
        type: minecraft:model
        path: "${pulling_0_model}"
        generation:
          parent: "minecraft:item/crossbow_pulling_0"
          textures:
            "layer0": "${pulling_0_texture}"
```

#### 旧版模型 <a href="#legacy-model" id="legacy-model"></a>

\*\*“旧版模型”\*\*特指 **1.21.3 及更早版本**中使用的物品模型格式。你可以使用 **legacy-model** 部分来指定旧版物品模型格式。然而，在大多数情况下，你不需要这样做，因为插件会在一些情况下自动将 **1.21.4 物品模型**转换为旧版格式。只有当旧版模型格式存在问题时，你才应该使用此配置部分。

```yaml
items#topaz_gears:
  default:topaz_rod:
    material: fishing_rod
    item-model: default:topaz_rod
    custom-model-data: 1000
    settings:
      tags:
        - "default:topaz_tools"
    data:
      item-name: "<!i><#FF8C00><i18n:item.topaz_rod>"
      tooltip-style: minecraft:topaz
    model:
      template: default:model/simplified_fishing_rod_2d
      arguments:
        path: minecraft:item/custom/topaz_rod
        cast_path: minecraft:item/custom/topaz_rod_cast
    # 如果你在 legacy-model 部分指定了一个模型，
    # 插件会使用你手动定义的模型，而不是使用自动转换的旧版格式模型。
    legacy-model:
      path: minecraft:item/custom/topaz_rod
      overrides:
        - path: minecraft:item/custom/topaz_rod_cast
          predicate: 
            cast: 1
```
