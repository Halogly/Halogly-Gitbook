# 链接参数

### Introduction 介绍 <a href="#introduction" id="introduction"></a>

**Chain Arguments** represent a dot-notation syntax (connected by `.`) used to access object-related parameters in a hierarchical manner.\
链参数表示一种点符号语法（通过 `.` 连接），用于以分层方式访问与对象相关的参数。

For example, in an interaction event where we can access the player instance, we can retrieve additional parameters through this object.\
例如，在一个可以访问玩家实例的交互事件中，我们可以通过这个对象获取额外的参数。

By chaining property accessors like:\
通过链式调用属性访问器，例如：

* `player.world` → Gets the player's current world\
  `player.world` → 获取玩家当前的世界
* `world.name` → Gets the name of that world\
  `world.name` → 获取那个世界的名称

We can combine them into a parameter tag format like `<arg:player.world.name>`. This tag will dynamically return the name of the world the player is currently in.\
我们可以将它们组合成一个参数标签格式，如 `<arg:player.world.name>` 。这个标签将动态返回玩家当前所在世界的名称。

### Objects 对象 <a href="#objects" id="objects"></a>

#### player 玩家 <a href="#player" id="player"></a>

parameter 参数type 类型description 描述

x

double 双精度浮点数

the x coordinate of the player\
玩家的 x 坐标

y

double 双精度浮点数

the y coordinate of the player\
玩家的 y 坐标

z

double 双精度浮点数

the z coordinate of the player\
玩家的 z 坐标

block\_x

int

the x coordinate of the player\
玩家的 x 坐标

block\_y

int

the y coordinate of the player\
玩家的 y 坐标

block\_z

int

the z coordinate of the player\
玩家的 z 坐标

name

string

the name of the player\
玩家的名称

uuid

uuid

the uuid of the player\
玩家的 uuid

is\_flying

boolean

check the fly state 检查飞行状态

is\_sneaking 正在潜行

boolean

check the sneak state 检查偷窥状态

gamemode 游戏模式

string 字符串

the gamemode of the player\
玩家的游戏模式

main\_hand\_item 主手物品

[item 物品](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#item)

the item in main hand\
主手中的物品

off\_hand\_item 副手物品

[item 物品](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#item)

the item in off hand\
副手中的物品

world 世界

[world 世界](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#world)

the world where the player is in\
玩家所在的世界

position 位置

[position 位置](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#position)

the position of the player\
玩家的位置

#### block 块 <a href="#block" id="block"></a>

parameter 参数type 类型description 描述

x

double 双精度浮点数

the x coordinate of the block\
块的 x 坐标

y

double 双精度浮点数

the y coordinate of the block\
块的 y 坐标

z

double

the z coordinate of the block\
块的 z 坐标

block\_x

int

the x coordinate of the block\
块的 x 坐标

block\_y

int

the y coordinate of the block\
块的 y 坐标

block\_z

int

the z coordinate of the block\
块的 z 坐标

world 世界

[world 世界](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#world)

the world where the block is in\
块所在的世界

block\_state

[block\_state](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#block_state)

the blockstate of the block\
该块的 blockstate

position

[position](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#position)

the position of the block\
块的定位

#### world 世界 <a href="#world" id="world"></a>

parametertype 类型description 描述

name 名称

string 字符串

the name of the world\
世界的名称

uuid

uuid

the uuid of the world\
世界的 uuid

time 时间

long

the time of the world\
世界的时间

#### block\_state <a href="#block_state" id="block_state"></a>

parameter 参数type 类型description 描述

#### position <a href="#position" id="position"></a>

parametertype 类型description 描述

x

double 双精度浮点数

the x coordinate x 坐标

y

double 双精度浮点数

the y coordinate y 坐标

z

double 双精度浮点数

the z coordinate z 坐标

block\_x

int

the x coordinate x 坐标

block\_y

int

the y coordinate y 坐标

block\_z

int

the z coordinate z 坐标

world 世界

[world 世界](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format/chain-arguments#world)

the world 世界

#### item 物品 <a href="#item" id="item"></a>

paramter 参数type 类型description 描述

id

string 字符串

the id of the item\
项目的 id

custom\_model\_data 自定义模型数据

int

the custom model data of the item\
物品的自定义模型数据

is\_custom

boolean

checks if the item is custom\
检查物品是否为自定义

#### furniture 家具 <a href="#furniture" id="furniture"></a>

parametertype 类型description 描述

id

string 字符串

the id of the furniture\
家具的 id

uuid

uuid

the uuid of the furniture\
家具的 uuid

anchor\_type

string 字符串

the anchor type of the furniture\
家具的锚类型
