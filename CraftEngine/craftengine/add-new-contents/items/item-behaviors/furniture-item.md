# 家具物品

家具物品是与一件家具绑定的物品。你可以在此处配置与其对应的家具 ID，甚至整个家具配置（但请注意，这样会导致加载家具的时间会被记录在物品的加载过程中）。当你将此行为绑定到物品时，可以通过右键点击来放置它。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSYOQXH6ZY0VcGYGZLdgN%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=d039abea\&sv=2)

```yaml
items:
  default:bench:
    behavior:
      type: furniture_item
      furniture: default:bench
```

这是配置家具物品最简单的方法，但前提是你已经配置了一件家具。如果你不确定如何配置家具，请参考[🪑 家具](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture)。

如果觉得单独配置太麻烦，可以选择一起配置。下面是一个示例。`furniture` 下的格式遵循标准的家具配置格式。

```yaml
items:
  default:bench:
    material: paper
    custom-model-data: 2000
    data:
      display-name: "<!i>长椅"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/bench"
    behavior:
      type: furniture_item
      furniture:
        settings:
          item: default:bench
          sounds:
            break: minecraft:block.bamboo_wood.break
            place: minecraft:block.bamboo_wood.place
        placement:
          ground:
            rules:
              rotation: EIGHT
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
