---
description: >-
  This page mainly explains how to add new blocks to your server.
  本页面主要解释如何向您的服务器添加新方块。
---

# 🧱 方块

### Sections to Configure  配置部分 <a href="#sections-to-configure" id="sections-to-configure"></a>

A complete block configuration contains the following sections:\
一个完整的方块配置包含以下部分：

* behavior  行为

[🕹️ Block Behaviors  🕹️ 方块行为](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors)

* settings  设置

[⚙️ Block Settings  ⚙️ 阻塞设置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-settings)

* states  状态

[🔣 Block States  🔣 块状态](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states)

* loot  战利品

[💎 Loot Table  💎 资源表](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/loot-table)

* events  事件

[🪇 Events  🪇 事件](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/events)

### How to Bind Items  如何绑定物品 <a href="#how-to-bind-items" id="how-to-bind-items"></a>

[🧱 Block Item   🧱 块物品](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-behaviors/block-item)

### Full Config Overview  完整配置概览 <a href="#full-config-overview" id="full-config-overview"></a>

This is a simplified version using the template system, including the sections that need to be configured.\
这是一个使用模板系统的简化版本，包括需要配置的部分。

Copy  复制

```
blocks:
  default:palm_log:
    behavior:
      type: strippable_block
      stripped: default:stripped_palm_log
    loot:
      template: loot_table:normal
      arguments:
        item: default:palm_log
    settings:
      template: block_settings:log
      overrides:
        item: default:palm_log
    states:
      template: "default:block_state/pillar"
      arguments:
        base_block: note_block
        texture_top_path: minecraft:block/custom/palm_log_top
        texture_side_path: minecraft:block/custom/palm_log
        model_vertical_path: minecraft:block/custom/palm_log
        model_horizontal_path: minecraft:block/custom/palm_log_horizontal
        vanilla_id:
          type: self_increase_int
          from: 0
          to: 2
        internal_id:
          type: self_increase_int
          from: 0
          to: 2
```

If you haven't learned how to use the template system yet, be sure to learn it now [📄 Templates \[MUST READ\]](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/templates-must-read)\
如果你还没有学习如何使用模板系统，一定要现在就学习它 📄 模板 \[必读]

What happens if you don't use a template? Then the configuration file for this block will look like this:\
如果你不使用模板会怎样？那么这个模块的配置文件将看起来像这样：

Copy  复制

```
blocks:
  default:palm_log:
    behavior:
      type: strippable_block
      stripped: default:stripped_palm_log
    loot:
      pools:
        - rolls: 1
          conditions:
            - type: survives_explosion
          entries:
            - type: item
              item: "default:palm_log"
    settings:
      hardness: 2.0
      resistance: 2.0
      push-reaction: NORMAL
      replaceable: false
      burnable: true
      burn-chance: 5
      fire-spread-chance: 5
      is-redstone-conductor: true
      is-suffocating: true
      instrument: BASS
      can-occlude: true
      item: default:palm_log
      tags:
        - minecraft:mineable/axe
        - minecraft:logs_that_burn
        - minecraft:logs
        - minecraft:completes_find_tree_tutorial
      sounds:
        break: minecraft:block.wood.break
        step: minecraft:block.wood.step
        place: minecraft:block.wood.place
        hit: minecraft:block.wood.hit
        fall: minecraft:block.wood.fall
    states:
      properties:
        axis:
          type: axis
          default: y
      appearances:
        axisY:
          state: "note_block:0"
          model:
            path: "minecraft:block/custom/stripped_palm_log"
            generation:
              parent: "minecraft:block/cube_column"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisX:
          state: "note_block:1"
          model:
            x: 90
            y: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisZ:
          state: "note_block:2"
          model:
            x: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
      variants:
        axis=x:
          appearance: axisX
          id: 0
        axis=y:
          appearance: axisY
          id: 1
        axis=z:
          appearance: axisZ
          id: 2
```
