# Sephiria Emoji Ping

[한국어](README.md) · [English](README.en.md) · [日本語](README.ja.md) · [简体中文](README.zh-CN.md)

A Sephiria mod that displays an emoji centered above your character's head. Includes five original game emojis and supports custom PNG animations. Current public version: **1.0.2**.

## Installation

Download **EmojiPing-1.0.2.zip** from [Releases](https://github.com/TaeHyun015/EmojiPing/releases). Close the game, copy the archive's `AddOns/EmojiPing` folder into the game's `AddOns` directory, and launch the game. Preserve your existing `pack.json` and `Images` when updating manually. Uses the game's built-in mod loader; BepInEx is not required.

## How to use

1. Hold **backquote (the key to the left of 1)**, or your configured emoji key.
2. Move the mouse into an emoji slot and release the key.
3. Release over empty space or press **Esc** to cancel.

Five slots form a regular pentagon, with a bright border on the selected slot. Other counts are arranged automatically. The game's middle-click ping remains available.

- Change the key in **Settings → Keyboard → Emoji selection (EP)**.
- Reload images through **Emoji images (EP) → Reload** in the same tab, or **Ctrl + your emoji key**. Setting labels may appear in Korean.
- Default display duration: 2.5 seconds; cooldown: 0.75 seconds.

## Custom emojis

Create a folder per emoji under `Images`, with frames named `1.png`, `2.png`, … `8.png`. One frame produces a still image. Numbers must be consecutive, and every frame must have the same dimensions.

| Item | Limit |
|---|---|
| Recommended canvas | 16×16 or 24×24, matching the display size |
| Maximum source canvas | 64×64 per frame |
| Display size | 8–24 logical pixels on the longer side |
| Format | 8-bit RGBA PNG; transparent background recommended |
| Animation | Up to 8 frames, 1–12 FPS |
| Size and count | Up to 1 MiB per emoji, 8 emoji types per pack |

Use a pixel pencil and avoid antialiasing and blur. **Register new folders in the `emojis` array of `pack.json`**; folders are not discovered automatically. For example, add this entry for 24×24 frames in `Images/my-heart`:

```json
{"id":"my-heart","name":"Heart","folder":"my-heart","fps":8,"displayPixels":24}
```

Save and reload images to apply changes. The archive's `Templates` folder includes transparent frames and an eight-frame thumbs-up example.

## Multiplayer

Players using the same latest mod version share their own custom emojis directly in Steam lobbies. Mod users see **EP badges** to the right of player names in the multiplayer list. Players without the mod see neither the badges nor mod emojis. Sharing is implemented independently of the host's mod installation; local playback remains available if direct communication is unavailable.

## Automatic updates

When the game loads the mod, it checks this repository's latest stable Release. If a newer version is available, an in-game prompt offers to download it, close the game, install the update, and restart. **Save your progress first.** Custom images, pack settings, and your key binding are preserved.

`EmojiPing-update.zip` is for automatic updates of existing installations. Use the full ZIP for first-time installation. To disable checks, create an empty `disable-updates.txt` in the mod folder. Failures are logged in `__EmojiPing_Update.log` in the game directory and in `Player.log`.
