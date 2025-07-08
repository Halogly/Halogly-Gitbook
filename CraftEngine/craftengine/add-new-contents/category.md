---
description: 本页面主要讲解如何向服务器添加新分类。
---

# 📂 分类

在使用物品浏览器时，`category` 用于管理物品的排列顺序和分类规则。

A basic configuration is as follows. Once you complete the setup, it will appear in your /ce menu.\
基本配置如下。设置完成后，它就会出现在你的`/ce`菜单中。

```yaml
categories:
  default:palm_tree:
    name: "<!i><green><i18n:category.palm_tree></green>"
    lore: []
    hidden: false
    priority: 1
    icon: default:palm_log
    list:
      - default:palm_sapling
      - default:palm_leaves
      - default:palm_log
      - default:stripped_palm_log
      - default:palm_wood
      - default:stripped_palm_wood
      - default:palm_planks
```

## 选项说明 <a href="#option-explanation" id="option-explanation"></a>

* `name` 和 `lore` 指定类别图标的标题和描述信息。
* `icon` 指定此类别的物品外观，你需要在插件中配置此物品的设置。
* `priority` 指定显示顺序；`priority` 值越小，其在 GUI 中的显示的优先级越高。
* `hidden` 指定此类别是否在主菜单中显示。你可能想要将一个类别嵌套在另一个类别中；如果要这样做，你就需要将其设置为 `true`。后续会提供相关示例。
* 在 `list` 中，你需要填写物品或类别（类别必须以 `#` 开头，例如 `#default:palm_tree`）。

## 子类别 <a href="#sub-categories" id="sub-categories"></a>

有时，你可能需要一个具有以下结构的分类配置，甚至需要更深层次的嵌套。在这种情况下，你需要灵活地使用 `hidden` 和 `#` 前缀。

```
category_main
  ├ category_1
  ├ category_2
  └ category_3
     ├ item_1
     ├ item_2
     └ item_3
```

```yaml
categories:
  default:default:
    priority: 1
    name: "<!i><white><i18n:category.default.name></white>"
    lore:
      - "<!i><gray><i18n:category.default.lore>"
    icon: default:topaz
    list:
      - "#default:palm_tree"
      - "#default:topaz"
      - "#default:furniture"
      - "#default:misc"
  default:palm_tree:
    name: "<!i><green><i18n:category.palm_tree></green>"
    hidden: true
    icon: default:palm_log
    list:
      - default:palm_sapling
      - default:palm_leaves
      - default:palm_log
      - default:stripped_palm_log
      - default:palm_wood
      - default:stripped_palm_wood
      - default:palm_planks
  default:topaz:
    name: "<!i><#FF8C00><i18n:category.topaz></#FF8C00>"
    hidden: true
    icon: default:topaz
    list:
      - default:topaz
      - default:topaz_ore
      - default:deepslate_topaz_ore
      - default:topaz_axe
      - default:topaz_pickaxe
      - default:topaz_hoe
      - default:topaz_shovel
      - default:topaz_sword
      - default:topaz_bow
      - default:topaz_crossbow
      - default:topaz_rod
  default:furniture:
    name: "<!i><#FFD700><i18n:category.furniture></#FFD700>"
    hidden: true
    icon: default:table_lamp
    list:
      - default:bench
      - default:table_lamp
      - default:wooden_chair
  default:misc:
    name: "<!i><gray><i18n:category.misc></gray>"
    hidden: true
    icon: default:chinese_lantern
    list:
      - default:chinese_lantern
      - default:fairy_flower
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FrcDhHCdZZA6vSyoL1mnX%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=8dddcc02\&sv=2)
主菜单

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F6je6hSGuuxseDsIEwsTS%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=5ce4abef\&sv=2)
子菜单

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FhZqKvQdnJcinwlIa9tae%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=36a479cb\&sv=2)
家具类别

## 提示 <a href="#tip" id="tip"></a>

你也可以为物品本身直接配置物品所属的类别。但请注意，这样我们就无法确定它在类别中的显示顺序。

```yaml
items:
  default:topaz_sword:
    # category: default:topaz
    category:
      - default:topaz # 使用类别列表
    material: golden_sword
    custom-model-data: 1000
    data:
      display-name: "<!i><#FF8C00><i18n:item.topaz_sword>"
      tooltip-style: minecraft:topaz
      components:
        minecraft:max_damage: 64
    model:
      type: minecraft:model
      path: minecraft:item/custom/topaz_sword
      generation:
        parent: "minecraft:item/handheld"
        textures:
          "layer0": "minecraft:item/custom/topaz_sword"
```
