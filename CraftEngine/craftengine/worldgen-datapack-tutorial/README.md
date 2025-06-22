# 📔 生成世界数据包教程

# 需要了解的重要事项 <a href="#important-things-to-know" id="important-things-to-know"></a>

由于 Minecraft 不允许动态修改方块的注册表，插件会预先注册所有必要的实际状态。你可以通过使用 [get-block-internal-id](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/commands#get-block-internal-id) 查询对应方块的实际状态。

Minecraft 仅识别符合 `craftengine:note_block_x` 格式的方块名称。即使你使用了其他插件，例如 MythicMobs 的方块放置技能，也适用此规则。这是因为 CraftEngine 采用了动态绑定方案，这意味着插件内的方块 ID 与服务器端的实际方块 ID 不一致。

# 本教程的目标受众 <a href="#the-target-audience-for-this-tutorial" id="the-target-audience-for-this-tutorial"></a>

本教程是快速入门教程，专为那些希望快速实现某些功能而不必投入时间学习 Minecraft 数据包的人。提供的示例仅为可行的解决方案，并不代表插件的全部潜力。你完全有能力利用 CraftEngine 生成类似于模组的地形和生物群系。

在制作数据包时，你可以将以下网站

[https://misode.github.io/worldgen/feature/](https://misode.github.io/worldgen/feature/)

[https://misode.github.io/worldgen/placed-feature/](https://misode.github.io/worldgen/placed-feature/)

整合到你的工作流程中，因为它是一个很有价值的工具，可以最大限度地减少配置中的语法错误。

本教程是在 1.21.4 版本时代编写的。请注意，不同版本之间可能存在差异，建议相应地谨慎对待。

本数据包教程并不专业；它只包含简单的示例。如果你对数据包感兴趣，你应该寻找更专业的教程并投入时间来学习。
