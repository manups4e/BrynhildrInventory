---
title: "StatsPanel"
parent: Panels
grand_parent: API Documentation
layout: default
---

# StatsPanel

The **StatsPanel** is used to display a list of character or object statistics. It can contain **up to 15 stat entries** if the turbine is inactive, or **10 entries** if the turbine display is active.

![Image]({{ site.baseurl }}/images/statspanel.png)

Additionally, the panel can feature a **Turbine Display**, which is a circular animated gauge that shows either a **short text** or a **percentage** in its center. The turbine has **three animation states**:  
- `Idle`: the turbine is spinning slowly, representing a normal state  
- `Random`: the turbine animation fluctuates randomly  
- `Stressed`: the turbine spins rapidly to indicate stress or overload  

The turbine is visually configurable with a **title**, **central label**, and **animation type**, allowing dynamic feedback on stats.

![Image]({{ site.baseurl }}/images/statspanel_turbine.png)


## Properties

| Property | Type | Description |
|----------|------|-------------|
| `Title` | string | Panel title |
| `nextId` | number | Counter for stat entries |
| `turbineVisible` | boolean | Whether the turbine display is active |
| `turbineTitle` | string | Title for the turbine display |
| `turbineCentralLabel` | string | Central label or value of the turbine |
| `turbineAnimation` | number | Animation state of the turbine (0 = idle, 1 = random, 2 = stressed) |

## Methods

| Method | Description |
|--------|-------------|
| `AddStat(label:string, percentage:number):number` | Adds a new stat entry to the panel and returns its index |
| `UpdateStat(id:number, label:string, percentage:number):StatsPanel` | Updates an existing stat entry by ID |
| `SetTurbine(visible:boolean, title:string, centralLabel:string, animation:number)` | Configures the turbine display with visibility, title, central label, and animation state |
| `Populate()` | Populates the panel in the scaleform, including the turbine if active |
| `ShowPanel()` | Displays the panel in the scaleform |
| `Clear()` | Clears all stats and resets the panel |
