---
title: PendingSound v2.0 Changelog - The Entity Update
date: 2024-06-08 09:00:00 -0000
categories: [PendingDevelopment, PendingSound]
tags: [fivem, development]
---

# New Exports

## PlaySoundFromEntity - Client

{: .prompt-info}
> Please note that if the entity plays a sound whilst out of render for the player, the entity will not play that sound.

```lua
exports["PendingSound"]:PlaySoundFromEntity(sound, resource, entity, volume)
```
E.G.:  
sound: "sound.ogg"  
resource: "MyResource"
entity: GetPlayerPed(-1)
volume: 1

```lua
exports.PendingSound:PlaySoundFromEntity("sound.ogg", "MyResource", GetPlayerPed(-1), 1)
```


You can combat repeating "MyResource" by doing the following:
```lua
exports.PendingSound:PlaySoundFromEntity("sound.ogg", GetCurrentResourceName(), GetPlayerPed(-1), 1)
```


## PlaySoundFromEntityURL - Client

{: .prompt-info}
> Please note that if the entity plays a sound whilst out of render for the player, the entity will not play that sound.

```lua
exports["PendingSound"]:PlaySoundFromEntity(url, entity, volume)
```
E.G.:  
url: "https://mywebsite.com/mymp3.mp3"  
entity: GetPlayerPed(-1)
volume: 1

```lua
exports.PendingSound:PlaySoundFromEntity("https://mywebsite.com/mymp3.mp3", GetPlayerPed(-1), 1)
```

## StopSoundFromEntity - Client

```lua
exports["PendingSound"]:StopSoundFromEntity(Entity)
```
entity: GetPlayerPed(-1)

## PlayLocalSoundURL - Client

```lua
exports["PendingSound"]:PlayLocalSoundURL(pos, url, volume)
```
E.G.:  
pos: {x = 0.0, y = 0.0, z = 0.0}  
url: "https://mywebsite.com/mymp3.mp3"  
volume: 1

## PlayLocalSoundURL - Server

```lua
exports["PendingSound"]:PlayLocalSoundURL(pos, url, volume)
```
E.G.:  
pos: {x = 0.0, y = 0.0, z = 0.0}  
url: "https://mywebsite.com/mymp3.mp3"  
volume: 1




