# 📓 配置格式变更日志

### 0.0.18 <a href="#id-0.0.18" id="id-0.0.18"></a>

Moved `tags`to `settings`  将 `tags` 移动到 `settings`

**before  之前**

Copy  复制

```
default:palm_planks:
  material: paper
  custom-model-data: 1004
  tags:
    - "minecraft:planks"
    - "minecraft:wooden_tool_materials"
```

**after  之后**

Copy  复制

```
default:palm_planks:
  material: paper
  custom-model-data: 1004
  settings:
    tags:
      - "minecraft:planks"
      - "minecraft:wooden_tool_materials"
```

### 0.0.35 <a href="#id-0.0.35" id="id-0.0.35"></a>

Renamed stonecutting recipe type\
重命名了石刻配方类型

**before  之前**

Copy  复制

```
type: stone_cutting
```

**after  之后**

Copy  复制

```
type: stonecutting
```

### 0.0.48 <a href="#id-0.0.48" id="id-0.0.48"></a>

Moved `offset-characters` to `image.offset-characters` in config.yml\
在 config.yml 中将 `offset-characters` 移至 `image.offset-characters`

### 0.0.49 <a href="#id-0.0.49" id="id-0.0.49"></a>

Changed how invalid furniture works in config.yml\
修改了 config.yml 中无效家具的处理方式

Copy  复制

```
furniture:
  remove-invalid-furniture-on-chunk-load:
    enable: false
    list:
    - "xxx:invalid_furniture"
```

->

Copy  复制

```
furniture:
  handle-invalid-furniture-on-chunk-load:
    enable: true
    remove:
      - "default:table_lamp"
    convert:
      "default:wooden_chair": "default:bench"
```

Refactored how host works in config.yml. Read this page for the new format:\
重构了 config.yml 中主机的处理方式。请阅读此页面了解新的格式：

[🛜 Host  🛜 主机](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/resource-pack/host)

### 0.0.57 <a href="#id-0.0.57" id="id-0.0.57"></a>

Changed the template argument format from `{parameter}` to `${parameter:-DEFAULT_VALUE}`\
将模板参数格式从 `{parameter}` 改为 `${parameter:-DEFAULT_VALUE}`
