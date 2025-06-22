---
description: >-
  This page mainly explains how to add new images to your server.
  本页面主要解释如何将新图片添加到您的服务器。
---

# 🖼️ 图片

Please read Minecraft Wiki firstly if you don't know how bitmap images work [https://minecraft.wiki/w/Font#Bitmap\_provider](https://minecraft.wiki/w/Font#Bitmap_provider)\
如果您不知道位图图像的工作原理，请首先阅读 Minecraft Wiki。 https://minecraft.wiki/w/Font#Bitmap\_provider

### Introduction  介绍 <a href="#introduction" id="introduction"></a>

At its core, Minecraft's "image display" is essentially a clever character substitution mechanism. The game renders textures by mapping specific Unicode characters to image files through its font system.\
其核心，Minecraft 的"图像显示"本质上是一种巧妙的字符替换机制。游戏通过其字体系统将特定的 Unicode 字符映射到图像文件来渲染纹理。

**Font Ecosystem Essentials**\
**字体生态系统要点**

1. **Multiple Font Sets** Minecraft natively supports various fonts (e.g., `minecraft:default`, `minecraft:uniform`) that can be extended or modified.\
   多种字体集 Minecraft 原生支持多种字体（例如， `minecraft:default` ， `minecraft:uniform` ），可以扩展或修改。
2. **Custom Font Creation** Users can create personalized fonts by defining:\
   自定义字体创建 用户可以通过定义以下内容创建个性化字体：

Copy  复制

```
assets/[namespace]/font/[font_name].json
```

* `namespace`: Your unique identifier (e.g., `my_namespace`)\
  `namespace` : 您的独特标识符（例如， `my_namespace` ）
* `font_name`: Custom font designation (e.g., `magic_symbols`)\
  `font_name` : 自定义字体名称（例如， `magic_symbols` ）

MiniMessage format: `<font:namespace:font_name>Text</font>`   MiniMessage 格式： `<font:namespace:font_name>Text</font>`

MineDown format `[Text](font=namespace:font_name)`  MineDown 格式 `[Text](font=namespace:font_name)`

**How It Works  工作原理**

* When using `\uXXXX` Unicode escape sequences:\
  当使用 `\uXXXX` Unicode 转义序列时：
  1. The game checks the font used in the text component\
     游戏检查文本组件中使用的字体
  2. Maps characters to corresponding textures\
     将字符映射到相应的纹理
  3. Renders textures at specified character positions\
     在指定的字符位置渲染纹理

**Question:  问题：**

Will the characters in my country be affected? Can my players illegally use these images through chat, anvils, or other means?\
我的国家的角色会受影响吗？ 我的玩家能否通过聊天、重锤或其他方式非法使用这些图像？

**Answer:** Certainly not, unless you use `minecraft:default` (Minecraft's default font). Please avoid using `minecraft:default`, as it is an unsupported behavior.\
答案： 当然不会，除非你使用 `minecraft:default` （Minecraft 的默认字体）。请避免使用 `minecraft:default` ，因为它是一种不受支持的行为。

### Single Character Bitmap  单字符位图 <a href="#single-character-bitmap" id="single-character-bitmap"></a>

Copy  复制

```
images:
  internal:item_browser:
    height: 140
    ascent: 18
    font: minecraft:internal
    file: minecraft:font/gui/custom/item_browser.png
    char: '\ub000'
```

The `height` value must always be greater than or equal to the `ascent` value. This is a strict requirement enforced by Minecraft, and you must adhere to this rule.\
`height` 值必须始终大于或等于 `ascent` 值。这是 Minecraft 强制执行的严格要求，你必须遵守此规则。

### Multiple Characters Bitmap 多字符位图 <a href="#multiple-characters-bitmap" id="multiple-characters-bitmap"></a>

Copy  复制

```
images:
  default:icons:
    height: 10
    ascent: 9
    font: minecraft:icons
    file: minecraft:font/image/icons.png
    chars:
     - '\ub000\ub001'
     - '\ub002\ub003'
```

If you'd like to learn how to use PlaceholderAPI to incorporate these images, please refer to the following page: [🅿️ PlaceholderAPI](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/placeholderapi).\
如果你想学习如何使用 PlaceholderAPI 来整合这些图像，请参考以下页面：🅿️ PlaceholderAPI。

If you're interested in learning how to use these images within the CraftEngine plugin, please consult the detailed instructions available at: [✏️ Text Format](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format).\
如果你对如何在 CraftEngine 插件中使用这些图像感兴趣，请查阅在✏️ 文本格式处提供的详细说明。

### Preview the Image In Game 游戏内预览图像 <a href="#preview-the-image-in-game" id="preview-the-image-in-game"></a>

You can use a very simple command to preview the effect of the image. All you need to do is replace `\ub000` with the character corresponding to your image.\
你可以使用一个非常简单的命令来预览图像的效果。你只需要将 `\ub000` 替换为与你图像对应的字符即可。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FX9GiJ4F4kOgPxWRoKenJ%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b85a884\&sv=2)Copy  复制

```
/tellraw @p {"text":"\ub000","font":"minecraft:icons"}
```

### Compatibility with Other Plugins 与其他插件的兼容性 <a href="#compatibility-with-other-plugins" id="compatibility-with-other-plugins"></a>

There are two ways to use images in other plugins:\
在其它插件中使用图片有两种方法：

1. Use a plugin that supports **MiniMessage/MineDown** and **PlaceholderAPI**. In this case, you just need to use the corresponding placeholder. Please refer to this article to see how to use placeholder. [🅿️ PlaceholderAPI](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/placeholderapi)\
   使用支持 MiniMessage/MineDown 和 PlaceholderAPI 的插件。在这种情况下，您只需使用相应的占位符即可。请参考这篇文章了解如何使用占位符。 🅿️ PlaceholderAPI
2. Use a tag in the format of `<image:namespace:id>` `<image:namespace:id:row:column>` `<shift:-20>` just like what we do in [✏️ Text Format](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format). CraftEngine will replace these tags with characters of the corresponding font at the **packet level**.\
   使用与 ✏️ 文本格式中类似的 `<image:namespace:id>` `<image:namespace:id:row:column>` `<shift:-20>` 格式的标签。CraftEngine 将在数据包级别将这些标签替换为相应字体的字符。

You can find the following configuration in config.yml, which controls the scope in which these tags are effective.\
你可以在 config.yml 中找到以下配置，它控制了这些标签生效的范围。

Copy  复制

```
image:
  # By intercepting packets, you are allowed to use <image:...> <shift:...> in other plugins
  intercept-packets:
    system-chat: true
    tab-list: true
    actionbar: true
    title: true
    bossbar: true
    container: true
    team: true
    scoreboard: true
    entity-name: false
    text-display: true
```
