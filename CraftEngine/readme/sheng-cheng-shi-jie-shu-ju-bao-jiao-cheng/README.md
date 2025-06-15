# 📔 生成世界数据包教程

### Important Things to Know  需要了解的重要事项 <a href="#important-things-to-know" id="important-things-to-know"></a>

Since Minecraft do not permit the dynamic modification of the block registry, the plugin pre-registers all necessary real states in advance. You can query the actual block states corresponding to a block by using [get-block-internal-id](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/commands#get-block-internal-id).\
由于 Minecraft 不允许动态修改方块注册表，插件会预先注册所有必要的实际状态。您可以通过使用 get-block-internal-id 查询对应方块的实际状态。

Minecraft only recognizes block names that follow the pattern similar to `craftengine:note_block_x`. This applies even when you are using other plugins, such as MythicMobs' block placement skills. The reason for this is that CraftEngine employs a dynamic binding scheme, which means the block IDs within the plugin do not align with the actual block IDs on serverside.\
Minecraft 仅识别符合 `craftengine:note_block_x` 格式的方块名称。即使你使用其他插件，例如 MythicMobs 的方块放置技能，也适用此规则。这是因为 CraftEngine 采用了动态绑定方案，这意味着插件内的方块 ID 与服务器端的实际方块 ID 不一致。

### The Target Audience for This Tutorial 本教程的目标受众 <a href="#the-target-audience-for-this-tutorial" id="the-target-audience-for-this-tutorial"></a>

This tutorial is designed as a crash course, tailored specifically for those who wish to swiftly implement certain functionalities without investing time in learning Minecraft datapacks. The examples provided are merely feasible solutions and do not represent the full potential of the plugin. You are entirely capable of utilizing CraftEngine to generate mod-like terrains and biomes.\
本教程设计为快速入门课程，专为那些希望快速实现某些功能而无需投入时间学习 Minecraft datapacks 的人士。提供的示例仅为可行的解决方案，并不代表插件的全部潜力。你完全有能力利用 CraftEngine 生成类似模组的 terrain 和 biome。

When making your datapack, you may integrate the website\
在制作你的 datapack 时，你可以整合网站

[https://misode.github.io/worldgen/feature/](https://misode.github.io/worldgen/feature/)

[https://misode.github.io/worldgen/placed-feature/](https://misode.github.io/worldgen/placed-feature/)

into your workflow, as it serves as a valuable tool to minimize syntax errors in your config.\
添加到你的工作流程中，因为它是一个宝贵的工具，可以最大限度地减少你的配置中的语法错误。

This tutorial was authored during the era of version 1.21.4. Please be aware that variations may exist across different versions, and it is advisable to exercise discernment accordingly.\
本教程是在 1.21.4 版本时代编写的。请注意，不同版本之间可能存在差异，建议相应地谨慎对待。

This is not a professional datapack tutorial; it contains only simple examples. If you are interested in datapacks, you should seek out professional tutorials and dedicate time to learning them thoroughly.\
这不是一个专业的 datapack 教程；它只包含简单的示例。如果你对 datapacks 感兴趣，你应该寻找专业的教程并投入时间彻底学习它们。
