---
description: https://zh.minecraft.wiki/w/物品模型映射#composite
---

# 🧩 组合

> 在同一命名空间中渲染多个子模型。

```yaml
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
