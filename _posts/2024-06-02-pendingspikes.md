---
title: PendingSpikes
date: 2024-06-02 13:40:00 -0000
categories: [PendingDevelopment, PendingSpikes]
tags: [fivem, development]
---

## Background

[PendingSpikes](https://pendingmitch.tebex.io/category/fivem) is a project that aims to create a simple, effective, and beautiful script for utilisiing spike strips in FiveM.

## Features

- Player Animations.
- Spike strip animations.
- Customisable spike strip length.
- Command and interaction support.
- Removing all spikes in a group at one time.
- Integration with RPEmotes.
- Exports and Events for developers.

## Try it Out!

Try it out at [PendingDevelopment's Tebex Webstore](https://pendingmitch.tebex.io/category/fivem).

## Credits

- [loaf_spikestrips](https://github.com/loaf-scripts/loaf_spikestrips) for the original script (forked from v1.2.1). - PendingDevelopment will work to fix any of the performance issues addressed between v1.2.1 and v2.1.0 in releases coming soon.

---

## Install

1. Add `PendingSpikes` to your `resources` folder.
2. Add `ensure PendingSpikes` to your server.cfg.
3. Configure the config.json file.
4. If you require use of `PendingToast`, install as described [here](https://pendingmitch.dev/posts/pendingtoast/).
4. If you require use of [rpemotes-reborn](https://github.com/alberttheprince/rpemotes-reborn) or [rpemotes](https://github.com/jimathy/rpemotes/blob/master/README.md) install the resources as "rpemotes".

---

# Config

| Config Name                      | Description                                                                                                                                                                                                           | Default Value                              | Other Possible Values                            |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ | ------------------------------------------------ |
| DEBUG                            | Toggle debug prints in the F8 console. More debugging prints will be made in future releases. This may hape PendingDevelopment troubleshoot your issues.                                                              | false                                      | true                                             |
| NPC_VEHICLES                     | Allow spikes strips to effect NPC / AI vehicles                                                                                                                                                                       | true                                       | false                                            |
| MESSAGE_STRINGS/REMOVE_STINGER   | The text to display to notify the user how to remove the spike strips.                                                                                                                                                | "~INPUT_CONTEXT~ ~r~Remove ~s~spikestrip"  | Any String                                       |
| MESSAGE_STRINGS/PLACE_STINGER    | The text to display to notify the user how to place the spike strips. This will only display if you have VEHICLE_BOOTS enabled, as a command can be used otherwise.                                                   | "~INPUT_CONTEXT~ ~g~Place ~s~spikestrip"   | Any String                                       |
| VEHICLE_BOOTS                    | Whether to enable the VEHICLE_BOOTS section of the script.                                                                                                                                                            | false                                      | true                                             |
| SET_SPIKE_COMMAND                | The command to use when VEHICLE_BOOTS is disabled.                                                                                                                                                                    | spike                                      | Any String                                       |
| SPIKE_LENGTH                     | How many individual strips to use when placing the spikes.                                                                                                                                                            | 2                                          | Any Integer                                      |
| PLAYER_ANIMATION/ENABLED         | Whether to enable player animation when placing down the spikes                                                                                                                                                       | true                                       | false                                            |
| PLAYER_ANIMATION/DICTIONARY      | Dictionary for the player animation.                                                                                                                                                                                  | "amb@world_human_bum_wash@male@low@idle_a" | Any dictionary (leave default if you're unsure). |
| PLAYER_ANIMATION/ANIMATION       | Animation name for the player animation.                                                                                                                                                                              | "idle_a"                                   | Any animation (leave default if you're unsure).  |
| PLAYER_ANIMATION/RP_EMOTES       | Whether to enable to integration with [rpemotes-reborn](https://github.com/alberttheprince/rpemotes-reborn) or [rpemotes](https://github.com/jimathy/rpemotes/blob/master/README.md). Resource name must be rpemotes. | true                                       | false                                            |
| PLAYER_ANIMATION/RP_EMOTES_EMOTE | The emote name to run when the player is holding the spike strips box.                                                                                                                                                | "suitcase2"                                | Any valid emote.                                 |
| SPIKE_ANIMATION | Whether to show the spike strips being laid accross the floor. If this is off, they will instantly be set down.                                                                                                       | true                                       | false                                            |

---

# Vehicle Boots Info

The vehicle boots part of the script allows you to gather the spike strips from a location, such as a vehicle boot, allowing more interactive roleplaying scenarios.

This part of the script was made with the idea of [ox_target](https://github.com/overextended/ox_target) in mind. Here you can see an example of the script in action. Their documentation can be found [here](https://overextended.dev/ox_target).

```lua
exports.ox_target:addModel(VehicleName, {
    {
        label = "Stinger",
        onSelect = function()
            if not exports.PendingSpikes:DoesPlayerHaveSpikesInHand() then
                exports.PendingSpikes:TakeOutSpikes(true)
            else
                exports.PendingSpikes:PutAwaySpikes(true)
            end
        end
    },
})
```

---

# Exports

## TakeOutSpikes

```lua
exports.PendingSpikes:TakeOutSpikes(DisplayNotification)
```

DisplayNotification: Whether to display a PendingToast notification. If not using PendingToast, leave blank.

## PutAwaySpikes

```lua
exports.PendingSpikes:PutAwaySpikes(DisplayNotification)
```

DisplayNotification: Whether to display a PendingToast notification. If not using PendingToast, leave blank.

---

# Client Events

## PendingSpikes:TakeOutSpikes

```lua
TriggerEvent("PendingSpikes:TakeOutSpikes", DisplayNotification)
```

DisplayNotification: Whether to display a PendingToast notification. If not using PendingToast, leave blank.

## PendingSpikes:PutAwaySpikes

```lua
TriggerEvent("PendingSpikes:PutAwaySpikes", DisplayNotification)
```

DisplayNotification: Whether to display a PendingToast notification. If not using PendingToast, leave blank.
