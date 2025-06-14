# Traincarts

**TrainCarts** is a plugin developed by Bergerkiller and features everything related to Trains of minecarts. It was initially developed to link multiple carts together, creating a moving train. Over time the plugin grew to host many more features, such as action signs, commands, properties, attachments and a broad API other plugins can implement to add their own features.

## Trains

The first thing you will notice is that you can now connect carts together to form infinitely long trains. Every cart in this train is called a _member_, all members combined are called a _group_. Every member communicates with the group, so when the front cart hits a block, it stops the entire group. When someone pushes a cart, this pushing force is shared among all members. Therefore, long trains are less responsive than short trains.

By default all minecarts placed by players become TrainCarts managed Minecarts. If you want to spawn Vanilla Minecarts that behave with original Minecraft Physics, you can do so through permissions or by spawning with a dispenser. [See this page for more information](https://wiki.traincarts.net/p/TrainCarts/VanillaMinecarts).

Mobs no longer get into Traincarts Minecarts by default. If you want to change this, [see this page for more information](https://wiki.traincarts.net/p/TrainCarts/MobEntering) or spawn vanilla minecarts instead.

## Spawning

Trains can be spawned by players using Minecart items or the [Train Spawn chest](https://wiki.traincarts.net/p/TrainCarts/Train_Spawn_Chest). They can be spawned automatically using the [spawn sign](https://wiki.traincarts.net/p/TrainCarts/Signs/Spawner).

[» Spawning](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Spawning)

[» Train Spawn Chest](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Train_Spawn_Chest)

## Properties

Trains and individual carts of trains have properties. These can be set using commands (/train and /cart) or using the [property sign](https://wiki.traincarts.net/p/TrainCarts/Signs/Property).

[» Property Sign](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Signs/Property)

## New physics

Trains can travel on top of pressure plates and alongside ladders, and also upside-down below vanilla rails placed on a ceiling.

[» Physical](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Physical)

## Signs

Loads of different signs are available to automate stations, eject trains, put players in trains or update train configuration.

## Command

The plugin has lots of commands you can use to alter the behavior of trains and minecarts.

[» Commands](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Commands)

## Command Selectors

You can use command selectors like _@train_ and _@ptrain_ in all other commands (including non-traincarts commands) to perform actions on trains or player passengers of trains based on selector criteria. For tighter integration with other plugins like economies and status effects, this is the ideal mechanism.

[» Command Selectors](https://wiki.traincarts.net/p/TrainCarts/Commands/Selectors)

## Path finding

Trains can have a destination set, after which switcher signs will automatically switch the track to lead the train towards it with the shortest route possible. This can be used to automate a large train network, sending trains to different stations fully automatically. It is also possible to configure a list of destinations the train should visit and have the train automatically go from one destination to the next.

[» Traincarts Path Finding](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/PathFinding)

## Tickets

Train ticket items can be used to restrict who can enter trains. They can also be used to assign properties to trains when used, such as assigning a destination to go to.

[» Traincarts Tickets](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Tickets)

## Configuration

TrainCarts can be configured in the config.yml file. All setting nodes have a header to help you understand what that particular node adjusts. Other than that, you can set the default train properties (properties applied to new trains) in the DefaultTrainProperties.yml file. The nodes should speak for themselves. Try not to touch the other files, as it can cause corrupted save data, or the plugin getting out of sync. Deleting the files should re-set TrainCarts completely, may one of the files get corrupted. The plugin automatically generates all configuration needed.

[» Train Properties](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/TrainProperties)

## Attachments

The attachment editor is used to configure the appearance of your train. The interactive menu enables players to configure customized trains using item models, entities, seats, sounds and more. All of these can be animated to bring the train alive.

[» Attachments](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Attachments)

## Permissions

Like in all plugins that use BKCommonLib as a base, all permissions can be found in PermissionDefaults.yml in the plugin folder. There they are all listed together with a description and permission default, which you can alter as well.

[» Overview of all permissions](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/Permissions)

## Performance

Some features by this plugin may result in server or client lag. There are ways to prevent them.

[» Lag](https://wiki.traincarts.net/p/TrainCarts/Lag)

## API and Add-ons

TrainCarts has a [flexible API](https://wiki.traincarts.net/p/TrainCarts/API) which allows other plugins to implement custom track, signs, attachments and more.

* [TC-Coasters](https://wiki.traincarts.net/p/Special:MyLanguage/TC-Coasters): Adds smooth rollercoaster track to TrainCarts
* [TC-Hangrail](https://www.spigotmc.org/resources/tc-hangrail.39627/): Hang below or float above any kind of block as fake track
* [TrainCartsDestinationSelector](https://www.spigotmc.org/resources/traincartsdestinationselector.73170/): Adds clickable signs so players can select train destinations
* [Traincarts AdvancedSigns](https://www.spigotmc.org/resources/traincarts-advancedsigns.99881/): Adds additional sign types, particularly useful for rollercoaster rides
* [TC Minecart Variants](https://www.spigotmc.org/resources/tcminecartvariants.100658/): Unique models for carts showing different types of resources (coal, gold, etc.)
* [TCAnimatronics](https://www.spigotmc.org/resources/tcanimatronics.101995/): Play [Animatronics](https://www.spigotmc.org/resources/animatronics-animate-armorstands-1-8-1-18-2.36518/) animations with a Traincarts sign

## Useful Links

* [Spigot Dev Page & Forum](https://www.spigotmc.org/resources/traincarts.39592/)
* [Discord](https://discord.gg/wvU2rFgSnw)

Traincarts [Spigot](https://www.spigotmc.org/resources/traincarts.39592/) [Jenkins](https://ci.mg-dev.eu/job/TrainCarts/) [GitHub](https://github.com/bergerhealer/TrainCarts)

BKCommonLib [Spigot](https://www.spigotmc.org/resources/bkcommonlib.39590/) [Jenkins](https://ci.mg-dev.eu/job/BKCommonLib/) [GitHub](https://github.com/bergerhealer/BKCommonLib)

TC Coasters [Spigot](https://www.spigotmc.org/resources/tc-coasters.59583/) [Jenkins](https://ci.mg-dev.eu/job/TC%20Coasters/) [GitHub](https://github.com/bergerhealer/TC-Coasters)

## Depreciated Addons

(No longer supported in current versions of Traincarts)

[ActionBlocks](https://wiki.traincarts.net/p/Special:MyLanguage/TrainCarts/ActionBlocks), added block-based systems to the game. They were dumbed-down versions of the sign systems mentioned above.

[TrainCartsBlocks GitHub Download Page](https://github.com/bergerkiller/TrainCartsBlocks/)

