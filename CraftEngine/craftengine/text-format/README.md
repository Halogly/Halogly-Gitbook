# ✏️ 文本格式

# MiniMessage <a href="#minimessage" id="minimessage"></a>

在配置插件的物品名称、描述信息、GUI等时，请使用[MiniMessage格式](https://docs.advntr.dev/minimessage/format.html)。

> 任何有意义的标记符都可以被转义。在纯文本中，可使用反斜杠（`\`）转义标签起始字符（`<`）。在带引号的字符串内，可对引号起始字符（`'` 或 `"`）转义。如果转义字符本身需要转义，也可以进行转义。未加引号的标签参数不能转义，用于简化设计。在不能转义的地方，转义字符会直接按原样传递。在可以转义但需要输出原义反斜杠的地方，可以通过转义转义字符本身来得到 `\`。

# 额外标签 <a href="#extra-tags" id="extra-tags"></a>

这是插件提供的额外标签。

`[_argument_]` 表示可选

你可以用 `'` 和 `"` 括住你的参数，例如 `<papi:'exp_multiplier':'1'>`

你也可以使用**嵌套**标签，例如 `<expr:'0.##':'<papi:exp_multiplier:1> * 10'>`

你会注意到有些标签以“**viewer\_**”开头。这是因为有时候一段文本可能由多个上下文实体构成。例如以下配置：

```yaml
message: -| 
  你好啊，<viewer_arg:player.name>。
  你有注意到<arg:player.name>与一个自定义方块交互了吗？
```

如果**玩家张三**与自定义方块交互并触发消息广播，那么收到这条消息的**玩家李四**会看到：`"你好啊，李四。你有注意到张三与一个自定义方块交互了吗？"`

## \<shift:\_偏移像素数\_> <a href="#less-than-shift-_pixels_greater-than" id="less-than-shift-_pixels_greater-than"></a>

`shift` 允许使用偏移字符。

```yaml
item-name: "<!i><shift:-100><#FF8C00>黄玉棒"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F3z6SBihmPpB19j9eenC2%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=a6c66a0e\&sv=2)

## \<papi:\_占位符\_:\[\_默认值\_]> <a href="#less-than-papi-_placeholder_-_default_value_-greater-than" id="less-than-papi-_placeholder_-_default_value_-greater-than"></a>

## \<viewer\_papi:\_占位符\_:\[\_默认值\_]> <a href="#less-than-viewer_papi-_placeholder_-_default_value_-greater-than" id="less-than-viewer_papi-_placeholder_-_default_value_-greater-than"></a>

## \<rel\_papi:\_占位符\_:\[\_默认值\_]> <a href="#less-than-rel_papi-_placeholder_-_default_value_-greater-than" id="less-than-rel_papi-_placeholder_-_default_value_-greater-than"></a>

`papi` 允许使用 `PlaceholderAPI` 的占位符。

```yaml
item-name: "<!i><#FF8C00><papi:player_name>的黄玉棒"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FygowY8l2F8zPS4Z2Ncl3%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=9f1f913c\&sv=2)

你还可以指定默认值，方便在更多地方使用而**不会导致出错**，例如：

```yaml
functions:
  - type: drop_exp
    count:
      type: uniform
      min: "<papi:exp_multiplier:1> * 3"
      max: "<papi:exp_multiplier:1> * 5"
```

**rel\_papi** 是关系型占位符。

## \<image:\_命名空间\_:\_id\_:\[\_行\_]:\[\_列\_]> <a href="#less-than-image-_namespace_-_id_-_row_-_column_-greater-than" id="less-than-image-_namespace_-_id_-_row_-_column_-greater-than"></a>

`image` 允许使用插件中注册的图片。

```yaml
item-name: "<!i><white><image:default:icons><#FF8C00> 黄玉棒"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Flhx8oEvcEEBsnCw4qMPB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=f5936846\&sv=2)

```yaml
item-name: "<!i><white><image:default:icons:0:1><#FF8C00> 黄玉棒"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FV2djYKHTMnBxFpZwuTWX%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=66a17118\&sv=2)

## \<i18n:\_id\_> <a href="#less-than-i18n-_id_greater-than" id="less-than-i18n-_id_greater-than"></a>

搜索适用于当前语言的翻译。

```yaml
internal:cooking_info:
  template: "internal:icon/2d"
  arguments:
    model_data: 1006
    texture: cooking_info
    name: "<!i><#FF8C00><i18n:internal.cooking_info>"
    lore:
      - "<!i><gray><i18n:internal.cooking_info.0>"
      - "<!i><gray><i18n:internal.cooking_info.1>"
```

## \<expr:\_格式\_:\_表达式\_> <a href="#less-than-expr-_format_-_expression_greater-than" id="less-than-expr-_format_-_expression_greater-than"></a>

执行一些数学运算。

```yaml
item-name: "<!i><#FF8C00><expr:0.##:'70 / 8'>"
```

```yaml
item-name: "<!i><#FF8C00><expr:0.##:'<papi:player_x> / 8'>"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FJVYm8tyyUtjNLBMVx02V%252Fimage.png%3Falt%3Dmedia%26token%3Da824c047-0f28-4a0c-a30d-0f9787c2b7fe\&width=768\&dpr=4\&quality=100\&sign=9537df0e\&sv=2)

> **实用链接**
> [https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html)
> 
> [https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)

## \<arg:\_索引\_> <a href="#less-than-arg-_index_greater-than" id="less-than-arg-_index_greater-than"></a>

仅用于 `translations` 下的文件，表示索引参数。

## \<arg:\_id\_> <a href="#less-than-arg-_id_greater-than" id="less-than-arg-_id_greater-than"></a>

## \<viewer\_arg:\_id\_> <a href="#less-than-viewer_arg-_id_greater-than" id="less-than-viewer_arg-_id_greater-than"></a>

这是一个命名参数。它的值可以来自两个地方：

1. **上下文特定参数** – 这些是在当前上下文中明确传递的参数。

```yaml
internal.cooking_info.0: "时间：<arg:cooking_time>刻"
internal.cooking_info.1: "经验值：<arg:cooking_experience>"
```

2. **常用参数**

```yaml
<arg:random>  # 生成一个介于 0 到 1 之间的随机数
<arg:last_random>  # 获取最后一个随机数
```

3. **上下文对象** - 如果上下文对象（例如玩家）提供参数。请前往下面的链接获取更多信息：

[🔗 链式参数](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments)

某些时候，多个**上下文对象**可能会共同存在。通过从不同的上下文对象访问参数，你可以精确控制函数的作用范围和行为。

```yaml
# 在方块的位置生成粒子
- type: particle
  x: '<arg:block.x> + 0.5'
  y: '<arg:block.y> + 0.5'
  z: '<arg:block.z> + 0.5'
  ...
# 在玩家的位置生成粒子
- type: particle
  x: '<arg:player.x>'
  y: '<arg:player.y>'
  z: '<arg:player.z>'
  ...
# 广播消息
- type: message
  target: 'all'
  message:
    - "你好啊<viewer_arg:player.name>！这条消息是来自<arg:player.name>的。"
    - "<arg:player.name>刚刚与<arg:block.owner>方块交互了以下！"
```

## \<global:\_id\_:\[参数...]> <a href="#less-than-global-_id_-args...-greater-than" id="less-than-global-_id_-args...-greater-than"></a>

用户定义的全局变量。

```yaml
item-name: "<global:rare_tag> 史诗级长矛"
```

[🔠 全局变量](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/global-variables)
