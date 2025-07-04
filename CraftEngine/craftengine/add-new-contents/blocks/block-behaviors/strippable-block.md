# 🪓 可去皮方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FLazB9XAUsqIk7I4fPu2m%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=75dc053c\&sv=2)

[🪓 可去皮方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/strippable-block)是一种可以通过用斧右键进行去皮的方块，主要用于树桩。

```yaml
blocks:
  default:palm_log:
    behavior:
      type: strippable_block
      stripped: default:stripped_palm_log
```
