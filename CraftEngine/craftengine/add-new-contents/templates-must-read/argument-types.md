# 🟢 参数类型

# 直接赋值 <a href="#direct-assignment" id="direct-assignment"></a>

最简单的参数类型是直接赋值，即在参数名后面直接填写值。

```yaml
arguments:
  value_1: true
  value_2: 100

# 使用映射
arguments:
  value_map:
    a: b
    c: d

# 使用列表
arguments:
  value_list:
    - 123
    - 456
```
{% hint style="danger" %}
当直接赋值一个映射时，映射的参数不能包含 type ，否则会发生错误！在这种情况下，你应该按照下面的描述使用 Map 类型。
❌️

```yaml
arguments:
  value_map:
    type: c
    a: b
    c: d
```

✔️

```yaml
arguments:
  value_map:
    type: map
    map:
      type: c
      a: b
      c: d
```
{% endhint %}
{% hint style="info" %}
所有非直接赋值参数类型都需要指定参数类型 `type`。以下是一些可用的参数类型和示例
{% endhint %}

# 自增整数 <a href="#self-increase-int" id="self-increase-int"></a>

`self_increase_int` 是一个自增的数字 ID，每次使用参数时增加一次 1。

> 配置

```yaml
# 模板部分
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

# 方块配置部分
arguments:
  internal_id:
    type: self_increase_int
    from: 0
    to: 2
```

> 结果

```yaml
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

# 表达式 <a href="#expression" id="expression"></a>

```yaml
arguments:
  saturation:
    type: expression
    expression: "{nutrition} * 1.5"
    value-type: double # int/double/float/short/long/boolean
```

# 映射 <a href="#map" id="map"></a>

用指定的映射替换占位符。

```yaml
arguments:
  enchantments:
    type: map
    map:
      minecraft:sharpness: 1
```
{% hint style="warning" %}
在这种情况下，映射不能正确应用

❌️

```yaml
template:
  components:enchantments: "{enchantments}, 123"
```

✔️

```yaml
template:
  components:enchantments: "{enchantments}"
```
{% endhint %}

# 列表 <a href="#list" id="list"></a>

用指定的列表替换占位符。

```yaml
arguments:
  lore:
    type: list
    list:
      - "你好，Minecraft!"
```
{% hint style="warning" %}
在这种情况下，列表不能正确应用

❌️

```yaml
template:
  lore: "{lore}, 1"
```

✔️

```yaml
template:
  lore: "{lore}"
```
{% endhint %}