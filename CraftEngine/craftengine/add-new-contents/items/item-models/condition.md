---
description: https://zh.minecraft.wiki/w/物品模型映射#condition
---

# ⚖️ 条件

在这个配置中，当你使用“minecraft:condition”时，需要指定条件类型，即下面提到的 `property`。`on-false` 和 `on-true` 分别代表在不同条件下显示不同的模型。

```yaml
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

# Available Properties 可用属性 <a href="#available-properties" id="available-properties"></a>

请查阅 [https://zh.minecraft.wiki/w/物品模型映射#condition](https://zh.minecraft.wiki/w/物品模型映射#condition) 了解每个参数的用法

## minecraft:broken 物品报废 <a href="#minecraft-broken" id="minecraft-broken"></a>

> 如果物品是可损坏的并且仅剩最后一次使用次数就损坏了，则返回 `true`。

## minecraft:carried 容器拾取 <a href="#minecraft-carried" id="minecraft-carried"></a>

> 如果在容器 GUI 中使用光标拾取了这个物品，则返回 `true`。

## minecraft:**damaged** 物品损坏 <a href="#minecraft-damaged" id="minecraft-damaged"></a>

> 如果物品可损坏且至少已被使用过一次，则返回 `true`。

## minecraft:**extended\_view** 扩展详情 <a href="#minecraft-extended_view" id="minecraft-extended_view"></a>

> 如果玩家按住 Shift 键请求扩展详细信息，则返回 `true`。仅物品在 GUI 内时有效。注意：不是按键绑定，也无法重新绑定。

## minecraft:**fishing\_rod/cast** 钓鱼竿 <a href="#minecraft-fishing_rod-cast" id="minecraft-fishing_rod-cast"></a>

> 如果当前使用的钓鱼竿已经抛出了钓鱼钩，则返回 `true`。

## minecraft:**selected** 选中 <a href="#minecraft-selected" id="minecraft-selected"></a>

> 如果玩家在快捷栏内选择了这个物品，返回 `true`。

## minecraft:**using\_item** 使用物品 <a href="#minecraft-using_item" id="minecraft-using_item"></a>

> 如果玩家当前正在使用这个物品，返回 `true`。

## minecraft:**view\_entity** 旁观实体 <a href="#minecraft-view_entity" id="minecraft-view_entity"></a>

> * 如果不处于旁观模式，持有此物品的实体是当前玩家实体，即由客户端控制的玩家，则返回 `true`。
> * 如果处于旁观模式，持有此物品的实体是被旁观的实体，则返回 `true`。
> * 如果不存在持有此物品的实体，则返回 `false`。

## minecraft:**bundle/has\_selected\_item** 收纳袋选中物品 <a href="#minecraft-bundle-has_selected_item" id="minecraft-bundle-has_selected_item"></a>

> 如果收纳袋处于“打开”状态，即 GUI 中可以看见选中的物品，则返回 `true`。

## minecraft:**component（未实现）** 物品组件 <a href="#minecraft-component-not-implemented" id="minecraft-component-not-implemented"></a>

> 使用组件[物品子谓词](https://zh.minecraft.wiki/w/数据组件谓词)来匹配物品组件。

## minecraft:has\_**component** 拥有组件 <a href="#minecraft-has_component" id="minecraft-has_component"></a>

> Return `true` if the given component is present on the item.\
> 如果物品上存在给定的组件，则返回 `true`。

```yaml
type: "minecraft:condition"
property: "minecraft:has_component"
component: minecraft:enchantments
ignore-default: false
```

## minecraft:**keybind\_down** 按键绑定 <a href="#minecraft-keybind_down" id="minecraft-keybind_down"></a>

> 如果键位绑定被按下，则返回 `true`。

```yaml
type: "minecraft:condition"
property: "minecraft:keybind_down"
keybind: key.left
```

## minecraft:**custom\_model\_data** 自定义模型数据 <a href="#minecraft-custom_model_data" id="minecraft-custom_model_data"></a>

> 返回 `minecraft:custom_model_data` 组件中的 `flags` 列表的值。

```yaml
type: "minecraft:condition"
property: "minecraft:custom_model_data"
index: 0
```
