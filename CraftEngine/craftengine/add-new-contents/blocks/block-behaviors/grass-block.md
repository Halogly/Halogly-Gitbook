# 🌿 草方块

[🌿 草方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/grass-block)是一种可以对其使用骨粉来生长草和花朵的方块。别忘了给方块添加 `minecraft:dirt` 标签，否则草无法在它们上面存活。如果你不知道如何给你的方块添加标签，请参阅[标签](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-settings#tags)。

```yaml
blocks:
  default:grass_block:
    behavior:
      type: grass_block
```
