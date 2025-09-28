---
title: "Grid8by5Column"
parent: Columns
grand_parent: API Documentation
layout: default
nav_order: 2
---

# Grid8by5Column

The **Grid8by5Column** defines a column layout with **8 columns** and **5 rows** for a total of **40 available slots**,  
making it one of the largest available grid configurations.  

This layout is ideal for inventories with a large number of items (such as general storage or backpack-style interfaces).  
It inherits all functionalities from [`BaseColumn`](./BaseColumn.md).

⚠️ **Note:** Columns are created and managed internally by **Tabs**. Developers usually do not instantiate `Grid8by5Column` directly; instead, they use a corresponding Tab (e.g., `Tab8by5`) that creates and binds the column and its Panel member.

---

## Main Features

- 8x5 grid layout (maximum 40 cells).  
- Used internally in the inventory **Tabs**.  
- Manages the organization and rendering of items using the same set of methods as `BaseColumn`.

---

## Properties

| Name | Type | Access | Description |
|------|------|--------|-------------|
| `batchCols` | `number` | private | Number of columns per batch (5). |
| `batchRows` | `number` | private | Number of rows per batch (5). |

## Methods

| Name | Type | Access | Description |
|------|------|--------|-------------|
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

This column extends **[`BaseColumn`](./BaseColumn.md)** and does not add new methods, but specializes the behavior  
by setting a specific layout (8x5).