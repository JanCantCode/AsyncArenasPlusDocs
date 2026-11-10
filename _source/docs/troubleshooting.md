---
title: Troubleshoot Minecraft Arena Resets
description: Fix AsyncArenasPlus reset problems, slow player-visible updates, lighting issues, migration failures, and automatic reset schedules.
---

# Troubleshooting

## Arena is not resetting as expected

1. Confirm the arena exists:

```text
/arena list
```

2. Check the arena details:

```text
/arena info <name>
```

3. Run a manual reset:

```text
/arena reset <name>
```

If the saved arena version is wrong, update it with the safe edit workflow:

```text
/arena pause <time>
/arena reset <name>
```

Make your changes, then save them:

```text
/arena edit <name>
/arena pause off
```

## Players see resets slowly

Large arenas may need more time to visually update for every player.

If you know what you are doing, you can adjust:

```yaml
update-queue:
  enabled: true
  max-sections-per-player-per-tick: 6
```

Higher values make reset visuals appear faster but can increase packet bursts.

## Light looks wrong after a reset

Make sure light update packets are enabled:

```yaml
reset-packets:
  send-light-updates: true
```

If the arena was saved with bad lighting, fix the lighting in-world and run:

```text
/arena edit <name>
```

## Migration provider says "not available"

The plugin you are migrating from must be:

- installed
- enabled
- running on the same server while you migrate

After migration is complete, you can disable or remove the old plugin.

## Migration fails for one arena

Try migrating one arena at a time:

```text
/arena migrate <provider> <arena>
```

Confirm that the old plugin can still load or reset that arena before migrating it.

## Periodic resets feel bursty

Use the rotation helper for shared-area rotations:

```text
/arena rotation <time_between_resets> <arena1> <arena2> [arena3...]
```

For unrelated arenas, offsets are optional. Use one only when you want an arena to start its schedule later than another arena:

```text
/arena periodic <name> <time> <offset>
```

## Automatic resets need to stop temporarily

Pause every automatic periodic reset:

```text
/arena pause 5m
```

Resume:

```text
/arena pause off
```

Check status:

```text
/arena pause status
```

Manual `/arena reset <name>` still works while automatic resets are paused.
