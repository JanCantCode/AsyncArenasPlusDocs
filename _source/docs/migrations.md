---
title: Migrate Arenas to AsyncArenasPlus
description: Import Minecraft arenas from AsyncArenas, AreaResetterPro, or AreaReloader-FAWE into AsyncArenasPlus and verify the imported resets.
---

# Migration Guide

AsyncArenasPlus can import arenas from supported plugins.

## Supported Sources

- `asyncarenas`
- `arearesetterpro`
- `areareloader-fawe`

## Requirement

The plugin you are migrating from must be installed, enabled, and running on the server while you migrate.

After the migration is complete and you have confirmed the arenas work in AsyncArenasPlus, you can disable or remove the old plugin.

## Commands

Migrate using the first available source plugin:

```text
/arena migrate <name|all>
```

Migrate from a specific source plugin:

```text
/arena migrate <provider> <name|all>
```

Examples:

```text
/arena migrate all
/arena migrate asyncarenas all
/arena migrate arearesetterpro mine_1
```

## After Migration

Check the imported arenas:

```text
/arena list
/arena info <arena>
/arena reset <arena>
```

If you want a nicer public name, set one with:

```text
/arena displayname <arena> <new display name>
```
