---
description: 此页面主要讲解如何向服务器添加新物品。
---

# 🗡️ 物品

## 配置部分 <a href="#sections-to-configure" id="sections-to-configure"></a>

完整的物品配置需要包含以下部分：

* **材料**（必需）

`material`是物品的基础模板，如`paper`或`wooden_sword`。

* **客户端材料**（可选）

用于物品的`client-bound-material`。你可以使用此功能为服务端/客户端上的物品分配完全不同的基础材料，从而影响它们在服务端/客户端环境中的特定行为。

* **自定义模型数据**（可选）

`custom-model-data`值为正整数，具有相同`material`的自定义物品需具有不同的`custom-model-data`值。`custom-model-data`决定物品显示的模型，对于下面的`model`部分也至关重要。

```yaml
items:
  default:topaz_rod:
    material: fishing_rod
    custom-model-data: 1000
    data:
      display-name: "<!i><#FF8C00>黄玉钓竿"
    model:
      template: models:fishing_rod_2d
      arguments:
        rod_model: minecraft:item/custom/topaz_rod
        rod_texture: minecraft:item/custom/topaz_rod
        rod_cast_model: minecraft:item/custom/topaz_rod_cast
        rod_cast_texture: minecraft:item/custom/topaz_rod_cast
```

* **物品模型**（可选，1.21.2+）

定义物品的模型资源位置。例如`default:custom_book`。

1.21.4+ `assets/[命名空间]/items/`
1.21.2+ `assets/[命名空间]/models/item/`

```yaml
items:
  default:topaz_rod:
    material: fishing_rod
    item-model: minecraft:topaz_rod
    data:
      display-name: "<!i><#FF8C00>黄玉钓竿"
    model:
      template: models:fishing_rod_2d
      arguments:
        rod_model: minecraft:item/custom/topaz_rod
        rod_texture: minecraft:item/custom/topaz_rod
        rod_cast_model: minecraft:item/custom/topaz_rod_cast
        rod_cast_texture: minecraft:item/custom/topaz_rod_cast
```

{% hint style="success" %}
使用自定义模型数据具有更好的版本兼容性，因为它从1.14版本开始就已存在，而`item_model`则要求至少1.21.2版本。

你可以同时使用`custom-model-data`和`item-model`。
{% endhint %}

{% hint style="danger" %}
在配置模型部分时，必须指定`custom-model-data`或`item-model`。如果你的资源包支持1.21.2版本或更高版本，插件会自动使用物品ID作为`item-model`的值。但是，如果你的物品ID包含违反Minecraft规定的字符，那就可能会导致资源包无法正常加载。在这种情况下，你必须使用`custom-model-data`或指定一个有效的`item-model`值。
{% endhint %}

* **数据或客户端数据**（可选）

<details>

<summary><a href="./item-data/README.md">🔢 物品数据</a></summary>

* **行为**（可选）

<details>

<summary><a href="./item-behaviors/README.md">🕹️ 物品行为</a></summary>

* **设置**（可选）

<details>

<summary><a href="./item-settings.md">⚙️ 物品设置</a></summary>

* **模型或旧版模型**（可选）

<details>

<summary><a href="./item-models/README.md">🟰 物品模型</a></summary>

* **事件**（可选）

<details>

<summary><a href="../events.md">🪇 事件</a></summary>

* **分类**（可选）

<details>

<summary><a href="../category.md">📂 分类</a></summary>

## 完整配置概览 <a href="#full-config-overview" id="full-config-overview"></a>

```yaml
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
      display-name: "<!i>棕榈原木"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/palm_log"
      generation:
        parent: "minecraft:block/custom/palm_log"
    behavior:
      type: block_item
      block: default:palm_log
```
