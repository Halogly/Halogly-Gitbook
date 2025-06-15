---
description: This page mainly explains how to add new furniture to your server.
---

# 🪑 Furniture

Please note that reloading the plugin will not affect furniture that already placed! You will need to restart the server or reload the chunks to apply new configurations to existing furniture. The plugin utilizes caching to enhance the performance of the furniture. Forcibly reloading furniture that is already loaded on the server without caution could have a significant impact on the server's stability. In the future, the plugin may consider introducing related unsafe flags for forced reloading, but certainly not at this moment.

### Sections to Configure <a href="#sections-to-configure" id="sections-to-configure"></a>

A complete furniture configuration contains the following sections:

* behavior

[🕹️ Furniture Behaviors](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture/furniture-behaviors)

* settings

[⚙️ Furniture Settings](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture/furniture-settings)

* placement

[📍 Furniture Placement](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture/furniture-placement)

* loot

[💎 Loot Table](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/loot-table)

* events

[🪇 Events](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/events)

### How to Bind Items <a href="#how-to-bind-items" id="how-to-bind-items"></a>

[🪑 Furniture Item](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-behaviors/furniture-item)

### Full Config Overview <a href="#full-config-overview" id="full-config-overview"></a>

Copy

```
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
