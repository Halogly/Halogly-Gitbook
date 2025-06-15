# 📍 Furniture Placement

### Introduction <a href="#introduction" id="introduction"></a>

Furniture supports three placement modes: ground, ceiling, and wall. You can employ distinct appearances and collision box schemes for different placement modes. For instance, a potted plant furniture item may stand upright when placed on the ground, dangle with a rope when hung from the ceiling, and be supported by a wooden plank when mounted on the wall—much like vanilla bell block.

You can configure multiple placement modes simultaneously for a single piece of furniture.

Below, I will use the ground mode as an example to explain how to configure a basic placement.

Copy

```
furniture:
  default:bench:
    placement:
      ground:
        # create offsets for the drops so they won't spawn in blocks
        loot-spawn-offset: 0,0,0
        # Supports External Models Here
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
            apply-dyed-color: true # default: true
        hitboxes:
          - type: interaction # non-collision hitbox
            can-use-item-on: false # default: false
            can-be-hit-by-projectile: false # default: false
            blocks-building: false # default: true
            position: 0,0,0
            width: 1
            height: 2
            # 'width'/'height' can be simplified to 'scale'
            # scale: 1,2 
            interactive: true # whether the interaction entity is interactive
            seats:
              - 0,0,-0.1 0
          - type: shulker # hard-collision hitbox
            can-use-item-on: true # default: true
            can-be-hit-by-projectile: true # default: true
            blocks-building: true # default: true
            position: 1,0,0
            scale: 1 # 1.20.5+
            peek: 0 # 0~100
            # Relative direction. North = facing the player
            direction: UP # UP/DOWN/NORTH/WEST/EAST/SOUTH
            interaction-entity: true # whether to summon another interaction entity
            interactive: true # whether the interaction entity is interactive
            seats:
              - 1,0,-0.1 0
          - type: custom # soft-collision hitbox
            position: 1,0,0
            scale: 5 # 1.20.5+
            # You can use any entity here
            entity-type: slime # default: slime
```

There are three sections: `rules`, `elements`, and `hitboxes`.

The `rules` section determines the position and rotation constraints of the furniture after placement. The `elements` section defines which items compose the furniture (you can configure multiple items for a single piece of furniture, each with different display modes). The `hitboxes` section specifies the collision volume of the furniture.

### Rules <a href="#rules" id="rules"></a>

#### rotation <a href="#rotation" id="rotation"></a>

The plugin's furniture supports a variety of rotation schemes, with the differences between them lying in the limitations on the number of rotation angles or the direct specification of rotation directions.

Rotation has no effect on wall-mounted placement methods.

#### alignment <a href="#alignment" id="alignment"></a>

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F36xb0WeQSH45cr7iSVz6%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=96539c4\&sv=2)center

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FF7HhjgTtxdk3wIucZwqy%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=d60dc763\&sv=2)half

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fk4jaenbMWri8AKqaiCPb%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=7f9085b4\&sv=2)quarter

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fq0lwi6Z0jqkueQMDoiHD%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=b9bf03fb\&sv=2)corner

Alignment is also applicable to wall-mounted placements.

### Elements <a href="#elements" id="elements"></a>

An `element` is each item that constitutes the appearance of the furniture. For most furniture, a single item suffices. However, if you wish to create a more intricate piece of furniture, you can assemble it from multiple items. For example, a holographic projection could be divided into two items: a base and the projection itself. The base could have a fixed orientation, while the projection could be set to always face the player.

Copy

```
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

Please note the distinction between `position` and `translation`. `position` alters the coordinate location of the corresponding display entity, whereas `translation` is a displacement attribute of the display entity itself.

For furniture placed on walls, you need to use `position` for slight offsets; otherwise, the furniture may turn black in certain directions. This is related to how Minecraft renders entities.

### Hitboxes <a href="#hitboxes" id="hitboxes"></a>

The `hitbox` is the interaction entity sent to the player, and you can visualize its effect by using the F3+B debug screen.

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2FZAkiDfKUD0JhyjS161gT%2Fimage.png\&width=768\&dpr=4\&quality=100\&sign=1f5505f0\&sv=2)Copy

```
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

A single `hitbox` can be configured with multiple seats. If the seats of multiple `hitboxes` are positioned at the same location, it is equivalent to having only one seat.

The position of a `seat` is determined by a location and a rotation, separated by a space in the configuration.

Copy

```
0,0,0 0
```

You may also choose not to configure a rotation angle, allowing players to rotate freely to any angle while seated.

Copy

```
0,0,0
```

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2Fy0rBULzgm88rptOyeP5e%2F2.gif\&width=768\&dpr=4\&quality=100\&sign=1d64a0c5\&sv=2)0,0,0 0

![](https://mo-mi.gitbook.io/~gitbook/image?url=https%3A%2F%2Fcontent.gitbook.com%2Fcontent%2FOgvQ1fEJPROp7131PPlK%2Fblobs%2F7QS8DIznzoLlEmVELu1I%2F1.gif\&width=768\&dpr=4\&quality=100\&sign=1ad793da\&sv=2)0,0,0

### External Models <a href="#external-models" id="external-models"></a>

You can also use external models from ModelEngine/BetterModel

Copy

```
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
