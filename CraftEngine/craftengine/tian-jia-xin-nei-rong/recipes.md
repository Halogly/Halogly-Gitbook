---
description: This page mainly explains how to add new recipes to your server.
---

# 📖 Recipes

# 标签 <a href="#tags" id="tags"></a>

CraftEngine 允许你使用标签，并且可以自定义标签。要使用标签，只需要符合这个格式：`#namespace:tag`。

在以下示例中，我为 `palm_planks` 添加了两个原版标签，使它们能够参与使用这两个标签的数据包中的所有配方。

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
      item-name: "<!i>Palm Planks"
    model:
      type: "minecraft:model"
      path: "minecraft:item/custom/palm_planks"
      generation:
        parent: "minecraft:block/custom/palm_planks"
    behavior:
      type: block_item
      block: default:palm_planks
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FUohuvWjBBMBvvYIt8rG0%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=18f87368\&sv=2)#minecraft:planks

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Ff6mY7xsQNvHMDOn3vf1C%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=7db12ddc\&sv=2)#minecraft:wooden\_tool\_materials

### Group / Category <a href="#group-category" id="group-category"></a>

Copy

```
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

The `group` determines which group this recipe belongs to after it is unlocked on the client side. The `group` can be any name you choose freely. However, please avoid using illegal characters.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSoRMQK6BhH7By5iaVOcF%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=38c99bf0\&sv=2)

The `category` determines which tab this recipe is located in within the recipe book. The `category` type is limited.

* For cooking-type recipes, the options are `food`, `blocks`, and `misc`.
* For crafting-type recipes, the options are `building`, `redstone`, `equipment`, and `misc`.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FMvzwXvGqBXFtC5RXTIXg%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=637cf10e\&sv=2)

### Shaped Crafting Recipe <a href="#shaped-crafting-recipe" id="shaped-crafting-recipe"></a>

Copy

```
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

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FGr062ZfKJry53tqR4lLB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=4aa78640\&sv=2)Copy

```
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

### Shapeless Crafting Recipe <a href="#shapeless-crafting-recipe" id="shapeless-crafting-recipe"></a>

Copy

```
recipes:
  default:palm_planks:
    type: shapeless
    category: building
    group: planks
    ingredients:
      - "#default:palm_logs"
      # list is also supported
      - - test:ingredient1
        - test:ingredient2
    result:
      id: default:palm_planks
      count: 4
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FQajicG9iHchp728pMRmm%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=e198fba\&sv=2)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FyfUiEjTjVRjO7AG5dQID%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=e99a4805\&sv=2)

### Cooking Recipe <a href="#cooking-recipe" id="cooking-recipe"></a>

Cooking Recipe includes `smelting`, `blasting`, `smoking`, and `campfire_cooking`. Regardless of the type, the configuration format remains the same.

Copy

```
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

### Stone Cutting Recipe <a href="#stone-cutting-recipe" id="stone-cutting-recipe"></a>

Stone Cutting Recipe is a somewhat unique recipe type. I do not recommend using custom items as ingredients, as this is highly likely to cause significant client-side visual issues.

Copy

```
recipes:
  default:stonecutting_example:
    type: stonecutting
    group: topaz
    ingredient: "minecraft:stone"
    result:
      id: default:topaz
      count: 1
```

### Smithing Transform Recipe <a href="#smithing-transform-recipe" id="smithing-transform-recipe"></a>

Copy

```
default:topaz_bow:
  type: smithing_transform
  # slot 1 (Optional)
  template-type: default:topaz
  # slot 2 (Required)
  base: minecraft:bow
  # slot 3 (Optional)
  addition: default:topaz
  # merge two items' components like what vanilla does
  merge-components: true # default: true
  # see the guide below
  post-processors: []
  result:
    id: default:topaz_bow
    count: 1
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FEvTD2AqtbFndtXO4icWX%252Fimage.png%3Falt%3Dmedia%26token%3D1f4a412f-0ccb-465d-adde-e257c2a7a73e\&width=768\&dpr=4\&quality=100\&sign=66e098ea\&sv=2)

If you don't like the vanilla merging method, you can use a custom post-processor.

Copy

```
post-processors:
  # Keep the specified components (1.20.5+)
  - type: keep_components
    components:
      - minecraft:enchantments
  # Keep the specified nbt tags (1.20-1.20.4)
  - type: keep_tags
    tags:
      - display.Name
      - CustomModelData
```
