---
description: >-
  This page mainly explains how to add new templates to your server.
  本页面主要解释如何将新模板添加到您的服务器
---

# 📄 模 \[必读]

The following content applies to CraftEngine 0.0.57 and above. If you update to version 0.0.57 or newer, you need to use the command `/ce debug migrate-templates` to migrate the old templates.\
以下内容适用于 CraftEngine 0.0.57 及以上版本。如果您更新到 0.0.57 或更高版本，需要使用命令 `/ce debug migrate-templates` 迁移旧模板。

### Introduction  介绍 <a href="#introduction" id="introduction"></a>

The plugin boasts an exceptionally high degree of customization, but it's impossible to configure it without providing any settings. Even a very brief option requires a line in your YAML file. With numerous such options, a configuration file can become excessively long. Therefore, the plugin has introduced a template system, allowing you to define a base template and use parameters and overrides to fill in or overwrite certain parameters, significantly simplifying the process and reducing the time spent on repetitive configurations.\
该插件具有极高的自定义程度，但如果没有提供任何设置就无法配置它。即使是极其简短的选项也需要在您的 YAML 文件中占用一行。由于存在大量此类选项，配置文件可能会变得异常冗长。因此，该插件引入了模板系统，允许您定义一个基础模板，并使用参数和覆盖来填充或覆盖某些参数，从而显著简化流程并减少重复配置所花费的时间。

### How it works?  它是如何工作的？ <a href="#how-it-works" id="how-it-works"></a>

To configure a template, you need to use `templates` as the root key in your YAML file. The first thing under `templates` is your template's name. In the example below, the template is called **`namespace:my_first_template`**. Everything under that name is the actual template content.\
要配置模板，您需要在 YAML 文件中使用 `templates` 作为根键。 `templates` 下的第一项是您的模板名称。在下面的示例中，模板的名称是 **`namespace:my_first_template`** 。在该名称下的所有内容实际上是模板内容。

Copy  复制

```
templates:
  namespace:my_first_template:
    option_1: true
    option_2: false
    option_3: 
      - hello
    option_4: 20.25
    option_5:
      hello: world
```

Check out this quick animation to see how the plugin applies the template:\
查看这个快速动画，了解该插件如何应用模板：

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F0JyPNp4niJkzAGHID1Kv%252Ftemplate.gif%3Falt%3Dmedia%26token%3Dcfecd8c1-d494-407f-a5db-ba2cce189f13\&width=768\&dpr=4\&quality=100\&sign=2ad8ae14\&sv=2)

`namespace:template_id` serves as the unique identifier for your template. This name must be used whenever referencing or invoking this template elsewhere.\
`namespace:template_id` 作为您模板的唯一标识符。在引用或调用此模板的其他地方时，必须使用此名称。

The configuration area under `namespace:template_id` is entirely customizable, as long as it adheres to YAML syntax. You have complete freedom to define it according to your needs.\
`namespace:template_id` 下的配置区域完全是可定制的，只要它遵循 YAML 语法。您可以完全自由地根据您的需求来定义它。

### Multiple Templates  多个模板 <a href="#multiple-templates" id="multiple-templates"></a>

You can combine multiple templates by setting up the `template` as a list.\
您可以通过将 `template` 设置为列表来组合多个模板。

Copy  复制

```
items:
  craftengine:custom_item:
     template:
       - namespace:my_first_template
       - namespace:my_second_template
```

**Heads up:** If two templates have the same setting, the one below will overwrite the one above. But if the setting is a list, they’ll merge into one combined list instead.\
注意：如果两个模板设置相同，下面的模板会覆盖上面的模板。但如果设置是列表，它们会合并成一个组合列表。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FWiQor59iwPiY7n185412%252Fmultiple.gif%3Falt%3Dmedia%26token%3Dac0c9ff6-d883-4666-81aa-2b279a56e6a2\&width=768\&dpr=4\&quality=100\&sign=51fb7ed3\&sv=2)

### Arguments  参数 <a href="#arguments" id="arguments"></a>

You can define parameters in template using `${xxx}`, like `${nutrition}` or `${saturation}`. Then, when calling the template, use the **`"arguments"`** section to set the parameter values. Here's a quick example:\
您可以在模板中使用 `${xxx}` 定义参数，例如 `${nutrition}` 或 `${saturation}` 。 然后，在调用模板时，使用 **`"arguments"`** 部分来设置参数值。这里有一个快速示例：

Copy  复制

```
templates:
  craftengine:apple_template:
    material: apple
    data:
      food:
        nutrition: "${nutrition}"
        saturation: "${saturation}"
items:
  craftengine:custom_apple:
    template: craftengine:apple_template
    arguments:
      nutrition: 1
      saturation: 2.5
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FEBlTqSuHobBp0HHdAlwK%252Farguments.gif%3Falt%3Dmedia%26token%3D358280cf-c114-41f9-a715-93b6a0edc395\&width=768\&dpr=4\&quality=100\&sign=264d6527\&sv=2)

If you need to use curly braces `{}` as normal text (not as parameters), just escape them with a backslash like `\{` or `\}`.\
如果你需要将花括号 `{}` 作为普通文本使用（而不是作为参数），只需用反斜杠进行转义，如 `\{` 或 `\}` 。

`\${Hello world}`

`${a\{b\}c}`

To set default values for parameters, add `:-` after the parameter name - for example:\
为参数设置默认值，在参数名后添加 `:-` ，例如：

* `${nutrition:-1}`
* `${saturation:-2.5d}`
* `${map:-{aa:bb,cc:ddd}}`
* `${string:-"1234"}`

The default values follow Minecraft's SNBT format (the same format used when specifying NBT data in commands).\
默认值遵循 Minecraft 的 SNBT 格式（与在命令中指定 NBT 数据时使用的格式相同）。

### Overrides  覆盖 <a href="#overrides" id="overrides"></a>

Overrides completely replace whatever's in the specified config path—including lists and maps. No merging, just a full swap.\
完全覆盖指定配置路径中的所有内容——包括列表和映射。不进行合并，只是完全替换。

Copy  复制

```
items:
  craftengine:custom_bread:
    template: craftengine:apple_template
    arguments:
      nutrition: 1
      saturation: 2.5
    overrides:
      material: bread
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FVSIK99qhdnIUTu7ibtfg%252Foverrides.gif%3Falt%3Dmedia%26token%3Dbcdbc323-c3dc-4eb8-aa3e-233131894689\&width=768\&dpr=4\&quality=100\&sign=c50a7c9b\&sv=2)

### Merges  合并 <a href="#merges" id="merges"></a>

Merges deeply combines two config sections, including all lists - nothing gets left behind. Basically, merges function almost exactly like multiple templates.\
Merges 深度融合两个配置部分，包括所有列表——没有任何内容被遗漏。基本上，merges 功能几乎与多个模板完全相同。

Copy  复制

```
items:
  craftengine:custom_bread:
    template: craftengine:apple_template
    arguments:
      nutrition: 1
      saturation: 2.5
    merges:
      data:
        food:
          can-always-eat: true
```
