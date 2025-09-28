---
title: "SColor"
parent: Utility Elements
grand_parent: API Documentation
layout: default
permalink: /api/elements/scolor/
---

# SColor

`SColor` is a class for handling RGBA colors and GTA HUD colors, with methods for conversion, random generation, and utility functions.

## Constructors

### `SColor.FromHex(hexColor: string) → SColor`

Creates an `SColor` object from a hexadecimal string.

### `SColor.FromRgb(red: number, green: number, blue: number) → SColor`

Creates a color from RGB values (alpha = 255).

### `SColor.FromArgb(...) → SColor`

Accepts either 1 ARGB integer or 4 separate values (A, R, G, B).

### `SColor.FromHudColor(color: HudColours) → SColor`

Creates a color from a defined HUD color in the game.

### `SColor.FromRandomValues() → SColor`

Generates a random color with alpha = 255.

## Instance Methods

* `GetBrightness() → number` : returns the color brightness (0-1)
* `GetHue() → number` : returns the hue (0-360)
* `GetSaturation() → number` : returns the saturation (0-1)
* `ToArgb() → number` : returns the color as an ARGB integer
* `ToHex() → string` : returns the color as a hexadecimal string
* `ToVector() → Vector4` : returns the color as a normalized vector (R, G, B, A) with values 0-1

## Properties

* `A: number` : alpha value (0-255)
* `R: number` : red value (0-255)
* `G: number` : green value (0-255)
* `B: number` : blue value (0-255)

## Examples

```lua
local white = SColor.White
local random = SColor.FromRandomValues()
print(random:ToHex())
```

# SColor Available Colors

## Predefined colors not present in game

| Color Name                       |
| -------------------------------- |
| Transparent                      |
| AliceBlue                        |
| AntiqueWhite                     |
| Aqua                             |
| Aquamarine                       |
| Azure                            |
| Beige                            |
| Bisque                           |
| Black                            |
| BlanchedAlmond                   |
| Blue                             |
| BlueViolet                       |
| Brown                            |
| BurlyWood                        |
| CadetBlue                        |
| Chartreuse                       |
| Chocolate                        |
| Coral                            |
| CornflowerBlue                   |
| Cornsilk                         |
| Crimson                          |
| Cyan                             |
| DarkBlue                         |
| DarkCyan                         |
| DarkGoldenrod                    |
| DarkGray                         |
| DarkGreen                        |
| DarkKhaki                        |
| DarkMagenta                      |
| DarkOliveGreen                   |
| DarkOrange                       |
| DarkOrchid                       |
| DarkRed                          |
| DarkSalmon                       |
| DarkSeaGreen                     |
| DarkSlateBlue                    |
| DarkSlateGray                    |
| DarkTurquoise                    |
| DarkViolet                       |
| DeepPink                         |
| DeepSkyBlue                      |
| DimGray                          |
| DodgerBlue                       |
| Firebrick                        |
| FloralWhite                      |
| ForestGreen                      |
| Fuchsia                          |
| Gainsboro                        |
| GhostWhite                       |
| Gold                             |
| Goldenrod                        |
| Gray                             |
| Green                            |
| GreenYellow                      |
| Honeydew                         |
| HotPink                          |
| IndianRed                        |
| Indigo                           |
| Ivory                            |
| Khaki                            |
| Lavender                         |
| LavenderBlush                    |
| LawnGreen                        |
| LemonChiffon                     |
| LightBlue                        |
| LightCoral                       |
| LightCyan                        |
| LightGoldenrodYellow             |
| LightGreen                       |
| LightGray                        |
| LightPink                        |
| LightSalmon                      |
| LightSeaGreen                    |
| LightSkyBlue                     |
| LightSlateGray                   |
| LightSteelBlue                   |
| LightYellow                      |
| Lime                             |
| LimeGreen                        |
| Linen                            |
| Magenta                          |
| Maroon                           |
| MediumAquamarine                 |
| MediumBlue                       |
| MediumOrchid                     |
| MediumPurple                     |
| MediumSeaGreen                   |
| MediumSlateBlue                  |
| MediumSpringGreen                |
| MediumTurquoise                  |
| MediumVioletRed                  |
| MidnightBlue                     |
| MintCream                        |
| MistyRose                        |
| Moccasin                         |
| NavajoWhite                      |
| Navy                             |
| OldLace                          |
| Olive                            |
| OliveDrab                        |
| Orange                           |
| OrangeRed                        |
| Orchid                           |
| PaleGoldenrod                    |
| PaleGreen                        |
| PaleTurquoise                    |
| PaleVioletRed                    |
| PapayaWhip                       |
| PeachPuff                        |
| Peru                             |
| Pink                             |
| Plum                             |
| PowderBlue                       |
| Purple                           |
| Red                              |
| RosyBrown                        |
| RoyalBlue                        |
| SaddleBrown                      |
| Salmon                           |
| SandyBrown                       |
| SeaGreen                         |
| SeaShell                         |
| Sienna                           |
| Silver                           |
| SkyBlue                          |
| SlateBlue                        |
| SlateGray                        |
| Snow                             |
| SpringGreen                      |
| SteelBlue                        |
| Tan                              |
| Teal                             |
| Thistle                          |
| Tomato                           |
| Turquoise                        |
| Violet                           |
| Wheat                            |
| White                            |
| WhiteSmoke                       |
| Yellow                           |
| YellowGreen                      |

## Predefined colors from Game's HUD Colours

| Color Name                       |
| -------------------------------- |
| HUD_None                         |
| HUD_Pure_white                   |
| HUD_White                        |
| HUD_Black                        |
| HUD_Grey                         |
| HUD_Greylight                    |
| HUD_Greydark                     |
| HUD_Red                          |
| HUD_Redlight                     |
| HUD_Reddark                      |
| HUD_Blue                         |
| HUD_Bluelight                    |
| HUD_Bluedark                     |
| HUD_Yellow                       |
| HUD_Yellowlight                  |
| HUD_Yellowdark                   |
| HUD_Orange                       |
| HUD_Orangelight                  |
| HUD_Orangedark                   |
| HUD_Green                        |
| HUD_Greenlight                   |
| HUD_Greendark                    |
| HUD_Purple                       |
| HUD_Purplelight                  |
| HUD_Purpledark                   |
| HUD_Pink                         |
| HUD_Radar_health                 |
| HUD_Radar_armour                 |
| HUD_Radar_damage                 |
| HUD_Net_player1                  |
| HUD_Net_player2                  |
| HUD_Net_player3                  |
| HUD_Net_player4                  |
| HUD_Net_player5                  |
| HUD_Net_player6                  |
| HUD_Net_player7                  |
| HUD_Net_player8                  |
| HUD_Net_player9                  |
| HUD_Net_player10                 |
| HUD_Net_player11                 |
| HUD_Net_player12                 |
| HUD_Net_player13                 |
| HUD_Net_player14                 |
| HUD_Net_player15                 |
| HUD_Net_player16                 |
| HUD_Net_player17                 |
| HUD_Net_player18                 |
| HUD_Net_player19                 |
| HUD_Net_player20                 |
| HUD_Net_player21                 |
| HUD_Net_player22                 |
| HUD_Net_player23                 |
| HUD_Net_player24                 |
| HUD_Net_player25                 |
| HUD_Net_player26                 |
| HUD_Net_player27                 |
| HUD_Net_player28                 |
| HUD_Net_player29                 |
| HUD_Net_player30                 |
| HUD_Net_player31                 |
| HUD_Net_player32                 |
| HUD_Simpleblip_default           |
| HUD_Menu_blue                    |
| HUD_Menu_grey_light              |
| HUD_Menu_blue_extra_dark         |
| HUD_Menu_yellow                  |
| HUD_Menu_yellow_dark             |
| HUD_Menu_green                   |
| HUD_Menu_grey                    |
| HUD_Menu_grey_dark               |
| HUD_Menu_highlight               |
| HUD_Menu_standard                |
| HUD_Menu_dimmed                  |
| HUD_Menu_extra_dimmed            |
| HUD_Brief_title                  |
| HUD_Mid_grey_mp                  |
| HUD_Net_player1_dark             |
| HUD_Net_player2_dark             |
| HUD_Net_player3_dark             |
| HUD_Net_player4_dark             |
| HUD_Net_player5_dark             |
| HUD_Net_player6_dark             |
| HUD_Net_player7_dark             |
| HUD_Net_player8_dark             |
| HUD_Net_player9_dark             |
| HUD_Net_player10_dark            |
| HUD_Net_player11_dark            |
| HUD_Net_player12_dark            |
| HUD_Net_player13_dark            |
| HUD_Net_player14_dark            |
| HUD_Net_player15_dark            |
| HUD_Net_player16_dark            |
| HUD_Net_player17_dark            |
| HUD_Net_player18_dark            |
| HUD_Net_player19_dark            |
| HUD_Net_player20_dark            |
| HUD_Net_player21_dark            |
| HUD_Net_player22_dark            |
| HUD_Net_player23_dark            |
| HUD_Net_player24_dark            |
| HUD_Net_player25_dark            |
| HUD_Net_player26_dark            |
| HUD_Net_player27_dark            |
| HUD_Net_player28_dark            |
| HUD_Net_player29_dark            |
| HUD_Net_player30_dark            |
| HUD_Net_player31_dark            |
| HUD_Net_player32_dark            |
| HUD_Bronze                       |
| HUD_Silver                       |
| HUD_Gold                         |
| HUD_Platinum                     |
| HUD_Gang1                        |
| HUD_Gang2                        |
| HUD_Gang3                        |
| HUD_Gang4                        |
| HUD_Same_crew                    |
| HUD_Freemode                     |
| HUD_Pause_bg                     |
| HUD_Friendly                     |
| HUD_Enemy                        |
| HUD_Location                     |
| HUD_Pickup                       |
| HUD_Pause_singleplayer           |
| HUD_Freemode_dark                |
| HUD_Inactive_mission             |
| HUD_Damage                       |
| HUD_Pinklight                    |
| HUD_Pm_mitem_highlight           |
| HUD_Script_variable              |
| HUD_Yoga                         |
| HUD_Tennis                       |
| HUD_Golf                         |
| HUD_Shooting_range               |
| HUD_Flight_school                |
| HUD_North_blue                   |
| HUD_Social_club                  |
| HUD_Platform_blue                |
| HUD_Platform_green               |
| HUD_Platform_grey                |
| HUD_Facebook_blue                |
| HUD_Ingame_bg                    |
| HUD_Darts                        |
| HUD_Waypoint                     |
| HUD_Michael                      |
| HUD_Franklin                     |
| HUD_Trevor                       |
| HUD_Golf_p1                      |
| HUD_Golf_p2                      |
| HUD_Golf_p3                      |
| HUD_Golf_p4                      |
| HUD_Waypointlight                |
| HUD_Waypointdark                 |
| HUD_Panel_light                  |
| HUD_Michael_dark                 |
| HUD_Franklin_dark                |
| HUD_Trevor_dark                  |
| HUD_Objective_route              |
| HUD_Pausemap_tint                |
| HUD_Pause_deselect               |
| HUD_Pm_weapons_purchasable       |
| HUD_Pm_weapons_locked            |
| HUD_End_screen_bg                |
| HUD_Chop                         |
| HUD_Pausemap_tint_half           |
| HUD_North_blue_official          |
| HUD_Script_variable_2            |
| HUD_H                            |
| HUD_Hdark                        |
| HUD_T                            |
| HUD_Tdark                        |
| HUD_Hshard                       |
| HUD_Controller_michael           |
| HUD_Controller_franklin          |
| HUD_Controller_trevor            |
| HUD_Controller_chop              |
| HUD_Video_editor_video           |
| HUD_Video_editor_audio           |
| HUD_Video_editor_text            |
| HUD_Hb_blue                      |
| HUD_Hb_yellow                    |
| HUD_Video_editor_score           |
| HUD_Video_editor_audio_fadeout   |
| HUD_Video_editor_text_fadeout    |
| HUD_Video_editor_score_fadeout   |
| HUD_Heist_background             |
| HUD_Video_editor_ambient         |
| HUD_Video_editor_ambient_fadeout |
| HUD_Gb                           |
| HUD_G                            |
| HUD_B                            |
| HUD_Low_flow                     |
| HUD_Low_flow_dark                |
| HUD_G1                           |
| HUD_G2                           |
| HUD_G3                           |
| HUD_G4                           |
| HUD_G5                           |
| HUD_G6                           |
| HUD_G7                           |
| HUD_G8                           |
| HUD_G9                           |
| HUD_G10                          |
| HUD_G11                          |
| HUD_G12                          |
| HUD_G13                          |
| HUD_G14                          |
| HUD_G15                          |
| HUD_Adversary                    |
| HUD_Degen_red                    |
| HUD_Degen_yellow                 |
| HUD_Degen_green                  |
| HUD_Degen_cyan                   |
| HUD_Degen_blue                   |
| HUD_Degen_magenta                |
| HUD_Stunt_1                      |
| HUD_Stunt_2                      |
| HUD_Special_race_series          |
| HUD_Special_race_series_dark     |
| HUD_Cs                           |
| HUD_Cs_dark                      |
| HUD_Tech_green                   |
| HUD_Tech_green_dark              |
| HUD_Tech_red                     |
| HUD_Tech_green_very_dark         |

** Example: **
```lua
SColor.HUD_Tech_red
```