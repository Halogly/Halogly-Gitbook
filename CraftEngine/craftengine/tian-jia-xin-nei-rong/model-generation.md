---
description: This page mainly explains how to use model generation.
---

# 🏭️ Model Generation

### Introduction <a href="#introduction" id="introduction"></a>

[🏭️ Model Generation](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/model-generation) is acting a role to create a model in YAML format.

When configuring multiple similar models (e.g., 16 wool-colored sofas that only differ in textures), you would normally need to create an equal number of separate models. However, with Model Generation, you can easily manage these model inheritance relationships using YAML format.

The path specified in the `path` option (located in the same configuration section as `generation`) must point to a non-existent model path! Otherwise, it will conflict with your existing models.

Model generation is **always an optional** configuration. If you already have a dedicated JSON model file for that block/item, you **do not need** to use `generation`—simply specify the model path using `path` instead.

### Where to Configure <a href="#where-to-configure" id="where-to-configure"></a>

If you observe carefully, you'll notice that the plugin uses the following configuration format in many places.

Copy

```
path: "xxx:xxx"
generation:
  parent: "minecraft:xxx/xxx"
  textures:
    "xxx": "xxx:xxx"
```

In fact, the plugin supports model generation wherever a model path (`path`) can be specified. Whenever you see `path`, it means you can use `generation` within the same configuration section.

### Arguments <a href="#arguments" id="arguments"></a>

#### parent <a href="#parent" id="parent"></a>

> Loads a different model from the given path, in form of a [resource location](https://minecraft.wiki/w/Tutorial:Models#File_path)

The `parent` field can not only reference the default models provided by vanilla Minecraft but can also point to your custom models. You can view all available Minecraft models on this [website](https://misode.github.io/assets/model/)

Copy

```
items#test:
  default:big_apple:
    material: apple
    custom-model-data: 1000
    model:
      type: minecraft:model
      path: "minecraft:item/custom/big_apple"
      generation:
        parent: "minecraft:item/apple" # inherits apple's model
        # displays a big apple in gui
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
        # inherits the custom big apple model above
        parent: "minecraft:item/custom/big_apple"
        # now it would be very big both in hand and in gui
        display:
          firstperson_righthand:
            scale: 4,4,4
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fto4U9vBexccrrEoONGwg%252Fimage.png%3Falt%3Dmedia%26token%3Deabaf9a9-a8d6-45a9-bf90-b15ed1b917ad\&width=768\&dpr=4\&quality=100\&sign=18696418\&sv=2)big apple

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FdFCvFSb48gXkn8JCLPCF%252Fimage.png%3Falt%3Dmedia%26token%3D34b110c6-34e5-40d3-9772-fec90a2d0903\&width=768\&dpr=4\&quality=100\&sign=7bc1abe6\&sv=2)big big apple

#### textures <a href="#textures" id="textures"></a>

> Holds the textures of the model, in form of a [resource location](https://minecraft.wiki/w/Tutorial:Models#File_path) or can be another texture variable.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F7Av9LqhtMmYcb2pFXS9X%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=99c63916\&sv=2)

If we intend to generate a block based on this model, the parameters for `parent` and `textures` should be specified as follows:

Copy

```
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

Copy

```
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
          # replace the apple's texture with an axe
          layer0: minecraft:item/custom/topaz_axe 
        display:
          gui:
            scale: 2,2,2
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FUwVKVhbAtn1FNPStu82a%252Fimage.png%3Falt%3Dmedia%26token%3D89a11095-54ab-4f07-82fe-b36c61c30bf0\&width=768\&dpr=4\&quality=100\&sign=a3d69454\&sv=2)

The key-value pairs under the `textures` section are determined by the parent model.

For example:

* `minecraft:item/apple` inherits from `minecraft:item/generated`.
* `layer0` is one of the `textures` parameters defined in `minecraft:item/generated`.
* This is why you can override this texture in the child model (`apple`).

**You can view all available Minecraft models and their textures on this** [**website**](https://misode.github.io/assets/model/)

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FsYTMHVsoTPN2uOsYs9hZ%252Fimage.png%3Falt%3Dmedia%26token%3De4496f8f-6daa-4da2-a407-89a9444807d0\&width=300\&dpr=4\&quality=100\&sign=fbaab065\&sv=2)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F0s9Mqk0BpqkZj48WC3mQ%252Fimage.png%3Falt%3Dmedia%26token%3D15b290f8-f945-4384-944a-fb27ec0de698\&width=300\&dpr=4\&quality=100\&sign=c50330a0\&sv=2)

#### gui-light <a href="#gui-light" id="gui-light"></a>

> Can be `"front"` or `"side"`. If set to `"side"`, the model is rendered like a block. If set to `"front"`, model is shaded like a flat item. Defaults to `"side"`.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FSHZtI9R1FFXQulE7pVmM%252Fimage.png%3Falt%3Dmedia%26token%3D5d351073-450f-48cb-945a-a9e72401bfb3\&width=768\&dpr=4\&quality=100\&sign=befd1e70\&sv=2)left: front right: side

#### display <a href="#display" id="display"></a>

> Holds the different places where item models are displayed.
>
> * rotation: Specifies the rotation of the model according to the scheme `[x, y, z]`.
> * translation: Specifies the position of the model according to the scheme `[x, y, z]`. If the value is greater than 80, it is displayed as 80. If the value is less than -80, it is displayed as -80.
> * scale: Specifies the scale of the model according to the scheme `[x, y, z]`. If the value is greater than 4, it is displayed as 4.

Available values: `thirdperson_righthand`, `thirdperson_lefthand`, `firstperson_righthand`, `firstperson_lefthand`, `gui`, `head`, `ground`, or `fixed`.

Let's continue with this **big big apple** example. You may notice that when held in the right hand, its rotation behaves incorrectly. This happens because we overrode its parent model's `display.firstperson_righthand` settings. Now, let's fix it!

Copy

```
generation:
  parent: "minecraft:item/custom/big_apple"
  display:
    firstperson_righthand:
      scale: 4,4,4
      rotation: 0,-90,25
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FDTJGNCHXveVe5Rb4Z9PQ%252Fimage.png%3Falt%3Dmedia%26token%3Df6d88f18-0cad-429f-ad63-eb5808c06a42\&width=768\&dpr=4\&quality=100\&sign=b97cc872\&sv=2)
