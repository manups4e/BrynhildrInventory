---
title: "IBColumn"
parent: Columns
grand_parent: API Documentation
layout: default
nav_order: 5
---

# IBColumn
The instructional buttons column is common for all tabs, each tab has its own instance of instructional buttons.
The buttons are not automatically added to give complete freedom to the developer.

You can either choose to include the default instructional buttons by adding them yourself or to add your own for custom commands exterior to the inventory.

## Public functions

![Image]({{ site.baseurl }}/images/ib.png)

## AddItem`
Adds an instructional button to the line, you can add up to 10 instructional buttons.
Below an example of the instructional buttons for the inventory common commands.

**Example**:
```lua
tab8by5.IBPanel:AddItem({Label="Move", Control="~INPUTGROUP_FRONTEND_DPAD_ALL~"})
tab8by5.IBPanel:AddItem({Label="Change Tab", Control="~INPUTGROUP_FRONTEND_BUMPERS~"})
tab8by5.IBPanel:AddItem({Label="Change Grid", Control="~INPUT_FRONTEND_X~"}) -- used for the dual grid with frontend_x option of switching
tab8by5.IBPanel:AddItem({Label="Select", Control="~INPUT_FRONTEND_ACCEPT~"})
tab8by5.IBPanel:AddItem({Label="Back", Control="~INPUT_FRONTEND_CANCEL~"})
```