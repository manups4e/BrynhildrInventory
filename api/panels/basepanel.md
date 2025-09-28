---
title: "BasePanel"
parent: Panels
grand_parent: API Documentation
nav_order: 1
layout: default
permalink: /api/panels/basepanel
---

# BasePanel

`BasePanel` is the base class for all panels that derive from `BaseColumn`.  
It provides the **common behavior and lifecycle** used by panels inside a tab, such as visibility handling, initialization in the scaleform, and data management.

Not all panels extend from `BasePanel`, but those that do share its foundational functions.

---

## Properties & Methods

| Name | Type | Description |
|------|------|-------------|
| `type` | `PanelType` | The type of the panel. |
| `Parent` | `BaseTab` | Reference to the parent tab that owns this panel. |
| `_visible` | `boolean` (private) | Internal visibility state. |
| `Init()` | `fun(self:BasePanel)` | Initializes the panel in the scaleform (`SET_PANEL_STATE`). |
| `ShowPanel()` | `fun(self:BasePanel):BasePanel` | Internally tells the scaleform to display the panel data. |
| `SetVisible(state:boolean\|nil)` | `fun(self:BasePanel):BasePanel` | Sets the panel visibility (true/false). If `nil` is passed, retrieves the current visibility. |
| `ClearPanel()` | `fun(self:BasePanel)` | Clears all data inside the panel (empties it). |
| `GetType()` | `fun(self:BasePanel):PanelType` | Returns the type of the panel. |
| `UpdateDescription()` | `fun(self:BasePanel)` | Updates the panel description (placeholder, empty by default). |

---

## Usage

A `BasePanel` is not used directly. Instead, it acts as the **foundation** for specialized panels (e.g., `DescriptionPanel`, `LorePanel`, etc.), which implement their own specific behavior on top of it.