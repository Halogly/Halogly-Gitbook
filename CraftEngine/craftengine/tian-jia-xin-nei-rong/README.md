---
description: 本页面主要讲解如何管理自定义内容
---

# ➕️ 添加新内容

### 资源 <a href="#resources" id="resources"></a>

在插件的根目录（`plugins/CraftEngine/resources/`）中，所有包都储存在这里，这些包的名称是任意的。每个包由两个文件夹和一个 YAML 文件组成。两个文件夹分别管理配置信息和资源包，而 YAML 文件管理包的元数据。

```
plugins
  └ CraftEngine
     └ resources
         ├ pack_1
         ├ pack_2
         └ pack_3
            ├ configuration
            ├ resourcepack
            └ pack.yml
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fk0BUh80VNuR2bSJvfjhO%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=5412ebbb\&sv=2)

# 包元数据文件 <a href="#pack-meta-file" id="pack-meta-file"></a>

元数据文件是一个 YAML 格式的文档，记录包的基本信息。其中，最重要的是`namespace`命名空间。

```yaml
author: XiaoMoMi
version: 0.0.1
description: CraftEngine 的默认资源
namespace: default
enable: true # 设置为`false`禁用此包 
```
{% hint style="info" %}
命名空间的作用范围仅限于 YAML 层级结构中根节点下的二级节点，这里以“default:palm\_leaves”和“palm\_leaves”为例。只要在`pack.yml`中指定了命名空间，即使没有明确指定命名空间，也会使用默认的包命名空间。

```yaml
blocks:
  default:palm_leaves:
    behavior:
      type: leaves_block
```

等同于

```yaml
blocks:
  palm_leaves:
    behavior:
      type: leaves_block
```
{% endhint %}
### 配置 <a href="#configuration" id="configuration"></a>

```
plugins
  └ CraftEngine
     └ resources
         └ pack
            └ configuration
```

配置文件储存在上述目录中。配置文件支持 json 和 yml 格式。此外，你可以在配置目录下创建任意数量的子目录。
{% hint style="success" %}
在 YAML 文件配置中，以下格式是不允许的：

```yaml
items:
  default:topaz_helmet:
    template: default:topaz_armor
    arguments:
      part: helmet
      slot: head
items:
  default:topaz_boots:
    template: default:topaz_armor
    arguments:
      part: boots
      slot: feet
```

因此，你需要在配置节点名称后添加`# + 任意标识符`，这样就可以在单个 YAML 文件中配置同一类型的多个节点。

```yaml
items#0:
  default:topaz_helmet:
    template: default:topaz_armor
    arguments:
      part: helmet
      slot: head
items#1:
  default:topaz_boots:
    template: default:topaz_armor
    arguments:
      part: boots
      slot: feet
```
{% endhint %}
### 资源包 <a href="#resoucepack" id="resoucepack"></a>

```
plugins
  └ CraftEngine
     └ resources
         └ pack
            └ resourcepack
               ├ assets
               ├ overlay_folder
               ├ pack.mcmeta
               └ pack.png
```

请确保你的资源包目录结构符合上图所示，否则可能会导致一些合并问题。overlay\_folder、pack.mcmeta 和 pack.png 文件不是必须的。
