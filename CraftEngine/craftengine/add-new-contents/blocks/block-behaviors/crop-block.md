# 🌽 Crop Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FhmVLWF8LYSK3x2zJDRy2%252Fimage.png%3Falt%3Dmedia%26token%3D8dc7854c-a1f7-49d4-a713-6f6ef31a2069\&width=768\&dpr=4\&quality=100\&sign=cc14e879\&sv=2)

[🌽 Crop Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/crop-block) is a type of block that grows over time. When receiving random ticks, it has a chance to advance to the next growth stage. However, if the plant lacks sufficient light, it will either stop growing or drop as an item.

You **must** configure the `age` property for this block, as it determines its stages. If you are unsure how to set up properties, please refer to [🔣 Block States](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states).

Copy

```
blocks:
  default:ender_pearl_flower:
    behavior:
      type: crop_block
      grow-speed: 0.25  # 0~1, the chance of growing on random tick
      light-requirement: 9  # light requirement for this crop
      is-bone-meal-target: true # default true
      bone-meal-age-bonus:
        type: uniform
        min: 1
        max: 3
```
