---
description: 本页面主要讲解如何将新模板添加到你的服务器。
---

# 📄 模板 \[必读]

{% hint style="danger" %}
以下内容适用于 CraftEngine 0.0.57 及以上版本。如果你更新到了 0.0.57 或更高版本，需要使用命令 `/ce debug migrate-templates` 迁移旧模板。
{% endhint %}

# 介绍 <a href="#introduction" id="introduction"></a>

该插件具有极高的自定义程度，但如果没有提供任何设置就无法配置它。即使是极其简短的选项也需要在你的 YAML 文件中占用一行。由于存在大量此类选项，配置文件可能会变得异常冗长。因此，该插件引入了模板系统，允许你定义一个基础模板，并使用参数和覆盖来填充或覆盖某些参数，从而显著简化流程并减少重复配置所花费的时间。

# 它是如何运作的？ <a href="#how-it-works" id="how-it-works"></a>

要配置模板，你需要在 YAML 文件中使用 `templates` 作为根键。`templates` 下的第一项是你的模板名称。在下面的示例中，模板的名称是**`namespace:my_first_template`**。在该名称以下的所有内容才是模板内容。

```yaml
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

可以观看这个小动画，了解插件是如何应用模板的：

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F0JyPNp4niJkzAGHID1Kv%252Ftemplate.gif%3Falt%3Dmedia%26token%3Dcfecd8c1-d494-407f-a5db-ba2cce189f13\&width=768\&dpr=4\&quality=100\&sign=2ad8ae14\&sv=2)
{% hint style="info" %}
`namespace:template_id` 是你模板的唯一标识符。在引用或调用此模板到其他地方时，必须使用这个标识符名称。
{% endhint %}
{% hint style="success" %}
`namespace:template_id` 以下的配置区域是完全可定制的，遵循 YAML 语法即可。你完全可以自由地根据自身需求进行自定义。
{% endhint %}

# 多模板 <a href="#multiple-templates" id="multiple-templates"></a>

你可以通过将 `template` 设置成列表来组合多个模板。

```yaml
items:
  craftengine:custom_item:
     template:
       - namespace:my_first_template
       - namespace:my_second_template
```
{% hint style="warning" %}
**注意：**如果两个模板设置相同，下面的模板会覆盖上面的模板。但如果设置的是列表，它们会合并成一个组合列表。
{% endhint %}
![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FWiQor59iwPiY7n185412%252Fmultiple.gif%3Falt%3Dmedia%26token%3Dac0c9ff6-d883-4666-81aa-2b279a56e6a2\&width=768\&dpr=4\&quality=100\&sign=51fb7ed3\&sv=2)

# 参数 <a href="#arguments" id="arguments"></a>

你可以在模板中使用 `${xxx}` 定义参数，例如 `${nutrition}` 或 `${saturation}`。然后，在调用模板时，使用 **`"arguments"`** 部分来设置参数值。示例：

```yaml
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
{% hint style="info" %}
如果你需要将花括号 `{}` 作为普通文本使用（而不是作为参数），只需用反斜杠进行转义，如 `\{` 或 `\}`。

`\${Hello world}`

`${a\{b\}c}`
{% endhint %}
{% hint style="success" %}
要设置参数的默认值，则要在参数名后添加 `:-`，例如：

* `${nutrition:-1}`
* `${saturation:-2.5d}`
* `${map:-{aa:bb,cc:ddd}}`
* `${string:-"1234"}`

默认值遵循 Minecraft 的 SNBT 格式（与在命令中指定 NBT 数据时使用的格式相同）。
{% endhint %}

# 覆盖 <a href="#overrides" id="overrides"></a>

完全覆盖指定配置路径中的所有内容——包括列表和映射。不进行合并，只是完全替换。

```yaml
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

# 合并 <a href="#merges" id="merges"></a>

Merges 会深度融合两个配置部分，包括所有列表——没有任何内容会遗漏掉。基本上，merges 功能几乎与多模板完全相同。

```yaml
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
