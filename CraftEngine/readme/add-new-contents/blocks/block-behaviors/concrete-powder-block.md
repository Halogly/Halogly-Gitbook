# 💦 Concrete Powder Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FTZqK3Gho57vlt2oJEPJy%252Fimage.png%3Falt%3Dmedia%26token%3D89aadbd0-381d-4b68-b315-48133832ad61\&width=768\&dpr=4\&quality=100\&sign=7b674195\&sv=2)

[💦 Concrete Powder Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/concrete-powder-block) is a type of block that hardens when it comes into contact with water. A configuration example is shown below:

Copy

```
blocks:
  default:gunpowder_block:
    behavior:
      type: concrete_powder_block
      solid-block: default:solid_gunpowder_block
```

Currently, custom blocks cannot turn into blocks upon contacting water while in a falling entity state. This is because this piece of code is hardcoded in Minecraft, and we cannot modify its behavioral logic.
