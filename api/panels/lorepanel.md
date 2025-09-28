---
title: "LorePanel"
parent: Panels
grand_parent: API Documentation
layout: default
---

# LorePanel

![Image]({{ site.baseurl }}/images/lorepanel.png)

`LorePanel` is used to display long vertical text, such as the story or content of an object, book, or document. It is similar to `DescriptionPanel` but shows vertically to allow for longer content.

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `Title` | string | Panel title. |
| `Description` | string | Panel description text. |
| `IsVisible`   | `boolean`  | Indicates whether the panel is currently visible. |

## Methods

| Method | Parameters | Returns | Description |
|--------|------------|---------|-------------|
| `UpdateDescription(title, desc)` | `title: string`, `desc: string` | — | Updates the panel's title and description. |
| `Clear()`| — | — | | Clears all stats and resets the panel |
| `Populate()` | — | — | Initializes the panel in the scaleform. |
| `ShowPanel()` | — | — | Displays the panel and sets background color. |
| `SetVisible`         | `state?: boolean` | `BasePanel` | Shows or hides the panel; returns the panel instance. |

## Example
```lua
gridLorePanel:UpdateDescription("Lore Panel",
    "An ancient artifact blackened by time, its surface carved with twisted symbols and deep scratches. " ..
    "Those who hold it feel a chilling shiver crawl down their spine, as if a thousand voices whispered in a forgotten tongue. " ..
    "It is said to have been forged to inflict unspeakable torment, trapping the victim’s soul in an endless cycle of agony."
)
```
This example shows how to update the LorePanel with a long vertical text description for an object or item, you can change its description using OnIndexChange to allow each item to show.
