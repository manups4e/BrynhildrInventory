---
title: "Panels"
parent: API Documentation
has_children: true
layout: default
nav_order: 5
permalink: /api/panels/
---

# Panels

Panels are the building blocks that define the content and layout inside a tab.
The panels shown in this section are solely made for the Left, Right and Bottom (Description) sides of the tab.
Each panel is responsible for managing a specific portion of the tab’s interface — such as a list of details or statistics, a description area, or instructional buttons.

---

## Overview

- Panels determine **how data is displayed and interacted with** inside a tab.  
- A tab can contain multiple panels at once (e.g., left, right, bottom, context, IBPanel).  
- Panels can show lists, grids, contextual options, or additional information depending on their type.  

---

## Key Notes

- All panels inherit from [`BasePanel`](./basepanel.md), which provides common functionality like visibility management and initialization.  
- Not all panels expand `BasePanel` functionalities: some implement their own behavior and lifecycle independently.
- Each panel defines its own **functions and events**, tailored to the type of content it manages (e.g., adding/removing items, updating descriptions).
- Panels are always tied to a **parent tab**, ensuring they work together as part of a structured interface.  
- Panels are solely for view purpose, they cannot be interacted directly by the player.
- Panels can be switched on need, you can hide them, show them, change them for other panels on need by simply instancing them and then using `tab:SetupLeftPanel` or `tab:SetupRightPanel`

{: .note}
> Changing panels at runtime is absolutely possible and highly recommended. Every time you replace a panel with another, you need to call its internal functions to make it work:
> - `panel:Clear()`: Clears the panel’s contents if it was already created, giving you a clean slate.
> - `panel:DoStuff()`: Call functions like `AddItem`, `UpdateDescription`, or any other relevant methods. If the inventory is visible on screen, the items will automatically be added to the scaleform buffer.
> - `panel:ShowPanel()`: Instructs the scaleform to build the items and display them from the buffer to the visual layer.
>
> Below is an example of updating a `DetailsPanel` in an index change:
```lua
-- in this example the right panel is already a DetailsPanel but in case you want to change it.. 
-- you simply add tab:SetupLeftPanel or tab:SetupRightPanel before the clear function.. simple
tab8by5.OnIndexChange = function(item, index)
    tab8by5.RightPanel:Clear() -- empty the panel frum old junk
    for i = 1, 8 do
        local detail = someDetailTableBasedOnItem[item.Label]
        tab8by5.RightPanel:AddDetail(detail.label, detail.desc, detail.txd, detail.txn)
    end
    tab8by5.RightPanel:ShowPanel() -- required after Clear; the scaleform needs its buffer to be called
end
```

This section documents the different panel types, their purpose, and the functions they expose.