---
description: https://minecraft.wiki/w/Items_model_definition#condition
---

# ⚖️ 条件

In this configuration, when you use "minecraft:condition," you need to specify the condition type, which is the "property" mentioned below. "on-false" and "on-true" respectively represent displaying different models under different conditions.\
在这个配置中，当你使用"minecraft:condition"时，需要指定条件类型，即下面提到的"property"。"on-false"和"on-true"分别代表在不同条件下显示不同的模型。

Copy  复制

```
items:
  default:condition_item:
    model:
      type: "minecraft:condition"
      property: "minecraft:using_item"
      on-false:
        type: "minecraft:model"
        path: "minecraft:item/custom/model_false"
      on-true:
        type: "minecraft:model"
        path: "minecraft:item/custom/model_true"
```

### Available Properties  可用属性 <a href="#available-properties" id="available-properties"></a>

check [https://minecraft.wiki/w/Items\_model\_definition#condition](https://minecraft.wiki/w/Items_model_definition#condition) for the usage of each argument\
请查阅 https://minecraft.wiki/w/Items\_model\_definition#condition 了解每个参数的用法

#### minecraft:broken <a href="#minecraft-broken" id="minecraft-broken"></a>

> Return `true` if the item is damageable and has only one use remaining before breaking.\
> 如果物品是可损坏的并且仅剩一次使用次数就损坏了，则返回 `true` 。

#### minecraft:carried <a href="#minecraft-carried" id="minecraft-carried"></a>

> Return `true` if item is carried between slots in GUI.\
> 如果物品在 GUI 的槽位之间被携带，则返回 `true` 。

#### minecraft:**damaged** <a href="#minecraft-damaged" id="minecraft-damaged"></a>

> Return `true` if the item is damageable and has been used at least once.\
> 如果物品可损坏且至少已被使用过一次，则返回 `true` 。

#### minecraft:**extended\_view** <a href="#minecraft-extended_view" id="minecraft-extended_view"></a>

> Return `true` if player has requested extended details by holding shift key down. Only works when item is displayed in UI. Note: not a keybind, can't be rebound.\
> 如果玩家按住 Shift 键请求扩展详细信息，则返回 `true` 。仅在物品显示在 UI 中时有效。注意：不是按键绑定，无法重新绑定。

#### minecraft:**fishing\_rod/cast** <a href="#minecraft-fishing_rod-cast" id="minecraft-fishing_rod-cast"></a>

> Return `true` if there is a fishing bobber attached to currently used fishing rod.\
> 如果当前使用的钓鱼竿上附着了钓鱼浮标，则返回 `true` 。

#### minecraft:**selected**  minecraft:选中 <a href="#minecraft-selected" id="minecraft-selected"></a>

> Return `true` if item is selected on a hotbar.\
> 如果物品在热力槽中被选中，返回 `true` 。

#### minecraft:**using\_item**  minecraft:使用物品 <a href="#minecraft-using_item" id="minecraft-using_item"></a>

> Return `true` if player is currently using this item.\
> 如果玩家当前正在使用这个物品，返回 `true` 。

#### minecraft:**view\_entity** <a href="#minecraft-view_entity" id="minecraft-view_entity"></a>

> * When not spectating, return `true` if context entity is the local player entity, i.e. the one controlled by client.\
>   如果不是在观战状态，如果上下文实体是本地玩家实体，即由客户端控制的那个实体，则返回 `true` 。
> * When spectating, return `true` if context entity is the _spectated_ entity.\
>   如果在观战状态，如果上下文实体是被观战的实体，则返回 `true` 。
> * If context entity is not present, will return `false`.\
>   如果上下文实体不存在，将返回 `false` 。

#### minecraft:**bundle/has\_selected\_item** <a href="#minecraft-bundle-has_selected_item" id="minecraft-bundle-has_selected_item"></a>

> Return `true` if bundle is "open", i.e. it has selected item visible in GUI.\
> 如果 bundle 处于"打开"状态，即 GUI 中可见选中项，则返回 `true` 。

#### minecraft:**component (Not Implemented)** minecraft:component (未实现) <a href="#minecraft-component-not-implemented" id="minecraft-component-not-implemented"></a>

> Uses component [item sub predicates](https://minecraft.wiki/w/Item_sub-predicate) to match item components.\
> 使用组件物品子谓词来匹配物品组件。

#### minecraft:has\_**component** <a href="#minecraft-has_component" id="minecraft-has_component"></a>

> Return `true` if the given component is present on the item.\
> 如果给定的组件在物品上存在，则返回 `true` 。

Copy  复制

```
type: "minecraft:condition"
property: "minecraft:has_component"
component: minecraft:enchantments
ignore-default: false
```

#### minecraft:**keybind\_down** <a href="#minecraft-keybind_down" id="minecraft-keybind_down"></a>

> Return `true` if keybind is currently active.\
> 如果按键绑定当前处于激活状态，则返回 `true` 。

Copy  复制

```
type: "minecraft:condition"
property: "minecraft:keybind_down"
keybind: key.left
```

#### minecraft:**custom\_model\_data** <a href="#minecraft-custom_model_data" id="minecraft-custom_model_data"></a>

> Return value from `flags` list in `minecraft:custom_model_data` component.\
> 从 `minecraft:custom_model_data` 组件中的 `flags` 列表返回值。

Copy  复制

```
type: "minecraft:condition"
property: "minecraft:custom_model_data"
index: 0
```
