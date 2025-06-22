---
description: >-
  Plugin supports all the content mentioned in this article in all places where
  numbers are used. It can be used wherever you can think of it!
  插件在所有使用数字的地方都支持本文中提到的所有内容。你想到哪里都可以使用！
---

# 数字格式

#### constant <a href="#constant" id="constant"></a>

Provide a fixed numerical value.\
提供一个固定的数值。

Copy 复制

```
type: constant
value: 1
```

In most cases, you can use the following abbreviated notation.\
在大多数情况下，您可以使用以下简写符号。

Copy 复制

```
count:
  type: constant
  value: 1
```

->

Copy 复制

```
count: 1
```

#### uniform <a href="#uniform" id="uniform"></a>

Provide a random number within the given range.\
提供给定范围内的随机数。

Copy 复制

```
type: uniform
min: 1
max: 3
```

In most cases, you can use the following abbreviated notation.\
在大多数情况下，您可以使用以下简写符号。

Copy 复制

```
count:
  type: uniform
  min: 1
  max: 3
```

->

Copy 复制

```
count: 1~3
```

Both `min` and `max` also support the nested use of `number provider`.\
`min` 和 `max` 也都支持 `number provider` 的嵌套使用。

Copy 复制

```
count:
  type: uniform
  min:
    type: uniform
    min: 2
    max: 7
  max: "<papi:skilllevel_farming>*5~<papi:skilllevel_farming>*10"
```

#### expression 表达式 <a href="#expression" id="expression"></a>

[https://ezylang.github.io/EvalEx/references/references.html](https://ezylang.github.io/EvalEx/references/references.html)

Copy 复制

```
type: expression
expression: "20 + 70 / 2"
```

In most cases, you can use the following abbreviated notation.\
在大多数情况下，您可以使用以下简写符号。

Copy 复制

```
count:
  type: expression
  expression: "<papi:skilllevel_farming> / 20 + 5"
```

->

Copy 复制

```
count: "<papi:skilllevel_farming> / 20 + 5"
```
