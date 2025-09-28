---
title: Getting Started
nav_order: 2
permalink: /getting-started/
---

# Getting Started
Here i'll show you the first steps on how to install the resource and start it.
When downloaded, the resource will be presented inside its own folder `[BrynhildrInventory]` containing both the `assets` folder and the `API script` folder. 

First of all, keep the `assets folder` containing the scaleform (gfx) and its textures (ytd) in a separate folder than the `API code`, this will make sure that in case of restart of the API, the scaleform won't be affected.

{: .warning}
Make sure that the gfx and the ytd are always in the same folder, as they're in love with each other and need to stay together to work properly!

## Requirements

- FiveM server
- Lua 5.4 (integrated in FiveM)
- Basic coding and logic skills

## Installation

1. Copy the `BrynhildrInventory` resource into your FiveM `resources/` folder or any sub-folder you want.
2. Add it to your `server.cfg`:
   ```
   ensure BrynhildrInventory_assets # In case you decide to keep them in their own resource, you can put these files in any asset folder you have as long as the gfx and the ytd stay together
   ensure BrynhildrInventory
   ```
3. There are 2 ways you can use the lua API library.
  - First option: Place your `BrynhildrInventory.lua` in each resource that uses it and start it before any other client file.
  - Second option: Leave it in its own `BrynhildrInventory` resource and start it before the other resources. When you want to use it in any resource simply add `"@BrynhildrInventory/BrynhildrInventory.lua"`, in the resource manifest in the client_scripts section before anything else.

{: .note }
> I personally suggest the second option for 2 main reasons: 
> - Whenever you need to update the API you do it only once in its own resource instead of looking for every resource using it. 
> - this way you don’t risk to have multiple instances of the API at the same time, less memory used, happy players, happy server scripter, happy me! 🥳🥳
