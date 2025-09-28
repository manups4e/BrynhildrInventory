---
title: "HUD Colours"
parent: Utility Elements
grand_parent: API Documentation
layout: default
---

# Hud Colours

The **HudColours** enum defines a wide range of HUD (Heads-Up Display) colors that can be used in panels, text, blips, and other UI elements. Each color has a numeric value associated with it.

## Values

| Name | Value | Description |
|------|-------|-------------|
| NONE | -1 | No color assigned |
| HUD_COLOUR_PURE_WHITE | 0 | Pure white |
| HUD_COLOUR_WHITE | 1 | White |
| HUD_COLOUR_BLACK | 2 | Black |
| HUD_COLOUR_GREY | 3 | Grey |
| HUD_COLOUR_GREYLIGHT | 4 | Light grey |
| HUD_COLOUR_GREYDARK | 5 | Dark grey |
| HUD_COLOUR_RED | 6 | Red |
| HUD_COLOUR_REDLIGHT | 7 | Light red |
| HUD_COLOUR_REDDARK | 8 | Dark red |
| HUD_COLOUR_BLUE | 9 | Blue |
| HUD_COLOUR_BLUELIGHT | 10 | Light blue |
| HUD_COLOUR_BLUEDARK | 11 | Dark blue |
| HUD_COLOUR_YELLOW | 12 | Yellow |
| HUD_COLOUR_YELLOWLIGHT | 13 | Light yellow |
| HUD_COLOUR_YELLOWDARK | 14 | Dark yellow |
| HUD_COLOUR_ORANGE | 15 | Orange |
| HUD_COLOUR_ORANGELIGHT | 16 | Light orange |
| HUD_COLOUR_ORANGEDARK | 17 | Dark orange |
| HUD_COLOUR_GREEN | 18 | Green |
| HUD_COLOUR_GREENLIGHT | 19 | Light green |
| HUD_COLOUR_GREENDARK | 20 | Dark green |
| HUD_COLOUR_PURPLE | 21 | Purple |
| HUD_COLOUR_PURPLELIGHT | 22 | Light purple |
| HUD_COLOUR_PURPLEDARK | 23 | Dark purple |
| HUD_COLOUR_PINK | 24 | Pink |
| HUD_COLOUR_RADAR_HEALTH | 25 | Health color on radar |
| HUD_COLOUR_RADAR_ARMOUR | 26 | Armor color on radar |
| HUD_COLOUR_RADAR_DAMAGE | 27 | Damage color on radar |
| HUD_COLOUR_NET_PLAYER1 | 28 | Network player 1 color |
| HUD_COLOUR_NET_PLAYER2 | 29 | Network player 2 color |
| ... | ... | Network player 3-32, each incremented by 1 |
| HUD_COLOUR_SIMPLEBLIP_DEFAULT | 60 | Default blip color |
| HUD_COLOUR_MENU_BLUE | 61 | Menu blue |
| HUD_COLOUR_MENU_GREY_LIGHT | 62 | Light grey menu color |
| HUD_COLOUR_MENU_BLUE_EXTRA_DARK | 63 | Extra dark blue menu |
| HUD_COLOUR_MENU_YELLOW | 64 | Menu yellow |
| HUD_COLOUR_MENU_YELLOW_DARK | 65 | Dark menu yellow |
| HUD_COLOUR_MENU_GREEN | 66 | Menu green |
| HUD_COLOUR_MENU_GREY | 67 | Grey menu |
| HUD_COLOUR_MENU_GREY_DARK | 68 | Dark grey menu |
| HUD_COLOUR_MENU_HIGHLIGHT | 69 | Highlight color for menu items |
| HUD_COLOUR_MENU_STANDARD | 70 | Standard menu color |
| HUD_COLOUR_MENU_DIMMED | 71 | Dimmed menu color |
| HUD_COLOUR_MENU_EXTRA_DIMMED | 72 | Extra dimmed menu color |
| HUD_COLOUR_BRIEF_TITLE | 73 | Color for brief titles |
| HUD_COLOUR_MID_GREY_MP | 74 | Mid grey for multiplayer |
| HUD_COLOUR_NET_PLAYER1_DARK | 75 | Dark color for network player 1 |
| ... | ... | Dark colors for network players 2-32 |
| HUD_COLOUR_BRONZE | 107 | Bronze color |
| HUD_COLOUR_SILVER | 108 | Silver color |
| HUD_COLOUR_GOLD | 109 | Gold color |
| HUD_COLOUR_PLATINUM | 110 | Platinum color |
| HUD_COLOUR_GANG1 | 111 | Gang 1 color |
| HUD_COLOUR_GANG2 | 112 | Gang 2 color |
| HUD_COLOUR_GANG3 | 113 | Gang 3 color |
| HUD_COLOUR_GANG4 | 114 | Gang 4 color |
| HUD_COLOUR_SAME_CREW | 115 | Color for same crew members |
| HUD_COLOUR_FREEMODE | 116 | Freemode color |
| HUD_COLOUR_PAUSE_BG | 117 | Pause background color |
| HUD_COLOUR_FRIENDLY | 118 | Friendly color |
| HUD_COLOUR_ENEMY | 119 | Enemy color |
| HUD_COLOUR_LOCATION | 120 | Location marker color |
| HUD_COLOUR_PICKUP | 121 | Pickup color |
| HUD_COLOUR_PAUSE_SINGLEPLAYER | 122 | Pause single-player color |
| HUD_COLOUR_FREEMODE_DARK | 123 | Dark freemode color |
| HUD_COLOUR_INACTIVE_MISSION | 124 | Inactive mission color |
| HUD_COLOUR_DAMAGE | 125 | Damage indicator color |
| HUD_COLOUR_PINKLIGHT | 126 | Light pink |
| HUD_COLOUR_PM_MITEM_HIGHLIGHT | 127 | Highlight for mission items |
| HUD_COLOUR_SCRIPT_VARIABLE | 128 | Script variable color |
| ... | ... | Various special purpose colors, minigame colors, platform colors, character-specific colors, and UI colors up to 223 |

> ⚠️ **Note:** The enum covers hundreds of colors, including network player variants, menu variants, mission and activity indicators, platform-specific colors, and scripted UI colors. Use these constants to maintain consistency with the game's HUD color scheme.

## Example
```lua
HudColours.HUD_COLOUR_PURE_WHITE
```