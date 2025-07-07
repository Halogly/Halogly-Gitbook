---
description: 与物品数据不同，本页面的设置内容属于插件处理的范畴。
---

# ⚙️ 物品设置

## fuel-time <a href="#fuel-time" id="fuel-time"></a>

设置要燃烧多少刻的时间。

```yaml
fuel-time: 100
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FETo97tqrp6GsxMMc4zOX%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=624f167b\&sv=2)

## tags <a href="#tags" id="tags"></a>

参考[📖 合成配方](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/recipes)。

```yaml
tags:
  - "default:palm_logs"
  - "minecraft:logs"
  - "minecraft:logs_that_burn"
```

## equippable 可穿戴性（1.21.2+） <a href="#equippable-1.21.2" id="equippable-1.21.2"></a>

请注意[🔢 物品数据](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data)和[⚙️ 物品设置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-settings)中的 `equippable` 和 `equippable` 并不相同。`settings` 中的 `equippable` 会自动为用户生成相关的 JSON 文件，能兼容许多版本，而 `data` 中的 `equippable` 则需要用户在资源包中手动创建 JSON 文件，并且仅支持 1.21.2 及以上版本。

Methods of creating custom armor using leather combined with shaders will never be supported. Utilizing core shaders often results in poorer compatibility with client shaders. Moreover, this approach is not considered stable or reliable by the developers of Minecraft, and we should strive to avoid the excessive use of core shaders.\
永远不支持使用皮革结合着色器创建自定义盔甲的方法。使用 Minecraft 的核心着色器基本都会导致与客户端着色器的兼容性变差。此外，这种做法对于 Minecraft 的开发者来说并不稳定可靠，我们应该尽量避免过度使用核心着色器。

```yaml
equippable:
  # 必需参数
  # 放置物品的槽位
  slot: head # HEAD / CHEST / LEGS / FEET / BODY / MAIN_HAND / OFF_HAND / SADDLE
  
  # 这个目录指的是 assets/<命名空间>/equipment/<id>.json
  asset-id: topaz
  # 在实际操作中，你只需要从下方的选项中选择你希望使用的条目，并进行相应的配置。
  # 请注意，当多个物品共用同一个 asset-id 时，你必须确保它们的纹理路径一致；
  # 否则，可能会导致其中一个物品出现错误。
  humanoid: "minecraft:topaz"
  humanoid-leggings: "minecraft:topaz"
  llama-body: "minecraft:topaz"
  horse-body: "minecraft:topaz"
  wolf-body: "minecraft:topaz"
  wings: "minecraft:topaz"
  
  # 可选参数
  # 装备时覆盖纹理的资源位置。这个目录指的是 assets/<命名空间>/textures/<id>。
  camera-overlay: "namespace:id"
  # 物品是否可以被发射器发射出去并装备上。
  dispensable: true
  # 当穿戴者受伤时，物品是否也会受损。
  damage-on-hurt: true
  # 物品是否可以通过右键点击装备到相应的槽位。
  swappable: true
  # >= 1.21.5
  # 通过对目标怪物按使用键，物品是否可以装备到目标身上（只要这个物品可以装备到目标身上）
  equip-on-interact: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FDrJjArxUMGqZdTcFNlbB%252Fimage.png%3Falt%3Dmedia%26token%3Db507bcfd-b23f-42d5-a610-51e45544b465\&width=768\&dpr=4\&quality=100\&sign=fe58be0c\&sv=2)

## repairable 铁砧上能被什么物品修复 <a href="#repairable" id="repairable"></a>

设置物品是否可以通过工作台或铁砧修复（默认: true）

```yaml
repairable: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FsFmbIZ3gKhZRd0i2aJ8N%252Fimage.png%3Falt%3Dmedia%26token%3D105464c8-4910-4b0e-9e68-a3f968468e99\&width=768\&dpr=4\&quality=100\&sign=f8247985\&sv=2)

## anvil-repair-item 铁砧物品修复 <a href="#anvil-repair-item" id="anvil-repair-item"></a>

设置使用铁砧修复时为物品提供多少耐久度

```yaml
anvil-repair-item:
  - target: "#topaz_tools"
    amount: 20  # 修复固定的耐久度
  - target:
      - "minecraft:iron_pickaxe"
      - "minecraft:shears"
    percent: 0.25  # 0.25 = 25%, 修复多少百分比的耐久度
```

## renameable 可重命名 <a href="#renameable" id="renameable"></a>

设置物品是否可以通过铁砧重命名（默认: true）

```yaml
renameable: false
```

## projectile 弹射物 <a href="#projectile" id="projectile"></a>

Creates a custom projectile entity based on the item. It supports `trident`, `arrow`, `snowball` and more.\
基于物品创建自定义弹射物实体。支持 `trident`、`arrow`、`snowball` 以及更多类型。

```yaml
projectile:
  item: default:topaz_trident # 要显示的物品
  translation: 0,0,0
  rotation: 1,1,1,1
  display-transform: NONE
  scale: 0.5
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FMXNMpGU2nEZuaIZZdXje%252Fimage.png%3Falt%3Dmedia%26token%3Da8d196fb-e093-4c29-a796-83ad28ca3cac\&width=768\&dpr=4\&quality=100\&sign=8efddc31\&sv=2)

建模的方式会直接影响到配置文件中的 `rotation` 参数。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F6VmwwP0bhtIijZEsXG2e%252Fimage.png%3Falt%3Dmedia%26token%3Ddf1e2bd8-d608-4c19-9cf5-dcd2cc534505\&width=300\&dpr=4\&quality=100\&sign=9fbf83c3\&sv=2)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FL7y7eP6xIqwRXrLKlqcb%252Fimage.png%3Falt%3Dmedia%26token%3Ddf7f1d90-dffd-4db4-b3e9-c86195564187\&width=300\&dpr=4\&quality=100\&sign=ea21caea\&sv=2)\
无论你使用哪种建模方式，都必须将三叉戟的尖端部分调整为上图所示的位置，确保投射时击中目标的位置是正确的。

## dyeable 可染色 <a href="#dyeable" id="dyeable"></a>

设置物品（[皮革盔甲](https://zh.minecraft.wiki/w/%E7%9B%94%E7%94%B2#%E6%9F%93%E8%89%B2)或[狼铠](https://zh.minecraft.wiki/w/%E7%8B%BC%E9%93%A0)）是否可以在工作台上染色。（默认: true）

```yaml
dyeable: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FKPAQnbm7LyeQtQ6UHHyp%252Fimage.png%3Falt%3Dmedia%26token%3Dbbe9e687-6486-451f-8762-32849b4c0e34\&width=768\&dpr=4\&quality=100\&sign=af44b58\&sv=2)

## food 食物 <a href="#food" id="food"></a>

```yaml
food:
  nutrition: 5  # 0~20, 整数
  saturation: 3.5  # 0~10, 浮点数（小数）
```

Better to use `food` components on a 1.20.5+ server\
在 1.20.5+ 的服务器上最好使用 `food` 组件

## consume-replacement 消耗替换 <a href="#consume-replacement" id="consume-replacement"></a>

在消耗物品后设置返回的物品。例如，玩家喝完水瓶后，会返回空的玻璃瓶。（默认: null）

```yaml
consume-replacement: minecraft:apple
```

## craft-remaining-item 合成时剩余物品 <a href="#craft-remaining-item" id="craft-remaining-item"></a>

设置是否在完成合成后让物品返回其他物品。此选项仅适用于最大堆叠大小为 1 的自定义物品。

```yaml
craft-remaining-item: bucket
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FG5Gx2xMlH4SspQC1P66y%252Fimage.png%3Falt%3Dmedia%26token%3D5a6e6d26-8730-4f07-ae94-dabb0fc3b520\&width=768\&dpr=4\&quality=100\&sign=707a666e\&sv=2)

## invulnerable 不可摧毁 <a href="#invulnerable" id="invulnerable"></a>

```yaml
invulnerable:
  - lava
  - fire_tick
  - block_explosion  # 重生锚
  - entity_explosion  # 苦力怕, TNT
  - lightning
  - contact  # 仙人掌
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FHYC5C0eMeqoVtNWk2QbI%252Fimage.png%3Falt%3Dmedia%26token%3D15fdae30-932b-4ab3-9a00-a81102e5dccf\&width=768\&dpr=4\&quality=100\&sign=9de3289e\&sv=2)

## enchantable 在附魔台上的附魔能力 <a href="#enchantable" id="enchantable"></a>

这个选项可以禁止某些物品在附魔台上使用。注意：设置为 `true` 并不会使不可附魔的物品变得可以附魔。（默认: true）

```yaml
enchantable: false
```

## compost-probability 堆肥概率 <a href="#compost-probability" id="compost-probability"></a>

控制堆肥成功的可能性（默认值: 0.5）

```yaml
compost-probability: 0.5
```
