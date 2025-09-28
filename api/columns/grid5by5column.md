---
title: "Grid5by5Column"
parent: Columns
grand_parent: API Documentation
layout: default
nav_order: 3
---

# Grid5by5Column

The **`Grid5by5Column`** class represents a column organized in a **5 columns by 5 rows grid**, for a total of **25 available slots**.  
It inherits and expand all functionalities from [`BaseColumn`](BaseColumn.md).

⚠️ Note: Columns are created and managed internally by Tabs. Developers usually do not instantiate Grid8by5Column directly; instead, they use a corresponding Tab (e.g., Tab8by5) that creates and binds the column and its Panel member.

---

## Main Features

- 5x5 grid layout (maximum 25 cells).  
- Used internally in the inventory **Tabs**.  
- Ideal for more compact inventories.

---

## Properties

| Name | Type | Access | Description |
|------|------|--------|-------------|
| `batchCols` | `number` | private | Number of columns per batch (5). |
| `batchRows` | `number` | private | Number of rows per batch (5). |

## Methods

| Name | Type | Access | Description |
| `CurrentSelection` | `function` | public | Get or set the current selection index. |
| `ShowColumn` | `function` | public | Displays the column on the screen. |
| `AddItem` | `function` | public | Adds an item to the grid. |
| `Populate` | `function` | public | Populates the grid with items. |
| `GoUp` | `function` | public | Moves the selection up. |
| `GoDown` | `function` | public | Moves the selection down. |
| `GoLeft` | `function` | public | Moves the selection left. |
| `GoRight` | `function` | public | Moves the selection right. |

---

## Inheritance

This column extends **`BaseColumn`** and does not add new methods, but specializes the behavior  
by setting a specific layout (5x5).