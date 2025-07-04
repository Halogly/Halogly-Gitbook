# 🏷️ 属性

请注意，无论属性类型如何，你都必须在合理范围内为每个属性配置一个默认值。

## 自定义属性 <a href="#custom-property" id="custom-property"></a>

### boolean <a href="#boolean" id="boolean"></a>

`boolean` 属性只有两个值：`true` 或 `false`。

```yaml
properties:
  happy:
    type: boolean
    default: false
```

### int <a href="#int" id="int"></a>

`int` 属性可以使用指定范围内的任何整数值。

```yaml
properties:
  mode:
    type: int
    default: 1
    range: 1~3
```

### string <a href="#string" id="string"></a>

`string` 属性只能从一组预定义的选项中获取值。

```yaml
properties:
  color:
    type: string
    default: red
    values:
      - read
      - green
      - blue
```

## 硬编码属性 <a href="#hard-coded-property" id="hard-coded-property"></a>

请注意，属性名称必须与示例相同才能生效

### facing <a href="#facing" id="facing"></a>

朝向的值可为 `east, south, west, north, up, down`。当方块具有此硬编码属性时，它会自适应放置的方向。

```yaml
properties:
  facing:
    # horizontal_direction = 4面朝向
    # direction = 6面朝向
    type: direction
    default: north
```

### facing\_clockwise <a href="#facing_clockwise" id="facing_clockwise"></a>

与上述不同，放置时会旋转90度。

```yaml
properties:
  facing_clockwise:
    type: horizontal_direction
    default: north
```

### waterlogged <a href="#waterlogged" id="waterlogged"></a>

方块是否可以含水。

请注意：使用此状态时，必须确保相应的视觉方块也包含水，否则客户端无法渲染水。

```yaml
properties:
  waterlogged:
    type: boolean
    default: false
```

### axis <a href="#axis" id="axis"></a>

指定方块是否沿某坐标轴放置，例如一些柱形方块和原木。轴只能是 `x, y, z`。

```yaml
properties:
  axis:
    type: axis
    default: y
```

### single\_block\_half / double\_block\_half <a href="#single_block_half-double_block_half" id="single_block_half-double_block_half"></a>

```yaml
properties:
  half:
    # single_block_half （用于台阶，活扳门）[top, bottom]
    # double_block_half （用于门，两格高的植物）[upper, lower]
    type: single_block_half
    default: bottom
```

### hinge <a href="#hinge" id="hinge"></a>

铰链的值只能为 `left, right`。

```yaml
properties:
  hinge:
    type: hinge
```

### slab\_type <a href="#slab_type" id="slab_type"></a>

台阶类型只能是 `top, bottom, double`。

```yaml
properties:
  type:
    type: slab_type
```
