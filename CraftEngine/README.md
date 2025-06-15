# 📍图集 \[必读]

{% hint style="success" %}
如果你不想自己编写图集文件，可以启用插件的混淆选项（obfuscation），它会自动为你处理 atlas。非常简单！

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

从 Minecraft 1.19 版本开始，资源包Since Minecraft 1.19, resource packs have introduced the concept of "atlas," which determines the paths from which texture images are read. By default, Minecraft can only load textures from the `/textures/block` and `/textures/item` directories because the default `atlas` file only supports these two folders.

Copy

```
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
        ...more
    ]
}
```

If you move the texture paths from `/textures/block/custom` to `/textures/custom`, Minecraft will be unable to load these textures because they fall outside the scope defined by the atlas. Textures located outside the atlas will appear as purple-and-black checkered squares, as shown in the image below.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FRQZMAM1TnobkCpWCAuPD%252Fimage.png%3Falt%3Dmedia%26token%3D2a25a84d-c323-440f-9c67-decd171774df\&width=768\&dpr=4\&quality=100\&sign=6df4975\&sv=2)

### Create Atlas <a href="#create-atlas" id="create-atlas"></a>

To create an atlas path, you simply need to add a file to your resource pack at the following path: `resourcepack/assets/minecraft/atlases/blocks.json`. Below is a simple example that adds the `custom` path to the atlas:

Copy

```
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

[151Bblocks.json](https://1836335287-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOgvQ1fEJPROp7131PPlK%2Fuploads%2FjafUqhjPxfRdlPJ6v9Xk%2Fblocks.json?alt=media\&token=9f43d1ce-4d9c-4818-ac8e-0d16ad1dc56f)![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FQIyqzq01rJZeLlvMTg10%252Fimage.png%3Falt%3Dmedia%26token%3D2899af97-58ed-4f16-8d95-056b2223c74a\&width=768\&dpr=4\&quality=100\&sign=5e2ebea\&sv=2)

After adding such a JSON file, reload the resource pack, and you will see the changes take effect.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fw6QIh0iqDdLtADU6IqqZ%252Fimage.png%3Falt%3Dmedia%26token%3D7235dd04-76a9-41b7-b17c-559f950bf2ce\&width=768\&dpr=4\&quality=100\&sign=951f3957\&sv=2)

When you have multiple files containing atlas configurations, you can check [⚔️ File Conflict](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/resource-pack/file-conflict) to merge the atlases. By default, the plugin has already configured this option for you.

**Texture Atlas Requirements** All textures within the atlas directory must conform to power-of-two dimensions (e.g., 16×16, 32×16, 64×128) to maintain full Mipmap functionality. Non-compliant textures will trigger automatic Mipmap level reduction. For detailed Mipmap guidelines, consult [🗺️ Mipmap \[MUST READ\]](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/mipmap-must-read)

**Critical Separation Notice** Font assets (e.g., 21×7 rank icons) must be stored separately from model textures. Key reasons:

1. **Mipmap Incompatibility**: Font textures don't require Mipmap
2. **Quality Protection**: Co-location forces unnecessary Mipmap downgrades on adjacent textures
3. **Compliance**: Violates Minecraft's texture management best practices

Maintain strict isolation between atlas-managed textures and GUI/font elements to preserve rendering quality.
