# 🧱 Block Item

A block item is an item that is bound to a block. You can configure its corresponding block ID here, or even the entire block configuration (but please note that doing so will result in the time taken to load the block being recorded under the item loading process). When you bind this behavior to an item, you can place it by right-clicking.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F0g6l5DAJuu3yiN1h9X0I%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b35f2adb\&sv=2)

Please note, where a block can be placed is determined by its [🕹️ Block Behaviors](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors). For example, the sapling in the image can only be placed on blocks with the `dirt` or `farmland` tags because its block behavior is that of a `sapling block`.

Copy

```
items:
  default:palm_sapling:
    material: paper
    behavior:
      type: block_item
      block: default:palm_sapling
```

This is the simplest way to configure a block-item, but it assumes that you have already configured a block. If you are unsure how to configure a block, please refer to [🧱 Blocks](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks).

If you find it too cumbersome to configure them separately, you can choose to configure them together. Below is an example. The format under `block` follows the standard block configuration format.

Copy

```
items:
  default:palm_sapling:
    material: paper
    custom-model-data: 1005
    settings:
      fuel-time: 100
    data:
      item-name: "<!i><i18n:item.palm_sapling>"
    model:
      template: "default:model/generated"
      arguments:
        model: "minecraft:item/custom/palm_sapling"
        texture: "minecraft:block/custom/palm_sapling"
    behavior:
      type: block_item
      block:
        settings:
          template: "default:settings/sapling"
          overrides:
            item: default:palm_sapling
        behavior:
          type: sapling_block
          feature: craftengine:palm_tree
          bone-meal-success-chance: 0.45
          tags:
            - minecraft:dirt
            - minecraft:farmland
            - minecraft:sand
        loot:
          template: "default:loot_table/basic"
          arguments:
            item: default:palm_sapling
        states:
          properties:
            stage:
              type: int
              default-value: 0
              range: 0~1
          appearances:
            default:
              state: oak_sapling:0
              model:
                path: "minecraft:block/custom/palm_sapling"
                generation:
                  parent: "minecraft:block/cross"
                  textures:
                    "cross": "minecraft:block/custom/palm_sapling"
          variants:
            stage=0:
              appearance: "default"
              id: 0
            stage=1:
              appearance: "default"
              id: 1
```
