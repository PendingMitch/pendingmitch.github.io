---
title: Get Entity Speed (MPH)
date: 2024-06-04 13:00:00 -0000
categories: [PendingDevelopment, PendingYourCreation]
tags: [pendingyourcreation]
---

Getting the speed of vehicles is easy once you know how! Rounding numbers and converting GTA's units to MPH can be difficult for new developers.

## client.lua
```lua
function GetSpeedOf(Entity)
    if Entity == false then return 0 end

    local Speed = GetEntitySpeed(Entity)
    Speed = Speed * 2.2369 -- Convert to miles per hour
    Speed = math.floor(Speed)

    return Speed
end

```

## References

[GetEntitySpeed](https://docs.fivem.net/natives/?_0xD5037BA82E12416F)