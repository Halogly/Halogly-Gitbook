# Spawning

## Introduction

TrainCarts features several different ways to spawn trains. These are:

* [Vanilla Minecarts](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/VanillaMinecarts) - Players can spawn TrainCarts Minecarts. The page details how to have Vanilla Minecart behavior as well.
* [Spawn Sign](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Signs/Spawner) - Spawns trains onto the track above in response to Redstone or automatically on a period
* [Train Spawn Chest](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Train_Spawn_Chest) - A portable item with which players can pick up trains and spawn them onto the track

## Spawn Pattern

Both the train spawn chest and the spawn sign support a spawn pattern syntax. With this syntax a train can be composed of multiple different carts or saved trains, and then spawned as a whole.

| Mechanism         | Pattern                                  | Explanation                                                                      |
| ----------------- | ---------------------------------------- | -------------------------------------------------------------------------------- |
| Vanilla Minecarts | `m`                                      | Spawns a rideable Minecart                                                       |
| Saved Trains      | `MyTrain`                                | Spawns the train saved as _MyTrain_                                              |
| Repetition        | `mmm`                                    | Spawns three rideable Minecarts                                                  |
| Amount Prefix     | `3m3s`                                   | Spawns three rideable Minecarts and three Minecarts with Chest as a 6-cart train |
| Grouped Sequences | `3[ms]`                                  | Spawns 3 pairs of a rideable Minecart and Minecart with Chest. Same as `msmsms`  |
| Random            | `3[33%RedCart 33%GreenCart 33%BlueCart]` | Spawns a 3-cart train with random color carts that were previous saved           |

### Vanilla Minecarts

Default Vanilla Minecarts can be specified with the single-character names below:

| Text | Minecart type                                                                   |
| ---- | ------------------------------------------------------------------------------- |
| m    | [Regular Minecart](https://minecraft.wiki/w/Minecart)                           |
| p    | [Powered Minecart](https://minecraft.wiki/w/Minecart_with_Furnace)              |
| s    | [Storage Minecart](https://minecraft.wiki/w/Minecart_with_Chest)                |
| t    | [TNT Minecart](https://minecraft.wiki/w/Minecart_with_TNT)                      |
| h    | [Hopper minecart](https://minecraft.wiki/w/Minecart_with_Hopper)                |
| e    | [Minecart with Spawner](https://minecraft.wiki/w/Minecart_with_Monster_Spawner) |

For example, this [spawn sign](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Signs/Spawner) spawns a 3-minecart train:

<figure><img src=".gitbook/assets/PixPin_2025-06-13_13-07-06 (4).png" alt="" width="375"><figcaption></figcaption></figure>

And this command gives the player a [train spawn chest](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Train_Spawn_Chest) that spawns a 3-minecart train:

```
/train chest mmm
```

### Saved Trains

Players can use `/train save [name]` to save the train they are [editing](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Editing) as a _saved train_. This name can then be used in a spawn pattern.

* When matching a saved train name, the longest name that matches is selected
* Saved train names can be listed with command: `/savedtrain list`
* Saved trains can be imported or edited with command: `/savedtrain [name] [subcommand]`
* Saved trains can also be included in a resource pack loaded on the server, like what the _TrainCarts Demo Resource Pack_
* Note: Saved train names are not the same as named trains (`/train rename`). There is no relation between the two.

For example, this [spawn sign](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Signs/Spawner) spawns a train named MyTrain:

<figure><img src=".gitbook/assets/PixPin_2025-06-13_13-07-06 (5).png" alt="" width="375"><figcaption></figcaption></figure>

And this command gives the player a [train spawn chest](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Train_Spawn_Chest) that spawns a train named MyTrain:

```
/train chest MyTrain
```

### Saved Spawn Patterns

Instead of saving a train, a (long) train spawning pattern can be saved instead with `/savedtrain [name] spawn [pattern]`.

For example:

```
/savedtrain MyTrain spawn 4[50%m 50%s] p
```

When spawning _MyTrain_ this will spawn 4 random rideable Minecarts or Minecart with chest, followed by a single Minecart with Furnace. This is especially useful when patterns are too long to fit on spawn signs. These patterns can be used recursively.

### Repetition

Multiple train names or Vanilla Minecart names can be put following each other, no space required. When matching the names, it matches the longest saved train name that matches the pattern.

### Amount Prefix

Digits can be put in front of names to repeat that pattern a number of times. If you want to spawn _MyTrain_ three times, you can put `3MyTrain`.

### Grouped Sequences

Patterns can be grouped so that the amount prefix repeats the entire group, instead of only the one train or cart specified.

For example, if you want to spawn a locomotive followed by red-green-blue carriages repeated four times (12 carriages), you can put:

```
4[carr carg carb] loco
```

### Random

Use the % weighted prefix to randomly have a pattern choose between different types of trains to spawn. This follows a syntax [similar to the WorldEdit syntax](https://worldedit.enginehub.org/en/latest/usage/general/patterns/#random-pattern).

For example, to spawn a locomotive followed by 12 carts of random red, green or blue carriages:

```
12[33%carr 33%carg 33%carb] loco
```

These prefixes can also be applied to grouped sequences to create variable-length trains. This will spawn a locomotive with randomly 0, 1 or 2 carriages:

```
[33%[] 33%carb 33%[carr carg]] loco
```

The percentage total is normalized, so in the above examples using 50% or 200% would have resulted in the same behavior.
