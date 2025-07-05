---
description: 本页面主要讲解如何添加新字体
---

# ㊙️ 字体

## ㊙️ 字体

## TTF <a href="#ttf" id="ttf"></a>

[![Logo](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fminecraft.wiki%2Ffavicon.ico\&width=20\&dpr=4\&quality=100\&sign=e464f1f5\&sv=2)自定义字体 – Minecraft Wiki](https://zh.minecraft.wiki/w/%E8%87%AA%E5%AE%9A%E4%B9%89%E5%AD%97%E4%BD%93#ttf)

对于 TTF 字体，你需要在以下路径中创建一个 `default.json` 文件。如果已存在 `default.json` 文件，那么只需将字体 JSON 附加到现有 JSON 文件的底部。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FiIqkr8gniPWWU3QCYKIS%252Fimage.png%3Falt%3Dmedia%26token%3D7c94e751-1cf2-4b1c-875d-39a7e7346f58\&width=768\&dpr=4\&quality=100\&sign=dc66e3ca\&sv=2)

```json
// default.json
{
    "providers": [
        {
            "type": "ttf",
            "file": "minecraft:custom_font.ttf",
            "oversample": 10,
            "size": 11
        }
    ]
}
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252FTKv2B9h3sS7TVSgIJkaA%252Fimage.png%3Falt%3Dmedia%26token%3D10a0ea88-c186-4638-9946-e3c98844c94b\&width=768\&dpr=4\&quality=100\&sign=b77f6c8c\&sv=2)

## 位图 <a href="#bitmap" id="bitmap"></a>

[![Logo](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fminecraft.wiki%2Ffavicon.ico\&width=20\&dpr=4\&quality=100\&sign=e464f1f5\&sv=2)Font – Minecraft Wiki 字体 – Minecraft WikiMinecraft Wiki](https://minecraft.wiki/w/Font#Bitmap_provider)

如果你希望替换原版字符图片，只需将以下 PNG 文件放置在下方指定的路径中。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2F1836335287-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FOgvQ1fEJPROp7131PPlK%252Fuploads%252Fb4x0H5SUIl3TSku2UKHa%252Fimage.png%3Falt%3Dmedia%26token%3Dbffc7f87-97f0-4e5f-af5c-735ad8189d60\&width=768\&dpr=4\&quality=100\&sign=dd695814\&sv=2)

## Unihex <a href="#unihex" id="unihex"></a>

要在 Minecraft 中配置不常用且较少使用的 `unihex` 字体，你可以参阅 Minecraft Wiki 获取详细说明。

[![Logo](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fminecraft.wiki%2Ffavicon.ico\&width=20\&dpr=4\&quality=100\&sign=e464f1f5\&sv=2)Font – Minecraft WikiMinecraft Wiki](https://minecraft.wiki/w/Font#Unihex_provider)

```json
{
    "providers": [
        {
            "type": "unihex",
            "hex_file": "minecraft:font/unifont_jp.zip",
            "size_overrides": [
                {
                    "__ranges": [
                        "Enclosed CJK Letters and Months",
                        "CJK Compatibility",
                        "CJK Unified Ideographs Extension A",
                        "Yijing Hexagram Symbols",
                        "CJK Unified Ideographs"
                    ],
                    "from": "\u3200",
                    "to": "\u9FFF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "CJK Compatibility Ideographs"
                    ],
                    "from": "\uF900",
                    "to": "\uFAFF",
                    "left": 0,
                    "right": 15
                }
            ],
            "filter": {
                "jp": true
            }
        },
        {
            "type": "unihex",
            "hex_file": "minecraft:font/unifont.zip",
            "size_overrides": [
                {
                    "__ranges": [
                        "CJK Symbols and Punctuation",
                        "Hiragana",
                        "Katakana"
                    ],
                    "from": "\u3001",
                    "to": "\u30FF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Enclosed CJK Letters and Months",
                        "CJK Compatibility",
                        "CJK Unified Ideographs Extension A",
                        "Yijing Hexagram Symbols",
                        "CJK Unified Ideographs"
                    ],
                    "from": "\u3200",
                    "to": "\u9FFF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Jamo"
                    ],
                    "from": "\u1100",
                    "to": "\u11FF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Compatibility Jamo"
                    ],
                    "from": "\u3130",
                    "to": "\u318F",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Jamo Extended-A"
                    ],
                    "from": "\uA960",
                    "to": "\uA97F",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Jamo Extended-B"
                    ],
                    "from": "\uD7B0",
                    "to": "\uD7FF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Hangul Syllables",
                    ],
                    "from": "\uAC00",
                    "to": "\uD7AF",
                    "left": 1,
                    "right": 15
                },
                {
                    "__ranges": [
                        "CJK Compatibility Ideographs"
                    ],
                    "from": "\uF900",
                    "to": "\uFAFF",
                    "left": 0,
                    "right": 15
                },
                {
                    "__ranges": [
                        "Halfwidth and Fullwidth Forms"
                    ],
                    "from": "\uFF01",
                    "to": "\uFF5E",
                    "left": 0,
                    "right": 15
                }
            ]
        }
    ]
}
```
