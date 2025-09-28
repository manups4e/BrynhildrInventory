---
title: "GridItem"
parent: Items
grand_parent: API Documentation
layout: default
---

# GridItem

![Image]({{ site.baseurl }}/images/griditem.png)

## Description:
Represents a grid item in the UI. Inherits from BaseItem and adds properties specific to inventory, weapons, and items with textures.

- Item can be represented in 2 ways:
  - Weapon Hash: give hash a weapon hash value and keep textures nil
  - Texture: set weapon hash to "" or 0 and set a texture dictionary and a texture name for the item.

{: .warning }
The texture takes precedence over the weapon hash. If both a weapon hash and a texture (dictionary and name) are provided, the texture will be used.

## Properties:

| Property               | Type                 | Description                           |
|------------------------|--------------------|---------------------------------------|
| `_amount`              | `number or string`  | Amount of the item.                   |
| `_hash`                | `number`            | Weapon hash identifier.               |
| `_name`                | `string`            | Item name.                             |
| `_description`         | `string`            | Item description.                      |
| `_textureDictionary`   | `string`            | Texture dictionary.                    |
| `_textureName`         | `string`            | Texture name.                          |
| `BGColor`              | `SColor`            | Background color.                      |
| `CountourColor`        | `SColor`            | Outline color.                         |
| `HighlightColor`       | `SColor`            | Highlight color.                       |

## Methods

| Method| Return Type| Description|
|---------------|-------------------------------|-------------------------------------------------|
| `New(name, description, amount, weaponHash, txd?, txn?)`       | `GridItem`                    | Creates a new grid item.                        |
| `SetColors(bgColor, contourColor, highlightColor)`            | `void`                        | Sets item colors using [SColor]({{ site.baseurl }}/api/elements/scolor) custom class.                               |
| `Amount(value?: number or string)`                             | `number or string or GridItem`| Get or set amount, you can send a number to only visualize it or a string like "x10". To **get** leave input empty                              |
| `Hash(value?: number)`                                         | `number or GridItem`          | Get or set weapon hash. To **get** leave input empty                        |
| `Name(value?: string)`                                         | `string or GridItem`          | Get or set item name. To **get** leave input empty                           |
| `Description(value?: string)`                                  | `string or GridItem`          | Get or set item description. To **get** leave input empty                   |
| `UpdateTexture(txd: string, txn: string)`                      | `void`                        | Set the texture dictionary and name.           |

## Example:

```lua
local gridItem = GridItem.New("Pistol", "A standard pistol", 10, 453432689)
gridItem:SetColors(SColor.FromArgb(255,0,0,0), SColor.FromArgb(255,255,255,255), SColor.FromArgb(255,255,0,0))
gridItem:Amount(5)
gridItem:UpdateTexture("weapons", "pistol")
```