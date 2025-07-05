---
description: 为物品设置原版 NBT 标签或组件，以利用某些原版 Minecraft 功能。
---

# 🔢 物品数据

## 🔢 Item Data

## 什么是物品数据？ <a href="#what-is-item-data" id="what-is-item-data"></a>

物品数据是指旧版本中物品的 NBT（二进制命名标签），或 1.20.5 及以上版本中的物品组件。通过这些数据，我们可以自定义物品的各个方面，如名称、描述、属性和其他功能。

## 外部数据 <a href="#external-data" id="external-data"></a>

如果你希望 CraftEngine 物品保留外部插件物品的数据，请按照此配置：

```yaml
items:
  default:example_item:
    data:
      external:
        plugin: NeigeItems
        id: example_item
```

[🐌 External Item Providers](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/external-item-providers)

## 硬编码数据 <a href="#hard-coded-data" id="hard-coded-data"></a>

在此上下文中，硬编码数据意味着配置格式由插件提供和维护，这确保了跨版本的兼容性。这些格式由插件定义，因此可能与游戏本身使用的标准 NBT（命名二进制标签）或组件格式有所不同。这种方法的优点是插件处理所有维护工作，包括版本兼容性，因此用户无需担心游戏版本之间的变化或更新。

```yaml
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>黄玉棒"
```

### item-name 物品名称 <a href="#item-name" id="item-name"></a>

Determines the default name of this item, unlike the `custom-name`, this name can't be erased using an anvil, won't be italicized, and does not show in some labels, such as banner markers and item frames.\
设置物品的默认名称，与 `custom-name` 不同，此名称无法使用铁砧消除，不会斜体显示，也不会在某些标签中显示，例如织布机和物品展示框。

```yaml
items:
  default:topaz_rod:
    data:
      item-name: "<!i><#FF8C00>黄玉棒" 
      # 这里使用 <!i> 是因为 1.20.4 及以下版本没有 item_name 组件
```

### custom-name 自定义名称 <a href="#custom-name" id="custom-name"></a>

设置物品的自定义名称，就像在铁砧中修改的名称那样。

```yaml
items:
  default:topaz_rod:
    data:
      custom-name: "<!i><#FF8C00>黄玉棒"
```

### lore 描述信息 <a href="#lore" id="lore"></a>

设置物品提示框中的描述信息。

```yaml
items:
  default:topaz_rod:
    data:
      lore: 
        - "亮晶晶的棒子！"
```

### unbreakable 无法破坏 <a href="#unbreakable" id="unbreakable"></a>

设置物品是否不可破坏

```yaml
items:
  default:topaz_rod:
    data:
      unbreakable: true
```

### enchantment 魔咒 <a href="#enchantment" id="enchantment"></a>

设置物品的附魔属性

```yaml
items:
  default:topaz_rod:
    data:
      enchantment:
        minecraft:sharpness: 1
        custom:enchant: 3
```

### dyed-color 所染颜色 <a href="#dyed-color" id="dyed-color"></a>

设置物品的颜色

```yaml
items:
  default:sofa:
    data:
      dyed-color: 255,255,255
```

### custom-model-data 自定义模型数据 <a href="#custom-model-data" id="custom-model-data"></a>

```yaml
items:
  default:sofa:
    data:
      custom-model-data: 100
```

### food 食物（1.20.5+） <a href="#food-1.20.5" id="food-1.20.5"></a>

```yaml
items:
  default:magic_apple:
    material: apple
    data:
      food: 
        nutrition: 5
        saturation: 3.5
        can-always-eat: false
```

### jukebox-playable 插入唱片机所播放的音乐 (1.21+) <a href="#jukebox-playable-1.21" id="jukebox-playable-1.21"></a>

```yaml
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```

### item-model 物品模型 (1.21.2+) <a href="#item-model-1.21.2" id="item-model-1.21.2"></a>

```yaml
items:
  default:music_stick:
    data:
      item-model: default:music_stick
```

### tooltip-style 物品提示框背景和边框样式 (1.21.2+) <a href="#tooltip-style-1.21.2" id="tooltip-style-1.21.2"></a>

设置物品的提示框背景和边框样式

```yaml
items:
  default:topaz_rod:
    data:
      tooltip-style: minecraft:topaz #namespace:tooltip_style_id
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FG5cqs5c033VOfKiw2TJu%252Fimage.png%3Falt%3Dmedia%26token%3D4c517089-ab55-4fc8-adfe-c26bb7176e91\&width=768\&dpr=4\&quality=100\&sign=81334337\&sv=2)

要创建提示框样式，你必须将纹理放置在以下目录中。

[https://zh.minecraft.wiki/w/数据组件?variant=zh-cn#tooltip\_style](https://zh.minecraft.wiki/w/%E6%95%B0%E6%8D%AE%E7%BB%84%E4%BB%B6?variant=zh-cn#tooltip_style)

### trim 盔甲纹饰 <a href="#trim" id="trim"></a>

apply a decorative alteration to a [tool](https://minecraft.wiki/w/Tool) or [armor](https://minecraft.wiki/w/Armor)\
更改[工具](https://zh.minecraft.wiki/w/%E5%B7%A5%E5%85%B7)或[盔甲](https://zh.minecraft.wiki/w/%E7%9B%94%E7%94%B2)的装饰

```yaml
trim:
  pattern: eye # https://minecraft.wiki/w/Smithing#Trimming
  material: iron # https://minecraft.wiki/w/Smithing#Material
```

### equippable 可穿戴性（1.21.2+） <a href="#equippable-1.21.2" id="equippable-1.21.2"></a>

如果存在，此物品可以装备在指定槽位。

```yaml
equippable:
  # 放置物品的槽位
  slot: head # HEAD / CHEST / LEGS / FEET / BODY / MAIN_HAND / OFF_HAND / SADDLE
  
  # 可选参数
  # 这个目录指的是 assets/<命名空间>/equipment/<id>.json
  asset-id: minecraft:topaz
  # 装备时覆盖纹理的资源位置。这个目录指的是 assets/<命名空间>/textures/<id>。
  camera-overlay: namespace:id
  # 物品是否可以被发射器发射出去并装备上。
  dispensable: true
  # 当穿戴者受伤时，物品是否也会受损。
  damage-on-hurt: true
  # 物品是否可以通过右键点击装备到相应的槽位。
  swappable: true
  # >= 1.21.5
  # 通过对目标怪物按使用键，物品是否可以装备到目标身上（只要这个物品可以装备到目标身上）
  equip-on-interact: true
```

## 可自定义数据 <a href="#customizable-data" id="customizable-data"></a>

可自定义数据不由插件维护，其格式会随着 Minecraft 的更新而变化，尤其是近期数据组件频繁的更新。若想避免因版本更新导致配置大幅改动，可以考虑使用模板来建立标准化的配置文件格式。当发布新版本时，只需更新模板就能够适应任何更新。如果你不熟悉如何使用模板，请务必阅读[📄 模板 \[必读\]](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/templates-must-read)。这种方法有助于简化更新流程，减少配置与最新游戏版本保持兼容性的工作量。

### NBT（1.20-1.20.4） <a href="#nbt-1.20-1.20.4" id="nbt-1.20-1.20.4"></a>

由于 NBT（二进制命名标签）已经过时，因此在此不会详细讨论。

[https://zh.minecraft.wiki/w/物品格式](https://zh.minecraft.wiki/w/%E7%89%A9%E5%93%81%E6%A0%BC%E5%BC%8F)

```yaml
items:
  default:topaz_rod:
    data:
      nbt:
        CustomModelData: 1000
```

### 组件（1.20.5+） <a href="#components-1.20.5" id="components-1.20.5"></a>

自定义组件的格式严格遵循 [Minecraft Wiki](https://zh.minecraft.wiki/w/%E6%95%B0%E6%8D%AE%E7%BB%84%E4%BB%B6) 指南。下面，我会通过几个示例来指导你如何配置自定义组件。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FNrlWy1Cxy4vn2GK1ODdL%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=21ad2949\&sv=2)

从图中可以看出，`max_damage` 接受一个 `I`（代表一个整数类型参数）。因此，在我们的配置中，我们只需要直接使用一个整数即可。

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:max_damage: 128
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F7cqvxKcjpE2LTlsbTj9K%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=cfd2fc97\&sv=2)

从图中可以看出，`food` 需要三个参数：类型为 `int` 的 `nutrition`，类型为 `float` 的 `saturation`，以及类型为 `boolean` 的 `can_always_eat`。

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:food:
          nutrition: 4
          saturation: 2.0
          can_always_eat: false
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FB6jF06WTXXXnonNs0kqo%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=37ba2404\&sv=2)

现在，让我们尝试处理一个复合标签。`{}` 表示你需要在你的 YAML 配置中打开一个新的部分。

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:enchantments:
          levels:
            minecraft:sharpness: 1
          show_in_tooltip: false
```

然而，仔细阅读 Wiki 后，你会发现此方法在 1.21.5 版本中已经过时。当 1.21.5 版本发布时，你需要按照以下方式更新你的配置文件：

```yaml
items:
  guide:test:
    data:
      components:
        minecraft:enchantments:
          minecraft:sharpness: 1
```

你也可以使用 json 格式配置组件

```yaml
minecraft:custom_data: "(json) {\"test\":1}"
```

### 移除组件（1.20.5+） <a href="#remove-components-1.20.5" id="remove-components-1.20.5"></a>

从物品中移除组件

```yaml
items:
  test:item:
    data:
      remove-components:
        - minecraft:equippable
```
