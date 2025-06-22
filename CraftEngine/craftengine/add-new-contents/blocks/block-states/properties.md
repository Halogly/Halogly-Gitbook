# 🏷️ Properties

Please note that, regardless of the type of property, you must configure a default value within a reasonable range for each one.

### Custom Property <a href="#custom-property" id="custom-property"></a>

#### boolean <a href="#boolean" id="boolean"></a>

A property of type `boolean` can only have two possible values: `true` or `false`.

Copy

```
properties:
  happy:
    type: boolean
    default: false
```

#### int <a href="#int" id="int"></a>

A property of type `int` can take any integer value within the specified range.

Copy

```
properties:
  mode:
    type: int
    default: 1
    range: 1~3
```

#### string <a href="#string" id="string"></a>

A property of type `string` can only take values from a predefined set of options.

Copy

```
properties:
  color:
    type: string
    default: red
    values:
      - read
      - green
      - blue
```

### Hard-coded Property <a href="#hard-coded-property" id="hard-coded-property"></a>

Please note that the property name must be the same as the examples to take effect

#### facing <a href="#facing" id="facing"></a>

The facing values ​​are `east, south, west, north, up, down`. When a block has this hardcoded property, its placement orientation will automatically adapt.

Copy

```
properties:
  facing:
    # horizontal_direction = 4 faces
    # direction = 6 faces
    type: direction
    default: north
```

#### facing\_clockwise <a href="#facing_clockwise" id="facing_clockwise"></a>

Unlike the above, it will be rotated 90 degrees when placed

Copy

```
properties:
  facing_clockwise:
    type: horizontal_direction
    default: north
```

#### waterlogged <a href="#waterlogged" id="waterlogged"></a>

waterlogged determines whether this block can contain water.

Please note: When using this state, you must ensure that the corresponding visual block also contains water, otherwise the client cannot render the water.

Copy

```
properties:
  waterlogged:
    type: boolean
    default: false
```

#### axis <a href="#axis" id="axis"></a>

Axis determines whether the blocks are placed along the axis, such as pillar and log. The axis can only be `x, y, z`

Copy

```
properties:
  axis:
    type: axis
    default: y
```

#### single\_block\_half / double\_block\_half <a href="#single_block_half-double_block_half" id="single_block_half-double_block_half"></a>

Copy

```
properties:
  half:
    # single_block_half  (for slabs, trapdoors) [top, bottom]
    # double_block_half  (for doors, double height plants) [upper, lower]
    type: single_block_half
    default: bottom
```

#### hinge <a href="#hinge" id="hinge"></a>

The hinge can only be `left, right`

Copy

```
properties:
  hinge:
    type: hinge
```

#### slab\_type <a href="#slab_type" id="slab_type"></a>

The slab\_type can only be `top, bottom, double`

Copy

```
properties:
  type:
    type: slab_type
```
