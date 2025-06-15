---
description: This page mainly explains how to add new templates to your server.
---

# 📄 Templates \[MUST READ]

The following content applies to CraftEngine 0.0.57 and above. If you update to version 0.0.57 or newer, you need to use the command `/ce debug migrate-templates` to migrate the old templates.

### Introduction <a href="#introduction" id="introduction"></a>

The plugin boasts an exceptionally high degree of customization, but it's impossible to configure it without providing any settings. Even a very brief option requires a line in your YAML file. With numerous such options, a configuration file can become excessively long. Therefore, the plugin has introduced a template system, allowing you to define a base template and use parameters and overrides to fill in or overwrite certain parameters, significantly simplifying the process and reducing the time spent on repetitive configurations.

### How it works? <a href="#how-it-works" id="how-it-works"></a>

To configure a template, you need to use `templates` as the root key in your YAML file. The first thing under `templates` is your template's name. In the example below, the template is called **`namespace:my_first_template`**. Everything under that name is the actual template content.

Copy

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

Check out this quick animation to see how the plugin applies the template:

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F0JyPNp4niJkzAGHID1Kv%252Ftemplate.gif%3Falt%3Dmedia%26token%3Dcfecd8c1-d494-407f-a5db-ba2cce189f13\&width=768\&dpr=4\&quality=100\&sign=2ad8ae14\&sv=2)

`namespace:template_id` serves as the unique identifier for your template. This name must be used whenever referencing or invoking this template elsewhere.

The configuration area under `namespace:template_id` is entirely customizable, as long as it adheres to YAML syntax. You have complete freedom to define it according to your needs.

### Multiple Templates <a href="#multiple-templates" id="multiple-templates"></a>

You can combine multiple templates by setting up the `template` as a list.

Copy

```
items:
  craftengine:custom_item:
     template:
       - namespace:my_first_template
       - namespace:my_second_template
```

**Heads up:** If two templates have the same setting, the one below will overwrite the one above. But if the setting is a list, they’ll merge into one combined list instead.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FWiQor59iwPiY7n185412%252Fmultiple.gif%3Falt%3Dmedia%26token%3Dac0c9ff6-d883-4666-81aa-2b279a56e6a2\&width=768\&dpr=4\&quality=100\&sign=51fb7ed3\&sv=2)

### Arguments <a href="#arguments" id="arguments"></a>

You can define parameters in template using `${xxx}`, like `${nutrition}` or `${saturation}`. Then, when calling the template, use the **`"arguments"`** section to set the parameter values. Here's a quick example:

Copy

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

If you need to use curly braces `{}` as normal text (not as parameters), just escape them with a backslash like `\{` or `\}`.

`\${Hello world}`

`${a\{b\}c}`

To set default values for parameters, add `:-` after the parameter name - for example:

* `${nutrition:-1}`
* `${saturation:-2.5d}`
* `${map:-{aa:bb,cc:ddd}}`
* `${string:-"1234"}`

The default values follow Minecraft's SNBT format (the same format used when specifying NBT data in commands).

### Overrides <a href="#overrides" id="overrides"></a>

Overrides completely replace whatever's in the specified config path—including lists and maps. No merging, just a full swap.

Copy

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

### Merges <a href="#merges" id="merges"></a>

Merges deeply combines two config sections, including all lists - nothing gets left behind. Basically, merges function almost exactly like multiple templates.

Copy

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
