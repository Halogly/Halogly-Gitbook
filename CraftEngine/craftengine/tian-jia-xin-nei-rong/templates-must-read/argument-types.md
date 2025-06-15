# 🟢 Argument Types

### Direct Assignment <a href="#direct-assignment" id="direct-assignment"></a>

The simplest type of parameter is direct assignment, where you directly write the value after the parameter name.

Copy

```
arguments:
  value_1: true
  value_2: 100

# Use a map
arguments:
  value_map:
    a: b
    c: d

# Use a list
arguments:
  value_list:
    - 123
    - 456
```

When directly assigning a map, the parameters of the map must not include `type`, otherwise an error will occur! In such cases, you should use the Map type as described below. ❌️

Copy

```
arguments:
  value_map:
    type: c
    a: b
    c: d
```

✔️

Copy

```
arguments:
  value_map:
    type: map
    map:
      type: c
      a: b
      c: d
```

All non-direct assignment parameter types require specifying the parameter type `type`. Below are some available parameter types and examples

### Self Increase Int <a href="#self-increase-int" id="self-increase-int"></a>

`self_increase_int` is an auto-incrementing numeric ID that increases by 1 each time the parameter is used.

> Config

Copy

```
# Part of template
variants:
  axis=x:
    appearance: axisX
    id: "{internal_id}"
  axis=y:
    appearance: axisY
    id: "{internal_id}"
  axis=z:
    appearance: axisZ
    id: "{internal_id}"

# Part of the block config
arguments:
  internal_id:
    type: self_increase_int
    from: 0
    to: 2
```

> Result

Copy

```
variants:
  axis=x:
    appearance: axisX
    id: 0
  axis=y:
    appearance: axisY
    id: 1
  axis=z:
    appearance: axisZ
    id: 2
```

### Expression <a href="#expression" id="expression"></a>

Copy

```
arguments:
  saturation:
    type: expression
    expression: "{nutrition} * 1.5"
    value-type: double # int/double/float/short/long/boolean
```

### Map <a href="#map" id="map"></a>

Replace the placeholder with the specified map.

Copy

```
arguments:
  enchantments:
    type: map
    map:
      minecraft:sharpness: 1
```

In this case, the map cannot be applied correctly

❌️

Copy

```
template:
  components:enchantments: "{enchantments}, 123"
```

✔️

Copy

```
template:
  components:enchantments: "{enchantments}"
```

### List <a href="#list" id="list"></a>

Replace the placeholder with the specified list.

Copy

```
arguments:
  lore:
    type: list
    list:
      - "Hello, Minecraft!"
```

In this case, the list cannot be applied correctly

❌️

Copy

```
template:
  lore: "{lore}, 1"
```

✔️

Copy

```
template:
  lore: "{lore}"
```
