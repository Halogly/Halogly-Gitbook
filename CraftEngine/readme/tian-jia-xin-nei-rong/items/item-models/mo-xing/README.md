---
description: https://minecraft.wiki/w/Items_model_definition#model
---

# 📐 模型

The model consists of two parts: path and tints. Tints are optional. You can view all available tint types in the link below.\
该模型由两部分组成：路径和色调。色调是可选的。您可以在以下链接中查看所有可用的色调类型。

[🎨 Tint  🎨 色调](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-models/model/tint)

In this configuration, we create a model for custom leaves. However, the default leaves in the vanilla game do not have color, so we need to configure a tint to color them.\
在这个配置中，我们为自定义树叶创建了一个模型。然而，原版游戏中的默认树叶没有颜色，因此我们需要配置一个色调来为它们上色。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FrlM7FKXsEbSji4SFQsn2%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=1bca6382\&sv=2)Copy  复制

```
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
