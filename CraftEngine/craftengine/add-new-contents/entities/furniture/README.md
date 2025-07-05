---
description: 本页面主要讲解如何在服务器中添加新家具。
---

# 🪑 家具

请注意，重新加载插件不会影响已放置的家具！你需要重启服务器或重新加载区块才能将新配置应用到现有的家具。插件利用缓存来提高家具的性能。在没有深思熟虑的情况下强制重新加载服务器上已加载的家具可能会对服务器的稳定性产生重大影响。

未来，插件可能会考虑加入关于强制重载的危险提示，当然，目前没有。

## 配置 <a href="#sections-to-configure" id="sections-to-configure"></a>

一个完整的家具配置包含以下部分：

* 行为

[🕹️ 家具行为](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture/furniture-behaviors)

* settings

[⚙️ 家具设置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture/furniture-settings)

* placement

[📍 家具放置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture/furniture-placement)

* 战利品

[💎 战利品表](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/loot-table)

* 事件

[🪇 事件](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/events)

## 如何绑定物品 <a href="#how-to-bind-items" id="how-to-bind-items"></a>

[🪑 家具物品](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-behaviors/furniture-item)

## 完整配置概览 <a href="#full-config-overview" id="full-config-overview"></a>

```yaml
furniture:
  default:bench:
    settings:
      item: default:bench
      sounds:
        break: minecraft:block.bamboo_wood.break
        place: minecraft:block.bamboo_wood.place
    placement:
      ground:
        rules:
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
        elements:
          - item: default:bench
            display-transform: NONE
            billboard: FIXED
            position: 0.5,0,0
            translation: 0,0.5,0
        hitboxes:
          - position: 0,0,0
            width: 1
            height: 1
            interactive: true
            seats:
              - 0,0,-0.1 0
          - position: 1,0,0
            width: 1
            height: 1
            interactive: true
            seats:
              - 1,0,-0.1 0
    loot:
      template: loot_table:normal
      arguments:
        item: default:bench
```
