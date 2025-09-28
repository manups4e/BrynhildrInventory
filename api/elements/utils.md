---
layout: default
title: Utils
parent: Utility Elements
---

# Utils

The `utils.lua` module provides a collection of helper functions for strings, tables, math, resolution, vectors, and user interface handling.  
These utilities are widely used across the inventory system to simplify repetitive tasks such as string manipulation, coordinate conversions, and resolution adjustments.

---

## String Utilities

| Function | Parameters | Returns | Description |
|----------|------------|---------|-------------|
| `string.starts(Str, Start)` | `Str: string`, `Start: string` | `boolean` | Checks if `Str` begins with `Start`. |
| `string.StartsWith(self, str)` | `self: string`, `str: string` | `boolean` | Returns `true` if the string starts with `str`. |
| `string.IsNullOrEmpty(self)` | `self: string` | `boolean` | Returns `true` if the string is `nil`, empty, or whitespace. |
| `string.SplitLabel(self)` | `self: string` | `table` | Splits a long string into chunks of max 99 characters. |
| `string.Insert(self, pos, str2)` | `self: string`, `pos: number`, `str2: string` | `string` | Inserts `str2` into `self` at the given position. |
| `string.split(inputstr, sep)` | `inputstr: string`, `sep?: string` | `table` | Splits a string using the given separator (defaults to whitespace). |

---

## Table Utilities

| Function | Parameters | Returns | Description |
|----------|------------|---------|-------------|
| `IndexOf(array, value)` | `array: table`, `value: any` | `number` | Returns the index of `value` in `array`, or `-1` if not found. |
| `KeyOf(tbl, value)` | `tbl: table`, `value: any` | `any` | Returns the key of the given value, or `nil` if not found. |
| `TableHasKey(table, key)` | `table: table`, `key: string` | `boolean` | Returns `true` if `key` exists in the table (case-insensitive). |
| `Join(symbol, list)` | `symbol: string`, `list: table` | `string` | Joins all elements of the list with the given separator. |

---

## Math Utilities

| Function | Parameters | Returns | Description |
|----------|------------|---------|-------------|
| `math.round(num, numDecimalPlaces?)` | `num: number`, `numDecimalPlaces?: number` | `number` | Rounds a number to the nearest integer or specified decimals. |
| `ToBool(input)` | `input: string|number|boolean` | `boolean` | Converts input into a boolean (`true`/`false`). |
| `Wrap(value, min, max)` | `value: number`, `min: number`, `max: number` | `number` | Wraps a value within the specified range. |

---

## Resolution & Screen Utilities

| Function | Parameters | Returns | Description |
|----------|------------|---------|-------------|
| `ResolutionMaintainRatio()` | – | `(width: number, height: number)` | Returns width and height adjusted for aspect ratio (base 1080p). |
| `SafezoneBounds()` | – | `(x: number, y: number)` | Returns safe zone boundaries for UI placement. |
| `FormatXWYH(Value, Value2)` | `Value: number`, `Value2: number` | `(x: number, y: number)` | Normalizes coordinates based on resolution. |
| `IsMouseInBounds(X, Y, Width, Height)` | `X: number`, `Y: number`, `Width: number`, `Height: number` | `boolean` | Returns `true` if the mouse is inside the given rectangle. |
| `ConvertResolutionCoordsToScaleformCoords(realX, realY)` | `realX: number`, `realY: number` | `vector2` | Converts resolution coords to Scaleform coords (1280x720). |
| `ConvertScaleformCoordsToResolutionCoords(scaleformX, scaleformY)` | `scaleformX: number`, `scaleformY: number` | `vector2` | Converts Scaleform coords to resolution coords. |
| `ConvertScreenCoordsToScaleformCoords(scX, scY)` | `scX: number`, `scY: number` | `vector2` | Converts screen coords (0–1) to Scaleform coords. |
| `ConvertScaleformCoordsToScreenCoords(scaleformX, scaleformY)` | `scaleformX: number`, `scaleformY: number` | `vector2` | Converts Scaleform coords to screen coords (0–1). |
| `ConvertResolutionSizeToScaleformSize(realWidth, realHeight)` | `realWidth: number`, `realHeight: number` | `vector2` | Converts resolution size to Scaleform size (1280x720). |
| `ConvertScaleformSizeToResolutionSize(scaleformWidth, scaleformHeight)` | `scaleformWidth: number`, `scaleformHeight: number` | `vector2` | Converts Scaleform size to resolution size. |
| `ConvertScreenSizeToScaleformSize(scWidth, scHeight)` | `scWidth: number`, `scHeight: number` | `vector2` | Converts screen size (0–1) to Scaleform size (1280x720). |
| `ConvertScaleformSizeToScreenSize(scaleformWidth, scaleformHeight)` | `scaleformWidth: number`, `scaleformHeight: number` | `vector2` | Converts Scaleform size to screen size (0–1). |
| `AdjustNormalized16_9ValuesForCurrentAspectRatio(x, y, w, h)` | `x, y, w, h: number` | `(x, y, w, h)` | Adjusts 16:9 values for current aspect ratio. |
| `GetWideScreen()` | – | `boolean` | Returns `true` if the current resolution is widescreen. |
| `AdjustForSuperWidescreen(x, w)` | `x: number`, `w: number` | `(x: number, w: number)` | Adjusts coordinates for super widescreen ratios. |
| `IsSuperWideScreen()` | – | `boolean` | Returns `true` if the display is super widescreen. |

---

## Vector Utilities

| Function | Parameters | Returns | Description |
|----------|------------|---------|-------------|
| `GetVectorMagnitude(vector)` | `vector: vector3` | `number` | Returns the magnitude (length) of a vector. |
| `IsVectorInsideSphere(vector, position, scale)` | `vector: vector3`, `position: vector3`, `scale: vector3` | `boolean` | Checks if a vector is inside a sphere defined by position and scale. |
| `LengthSquared(vector)` | `vector: vector3` | `number` | Returns the squared length of a vector. |

---

## Boolean Helpers

| Function | Parameters | Returns | Description |
|----------|------------|---------|-------------|
| `AllTrue(t)` | `t: table` | `boolean` | Returns `true` if all values in the table are true. |
| `AllFalse(t)` | `t: table` | `boolean` | Returns `true` if all values in the table are false. |

---

## Examples

### Splitting a string
```lua
local parts = string.split("hello world example", " ")
-- parts = {"hello", "world", "example"}
```

### Checking mouse position
```lua
if IsMouseInBounds(100, 200, 300, 400) then
    print("Mouse is inside the rectangle!")
end
```

### Converting screen coordinates
```lua
local scaleformCoords = ConvertScreenCoordsToScaleformCoords(0.5, 0.5)
-- Result: vector2(640, 360) in a 1280x720 space
```
