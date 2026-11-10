---
title: Minecraft Area & Arena Reset Plugin
description: AsyncArenasPlus is a Minecraft area and arena reset plugin for Paper and Folia. Restore saved regions manually or on a timer without WorldEdit or FAWE.
---

# AsyncArenasPlus: Minecraft Area and Arena Reset Plugin

AsyncArenasPlus is a Minecraft Java server plugin for restoring selected areas and arenas to saved states. Use it to reset PvP arenas, repair spawn areas, restore minigame maps, or rotate one region between different terrain layouts. Resets can run manually or automatically on a timer.

Normal arena creation and resets do not require WorldEdit, FastAsyncWorldEdit (FAWE), or another plugin.

[Get AsyncArenasPlus on BuiltByBit](https://builtbybit.com/resources/asyncarenasplus-fastest-arena-resets.110929/){ .md-button .md-button--primary }
[Installation and setup](getting-started.md){ .md-button }

## Reset a Minecraft arena every five minutes

After [installing and activating the plugin](getting-started.md#2-license-loader-setup):

1. Run `/arena wand` and select two opposite corners of the area you want to restore.
2. Run `/arena create pvp` to save the arena's current state.
3. Change a few blocks inside the area, then run `/arena reset pvp` to verify that they return to the saved state.
4. Run `/arena periodic pvp 5m` to reset the arena automatically every five minutes.

The selection is the region that will be restored, so check its boundaries before enabling automatic resets. See the [full setup guide](getting-started.md) for coordinates, time formats, and terrain rotation.

## What can you reset?

| Server area | Example workflow |
| --- | --- |
| PvP, Crystal PvP, or practice arena | Save the arena before play and restore it manually or on a timer. |
| Spawn or public building area | Periodically return the selected region to its saved layout. |
| Mine or minigame map | Restore the blocks captured in the saved arena. |
| Arena with multiple terrain layouts | Save variants of the same region and [rotate between them](main-features.md#terrain-rotation). |

A reset restores a saved region. It does not generate a new world or automatically provide minigame rules, queues, or match-end detection.

## Compatibility and dependencies

| Requirement | Details |
| --- | --- |
| Edition and server software | Minecraft Java Edition; Paper and Folia. Check the [current product listing](https://builtbybit.com/resources/asyncarenasplus-fastest-arena-resets.110929/) for the Minecraft versions supported by the build you purchase. |
| WorldEdit or FAWE | Not required for normal arena creation and resets. An optional compatibility layer supports external editing workflows. |
| PlaceholderAPI | Optional; adds [reset countdown placeholders](placeholders.md). |
| An existing arena plugin | Only required while [importing arenas](migrations.md) from that plugin. |
| License setup | Follow the [installation instructions](getting-started.md#2-license-loader-setup) to activate a purchased build. |

## AsyncArenas or AsyncArenasPlus?

[AsyncArenas](https://builtbybit.com/resources/asyncarenas-fast-arena-resets.46153/) and AsyncArenasPlus are separate paid plugins by the same creator. AsyncArenas uses a FAWE-based workflow. Plus has its own reset workflow and does not require FAWE for normal resets.

Plus is designed for repeated arena restoration while players are online, with controls for pacing player-visible updates. Actual reset duration and smoothness depend on the arena, server, settings, and nearby players; there is no universal zero-lag guarantee.

Read the [arena reset plugin comparison](arena-reset-plugin-comparison.md) for tradeoffs, free alternatives, and how to evaluate reset performance on your server. Existing AsyncArenas users can [migrate saved arenas](migrations.md).

## Common questions

### Can I automatically reset a selected Minecraft area?

Yes. Select two corners, save the region with `/arena create <name>`, and set a timer with `/arena periodic <name> <time>`. For example, `/arena periodic pvp 5m` resets the saved `pvp` arena every five minutes.

### Does an arena reset restore my build or regenerate the world seed?

It restores the region to the state saved when you created or last edited that arena. To change the saved layout, follow the [template editing workflow](main-features.md#editing-saved-templates).

### Can I display a countdown before the next reset?

Yes. With PlaceholderAPI installed, use `%asyncarenasplus_reset_time_pvp%` for an arena named `pvp`. See [countdown placeholders](placeholders.md) for additional formats and multiple arenas.

### Where are the commands and troubleshooting steps?

See [arena commands](commands.md), [configuration](configuration.md), and [troubleshooting](troubleshooting.md). For support, use the [AsyncArenasPlus Discord](https://discord.gg/GY73CJuvHQ).
