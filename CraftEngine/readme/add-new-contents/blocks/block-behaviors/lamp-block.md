# 💡 Lamp Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FUIoDMeUnwqBcif3P0eed%252Fimage.png%3Falt%3Dmedia%26token%3De1c32789-458f-489d-be5c-dbe3b911e69e\&width=768\&dpr=4\&quality=100\&sign=e10c177b\&sv=2)

[💡 Lamp Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/lamp-block) allows the block to turn into `lit` state on redstone powered.

Copy

```
blocks:
  default:copper_coil:
    behaviors:
      - type: lamp_block
```

Please note that all lamp blocks must have a property named `lit`of type `boolean`. If you are unsure how to set up properties, please refer to [🔣 Block States](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states).
