---
title: "DualGridSingleColumn"
parent: DualGridColumn
grand_parent: Columns
layout: default
---

# DualGridSingleColumn

The **`DualGridSingleColumn`** class extends [`BaseColumn`](./BaseColumn.md) and represents internally a single grid within a dual-grid column.  
It is **used exclusively** by `DualGridColumn` to instantiate the `leftGrid` and `rightGrid`.

It **inherits all methods and properties** from `BaseColumn` and does **not add any new functionality**.  
Its sole purpose is to act as an individual grid within the dual-grid system.
---

## Properties

| Name | Type | Access | Description |
|------|------|--------|-------------|
| `batchCols` | `number` | private | Number of columns per batch. |
| `batchRows` | `number` | private | Number of rows per batch. |
| `gridIndex` | `number` | private | Index of the current grid (0-based). |

## Functions

| Name | Type | Access | Description |
|------|------|--------|-------------|
| `AddItem` | `function` | public | Adds an item to the grid. |
| `Populate` | `function` | public | Populates the grid with items. |
| `GoUp` | `function` | public | Moves the selection up. |
| `GoDown` | `function` | public | Moves the selection down. |
| `GoLeft` | `function` | public | Moves the selection left. |
| `GoRight` | `function` | public | Moves the selection right. |
| `_currentSelection` | `function` | private | Gets or sets the current selection index. |
| `checkViewEdge` | `function` | private | Returns information about the current row edges (`atLeft`, `atRight`, `col`, `row`). |

---