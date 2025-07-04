# 🪻 灌木方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FRFE0okQV9AmYrWNZNon9%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=2a071689\&sv=2)

[🪻 灌木方块](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/bush-block)是一种必须在特定支撑方块上生长的方块。如果它下方的方块被破坏，或者它处于不合适的位置，它就会被破坏，或者掉落为物品。

```yaml
blocks:
  default:fairy_flower:
    behavior:
      type: bush_block
      stackable: false
      blacklist: false # 使用黑名单
      delay: 0
      bottom-blocks:
        - custom:xxx
        - minecraft:stone
      bottom-block-tags:
        - minecraft:dirt
        - minecraft:farmland
```

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FjeEOdk98aCeu339mvteN%252Fimage.png%3Falt%3Dmedia%26token%3D8ce624ed-d10f-409a-851f-c734d662278b\&width=768\&dpr=4\&quality=100\&sign=656383bd\&sv=2)
