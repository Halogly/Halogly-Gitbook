---
description: How to resolve file conflict 如何解决文件冲突
---

# ⚔️ 文件冲突

### 👋 Introduction  👋 简介 <a href="#introduction" id="introduction"></a>

When merging multiple resource packs, we often encounter conflicting files, such as pack.png, sounds.json, and so on. Configuring them into a single file can be quite tedious. Therefore, the plugin provides a conflict resolver that allows you to customize the solution for resolving conflicts. When the plugin detects conflicting files, it will search for the first solution that meets the conditions. If no suitable solution is found, it will issue a warning to the user in the console.\
在合并多个资源包时，我们经常遇到冲突文件，例如 pack.png、sounds.json 等。将它们配置成一个文件可能相当繁琐。因此，该插件提供了一个冲突解决器，允许您自定义解决冲突的方案。当插件检测到冲突文件时，它会搜索第一个满足条件的解决方案。如果没有找到合适的解决方案，它将在控制台中向用户发出警告。

The configuration for conflict resolution is located in the `config.yml` file under the section `resource-pack.duplicated-files-handler`.\
冲突解决的配置位于 `config.yml` 文件下的 `resource-pack.duplicated-files-handler` 部分。

The plugin does not support the merging of shaders, as it is considered unstable.\
插件不支持着色器合并，因为这被认为是不稳定的。

Copy  复制

```
duplicated-files-handler:
  # handle item models
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
  # handle pack.mcmeta
  - term:
      type: exact
      path: "pack.mcmeta"
    resolution:
      type: merge_pack_mcmeta
      description: "<gray>CraftEngine ResourcePack"
  # handle pack.png
  - term:
      type: exact
      path: "pack.png"
    resolution:
      type: retain_matching
      term:
        type: contains
        path: "resources/default/resourcepack"
  # handle sounds
  - term:
      type: filename
      name: "sounds.json"
    resolution:
      type: merge_json
      deeply: false
```

You can simply understand it as: **term** determines the matching rules, and **resolution** decides how to handle the conflicting files. Below are some available matching methods and resolution options:\
你可以简单地理解为：术语决定匹配规则，分辨率决定如何处理冲突文件。以下是可用的匹配方法和解决方案选项：

### 🔢 Matching Rule  🔢 匹配规则 <a href="#matching-rule" id="matching-rule"></a>

#### all\_of <a href="#all_of" id="all_of"></a>

All conditions must be satisfied.\
所有条件都必须满足。

Copy  复制

```
type: all_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

#### any\_of <a href="#any_of" id="any_of"></a>

Satisfy any one of the conditions.\
满足其中任意一个条件。

Copy  复制

```
type: any_of
terms:
  - type: xxx1
    aaa: bbb
  - type: xxx2
    ccc: ddd
```

#### inverted  反转 <a href="#inverted" id="inverted"></a>

Negate the result value of the current condition.\
否定当前条件的计算结果。

Copy  复制

```
type: inverted
term:
  type: xxx
```

#### filename  文件名 <a href="#filename" id="filename"></a>

Match the filename  匹配文件名

Copy  复制

```
type: filename
name: "sounds.json"
```

#### exact  精确 <a href="#exact" id="exact"></a>

Match the exact path  匹配精确路径

Copy  复制

```
type: exact
path: "assets/minecraft/lang/en_us.json"

type: exact
path: "pack.mcmeta"
```

#### parent\_path\_prefix / parent\_path\_suffix 父路径前缀 / 父路径后缀 <a href="#parent_path_prefix-parent_path_suffix" id="parent_path_prefix-parent_path_suffix"></a>

Detect whether a path has a specific prefix or suffix\
检测路径是否具有特定前缀或后缀

Copy  复制

```
type: parent_path_prefix 
path: "assets/minecraft"

type: parent_path_suffix
path: "minecraft/models/item"
```

#### contains <a href="#contains" id="contains"></a>

Check if the path contains the characters\
检查路径是否包含特定字符

Copy  复制

```
type: contains
path: "custom/furniture"
```

#### pattern  模式 <a href="#pattern" id="pattern"></a>

Use regex to match path\
使用正则表达式匹配路径

Copy  复制

```
type: pattern
pattern: "Regex Here"
```

### 🧑‍💻 Resolution  🧑‍💻 分辨率 <a href="#resolution" id="resolution"></a>

#### merge\_json  合并 json <a href="#merge_json" id="merge_json"></a>

Combine two json files into one\
将两个 json 文件合并为一个

Copy  复制

```
type: merge_json
deeply: true
```

#### retain\_matching <a href="#retain_matching" id="retain_matching"></a>

When two files conflict, keep the one that meets the specified condition.\
当两个文件冲突时，保留符合指定条件的那一个。

Copy  复制

```
type: retain_matching
term:
  type: contains
  path: "resources/default/resourcepack"
```

#### conditional  条件 <a href="#conditional" id="conditional"></a>

Run a conditional resolution\
执行条件解决

Copy  复制

```
type: conditional
term:
  type: xxx
resolution:
  type: xxx
```

#### merge\_pack\_mcmeta <a href="#merge_pack_mcmeta" id="merge_pack_mcmeta"></a>

A special resolution customized for `pack.mcmeta`\
为 `pack.mcmeta` 定制特殊解决

Copy  复制

```
type: "merge_pack_mcmeta"
description: "<gray>CraftEngine ResourcePack" # pack description
```

#### merge\_atlas <a href="#merge_atlas" id="merge_atlas"></a>

A special resolution customized for `atlases/xx.json`\
一个为 `atlases/xx.json` 定制的特别决议

Copy  复制

```
type: "merge_atlas"
```
