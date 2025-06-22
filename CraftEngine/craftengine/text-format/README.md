# 文本格式

### MiniMessage <a href="#minimessage" id="minimessage"></a>

When configuring item names, descriptions, GUIs, etc., for the plugin, please use the MiniMessage format. [https://docs.advntr.dev/minimessage/format.html](https://docs.advntr.dev/minimessage/format.html)\
在配置插件的物品名称、描述、GUI 等时，请使用 MiniMessage 格式。https://docs.advntr.dev/minimessage/format.html

> Any meaningful token can be escaped in the locations where they have influence. In plain text, tag open characters (`<`) can be escaped with a leading backslash (`\`). Within quoted strings, the opening quote character can be escaped (`'` or `"`). In either place, the escape character can be escaped in places where it would otherwise be relevant. Unquoted tag arguments cannot have escapes, for simplicity. In locations where escaping is not supported, the literal escape character will be passed through. In locations where escaping _is_ supported but a literal escape character is desired, the escape character can itself be escaped to produce a `\`.\
> 在任何有影响力的位置，任何有意义的标记都可以被转义。在纯文本中，标签开启字符（ `<` ）可以用一个开头的反斜杠（ `\` ）转义。在引号字符串中，引号开启字符可以被转义（ `'` 或 `"` ）。在任何位置，转义字符可以在它原本相关的地方被转义。未加引号的标签参数不能有转义，为了简化。在不能转义的位置，字面值的转义字符将被直接传递。在可以转义但希望传递字面值转义字符的位置，转义字符本身可以被转义来产生一个 `\` 。

### Extra Tags 额外标签 <a href="#extra-tags" id="extra-tags"></a>

These are additional tags provided by the plugin.\
这是插件提供的附加标签。

`[_argument_]` means Optional `[_argument_]` 表示可选

You can surround your arguments with `'` & `"` for instance `<papi:'exp_multiplier':'1'>`\
你可以用 `'` & `"` 包围你的参数，例如 `<papi:'exp_multiplier':'1'>`

You can also use **nested** tags for instance `<expr:'0.##':'<papi:exp_multiplier:1> * 10'>`\
你也可以使用嵌套标签，例如 `<expr:'0.##':'<papi:exp_multiplier:1> * 10'>`

You'll notice that some tags start with "**viewer\_**". This is because, in certain scenarios, a text might be constructed by multiple contextual entities. For example, consider the following configuration:\
你会注意到有些标签以"viewer\_"开头。这是因为在某些情况下，一段文本可能由多个上下文实体构建。例如，考虑以下配置：

Copy 复制

```
message: -| 
  Hi, <viewer_arg:player.name>. 
  Did you notice that <arg:player.name> interacted a custom block?
```

If **Player A** interacts with the custom block and triggers a message broadcast, then **Player B** receiving this message would see: `"Hi, B. Did you notice that A interacted a custom block?"`\
如果玩家 A 与自定义方块互动并触发消息广播，那么收到这条消息的玩家 B 会看到： `"Hi, B. Did you notice that A interacted a custom block?"`

#### \<shift:\_pixels\_> <a href="#less-than-shift-_pixels_greater-than" id="less-than-shift-_pixels_greater-than"></a>

`shift` allows you to directly use the plugin's offset characters.\
`shift` 允许你直接使用插件的偏移字符。

Copy 复制

```
item-name: "<!i><shift:-100><#FF8C00>Topaz Rod"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F3z6SBihmPpB19j9eenC2%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=a6c66a0e\&sv=2)

#### \<papi:\_placeholder\_:\[\_default\_value\_]> <a href="#less-than-papi-_placeholder_-_default_value_-greater-than" id="less-than-papi-_placeholder_-_default_value_-greater-than"></a>

#### \<viewer\_papi:\_placeholder\_:\[\_default\_value\_]> <a href="#less-than-viewer_papi-_placeholder_-_default_value_-greater-than" id="less-than-viewer_papi-_placeholder_-_default_value_-greater-than"></a>

#### \<rel\_papi:\_placeholder\_:\[\_default\_value\_]> <a href="#less-than-rel_papi-_placeholder_-_default_value_-greater-than" id="less-than-rel_papi-_placeholder_-_default_value_-greater-than"></a>

`papi` allows to use placeholders provided by `PlaceholderAPI`.\
`papi` 允许使用 `PlaceholderAPI` 提供的占位符。

Copy 复制

```
item-name: "<!i><#FF8C00><papi:player_name>'s Topaz Rod"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FygowY8l2F8zPS4Z2Ncl3%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=9f1f913c\&sv=2)

You can also specify a default value to make it available in more places **without causing errors** for example:\
您还可以指定默认值，以便在更多地方使用而不会导致错误，例如：

Copy 复制

```
functions:
  - type: drop_exp
    count:
      type: uniform
      min: "<papi:exp_multiplier:1> * 3"
      max: "<papi:exp_multiplier:1> * 5"
```

**rel\_papi** refers to relational placeholders\
rel\_papi 指的是关系型占位符

#### \<image:\_namespace\_:\_id\_:\[\_row\_]:\[\_column\_]> <a href="#less-than-image-_namespace_-_id_-_row_-_column_-greater-than" id="less-than-image-_namespace_-_id_-_row_-_column_-greater-than"></a>

`image` allows to use images registered in the plugin\
`image` 允许使用插件中注册的图片

Copy 复制

```
item-name: "<!i><white><image:default:icons><#FF8C00> Topaz Rod"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Flhx8oEvcEEBsnCw4qMPB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=f5936846\&sv=2)Copy 复制

```
item-name: "<!i><white><image:default:icons:0:1><#FF8C00> Topaz Rod"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FV2djYKHTMnBxFpZwuTWX%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=66a17118\&sv=2)

#### \<i18n:\_id\_> <a href="#less-than-i18n-_id_greater-than" id="less-than-i18n-_id_greater-than"></a>

Searching for translations applicable to the current language.\
正在搜索适用于当前语言的翻译。

Copy 复制

```
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

#### \<expr:\_format\_:\_expression\_> <a href="#less-than-expr-_format_-_expression_greater-than" id="less-than-expr-_format_-_expression_greater-than"></a>

Perform some math operations\
执行一些数学运算

Copy 复制

```
item-name: "<!i><#FF8C00><expr:0.##:'70 / 8'>"
```

Copy 复制

```
item-name: "<!i><#FF8C00><expr:0.##:'<papi:player_x> / 8'>"
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FJVYm8tyyUtjNLBMVx02V%252Fimage.png%3Falt%3Dmedia%26token%3Da824c047-0f28-4a0c-a30d-0f9787c2b7fe\&width=768\&dpr=4\&quality=100\&sign=9537df0e\&sv=2)

**Useful links 有用链接**

[https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/DecimalFormat.html)

[https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)

#### \<arg:\_index\_> <a href="#less-than-arg-_index_greater-than" id="less-than-arg-_index_greater-than"></a>

Only used for files under `translations`, representing indexed parameters.\
仅用于 `translations` 下的文件，表示索引参数。

#### \<arg:\_id\_> <a href="#less-than-arg-_id_greater-than" id="less-than-arg-_id_greater-than"></a>

#### \<viewer\_arg:\_id\_> <a href="#less-than-viewer_arg-_id_greater-than" id="less-than-viewer_arg-_id_greater-than"></a>

The is a named parameter. Its value can come from two possible sources:\
这是一个命名参数。它的值可以来自两个可能的来源：

1. **Context-specific arguments** – These are parameters explicitly passed in the current context.\
   上下文特定参数——这些是在当前上下文中明确传递的参数。

Copy 复制

```
internal.cooking_info.0: "Time: <arg:cooking_time>ticks"
internal.cooking_info.1: "Experience: <arg:cooking_experience>"
```

1. **Common arguments 常见参数**

Copy 复制

```
<arg:random>  # generates a random number between 0 and 1
<arg:last_random>  # gets the last random number
```

1. **Context subjects** – If the context subject (e.g., a player) provides parameters. Check this page for more:\
   上下文主题——如果上下文主题（例如，玩家）提供参数。请查看此页面获取更多信息：

[🔗 Chain Arguments 🔗 链式参数](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments)

In certain cases, multiple **context subjects** may coexist. By accessing parameters from different context subjects, you can precisely control the scope and behavior of functions.\
在某些情况下，多个上下文主题可能共存。通过从不同的上下文主题访问参数，您可以精确控制函数的作用范围和行为。

Copy 复制

```
# spawns the particle at the location of the block
- type: particle
  x: '<arg:block.x> + 0.5'
  y: '<arg:block.y> + 0.5'
  z: '<arg:block.z> + 0.5'
  ...
# spawns the particle at the location of the player
- type: particle
  x: '<arg:player.x>'
  y: '<arg:player.y>'
  z: '<arg:player.z>'
  ...
# broadcast the message
- type: message
  target: 'all'
  message:
    - "Hello <viewer_arg:player.name>! This message is from <arg:player.name>."
    - "<arg:player.name> just interacted a <arg:block.owner> block!"
```

#### \<global:\_id\_:\[args...]> <a href="#less-than-global-_id_-args...-greater-than" id="less-than-global-_id_-args...-greater-than"></a>

global variable defined by users\
用户定义的全局变量

Copy 复制

```
item-name: "<global:rare_tag> Rare spear"
```

[🔠 Global Variables 🔠 全局变量](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/global-variables)
