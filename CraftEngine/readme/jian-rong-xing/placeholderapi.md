# 🅿️ PlaceholderAPI

### %image\_% <a href="#image" id="image"></a>

The `image` placeholder is used to return the original Unicode characters and their associated font for the image corresponding to a given ID.\
`image` 占位符用于返回给定 ID 对应图像的原始 Unicode 字符及其关联的字体。

Both "row" and "column" are optional, but when you use one of them, they must be used in pairs.\
"行"和"列"都是可选的，但当你使用其中一个时，它们必须成对使用。

#### %image\_mm\_namespace:id:\[row]:\[column]% %image\_mm\_namespace:id:\[行]:\[列]% <a href="#image_mm_namespace-id-row-column" id="image_mm_namespace-id-row-column"></a>

Return an image in `minimessage` format.\
以 `minimessage` 格式返回图像。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSoNyzs9VyYKmXS6gbzQD%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=c47b4dea\&sv=2)

#### %image\_md\_namespace:id:\[row]:\[column]% <a href="#image_md_namespace-id-row-column" id="image_md_namespace-id-row-column"></a>

Return an image in `minedown` format.\
返回 `minedown` 格式的图片。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSWKg5BjsPNE3WVBfnMB6%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=54cb343a\&sv=2)

#### %image\_raw\_namespace:id:\[row]:\[column]% <a href="#image_raw_namespace-id-row-column" id="image_raw_namespace-id-row-column"></a>

Return an the raw image character.\
返回原始图片字符。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F9WCfoMnR1xOkbdActj5Q%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=bdc70e04\&sv=2)

**Why placeholder doesn't work for some plugins?**\
**为什么某些插件占位符无法工作？**

First, you must ensure that the plugin responsible for parsing variables supports either the `MiniMessage` format or the `MineDown` format. Otherwise, the font cannot be properly applied to the text, resulting in the image not being displayed.\
首先，你必须确保负责解析变量的插件支持 `MiniMessage` 格式或 `MineDown` 格式。否则，字体无法正确应用于文本，导致图像无法显示。

If the plugin does not support it, be sure to ask their developers to add support, or find another plugin that supports custom fonts. The era of `&` is long over; please don't stay stuck in the Minecraft 1.15 days.re. [🖼️ Images](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/images)\
如果插件不支持，请务必询问其开发者添加支持，或寻找另一个支持自定义字体的插件。 `&` 的时代早已过去；请不要停留在 Minecraft 1.15 的时代。🖼️ 图像

_Currently, there are still a large number of plugins on the market that use the Bukkit API to create GUIs, which is a terrible practice. Even when they claim to support the MiniMessage format, they still process colors using the legacy colors. This is truly a shameful behavior!_\
&#xNAN;_&#x76EE;前，市场上仍有大量使用 Bukkit API 创建 GUI 的插件，这是一种糟糕的做法。即使他们声称支持 MiniMessage 格式，仍然使用传统颜色处理颜色。这真是可耻的行为！_

If there is no other way to ask the plugin to add font support, you can configure the `image` to use the `minecraft:default` font (since this is the default font, it will be used if no specific text font is specified).\
如果没有其他方法让插件添加字体支持，你可以配置 `image` 使用 `minecraft:default` 字体（因为这是默认字体，如果没有指定特定文本字体，它将被使用）。

**Using minecraft:default is always the worst solution. Please do not use it unless it is absolutely necessary. Perhaps you can consider the solution in the green tip below?**\
**使用 minecraft:default 永远是最糟糕的解决方案。除非绝对必要，否则请不要使用它。或许你可以考虑下面绿色提示中的解决方案？**

**Have you tried it?  你试过了吗？**

CraftEngine can modify text components sent by plugins that do not support fonts at **packet level**. Read this page for more: [Compatibility with Other Plugins](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/images#compatibility-with-other-plugins)\
CraftEngine 可以在数据包级别修改不支持字体的插件发送的文本组件。了解更多：与其他插件的兼容性

### %shift\_% <a href="#shift" id="shift"></a>

The `shift` placeholder is used to obtain the character for offset, typically employed for aligning menu titles and similar operations.\
`shift` 占位符用于获取偏移字符，通常用于对齐菜单标题和类似操作。

#### %shift\_mm\_value% <a href="#shift_mm_value" id="shift_mm_value"></a>

Return shift characters in `minimessage` format.\
以 `minimessage` 格式返回偏移字符。

#### %shift\_md\_value% <a href="#shift_md_value" id="shift_md_value"></a>

Return shift characters in `minedown` format.\
以 `minedown` 格式返回偏移字符。

#### %shift\_raw\_value% <a href="#shift_raw_value" id="shift_raw_value"></a>

Return raw shift characters\
返回原始偏移字符

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FpErqfau4KpSshwI7fAeD%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=3518b00e\&sv=2)with shift  加 Shift 键

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FwYlukrOaIpR8uLpkXi6E%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=61d5fcc7\&sv=2)without shift  不使用 shift
