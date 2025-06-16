# 🅿️ PlaceholderAPI

# %image\_% <a href="#image" id="image"></a>

`image` 占位符用于返回给定 ID 对应图像的原始 Unicode 字符及其关联的字体。

“行”和“列”都是可选的，但如果使用了其中一个，它们就必须成对使用。

# %image\_mm\_namespace:id:\[行]:\[列]% <a href="#image_mm_namespace-id-row-column" id="image_mm_namespace-id-row-column"></a>

返回 `minimessage` 格式的图片。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSoNyzs9VyYKmXS6gbzQD%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=c47b4dea\&sv=2)

# %image\_md\_namespace:id:\[行]:\[列]% <a href="#image_md_namespace-id-row-column" id="image_md_namespace-id-row-column"></a>

返回 `minedown` 格式的图片。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FSWKg5BjsPNE3WVBfnMB6%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=54cb343a\&sv=2)

# %image\_raw\_namespace:id:\[行]:\[列]% <a href="#image_raw_namespace-id-row-column" id="image_raw_namespace-id-row-column"></a>

返回原始图片字符。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F9WCfoMnR1xOkbdActj5Q%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=bdc70e04\&sv=2)

**为什么某些插件占位符无法运作？**

首先，你必须确保负责解析变量的插件支持 `MiniMessage` 格式或 `MineDown` 格式。否则，字体无法正确应用到文本上，会导致图像无法显示。

如果插件不支持，请务必询问插件的开发者添加支持，或寻找另一个支持自定义字体的插件。`&` 的时代早已过去；请不要停留在 Minecraft 1.15 的时代。[🖼️ 图像](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/images)

目前，市面上仍存在大量使用 Bukkit API 创建 GUI 的插件，这种方法太差了。虽然他们声称支持 MiniMessage 格式，但实际上仍然使用传统颜色来处理颜色。这真是太可耻了！_

If there is no other way to ask the plugin to add font support, you can configure the `image` to use the `minecraft:default` font (since this is the default font, it will be used if no specific text font is specified).\
如果没有其他办法让插件添加字体支持，你可以配置 `image` 使用 `minecraft:default` 字体（因为这是默认字体，如果没有指定特定的文本字体，它就会被使用）。

**使用 minecraft:default 永远是最差的解决方案。除非绝对必要，否则请不要使用它。或许你可以考虑下面绿色提示中的解决方案？**

**你试过了吗？**

CraftEngine 可以在**数据包级别**修改不支持字体的插件发送的文本组件。了解更多：[与其他插件的兼容性](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/images#compatibility-with-other-plugins)

# %shift\_% <a href="#shift" id="shift"></a>

`shift` 占位符用于偏移字符，通常用于对齐菜单标题和类似操作。

# %shift\_mm\_value% <a href="#shift_mm_value" id="shift_mm_value"></a>

返回 `minimessage` 格式的偏移字符。

# %shift\_md\_value% <a href="#shift_md_value" id="shift_md_value"></a>

返回 `minedown` 格式的偏移字符。

# %shift\_raw\_value% <a href="#shift_raw_value" id="shift_raw_value"></a>

返回原始偏移字符

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FpErqfau4KpSshwI7fAeD%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=3518b00e\&sv=2)偏移校正后

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FwYlukrOaIpR8uLpkXi6E%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=61d5fcc7\&sv=2)偏移校正前