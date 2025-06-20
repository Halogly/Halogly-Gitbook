# 🧱 Block Item

方块物品是一个绑定到方块的物品。你可以在此处配置与其对应的方块 ID，甚至整个方块配置（但请注意，这样会导致加载方块的时间被记录在物品的加载过程中）。当你将此行为绑定到物品时，可以通过右键点击来放置它。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F0g6l5DAJuu3yiN1h9X0I%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b35f2adb\&sv=2)

请注意，方块放置的位置由其[🕹️ 方块行为](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors)决定。例如，图片中的小幼苗只能放置在带有 `dirt` 或 `farmland` 标签的方块上，因为它的方块行为是 `sapling block`。

```yaml
items:
  default:palm_sapling:
    material: paper
    behavior:
      type: block_item
      block: default:palm_sapling
```

这是配置方块物品最简单的方法，但前提是你已经配置了一个方块。如果你不确定如何配置方块，请参考[🧱 方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks)。


If you find it too cumbersome to configure them separately, you can choose to configure them together. Below is an example. The format under `block` follows the standard block configuration format.
如果觉得单独配置太麻烦，可以选择一起配置。下面是一个示例。`block` 下的格式遵循标准的方块配置格式。

```yaml
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
