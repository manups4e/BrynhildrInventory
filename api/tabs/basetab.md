---
title: "BaseTab"
parent: Tabs
grand_parent: API Documentation
layout: default
nav_order: 1
---

# BaseTab

`BaseTab` is the base class for all tabs in the UI system. Each tab contains panels (columns), an instructional buttons panel (IBPanel), and a context menu (Context) that can be opened above the selected item. Tabs manage navigation, selection, and focus internally, and provide callbacks for state changes.

---

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `Title` | `string` | Tab title. |
| `Type` | `number` | Tab type (numeric identifier). |
| `Visible` | `boolean` | Whether the tab is currently visible. |
| `Focused` | `boolean` | Whether the tab is currently focused. |
| `Active` | `boolean` | Whether the tab is active. |
| `Parent` | `Inventory` | Parent inventory (if nested). |
| `LeftPanel` | `BaseColumn children` | Left panel column. |
| `CenterPanel` | `BaseColumn children` | Center panel column. |
| `RightPanel` | `BaseColumn children` | Right panel column. |
| `BottomPanel` | `BaseColumn children` | Description panel. **Cannot be replaced** with another panel type; can only be shown/hidden and its data is handled automatically. |
| `Context` | `ContextColumn` | Context menu associated with the tab, displayed above the selected item. |
| `IBPanel` | `IBColumn` | Panel for instructional buttons. |
| `Activated` | `fun(self:BaseTab, item:BaseTab)` | Callback triggered when the tab is activated. |

---

## Methods
All tabs extend the functionality of BaseTab. The methods defined in BaseTab are only placeholders and are meant to be implemented or overridden by derived tabs.

| Method | Description |
|--------|-------------|
| `New(title:string): BaseTab` | Creates a new tab instance. |
| `SetupLeftPanel(panel:BasePanel): BaseColumn` | Sets up the left panel. |
| `SetupRightPanel(panel:BasePanel): BaseColumn` | Sets up the right panel. |
| `CurrentPanel(): BaseColumn` | Returns the currently active panel. |
| `GetPanelAtPosition(pos:integer): BaseColumn` | Returns the panel at a specific position (0 = Left, 1 = Center, 2 = Right). |
| `Populate()` | Placeholder method to populate tab panels. |
| `Refresh(highlightOldIndex:boolean)` | Placeholder method to refresh tab panels. |
| `ShowPanels()` | Placeholder method to show all panels. |
| `SetDataSlot(slot, index)` | Placeholder method to set a data slot. |
| `UpdateSlot(slot, index)` | Placeholder method to update a slot. |
| `AddSlot(slot, index)` | Placeholder method to add a slot. |
| `Focus()` | Focuses the tab. |
| `UnFocus()` | Unfocuses the tab. |
| `GoUp()` | Navigate up inside the tab. |
| `GoDown()` | Navigate down inside the tab. |
| `GoLeft()` | Navigate left inside the tab. |
| `GoRight()` | Navigate right inside the tab. |
| `Select()` | Select the currently highlighted item. |
| `GoBack()` | Navigate back. |
| `Selected()` | Returns the currently selected item. |
| `MouseEvent(eventType, context, index)` | Handle a mouse event on the tab. |
| `StateChange(state)` | Handle tab state changes. |

---

## Notes

- Each tab is composed of multiple **columns (panels)**: left, center, right, and bottom.
- **BottomPanel** is reserved for descriptions and cannot be replaced with other panel types.
- **Context** allows developers to define context-sensitive menus above selected items, containing simple labels or selectable quantities.
- **IBPanel** is used for instructional buttons (interactive prompts) and is unique per tab.
- Tabs manage navigation internally and provide methods for moving between panels and items.