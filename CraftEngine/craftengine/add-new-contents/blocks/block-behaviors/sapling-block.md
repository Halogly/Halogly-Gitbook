# 🌴 树苗方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F2qxcorsLzCM5Vs1MyzC8%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=58b8017a\&sv=2)![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FTHfxu33nMbDazLNxRNnE%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b134eb36\&sv=2)

一旦指定了 `configured feature`，[🌴 树苗方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/sapling-block)就可以在随机刻事件中生长成指定配置的树。

```yaml
blocks:
  default:palm_sapling:
    behavior:
      type: sapling_block
      # 需要使用数据包注册自定义树配置
      # 为了防止出错，我们在这里使用了原版的树功能
      feature: minecraft:fancy_oak
      bone-meal-success-chance: 0.45
      grow-speed: 0.7  # (0-1)
```

请注意，所有树苗方块都必须有一个名为 `stage` 的 `int` 类型属性。如果你不确定如何设置属性，请参阅[🔣 方块状态](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states)。树苗的 `stage` 值越高，其所需的生长时间就越长。在原版中，树苗只有两个阶段：0 和 1。
