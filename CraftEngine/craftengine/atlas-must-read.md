# 📍 纹理图集 \[必读]

{% hint style="success" %}
如果你不想自己编写图集文件，可以启用插件的混淆选项（obfuscation），它会自动处理图集。非常方便！

```yaml
#config.yml
resource-pack:
  protection:
    obfuscation:
      enable: true
      resource-location:
        enable: true
```
{% endhint %}

## 介绍 <a href="#introduction" id="introduction"></a>

从Minecraft 1.19版本起，资源包引入了“纹理图集”的概念，它决定了纹理图像读取的路径。默认情况下，Minecraft 只能从`/textures/block`和`/textures/item`目录加载纹理，因为默认`atlas`图集文件只支持这两个文件夹。

```yaml
{
    "sources": [
        {
            "type": "directory",
            "source": "block",
            "prefix": "block/"
        },
        {
            "type": "directory",
            "source": "item",
            "prefix": "item/"
        },
        ...
    ]
}
```

如果你把纹理路径从`/textures/block/custom`移动到了`/textures/custom`，Minecraft会无法加载这些纹理，因为它们不在图集定义的范围内。定义错误的图集纹理会显示为紫黑相间的方块，如下图所示。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FRQZMAM1TnobkCpWCAuPD%252Fimage.png%3Falt%3Dmedia%26token%3D2a25a84d-c323-440f-9c67-decd171774df\&width=768\&dpr=4\&quality=100\&sign=6df4975\&sv=2)

## 创建图集 <a href="#create-atlas" id="create-atlas"></a>

要创建图集路径，你只需要将文件添加到资源包的以下路径：`resourcepack/assets/minecraft/atlases/blocks.json`。下面是一个简单的示例，将`custom`路径添加到图集中：

```yaml
{
    "sources": [
        {
            "type": "directory",
            "source": "custom",
            "prefix": "custom/"
        }
    ]
}
```

{% file src="../.gitbook/assets/blocks.json" %}

<figure><img src="https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FQIyqzq01rJZeLlvMTg10%252Fimage.png%3Falt%3Dmedia%26token%3D2899af97-58ed-4f16-8d95-056b2223c74a&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=5e2ebea&#x26;sv=2" alt=""><figcaption></figcaption></figure>

添加这样的JSON文件后，重新加载资源包，更改生效。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fw6QIh0iqDdLtADU6IqqZ%252Fimage.png%3Falt%3Dmedia%26token%3D7235dd04-76a9-41b7-b17c-559f950bf2ce\&width=768\&dpr=4\&quality=100\&sign=951f3957\&sv=2)

{% hint style="success" %}
当你有多个包含纹理图集配置的文件时，可以查阅篇章[⚔️ 文件冲突](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/resource-pack/file-conflict)来合并纹理图集。默认插件已经为你配置了这个选项。
{% endhint %}

{% hint style="danger" %}
**纹理图集需求**\
图集目录中的所有纹理必须符合2的幂次方尺寸（例如，16×16，32×16，64×128）以确保完整支持Mipmap功能。不符合要求的纹理会触发自动Mipmap级别降低。有关详细的Mipmap指南，请参考[🗺️ Mipmap \[必读\]](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/mipmap-must-read)

**分离存储事项**\
字体资源（例如，21×7的等级图标）必须与模型纹理分开存储。主要原因如下：

1. **Mipmap不兼容**：字体纹理不需要Mipmap
2. **影响纹理质量**：相同位置存储会导致相邻纹理被迫进行不必要的Mipmap降级
3. **合规性**：违反了Minecraft纹理管理的最佳实践

必须严格隔离图集管理的纹理与GUI/字体元素，以确保不会影响到渲染质量。
{% endhint %}
