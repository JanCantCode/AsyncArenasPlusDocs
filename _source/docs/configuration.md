---
title: Arena Reset Configuration and Update Queue
description: Configure AsyncArenasPlus licensing, reset packets, lighting updates, the player update queue, and saved Minecraft arena files.
---

# Configuration

The main config file is:

```text
plugins/AsyncArenasPlus/config.yml
```

Run this after editing it:

```text
/arena reload
```

## Loader License

If you bought AsyncArenasPlus, start the server once after installing the plugin jar. The plugin creates:

```text
plugins/AsyncArenasPlus/loader.yml
```

Put the license from the purchase Discord into `loader.yml`, then restart the server.

## Periodic Resets

```yaml
periodic-resets: {}
periodic-offsets: {}
```

`periodic-resets`
: Controls how often each arena resets automatically. The key is the arena name and the value is the reset interval.

`periodic-offsets`
: Optional. Delays when an arena starts its reset schedule. This is useful when you have multiple arenas and do not want all of them resetting at the same time.

Example:

```yaml
periodic-resets:
  mine_1: 15m
  mine_2: 15m
periodic-offsets:
  mine_2: 5m
```

In this example, both arenas reset every 15 minutes, but `mine_2` starts 5 minutes later than `mine_1`.

Most arenas do not need an offset.

Time values support `10s`, `5m`, `3h`, `1d`, `20t`, or a raw tick value with no suffix. Use explicit units in normal configs.

## Display Names

```yaml
arena-display-names: {}
```

Arena files use the name from `/arena create <name>`. Display names let command output and placeholders show a cleaner public name without renaming the arena file.

Example:

```yaml
arena-display-names:
  mine_1: Mine Arena 1
```

## Reset Packets

```yaml
reset-packets:
  use-precise-dirty-blocks: false
  send-light-updates: true
```

`use-precise-dirty-blocks`
: Advanced/debug option for reset packet behavior. Do not change this unless you know what you are doing or have been asked to while troubleshooting.

`send-light-updates`
: Sends lighting updates to players after arena resets. Keep this enabled if players need lighting to update immediately after a reset.

## Reset Section Preparation

```yaml
reset-sections:
  preparation-mode: construct-from-scratch
```

Supported values:

- `construct-from-scratch`: safest option and the recommended default.
- `copy`: can be faster, but can cause weird issues in certain server/plugin contexts.

Stick to `construct-from-scratch` unless you have tested your server, confirmed this part is actually too slow, and verified that `copy` behaves correctly in your setup.

## Update Queue

```yaml
update-queue:
  enabled: true
  max-sections-per-player-per-tick: 6
  max-queued-sections-per-player: 10000
```

`enabled`
: Controls whether visible reset updates are smoothed out for players instead of being sent all at once.

`max-sections-per-player-per-tick`
: Controls how quickly each player receives visible reset updates. Higher values make reset visuals appear faster, but send more packets at once.

`max-queued-sections-per-player`
: Limits how many visible reset updates can wait for one player. This prevents unbounded queues during very large resets.

## Arena Files

AsyncArenasPlus stores arena files in:

```text
plugins/AsyncArenasPlus/arenas/
```

Each arena is stored as:

```text
<arenaName>.aarena
```
