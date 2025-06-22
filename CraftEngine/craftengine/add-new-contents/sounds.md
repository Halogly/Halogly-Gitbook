---
description: >-
  This page mainly explains how to add new sounds to your server.
  本页面主要解释如何向您的服务器添加新声音。
---

# 🔊 声音

### Sound  声音 <a href="#sound" id="sound"></a>

Copy  复制

```
sounds:
  minecraft:custom_block.place:
    replace: false
    subtitle: subtitles.custom_block.place
    sounds:
      - "block/custom_block_1"
  minecraft:custom_ambient.custom_biome:
    replace: false
    subtitle: subtitles.custom_ambient.custom_biome
    sounds:
      - name: "ambient/custom_biome_1"
        volume: 0.4
        weight: 3
      - name: "ambient/custom_biome_2"
        volume: 0.4
        weight: 7
      - name: "ambient/custom_biome_3"
        volume: 0.4
        weight: 10
        stream: false
        attenuation-distance: 16
        preload: false
        type: "file"
```

When you use the `/playsound` command to play a sound, it should actually be referred to as a sound event, while the actual sounds are located under the `sounds` list. You can check the [Minecraft Wiki](https://minecraft.wiki/w/Sounds.json) to understand the effects corresponding to each parameter. The plugin does not provide extensive descriptions here because the Minecraft Wiki already explains each part very clearly, and CraftEngine uses the same configuration option names as those described in the wiki.\
当您使用 `/playsound` 命令播放声音时，实际上应该称为声音事件，而实际的声音位于 `sounds` 列表中。您可以查看 Minecraft 维基来了解每个参数对应的效果。插件在这里没有提供详细描述，因为 Minecraft 维基已经非常清楚地解释了每个部分，而 CraftEngine 使用与维基中描述相同的配置选项名称。

### Jukebox Song (1.21+)  点唱机歌曲 (1.21+) <a href="#jukebox-song-1.21" id="jukebox-song-1.21"></a>

Due to the fact that Minecraft's registry becomes immutable once registered, you will need to restart the server in order to apply any new modifications. However, you can register a new song in real-time by modifying the configuration ID.\
由于 Minecraft 的注册表一旦注册就变为不可变，您需要重启服务器才能应用任何新的修改。但是，您可以通过修改配置 ID 实时注册一首新歌。

Copy  复制

```
jukebox_songs:
  default:credits_music:
    sound: minecraft:music.credits
    length: 100.0  # music length in seconds
    description: "Credits"  
    comparator-output: 15
    range: 32
```

Copy  复制

```
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```
