---
title: "BaseColumn"
parent: Columns
grand_parent: API Documentation
layout: default
nav_order: 1
---

# BaseColumn

The `BaseColumn` class represents the basic structure of a column within the 3D inventory.
All other columns (such as `Grid8by5Column`, `Grid6by4Column`, etc.) inherit from this class, extending or specializing its behaviors.

Columns are used internally by the inventory **Tabs** and provide an organized container for **Items**, with support for navigation, selection, and rendering via Scaleform.

---

## Properties

| Name | Type | Access | Description |
|------|------|--------|-------------|
| `position` | `number` | protected | Index of the column’s position. |
| `index` | `number` | private | Current index of the selected item. |
| `columnVisible` | `boolean` | private | Indicates whether the column is visible. |
| `Items` | `BaseItem[]` | public | List of items contained in the column. |
| `VisibleItems` | `number` | public | Maximum number of items visible at the same time. Default: `16`. |
| `Focused` | `boolean` | public | Indicates whether the column is focused. |
| `Label` | `string` | public | Column label. |
| `BGColor` | `SColor` | public | Column background color. Default: `ARGB(255,61,91,109)`. |
| `Parent` | `BaseTab` | public | Reference to the parent tab (if any). |

---

## Methods

### Creation
```lua
---@param pos number|nil Column position
---@return BaseColumn
BaseColumn.New(pos)
```

Creates a new column instance.
If pos is not specified, the default value is -1.

---

### Visibility
```lua
---@return boolean
BaseColumn:visible()
```
Returns whether the column is actually visible, taking into account the parent tab and its container.

```lua
---@param bool boolean|nil
---@return boolean|nil
BaseColumn:ColumnVisible(bool)
```
Gets or sets the visibility state of the column. When changed, it also updates the linked Scaleform.

---

### Navigation and Selection
```lua
---@return BaseItem|nil
BaseColumn:CurrentItem()
```
Returns the item currently selected (or `nil` if none is present).

```lua
---@param index number|nil
---@return number
BaseColumn:Index(index)
```
Gets or sets the current index.  
Automatically skips over **enabled** items and updates the selection in the Scaleform.

```lua
BaseColumn:GoUp()
BaseColumn:GoDown()
BaseColumn:GoLeft()
BaseColumn:GoRight()
BaseColumn:Select()
BaseColumn:GoBack()
```
Navigation and interaction methods to move or select items within the column.  
(In derived classes, these can be overridden).

---

### Item Management
```lua
---@param item BaseItem
BaseColumn:AddItem(item)
```
Adds a new item to the column.

```lua
BaseColumn:Clear()
BaseColumn:ClearColumn()
```
Removes all items from the column and resets the internal state.  

```lua
---@param idx number
BaseColumn:RemoveSlot(idx)
```
Removes the slot at the specified index and updates the interface.

---

### Slots and Population
```lua
---@param index number
BaseColumn:SetDataSlot(index)

---@param index number
BaseColumn:UpdateSlot(index)

---@param index number
BaseColumn:AddSlot(index)
```
Base methods for managing the column’s slots.  
They serve as extension points used in specific subclass implementations.

```lua
BaseColumn:Populate()
```
Placeholder method to populate the column (to be implemented in subclasses).

---

### Rendering
```lua
BaseColumn:ShowColumn()
```
Displays the column in the Scaleform.

```lua
---@param color SColor
BaseColumn:SetBGColor(color)
```
Sets a new background color for the column and updates the Scaleform if visible.

---

## Inheritance

All specialized columns (such as `Grid8by5Column`) **extend `BaseColumn`**, inheriting:  
- Common data structure (`Items`, `index`, `Label`, etc.)  
- Navigation and item management methods  
- Integration with the Scaleform system  

Subclasses only define the layout or additional behavior (e.g., number of cells, grid arrangement, population logic).
