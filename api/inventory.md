---
title: "Inventory"
parent: API Documentation
layout: default
permalink: /inventory/
nav_order: 1
---

# Inventory

The `Inventory` class is the **main container** for all inventories.  
It manages tabs, visibility, callbacks, and input handling.  
Every specific inventory implementation derives from this class.

---

## Properties

| Name         | Type         | Description |
|--------------|-------------|-------------|
| `Tabs`       | `BaseTab[]` | List of all tabs contained in the inventory. |
| `index`      | `integer`   | Current active tab index (1-based). |
| `_Visible`   | `boolean`   | Internal state for inventory visibility. |
| `_canBuild`  | `boolean`   | Internal flag to allow building. |
| `_isBuilding`| `boolean`   | Internal flag to avoid drawing/inputs while building. |
| `TemporarilyHidden` | `boolean` | Optional flag used to temporarily hide the inventory without closing it. |

---

## Callbacks

Callbacks allow you to react to inventory events.  
They are **functions you can override** when creating your inventory instance.

| Callback | Signature | Description |
|----------|-----------|-------------|
| `OnTabChange`     | `(menu: Inventory, newTab: BaseTab)` | Triggered when the active tab changes. |
| `OnInventoryOpen` | `(menu: Inventory)` | Triggered when the inventory is opened. |
| `OnInventoryClose`| `(menu: Inventory)` | Triggered when the inventory is closed. |

---

## Methods

| Method | Signature | Description |
|--------|-----------|-------------|
| `New` | `Inventory.New(): Inventory` | Creates a new `Inventory` instance. |
| `Visible` | `Inventory:Visible(visible?: boolean): boolean` | Sets or gets the inventory visibility. When set to `true`, it initializes the scaleform and displays tabs triggering `OnInventoryOpen`. When set to `false`, it triggers `OnInventoryClose`. |
| `Index` | `Inventory:Index(idx?: integer): integer` | Sets or gets the current active tab index. Triggers `OnTabChange` when modified. |
| `AddTab` | `Inventory:AddTab(tab: BaseTab): BaseTab` | Adds a new tab to the inventory. Returns the tab added. |
| `CurrentTab` | `Inventory:CurrentTab(): BaseTab` | Returns the currently active tab. |
| `ProcessControl` | `Inventory:ProcessControl()` | Handles user input for switching tabs, going back, or delegating input to the current tab. |

---

{: .note}
> The inventory uses its own inputs to handle controls.  
> You can check more about game input controls at [FiveM Docs/Controls](https://docs.fivem.net/docs/game-references/controls/).  
>  
> Inputs are:  
> - **Move**: `Frontend Up (188)`, `Frontend Down (187)`, `Frontend Left (189)`, `Frontend Right (190)` — Controller: D-Pad / Keyboard: Arrows  
> - **Change Tab**: `Frontend LB (205)` — Controller: LB / Keyboard: Q  
>   `Frontend RB (206)` — Controller: RB / Keyboard: E  
>   `Frontend_RUP (192)` — Keyboard: TAB only  
> - **Change Grid**: `Frontend_X (203)` — Controller: X / Keyboard: Spacebar (used for dual grid switching)  
> - **Select**: `Frontend_Accept (201)` — Controller: A / Keyboard: Return  
> - **Back / Close inventory**: `Frontend_Cancel (202)` — Controller: B / Keyboard: Backspace or ESC
> 
> {: .warning}
> Controls cannot be changed, they are enforced, Instructional buttons for these controls are not automatically added, the choice is given to the developer.

---

## Usage Example

```lua
local inv = Inventory.New()

-- Add a tab
local myTab = Grid8by5.New("My Tab", txd, txn)
inv:AddTab(myTab)

-- React to tab change
inv.OnTabChange = function(menu, newTab)
    print("Changed to tab:", newTab.Title)
end

-- Show the inventory
inv:Visible(true)
```

## Notes

- The ProcessControl() method internally handles navigation (LB/RB), back actions, and delegates input handling to the current tab.
- The ProcessControl() method **MUST** be called on frame when drawing the scaleform to allow handling controls.
- The inventory uses Scaleform (BrynhildrInventory.gfx) for its rendering, and tabs are populated through their own Populate() and ShowColumns() methods.