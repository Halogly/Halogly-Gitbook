# ⚙️ Furniture Settings

### item <a href="#item" id="item"></a>

Determines the item that this furniture corresponds to. This is usually used to get furniture item in creative mode with middle click(1.21.4+).

Copy

```
item: default:test_furniture
```

### sounds <a href="#sounds" id="sounds"></a>

Determines the sound of the furniture in various situations

* break When the player breaks this furniture
* place When the player places this furniture

Copy

```
sounds:
  break: minecraft:block.bamboo_wood.break
  place: minecraft:block.bamboo_wood.place
```

You can configure like this to precisely control the volume and pitch

Copy

```
sounds:
  break:
    id: minecraft:block.deepslate.break
    pitch: 0.5
    volume: 0.25
  place: minecraft:block.deepslate.step
```

### minimized <a href="#minimized" id="minimized"></a>

Determines whether this furniture should minimize the network packet sent to players without admin permissions.

Copy

```
minimized: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FqmuOtslb0m4pzkyKjf20%252Fimage.png%3Falt%3Dmedia%26token%3D7651bfce-5d2e-494a-8893-5017aa63a332\&width=768\&dpr=4\&quality=100\&sign=bad16b1e\&sv=2)
