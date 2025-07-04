---
description: 本插件支持本文中提到的所有数值内容，适用于任何你能想到的使用数字的地方！
---

# 🔢 数字格式

## 常量 <a href="#constant" id="constant"></a>

提供一个固定的数值。

```yaml
type: constant
value: 1
```

通常你可以像下面这样简化配置。

```yaml
count:
  type: constant
  value: 1
```

->

```yaml
count: 1
```

## uniform <a href="#uniform" id="uniform"></a>

提供指定范围内的随机数。

```yaml
type: uniform
min: 1
max: 3
```

通常你可以像下面这样简化配置。

```yaml
count:
  type: uniform
  min: 1
  max: 3
```

->

```yaml
count: 1~3
```

`min` 和 `max` 都支持 `number provider` 的嵌套使用。

```yaml
count:
  type: uniform
  min:
    type: uniform
    min: 2
    max: 7
  max: "<papi:skilllevel_farming>*5~<papi:skilllevel_farming>*10"
```

## 表达式 <a href="#expression" id="expression"></a>

[https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)

```yaml
type: expression
expression: "20 + 70 / 2"
```

通常你可以像下面这样简化配置。

```yaml
count:
  type: expression
  expression: "<papi:skilllevel_farming> / 20 + 5"
```

->

```yaml
count: "<papi:skilllevel_farming> / 20 + 5"
```
