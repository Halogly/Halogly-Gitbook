---
description: >-
  This page mainly explains how to add new categories to your server.
  本页面主要解释如何向您的服务器添加新分类。
---

# 分类

The `category` is used to manage the arrangement order and classification rules of items when using the item browser.\
在使用物品浏览器时， `category` 用于管理物品的排列顺序和分类规则。

A basic configuration is as follows. Once you complete the setup, it will appear in your /ce menu.\
基本配置如下。设置完成后，它将出现在您的 /ce 菜单中。

Copy 复制

```
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

#### Option Explanation 选项说明 <a href="#option-explanation" id="option-explanation"></a>

* The `name` and `lore` determine the title and description of the category icon.\
  `name` 和 `lore` 确定分类图标的标题和描述。
* The `icon` represents the visual appearance of the item for this category, and you are required to configure the settings for this item within the plugin.\
  `icon` 代表此分类中项目的视觉外观，您需要在插件中配置此项目的设置。
* The `priority` determines the display order; the smaller the 'priority' value, the higher the precedence it has for presentation in the GUI.\
  `priority` 决定显示顺序；'priority' 值越小，其在 GUI 中的显示优先级越高。
* The `hidden` attribute determines whether this category is displayed in the main menu. There may be instances where you wish to nest a category within another; in such cases, you would set this attribute to `true`. Relevant examples will be provided later.\
  `hidden` 属性决定此分类是否在主菜单中显示。你可能希望将一个分类嵌套在另一个分类中；在这种情况下，你需要将此属性设置为 `true` 。后续将提供相关示例。
* In the `list`, you need to fill in items or categories (categories must be prefixed with a '#', for example, `#default:palm_tree` ).\
  在 `list` 中，你需要填写项目或分类（分类必须以 '#' 开头，例如 `#default:palm_tree` ）。

#### Sub Categories 子分类 <a href="#sub-categories" id="sub-categories"></a>

At times, you may require a category configuration with the following structure, or even with deeper nesting. In such cases, you will need to flexibly utilize `hidden` and the `#` prefix.\
有时，你可能需要一个具有以下结构的分类配置，甚至需要更深层次的嵌套。在这种情况下，你需要灵活地使用 `hidden` 和 `#` 前缀。

Copy 复制

```
category_main
  ├ category_1
  ├ category_2
  └ category_3
     ├ item_1
     ├ item_2
     └ item_3
```

Copy 复制

```
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

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FrcDhHCdZZA6vSyoL1mnX%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=8dddcc02\&sv=2)main menu 主菜单

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F6je6hSGuuxseDsIEwsTS%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=5ce4abef\&sv=2)sub menu 子菜单

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FhZqKvQdnJcinwlIa9tae%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=36a479cb\&sv=2)furniture category 家具类别

#### Tip 提示 <a href="#tip" id="tip"></a>

You can also directly configure the category to which an item belongs within the item itself. However, please note that in such cases, we cannot guarantee the order in which it will be displayed within the category.\
你也可以在项目本身中直接配置项目所属的分类。但是请注意，在这种情况下，我们无法保证它在分类中的显示顺序。

Copy 复制

```
items:
  default:topaz_sword:
    # category: default:topaz 
    category:
      - default:topaz # use a list of categories
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
