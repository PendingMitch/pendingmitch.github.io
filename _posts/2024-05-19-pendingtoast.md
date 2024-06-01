---
title: PendingToast
date: 2024-05-19 13:00:00 -0000
categories: [PendingDevelopment, PendingToast]
tags: [fivem, development]
---

## Background

[PendingToast](https://pendingmitch.tebex.io/category/fivem) is a project that aims to create a simple method of sending toast notifications to your players.

Playing on different servers it becomes apparent that new players may struggle understanding nuances about certain scripts. For example, they may question why they can't open a certain door as a civilian. No longer! With PendingToast, you can let them know that they can't open the door because they aren't on duty in a simple, effective manner.

## Try it Out!

Try it out at [PendingDevelopment's Tebex Webstore](https://pendingmitch.tebex.io/package/6273535).

---

## Send a Notification

1. Add `PendingToast` to your `resources` folder.
2. Add `ensure PendingToast` to your server.cfg.
3. Use events described below.
4. If you require use of `PendingSound`, install as described [here](https://github.com/PendingMitch/PendingSound/releases/latest)

---

# Exports

## Notify - From Client

```lua
TriggerEvent("PendingToast:Notify", NotificationOptions, SoundInfo)
```

E.G.:  
Src: 1  
NotificationOptions: [See below...](#notificationoptions)  
SoundInfo: [See below...](#soundinfo)

## Notify - From Client to Server to Another Client

```lua
TriggerServerEvent("PendingToast:Notify", Src, NotificationOptions, SoundInfo)
```

E.G.:  
Src: 1  
NotificationOptions: [See below...](#notificationoptions)  
SoundInfo: [See below...](#soundinfo)

## Notify - From Server to Client

```lua
TriggerClientEvent("PendingToast:Notify", Src, NotificationOptions, SoundInfo)
```

E.G.:  
Src: 1  
NotificationOptions: [See below...](#notificationoptions)  
SoundInfo: [See below...](#soundinfo)

## Notify - Presets

As a simple starter, we've implemented some default presets. Feel free to use them, or create your own!

```lua
TriggerEvent("PendingToast:Success", NotificationOptions, SoundInfo)
TriggerClientEvent("PendingToast:Success", Src, NotificationOptions, SoundInfo)
TriggerServerEvent("PendingToast:Success", Src, NotificationOptions, , SoundInfo)
```

All default presets:

-   PendingToast:Success
-   PendingToast:Info
-   PendingToast:Error

---

## NotificationOptions

| Object Key        | Example Input                                  | Default Input (If left blank) |
| ----------------- | ---------------------------------------------- | ----------------------------- |
| Text              | "This is a notification!"                      | "PendingDevelopment"          |
| LengthInSeconds   | 10                                             | 5                             |
| BarColour         | "green" or "#ffffff"                           | undefined                     |
| ImageURL          | "https://pendingmitch.dev/assets/img/Icon.png" | "imgs/PendingDevelopment.svg" |
| RoundedBackground | true                                           | false                         |

---

## SoundInfo

The SoundInfo object relates PendingToast to PendingSound. Note that is this is left undefined, or Resource or Sound values aren't set, PendingToast will nto attempt to call PendingSound. In addition, if PendingSound is not started PendingToast will not attempt to call PendingSound.

| Object Key | Example Input            | Default Input (If left blank) |
| ---------- | ------------------------ | ----------------------------- |
| Resource   | GetCurrentResourceName() |                               |
| Sound      | "sounds/MySound.mp3"     |                               |
| Volume     | 0.5                      | 1                             |

---

For use in JavaScript and C# see FiveM's [Triggering Events](https://docs.fivem.net/docs/scripting-manual/working-with-events/triggering-events/) page.
