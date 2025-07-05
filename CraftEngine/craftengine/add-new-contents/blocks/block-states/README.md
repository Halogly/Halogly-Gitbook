---
description: 本页面主要讲解如何向服务器添加新方块。
---

# 🔣 方块状态

## 🔣 方块状态

## 介绍 <a href="#introduction" id="introduction"></a>

在 Minecraft 中，每个方块会有一个或多个方块状态。例如，木头有朝向，或是树叶在离原木不同距离下有不同的方块状态。这些状态决定了方块在游戏中的行为和外观。

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fu2u3K5ZjVw9Qf7gLcp3k%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=a04ecb9b\&sv=2)

## 示例 <a href="#examples" id="examples"></a>

这里有三个示例，展示如何在 Minecraft 中创建具有单一状态和具有多个状态的方块：

### **示例1：创建单一状态的方块** <a href="#example-1-creating-a-block-with-a-single-state" id="example-1-creating-a-block-with-a-single-state"></a>

```yaml
blocks:
  default:chinese_lantern:
    state:
      id: 15
      state: note_block:15
      model:
        path: "minecraft:block/custom/chinese_lantern"
        generation:
          parent: "minecraft:block/cube_column"
          textures:
            "end": "minecraft:block/custom/chinese_lantern_top"
            "side": "minecraft:block/custom/chinese_lantern"
```

**内部ID**（id）是方块的唯一标识符。内部ID的最大数值由两个因素决定：

1. **可用的方块外观状态**：需在 `mappings.yml` 文件中定义。对于单个方块类型，“定义”的方块状态越多，可用的外观状态数量就越多。
2. **额外注册的真实状态**：需在 `additional-real-blocks.yml` 文件中添加。此配置允许你手动为特定方块注册额外的真实服务端状态，从而进一步增加内部ID的总数。

**为什么注册额外的真实方块？** 一些方块（例如原版的树叶）具有比实际外观还要更多的方块状态。例如：

* **原版树叶**有**28个方块状态**（如距离、连接等属性），但只有2种不同的视觉外观（例如带水/不带水的橡树树叶）。
* 未使用的方块状态（例如28个中的26个）可以重新利用，用来创建**新的自定义块**（例如棕榈树叶等）。

**挑战**

创建一个具有独特功能的**新树叶类型**可能需要**28个服务端状态**，即使它只使用了**2种外观**。然而，原版树叶中只有**26个服务端真实状态**可用，因此会**缺少2个状态**。

**`state`** 指自定义方块状态使用的**原版方块状态外观**。 例如，**`noteblock:15`** 表示 `mappings.yml` 中定义的第16个音符方块状态（计数从0开始）。

如果你想要精确控制方块状态，可以这样配置：

```yaml
state: minecraft:note_block[instrument=hat,note=0,powered=false]
```

**模型选项**

**`model`** 指定方块使用的自定义模型的文件路径。

**生成选项**

**`generation`** 是**可选的**。如果你不确定这个选项的作用，请参阅：[🏭️ 模型生成](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/model-generation)

### **示例2：创建只有一个自定义属性的方块** <a href="#example-2-creating-a-block-with-one-custom-property" id="example-2-creating-a-block-with-one-custom-property"></a>

**对于具有多个状态的方块，请使用 `states` 而不是 `state`。**

```yaml
blocks:
  default:palm_log:
    states:
      properties:
        axis:
          type: axis
          default: y
      appearances:
        axisY:
          state: "note_block:0"
          model:
            path: "minecraft:block/custom/stripped_palm_log"
            generation:
              parent: "minecraft:block/cube_column"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisX:
          state: "note_block:1"
          model:
            x: 90
            y: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
        axisZ:
          state: "note_block:2"
          model:
            x: 90
            path: "minecraft:block/custom/stripped_palm_log_horizontal"
            generation:
              parent: "minecraft:block/cube_column_horizontal"
              textures:
                "end": "minecraft:block/custom/palm_log_top"
                "side": "minecraft:block/custom/palm_log"
      variants:
        axis=x:
          appearance: axisX
          id: 0
        axis=y:
          appearance: axisY
          id: 1
        axis=z:
          appearance: axisZ
          id: 2
```

**配置文件看起来可能会比较冗长复杂，但我们可以用模板来简化配置。** _(如果你还没阅读过模板教程，请在学习完 `states` 后务必前往学习！)_

我们把 `states` 分为三个关键部分，这样可以更清晰地理解：

**1. 定义方块属性**

定义决定方块行为或交互方式的**方块属性**（例如 `facing`，`level`，`lit`）。详情可参阅[🏷️ 属性](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states/properties)

```yaml
properties:
  axis:             # 属性名称（例如 axis，color）
    type: axis      # 数据类型（例如 axis，boolean，int，string）
    default: y      # 默认状态（例如 y 表示垂直方向）
```

**2. 配置外观**

外观定义使用的视觉状态。

```yaml
appearances:
  axisY:            # 唯一外观名称（例如 axisY，red）
    state: "note_block:0"  # 原版状态（例如 note_block:0）
    model:
      path: "minecraft:block/custom/stripped_palm_log"  # 模型文件的路径
      generation:   # （可选）程序化模型生成规则
        parent: "minecraft:block/cube_column"  # 基础模型模板
        textures:    # 覆盖父模型的纹理
          "end": "minecraft:block/custom/palm_log_top"
          "side": "minecraft:block/custom/palm_log"
```

**3. Map Variants**

变体将属性组合链接到特定的外观和内部ID。

```yaml
variants:
  axis=x:           # 属性条件（例如 axis=x，color=red）
    appearance: axisX  # 用于此变体的外观
    id: 0           # 唯一内部ID（每个变体必须唯一）
    settings:       # 可选设置覆盖
      ...
```

如果你不知道如何配置设置，请参阅[⚙️ 方块设置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-settings)

### **示例3：创建具有多个属性的方块** <a href="#example-3-creating-a-block-with-multiple-properties" id="example-3-creating-a-block-with-multiple-properties"></a>

如果觉得有点难懂，没事！在 Minecraft 中，**只有少数原版方块才会有很多的方块状态**，这就是为什么大多数自定义方块都是基于这些“状态丰富”的原版方块创建的。让我们一步步来。

```yaml
default:palm_leaves:
  states:
    properties:
      waterlogged:
        type: boolean
        default: false
      persistent:
        type: boolean
        default: true
      distance:
        type: int
        default: 7
        range: 1~7
    appearances:
      default:
        state: "oak_leaves[distance=1,persistent=false,waterlogged=false]"
        model:
          path: "minecraft:block/custom/palm_leaves"
          generation:
            parent: "minecraft:block/leaves"
            textures:
              "all": "minecraft:block/custom/palm_leaves"
      waterlogged:
        state: "oak_leaves[distance=1,persistent=false,waterlogged=true]"
        model:
          path: "minecraft:block/custom/palm_leaves"
    variants:
      distance=1,persistent=false,waterlogged=false:
        appearance: "default"
        id: "0"
      distance=2,persistent=false,waterlogged=false:
        appearance: "default"
        id: "1"
      distance=3,persistent=false,waterlogged=false:
        appearance: "default"
        id: "2"
      distance=4,persistent=false,waterlogged=false:
        appearance: "default"
        id: "3"
      distance=5,persistent=false,waterlogged=false:
        appearance: "default"
        id: "4"
      distance=6,persistent=false,waterlogged=false:
        appearance: "default"
        id: "5"
      distance=7,persistent=false,waterlogged=false:
        appearance: "default"
        id: "6"
        settings:
          is-randomly-ticking: true
      distance=1,persistent=true,waterlogged=false:
        appearance: "default"
        id: "7"
      distance=2,persistent=true,waterlogged=false:
        appearance: "default"
        id: "8"
      distance=3,persistent=true,waterlogged=false:
        appearance: "default"
        id: "9"
      distance=4,persistent=true,waterlogged=false:
        appearance: "default"
        id: "10"
      distance=5,persistent=true,waterlogged=false:
        appearance: "default"
        id: "11"
      distance=6,persistent=true,waterlogged=false:
        appearance: "default"
        id: "12"
      distance=7,persistent=true,waterlogged=false:
        appearance: "default"
        id: "13"
      distance=1,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "14"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=2,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "15"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=3,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "16"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=4,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "17"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=5,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "18"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=6,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "19"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=7,persistent=false,waterlogged=true:
        appearance: "waterlogged"
        id: "20"
        settings:
          resistance: 1200.0
          burnable: false
          is-randomly-ticking: true
          fluid-state: water
      distance=1,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "21"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=2,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "22"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=3,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "23"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=4,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "24"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=5,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "25"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=6,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "26"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
      distance=7,persistent=true,waterlogged=true:
        appearance: "waterlogged"
        id: "27"
        settings:
          resistance: 1200.0
          burnable: false
          fluid-state: water
```

**第一步：定义属性**

我们首先为方块声明三个属性，这些属性定义它的可能变体：

```yaml
properties:
  waterlogged:
    type: boolean
    default: false  # 方块是否含水
  persistent:
    type: boolean
    default: true   # 方块是否需要连接（例如，如果为 false，则树叶会枯萎）
  distance:
    type: int
    default: 7      # 与最近的原木的距离（1-7）
    min: 1
    max: 7
```

**总变体数**

这些属性的组合创建了**2 × 2 × 7 = 28个变体**：

* **`waterlogged`**：2个状态（`true`/`false`）。
* **`persistent`**：2个状态 (`true`/`false`）。
* **`distance`**：7个状态（值 `1` 到 `7`）。

**第二步：定义视觉状态**

尽管方块使用了**28种服务端状态**（`waterlogged`、`persistent` 和 `distance` 的组合），但我们只需要**两种外观**来显示它。以下是实现的方法：

```yaml
appearances:
  default:
    # （非含水）树叶
    state: "oak_leaves[distance=1,persistent=false,waterlogged=false]"
    model:
      path: "minecraft:block/custom/palm_leaves"
      generation:
        parent: "minecraft:block/leaves"  # 继承原版树叶模型
        textures:
          "all": "minecraft:block/custom/palm_leaves"  # 自定义纹理
  waterlogged:
    # 含水树叶
    state: "oak_leaves[distance=1,persistent=false,waterlogged=true]"
    model:
      path: "minecraft:block/custom/palm_leaves"  # 与默认模型相同
```

**第三步：分配内部ID和覆盖行为**

将所有可能的方块状态组合映射到**内部ID**和外观。某些变体需要覆盖原版行为（例如，含水方块完全免疫爆炸，`distance=7` 格方块外会触发 `randomTick`）。

**示例配置**

```yaml
variants:
  distance=1,persistent=false,waterlogged=false:
    appearance: "default"  # 树叶"默认"的视觉状态
    id: 0                  # 唯一内部ID
  distance=2,persistent=false,waterlogged=false:
    appearance: "default"  # 重新使用"默认"的视觉状态
    id: 1
```

**高级覆盖**

要为特定状态自定义方块行为，请添加如下逻辑：

```yaml
variants:
  distance=7,persistent=false,waterlogged=false:
    appearance: "default"
    id: "6"
    settings:
      is-randomly-ticking: true
  distance=7,persistent=true,waterlogged=true:
    appearance: "waterlogged"
    id: "27"
    settings:
      resistance: 1200.0
      burnable: false
```

## 方块模型 <a href="#block-models" id="block-models"></a>

```yaml
# 方块状态配置的一部分
state:
  id: 0
  state: tripwire:0
  models:
    - path: "minecraft:block/custom/fairy_flower_1"
      weight: 100
    - path: "minecraft:block/custom/fairy_flower_2"
      weight: 5
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_2"
    - path: "minecraft:block/custom/fairy_flower_3"
      weight: 5
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_3"
    - path: "minecraft:block/custom/fairy_flower_4"
      weight: 5
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_4"
    - path: "minecraft:block/custom/fairy_flower_5"
      weight: 1
      generation:
        parent: "minecraft:block/custom/fairy_flower_1"
        textures:
          "0": "minecraft:block/custom/fairy_flower_5"
```

方块模型支持多种模型，并且具有随机权重。使用时只需要将“model”改为“models”，并提供包含所有模型的列表即可。

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FwZsDZu6S6d2iyfANAoLl%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=c20975b\&sv=2)

```yaml
# 方块状态模板的一部分
appearances:
  axisY:
    state: "${base_block}:${vanilla_id}"
    model:
      path: "${model_vertical_path}"
      generation:
        parent: "minecraft:block/cube_column"
        textures:
          "end": "${texture_top_path}"
          "side": "${texture_side_path}"
  axisX:
    state: "${base_block}:${vanilla_id}"
    model:
      x: 90
      y: 90
      path: "${model_horizontal_path}"
      generation:
        parent: "minecraft:block/cube_column_horizontal"
        textures:
          "end": "${texture_top_path}"
          "side": "${texture_side_path}"
  axisZ:
    state: "${base_block}:${vanilla_id}"
    model:
      x: 90
      path: "${model_horizontal_path}"
      generation:
        parent: "minecraft:block/cube_column_horizontal"
        textures:
          "end": "${texture_top_path}"
          "side": "${texture_side_path}"
```

此外，你还可以使用 `x` 和 `y` 沿着x轴或y轴把模型旋转到一定角度。在这个示例中，插件实际上只使用了两个模型，而x轴和z轴的变体是通过旋转得来的。

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F0cprZp0jgclG0YVFJHgf%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=94ad4e60\&sv=2)
