---
description: This page mainly explains how to add new items to your server.
---

# 物品

### Sections to Configure <a href="#sections-to-configure" id="sections-to-configure"></a>

A complete item configuration contains the following sections:

* **material** (Required)

The `material` serves as the foundational template of the item, such as `paper` or `wooden_sword`.

* **client-bound-material** (Optional)

The `client-bound-material` used for this item. You can use this feature to assign completely different base material for items on the server/client side, thereby affecting their specific behaviors in server/client contexts.

* **custom-model-data** (Optional)

The `custom-model-data` is a positive integer, and custom items of the same `material` should possess distinct `custom-model-data` values. The `custom-model-data` determines the model displayed for the item and is crucial for the `model` section below.

Copy

```
items:
  default:topaz_rod:
    material: fishing_rod
    custom-model-data: 1000
    data:
      display-name: "<!i><#FF8C00>Topaz Rod"
    model:
      template: models:fishing_rod_2d
      arguments:
        rod_model: minecraft:item/custom/topaz_rod
        rod_texture: minecraft:item/custom/topaz_rod
        rod_cast_model: minecraft:item/custom/topaz_rod_cast
        rod_cast_texture: minecraft:item/custom/topaz_rod_cast
```

* **item-model** (1.21.2+) (Optional)

Defines the item model resource location of this item. For instance `default:custom_book`

1.21.4+ `assets/[namespace]/items/` 1.21.2+ `assets/[namespace]/models/item/`

Copy

```
items:
  default:topaz_rod:
    material: fishing_rod
    item-model: minecraft:topaz_rod
    data:
      display-name: "<!i><#FF8C00>Topaz Rod"
    model:
      template: models:fishing_rod_2d
      arguments:
        rod_model: minecraft:item/custom/topaz_rod
        rod_texture: minecraft:item/custom/topaz_rod
        rod_cast_model: minecraft:item/custom/topaz_rod_cast
        rod_cast_texture: minecraft:item/custom/topaz_rod_cast
```

Using custom model data has better version compatibility because it has been released since 1.14 while `item_model` requires at least 1.21.2

You can use `custom-model-data` and `item-model` at the same time

When configuring the model section, you must specify either `custom-model-data` or `item-model`. If your resource pack supports version 1.21.2 or later, the plugin will automatically use the item ID as the value for `item-model`. However, if your item ID contains characters that violate Minecraft's rules, it may cause the resource pack to fail to load properly. In such cases, you must use `custom-model-data` or specify a valid `item-model` value.

* **data / client-bound-data** (Optional)

[🔢 Item Data](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data)

* **behavior(s)** (Optional)

[🕹️ Item Behaviors](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-behaviors)

* **settings** (Optional)

[⚙️ Item Settings](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-settings)

* **model / legacy-model** (Optional)

[🟰 Item Models](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models)

* **events** (Optional)

[🪇 Events](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/events)

* **category** (Optional)

[📂 Category](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/category)

### Full Config Overview <a href="#full-config-overview" id="full-config-overview"></a>

Copy

```
items:
  default:palm_log:
    material: paper
    custom-model-data: 1000
    settings:
      fuel-time: 300
      tags:
        - "default:palm_logs"
        - "minecraft:logs"
        - "minecraft:logs_that_burn"
    data:
      display-name: "<!i>Palm Log"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/palm_log"
      generation:
        parent: "minecraft:block/custom/palm_log"
    behavior:
      type: block_item
      block: default:palm_log
```
