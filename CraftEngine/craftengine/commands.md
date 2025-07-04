# 🐚 命令

## 物品命令 <a href="#item-commands" id="item-commands"></a>

## 调试命令 <a href="#debug-commands" id="debug-commands"></a>

### appearance-state-usage <a href="#appearance-state-usage" id="appearance-state-usage"></a>

`/ce debug appearance-state-usage [方块类型]`

该命令用于获取指定方块类型的额外外观使用状态。红色部分表示已使用的状态，绿色部分表示可用的未使用状态。将鼠标悬停在对应的部分，可以查看具体的状态并得知哪些自定义状态正在使用中。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FZsqvpYSQpt2o4uhDUE3C%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=8e6e37eb\&sv=2)

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FkMmfb8UeeAhOKASNSMx5%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=44906d4e\&sv=2)
已使用的状态外观

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FblSWDyawRrCQDbXhfvGB%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=6bb17a34\&sv=2)
未使用状态

### real-state-usage <a href="#real-state-usage" id="real-state-usage"></a>

`/ce debug real-state-usage [方块类型]`

该命令与上述的命令类似，但区别在于这条命令检测的是可用的实际状态。当你在 `additional-real-blocks.yml` 文件中注册了额外的实际状态时，实际状态的数量可能会超过可用外观的数量。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FDXynVOE87LdmEvt821of%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=73f90a12\&sv=2)

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FKD4bwQJMH8vYjvQnr8M2%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=6fb0443f\&sv=2)
已使用的实际状态

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FtI4QxOAKRLBDLgZgQ4cQ%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=ed567b82\&sv=2)
未使用状态

在下面的图片中，上半部分显示了橡树树叶的可用外观状态，而下半部分显示了橡树树叶的可用实际状态。 你可以使用命令来体验它们之间的差异。

```yaml
/ce debug appearance-state-usage minecraft:oak_leaves
```

```yaml
/ce debug real-state-usage minecraft:oak_leaves
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F1In5q6KSkwz62u0nsEvh%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b0ce7d95\&sv=2)

### item-data <a href="#item-data" id="item-data"></a>

`/ce debug item-data`

该命令会检测当前持有的物品的数据（例如NBT或组件）。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FaPpHMG3j3evHchOBYGia%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=719501a\&sv=2)

### get-block-internal-id <a href="#get-block-internal-id" id="get-block-internal-id"></a>

`/ce debug get-block-internal-id [自定义方块状态]`

该命令用于获取自定义方块对应的服务端实际的方块名称，常用于WorldEdit等工具和数据包。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FXQUPusg2dgKs7uOSvab5%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=5095746a\&sv=2)
![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FW7IlQqRjFAGLxMvYl5Fu%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=a1d201fb\&sv=2)

### get-block-state-registry-id <a href="#get-block-state-registry-id" id="get-block-state-registry-id"></a>

`/ce debug get-block-state-registry-id [real_block_state]`

该命令用于获取相应方块状态的注册ID（不常用）。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fb52WtGRjXNVDwqVG2yJc%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=71d5a622\&sv=2)

### target-block <a href="#target-block" id="target-block"></a>

`/ce debug target-block [--this]`

`target-block` 用于检测准心指向方块的数据（或在后面加上 `--this` 获取当前位置方块的数据）。它包括实际方块ID和CraftEngine方块状态。如果方块有自定义标签，也会显示出来。
