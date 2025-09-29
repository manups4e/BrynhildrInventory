---
title: Getting Started
nav_order: 2
permalink: /getting-started/
---

# Getting Started
Here i'll show you the first steps on how to install the resource and start it.
When downloaded, the resource will be presented inside its own folder `[Brynhildr]` containing both the `assets` folder and the `API` folder, along with a test script to check, learn, and take examples. 

First of all, keep the `assets folder` containing the scaleform (gfx) and its textures (ytd) in a separate folder than the `API code`, this will make sure that in case of restart of the API, the scaleform won't be affected.

{: .warning}
Make sure that the gfx and the ytd are always in the same folder, as they're in love with each other and need to stay together to work properly!

## Requirements

- FiveM server
- Lua 5.4 (integrated in FiveM)
- Basic coding and logic skills (to make your own inventory)

## Installation

1. Copy the `[Brynhildr]` resource into your FiveM `resources/` folder or any sub-folder you want.
2. Add it to your `server.cfg`:
   ```
   ensure brynhildr_assets # In case you decide to keep them in their own resource. You can also move these files in any asset folder you have as long as the gfx and the ytd stay together.
   ensure brynhildr_api
   ```
   - You can also do `ensure [Brynhildr]` to ensure everything inside the folder without specifying it. (you can delete the test script if you don't use it)
3. There are 2 ways you can use the lua API library.
  - First option: Place the file `API.lua` in each resource that uses it (you don't need to start `brynhildr_api` in this case as its api is moved across resources).
  - Second option: Leave it in its own `brynhildr_api` resource and start it before any other resources using it. When you want to use it in any resource simply add `"@brynhildr_api/API.lua"`, in the resource manifest in the client_scripts section before anything else. 
    - Check the `brynhildr_test` script `fxmanifest.lua` for a better look.

{: .note }
> I personally suggest the second option for 2 main reasons: 
> - Whenever you need to update the API you do it only once in its own resource instead of looking for every resource using it. 
> - this way you don’t risk to have multiple instances of the API at the same time, less memory used, happy players, happy server scripter, happy me! 🥳🥳
