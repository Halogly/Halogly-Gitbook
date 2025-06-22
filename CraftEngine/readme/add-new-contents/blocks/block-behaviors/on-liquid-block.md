# 🌊 On Liquid Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FifONQugd3ngUzr5fCDTQ%252Fimage.png%3Falt%3Dmedia%26token%3Dd763dfb8-40bb-4a22-ac42-4e57aa76ac0e\&width=768\&dpr=4\&quality=100\&sign=b79aab4a\&sv=2)

The [🌊 On Liquid Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/on-liquid-block) is a type of block that can only be placed on the surface of fluid **sources**. Currently, there are only two fluid options available (water and lava).

Copy

```
blocks:
  default:reed:
    behavior:
      type: on_liquid_block
      stackable: false
      liquid-type:
        - water
        # - lava
```

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FAyCJMAE4D0vZnqeAUG7w%252Fimage.png%3Falt%3Dmedia%26token%3Dbc2c35fa-afb3-48a4-bbca-a53370b24eeb\&width=768\&dpr=4\&quality=100\&sign=9352b9d9\&sv=2)
