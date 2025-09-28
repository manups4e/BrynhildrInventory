---
layout: default
title: Scaleform
parent: Utility Elements
nav_order: 3
permalink: /api/elements/scaleform/
---

# Scaleform

The `Scaleform` class is a **wrapper for GTA V scaleform movies**, providing a Lua-friendly API to load, render, and interact with scaleform elements.  
It handles function calls, parameter passing, rendering in both 2D and 3D space, and async return values.

---

## Properties

| Name    | Type    | Description |
|---------|---------|-------------|
| `handle` | `number` | The native handle of the loaded scaleform movie. |
| `name`   | `string` | The name of the loaded scaleform (set on creation). |

---

## Static Constructors

| Method | Signature | Description |
|--------|-----------|-------------|
| `Request` | `Scaleform.Request(name: string): Scaleform` | Loads a new scaleform movie by name. |
| `RequestWidescreen` | `Scaleform.RequestWidescreen(name: string): Scaleform` | Loads a widescreen scaleform movie instance by name. |

---

## Core Methods

| Method | Signature | Description |
|--------|-----------|-------------|
| `CallFunction` | `Scaleform:CallFunction(theFunction: string, ...: any): nil` | Calls a function on the scaleform, passing arguments of type `boolean`, `number`, `string`, `SColor`, or text labels. |
| `CallFunctionAsyncReturnInt` | `Scaleform:CallFunctionAsyncReturnInt(theFunction: string, ...: any): number` | Calls a scaleform function and waits for an **integer return value**. |
| `CallFunctionAsyncReturnBool` | `Scaleform:CallFunctionAsyncReturnBool(theFunction: string, ...: any): boolean` | Calls a scaleform function and waits for a **boolean return value**. |
| `CallFunctionAsyncReturnString` | `Scaleform:CallFunctionAsyncReturnString(theFunction: string, ...: any): string` | Calls a scaleform function and waits for a **string return value**. |
| `Dispose` | `Scaleform:Dispose()` | Releases the scaleform handle, marking it as no longer needed. |
| `IsLoaded` | `Scaleform:IsLoaded(): boolean` | Returns `true` if the scaleform has finished loading. |
| `IsValid` | `Scaleform:IsValid(): boolean` | Returns `true` if the scaleform object is valid and initialized. |

---

## Rendering Methods

| Method | Signature | Description |
|--------|-----------|-------------|
| `Render2D` | `Scaleform:Render2D()` | Draws the scaleform full screen. |
| `Render2DNormal` | `Scaleform:Render2DNormal(x: number, y: number, width: number, height: number)` | Draws the scaleform in a rectangular area of the screen. |
| `Render2DScreenSpace` | `Scaleform:Render2DScreenSpace(locx: number, locy: number, sizex: number, sizey: number)` | Draws the scaleform in **screen space coordinates**. |
| `Render3D` | `Scaleform:Render3D(pos: vector3, rot: vector3, scale: vector3)` | Renders the scaleform in 3D space (solid). |
| `Render3DAdditive` | `Scaleform:Render3DAdditive(pos: vector3, rot: vector3, scale: vector3)` | Renders the scaleform in 3D space with **additive blending**. |

---

## Example

```lua
-- Request and show a scaleform
local sf = Scaleform.Request("instructional_buttons")

-- Wait until it is loaded
while not sf:IsLoaded() do
    Citizen.Wait(0)
end

-- Call a function
sf:CallFunction("CLEAR_ALL")
sf:CallFunction("TOGGLE_MOUSE_BUTTONS", true)

-- Render it full screen
Citizen.CreateThread(function()
    while sf:IsValid() do
        Citizen.Wait(0)
        sf:Render2D()
    end
end)
```

## Notes

- Parameters passed to CallFunction can include:
  - boolean, integer, float
  - strings (labels, player names, texture names)
  - tables with { type = "label" or "literal", data = "..." }
  - SColor instances (automatically converted to ARGB).
- Async functions (CallFunctionAsyncReturnInt/Bool/String) yield until the return value is ready.
- Always call Dispose() when finished with a scaleform to free memory.