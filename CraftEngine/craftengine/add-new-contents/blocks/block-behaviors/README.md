# 🕹️ 方块行为

CraftEngine 实现了一个全面的物理属性系统，可以自由组合多种方块行为！这里有两个简单的例子：

```yaml
# 单个行为
blocks:
  default:fairy_flower:
    behavior:
      type: bush_block
      bottom-block-tags:
        - minecraft:dirt
        - minecraft:farmland
```

```yaml
# 组合行为
blocks:
  default:gunpowder_block:
    behaviors:
      - type: concrete_powder_block
        solid-block: default:solid_gunpowder_block
      - type: falling_block
```

请注意：组合某些方块行为可能会导致意外的冲突。如果你遇到问题，请联系支持，我们会尽力解决任何冲突。
