# 🚪 Door Block

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FkhYqDmF2zkkWE0L7OLnT%252Fimage.png%3Falt%3Dmedia%26token%3D390a5cf9-4449-4c01-931d-caea5df7672f\&width=768\&dpr=4\&quality=100\&sign=363801ee\&sv=2)Copy

```
blocks:
  default:palm_door:
    behavior:
      type: door_block
      can-open-with-hand: true
      can-open-by-wind-charge: true
      sounds:
        open: block.wooden_door.open
        close: block.wooden_door.close
```

Please note that all door blocks must have `open`, `powered`, `half`, `facing`, `hinge` properties. If you are unsure how to set up properties, please refer to [🔣 Block States](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/blocks/block-states).

You can create at most 25 new doors

![](https://mo-mi.gitbook.io/xiaomomi-plugins/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fnw9ld2yOdjO4jI2cg3Ha%252Fimage%2520%281%29.png%3Falt%3Dmedia%26token%3Dcd0a9263-483e-4249-92bb-3e54390c75e7\&width=300\&dpr=4\&quality=100\&sign=f5e13290\&sv=2)
