# 🗺️ Mipmap \[必读]

## 介绍 <a href="#introduction" id="introduction"></a>

Mipmap决定Minecraft中的抗锯齿级别。以下是Mipmap的4级和0级的区别。

<figure><img src="https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FodziDESugHu27t1CRnHd%252Fimage.png%3Falt%3Dmedia%26token%3D0c20f995-a097-4fc6-8c4a-1b25e77d7a43&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=75c17dc9&#x26;sv=2" alt=""><figcaption><p>mipmap：4</p></figcaption></figure>

<figure><img src="https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FVj5ddbIqysE7Hchz5HMW%252Fimage.png%3Falt%3Dmedia%26token%3D7684ae4c-137c-4f95-9efd-c6d443209781&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=68a235b5&#x26;sv=2" alt=""><figcaption><p>mipmap：0</p></figcaption></figure>

资源包在什么情况下会导致Mipmap级别降低呢？

通常情况下，当模型纹理的宽度和高度都不满足2的幂次方时，Mipmap级别就会降低。16x16、32x16和128x32等尺寸是符合要求的，而15x15、1x7和29x37等尺寸是不合规的（注意：字体图像没有这个限制）。

{% hint style="success" %}
如果你不想修复那些绘制很差的纹理，可以启用插件的**混淆**选项，它会自动为你修复Mipmap。非常方便！同时，插件会自动分离那些不应该放在图集路径中的字体图像，以防止它们影响到Mipmap的级别。

**然而，插件不会修复那些带有.mcmeta文件的纹理。**

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
当你在客户端遇到Mipmap问题时，请查看你的客户端日志！它会告诉你是什么原因导致了Mipmap级别降低。`Texture xxx:xxx with size xxx limits mip level from 4 to 0`
{% endhint %}
