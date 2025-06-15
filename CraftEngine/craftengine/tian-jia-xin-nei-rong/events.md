# 🪇 Events

### Introduction <a href="#introduction" id="introduction"></a>

The `events` section determines which item/furniture/block will execute predefined behaviors during specific events. Under the `events` section, you need to specify an event trigger, such as `"right_click"` for a right-click action. Below the event trigger, you must pass a list of actions with their corresponding types. For example, `command` executes a specific command.

Copy

```
# format 1
events:
  right_click:
    - type: command
      command: say 1
      conditions:
        - type: permission
          permission: "craftengine.admin"
    - type: command
      command: say 2
      conditions: []
# format 2
events:
  - on: right_click
    functions:
      - type: command
        command: say 1
        conditions:
          - type: permission
            permission: "craftengine.admin"
      - type: command
        command: say 2
        conditions: []
```

[⚖️ Conditions](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/add-new-contents/conditions)

### 🧨 Event Triggers <a href="#event-triggers" id="event-triggers"></a>

#### items <a href="#items" id="items"></a>

* break
* right\_click
* left\_click
* consume

#### blocks <a href="#blocks" id="blocks"></a>

* break
* place
* right\_click
* left\_click
* step

#### Furniture <a href="#furniture" id="furniture"></a>

* break
* place
* right\_click

Please note that the corresponding events should be placed in the appropriate configuration area. For example, if you want to execute a command when interacting with a piece of furniture, the correct approach is to place the `events` under the `furniture` section, not under your item section.

Copy

```
items:
  default:bench:
    events: # ❌️
      right_click:
       - type: command
    behavior:
      type: furniture_item
      furniture:
        events: # ✅️
          right_click:
           - type: command
```

### 🔧 Functions <a href="#functions" id="functions"></a>

#### cancel\_event <a href="#cancel_event" id="cancel_event"></a>

Cancels the original event.

Copy

```
type: cancel_event
```

#### run <a href="#run" id="run"></a>

Runs a list of functions in order. It's useful for functions that share the same conditions.

Copy

```
type: run
delay: 0 # optional; number; [default: 0]
functions: # required; maplist
  - type: command
  - type: message
```

#### command <a href="#command" id="command"></a>

Runs a command as a player or console.

Copy

```
type: command
command: "say hello <arg:player.name>" # required; stringlist/string
target: "self" # optional; enum[all,self]/player selector; [default: self]
as-player: false # optional; [default: false]
```

#### message <a href="#message" id="message"></a>

Sends a message/system actionbar message

Copy

```
type: message
message: "Hello <papi:player_name>" # required; string list/string
target: "self" # optional; enum[all,self]/player selector
overlay: false # optional; [default: false]; false = chat box / true = actionbar
```

#### actionBar <a href="#actionbar" id="actionbar"></a>

Sends an actionbar

Copy

```
type: actionbar
actionbar: "This is an action bar"  # required; string
target: "self" # optional; enum[all,self]/player selector; [default: self]
```

#### Title <a href="#title" id="title"></a>

Sends a title

Copy

```
type: title
title: "<red>Title</red>"  # required; string
subtitle: "<Yellow>Subtitle</yellow>" # required; string
fade-in: 20 # optional; number; [default: 10]
stay: 10 # optional; number; [default: 20]
fade-out: 10 # optional; number; [default: 5]
```

#### open\_window <a href="#open_window" id="open_window"></a>

Opens a gui window

Copy

```
type: open_window #
gui-type: anvil # required; enum[anvil, enchantment, grindstone, loom, smithing, crafting, cartography];
title: "Super Anvil"  # optional; string
target: "self" # optional; enum[all,self]/player selector; [default: self]
```

#### place\_block <a href="#place_block" id="place_block"></a>

Places a block

Copy

```
type: place_block
block-state: "default:chinese_lantern"
x: <arg:block.block_x>
y: <arg:block.block_y>
z: <arg:block.block_z>
```

#### drop\_loot <a href="#drop_loot" id="drop_loot"></a>

Drops loots based on the give loot table

Copy

```
type: drop_loot
x: <arg:block.block_x> + 0.5
y: <arg:block.block_y> + 0.5
z: <arg:block.block_z> + 0.5
loot:
  pools: ...
```

#### update\_interaction\_tick <a href="#update_interaction_tick" id="update_interaction_tick"></a>

Updates the tick when the last interaction ends

Copy

```
type: update_interaction_tick
```

#### set\_count <a href="#set_count" id="set_count"></a>

Sets the count of the current item in this event

Copy

```
type: set_count
add: true # Default: false
count: -1
target: "self" # optional; enum[all,self]/player selector
```

#### set\_food <a href="#set_food" id="set_food"></a>

Sets the food level (0\~20) of the player

Copy

```
type: set_food
add: true
food: 4
target: "self" # optional; enum[all,self]/player selector
```

#### set\_saturation <a href="#set_saturation" id="set_saturation"></a>

Sets the saturation(0\~10) of the player

Copy

```
type: set_saturation
add: true
saturation: 2.5
target: "self" # optional; enum[all,self]/player selector
```

#### swing\_hand <a href="#swing_hand" id="swing_hand"></a>

Swings the hand involved in this event or the hand specified in config

Copy

```
type: swing_hand
hand: main_hand # Optional Argument
```

#### particle <a href="#particle" id="particle"></a>

Spawns a particle

Copy

```
type: particle
particle: minecraft:end_rod
x: "<arg:position.x>"
y: "<arg:position.y>"
z: "<arg:position.z>"
count: 5
offset-x: 0.3
offset-y: 0.3
offset-z: 0.3
speed: 0

# The following arguments are only effective
# when the particles are of a certain type.

# item
item: default:chinese_lantern

# block/falling_dust/dust_pillar/block_crumble/block_marker
block-state: default:plam_log[axis=y]

# charge
charge: 1.5

# shriek
shriek: 1

# dust
color: 255,255,255
scale: 1.0

# dust_color_transition
from: 255,255,255
to: 0,0,0
scale: 4.0

# vibration
target-x: 0
target-y: 1
target-z: 0
arrival-time: 10

# trail
target-x: 0
target-y: 1
target-z: 0
duration: 10
```

#### potion\_effect <a href="#potion_effect" id="potion_effect"></a>

Adds a potion effect

Copy

```
type: potion_effect
potion-effect: minecraft:blindness
duration: 20  # Default: 20
amplifier: 0   # Default: 0
ambient: false # from beacon
particles: true
```

#### remove\_potion\_effect <a href="#remove_potion_effect" id="remove_potion_effect"></a>

Removes a potion effect

Copy

```
type: remove_potion_effect
potion-effect: minecraft:blindness # Optional if 'all' is true
all: false  # Default: false
```

#### leveler\_exp <a href="#leveler_exp" id="leveler_exp"></a>

Adds skill/job experience

[👔 Supported Levelers](https://mo-mi.gitbook.io/xiaomomi-plugins/craftengine/plugin-wiki/craftengine/compatibility/supported-levelers)Copy

```
type: leveler_exp
plugin: AuraSkills  # The leveler plugin
leveler: fishing  # the job/skill id
count: 10  # the amount of exp to give
```

#### set\_cooldown <a href="#set_cooldown" id="set_cooldown"></a>

Sets cooldown for player

Copy

```
type: set_cooldown
time: 1m30s
id: my_cooldown_id
add: false  # Default: false  (Whether to accumulate cooldown time)
```

#### remove\_cooldown <a href="#remove_cooldown" id="remove_cooldown"></a>

Removes cooldown for player

Copy

```
type: remove_cooldown
id: my_cooldown_id  # Optional if 'all' is true
all: false  # Default: false
```

#### play\_sound <a href="#play_sound" id="play_sound"></a>

Plays a sound

Copy

```
type: play_sound
sound: minecraft:xxxx.xxx
x: <arg:position.x>
y: <arg:position.y>
z: <arg:position.z>
pitch: 1
volume: 1
source: master
```

More functions are coming...
