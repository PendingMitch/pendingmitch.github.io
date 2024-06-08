---
title: PendingSound
date: 2024-05-19 13:00:00 -0000
categories: [PendingDevelopment, PendingSound]
tags: [fivem, development]
---

## Background

[PendingSound](https://pendingmitch.tebex.io/category/fivem) is a FiveM utility resource that allows you to play sounds to your clients in a modular way. It's the first of it's kind; the FiveM client code was even changed because of it. See the [FiveM forum thread](https://forum.cfx.re/t/sharing-audio-between-resources/5012406/6?u=pendingmitch).

## Play a sound

1. Add `PendingSound` to your `resources` folder.
2. Add `ensure PendingSound` to your server.cfg **BEFORE** any resources with sound playing through PendingSound. 
3. Create or edit a resource that is above the "cerelean" FX Version. See [Resource Manifest](https://docs.fivem.net/docs/scripting-reference/resource-manifest/resource-manifest/#fx-version-cerulean-2020-05) for more information.
4. Add the sound files that you wish to play into the resource that you wish to play it from.
5. Add the following in your `__resource.lua` file, replacing the sound file names with the ones that you will use. There is support for all sound files that can be played through HTML and FiveM's NUI system. !! Ensure that you add the file extension name at the end, and any folder directories that may be before the sound file itself !! 
```lua 
dependency 'PendingSound'
files {
  "sound1.ogg",
  "sound2.ogg"
}
```
6. Use PlaySound export.

---

# Exports
## PlaySound - Client

```lua
exports["PendingSound"]:PlaySound(name, resource, volume)
```
E.G.:  
name: "sound.ogg"  
resource: "MyResource"  
volume: 1 (Volume is between 0-1)  

```lua
exports["PendingSound"]:PlaySound("sound.ogg", "MyResource", 1)
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:PlaySound("sound.ogg", GetCurrentResourceName(), 1)
```

## PlaySound - Server

```lua
exports["PendingSound"]:PlaySound(src, name, resource, volume)
```
E.G.:  
src: -1  
name: "sound.ogg"  
resource: "MyResource"  
volume: 1 (Volume is between 0-1)  

```lua
exports["PendingSound"]:PlaySound(-1, "sound.ogg", "MyResource", 1)
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:PlaySound(-1, "sound.ogg", GetCurrentResourceName(), 1)
```
----
## PlaySoundURL - Client

```lua
exports["PendingSound"]:PlaySoundURL(name, resource, volume)
```
E.G.:  
name: "https://mywebsite.com/mymp3.mp3"  
resource: "MyResource"  
volume: 1 (Volume is between 0-1)  

```lua
exports["PendingSound"]:PlaySoundURL("https://mywebsite.com/mymp3.mp3", "MyResource", 1)
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:PlaySoundURL("https://mywebsite.com/mymp3.mp3", GetCurrentResourceName(), 1)
```

## PlaySoundURL - Server

```lua
exports["PendingSound"]:PlaySoundURL(src, url, resource, volume)
```
E.G.:  
src: -1  
url: "https://mywebsite.com/mymp3.mp3"  
resource: "MyResource"  
volume: 1 (Volume is between 0-1)  

```lua
exports["PendingSound"]:PlaySoundURL(-1, "https://mywebsite.com/mymp3.mp3", "MyResource", 1)
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:PlaySoundURL(-1, "https://mywebsite.com/mymp3.mp3", GetCurrentResourceName(), 1)
```
----
## PlayLocalSound - Client

PlayLocalSound plays a sound based off a coordinate. This function only plays the sound to the play of which the client script is running on.

```lua
exports["PendingSound"]:PlayLocalSound(pos, sound, resource, volume)
```
E.G.:  
pos: {x = 0.0, y = 0.0, z = 0.0}  
sound: "sound.ogg"  
resource: "MyResource"
volume: 1

```lua
  exports["PendingSound"]:PlayLocalSound({x = 0.0, y = 0.0, z = 0.0}, "sound.ogg", "MyResource", 1)
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:PlayLocalSound({x = 0.0, y = 0.0, z = 0.0}, "sound.ogg", GetCurrentResourceName(), 1)
```

## PlayLocalSound - Server

```lua
TriggerServerEvent("PendingSound:PlayLocalSound", pos, sound, resource, volume)
```

PlayLocalSound plays a sound based off a coordinate. This function plays the sound to all clients. If they are close enough - they will hear it.


```lua
exports["PendingSound"]:PlayLocalSound(pos, sound, resource, volume)
```
E.G.:  
pos: {x = 0.0, y = 0.0, z = 0.0}  
sound: "sound.ogg"  
resource: "MyResource"
volume: 1

```lua
  exports["PendingSound"]:PlayLocalSound({x = 0.0, y = 0.0, z = 0.0}, "sound.ogg", "MyResource", 1)
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:PlayLocalSound({x = 0.0, y = 0.0, z = 0.0}, "sound.ogg", GetCurrentResourceName(), 1)
```

---

## PlayLocalSoundURL - Client

{: .prompt-info}
> Minimum Version Number: 2.0 "The Entity Update"

```lua
exports["PendingSound"]:PlayLocalSoundURL(pos, url, volume)
```
E.G.:  
pos: {x = 0.0, y = 0.0, z = 0.0}  
url: "https://mywebsite.com/mymp3.mp3"  
volume: 1

## PlayLocalSoundURL - Server

{: .prompt-info}
> Minimum Version Number: 2.0 "The Entity Update"

```lua
exports["PendingSound"]:PlayLocalSoundURL(pos, url, volume)
```
E.G.:  
pos: {x = 0.0, y = 0.0, z = 0.0}  
url: "https://mywebsite.com/mymp3.mp3"  
volume: 1

---

## PlaySoundFromEntity - Client

{: .prompt-info}
> Minimum Version Number: 2.0 "The Entity Update"

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
> Minimum Version Number: 2.0 "The Entity Update"

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

----
## StopSound - Client

```lua
exports["PendingSound"]:StopSound(name, resource)
```
E.G.:  
name: "sound.ogg"  
resource: "MyResource"  

```lua
exports["PendingSound"]:StopSound("sound.ogg", "MyResource")
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:StopSound("sound.ogg", GetCurrentResourceName())
```

## StopSound - Server

```lua
exports["PendingSound"]:StopSound(src, name, resource)
```
E.G.:  
src: -1  
name: "sound.ogg"  
resource: "MyResource"  

```lua
exports["PendingSound"]:StopSound(-1, "sound.ogg", "MyResource")
```
You can combat repeating "MyResource" by doing the following:
```lua
exports["PendingSound"]:StopSound(-1, "sound.ogg", GetCurrentResourceName())
```
----
## StopSoundURL - Client

```lua
exports["PendingSound"]:StopSoundURL(url)
```
E.G.:  
url: "https://mywebsite.com/mymp3.mp3"  

```lua
exports["PendingSound"]:StopSoundURL("https://mywebsite.com/mymp3.mp3")
```

## StopSoundURL - Server

```lua
exports["PendingSound"]:StopSoundURL(src, url)
```
E.G.:  
src: -1  
url: "https://mywebsite.com/mymp3.mp3"  

```lua
exports["PendingSound"]:StopSoundURL(-1, "https://mywebsite.com/mymp3.mp3")
```

## StopSoundFromEntity - Client

{: .prompt-info}
> Minimum Version Number: 2.0 "The Entity Update"

```lua
exports["PendingSound"]:StopSoundFromEntity(Entity)
```
entity: GetPlayerPed(-1)