---
description: 本页面主要讲解如何向服务器中添加新的合成配方。
---

# 📖 Recipes

# 标签 <a href="#tags" id="tags"></a>

CraftEngine 允许你使用标签，并且可以自定义标签。要使用标签，只需要符合这个格式：`#namespace:tag`。

在下面的示例中，我为 `palm_planks` 添加了两个原版标签，这样它就可以参与这两个标签在数据包中的代表的合成配方了。

```yaml
items:
  default:palm_planks:
    material: paper
    custom-model-data: 1004
    settings:
      fuel-time: 300
      tags:
        - "minecraft:planks"
        - "minecraft:wooden_tool_materials"
    data:
      item-name: "<!i>棕榈木板"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/palm_planks"
      generation:
        parent: "minecraft:block/custom/palm_planks"
    behavior:
      type: block_item
      block: default:palm_planks
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FUohuvWjBBMBvvYIt8rG0%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=18f87368\&sv=2)
#minecraft:planks

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Ff6mY7xsQNvHMDOn3vf1C%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=7db12ddc\&sv=2)
#minecraft:wooden\_tool\_materials

# 分组/分类 <a href="#group-category" id="group-category"></a>

```yaml
recipes:
  default:palm_planks:
    type: shapeless
    category: building
    group: planks
    ingredients:
      A: "#default:palm_logs"
    result:
      id: default:palm_planks
      count: 4
```

`group` 决定这个合成配方在客户端解锁后属于哪个分组。`group` 的名称任由你自己决定。但注意不要使用非法字符。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSoRMQK6BhH7By5iaVOcF%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=38c99bf0\&sv=2)

The `category` determines which tab this recipe is located in within the recipe book. The `category` type is limited.
`category` 决定这个合成配方在配方书中位于哪个标签页。`category` 类型是有限的。

* 对于烹饪类型的配方，选项是 `food`、`blocks` 和 `misc`。
* 对于制作类型的配方，选项是 `building`、`redstone`、`equipment` 和 `misc`。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FMvzwXvGqBXFtC5RXTIXg%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=637cf10e\&sv=2)

# 有序配方 <a href="#shaped-crafting-recipe" id="shaped-crafting-recipe"></a>

```yaml
recipes:
  default:topaz_shovel:
    type: shaped
    pattern:
      - "A"
      - "B"
      - "B"
    ingredients:
      A: "default:topaz"
      B: "minecraft:stick"
    result:
      id: default:topaz_shovel
      count: 1
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FGr062ZfKJry53tqR4lLB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=4aa78640\&sv=2)

```yaml
recipes:
  default:chinese_lantern:
    type: shaped
    pattern:
      - "ABA"
      - "BCB"
      - "ABA"
    ingredients:
      A: "#minecraft:planks"
      B: "minecraft:stick"
      C: "minecraft:torch"
    result:
      id: default:chinese_lantern
      count: 1
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FuOlikOvTLLzJZZxki5Cl%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=671f42c3\&sv=2)

# 无序配方 <a href="#shapeless-crafting-recipe" id="shapeless-crafting-recipe"></a>

```yaml
recipes:
  default:palm_planks:
    type: shapeless
    category: building
    group: planks
    ingredients:
      - "#default:palm_logs"
      # 支持列表
      - - test:ingredient1
        - test:ingredient2
    result:
      id: default:palm_planks
      count: 4
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FQajicG9iHchp728pMRmm%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=e198fba\&sv=2)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FyfUiEjTjVRjO7AG5dQID%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=e99a4805\&sv=2)

# 烧炼配方 <a href="#cooking-recipe" id="cooking-recipe"></a>

烧炼配方包括 `smelting` 熔炉配方、`blasting` 高炉配方、`smoking` 烟熏炉配方和 `campfire_cooking` 营火配方。无论类型如何，配置格式保持不变。

```yaml
recipes:
  default:topaz_from_smelting_topaz_ore:
    type: smelting
    experience: 1.0
    category: misc
    group: topaz
    time: 200
    ingredient: "default:topaz_ore"
    result:
      id: default:topaz
      count: 1
  default:topaz_from_smelting_deepslate_topaz_ore:
    type: smelting
    experience: 1.0
    category: misc
    group: topaz
    time: 200
    ingredient: "default:deepslate_topaz_ore"
    result:
      id: default:topaz
      count: 1
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSJHB7w9gPm0UDldpjwwM%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=47bddd6\&sv=2)

# 切石机配方 <a href="#stone-cutting-recipe" id="stone-cutting-recipe"></a>

切石机配方是一种比较独特的配方类型。不建议使用自定义物品作为原料，因为这很可能会导致客户端显示异常。

```yaml
recipes:
  default:stonecutting_example:
    type: stonecutting
    group: topaz
    ingredient: "minecraft:stone"
    result:
      id: default:topaz
      count: 1
```

# 锻造升级配方 <a href="#smithing-transform-recipe" id="smithing-transform-recipe"></a>

```yaml
default:topaz_bow:
  type: smithing_transform
  # 槽位 1（可选）
  template-type: default:topaz
  # 槽位 2（必需）
  base: minecraft:bow
  # 槽位 3（可选）
  addition: default:topaz
  # 合并两个物品的组件，就像原版那样
  merge-components: true # 默认: true
  # 请参阅下方的指南
  post-processors: []
  result:
    id: default:topaz_bow
    count: 1
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FEvTD2AqtbFndtXO4icWX%252Fimage.png%3Falt%3Dmedia%26token%3D1f4a412f-0ccb-465d-adde-e257c2a7a73e\&width=768\&dpr=4\&quality=100\&sign=66e098ea\&sv=2)

如果你不喜欢原版的合并方式，你可以使用一个自定义的后端处理器。

```yaml
post-processors:
  # 保持指定的组件（1.20.5+）
  - type: keep_components
    components:
      - minecraft:enchantments
  # 保持指定的 NBT 标签（1.20-1.20.4）
  - type: keep_tags
    tags:
      - display.Name
      - CustomModelData
```
