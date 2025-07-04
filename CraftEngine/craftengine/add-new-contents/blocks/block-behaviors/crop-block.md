# 🌽 作物方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FhmVLWF8LYSK3x2zJDRy2%252Fimage.png%3Falt%3Dmedia%26token%3D8dc7854c-a1f7-49d4-a713-6f6ef31a2069\&width=768\&dpr=4\&quality=100\&sign=cc14e879\&sv=2)

[🌽 作物方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/crop-block)是一种随时间生长的方块。当接收到随机刻时，它有几率进入下一生长阶段。但如果植物光照不足，它将停止生长或掉落为物品。

**必须**为此类方块配置 `age` 属性，因为它决定此类方块的生长速度。如果你不确定如何设置属性，请参阅[🔣 方块状态](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states)。

```yaml
blocks:
  default:ender_pearl_flower:
    behavior:
      type: crop_block
      grow-speed: 0.25  # 0~1，随机刻生长的几率
      light-requirement: 9  # 作物的光照需求
      is-bone-meal-target: true # 默认为 true
      bone-meal-age-bonus:
        type: uniform
        min: 1
        max: 3
```
