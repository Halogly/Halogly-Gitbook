---
description: 本页面主要讲解如何向服务器添加新声音。
---

# 🔊 声音

## 🔊 声音

## 声音 <a href="#sound" id="sound"></a>

```yaml
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

当使用 `/playsound` 命令播放声音时，实际上应该称为执行声音事件，实际的声音位于 `sounds` 列表中。你可以查看 Minecraft Wiki 了解每个参数对应的效果。插件在这里没有提供详细描述，因为 Minecraft Wiki 每个部分已经讲得非常清楚，并且 CraftEngine 使用与 Wiki 中描述相同的配置选项名称。

## 唱片机歌曲（1.21+） <a href="#jukebox-song-1.21" id="jukebox-song-1.21"></a>

由于 Minecraft 的注册表一旦注册就不可变，因此你需要重启服务器才能应用任何新修改。但是，你可以通过修改配置ID实时注册一首新歌。

```yaml
jukebox_songs:
  default:credits_music:
    sound: minecraft:music.credits
    length: 100.0  # 音乐时长（秒）
    description: "Credits"  
    comparator-output: 15
    range: 32
```

```yaml
items:
  default:music_stick:
    material: stick
    data:
      jukebox-playable: default:credits_music
```
