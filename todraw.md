---
title: How to draw
nav_order: 4
permalink: /todraw/
---

## How to Draw

By default, the `Inventory:Draw()` method does not exist.  
This is intentional: you are free to choose how and where to render the scaleform, depending on your resource’s needs.

The inventory scaleform is rendered as a **3D object in the world**.  
It must be drawn **inside a render loop**, typically every frame if you don't want it to flicker / disappear.

You can use any camera setup you desire and draw the scaleform the way you want it thanks to the exposed `Brynhildr.scaleform` API, to learn how it works you can check the [Scaleform class API]({{ site.baseurl }}/api/elements/scaleform/)

There are infinite ways to do it, here you'll see some common approaches:

## Static drawing
The scaleform will be drawn in place and will not move, will not rotate, will be static where it is and that's all
This approach is useful when drawing the scaleform on static places, for example against a wall or inside an interior.

![Image]({{ site.baseurl }}/images/static_draw.gif)

```lua
-- code to build the inventory executed.. i called myInventory:Visible(true)

Citizen.CreateThread(function()
    -- get the player position, shift it slightly to the right, and up
    local renderPos = GetOffsetFromEntityInWorldCoords(PlayerPedId(), 0.0, 1.5, 0.8)
    -- get the player rotation and slightly rotate it horizontally 
    -- (scaleform automatically negate it when converting -180 to 180 into 0 to 360 angles)
    local rot = GetEntityRotation(PlayerPedId(), 2) + vector3(5.0, 0.0, 0.0)
    while true do
        Wait(0)
        if myInventory:Visible() then
            if Brynhildr.scaleform ~= nil and Brynhildr.scaleform:IsLoaded() then
                -- render it in the world, the third vector is the size of the scaleform
                Brynhildr.scaleform:Render3D(renderPos, rot, vector3(2.5, 1.5, 1.5))
                myInventory:ProcessControl()
            end
        end
    end
end)
```

## Ped Following Drawing
In this approach, the inventory scaleform **follows the player**, rotating and moving with them.  
This is useful for immersive interfaces, like in *Dead Space* games, where the UI floats in front of the player in the world.

### DeadSpace reference:
![deadspace]({{ site.baseurl }}/images/deadspaceinv.png)

There are 2 ways to handle this case, you can either face the scaleform to the ped's face or to the camera here you'll see how.

### Scaleform facing the ped

![deadspace]({{ site.baseurl }}/images/following_ped_rot.gif)

```lua
-- code to build the inventory executed.. i called myInventory:Visible(true)

Citizen.CreateThread(function()
    while true do
        Wait(0)
        if myInventory:Visible() then
            if Brynhildr.scaleform ~= nil and Brynhildr.scaleform:IsLoaded() then
                -- vectors are taken on frame to keep position updated.
                -- get the player position, shift it slightly to the right, and up
                local renderPos = GetOffsetFromEntityInWorldCoords(PlayerPedId(), 0.0, 1.5, 0.8)
                -- get the player rotation and slightly rotate it horizontally
                -- (scaleform automatically negate it when converting -180 to 180 into 0 to 360 angles)
                local rot = GetEntityRotation(PlayerPedId(), 2) + vector3(5.0, 0.0, 0.0)
                -- render it in the world, the third vector is the size of the scaleform
                Brynhildr.scaleform:Render3D(renderPos, rot, vector3(2.5, 1.5, 1.5))
                myInventory:ProcessControl()
            end
        end
    end
end)
```


### Scaleform facing rendering camera
Scaleform follows the ped but rotates to follow the camera position.
The main difference is that instead of calling `GetEntityRotation(PlayerPedId(), 2)` you call `GetFinalRenderedCamRot(2)`.

![deadspace]({{ site.baseurl }}/images/following_cam_rot.gif)

```lua
-- code to build the inventory executed.. called myInventory:Visible(true)

Citizen.CreateThread(function()
    while true do
        Wait(0)
        if myInventory:Visible() then
            if Brynhildr.scaleform ~= nil and Brynhildr.scaleform:IsLoaded() then
                -- vectors are taken on frame to keep position updated.
                -- get the player position, shift it slightly to the right, and up
                local renderPos = GetOffsetFromEntityInWorldCoords(PlayerPedId(), 0.0, 1.5, 0.8)
                -- get the player rotation and slightly rotate it horizontally
                -- (scaleform automatically negate it when converting -180 to 180 into 0 to 360 angles)
                local rot = GetFinalRenderedCamRot(2) + vector3(5.0, 0.0, 0.0)
                -- render it in the world, the third vector is the size of the scaleform
                Brynhildr.scaleform:Render3D(renderPos, rot, vector3(2.5, 1.5, 1.5))
                myInventory:ProcessControl()
            end
        end
    end
end)
```
---

{: .note}
> In each example, `myInventory:ProcessControl()` is called.
> it **must** be called alongside the scaleform drawing. If it is not called, the player will not be able to navigate the inventory.