# 🌴 Sapling Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F2qxcorsLzCM5Vs1MyzC8%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=58b8017a\&sv=2)![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FTHfxu33nMbDazLNxRNnE%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b134eb36\&sv=2)

Once a `configured feature` is specified, the [🌴 Sapling Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/sapling-block) can grow into the designated tree configuration during a random tick event.

Copy

```
blocks:
  default:palm_sapling:
    behavior:
      type: sapling_block
      # This requires you to register a custom tree configuration with data pack
      # To prevent errors, we use tree feature from vanilla here
      feature: minecraft:fancy_oak
      bone-meal-success-chance: 0.45
      grow-speed: 0.7  # (0-1)
```

Please note that all sapling blocks must have a property named `stage` of type `int`. If you are unsure how to set up properties, please refer to [🔣 Block States](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states). The more `stage` values a sapling has, the longer its required growth time. In the vanilla game, saplings only have two stages: 0 and 1.
