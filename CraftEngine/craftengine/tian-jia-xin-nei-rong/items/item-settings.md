---
description: >-
  Unlike data, the contents within settings pertain to special mechanisms
  processed by the plugin.
---

# ⚙️ Item Settings

### fuel-time <a href="#fuel-time" id="fuel-time"></a>

Determines how many ticks can be burned

Copy

```
fuel-time: 100
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FETo97tqrp6GsxMMc4zOX%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=624f167b\&sv=2)

### tags <a href="#tags" id="tags"></a>

See [📖 Recipes](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/recipes)

Copy

```
tags:
  - "default:palm_logs"
  - "minecraft:logs"
  - "minecraft:logs_that_burn"
```

### equippable (1.21.2+) <a href="#equippable-1.21.2" id="equippable-1.21.2"></a>

Please note that the `equippable` in [🔢 Item Data](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data) and the `equippable` in [⚙️ Item Settings](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-settings) are not the same. The `equippable` in `settings` automatically generates the relevant JSON files for the user and have a wide version support, whereas the `equippable` within `data` requires the user to manually create the JSON files in the resource pack and is only supported in version 1.21.2 and above.

Methods of creating custom armor using leather combined with shaders will never be supported. Utilizing core shaders often results in poorer compatibility with client shaders. Moreover, this approach is not considered stable or reliable by the developers of Minecraft, and we should strive to avoid the excessive use of core shaders.

Copy

```
equippable:
  # Required Arguments
  # The slot to put the item on
  slot: head # HEAD / CHEST / LEGS / FEET / BODY / MAIN_HAND / OFF_HAND / SADDLE
  
  # The directory this refers to is assets/<namespace>/equipment/<id>.json
  asset-id: topaz
  # In practice, you only need to select the entries you wish to use
  # from the options below and configure them accordingly. Please be 
  # aware that when multiple items share the same asset-id, you must 
  # ensure that their texture paths are consistent; otherwise, it may
  # result in errors for one of the items.
  humanoid: "minecraft:topaz"
  humanoid-leggings: "minecraft:topaz"
  llama-body: "minecraft:topaz"
  horse-body: "minecraft:topaz"
  wolf-body: "minecraft:topaz"
  wings: "minecraft:topaz"
  
  # Optional Arguments
  # The resource location of the overlay texture to use when equipped. The directory this refers to is assets/<namespace>/textures/<id>.
  camera-overlay: "namespace:id"
  # Whether the item can be dispensed by using a dispenser.
  dispensable: true
  # Whether this item is damaged when the wearing entity is damaged.
  damage-on-hurt: true
  # Whether the item can be equipped into the relevant slot by right-clicking.
  swappable: true
  # >= 1.21.5
  # Whether this item can be equipped onto a target mob by pressing use on it (as long as this item can be equipped on the target at all)
  equip-on-interact: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FDrJjArxUMGqZdTcFNlbB%252Fimage.png%3Falt%3Dmedia%26token%3Db507bcfd-b23f-42d5-a610-51e45544b465\&width=768\&dpr=4\&quality=100\&sign=fe58be0c\&sv=2)

### repairable <a href="#repairable" id="repairable"></a>

Decides if the item can be repaired through crafting table/anvil (Default: true)

Copy

```
repairable: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FsFmbIZ3gKhZRd0i2aJ8N%252Fimage.png%3Falt%3Dmedia%26token%3D105464c8-4910-4b0e-9e68-a3f968468e99\&width=768\&dpr=4\&quality=100\&sign=f8247985\&sv=2)

### anvil-repair-item <a href="#anvil-repair-item" id="anvil-repair-item"></a>

Determines how much durability a given item provides when repairing

Copy

```
anvil-repair-item:
  - target: "#topaz_tools"
    amount: 20  # restores fixed durability
  - target:
      - "minecraft:iron_pickaxe"
      - "minecraft:shears"
    percent: 0.25  # 0.25 = 25%, restores n% total durability
```

### renameable <a href="#renameable" id="renameable"></a>

Determines if the item can be renamed in anvil. (Default: true)

Copy

```
renameable: false
```

### projectile <a href="#projectile" id="projectile"></a>

Creates a custom projectile entity based on the item. It supports `trident`, `arrow`, `snowball` and more.

Copy

```
projectile:
  item: default:topaz_trident # the item to display
  translation: 0,0,0
  rotation: 1,1,1,1
  display-transform: NONE
  scale: 0.5
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FMXNMpGU2nEZuaIZZdXje%252Fimage.png%3Falt%3Dmedia%26token%3Da8d196fb-e093-4c29-a796-83ad28ca3cac\&width=768\&dpr=4\&quality=100\&sign=8efddc31\&sv=2)

The way you model directly affects the `rotation` arguments in the configuration file.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F6VmwwP0bhtIijZEsXG2e%252Fimage.png%3Falt%3Dmedia%26token%3Ddf1e2bd8-d608-4c19-9cf5-dcd2cc534505\&width=300\&dpr=4\&quality=100\&sign=9fbf83c3\&sv=2)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FL7y7eP6xIqwRXrLKlqcb%252Fimage.png%3Falt%3Dmedia%26token%3Ddf7f1d90-dffd-4db4-b3e9-c86195564187\&width=300\&dpr=4\&quality=100\&sign=ea21caea\&sv=2) No matter which modeling method you use, the most important thing is to make the sharp part of the trident in the position shown in the picture above to ensure the best hitting point.

### dyeable <a href="#dyeable" id="dyeable"></a>

Decides if the item([leather armor](https://minecraft.wiki/w/Leather_armor) or [wolf armor](https://minecraft.wiki/w/Wolf_armor)) can be dyed in crafting tables. (Default: true)

Copy

```
dyeable: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FKPAQnbm7LyeQtQ6UHHyp%252Fimage.png%3Falt%3Dmedia%26token%3Dbbe9e687-6486-451f-8762-32849b4c0e34\&width=768\&dpr=4\&quality=100\&sign=af44b58\&sv=2)

### food <a href="#food" id="food"></a>

Copy

```
food:
  nutrition: 5  # 0~20, integer
  saturation: 3.5  # 0~10, float
```

Better to use `food` components on a 1.20.5+ server

### consume-replacement <a href="#consume-replacement" id="consume-replacement"></a>

Set the return item after consuming the item. For example, after the player drinks the water bottle, the empty bottle will be returned. (Default: null)

Copy

```
consume-replacement: minecraft:apple
```

### craft-remaining-item <a href="#craft-remaining-item" id="craft-remaining-item"></a>

Choose whether items should return other items when the crafting recipe is finished. This option only works for custom items with a max stack size of 1

Copy

```
craft-remaining-item: bucket
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FG5Gx2xMlH4SspQC1P66y%252Fimage.png%3Falt%3Dmedia%26token%3D5a6e6d26-8730-4f07-ae94-dabb0fc3b520\&width=768\&dpr=4\&quality=100\&sign=707a666e\&sv=2)

### invulnerable <a href="#invulnerable" id="invulnerable"></a>

Copy

```
invulnerable:
  - lava
  - fire_tick
  - block_explosion  # respawn anchor
  - entity_explosion  # creeper, tnt
  - lightning
  - contact  # cactus
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FHYC5C0eMeqoVtNWk2QbI%252Fimage.png%3Falt%3Dmedia%26token%3D15fdae30-932b-4ab3-9a00-a81102e5dccf\&width=768\&dpr=4\&quality=100\&sign=9de3289e\&sv=2)

### enchantable <a href="#enchantable" id="enchantable"></a>

This option lets you block certain items from being used on the enchantment table. Tip: setting it to `true` won’t magically make unenchantable items enchantable. (Default: true)

Copy

```
enchantable: false
```

### compost-probability <a href="#compost-probability" id="compost-probability"></a>

This setting controls how likely it is for composting to succeed (Default: 0.5)

Copy

```
compost-probability: 0.5
```
