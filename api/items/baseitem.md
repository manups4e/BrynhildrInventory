---
title: "BaseItem"
parent: Items
grand_parent: API Documentation
layout: default
---

# BaseItem

# BaseItem

**Description:**  
Base class for all items in the UI. Provides basic properties like label, selected state, and enabled state.
At this moment the only item inheriting from it is GridItem

**Properties & Methods:**

| Property / Method        | Type                   | Description                                    |
|--------------------------|-----------------------|-----------------------------------------------|
| `Label`                  | `string`               | The label of the item.                        |
| `Parent`                 | `BaseItem`             | Reference to the parent item (if nested).    |
| `ParentTab`              | `BaseColumn or nil`    | Reference to the parent tab.                 |
| `ParentColumn`           | `BaseColumn or nil`    | Reference to the parent column.              |
| `Selected(bool?: boolean)` | `boolean`      | Get or set the selected state.               |
| `Enabled(bool?: boolean)`  | `boolean`      | Get or set the enabled state.                |
