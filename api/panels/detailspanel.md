---
title: "DetailsPanel"
parent: Panels
grand_parent: API Documentation
layout: default
---

### DetailsPanel

![Image]({{ site.baseurl }}/images/detailspanel.png)

The `DetailsPanel` is a panel used to display a list of **max 8** detailed entries (details) for a selected item. Each detail can have a label, sublabel, and optional texture (TXD) and texture name (TXN). This panel is commonly used in the right panel of tabs to show additional information dynamically when the selection changes.

{: .note}
You can have MAX 8 entries at once

---

### Properties

| Name       | Type     | Description |
|------------|----------|-------------|
| `Title`    | `string` | Panel title. |
| `Parent`   | `BaseTab` | Reference to the parent tab. |
| `BGColor`  | `SColor` | Background color for the panel. |

---

### Methods

| Name              | Parameters | Returns       | Description |
|-------------------|------------|---------------|-------------|
| `AddDetail`       | `label: string, sublabel: string, txd: string, txn: string` | `number` | Adds a new detail and returns its index. |
| `UpdateDetail`    | `id: number, label: string, sublabel: string, txd: string, txn: string` | `DetailsPanel` | Updates an existing detail by ID. |
| `ShowPanel`       | —          | `void`        | Displays the panel and sets its background color. |
| `Clear`           | —          | `void`        | Clears all details and resets the panel. |
| `Populate()` | — | `void` | Initializes the panel in the scaleform. |
| `SetVisible`      | `state?: boolean` | `BasePanel` | Shows or hides the panel; returns the panel instance. |

---

### Example: Dynamically updating details on item selection

```lua
tab8by5.OnIndexChange = function(item, index)
    tab8by5.RightPanel:Clear()
    for i = 1, #itemDetails do
        tab8by5.RightPanel:AddDetail(itemDetails.label, itemDetails.desc, itemDetails.txd, itemDetails.txn)
    end
    tab8by5.RightPanel:ShowPanel() -- Required if Clear() was called, to refresh the scaleform buffer and redraw.
end
```
This example demonstrates how to clear existing details, add new details dynamically for the selected item, and refresh the panel to reflect the changes in one frame.

{: .note}
Details can be shown with or without textures by leaving the txd and txn parameters empty. In both cases, the label and sublabel will automatically scroll if they are too long to fit.