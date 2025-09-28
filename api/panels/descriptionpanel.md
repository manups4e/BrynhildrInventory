---
title: "DescriptionPanel"
parent: Panels
grand_parent: API Documentation
layout: default
---

# DescriptionPanel

![Image]({{ site.baseurl }}/images/descriptionpanel.png)


The **DescriptionPanel** is a special type of panel that displays a title and a text description.  
It is used **exclusively as the BottomPanel** across all tabs and cannot be replaced with other panel types.  

By default, it is visible, but it can be toggled on or off using the `SetVisible` method on the parent tab’s `BottomPanel`.  

Example:
```lua
tab.BottomPanel:SetVisible(false) -- hides the description panel
```

### Properties

| Name          | Type       | Description |
|---------------|------------|-------------|
| `Title`       | `string`   | Panel title. |
| `Description` | `string`   | Panel description text. |
| `Parent`      | `BaseTab`  | Reference to the parent tab. |
| `IsVisible`   | `boolean`  | Indicates whether the panel is currently visible. |

### Methods

| Name                 | Parameters | Returns | Description |
|----------------------|------------|---------|-------------|
| `UpdateDescription`  | `title: string, desc: string, hash: number, txd: string, txn: string` | `void` | Updates the panel's title and description, and sets the appropriate texture or weapon hash. |
| `SetVisible`         | `state?: boolean` | `BasePanel` | Shows or hides the panel; returns the panel instance. |

{: .note }
By default `UpdateDescription` is called on index change internally. It is still public and can be called at will.