# 🔗 链接参数

## 🔗 链式参数

## 介绍 <a href="#introduction" id="introduction"></a>

**链式参数**表示一种点符号语法（通过 `.` 连接），用于以分层方式访问与对象相关的参数。

例如，在一个可以访问玩家实例的交互事件中，我们可以通过这个对象获取额外的参数。

通过链式调用属性访问器，例如：

* `player.world` → 获取玩家当前所处的世界
* `world.name` → 获取这个世界的名称

我们可以将它们组合成一个参数标签格式，如 `<arg:player.world.name>`。这个标签会动态返回玩家当前所处世界的名称。

## 对象 <a href="#objects" id="objects"></a>

### 玩家 <a href="#player" id="player"></a>

| 参数               | 类型                                                                                                                       | 描述      |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------ | ------- |
| x                | 双精度浮点型                                                                                                                   | 玩家的x坐标  |
| y                | 双精度浮点型                                                                                                                   | 玩家的y坐标  |
| z                | 双精度浮点型                                                                                                                   | 玩家的z坐标  |
| block\_x         | 整型                                                                                                                       | 玩家的x坐标  |
| block\_y         | 整型                                                                                                                       | 玩家的y坐标  |
| block\_z         | 整型                                                                                                                       | 玩家的z坐标  |
| name             | 字符串                                                                                                                      | 玩家的名称   |
| uuid             | uuid                                                                                                                     | 玩家的uuid |
| is\_flying       | 布尔型                                                                                                                      | 是否飞行    |
| is\_sneaking     | 布尔型                                                                                                                      | 是否潜行    |
| gamemode         | 字符串                                                                                                                      | 玩家的游戏模式 |
| main\_hand\_item | [物品](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#item)     | 主手的物品   |
| off\_hand\_item  | [物品](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#item)     | 副手的物品   |
| world            | [世界](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#world)    | 玩家所处的世界 |
| position         | [位置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#position) | 玩家的位置   |

### 方块 <a href="#block" id="block"></a>

| 参数           | 类型                                                                                                                            | 描述      |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------- | ------- |
| x            | 双精度浮点型                                                                                                                        | 方块的x坐标  |
| y            | 双精度浮点型                                                                                                                        | 方块的y坐标  |
| z            | 双精度浮点型                                                                                                                        | 方块的z坐标  |
| block\_x     | 整型                                                                                                                            | 方块的x坐标  |
| block\_y     | 整型                                                                                                                            | 方块的y坐标  |
| block\_z     | 整型                                                                                                                            | 方块的z坐标  |
| world        | [世界](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#world)         | 方块所处的世界 |
| block\_state | [方块状态](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#block_state) | 方块的状态   |
| position     | [位置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#position)      | 方块的位置   |

### 世界 <a href="#world" id="world"></a>

| 参数   | 类型   | 描述      |
| ---- | ---- | ------- |
| name | 字符串  | 世界的名称   |
| uuid | uuid | 世界的uuid |
| time | 长整型  | 世界的时间   |

### 方块状态 <a href="#block_state" id="block_state"></a>

### 位置 <a href="#position" id="position"></a>

| 参数       | 类型                                                                                                                    | 描述  |
| -------- | --------------------------------------------------------------------------------------------------------------------- | --- |
| x        | 双精度浮点型                                                                                                                | x坐标 |
| y        | 双精度浮点型                                                                                                                | y坐标 |
| z        | 双精度浮点型                                                                                                                | z坐标 |
| block\_x | 整型                                                                                                                    | x坐标 |
| block\_y | 整型                                                                                                                    | y坐标 |
| block\_z | 整型                                                                                                                    | z坐标 |
| world    | [世界](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#world) | 世界  |

### 物品 <a href="#item" id="item"></a>

| 参数                  | 类型  | 描述         |
| ------------------- | --- | ---------- |
| id                  | 字符串 | 物品的id      |
| custom\_model\_data | 整型  | 物品的自定义模型数据 |
| is\_custom          | 布尔型 | 是否是自定义物品   |

### 家具 <a href="#furniture" id="furniture"></a>

| 参数           | 类型                                                                                                                       | 描述      |
| ------------ | ------------------------------------------------------------------------------------------------------------------------ | ------- |
| id           | 字符串                                                                                                                      | 家具的id   |
| uuid         | uuid                                                                                                                     | 家具的uuid |
| anchor\_type | 字符串                                                                                                                      | 家具的锚类型  |
| x            | 双精度浮点型                                                                                                                   | 家具的x坐标  |
| y            | 双精度浮点型                                                                                                                   | 家具的y坐标  |
| z            | 双精度浮点型                                                                                                                   | 家具的z坐标  |
| position     | [位置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#position) | 家具的位置   |
