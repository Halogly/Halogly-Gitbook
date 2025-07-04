# 🍁 树叶方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FcOCjIhMj2mDHrpev05Zl%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=db1e9e14\&sv=2)

[🍁 树叶方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/leaves-block)拥有三个属性：`distance`（与原木的距离）、`persistent`（方块是否可以永久存在）和 `waterlogged`（方块是否含水\[可选]）。`distance` 属性会使自然生成的树叶随时间枯萎，而 `persistent` 属性确保玩家放置的树叶会永久存在。

```yaml
blocks:
  default:palm_leaves:
    behavior:
      type: leaves_block
```

请注意，所有树叶方块必须具有 `persistent`（布尔值）和 `distance`（整数）属性，`distance` 至少为1。如果不确定如何配置这些属性，请参阅[🔣 方块状态](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states)。

你可以根据需要增加或减少 `distance` 的值。对于特别大的树，为了防止树叶枯萎，可以将 `distance` 设置为 10 或更高。原版中，树叶最大的 `distance` 值为7。
