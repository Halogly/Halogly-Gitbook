# 🚟 Hanging Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FJeuDs9y5sL36WOa0fB4x%252Fimage.png%3Falt%3Dmedia%26token%3D049ac4d9-aee7-4605-b6f1-5debd761f33c\&width=768\&dpr=4\&quality=100\&sign=eb143fad\&sv=2)

[🚟 Hanging Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/hanging-block) is a type of block that must be attached beneath another block. If the block above it is destroyed, the hanging block itself will also break.

Copy

```
blocks:
  default:stalactites:
    behavior:
      type: hanging_block
      stackable: false
      blacklist: false # use blacklist mode
      above-block-tags: []
      above-blocks: []
      delay: 0
```
