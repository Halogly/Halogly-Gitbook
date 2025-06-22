# 客户端物品数据

"客户端数据"仅存在于客户端，服务端没有相关的组件。通过客户端物品组件，你可以轻松实时更新物品描述——即使是像 `item_model` 和 `custom_model_data` 这样的内容。此外，CraftEngine 物品不会像其他插件那样在创造模式下永久修改！

**Every option available in** [🔢 Item Data](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data) **is applicable in** [🔢 Client Bound Item Data](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data/client-bound-item-data)**.**[🔢 物品数据](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data)**中的所有选项都适用于**[🔢 客户端绑定物品数据](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data/client-bound-item-data)**。**

```yaml
items:
  default:topaz_rod:
    client-bound-data:
      item-name: "<!i><#FF8C00>我不是黄玉棒"
    data:
      item-name: "<!i><#FF8C00>黄玉棒"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FosV8ncsaaP8TTpxBwTP8%252Fimage.png%3Falt%3Dmedia%26token%3De06087ae-9871-4577-96d2-67f4a6e25fa7\&width=768\&dpr=4\&quality=100\&sign=c130673\&sv=2) ![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FXZ8JiAryf19y0MtzHlor%252Fimage.png%3Falt%3Dmedia%26token%3D4e44fefa-ba07-44f0-b939-564c9d7e8722\&width=768\&dpr=4\&quality=100\&sign=c5f338b1\&sv=2)

`client-bound-data` 对冒险模式的玩家非常实用，因为这可以让他们在服务端破坏某些真实的自定义方块。

```yaml
items:
  default:topaz_pickaxe:
    material: golden_pickaxe
    custom-model-data: 1000
    settings:
      tags:
        - "default:topaz_tools"
    client-bound-data:
      components:
        # 客户端的方块状态
        can_break:
          blocks: minecraft:note_block
          state:
            "instrument": "hat"
            "note": "0"
            "powered": "false"
    data:
      item-name: "<!i><#FF8C00><i18n:item.topaz_pickaxe>"
      tooltip-style: minecraft:topaz
      components:
        minecraft:max_damage: 64
        # 服务端的方块状态
        can_break:
          blocks: "craftengine:note_block_1"
    model:
      template: default:model/simplified_handheld
      arguments:
        path: "minecraft:item/custom/topaz_pickaxe"
```
