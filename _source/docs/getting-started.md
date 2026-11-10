---
title: Set Up Automatic Minecraft Arena Resets
description: Install AsyncArenasPlus, select and save a Minecraft arena, test a manual reset, and automatically restore the area every five minutes.
---

# How to Set Up Automatic Minecraft Arena Resets

This guide creates a saved Minecraft arena and restores it on a timer with AsyncArenasPlus. WorldEdit and FAWE are not required. Check the [current product listing](https://builtbybit.com/resources/asyncarenasplus-fastest-arena-resets.110929/) for supported Minecraft versions before installing a build.

## Example: reset an area every five minutes

After completing the installation and license setup below, run `/arena wand` and select two corners of your arena. Save it with `/arena create pvp`, change a few blocks, and test `/arena reset pvp`. Then run `/arena periodic pvp 5m` to enable automatic resets every five minutes.

You need the `asyncarenasplus.admin` permission; server operators have it by default. Verify the selected boundaries and saved layout before enabling a timer.

## 1. Install plugins

Required:

- AsyncArenasPlus

No other plugin is required for normal arena creation and resets.

## 2. License loader setup

If you bought AsyncArenasPlus:

1. Put the plugin jar in your server's `plugins` folder.
2. Start the server once.
3. Stop the server.
4. Open:

```text
plugins/AsyncArenasPlus/loader.yml
```

5. Add the license from the purchase Discord.
6. Start the server again.

Optional:

- PlaceholderAPI, if you want reset countdown placeholders.
- AsyncArenas, AreaResetterPro, or AreaReloader-FAWE, if you want to migrate existing arenas.

## 3. Create your first arena

1. Get the arena selection item:

```text
/arena wand
```

2. Use the amethyst shard to select two corners of your arena area.

3. Create the arena:

```text
/arena create <name>
```

Optional: create and set periodic reset in one step:

```text
/arena create <name> <time>
```

Tip: you can also create by coordinates:

```text
/arena create <name> <world> <x1> <y1> <z1> <x2> <y2> <z2> [time]
```

Time values support `10s`, `5m`, `3h`, `1d`, `20t`, or a raw tick value with no suffix.

## 4. Verify reset

1. Change blocks inside the arena.
2. Run:

```text
/arena reset <name>
```

## 5. Set periodic resets

Basic:

```text
/arena periodic <name> <time>
```

Offset is optional. Most arenas do not need one.

Optional offset example:

```text
/arena periodic <name> <time> <offset>
```

Example:

```text
/arena periodic pvp_1 15m 2m
```

This means:

- `pvp_1` resets every 15 minutes
- it waits 2 minutes before starting that schedule, which can help spread resets out

Use `/arena pause <time>` to temporarily stop all automatic periodic resets, `/arena pause off` to resume, and `/arena pause status` to check the current state.

## 6. Rotate one gameplay area between multiple terrain variants

If you want one physical area to cycle through different terrain versions:

1. Create arena variant A for that area.
2. Change the area to variant B and create a second arena with the same bounds.
3. Run the rotation command.

Example:

```text
/arena rotation 5m arena_variant_a arena_variant_b
```

This makes the same area alternate between stored variants every 5 minutes.

## 7. Inspect the result

Useful checks after setup:

```text
/arena list
/arena info <name>
```

`/arena info <name>` shows bounds, display name, and next periodic reset timing.
