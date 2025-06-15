# 🗺️ Mipmap \[必读]

## 介绍 <a href="#introduction" id="introduction"></a>

Mipmap 决定 Minecraft 中的抗锯齿级别。以下是 Mipmap 4级和0级的区别。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FodziDESugHu27t1CRnHd%252Fimage.png%3Falt%3Dmedia%26token%3D0c20f995-a097-4fc6-8c4a-1b25e77d7a43\&width=768\&dpr=4\&quality=100\&sign=75c17dc9\&sv=2)mipmap：4

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FVj5ddbIqysE7Hchz5HMW%252Fimage.png%3Falt%3Dmedia%26token%3D7684ae4c-137c-4f95-9efd-c6d443209781\&width=768\&dpr=4\&quality=100\&sign=68a235b5\&sv=2)mipmap：0

资源包在什么情况下会导致 Mipmap 级别降低呢？

通常情况下，当模型纹理的宽度和高度都不满足 2 的幂次方时，Mipmap 级别就会降低。16x16、32x16 和 128x32 等尺寸是符合要求的，而 15x15、1x7 和 29x37 等尺寸是不合规的（注意：字体图像没有这个限制）。

{% hint style="success" %}
如果你不想修复那些绘制很差的纹理，可以启用插件的**混淆**选项，它会自动为你修复 Mipmap。非常简单！同时，插件会自动分离那些不应该放在图集路径中的字体图像，以防止它们影响到 Mipmap。

**然而，插件不会修复那些带有 .mcmeta 文件的纹理。**

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

{% hint style="warning" %}
当你在客户端遇到 Mipmap 问题时，请查看你的客户端日志！它会告诉你是什么原因导致了 Mipmap 级别降低。`Texture xxx:xxx with size xxx limits mip level from 4 to 0`
{% endhint %}
