# 🗺️ Mipmap \[必读]

### Introduction <a href="#introduction" id="introduction"></a>

Mipmap determines the anti-aliasing level in Minecraft. Below is a comparison of the differences between Mipmap level 4 and level 0.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FodziDESugHu27t1CRnHd%252Fimage.png%3Falt%3Dmedia%26token%3D0c20f995-a097-4fc6-8c4a-1b25e77d7a43\&width=768\&dpr=4\&quality=100\&sign=75c17dc9\&sv=2)mipmap: 4

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FVj5ddbIqysE7Hchz5HMW%252Fimage.png%3Falt%3Dmedia%26token%3D7684ae4c-137c-4f95-9efd-c6d443209781\&width=768\&dpr=4\&quality=100\&sign=68a235b5\&sv=2)mipmap: 0

Under what circumstances will Mipmap be reduced due to a resource pack?

Generally, the Mipmap level will decrease when the width and height of a model texture do not meet the requirement of being a power of 2. Dimensions such as 16x16, 32x16, and 128x32 are valid, while sizes like 15x15, 1x7, and 29x37 are considered invalid (Note: font images are exempt from this restriction).

If you don't want to fix those badly made textures, you can enable the plugin's **obfuscation** option, which will automatically fix the mipmap for you. It's incredibly simple! At the same time, the plugin will automatically separate font images that should not be placed within the atlas path to prevent them from polluting the Mipmap.

**However, please note that the plugin will not fix textures that come with .mcmeta files.**

Copy

```
#config.yml
resource-pack:
  protection:
    obfuscation:
      enable: true
      resource-location:
        enable: true
```

When you notice Mipmap issues in your client, please open your client logs! They will tell you what caused the Mipmap level to decrease. `Texture xxx:xxx with size xxx limits mip level from 4 to 0`
