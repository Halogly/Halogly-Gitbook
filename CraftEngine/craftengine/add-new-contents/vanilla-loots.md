---
description: 本页主要讲解如何为原版内容配置掉落物
---

# 🗃️ 原版掉落物

# 介绍 <a href="#introduction" id="introduction"></a>

Minecraft的原版掉落系统已经相当完善，但它有一个明显的缺点：无法整合某些插件特定的元素，如占位符检查、权限和其他高级功能。此外，配置原版数据包是一个繁琐的过程，这会使得覆盖默认战利品表变得特别困难。为此，我们的插件提供了原版掉落系统的覆盖功能。你可以参考以下示例快速上手。在下面的文本中，“...”代表掉落物配置。建议先阅读[💎 战利品表](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/loot-table)了解如何正确配置掉落物。

# 方块掉落物 <a href="#block-loots" id="block-loots"></a>

```yaml
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target: "minecraft:grass"
    # 是否覆盖原版掉落物
    override: false
    loot:
      ...
```

```yaml
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target:
      - minecraft:wheat[age=0] # 使用详细的状态
      - minecraft:wheat[age=1]
    override: false
    loot:
      ...
```

# 实体掉落物 <a href="#entity-loots" id="entity-loots"></a>

```yaml
vanilla-loots:
  minecraft:sheep_loot:
    type: entity
    target: "minecraft:sheep"
    # 是否覆盖原版掉落物
    override: false
    loot:
      ...
```
