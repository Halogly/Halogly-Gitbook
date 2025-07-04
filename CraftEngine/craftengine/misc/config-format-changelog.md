# 📓 配置格式变更日志

# 0.0.18 <a href="#id-0.0.18" id="id-0.0.18"></a>

将 `tags` 移动到了 `settings`

**之前**

```yaml
default:palm_planks:
  material: paper
  custom-model-data: 1004
  tags:
    - "minecraft:planks"
    - "minecraft:wooden_tool_materials"
```

**之后**

```yaml
default:palm_planks:
  material: paper
  custom-model-data: 1004
  settings:
    tags:
      - "minecraft:planks"
      - "minecraft:wooden_tool_materials"
```

# 0.0.35 <a href="#id-0.0.35" id="id-0.0.35"></a>

重命名了切石机配方类型

**之前**

```yaml
type: stone_cutting
```

**之后**

```yaml
type: stonecutting
```

# 0.0.48 <a href="#id-0.0.48" id="id-0.0.48"></a>

在config.yml中将 `offset-characters` 移动到了 `image.offset-characters`

# 0.0.49 <a href="#id-0.0.49" id="id-0.0.49"></a>

修改了config.yml中无效家具的处理方式

```yaml
furniture:
  remove-invalid-furniture-on-chunk-load:
    enable: false
    list:
    - "xxx:invalid_furniture"
```

->

```yaml
furniture:
  handle-invalid-furniture-on-chunk-load:
    enable: true
    remove:
      - "default:table_lamp"
    convert:
      "default:wooden_chair": "default:bench"
```

重构了config.yml中主机的处理方式。请阅读此页面了解新的格式：

[🛜 主机](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/resource-pack/host)

# 0.0.57 <a href="#id-0.0.57" id="id-0.0.57"></a>

将模板参数格式从 `{parameter}` 改为了 `${parameter:-DEFAULT_VALUE}`