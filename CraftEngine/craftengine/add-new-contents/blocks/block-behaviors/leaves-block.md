# 🍁 Leaves Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FcOCjIhMj2mDHrpev05Zl%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=db1e9e14\&sv=2)

[🍁 Leaves Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/leaves-block) possess three properties: `distance` (the distance from the tree trunk), `persistent` (whether the block can exist permanently), and `waterlogged` (whether the block contains water \[optional]). The `distance` property enables naturally generated leaves to decay over time, while the `persistent` property ensures that player-placed leaves remain permanently.

Copy

```
blocks:
  default:palm_leaves:
    behavior:
      type: leaves_block
```

Please note that all leaf blocks must have the `persistent` (boolean) and `distance` (int) properties, with `distance` being at least 1. If you are unsure how to configure these properties, please refer to [🔣 Block States](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states).

You can increase or decrease the `distance` value as needed. For particularly large trees, to prevent leaf decay, you can set the `distance` to 10 or higher. In the vanilla game, the maximum `distance` for leaves is 7.
