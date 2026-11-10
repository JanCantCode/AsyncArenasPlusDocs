---
title: Arena Reset Features and Terrain Rotation
description: Create and restore Minecraft areas with AsyncArenasPlus, schedule arena resets, rotate terrain variants, display countdowns, and import existing arenas.
---

# AsyncArenasPlus Arena Reset Features

AsyncArenasPlus combines saved-region restoration, automatic reset timers, terrain rotation, and optional countdown placeholders. Use the examples below after [installing the plugin](getting-started.md).

## Arena creation

Use `/arena wand`, click two corners, then run `/arena create <name>`.

This is the normal workflow for creating new arenas.

Console users, command blocks, and scripted setup can create arenas with exact coordinates:

```text
/arena create <name> <world> <x1> <y1> <z1> <x2> <y2> <z2> [time]
```

## Manual arena resets

Use:

```text
/arena reset <name>
```

for immediate resets during events, testing, or moderation.

## Editing saved templates

To update the saved version of an arena:

1. Pause automatic resets.
2. Reset the arena you want to modify.
3. Make your changes in the world.
4. Save the new version.

Commands:

```text
/arena pause <time>
/arena reset <name>
/arena edit <name>
```

After you are done, resume automatic resets:

```text
/arena pause off
```

## Periodic resets

Use:

```text
/arena periodic <name> <time> [offset]
```

How it behaves:

- `time`: how often the arena resets
- `offset`: optional delay before that arena starts its schedule
- You do not need to specify an offset.

You can globally pause/resume automatic periodic resets with:

```text
/arena pause <time|off|status>
```

Time values support `10s`, `5m`, `3h`, `1d`, `20t`, or a raw tick value with no suffix.

## Terrain rotation

Use rotation when one gameplay area should cycle through multiple terrain variants.

Typical setup:

1. Create multiple arenas that cover the same area, each saved in a different terrain state.
2. Run the rotation command.

```text
/arena rotation <time_between_resets> <arena1> <arena2> [arena3...]
```

Example:

```text
/arena rotation 5m red blue green
```

This rotates the shared gameplay area between `red`, `blue`, and `green`, with one variant applying every 5 minutes.

## Display names

Arena files use the name you entered when creating the arena. If that name is not clean enough for public placeholders or command output, set a display name:

```text
/arena displayname <arena> <new display name>
```

Display names are shown by `/arena list`, `/arena info`, and PlaceholderAPI placeholders that return arena names.

## PlaceholderAPI reset countdowns

When PlaceholderAPI is installed, AsyncArenasPlus registers the `asyncarenasplus` expansion.

Supported placeholders:

- `%asyncarenasplus_reset_time_<arena>%`
- `%asyncarenasplus_reset_soonest_time_<arena1,arena2,...>%`
- `%asyncarenasplus_reset_soonest_name_<arena1,arena2,...>%`

See [PlaceholderAPI](placeholders.md) for examples and return values.

## Low-lag resets and compatibility

AsyncArenasPlus is designed for repeated arena resets during normal gameplay, with a configurable queue for pacing player-visible updates. Actual reset time and smoothness depend on arena size, server resources, nearby players, and configuration. See [reset performance and comparison](arena-reset-plugin-comparison.md#how-should-i-compare-arena-reset-performance).

An optional WorldEdit compatibility layer is available for servers that use external editing workflows.

## Migration from other arena plugins

You can import existing arenas from supported providers using `/arena migrate ...`.

Current providers:

- `asyncarenas`
- `arearesetterpro`
- `areareloader-fawe`
