---
title: "Columns"
parent: API Documentation
has_children: true
layout: default
nav_order: 3
permalink: /api/columns/
---

# Columns

**Columns** define the internal structure of an inventory tab.  
They are responsible for arranging **grid items** into rows and columns, ensuring consistent positioning across different inventory layouts.  

Columns are **not meant to be used directly**. Instead, they are created and managed by **Tabs**, which provide the developer-facing entry point to add or organize items in the inventory, but in case of need you can access columns by your `tab.CenterPanel` class member.

## Available Column Types

- **8x5 Column** – Large grid, ideal for wide inventories with many slots.  
- **5x5 Column** – Balanced grid, useful for compact layouts.  
- **Dual Grid Column** – Two smaller grids side by side, suitable for dual-slot inventories or equipment screens.  

## Key Points

- **Used Internally** – Columns are instantiated by Tabs, not directly by the developer.  
- **Automatic Positioning** – They handle grid item placement automatically.  
- **Layout Flexibility** – Different column types adapt the look and feel of each Tab.  

---

The following pages describe each available column type and how they integrate with their respective Tabs.