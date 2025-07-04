# 💦 混凝土粉末方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FTZqK3Gho57vlt2oJEPJy%252Fimage.png%3Falt%3Dmedia%26token%3D89aadbd0-381d-4b68-b315-48133832ad61\&width=768\&dpr=4\&quality=100\&sign=7b674195\&sv=2)

[💦 混凝土粉末方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/concrete-powder-block)是一种接触水后会变硬的方块。以下是配置示例：

```yaml
blocks:
  default:gunpowder_block:
    behavior:
      type: concrete_powder_block
      solid-block: default:solid_gunpowder_block
```

目前，自定义方块在处于下落实体状态时无法接触水后变成方块。这是因为这段代码在 Minecraft 中是硬编码的，我们无法修改其行为逻辑。
