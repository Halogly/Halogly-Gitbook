# 🌍 服务器语言 (i18n)

i18n is utilized for server-side localization. If you are seeking client-side localization, please consult the [🌎️ Client Lang (lang)](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/client-lang-lang). In general, typical users do not require the use of i18n, as it is primarily designed for providers of public model and asset packs who offer multilingual support.\
i18n 用于服务器端本地化。如果您需要客户端本地化，请参考🌎️客户端语言（lang）。通常情况下，普通用户不需要使用 i18n，因为它主要设计用于提供公共模型和资源包的多语言支持服务提供商。

To use i18n, please refer to the following link: [✏️ Text Format](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/text-format#less-than-i18n-id-greater-than).\
要使用 i18n，请参考以下链接：✏️文本格式。

The country or region specification for the language is optional (for example, "en\_us" can be simplified to "en"). The plugin will first attempt to find a language tailored to the specific country or region. If such a language is not available, it will then search for the general language. If the language is also not found, the plugin will default to using English (en) as the fallback language.\
语言的国家或地区规范是可选的（例如，“en\_us”可以简化为“en”）。插件将首先尝试查找针对特定国家或地区的语言。如果没有找到这样的语言，它将接着搜索通用语言。如果通用语言也未找到，插件将默认使用英语（en）作为备用语言。

Copy  复制

```
i18n:
  en:
    item.chinese_lantern: "Chinese Lantern"
    item.fairy_flower: "Fairy Flower"
    item.bench: "Bench"
    item.table_lamp: "Table Lamp"
    item.wooden_chair: "Wooden Chair"
    item.topaz_rod: "Topaz Rod"
    item.topaz_bow: "Topaz Bow"
    item.topaz_crossbow: "Topaz Crossbow"
    item.topaz_pickaxe: "Topaz Pickaxe"
    item.topaz_axe: "Topaz Axe"
    item.topaz_hoe: "Topaz Hoe"
    item.topaz_shovel: "Topaz Shovel"
    item.topaz_sword: "Topaz Sword"
    item.topaz_ore: "Topaz Ore"
    item.deepslate_topaz_ore: "Deepslate Topaz Ore"
    item.topaz: "Topaz"
    item.palm_log: "Palm Log"
    item.stripped_palm_log: "Stripped Palm Log"
    item.palm_wood: "Palm Wood"
    item.stripped_palm_wood: "Stripped Palm Wood"
    item.palm_planks: "Palm Planks"
    item.palm_sapling: "Palm Sapling"
    item.palm_leaves: "Palm Leaves"
  zh_cn:
    item.chinese_lantern: "灯笼"
    item.fairy_flower: "仙灵花"
    item.bench: "长椅"
    item.table_lamp: "台灯"
    item.wooden_chair: "木椅"
    item.topaz_rod: "黄玉钓竿"
    item.topaz_bow: "黄玉弓"
    item.topaz_crossbow: "黄玉弩"
    item.topaz_pickaxe: "黄玉镐"
    item.topaz_axe: "黄玉斧"
    item.topaz_hoe: "黄玉锄"
    item.topaz_shovel: "黄玉锹"
    item.topaz_sword: "黄玉剑"
    item.topaz_ore: "黄玉矿石"
    item.deepslate_topaz_ore: "深层黄玉矿石"
    item.topaz: "黄玉"
    item.palm_log: "棕榈原木"
    item.stripped_palm_log: "去皮棕榈原木"
    item.palm_wood: "棕榈木"
    item.stripped_palm_wood: "去皮棕榈木"
    item.palm_planks: "棕榈木板"
    item.palm_sapling: "棕榈树苗"
    item.palm_leaves: "棕榈树叶"
```

You can nest other tags within i18n for use.\
您可以在 i18n 内部嵌套其他标签以供使用。

Copy  复制

```
i18n:
  en:
    internal.cooking_info.0: "Time: <arg:cooking_time>ticks"
    internal.cooking_info.1: "Experience: <arg:cooking_experience>"
```
