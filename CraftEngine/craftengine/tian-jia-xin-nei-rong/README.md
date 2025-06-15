---
description: This page mainly explains how to manage custom contents
---

# ➕️ 添加新内容

### Resources <a href="#resources" id="resources"></a>

In the root directory of the plugin (`plugins/CraftEngine/resources/`), all packages are stored, and the names of these packages are arbitrary. Each package consists of two folders and one YAML file. The folders contain configurations and resource packs respectively, while the YAML file holds the metadata for the package.

Copy

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

### Pack Meta File <a href="#pack-meta-file" id="pack-meta-file"></a>

The Meta File is a YAML document that records some fundamental information. Among its entries, the most significant is the `namespace`.

Copy

```
author: XiaoMoMi
version: 0.0.1
description: Default Assets for CraftEngine
namespace: default
enable: true # set `false` to disable this pack 
```

The effect of a namespace is confined to the second-level nodes under the root node in the YAML hierarchy, exemplified here by "default:palm\_leaves " and "palm\_leaves". Provided that a namespace is specified in `pack.yml`, if a namespace is not explicitly designated, the package namespace will be used by default.

Copy

```
blocks:
  default:palm_leaves:
    behavior:
      type: leaves_block
```

is equivalent to

Copy

```
blocks:
  palm_leaves:
    behavior:
      type: leaves_block
```

### Configuration <a href="#configuration" id="configuration"></a>

Copy

```
plugins
  └ CraftEngine
     └ resources
         └ pack
            └ configuration
```

The configuration files are stored in the following folder. The configuration file format supports both json and yml. Moreover, you can create as many subdirectories as you like under the configuration.

In YAML configuration, the following format is not allowed:

Copy

```
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

Therefore, you need to add `# + any identifier` after the configuration section name, which allows you to configure multiple sections of the same type within a single YAML file.

Copy

```
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

### ResoucePack <a href="#resoucepack" id="resoucepack"></a>

Copy

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

Please ensure that the directory structure of your resource pack is as shown in the figure below, otherwise, it may lead to some merging issues. The overlay\_folder, pack.mcmeta, and pack.png files are not mandatory.
