---
description: >-
  This page mainly explains how to configure loot for vanilla stuff
  本页主要解释如何为原版内容配置掉落物
---

# 原版掉落品

### Introduction 介绍 <a href="#introduction" id="introduction"></a>

Minecraft's native loot system is already quite robust, but it has one notable shortfall: it cannot incorporate certain plugin-specific elements such as placeholder checks, permissions, and other advanced functionalities. Additionally, configuring vanilla data packs is a cumbersome process, making the overriding of default loot tables particularly challenging. To address this, the plugin offers an override feature for the vanilla loot system. You can refer to the following example to get started quickly. In the text below, the "..." represents loot configurations. It is advisable to first read [💎 Loot Table](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/loot-table) to understand how to configure loot effectively.\
Minecraft 的原生掉落系统已经相当完善，但它有一个明显的不足：无法整合某些插件特定的元素，如占位符检查、权限和其他高级功能。此外，配置原版数据包是一个繁琐的过程，使得覆盖默认掉落表变得特别困难。为此，该插件提供了原版掉落系统的覆盖功能。您可以参考以下示例快速上手。在下面的文本中，"..." 代表掉落物配置。建议您先阅读 💎 掉落表，以了解如何有效配置掉落物。

### Block Loots 区块掉落物 <a href="#block-loots" id="block-loots"></a>

Copy 复制

```
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target: "minecraft:grass"
    # Whether to overwrite the vanilla loots
    override: false
    loot:
      ...
```

Copy 复制

```
vanilla-loots:
  minecraft:grass_loot:
    type: block
    target:
      - minecraft:wheat[age=0] # use a detailed state
      - minecraft:wheat[age=1]
    override: false
    loot:
      ...
```

### Entity Loots 实体掉落物 <a href="#entity-loots" id="entity-loots"></a>

Copy 复制

```
vanilla-loots:
  minecraft:sheep_loot:
    type: entity
    target: "minecraft:sheep"
    # Whether to overwrite the vanilla loots
    override: false
    loot:
      ...
```
