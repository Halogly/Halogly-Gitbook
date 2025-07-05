# ⚙️ 家具设置

## 物品 <a href="#item" id="item"></a>

设置家具对应的物品。通常用于在创造模式下使用中键（1.21.4+）获取家具物品。

```yaml
item: default:test_furniture
```

## 声音 <a href="#sounds" id="sounds"></a>

设置家具在不同情况下的声音

* 当玩家破坏家具时
* 当玩家放置家具时

```yaml
sounds:
  break: minecraft:block.bamboo_wood.break
  place: minecraft:block.bamboo_wood.place
```

{% hint style="info" %}
你可以这样配置，来精确控制音量和音调

```yaml
sounds:
  break:
    id: minecraft:block.deepslate.break
    pitch: 0.5
    volume: 0.25
  place: minecraft:block.deepslate.step
```
{% endhint %}

## 减少数据内容 <a href="#minimized" id="minimized"></a>

设置家具是否向没有管理员权限的玩家发送最小化的网络数据包。

```yaml
minimized: true
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FqmuOtslb0m4pzkyKjf20%252Fimage.png%3Falt%3Dmedia%26token%3D7651bfce-5d2e-494a-8893-5017aa63a332\&width=768\&dpr=4\&quality=100\&sign=bad16b1e\&sv=2)
