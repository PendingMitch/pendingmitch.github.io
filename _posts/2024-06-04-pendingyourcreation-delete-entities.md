---
title: Deleting Entities
date: 2024-06-04 13:00:00 -0000
categories: [PendingDevelopment, PendingYourCreation]
tags: [pendingyourcreation]
---


Deleting entities can be difficult for some people, especially with the change of network owners. Using this code snippet will allow you to delete entities from the server. That means reliability!


## client.lua
```lua
function DeleteEntity(Entity)
    TriggerServerEvent("PendingDevelopment:DeleteEntity", NetworkGetNetworkIdFromEntity(Entity))
end
```

## server.lua
```lua
RegisterNetEvent("PendingDevelopment:DeleteEntity")
AddEventHandler("PendingDevelopment:DeleteEntity", function(NetworkID)
    DeleteEntity(NetworkGetEntityFromNetworkId(NetworkID))
end)
```

## References

[RegisterNetEvent](https://docs.fivem.net/docs/scripting-reference/runtimes/lua/functions/RegisterNetEvent/)  
[AddEventHandler](https://docs.fivem.net/docs/scripting-reference/runtimes/lua/functions/AddEventHandler/)  
[NetworkGetNetworkIdFromEntity](https://docs.fivem.net/natives/?_0x9E35DAB6)  
[NetworkGetEntityFromNetworkId](https://docs.fivem.net/natives/?_0x5B912C3F)  
[DeleteEntity](https://docs.fivem.net/natives/?_0xFAA3D236)  
