---
description: 本页面主要讲解如何管理自定义内容。
---

# ➕️ 添加新内容

## 资源 <a href="#resources" id="resources"></a>

在插件的根目录（`plugins/CraftEngine/resources/`）中，所有包都储存在这里，这些包的名称是任意的。每个包由两个文件夹和一个YAML文件组成。`configuration`管理配置信息，`resourcepack`存放资源包相关的资源，而YAML文件管理包的元数据。

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

### 包元数据文件 <a href="#pack-meta-file" id="pack-meta-file"></a>

元数据文件是一个YAML格式的文档，记录包的基本信息。其中，最重要的是`namespace`命名空间。

```yaml
author: XiaoMoMi
version: 0.0.1
description: CraftEngine的默认资源
namespace: default
enable: true # 设置为`false`禁用此包 
```

{% hint style="info" %}
命名空间的作用范围仅限于YAML层级结构中根节点下的二级节点，这里以“default:palm\_leaves”和“palm\_leaves”为例。只要在`pack.yml`中指定了命名空间，即使没有明确指定命名空间，也会使用默认的包命名空间。

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

配置文件储存在上述目录中。配置文件支持json和yml格式。此外，你可以在配置目录下创建任意数量的子目录。

{% hint style="success" %}
在YAML文件配置中，以下格式是不允许的：

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

因此，你需要在配置节点名称后添加`# + 任意标识符`，这样就可以在单个YAML文件中配置同一类型的多个节点。

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

## 资源包

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

请确保你的资源包目录结构符合上图所示，否则可能会导致一些合并问题。overlay\_folder、pack.mcmeta和pack.png文件不是必须的。

## 基于版本的配置

CraftEngine可以为不同的服务器版本添加基于版本的配置。只需在你的YAML文件中使用格式为`$$version`的键即可。

### 示例1：不同版本不同值

```yaml
# my_config.yml
settings:
  status:
    $$1.21.4: "enabled"
    $$1.20.1: "disabled"
  max_players:
    $$1.19: 50
    $$1.20~1.21.3: 80
    $$>=1.21.4: 100
  allowed_worlds:
    $$1.18: ["world", "world_nether"]
    $$fallback: ["default"]  # 若无版本匹配，则回退
```

### 示例2：合并配置

```yaml
# other_config.yml
server_properties:
  motd: "通用服务器"
  online_mode: true
  # 这是一个普通的映射，但包含了一个版本模块。
  # 这不是一个值选择器，因为它包含常规的键（motd，online_mode）  
  $$1.21.4:
    # 这部分会合并到server_properties中
    motd: "一个1.21.4版本的服务器！"  # 覆盖通用的motd
    new_feature_enabled: true  # 添加新键
```

## 调试

通过添加`debug`选项为该配置启用调试模式。

```yaml
items#0:
  default:topaz_helmet:
    debug: true
    template: default:topaz_armor
    arguments:
      part: helmet
      slot: head
```
