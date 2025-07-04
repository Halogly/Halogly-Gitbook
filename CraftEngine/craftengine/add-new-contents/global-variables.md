# 🔠 全局变量

## 示例用法 <a href="#example-usage" id="example-usage"></a>

```yaml
global-variables:
  test: "<!i><#FF8C00><arg:0>的<arg:1>"

items#topaz_gears:
  default:topaz_rod:
    material: fishing_rod
    custom-model-data: 1000
    settings:
      tags:
        - "default:topaz_tools"
    data:
     components:
        minecraft:max_damage: 10000
    client-bound-data:
      item-name: "<global:test:'<arg:player.name>':'<i18n:item.topaz_rod>'>"
      tooltip-style: minecraft:topaz
    model:
      template: default:model/simplified_fishing_rod_2d
      arguments:
        path: minecraft:item/custom/topaz_rod
        cast_path: minecraft:item/custom/topaz_rod_cast
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252F79kxK9uQ5dNFfsKILnT9%252Fimage.png%3Falt%3Dmedia%26token%3D16fda105-0db4-4ef8-8b23-6943a2aec895\&width=768\&dpr=4\&quality=100\&sign=1f68bf33\&sv=2)
