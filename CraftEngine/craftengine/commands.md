# 命令

### Item Commands <a href="#item-commands" id="item-commands"></a>

### Debug Commands 调试命令 <a href="#debug-commands" id="debug-commands"></a>

#### appearance-state-usage <a href="#appearance-state-usage" id="appearance-state-usage"></a>

`/ce debug appearance-state-usage [block_type]`

The command is used to retrieve the usage status of excess appearances for a specified block type. The red sections indicate states that are already in use, while the green sections represent available, unused states. When you hover your mouse over these sections, you can view the specific states and identify which custom states are utilizing them.\
该命令用于获取指定方块类型的额外外观使用状态。红色部分表示已使用的状态，绿色部分表示可用的未使用状态。当你将鼠标悬停在这些部分上时，可以查看具体状态并识别哪些自定义状态正在使用它们。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FZsqvpYSQpt2o4uhDUE3C%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=8e6e37eb\&sv=2)

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FkMmfb8UeeAhOKASNSMx5%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=44906d4e\&sv=2)appearance state in use 已使用的状态外观

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FblSWDyawRrCQDbXhfvGB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=6bb17a34\&sv=2)free state 自由状态

#### real-state-usage 实际状态使用 <a href="#real-state-usage" id="real-state-usage"></a>

`/ce debug real-state-usage [block_type]`

This command is similar to the one mentioned above, but the key difference lies in its function to inspect the available real states. When you register additional real states in the `additional-real-blocks.yml` file, the number of real states may exceed the number of available appearances.\
该命令与上述提到的命令类似，但关键区别在于其检查可用实际状态的功能。当你在 `additional-real-blocks.yml` 文件中注册额外的实际状态时，实际状态的数量可能会超过可用外观的数量。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FDXynVOE87LdmEvt821of%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=73f90a12\&sv=2)

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FKD4bwQJMH8vYjvQnr8M2%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=6fb0443f\&sv=2)real state in use 正在使用的实际状态

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FtI4QxOAKRLBDLgZgQ4cQ%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=ed567b82\&sv=2)free state 自由状态

In the image below, the upper section displays the available appearance states for oak leaves, while the lower section shows the available real states for oak leaves. You can use the command to experience the difference between them.\
在下面的图片中，上半部分显示了橡树叶的可用外观状态，而下半部分显示了橡树叶的可用真实状态。 您可以使用命令来体验它们之间的差异。

Copy 复制

```
/ce debug appearance-state-usage minecraft:oak_leaves
```

Copy 复制

```
/ce debug real-state-usage minecraft:oak_leaves
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F1In5q6KSkwz62u0nsEvh%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b0ce7d95\&sv=2)

#### item-data <a href="#item-data" id="item-data"></a>

`/ce debug item-data`

This command allows you to inspect the item data (such as NBT or components) of the item you are currently holding.\
这个命令允许你检查当前持有的物品的数据（例如 NBT 或组件）。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FaPpHMG3j3evHchOBYGia%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=719501a\&sv=2)

#### get-block-internal-id <a href="#get-block-internal-id" id="get-block-internal-id"></a>

`/ce debug get-block-internal-id [custom_block_state]`

This command is used to retrieve the server-side real block name corresponding to a custom block, and is commonly utilized in tools like WorldEdit and data packs.\
此命令用于获取自定义方块对应的服务器端真实方块名称，常用于 WorldEdit 等工具和数据包。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FXQUPusg2dgKs7uOSvab5%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=5095746a\&sv=2) ![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FW7IlQqRjFAGLxMvYl5Fu%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=a1d201fb\&sv=2)

#### get-block-state-registry-id <a href="#get-block-state-registry-id" id="get-block-state-registry-id"></a>

`/ce debug get-block-state-registry-id [real_block_state]`

This command is used to obtain the registry ID of the corresponding block state (not commonly used).\
此命令用于获取相应方块状态的注册 ID（不常用）。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fb52WtGRjXNVDwqVG2yJc%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=71d5a622\&sv=2)

#### target-block <a href="#target-block" id="target-block"></a>

`/ce debug target-block [--this]`

The 'target-block' is used to inspect the data of the block that the mouse is pointing at (or use the '--this' flag to obtain the current position). It includes the actual block ID and the CraftEngine block state. If the block has custom tags, they will also be displayed.\
'target-block'用于检查鼠标所指的方块数据（或使用'--this'标志获取当前位置）。它包括实际方块 ID 和 CraftEngine 方块状态。如果方块有自定义标签，也会显示出来。
