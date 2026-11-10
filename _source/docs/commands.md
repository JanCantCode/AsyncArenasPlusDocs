---
title: Arena Reset Commands and Permissions
description: AsyncArenasPlus commands for creating, resetting, scheduling, rotating, editing, and migrating Minecraft arenas, including the admin permission.
---

# Arena Commands

All normal arena commands are under:

```text
/arena
```

Required permission:

```text
asyncarenasplus.admin
```

## Time values

Commands that accept time use the same parser:

- `10s`: seconds
- `5m`: minutes
- `3h`: hours
- `1d`: days
- `20t`: ticks

Use an explicit unit in commands. No-suffix values are treated as ticks.

## Create

Create from your current wand selection:

```text
/arena create <name> [time]
```

Create from exact coordinates:

```text
/arena create <name> <world> <x1> <y1> <z1> <x2> <y2> <z2> [time]
```

If a time is provided, it becomes the arena's periodic reset interval.

## Wand

```text
/arena wand
```

Gives the arena selection amethyst shard to an in-game player.

Selection controls:

- Left click: position 1
- Right click: position 2

## Reset

```text
/arena reset <name>
```

Runs a manual arena reset.

## Edit

```text
/arena edit <name>
```

Saves the arena from the current world state while keeping the same bounds and schedule.

Recommended workflow:

```text
/arena pause <time>
/arena reset <name>
```

Make your changes, then run:

```text
/arena edit <name>
/arena pause off
```

## Info

```text
/arena info <name>
```

Shows:

- display name
- world
- bounds
- clickable midpoint teleport
- automatic reset schedule and next reset time

## List

```text
/arena list
```

Shows all loaded arenas with display name, world, and periodic reset schedule.

## Display Name

```text
/arena displayname <arena> <new display name>
```

Sets the public display name stored in `config.yml` under `arena-display-names`.

Arena files use the name you entered when creating the arena. Display names let placeholders and command output show a cleaner public name without renaming the arena file.

Example:

```text
/arena displayname pvp_1 PVP Arena 1
```

## Periodic Reset Schedule

```text
/arena periodic <name> <time> [offset]
```

Behavior:

- `time` sets the interval.
- `offset` is optional and delays when that arena starts its schedule.
- You do not need to specify an offset.
- A `time` of `0` disables automatic resets for that arena.

Examples:

```text
/arena periodic mine_1 15m
/arena periodic mine_1 15m 2m
/arena periodic mine_1 0
```

## Rotation Setup

```text
/arena rotation <time_between_resets> <arena1> <arena2> [arena3...]
```

This configures all listed arenas as one rotation.

Example:

```text
/arena rotation 5m red blue green
```

This rotates the shared gameplay area between `red`, `blue`, and `green`, with one variant applying every 5 minutes.

## Pause Or Resume Automatic Resets

Pause all automatic periodic resets:

```text
/arena pause <time>
```

Resume:

```text
/arena pause off
```

`resume` is also accepted:

```text
/arena pause resume
```

Check status:

```text
/arena pause status
```

`/arena pause 0` also resumes automatic resets.

## Reload Configuration

```text
/arena reload
```

Reloads `config.yml`, display names, and configured periodic schedules.

## Delete Arena

```text
/arena delete <name>
```

Deletes the arena from memory and removes its `.aarena` file if it exists.

## Migration

Use the default available provider:

```text
/arena migrate <name|all>
```

Use a specific provider:

```text
/arena migrate <provider> <name|all>
```

Providers:

- `asyncarenas`
- `arearesetterpro`
- `areareloader-fawe`

See [Migration Guide](migrations.md) for behavior and naming rules.
