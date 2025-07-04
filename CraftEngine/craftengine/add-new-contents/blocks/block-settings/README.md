---
description: 本页面主要讲解如何向服务器添加新方块。
---

# ⚙️ 方块设置

# 硬度 <a href="#hardness" id="hardness"></a>

玩家破坏方块所需的时间（默认: 2.0）

```yaml
hardness: 0.5
```

# 爆炸抗性 <a href="#resistance" id="resistance"></a>

方块阻挡爆炸的能力（默认: 2.0）

```yaml
resistance: 0.5
```

# 随机刻 <a href="#is-randomly-ticking" id="is-randomly-ticking"></a>

方块状态是否根据随机刻更新，这与某些方块的行为相关，例如树叶。（默认: false）

```yaml
is-randomly-ticking: true
```

# 活塞推动行为 <a href="#push-reaction" id="push-reaction"></a>

方块如何应对活塞推动。请注意，由于客户端显示同步问题，某些行为可能与特定方块类型不兼容。这个问题会在未来版本中修复。（默认: NORMAL）

* NORMAL 活塞可以正常地推动和拉动方块。
* DESTROY 活塞推动方块时会立即破坏方块。
* BLOCK 活塞无法移动方块。
* IGNORE 与 PUSH\_ONLY 类似，只不过方块可以被粘性方块粘连。
* PUSH\_ONLY 方块可被活塞推动，但不可被拉动。方块不被粘性方块粘连。

```yaml
push-reaction: NORMAL
```

# 地图基色 <a href="#map-color" id="map-color"></a>

方块在地图上显示的颜色。所有可用的颜色可以在 [https://zh.minecraft.wiki/w/地图存储格式?variant=zh-cn#地图基色](https://zh.minecraft.wiki/w/地图存储格式?variant=zh-cn#地图基色) 上找到。（默认: 0）

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F8WeafQSqNMDWGWeLd1NI%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=74875923\&sv=2)

```yaml
map-color: 36
```

# 可燃 <a href="#burnable" id="burnable"></a>

方块是否可燃。（默认: false）

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FyfgOaG8u4n8BGK600ymB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=75c2e1be\&sv=2)

```yaml
burnable: true
```

# 火势蔓延几率 <a href="#fire-spread-chance" id="fire-spread-chance"></a>

方块可以燃烧多久。更长的燃烧时间意味着有更大的几率将火传播到周围的方块。（默认: 0）

```yaml
fire-spread-chance: 100  # 0-100
```

# 引燃几率 <a href="#burn-chance" id="burn-chance"></a>

方块被引燃的概率。（默认: 0）

```yaml
burn-chance: 30  # 0-100
```

# 物品 <a href="#item" id="item"></a>

方块对应的物品。这通常用于在创造模式下使用中键获取方块。（默认: null）

```yaml
item: default:xxx_block_item
```

# 替换 <a href="#replaceable" id="replaceable"></a>

玩家在该方块的位置放置其他方块时是否会被替换。（默认: false）

```yaml
replaceable: false
```

# 红石导体 <a href="#is-redstone-conductor" id="is-redstone-conductor"></a>

方块是否是红石信号的导体（默认: UNDEFINED）

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FeneBtRUIfZA3e7IkDj43%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=af1a2733\&sv=2)

```yaml
is-redstone-conductor: true
```

# 窒息生物 <a href="#is-suffocating" id="is-suffocating"></a>

玩家是否会受到窒息伤害（默认: UNDEFINED）

```yaml
is-suffocating: true
```

# 阻挡视线 <a href="#is-view-blocking" id="is-view-blocking"></a>

是否阻挡视线。然而，此选项对玩家无用，但会影响服务器上的一些实体机制。（默认: UNDEFINED）

```yaml
is-view-blocking: true
```

### 声音 <a href="#sounds" id="sounds"></a>

方块在不同情况下的声音。（默认: null）

* fall 带有坠落伤害时坠落在方块上
* hit 挖掘方块时
* break 破坏方块时
* step 在方块上行走时
* place 放置方块时
* land 下落的方块落地且变为方块（下落的方块）
* destroy 下落的方块落地且未能变为方块（下落的方块）

```yaml
sounds:
  break: minecraft:block.deepslate.break
  step: minecraft:block.deepslate.step
  place: minecraft:block.deepslate.place
  hit: minecraft:block.deepslate.hit
  fall: minecraft:block.deepslate.fall
  land: minecraft:block.anvil.land
  destroy: minecraft:block.anvil.destroy
```

你可以这样配置来控制声音的音量和音调

```yaml
sounds:
  break:
    id: minecraft:block.deepslate.break
    pitch: 0.5
    volume: 0.25
  step: minecraft:block.deepslate.step
```

# 需要合适的工具 <a href="#require-correct-tools" id="require-correct-tools"></a>

是否需要合适的工具来获取掉落物（默认: false）

```yaml
require-correct-tools: false
```

# 尊重工具组件 <a href="#respect-tool-component" id="respect-tool-component"></a>

是否启用 `minecraft:tool` 组件的 `correct_for_drops` 选项，用 `correct-tools` 运行。（默认: false）

```yaml
respect-tool-component: false
```

# 合适工具 <a href="#correct-tools" id="correct-tools"></a>

挖掘方块所需的合适工具，若不使用合适的工具挖掘，则不会掉落物品。（默认: null）

```yaml
correct-tools:
  - minecraft:wooden_pickaxe
  - minecraft:stone_pickaxe
  - minecraft:iron_pickaxe
  - minecraft:golden_pickaxe
  - minecraft:diamond_pickaxe
  - minecraft:netherite_pickaxe
```

若设置了 `correct-tools`，则会启用 `require-correct-tools`

# 错误工具挖掘速度 <a href="#incorrect-tool-dig-speed" id="incorrect-tool-dig-speed"></a>

如果挖掘工具不正确，会减慢挖掘速度。（默认: 0.3）

```yaml
incorrect-tool-dig-speed: 0.3 # 0~1
```

# 标签 <a href="#tags" id="tags"></a>

标签决定方块的属性。例如，带有 minecraft:mineable/axe 标签的方块可以用斧头更快地开采。[🏷️ 有用的标签](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-settings/useful-tags)（默认: null）

```yaml
tags:
  - minecraft:mineable/axe
  - minecraft:logs_that_burn
  - minecraft:logs
  - minecraft:completes_find_tree_tutorial
```

# 客户端标签 <a href="#client-bound-tags" id="client-bound-tags"></a>

仅适用于原版方块。

```yaml
client-bound-tags:
  - minecraft:beacon_base_blocks
```

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fwnpy7kYwGeRAiJbBTdQ3%252Fimage.png%3Falt%3Dmedia%26token%3D79a6c177-14af-4798-8f49-19c4ca688131\&width=768\&dpr=4\&quality=100\&sign=a05afaf\&sv=2)

# 乐器 <a href="#instrument" id="instrument"></a>

当音符盒位于方块上方时会播放哪种乐器。（默认: harp）

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FNhpOFlvMUaWf3xPe3Byo%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=8f636002\&sv=2)

```yaml
instrument: BASEDRUM
```

# 含水状态 <a href="#fluid-state" id="fluid-state"></a>

方块的含水状态。（默认: empty）

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FNKagcQZqIIVMxX7odHKU%252Fimage.png%3Falt%3Dmedia%26token%3D0f500b1f-bde4-4e28-84de-9ea9a70a7ba4\&width=768\&dpr=4\&quality=100\&sign=2ad91398\&sv=2)

```yaml
fluid-state: water
```

# 支撑面 <a href="#support-shape" id="support-shape"></a>

方块提供的支撑面。默认情况下，自定义方块会使用符合其本身的**支撑面**。不过你也可以在这里手动指定原版方块的**支撑面**。

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fd4ZOrffIv47Tzkw2r2fc%252Fimage.png%3Falt%3Dmedia%26token%3D223541ed-7b5f-451a-b909-038fae926f7e\&width=768\&dpr=4\&quality=100\&sign=4dea0506\&sv=2)

```yaml
support-shape: minecraft:stone
```

以下的方块设置都与光照系统相关。CraftEngine 已经尽可能地在不影响服务器性能的情况下实现了部分光照效果。客户端光照系统出现视觉方面的问题是正常的，大多数情况下我无法修复它们。

方块遮挡**天空光照**完全由**客户端**决定，**无法**通过从服务器发送数据包来修复。因此，**方块光照**和**是否遮光**设置**仅影响方块发出的光**，不影响天空光照。

# 亮度 <a href="#luminance" id="luminance"></a>

方块的光照强度。（默认: 0）

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FUCgtZHRVaWqDMLV52UAB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=f7dffef2\&sv=2)

```yaml
luminance: 15
```

# 是否遮光 <a href="#can-occlude" id="can-occlude"></a>

方块是否可以遮挡光照。这也决定方块是否可以将下方的方块转化为另一种类型的方块。（例如草方块变为泥土）（默认: undefined）

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fmsw2GomMjl3nfMAjxIGd%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=f7627d60\&sv=2)
can-occlude: true

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FC116bz0ylSfikY93jQYN%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=aa5b24d2\&sv=2)
can-occlude: false

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fx3zMrfKsVSu4lEhU9Iru%252Fimage.png%3Falt%3Dmedia%26token%3D0c9e7da8-8bf0-42e9-883b-79aad4232a4c\&width=768\&dpr=4\&quality=100\&sign=86053d4f\&sv=2)
can-occlude: false

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FIQ62BLMGHWhQYfQbbbyZ%252Fimage.png%3Falt%3Dmedia%26token%3D8a5ff1d2-6d91-44b8-9bb6-ef701d1296e5\&width=768\&dpr=4\&quality=100\&sign=f33081f1\&sv=2)
can-occlude: true

```yaml
can-occlude: false
```

### 阻挡亮度 <a href="#block-light" id="block-light"></a>

光线穿过方块后降低亮度的程度。（默认: undefined）

```yaml
block-light: 0
```

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FIARHS7xk9UHdF4ZQ12pC%252Fimage.png%3Falt%3Dmedia%26token%3D199f84cd-ede7-40f3-8cd5-1713f2896886\&width=768\&dpr=4\&quality=100\&sign=1ccab382\&sv=2)
block-light: 15

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FFJBuj7nclW05zBTaWw6n%252Fimage.png%3Falt%3Dmedia%26token%3Dc2dd379c-0fa7-4c51-8778-667357cf6f03\&width=768\&dpr=4\&quality=100\&sign=ac9013bd\&sv=2)
block-light: 7

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F5uiR2P5WZBE6aVvLkiUi%252Fimage.png%3Falt%3Dmedia%26token%3Dc35aa388-96de-4354-abf2-a6dd21cc47ef\&width=768\&dpr=4\&quality=100\&sign=8cf4e4e7\&sv=2)
block-light: 0

### 穿透天空光照 <a href="#propagate-skylight" id="propagate-skyligh t"></a>

**此选项几乎没有效果，因为客户端会预测天空光照的更新。**

自然光是否可以穿透方块。

```yaml
propagate-skylight: true
```
