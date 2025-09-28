---
title: "Grid5by5"
parent: Tabs
grand_parent: API Documentation
nav_order: 3
layout: default
---

# Grid5by5

`Grid5by5` is a tab that inherits from `BaseTab` and displays a center grid with 5 columns by 5 rows.
It is designed to handle items in a structured grid, shows a description panel at the bottom, supports contextual menus (`ContextColumn`) for each item, and provides a callback when the selected index changes.

![Image]({{ site.baseurl }}/images/grid5by5tab.png)

---

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `CenterPanel` | `Grid5by5Column` | The main center grid containing all items. |
| `LeftPanel` | `BasePanel children` | The panel on the left side of the grid, optional and can be hidden or changed on need
| `RightPanel` | `BasePanel children` | The panel on the right side of the grid, optional and can be hidden or changed on need
| `BottomPanel` | `DescriptionPanel` | Panel used exclusively to display the description of the currently selected item. Cannot be replaced with other panels. |
| `_identifier` | `string` | Internal tab identifier. |
| `textureDict` | `string` | Texture dictionary used for the tab. |
| `textureFileName` | `string` | Texture file name used for the tab. |
| `OnIndexChange` | `fun(item:GridItem, index:integer)` | Callback triggered whenever the selection in the center grid changes. |

---

## Methods

| Method | Parameters | Returns | Description |
|--------|------------|---------|-------------|
| `New(name, txd, txn)` | `name:string`, `txd:string`, `txn:string` | `Grid5by5` | Creates a new `Grid5by5` tab with a given name and textures. |
| `AddItem(item)` | `item:GridItem` | - | Adds an item to the center grid. |
| `RemoveItem(index)` | `index:number` | - | Removes the item at the specified index from the center grid and updates the bottom description panel. |
| `CurrentSelection(index?)` | `index:number|nil` | `GridItem` | Gets or sets the currently selected item in the center grid. |
| `Populate()` | - | - | Populates all panels and the center grid with their items. |
| `ShowColumns()` | - | - | Displays all panels and the center grid. |
| `GoUp()` | - | - | Navigates up in the center grid and updates the bottom panel. |
| `GoDown()` | - | - | Navigates down in the center grid and updates the bottom panel. |
| `GoLeft()` | - | - | Navigates left in the center grid and updates the bottom panel. |
| `GoRight()` | - | - | Navigates right in the center grid and updates the bottom panel. |
| `Select()` | - | - | Opens the context menu (`ContextColumn`) for the currently selected item. |
| `HandleInput()` | - | - | Handles user input for navigation, selection, and context menu interaction. |

---

## Notes

- The `BottomPanel` is exclusively a **description panel** and cannot be replaced by other panels. Its only purpose is to show details for the currently selected grid item.  
- `ContextColumn` is automatically populated when `Select()` is called and appears above the selected item in the center grid.  
- Navigation methods (`GoUp`, `GoDown`, `GoLeft`, `GoRight`) automatically update the `BottomPanel` and trigger the `OnIndexChange` callback.

## Example:
```lua
-- create the tab
local tab5by5 = Grid5by5.New("Grid Tab", "testtxd", "bag")
-- add the tab to the inventory
inventory:AddTab(tab5by5)
-- create the Left panel as a LorePanel
local gridLorePanel = LorePanel.New("Lore Panel")
tab5by5:SetupLeftPanel(gridLorePanel)
-- create right panel without caching it in a parameter... unusual but allowed
tab5by5:SetupRightPanel(DetailsPanel.New("Item Details"))

-- set the istructional buttons to the panel
tab5by5.IBPanel:AddItem({Label="Move", Control="~INPUTGROUP_FRONTEND_DPAD_ALL~"})
tab5by5.IBPanel:AddItem({Label="Change Tab", Control="~INPUTGROUP_FRONTEND_BUMPERS~"})
tab5by5.IBPanel:AddItem({Label="Select", Control="~INPUT_FRONTEND_ACCEPT~"})
tab5by5.IBPanel:AddItem({Label="Back", Control="~INPUT_FRONTEND_CANCEL~"})

-- Add the context options to the context menu
-- it can be unique for all the tab items.
local gridUseItem = ContextItem.New("Use")
local gridThrowItem = ContextItem.New("Throw", 1, 3, 1)
tab5by5.Context:AddItem(gridUseItem)
tab5by5.Context:AddItem(gridThrowItem)

-- or it can be reset and re-created per item using OnIndexChange event called everytime you move the selection around
tab5by5.OnIndexChange = function(item, index)
    -- clear the items in the context menu
    tab5by5.Context:ClearItems()
    local gridUseItem = ContextItem.New("Use")
    local gridThrowItem = ContextItem.New("Throw", 1, item:Amount(), 1) -- if amount is a number.. if not you handle it as a string and convert it into a number
    -- add the items back into the context menu.
    tab5by5.Context:AddItem(gridUseItem)
    tab5by5.Context:AddItem(gridThrowItem)
end


local item = GridItem.New("Pistol", "A simple Pistol to start your criminal career", 100, `weapon_pistol`) -- no texture since we gave a weapon hash
tab5by5:AddItem(item)
-- we call the internal Panels to change their background colors using SColor class
tab5by5.CenterPanel:SetBGColor(SColor.FromRandomValues())
tab5by5.LeftPanel:SetBGColor(SColor.FromRandomValues())
tab5by5.RightPanel:SetBGColor(SColor.FromRandomValues())
```