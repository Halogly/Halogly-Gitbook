# 🪑 Furniture Item

A furniture item is an item that is bound to a piece of furniture. You can configure its corresponding furniture ID here, or even the entire furniture configuration (but please note that doing so will result in the time taken to load the furniture being recorded under the item loading process). When you bind this behavior to an item, you can place it by right-clicking.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSYOQXH6ZY0VcGYGZLdgN%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=d039abea\&sv=2)Copy

```
items:
  default:bench:
    behavior:
      type: furniture_item
      furniture: default:bench
```

This is the simplest way to configure a furniture-item, but it assumes that you have already configured a piece of furniture. If you are unsure how to configure a piece of furniture, please refer to [🪑 Furniture](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/furniture).

If you find it too cumbersome to configure them separately, you can choose to configure them together. Below is an example. The format under `furniture` follows the standard furniture configuration format.

Copy

```
items:
  default:bench:
    material: paper
    custom-model-data: 2000
    data:
      display-name: "<!i>Bench"
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
