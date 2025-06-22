# 液体碰撞方块物品

与 `block_item` 不同，`liquid_collision_block_item` 会检测与液体的碰撞。它适用于创建可以放置在水或岩浆表面的方块。其他所有配置选项都与 `block_item` 完全相同。

```yaml
items:
  default:reed:
    material: paper
    behavior:
      type: liquid_collision_block_item
      offset-y: 1 # 放置方块的位置
      block: default:reed
```
