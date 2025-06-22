---
description: https://zh.minecraft.wiki/w/物品模型映射#model
---

# 📐 模型

模型由两部分组成：路径和染色。染色是可选的。你可以在下面的链接中查看所有可用的染色类型。

[🎨 染色](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/model/tint)

在这个配置中，我们为自定义树叶创建了一个模型。然而，原版游戏中的默认树叶是没有颜色的，因此我们需要配置染色来给它们上色。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FrlM7FKXsEbSji4SFQsn2%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=1bca6382\&sv=2)

```yaml
default:palm_leaves:
  model:
    type: "minecraft:model"
    path: "minecraft:item/custom/palm_leaves"
    generation:
      parent: "minecraft:block/custom/palm_leaves"
    tints:
      - type: "minecraft:constant"
        value: -12012264
```
