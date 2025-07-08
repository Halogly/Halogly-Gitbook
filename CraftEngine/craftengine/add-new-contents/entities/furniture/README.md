---
description: 本页面主要讲解如何向服务器添加新家具。
---

# 🪑 家具

{% hint style="danger" %}
请注意，重新加载插件不会影响已放置的家具！你需要重启服务器或重新加载区块才能将新配置应用到现有的家具。插件利用缓存来提高家具的性能。在没有深思熟虑的情况下强制重新加载服务器上已加载的家具可能会对服务器的稳定性产生重大影响。

未来，插件可能会考虑加入关于强制重载的危险提示，当然，目前没有。
{% endhint %}

## 配置 <a href="#sections-to-configure" id="sections-to-configure"></a>

一个完整的家具配置需要包含以下部分：

* 行为

{% content-ref url="furniture-behaviors.md" %}
[furniture-behaviors.md](furniture-behaviors.md)
{% endcontent-ref %}

* 设置

{% content-ref url="furniture-settings.md" %}
[furniture-settings.md](furniture-settings.md)
{% endcontent-ref %}

* 放置

{% content-ref url="furniture-placement.md" %}
[furniture-placement.md](furniture-placement.md)
{% endcontent-ref %}

* 战利品

{% content-ref url="../../loot-table.md" %}
[loot-table.md](../../loot-table.md)
{% endcontent-ref %}

* 事件

{% content-ref url="../../events.md" %}
[events.md](../../events.md)
{% endcontent-ref %}

## 如何绑定物品 <a href="#how-to-bind-items" id="how-to-bind-items"></a>

<details>

<summary><a href="../../items/item-behaviors/furniture-item.md">🪑 家具物品</a></summary>



</details>

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
