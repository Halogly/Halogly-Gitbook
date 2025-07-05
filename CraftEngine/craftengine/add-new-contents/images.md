---
description: 本页面主要讲解如何将图片添加到服务器。
---

# 🖼️ 图片

## 🖼️ 图片

如果你不知道位图图片的原理，请先阅读 (Minecraft Wiki)\[https://zh.minecraft.wiki/w/自定义字体#bitmap]。

## 介绍 <a href="#introduction" id="introduction"></a>

从本质上讲，Minecraft 的“图片显示”就是用图片替换字符。通过自身的字体系统将特定的 Unicode 字符渲染为图片。

**字体生态系统要点**

1. **多字体集** Minecraft 原生支持多种字体（例如 `minecraft:default`，`minecraft:uniform`），可以扩展或修改。
2. **自定义字体创建** 你可以通过定义以下内容创建个性化字体：

```yaml
assets/[命名空间]/font/[字体名称].json
```

* `namespace`：唯一标识符（例如，`wo_de_ming_ming_kong_jian`）
* `font_name`：自定义字体名称（例如，`hao_kan_de_zi_ti`）

MiniMessage 格式： `<font:命名空间:字体名称>我是文本</font>`

MineDown 格式：`[我是文本](font=命名空间:字体名称)`

**运作方式**

* 当使用 `\uXXXX` Unicode 转义序列时：
  1. 游戏检查文本组件中使用的字体
  2. 将字符映射到相应的纹理
  3. 在指定的字符位置渲染纹理

**提问：**

我的国家的字符会受到影响吗？我的玩家能否通过聊天、铁砧或其他不太寻常的方式使用这些图片？

**回答：**

当然不会，除非你使用 `minecraft:default`（Minecraft 的默认字体）。请避免使用 `minecraft:default`，因为它的行为不受支持。

## 单字符位图 <a href="#single-character-bitmap" id="single-character-bitmap"></a>

```yaml
images:
  internal:item_browser:
    height: 140
    ascent: 18
    font: minecraft:internal
    file: minecraft:font/gui/custom/item_browser.png
    char: '\ub000'
```

`height` 值必须始终大于或等于 `ascent` 值。这是 Minecraft 的强制要求，你必须遵守此规则。

## 多字符位图 <a href="#multiple-characters-bitmap" id="multiple-characters-bitmap"></a>

```yaml
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

如果你想学习如何使用 PlaceholderAPI 来整合这些图片，请参阅以下页面：[🅿️ PlaceholderAPI](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/placeholderapi)。

如果你对如何在 CraftEngine 插件中使用这些图片感兴趣，请查阅[✏️ 文本格式](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format)。

## 预览游戏中的图片 <a href="#preview-the-image-in-game" id="preview-the-image-in-game"></a>

你可以使用一个非常简单的命令来预览图片的效果。你只需要将 `\ub000` 替换为与你图片对应的字符即可。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FX9GiJ4F4kOgPxWRoKenJ%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b85a884\&sv=2)

```
/tellraw @p {"text":"\ub000","font":"minecraft:icons"}
```

## 与其他插件的兼容性 <a href="#compatibility-with-other-plugins" id="compatibility-with-other-plugins"></a>

在其它插件中使用图片有两种办法：

1. 使用支持 **MiniMessage/MineDown** 和 **PlaceholderAPI** 的插件。这样你就只需要使用相应的占位符即可。请参阅[🅿️ PlaceholderAPI](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/placeholderapi)了解如何使用占位符。
2. 使用与[✏️ 文本格式](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format)中类似的 `<image:命名空间:id>` `<image:命名空间:id:行:列>` `<shift:-20>` 格式的标签。CraftEngine 会在**网络传输的数据包**中将这些标签替换为相应字体的字符。

你可以在 config.yml 中找到以下配置，它控制这些标签生效的范围。

```yaml
image:
  # 通过拦截数据包，就可以在其他插件中使用 <image:...> <shift:...>
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
