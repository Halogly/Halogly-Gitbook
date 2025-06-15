---
description: https://minecraft.wiki/w/Items_model_definition#composite
---

# 🧩 复合

> Render multiple sub-models in the same space.\
> 在同一空间中渲染多个子模型。

Copy  复制

```
default:composite_item:
  model:
    type: "minecraft:composite"
    models:
      - type: minecraft:model
        path: "minecraft:item/custom/model_1"
      - type: minecraft:model
        path: "minecraft:item/custom/model_2"
      - type: minecraft:model
        path: "minecraft:item/custom/model_3"
```
