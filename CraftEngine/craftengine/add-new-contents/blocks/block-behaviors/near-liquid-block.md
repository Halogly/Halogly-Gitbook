# 🌊 Near Liquid Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FQThsCr8DWL9MnDStY5c4%252Fimage.png%3Falt%3Dmedia%26token%3D0540cc32-fcf8-4a26-9e67-a5d9d81f27d7\&width=768\&dpr=4\&quality=100\&sign=f137ae4e\&sv=2)

Unlike [🌊 On Liquid Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/on-liquid-block) , [🌊 Near Liquid Block](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-behaviors/near-liquid-block) does not require the liquid to be a source block.

Copy

```
blocks:
  default:flame_cane:
    behaviors:
      - type: near_liquid_block
        liquid-type: lava
        stackable: true
        positions:
          - -1,-1,0
          - 1,-1,0
          - 0,-1,-1
          - 0,-1,1
```
