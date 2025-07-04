# 🎍 垂直作物方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FQThsCr8DWL9MnDStY5c4%252Fimage.png%3Falt%3Dmedia%26token%3D0540cc32-fcf8-4a26-9e67-a5d9d81f27d7\&width=768\&dpr=4\&quality=100\&sign=f137ae4e\&sv=2)

[🎍 垂直作物方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/vertical-crop-block)是一种随时间向上或向下生长的方块。

**必须**为此类方块配置 `age` 属性，因为它决定此类方块的生长速度。如果你不确定如何设置属性，请参阅[🔣 方块状态](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states)。甘蔗的 `age` 值越高，其所需的生长时间就越长。

```yaml
blocks:
  default:flame_cane:
    behaviors:
      - type: vertical_crop_block
        max-height: 4
        grow-speed: 0.333
        direction: down  # up/down
      - type: hanging_block
        stackable: true
        delay: 1
```

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F3vRZWSB3S8jeOEsAx8py%252Fimage.png%3Falt%3Dmedia%26token%3Dbb58619f-606e-41fd-ab69-0763d2fa669d\&width=768\&dpr=4\&quality=100\&sign=302dd003\&sv=2)
