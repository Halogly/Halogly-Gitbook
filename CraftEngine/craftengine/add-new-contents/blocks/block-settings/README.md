---
description: 本页面主要讲解如何向服务器添加新方块。
---

# ⚙️ 方块设置

### hardness <a href="#hardness" id="hardness"></a>

Determines how long it takes the player to destroy this block (Default: 2.0)

Copy

```
hardness: 0.5
```

### resistance <a href="#resistance" id="resistance"></a>

Determines the probability of the block surviving the explosion (Default: 2.0)

Copy

```
resistance: 0.5
```

### is-randomly-ticking <a href="#is-randomly-ticking" id="is-randomly-ticking"></a>

Determines whether the block state accepts random ticks, which is relevant for some block behaviors, such as leaves. (Default: false)

Copy

```
is-randomly-ticking: true
```

### push-reaction <a href="#push-reaction" id="push-reaction"></a>

Determines how the block reacts to piston pushes. Please note that some reactions may not work well with certain block types due to client visual sync issues. This problem will be fixed in future versions. (Default: NORMAL)

* NORMAL Pistons can push and pull this block normally.
* DESTROY Blocks pushed by pistons are destroyed instantly.
* BLOCK Pistons cannot move this block.
* IGNORE Seems to behave like PUSH\_ONLY but can stick to sticky blocks
* PUSH\_ONLY Blocks can be pushed by pistons, but cannot be retracted. Do not stick to sticky blocks.

Copy

```
push-reaction: NORMAL
```

### map-color <a href="#map-color" id="map-color"></a>

Determines what color the block is displayed on the map. Available colors can be found on [https://minecraft.wiki/w/Map\_item\_format](https://minecraft.wiki/w/Map_item_format) (Default: 0)

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F8WeafQSqNMDWGWeLd1NI%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=74875923\&sv=2)Copy

```
map-color: 36
```

### burnable <a href="#burnable" id="burnable"></a>

Determines whether this block can be ignited by the environment (Default: false)

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FyfgOaG8u4n8BGK600ymB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=75c2e1be\&sv=2)Copy

```
burnable: true
```

### fire-spread-chance <a href="#fire-spread-chance" id="fire-spread-chance"></a>

Determines how long the block can burn. A longer burn time means a greater chance of spreading fire to surrounding blocks. (Default: 0)

Copy

```
fire-spread-chance: 100  # 0-100
```

### burn-chance <a href="#burn-chance" id="burn-chance"></a>

Determines the probability of being ignited (Default: 0)

Copy

```
burn-chance: 30  # 0-100
```

### item <a href="#item" id="item"></a>

Determines the item that this block corresponds to. This is usually used to get blocks in creative mode with middle click. (Default: null)

Copy

```
item: default:xxx_block_item
```

### replaceable <a href="#replaceable" id="replaceable"></a>

Determines whether to replace the block at its original location when the player uses a block to interact with this block (Default: false)

Copy

```
replaceable: false
```

### is-redstone-conductor <a href="#is-redstone-conductor" id="is-redstone-conductor"></a>

Determines whether this block is a redstone signal conductor (Default: UNDEFINED)

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FeneBtRUIfZA3e7IkDj43%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=af1a2733\&sv=2)Copy

```
is-redstone-conductor: true
```

### is-suffocating <a href="#is-suffocating" id="is-suffocating"></a>

Determines whether the player will take suffocation damage (Default: UNDEFINED)

Copy

```
is-suffocating: true
```

### is-view-blocking <a href="#is-view-blocking" id="is-view-blocking"></a>

Whether to block the line of sight. However, this option is useless for players, but it will affect some entity mechanisms on the server. (Default: UNDEFINED)

Copy

```
is-view-blocking: true
```

### sounds <a href="#sounds" id="sounds"></a>

Determines the sound of the block in various situations (Default: null)

* fall When the player falls on this block
* hit When the player digs this block
* break When the player breaks this block
* step When the player walks on this block
* place When the player places this block
* land When the block falls on ground (For falling blocks)
* destroy When the block falls on ground and break (For falling blocks)

Copy

```
sounds:
  break: minecraft:block.deepslate.break
  step: minecraft:block.deepslate.step
  place: minecraft:block.deepslate.place
  hit: minecraft:block.deepslate.hit
  fall: minecraft:block.deepslate.fall
  land: minecraft:block.anvil.land
  destroy: minecraft:block.anvil.destroy
```

You can configure like this to precisely control the volume and pitch

Copy

```
sounds:
  break:
    id: minecraft:block.deepslate.break
    pitch: 0.5
    volume: 0.25
  step: minecraft:block.deepslate.step
```

### require-correct-tools <a href="#require-correct-tools" id="require-correct-tools"></a>

Determines if correct tool is required for the drops (Default: false)

Copy

```
require-correct-tools: false
```

### respect-tool-component <a href="#respect-tool-component" id="respect-tool-component"></a>

Decides if `minecraft:tool` component's `correct_for_drops` option should work as `correct-tools` below (Default: false)

Copy

```
respect-tool-component: false
```

### correct-tools <a href="#correct-tools" id="correct-tools"></a>

Determines the correct tool required to mine this block, otherwise no item will be dropped (Default: null)

Copy

```
correct-tools:
  - minecraft:wooden_pickaxe
  - minecraft:stone_pickaxe
  - minecraft:iron_pickaxe
  - minecraft:golden_pickaxe
  - minecraft:diamond_pickaxe
  - minecraft:netherite_pickaxe
```

If `correct-tools` is set, `require-correct-tools` would be true

### incorrect-tool-dig-speed <a href="#incorrect-tool-dig-speed" id="incorrect-tool-dig-speed"></a>

Slows down the dig speed if the tool is incorrect (Default: 0.3)

Copy

```
incorrect-tool-dig-speed: 0.3 # 0~1
```

### tags <a href="#tags" id="tags"></a>

Tags determine the properties of many blocks. For example, using minecraft:mineable/axe will make your blocks mine faster with an axe. [🏷️ Useful Tags](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-settings/useful-tags) (Default: null)

Copy

```
tags:
  - minecraft:mineable/axe
  - minecraft:logs_that_burn
  - minecraft:logs
  - minecraft:completes_find_tree_tutorial
```

### client-bound-tags <a href="#client-bound-tags" id="client-bound-tags"></a>

This would only work for vanilla blocks

Copy

```
client-bound-tags:
  - minecraft:beacon_base_blocks
```

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fwnpy7kYwGeRAiJbBTdQ3%252Fimage.png%3Falt%3Dmedia%26token%3D79a6c177-14af-4798-8f49-19c4ca688131\&width=768\&dpr=4\&quality=100\&sign=a05afaf\&sv=2)

### instrument <a href="#instrument" id="instrument"></a>

Determines what instrument the note block will play when it is above this block. (Default: harp)

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FNhpOFlvMUaWf3xPe3Byo%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=8f636002\&sv=2)Copy

```
instrument: BASEDRUM
```

### fluid-state <a href="#fluid-state" id="fluid-state"></a>

Decides the fluid state of this block state (Default: empty)

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FNKagcQZqIIVMxX7odHKU%252Fimage.png%3Falt%3Dmedia%26token%3D0f500b1f-bde4-4e28-84de-9ea9a70a7ba4\&width=768\&dpr=4\&quality=100\&sign=2ad91398\&sv=2)Copy

```
fluid-state: water
```

### support-shape <a href="#support-shape" id="support-shape"></a>

Determines the support shape provided by the block. By default, custom blocks will use the **support-shape** of their corresponding visual state. However, you can manually specify the **support-shape** of a vanilla block here instead.

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fd4ZOrffIv47Tzkw2r2fc%252Fimage.png%3Falt%3Dmedia%26token%3D223541ed-7b5f-451a-b909-038fae926f7e\&width=768\&dpr=4\&quality=100\&sign=4dea0506\&sv=2)Copy

```
support-shape: minecraft:stone
```

The remaining block settings are all related to the light system. CraftEngine has implemented partial light effects as much as possible without affecting server performance. Visual issues with the light system on the client side are normal and in most cases I can't fix them.

The block's occlusion of **skylight** is entirely determined by the **client-side** and **cannot be fixed** by sending packets from the server. Therefore, the **block-light** and **can-occlude** settings **only affect block-emitted light**, not skylight.

### luminance <a href="#luminance" id="luminance"></a>

Determines the light intensity of the block (Default: 0)

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FUCgtZHRVaWqDMLV52UAB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=f7dffef2\&sv=2)Copy

```
luminance: 15
```

### can-occlude <a href="#can-occlude" id="can-occlude"></a>

Determines whether this block can block light. This also determines whether the block can turn below block into another type. (For instance grass\_block -> dirt) (Default: undefined)

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fmsw2GomMjl3nfMAjxIGd%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=f7627d60\&sv=2)occlude: true

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FC116bz0ylSfikY93jQYN%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=aa5b24d2\&sv=2)occlude: false

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fx3zMrfKsVSu4lEhU9Iru%252Fimage.png%3Falt%3Dmedia%26token%3D0c9e7da8-8bf0-42e9-883b-79aad4232a4c\&width=768\&dpr=4\&quality=100\&sign=86053d4f\&sv=2)occlude: false

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FIQ62BLMGHWhQYfQbbbyZ%252Fimage.png%3Falt%3Dmedia%26token%3D8a5ff1d2-6d91-44b8-9bb6-ef701d1296e5\&width=768\&dpr=4\&quality=100\&sign=f33081f1\&sv=2)occlude: true

Copy

```
can-occlude: false
```

### block-light <a href="#block-light" id="block-light"></a>

Determines how much light level is reduced after passing through this block (Default: undefined)

Copy

```
block-light: 0
```

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FIARHS7xk9UHdF4ZQ12pC%252Fimage.png%3Falt%3Dmedia%26token%3D199f84cd-ede7-40f3-8cd5-1713f2896886\&width=768\&dpr=4\&quality=100\&sign=1ccab382\&sv=2)block-light: 15

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FFJBuj7nclW05zBTaWw6n%252Fimage.png%3Falt%3Dmedia%26token%3Dc2dd379c-0fa7-4c51-8778-667357cf6f03\&width=768\&dpr=4\&quality=100\&sign=ac9013bd\&sv=2)block-light: 7

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F5uiR2P5WZBE6aVvLkiUi%252Fimage.png%3Falt%3Dmedia%26token%3Dc35aa388-96de-4354-abf2-a6dd21cc47ef\&width=768\&dpr=4\&quality=100\&sign=8cf4e4e7\&sv=2)block-light: 0

### propagate-skylight <a href="#propagate-skylight" id="propagate-skylight"></a>

**This option has almost no effect, as the client will predict sky light updates.**

Determines whether natural light can pass through this block.

Copy

```
propagate-skylight: true
```
