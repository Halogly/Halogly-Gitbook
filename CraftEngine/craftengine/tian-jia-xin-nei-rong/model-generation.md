---
description: 本页面主要讲解如何使用模型生成。
---

# 🏭️ Model Generation

# 介绍 <a href="#introduction" id="introduction"></a>

[🏭️ 模型生成](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/model-generation)用于创建 YAML 格式的模型。

当配置了多个相似的模型（例如，只有纹理不同的 16 种羊毛颜色的沙发）时，通常需要创建对应数量的独立模型。但如果使用模型生成，你就可以轻松地通过 YAML 格式管理这些模型的继承关系。

`path` 选项中指定的路径（位于 `generation` 相同的配置部分）必须指向一个不存在的模型路径！否则它会与现有模型产生冲突。

模型生成始终是**可选配置**。如果你已经为该模块/项目创建了一个 JSON 模型文件，你**不需要**使用 `generation`——而是直接使用 `path` 指定的模型路径。

# 配置位置 <a href="#where-to-configure" id="where-to-configure"></a>

如果你仔细观察，就会发现插件在很多地方都会使用以下配置格式。

```yaml
path: "xxx:xxx"
generation:
  parent: "minecraft:xxx/xxx"
  textures:
    "xxx": "xxx:xxx"
```

本插件实际上在所有可指定模型路径（`path`）的位置均支持模型生成功能。当你在任何配置中看到 `path` 时，即表示可以在同一配置部分中使用 `generation`。

# 参数 <a href="#arguments" id="arguments"></a>

## 继承 <a href="#parent" id="parent"></a>

> 从指定路径加载其他模型，路径格式需符合[资源位置](https://zh.minecraft.wiki/w/Tutorial:%E5%88%B6%E4%BD%9C%E8%B5%84%E6%BA%90%E5%8C%85/%E6%A8%A1%E5%9E%8B/#%E6%96%87%E4%BB%B6%E8%B7%AF%E5%BE%84)

`parent` 字段不仅可以引用原版 Minecraft 提供的默认模型，还可以指向你的自定义模型。你可以在这个[网站](https://misode.github.io/assets/model/)上查看所有可用的 Minecraft 模型

```yaml
items#test:
  default:big_apple:
    material: apple
    custom-model-data: 1000
    model:
      type: minecraft:model
      path: "minecraft:item/custom/big_apple"
      generation:
        parent: "minecraft:item/apple" # 继承苹果的模型
        # 在GUI界面中显示一个大苹果
        display:
          gui:
            scale: 2,2,2
  default:big_big_apple:
    material: apple
    custom-model-data: 1001
    model:
      type: minecraft:model
      path: "namespace:item/custom/big_big_apple"
      generation:
        # 继承上述自定义的大苹果模型
        parent: "minecraft:item/custom/big_apple"
        # 现在它在手持和GUI界面上都会非常大。
        display:
          firstperson_righthand:
            scale: 4,4,4
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fto4U9vBexccrrEoONGwg%252Fimage.png%3Falt%3Dmedia%26token%3Deabaf9a9-a8d6-45a9-bf90-b15ed1b917ad\&width=768\&dpr=4\&quality=100\&sign=18696418\&sv=2)大苹果

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FdFCvFSb48gXkn8JCLPCF%252Fimage.png%3Falt%3Dmedia%26token%3D34b110c6-34e5-40d3-9772-fec90a2d0903\&width=768\&dpr=4\&quality=100\&sign=7bc1abe6\&sv=2)大大苹果

# 纹理 <a href="#textures" id="textures"></a>

> Holds the textures of the model, in form of a [resource location](https://minecraft.wiki/w/Tutorial:Models#File_path) or can be another texture variable.
> 存储模型所需的纹理资源，支持[资源位置](https://zh.minecraft.wiki/w/Tutorial:%E5%88%B6%E4%BD%9C%E8%B5%84%E6%BA%90%E5%8C%85/%E6%A8%A1%E5%9E%8B/#%E6%96%87%E4%BB%B6%E8%B7%AF%E5%BE%84)和其他已定义的纹理变量两种形式。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F7Av9LqhtMmYcb2pFXS9X%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=99c63916\&sv=2)

如果打算基于此模型生成一个方块， `parent` 和 `textures` 的参数应按如下指定：

```yaml
generation:
  parent: "minecraft:block/cube_all"
  textures:
    "particle": "minecraft:block/custom/block_particle"
    "down": "minecraft:block/custom/block_down"
    "up": "minecraft:block/custom/block_up"
    "north": "minecraft:block/custom/block_north"
    "east": "minecraft:block/custom/block_east"
    "south": "minecraft:block/custom/block_south"
    "west": "minecraft:block/custom/block_west"
```

```yaml
items#test:
  default:big_apple:
    material: apple
    custom-model-data: 1000
    model:
      type: minecraft:model
      path: "minecraft:item/custom/big_apple"
      generation:
        parent: "minecraft:item/apple"
        textures:
          # 用斧头替换苹果的纹理
          layer0: minecraft:item/custom/topaz_axe
        display:
          gui:
            scale: 2,2,2
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FUwVKVhbAtn1FNPStu82a%252Fimage.png%3Falt%3Dmedia%26token%3D89a11095-54ab-4f07-82fe-b36c61c30bf0\&width=768\&dpr=4\&quality=100\&sign=a3d69454\&sv=2)

`textures` 部分下的键值对由父模型决定。

例如：

* `minecraft:item/apple` 继承 `minecraft:item/generated`。
* `layer0` 是 `minecraft:item/generated` 中定义的 `textures` 参数之一。
* 这就是为什么你可以在子模型（`apple`）中覆盖这个纹理。

**You can view all available Minecraft models and their textures on this** [**website**](https://misode.github.io/assets/model/)
**你可以在这个[**网站**](https://misode.github.io/assets/model/)上找到所有可用的 Minecraft 模型及其纹理**

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FsYTMHVsoTPN2uOsYs9hZ%252Fimage.png%3Falt%3Dmedia%26token%3De4496f8f-6daa-4da2-a407-89a9444807d0\&width=300\&dpr=4\&quality=100\&sign=fbaab065\&sv=2)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F0s9Mqk0BpqkZj48WC3mQ%252Fimage.png%3Falt%3Dmedia%26token%3D15b290f8-f945-4384-944a-fb27ec0de698\&width=300\&dpr=4\&quality=100\&sign=c50330a0\&sv=2)

# GUI 光照 <a href="#gui-light" id="gui-light"></a>

> 可以是 `"front"` 或者 `"side"`。如果设置为 `"side"`，模型会像方块一样渲染。如果设置为 `"front"`，模型会像平面物品一样显示。默认为 `"side"`。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FSHZtI9R1FFXQulE7pVmM%252Fimage.png%3Falt%3Dmedia%26token%3D5d351073-450f-48cb-945a-a9e72401bfb3\&width=768\&dpr=4\&quality=100\&sign=befd1e70\&sv=2)左图：front 右图：side

# 显示 <a href="#display" id="display"></a>

> Holds the different places where item models are displayed.
>
> * rotation: 根据坐标系 `[x, y, z]` 指定模型的旋转。
> * translation: 根据坐标系 `[x, y, z]` 指定模型的位置。若值大于 80，则显示为 80。若值小于 -80，则显示为 -80。
> * scale: 根据坐标系 `[x, y, z]` 指定模型的缩放比例。若值大于 4，则显示为 4。

可用值：`thirdperson_righthand`、`thirdperson_lefthand`、`firstperson_righthand`、`firstperson_lefthand`、`gui`、`head`、`ground` 或 `fixed`。

继续**大大苹果**的例子。你可能会注意到，当它用右手拿着时，它的旋转是不太正确的。这是因为我们覆盖了其父模型的 `display.firstperson_righthand` 设置。现在，让我们来修复它！

```yaml
generation:
  parent: "minecraft:item/custom/big_apple"
  display:
    firstperson_righthand:
      scale: 4,4,4
      rotation: 0,-90,25
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FDTJGNCHXveVe5Rb4Z9PQ%252Fimage.png%3Falt%3Dmedia%26token%3Df6d88f18-0cad-429f-ad63-eb5808c06a42\&width=768\&dpr=4\&quality=100\&sign=b97cc872\&sv=2)
