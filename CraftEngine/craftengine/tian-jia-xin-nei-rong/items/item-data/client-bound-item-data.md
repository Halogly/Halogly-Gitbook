# 🔢 Client Bound Item Data

The "client-bound data" exists solely on the client side, and there are no related components on the server side. With the client-side item component, you can easily update item descriptions in real-time - even stuff like `item_model` and `custom_model_data`. Plus, CraftEngine items won't get permanently modified in creative mode like other plugins do!

**Every option available in** [🔢 Item Data](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data) **is applicable in** [🔢 Client Bound Item Data](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/items/item-data/client-bound-item-data)**.**

Copy

```
items:
  default:topaz_rod:
    client-bound-data:
      item-name: "<!i><#FF8C00>I'm not Topaz Rod"
    data:
      item-name: "<!i><#FF8C00>Topaz Rod"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FosV8ncsaaP8TTpxBwTP8%252Fimage.png%3Falt%3Dmedia%26token%3De06087ae-9871-4577-96d2-67f4a6e25fa7\&width=768\&dpr=4\&quality=100\&sign=c130673\&sv=2)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FXZ8JiAryf19y0MtzHlor%252Fimage.png%3Falt%3Dmedia%26token%3D4e44fefa-ba07-44f0-b939-564c9d7e8722\&width=768\&dpr=4\&quality=100\&sign=c5f338b1\&sv=2)

`client-bound-data` is quite useful for players in adventure mode, allowing them to break certain real custom blocks on serverside.

Copy

```
items:
  default:topaz_pickaxe:
    material: golden_pickaxe
    custom-model-data: 1000
    settings:
      tags:
        - "default:topaz_tools"
    client-bound-data:
      components:
        # client side block state
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
        # server side block state
        can_break:
          blocks: "craftengine:note_block_1"
    model:
      template: default:model/simplified_handheld
      arguments:
        path: "minecraft:item/custom/topaz_pickaxe"
```
