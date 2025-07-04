---
description: 本页面尚未完成
---

# ⌨️ Skript

对于高级Skript用户，请使用反射来实现更高级的功能。如果在使用Skript时遇到问题，请及时向我们反馈。如果希望增加新的Skript功能并且具备Java开发能力，可以考虑通过Pull request提交代码贡献！

请注意，如果服务器加载时出现错误，那很可能是Skript脚本在CraftEngine之前加载的。目前无法修复这个问题，只能通过重新加载来解决。

## 事件

CraftEngine已经与Skript语句集成。你可以使用以下格式来监听相应的自定义方块/家具事件

```yaml
on right click on default:chinese_lantern:
    say_message("你点击了自定义方块！")
```

```yaml
on break of default:palm_log[axis=y]:
    say_message("你破坏了自定义方块！")
```

## 表达式

**[the] custom block id of %方块%**
**%方块%'[s] custom block id**

*获取方块的自定义方块ID*

```yaml
# 示例
on block break:
   set {id} to custom block id of target block
   say_message("你破坏了%{id}%！")
```

```yaml
# 示例
on block break:
   set {id} to target block's custom block id
   say_message("你破坏了%{id}%！")
```

**[the] custom block state of %方块%**
**%方块%'[s] custom block state**

*获取方块的自定义状态*

```yaml
# 示例
on block break:
   set {custom_state} to target block's custom block state
   set {id} to custom block id of {custom_state}
   say_message("你破坏了%{custom_state}%，这是一个%{id}%方块！")
```

![img](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FY5CQfTc3ASBZASEdJxVz%252Fimage.png%3Falt%3Dmedia%26token%3D7d12dcf4-7b97-4ac7-ba77-9bedc90ecb55&width=768&dpr=4&quality=100&sign=1e173134&sv=2)

**[the] furniture id of %实体%**
**%实体%'[s] furniture id**

*获取实体的家具ID*

```yaml
# 暂时没有示例
```

**[the] custom item id of %物品%**
**%物品%'[s] custom item id**

*获取自定义物品*

```yaml
# 示例
set {_item} to a nether_brick
set the custom item id of {_item} to "default:bench"
give player {_item}
set {_id} to the custom item id of {_item}
say_message("你获得了%{_id}%！")
```

**[the] custom item [with id] %字符串%**

```yaml
# 示例
set {_item} to the custom item with id "default:bench"
give player {_item}
```

## 条件

**%方块% (is|are) custom block(s)**
**%方块% (is|are)(n't| not) custom block(s)**

*是否是自定义方块*

**%实体% (is|are) furniture**
**%实体% (is|are)(n't| not) furniture**

*实体是否是家具*

**%物品% (is|are) custom item(s)**
**%物品% (is|are)(n't| not) custom item(s)**

*是否是自定义物品*

## 效果

**place custom block %自定义方块状态% [%朝向% %位置%]**

*放置自定义方块状态*

```yaml
# 示例
place custom block default:palm_log[axis=x] at location of the player
```

**place furniture %字符串% [%朝向% %位置%]**

*放置家具*

```yaml
# 示例
place furniture "default:bench" at location of the player
```

**remove furniture %实体%**

*移除家具*

```yaml
# 示例
remove furniture target entity
```
