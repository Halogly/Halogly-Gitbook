---
description: 如何解决文件冲突
---

# ⚔️ 文件冲突

## 👋 简介 <a href="#introduction" id="introduction"></a>

在合并多个资源包时，我们经常会遇到文件冲突，例如pack.png、sounds.json等。将它们配置成一个文件可能会相当繁琐。因此，我们增加了一个解决冲突问题的功能，可以自定义解决冲突的方案。当插件检测到冲突的文件时，它会搜索第一个满足条件的解决方案。如果没有找到合适的解决方案，它会在控制台中输出警告。

冲突解决的配置位于 `config.yml` 文件下的 `resource-pack.duplicated-files-handler` 部分。

插件不支持着色器合并，因为这样做会影响稳定性。

```yaml
duplicated-files-handler:
  # 处理物品模型
  - term:
      type: any_of
      terms:
        - type: parent_path_suffix
          suffix: "minecraft/items" # 1.21.4+
        - type: parent_path_suffix
          suffix: "minecraft/models/item" # 1.20-1.21.3
    resolution:
      type: merge_json
      deeply: true
  # 处理pack.mcmeta
  - term:
      type: exact
      path: "pack.mcmeta"
    resolution:
      type: merge_pack_mcmeta
      description: "<gray>CraftEngine 资源包"
  # 处理pack.png
  - term:
      type: exact
      path: "pack.png"
    resolution:
      type: retain_matching
      term:
        type: contains
        path: "resources/default/resourcepack"
  # 处理sounds.json
  - term:
      type: filename
      name: "sounds.json"
    resolution:
      type: merge_json
      deeply: false
```

你可以简单地理解为：**术语**决定匹配规则，**方案**决定如何处理冲突文件。以下是可用的匹配方法和解决方案选项：

## 🔢 匹配规则 <a href="#matching-rule" id="matching-rule"></a>

### all\_of <a href="#all_of" id="all_of"></a>

所有条件都必须满足。

```yaml
type: all_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

### any\_of <a href="#any_of" id="any_of"></a>

满足其中任意一个条件。

```yaml
type: any_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

### inverted <a href="#inverted" id="inverted"></a>

否定当前条件的计算结果。

```yaml
type: inverted
term:
  type: xxx
```

### filename <a href="#filename" id="filename"></a>

匹配文件名。

```yaml
type: filename
name: "sounds.json"
```

### exact <a href="#exact" id="exact"></a>

匹配路径。

```yaml
type: exact
path: "assets/minecraft/lang/en_us.json"

type: exact
path: "pack.mcmeta"
```

### parent\_path\_prefix / parent\_path\_suffix <a href="#parent_path_prefix-parent_path_suffix" id="parent_path_prefix-parent_path_suffix"></a>

检测路径是否具有特定前缀或后缀。

```yaml
type: parent_path_prefix 
path: "assets/minecraft"

type: parent_path_suffix
path: "minecraft/models/item"
```

### contains <a href="#contains" id="contains"></a>

检测路径是否包含特定字符。

```yaml
type: contains
path: "custom/furniture"
```

### pattern <a href="#pattern" id="pattern"></a>

使用正则表达式匹配路径。

```yaml
type: pattern
pattern: "Regex Here"
```

## 🧑‍💻 方案 <a href="#resolution" id="resolution"></a>

### merge\_json <a href="#merge_json" id="merge_json"></a>

将两个json文件合并为一个。

```yaml
type: merge_json
deeply: true
```

### retain\_matching <a href="#retain_matching" id="retain_matching"></a>

当两个文件冲突时，保留符合指定条件的那一个。

```yaml
type: retain_matching
term:
  type: contains
  path: "resources/default/resourcepack"
```

### conditional <a href="#conditional" id="conditional"></a>

执行条件方案。

```yaml
type: conditional
term:
  type: xxx
resolution:
  type: xxx
```

### merge\_pack\_mcmeta <a href="#merge_pack_mcmeta" id="merge_pack_mcmeta"></a>

为 `pack.mcmeta` 定制特殊方案。

```yaml
type: "merge_pack_mcmeta"
description: "<gray>CraftEngine 资源包" # 资源包描述信息
```

### merge\_atlas <a href="#merge_atlas" id="merge_atlas"></a>

一个为 `atlases/xx.json` 定制的特殊方案。

```yaml
type: "merge_atlas"
```
