---
description: >-
  Set vanilla NBT/Components for items to utilize certain native Minecraft
  functionalities.
---

# 🔢 Item Data

### What is Item Data? <a href="#what-is-item-data" id="what-is-item-data"></a>

Item Data refers to the NBT (Named Binary Tag) of an item in older versions, or the item Components in version 1.20.5 and above. Through this data, we can customize various aspects of an item such as its name, description, attributes, and other functionalities.

### External Data <a href="#external-data" id="external-data"></a>

If you want a CraftEngine item to retain the data of an external plugin's item, follow this configuration:

Copy

```
items:
  default:example_item:
    data:
      external:
        plugin: NeigeItems
        id: example_item
```

[🐌 External Item Providers](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/external-item-providers)

### Hard-coded Data <a href="#hard-coded-data" id="hard-coded-data"></a>

Hardcoded data, in this context, means that the configuration formats are provided and maintained by plugin, which ensures compatibility across different versions. These formats are defined by the plugin, so they may differ from the standard NBT (Named Binary Tag) or Components formats used by the game itself. The advantage of this approach is that the plugin handles all the maintenance, including version compatibility, so users do not need to worry about changes or updates between game versions.

Copy

```
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>Topaz Rod"
```

#### item-name <a href="#item-name" id="item-name"></a>

Determines the default name of this item, unlike the `custom-name`, this name can't be erased using an anvil, won't be italicized, and does not show in some labels, such as banner markers and item frames.

Copy

```
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>Topaz Rod" # we use <!i> here because 1.20.4 and below
                                          # don't have item_name component
```

#### custom-name <a href="#custom-name" id="custom-name"></a>

Used to specify the item's custom name, like you can in an anvil.

Copy

```
items:
  default:topaz_rod:
    data:
      custom-name: "<!i><#FF8C00>Topaz Rod"
```

#### lore <a href="#lore" id="lore"></a>

Determines the displayed description of the item.

Copy

```
items:
  default:topaz_rod:
    data:
      lore: 
        - "What a shiny rod!"
```

#### unbreakable <a href="#unbreakable" id="unbreakable"></a>

Determines whether the item is unbreakable

Copy

```
items:
  default:topaz_rod:
    data:
      unbreakable: true
```

#### enchantment <a href="#enchantment" id="enchantment"></a>

Determines the enchantments of the item

Copy

```
items:
  default:topaz_rod:
    data:
      enchantment:
        minecraft:sharpness: 1
        custom:enchant: 3
```

#### dyed-color <a href="#dyed-color" id="dyed-color"></a>

Determines the color of the item

Copy

```
items:
  default:sofa:
    data:
      dyed-color: 255,255,255
```

#### custom-model-data <a href="#custom-model-data" id="custom-model-data"></a>

Copy

```
items:
  default:sofa:
    data:
      custom-model-data: 100
```

#### food (1.20.5+) <a href="#food-1.20.5" id="food-1.20.5"></a>

Copy

```
items:
  default:magic_apple:
    material: apple
    data:
      food: 
        nutrition: 5
        saturation: 3.5
        can-always-eat: false
```

#### jukebox-playable (1.21+) <a href="#jukebox-playable-1.21" id="jukebox-playable-1.21"></a>

Copy

```
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```

#### item-model (1.21.2+) <a href="#item-model-1.21.2" id="item-model-1.21.2"></a>

Copy

```
items:
  default:music_stick:
    data:
      item-model: default:music_stick
```

#### tooltip-style (1.21.2+) <a href="#tooltip-style-1.21.2" id="tooltip-style-1.21.2"></a>

Determines the tooltip style of the item

Copy

```
items:
  default:topaz_rod:
    data:
      tooltip-style: minecraft:topaz #namespace:tooltip_style_id
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FG5cqs5c033VOfKiw2TJu%252Fimage.png%3Falt%3Dmedia%26token%3D4c517089-ab55-4fc8-adfe-c26bb7176e91\&width=768\&dpr=4\&quality=100\&sign=81334337\&sv=2)

To create a tooltip style, you must place the texture in the directory as follows.

[https://minecraft.wiki/w/Data\_component\_format/tooltip\_style](https://minecraft.wiki/w/Data_component_format/tooltip_style)

#### trim <a href="#trim" id="trim"></a>

apply a decorative alteration to a [tool](https://minecraft.wiki/w/Tool) or [armor](https://minecraft.wiki/w/Armor)

Copy

```
trim:
  pattern: eye # https://minecraft.wiki/w/Smithing#Trimming
  material: iron # https://minecraft.wiki/w/Smithing#Material
```

#### equippable (1.21.2+) <a href="#equippable-1.21.2" id="equippable-1.21.2"></a>

If present, this item can be equipped in the specified slot.

Copy

```
equippable:
  # The slot to put the item on
  slot: head # HEAD / CHEST / LEGS / FEET / BODY / MAIN_HAND / OFF_HAND / SADDLE
  
  # Optional Arguments
  # The directory this refers to is assets/<namespace>/equipment/<id>.json
  asset-id: minecraft:topaz
  # The resource location of the overlay texture to use when equipped. The directory this refers to is assets/<namespace>/textures/<id>.
  camera-overlay: namespace:id
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

### Customizable Data <a href="#customizable-data" id="customizable-data"></a>

Customizable Data is not maintained by plugins, and its format can change with updates to Minecraft, particularly with the frequent recent changes to Components. If you want to avoid extensive configuration overhauls due to version updates, you might consider using templates to establish a standardized configuration file format. When a new version is released, you can simply update the template to accommodate any changes. If you are unfamiliar with how to use templates, please make sure to read the guide provided at [📄 Templates \[MUST READ\]](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/templates-must-read). This approach can help streamline the update process and reduce the effort required to keep your configurations compatible with the latest game versions.

#### NBT (1.20-1.20.4) <a href="#nbt-1.20-1.20.4" id="nbt-1.20-1.20.4"></a>

Since NBT (Named Binary Tag) has become outdated, it will not be discussed in detail here.

[https://minecraft.wiki/w/Item\_format/Before\_1.20.5](https://minecraft.wiki/w/Item_format/Before_1.20.5)

Copy

```
items:
  default:topaz_rod:
    data:
      nbt:
        CustomModelData: 1000
```

#### Components (1.20.5+) <a href="#components-1.20.5" id="components-1.20.5"></a>

The format for custom Components strictly adheres to the [Minecraft Wiki](https://minecraft.wiki/w/Data_component_format) guidelines. Below, I will guide you through a few examples to help you become familiar with how to configure custom Components.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FNrlWy1Cxy4vn2GK1ODdL%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=21ad2949\&sv=2)

From the image, we can see that `max_damage` accepts an `I` (which stands for an integer type parameter). Therefore, in our configuration, we simply need to use a numerical value directly.

Copy

```
items:
  guide:test:
    data:
      components:
        minecraft:max_damage: 128
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F7cqvxKcjpE2LTlsbTj9K%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=cfd2fc97\&sv=2)

From the image, we can see that `food` requires three parameters: `nutrition` of type `int`, `saturation` of type `float`, and `can_always_eat` of type `boolean`.

Copy

```
items:
  guide:test:
    data:
      components:
        minecraft:food:
          nutrition: 4
          saturation: 2.0
          can_always_eat: false
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FB6jF06WTXXXnonNs0kqo%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=37ba2404\&sv=2)

Now, let's try working with a compound tag. The `{}` signifies that you need to open a new section in your YAML configuration.

Copy

```
items:
  guide:test:
    data:
      components:
        minecraft:enchantments:
          levels:
            minecraft:sharpness: 1
          show_in_tooltip: false
```

However, upon closer inspection of the wiki, you'll notice that this method becomes obsolete in version 1.21.5. When 1.21.5 is released, you will need to update your configuration file as follows:

Copy

```
items:
  guide:test:
    data:
      components:
        minecraft:enchantments:
          minecraft:sharpness: 1
```

You can also configure the components in json format

Copy

```
minecraft:custom_data: "(json) {\"test\":1}"
```

#### Remove Components (1.20.5+) <a href="#remove-components-1.20.5" id="remove-components-1.20.5"></a>

Removes the component from the item

Copy

```
items:
  test:item:
    data:
      remove-components:
        - minecraft:equippable
```
