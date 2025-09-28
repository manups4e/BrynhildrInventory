---
title: "Context Menu"
parent: API Documentation
has_children: true
layout: default
nav_order: 6
permalink: /api/context/
---

# Context Menu API

Each `Tab` in the UI has a `Context` member, which is a `ContextColumn`.  
The `ContextColumn` represents a submenu that appears above the currently selected item in the tab.  
It contains a list of options (`ContextItem`) that the developer wants to expose for each item.
When a `ContextItem` is selected, a callback is invoked to handle the action.

Context items can be:
- **simple actions**, like `"Use"` or `"Throw"`.
- **selectable with quantity**, like `"Give"`, `"Take"`, or `"Throw"` with a quantity.  

{: .note }
> The player can increase or decrease the selected quantity before confirming the action, resulting in an event with 2 parameters: `SelectedQuantity` and `RemainingQuantity` (`RemainingQuantity` is based on what is given by the dev)