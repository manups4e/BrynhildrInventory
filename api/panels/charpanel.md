---
title: "CharPanel"
parent: Panels
grand_parent: API Documentation
layout: default
---

# CharPanel

The **CharPanel** is a panel derived from [`BasePanel`](./BasePanel.md).  
It displays the **silhouette of a male or female character** with body-part health indicators and up to **9 equipment slots**.  

![Image]({{ site.baseurl }}/images/charpanel.png)


This panel is mainly used to:
- Show the **status of each body part** (head, torso, arms, hands, legs, feet).
- Display the **character’s equipped items** (weapons, armor, utilities, etc.).
- Provide a clear overview of the player’s **current loadout**.

## Example Use Case
```lua
-- Creating and populating a character loadout
local loadoutChar = CharPanel.New("Loadout")

loadoutChar:SetSlot(1, "BACKPACK", "testtxd", "bag")
loadoutChar:SetSlot(2, "ARMOUR", "testtxd", "armor")
loadoutChar:SetSlot(3, "PHONE", "testtxd", "blue_phone")
loadoutChar:SetSlot(4, "RESERVED 1", "", "")
loadoutChar:SetSlot(5, "RESERVED 2", "", "")
loadoutChar:SetSlot(6, "RESERVED 3", "", "")
loadoutChar:SetSlot(7, "SECONDARY WEAPON", "testtxd", "weapon_compactrifle")
loadoutChar:SetSlot(8, "PRIMARY WEAPON", "testtxd", "mp5")
loadoutChar:SetSlot(9, "PARACHUTE", "testtxd", "parachute_blue")
```

## Properties

| Name      | Type       | Description |
|-----------|------------|-------------|
| `Gender`  | `number`   | Character gender (`0 = male`, `1 = female`). |
| `Title`   | `string`   | Panel title. |
| `Head`    | `number`   | Head body-part slot. |
| `Torso`   | `number`   | Torso body-part slot. |
| `Arm_l`   | `number`   | Left arm body-part slot. |
| `Arm_r`   | `number`   | Right arm body-part slot. |
| `Hand_l`  | `number`   | Left hand body-part slot. |
| `Hand_r`  | `number`   | Right hand body-part slot. |
| `Leg_l`   | `number`   | Left leg body-part slot. |
| `Leg_r`   | `number`   | Right leg body-part slot. |
| `Foot_l`  | `number`   | Left foot body-part slot. |
| `Foot_r`  | `number`   | Right foot body-part slot. |
| `Parent`  | `BaseTab`   | Reference to the parent tab. |
| `IsVisible`   | `boolean`  | Indicates whether the panel is currently visible. |

---

## Methods

| Name | Parameters | Returns | Description |
|------|------------|---------|-------------|
| `SetSlot` | `(id: number, label: string, txd: string, txn: string, weaponHash: number)` | `CharPanel` | Sets an equipment slot with label, texture, and optional weapon hash (same as GridItem logic). |
| `SetBodyParts` | `(head, torso, arm_l, arm_r, hand_l, hand_r, leg_l, leg_r, foot_l, foot_r: number)` | `void` | Defines the state of each body part. Check  [BodyPartState]({{ site.baseurl }}/api/elements/enums) for the values |
| `SetGender` | `(gender: number)` | `CharPanel` | Sets the character’s gender (0 = Male, 1 = Female). |
| `SetVisible`         | `state?: boolean` | `BasePanel` | Shows or hides the panel; returns the panel instance. |
| `Clear()`| — | — | | Clears all stats and resets the panel |
| `Populate()` | — | — | Initializes the panel in the scaleform. |
| `ShowPanel()` | — | — | Displays the panel and sets background color. |

## Enum used for SetBodyParts function
`BodyPartState` represents the health or condition of a character's body part.

| Name      | Value | Description                   |
|-----------|-------|-------------------------------|
| DISABLED  | -1    | Body part is not active       |
| HEALTHY   | 0     | Body part is healthy (green)         |
| DAMAGED   | 1     | Body part is damaged (yellow)         |
| DANGER    | 2     | Body part is in critical state (red) |

## Example
```lua
-- using numbers
loadoutChar:SetBodyParts(-1, 0, 1, 2, -1, 0, 1, 2, -1, 0)

loadoutChar:SetBodyParts(BodyPartState.DISABLED, BodyPartState.HEALTHY, BodyPartState.DAMAGED, BodyPartState.DANGER, BodyPartState.DISABLED, BodyPartState.  HEALTHY, BodyPartState.DAMAGED, BodyPartState.DANGER, BodyPartState.DISABLED, BodyPartState.HEALTHY)

```
This example shows how to update the LorePanel with a long vertical text description for an object or item, you can change its description using OnIndexChange to allow each item to show.
