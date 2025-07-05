# 📍 家具放置

## 📍 Furniture Placement

## 介绍 <a href="#introduction" id="introduction"></a>

家具支持三种放置模式：地面、天花板和墙壁。你可以为不同的放置模式采用不同的外观和碰撞箱。例如，一个盆栽家具物品放置在地面时可能是直立的，从天花板悬挂时可能用绳子吊着，放置在墙上时可能是由一根木棍子吊着——就像原版的钟那样。

{% hint style="info" %}
你可以为单个家具同时配置多种放置模式。
{% endhint %}

下面，我以地面模式为例，讲解如何配置基本的放置。

```yaml
furniture:
  default:bench:
    placement:
      ground:
        # 为掉落物创建偏移量，以便它们不会在方块内部生成
        loot-spawn-offset: 0,0,0
        # 支持在此处使用外部模型
        # model-engine: blueprint_id
        # better-model: blueprint_id
        rules:
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
        elements:
          - item: default:bench
            display-transform: NONE
            billboard: FIXED
            position: 0.5,0,0
            translation: 0,0.5,0
            apply-dyed-color: true # 默认: true
        hitboxes:
          - type: interaction # 无碰撞箱
            can-use-item-on: false # 默认: false
            can-be-hit-by-projectile: false # 默认: false
            blocks-building: false # 默认: true
            position: 0,0,0
            width: 1
            height: 2
            # 'width'/'height'可以简写为'scale'
            # scale: 1,2 
            interactive: true # 交互实体是否是可交互的
            seats:
              - 0,0,-0.1 0
          - type: shulker # 有碰撞箱
            can-use-item-on: true # 默认: true
            can-be-hit-by-projectile: true # 默认: true
            blocks-building: true # 默认: true
            position: 1,0,0
            scale: 1 # 1.20.5+
            peek: 0 # 0~100
            # 相对方向。North = 面向玩家
            direction: UP # UP/DOWN/NORTH/WEST/EAST/SOUTH
            interaction-entity: true # 是否生成另一个交互实体
            interactive: true # 交互实体是否是可交互的
            seats:
              - 1,0,-0.1 0
          - type: custom # 软碰撞箱
            position: 1,0,0
            scale: 5 # 1.20.5+
            # 你可以在这里使用任何实体
            entity-type: slime # 默认: slime
```

分为三个部分：`rules`、`elements`、`hitboxes`。

`rules` 定义家具放置后的位置和旋转限制。`elements` 定义由哪些物品组成家具（你可以为单个家具配置多个物品，每个物品可以有不同的显示模式）。`hitboxes` 定义家具的碰撞体积。

## 规则 <a href="#rules" id="rules"></a>

### 旋转 <a href="#rotation" id="rotation"></a>

插件为家具提供多种旋转方案，它们之间的区别在于对旋转角度数量的限制或直接指定旋转方向。

旋转对于壁挂式的摆放方式无效。

### 对齐 <a href="#alignment" id="alignment"></a>

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F36xb0WeQSH45cr7iSVz6%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=96539c4\&sv=2)\
居中对齐

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FF7HhjgTtxdk3wIucZwqy%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=d60dc763\&sv=2)\
半对齐

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fk4jaenbMWri8AKqaiCPb%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=7f9085b4\&sv=2)\
四分之一对齐

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fq0lwi6Z0jqkueQMDoiHD%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b9bf03fb\&sv=2)\
角落对齐

对齐也适用于壁挂式的摆放方式。

## 元素 <a href="#elements" id="elements"></a>

`element` 代表构成家具外观的每一个物品。对于大多数家具，单物品就足够了。但是，如果你希望创建一个更复杂的家具，可以将多个物品组装在一起。例如，一个全息投影可以被分成两个物品：一个底座和投影本身。底座可以有固定的方向，而投影则可以设置为始终面向玩家。

```yaml
elements:
  - item: default:bench
    display-transform: NONE # NONE / THIRD_PERSON_LEFT_HAND / THIRD_PERSON_RIGHT_HAND
                            # FIRST_PERSON_LEFT_HAND / FIRST_PERSON_RIGHT_HAND
                            # HEAD / GUI / GROUND / FIXED
    billboard: FIXED  # FIXED / VERTICAL / HORIZONTAL / CENTER
    position: 0.5,0,0
    translation: 0,0.5,0
    scale: 1,1,1
    apply-dyed-color: true
```

请注意 `position` 和 `translation` 之间的区别。`position` 改变显示实体的坐标位置，而 `translation` 是显示实体本身的位移属性。

对于放在墙上的家具，需要使用 `position` 进行微小的偏移；否则，家具在某些方向上可能会变成黑色。这与 Minecraft 渲染实体的方式有关。

## 碰撞箱 <a href="#hitboxes" id="hitboxes"></a>

The `hitbox` is the interaction entity sent to the player, and you can visualize its effect by using the F3+B debug screen.`hitbox` 是发送给玩家的交互实体，你可以通过按 F3+B 键启用判定箱调试来显示。

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FZAkiDfKUD0JhyjS161gT%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=1f5505f0\&sv=2)

```yaml
hitboxes:
  - position: 0,0,0
    width: 1
    height: 1
    interactive: true
    seats:
      - 0,0,-0.1 0
  - position: 1,0,0
    width: 1
    height: 1
    interactive: true
    seats:
      - 1,0,-0.1 0
```

单个 `hitbox` 可以配置多个座位。如果多个 `hitboxes` 的座位位于同一位置，则相当于只有一个座位。

`seat` 的位置由位置坐标和旋转角度决定，在配置中用空格分隔。

```yaml
0,0,0 0
```

你也可以选择不加旋转角度，这样玩家在坐着时就可以自由旋转到任何角度。

```yaml
0,0,0
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fy0rBULzgm88rptOyeP5e%2F2.gif\&width=768\&dpr=4\&quality=100\&sign=1d64a0c5\&sv=2)\
0,0,0 0

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F7QS8DIznzoLlEmVELu1I%2F1.gif\&width=768\&dpr=4\&quality=100\&sign=1ad793da\&sv=2)\
0,0,0

## 外部模型 <a href="#external-models" id="external-models"></a>

你也可以使用 ModelEngine/BetterModel 的外部模型

```yaml
furniture:
  default:bench:
    placement:
      ground:
        model-engine: blueprint_id
        better-model: blueprint_id
        rules:
          # ANY / FOUR / EIGHT / SIXTEEN / NORTH / EAST / WEST / SOUTH
          rotation: EIGHT
          # ANY / CENTER / HALF / QUARTER / CORNER
          alignment: CENTER
```
