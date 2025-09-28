---
title: "DualGridColumn"
parent: Columns
grand_parent: API Documentation
layout: default
nav_order: 4
---

# DualGridColumn

The **`DualGridColumn`** class represents a column organized into two adjacent grids,  
designed to display two sets of items within the same space.  
It inherits all functionalities from [`BaseColumn`](BaseColumn.md).

---

## Main Features

- Dual-grid layout (two separate sections).  
- Used internally in **Tabs** for complex or dual-panel inventories.  
- Allows visually separating two groups of items while sharing the same system.  
- Introduces additional functionalities specific to managing and interacting with both grids.

---

## Properties

| Name | Type | Access | Description |
|------|------|--------|-------------|
| `leftGrid` | `DualGridSingleColumn` | private | Left grid column used internally. |
| `rightGrid` | `DualGridSingleColumn` | private | Right grid column used internally. |
| `leftTitle` | `string` | private | Title of the left grid. |
| `rightTitle` | `string` | private | Title of the right grid. |
| `currentGridIndex` | `number` | private | Index of the currently active grid (0 = left, 1 = right). |

## Methods

| Name | Parameters | Return | Description |
|------|------------|--------|-------------|
| `GetCurrentGrid` | — | `DualGridSingleColumn` | Returns the currently active grid. |
| `SwitchGrid` | — | — | Switches the active grid to the other one. |
| `SetTitle` | `left:string`, `right:string` | — | Sets the titles for left and right grids. |
| `ShowColumn` | — | — | Displays both grids on the scaleform. |
| `CurrentSelection` | `grid:number|nil`, `index:number|nil` | `any` | Gets or sets the current selection in the active grid. |
| `CurrentItem` | — | `BaseItem|nil` | Returns the currently selected item from the active grid. |
| `AddLeftItem` | `item:BaseItem` | — | Adds an item to the left grid. |
| `AddRightItem` | `item:BaseItem` | — | Adds an item to the right grid. |
| `RemoveLeftItem` | `index:number` | — | Removes an item from the left grid by index. |
| `RemoveRightItem` | `index:number` | — | Removes an item from the right grid by index. |
| `Populate` | — | — | Populates both grids and shows them. |
| `GoUp` | — | — | Moves selection up in the active grid. |
| `GoDown` | — | — | Moves selection down in the active grid. |
| `GoLeft` | — | — | Moves selection left in the active grid, or switches grid if at left edge. |
| `GoRight` | — | — | Moves selection right in the active grid, or switches grid if at right edge. |

---

## Inheritance

This column extends **`BaseColumn`** and not only defines a **dual-grid** layout,  
but also adds new methods and behaviors to support the dual-grid functionality.

## Dual-Grid Features

### GetCurrentGrid
Returns the currently active grid (leftGrid or rightGrid) based on the current selection index.

```lua
local currentGrid = dualTab.CenterPanel:GetCurrentGrid()
```

### SwitchGrid
Switches the active grid between left and right.
Automatically updates the selection to the first enabled item in the new grid and refreshes the Scaleform highlight.
Also updates the bottom panel description if it is visible.
⚠️ This function is used internally by the parent tab when switch method is set to `FRONTEND_X`
```lua
dualTab.CenterPanel:SwitchGrid()
```

### SetTitle
Sets the titles for the left and right grids.

```lua
dualTab.CenterPanel:SetTitle(leftTitle,rightTitle)
```

### AddLeftItem
Adds a new item to the left grid of the dual-column, used internally by its parent tab


### AddRightItem
Adds a new item to the right grid of the dual-column, used internally by its parent tab

### RemoveLeftItem(index)
Removes an item from the left grid, used internally by its parent tab

### RemoveRightItem(index)
Removes an item from the right grid, used internally by its parent tab