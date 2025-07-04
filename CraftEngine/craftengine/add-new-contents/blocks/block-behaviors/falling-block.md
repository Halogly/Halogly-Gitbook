# 🟨 下落的方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Ff68xQ1ll4vIsWoN6KTOc%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=7538787b\&sv=2)

[🟨 下落的方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/falling-block)（如沙子和铁砧）在下落时会转化为临时的下落实体。以下是下落方块的配置示例：

```yaml
blocks:
  default:falling_block_example:
    behavior:
      type: falling_block
      # 可选
      hurt-amount: -1
      # 可选
      max-hurt: -1
```

`hurt-amount` 和 `max-hurt` 是可选的，但必须一起配置。它们的作用是确定下落方块击中实体时造成的伤害。
