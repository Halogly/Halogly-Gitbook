# 🟨 Falling Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Ff68xQ1ll4vIsWoN6KTOc%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=7538787b\&sv=2)

[🟨 Falling Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/falling-block) (such as sand and anvils) possess the property of transforming into temporary falling entities when triggered. The following example demonstrates how to configure a falling block:

Copy

```
blocks:
  default:falling_block_example:
    behavior:
      type: falling_block
      # Optional
      hurt-amount: -1
      # Optional
      max-hurt: -1
```

The configurations `hurt-amount` and `max-hurt` are optional, but they must be configured together. Their effect is to determine the damage inflicted on entities when struck by a falling block.
