# 🥪 可堆叠方块

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F4A2deddepooDFNBl9YaU%252Fimage.png%3Falt%3Dmedia%26token%3D8584d058-4036-4b06-99e2-32d9e67a158c\&width=768\&dpr=4\&quality=100\&sign=5b12e340\&sv=2)

```yaml
blocks:
  default:pebble:
    behavior:
      type: stackable_block
      property: pebble  # 数量的属性名称
      items:
        - default:pebble
      sounds:
        stack: minecraft:block.stone.fall
```
