---
description: 本页面主要讲解如何向服务器添加新方块。
---

# 🕹️ 方块行为

CraftEngine implements a comprehensive physical property system, allowing you to freely combine multiple block behaviors! Here are two simple examples: one demonstrating a single block behavior and another showing a combination of multiple block behaviors.

Copy

```
# single behavior
blocks:
  default:fairy_flower:
    behavior:
      type: bush_block
      bottom-block-tags:
        - minecraft:dirt
        - minecraft:farmland
```

Copy

```
# combined behaviors
blocks:
  default:gunpowder_block:
    behaviors:
      - type: concrete_powder_block
        solid-block: default:solid_gunpowder_block
      - type: falling_block
```

Please note: combining some block behaviors may cause unexpected conflicts. If you run into problems, please contact support and we will try to resolve any conflicts.
