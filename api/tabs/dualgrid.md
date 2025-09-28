---
title: "DualGrid"
parent: Tabs
grand_parent: API Documentation
nav_order: 4
layout: default
---

# DualGrid

`DualGrid` is a tab that inherits from `BaseTab` and displays two grids side by side within the center panel.  
It supports navigation between left and right grids, a bottom description panel, contextual menus (`ContextColumn`) for each item, and a callback when the selected index changes. The tab also supports switching behavior between grids depending on input type.

![Image]({{ site.baseurl }}/images/dualgrid.png)

---

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `CenterPanel` | `DualGridColumn` | The main center panel containing both left and right grids. |
| `BottomPanel` | `DescriptionPanel` | Panel used exclusively to display the description of the currently selected item. Cannot be replaced with other panels. |
| `_identifier` | `string` | Internal tab identifier. |
| `textureDict` | `string` | Texture dictionary used for the tab. |
| `textureFileName` | `string` | Texture file name used for the tab. |
| `OnIndexChange` | `fun(item:GridItem, index:integer)` | Callback triggered whenever the selection changes in either grid. |

---

## Methods

| Method | Parameters | Returns | Description |
|--------|------------|---------|-------------|
| `New(name, txd, txn)` | `name:string`, `txd:string`, `txn:string` | `DualGrid` | Creates a new `DualGrid` tab with a given name and textures. |
| `SetGridsTitles(leftGridTitle, rightGridTitle)` | `leftGridTitle:string`, `rightGridTitle:string` | - | Sets the titles of the left and right grids. |
| `AddLeftItem(item)` | `item:GridItem` | - | Adds an item to the left grid. |
| `AddRightItem(item)` | `item:GridItem` | - | Adds an item to the right grid and updates the bottom panel. |
| `RemoveLeftItem(index)` | `index:number` | - | Removes the item at the specified index from the left grid and updates the bottom panel. |
| `RemoveRightItem(index)` | `index:number` | - | Removes the item at the specified index from the right grid. |
| `CurrentSelection(gridIndex?, index?)` | `gridIndex:number|nil`, `index:number|nil` | `GridItem` | Gets or sets the currently selected item in the specified grid. |
| `SwitchType(switch:number)` | `switch:number` | - | Sets the tab switching type: `0 = Left-Right movement`, `1 = Frontend X (SpaceBar) control to switch grids`. |
| `Populate()` | - | - | Populates all panels and grids with their items. |
| `ShowColumns()` | - | - | Shows all columns/panels in the tab. |
| `GoUp()` | - | - | Navigates up in the current grid and updates the bottom panel. |
| `GoDown()` | - | - | Navigates down in the current grid and updates the bottom panel. |
| `GoLeft()` | - | - | Navigates left in the current grid. |
| `GoRight()` | - | - | Navigates right in the current grid. |
| `Select()` | - | - | Opens the context menu (`ContextColumn`) for the currently selected item. |
| `HandleInput()` | - | - | Handles user input for navigation, selection, context menus, and grid switching. |

---

## Notes

- The `BottomPanel` is exclusively a **description panel** and cannot be replaced by other panels. Its only purpose is to show details for the currently selected grid item.  
- `ContextColumn` is automatically populated when `Select()` is called and appears above the selected item in the current grid.  
- Navigation methods (`GoUp`, `GoDown`, `GoLeft`, `GoRight`) automatically update the `BottomPanel` and trigger the `OnIndexChange` callback.  
- The `SwitchType` method allows controlling how the user switches between left and right grids.

## DualGridSwitchType

`DualGridSwitchType` defines how a dual-grid interface can be switched.

| Name        | Value | Description                     |
|-------------|-------|---------------------------------|
| MOVEMENT    | 0     | Switch using movement keys      |
| FRONTEND_X  | 1     | Switch using the frontend X key |


## Example:
```lua
local dualGridTab = DualGrid.New("Dual Grid Tab", "testtxd", "popbox")
inventory:AddTab(dualGridTab)

dualGridTab:SetGridsTitles("Left Grid", "Right Grid")
dualGridTab.IBPanel:AddItem({Label="Move", Control="~INPUTGROUP_FRONTEND_DPAD_ALL~"})
dualGridTab.IBPanel:AddItem({Label="Change Tab", Control="~INPUTGROUP_FRONTEND_BUMPERS~"})
dualGridTab.IBPanel:AddItem({Label="Select", Control="~INPUT_FRONTEND_ACCEPT~"})
dualGridTab.IBPanel:AddItem({Label="Back", Control="~INPUT_FRONTEND_CANCEL~"})
dualGridTab.IBPanel:AddItem({Label="Switch grid", Control="~INPUT_FRONTEND_X~"})

-- if not specified, the left/right panels will not exist so won't be visible
-- local lootDetails = dualGridTab:SetupLeftPanel(PanelType.DETAILS_PANEL, "Item Details")
-- local lootStats = dualGridTab:SetupRightPanel(PanelType.STATS_PANEL, "Your Stats")

dualGridTab:SwitchType(DualGridSwitchType.FRONTEND_X) -- SpaceBar or X (square for PS controllers) on gamepad


local leftitem = GridItem.New("Pistol", "A simple Pistol to start your criminal career", 100, `weapon_pistol`) -- no texture since we gave a weapon hash

local rightitem = GridItem.New("Pistol", "A simple Pistol to start your criminal career", 100, "", "sometexture", "pistol") -- no weapon hash because we specify a texture.

dualGridTab:AddLeftItem(leftitem)
dualGridTab:AddRightItem(rightitem)
```