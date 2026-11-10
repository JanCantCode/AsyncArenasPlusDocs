---
title: Minecraft Arena Reset Countdown Placeholders
description: Display AsyncArenasPlus reset countdowns with PlaceholderAPI, including the next reset time and arena name across multiple saved arenas.
---

# PlaceholderAPI

AsyncArenasPlus registers PlaceholderAPI placeholders only when PlaceholderAPI is installed and enabled.

Identifier:

```text
asyncarenasplus
```

## Single Arena Reset Time

```text
%asyncarenasplus_reset_time_<arena>%
```

Returns the time until the arena's next periodic reset.

Examples:

```text
%asyncarenasplus_reset_time_mine_1%
%asyncarenasplus_reset_time_pvp_1%
```

Return values:

- `now`: reset time is due or overdue
- `never`: arena does not exist or has no next periodic reset scheduled
- a compact duration such as `45s`, `5m`, `1h 20m`, or `2d 3h 10m`

## Soonest Reset Time

```text
%asyncarenasplus_reset_soonest_time_<arena1,arena2,...>%
```

Returns the shortest reset countdown from a comma-separated arena list.

Example:

```text
%asyncarenasplus_reset_soonest_time_mine_1,mine_2,mine_3%
```

Return values:

- `never`: no listed arena has a scheduled next reset
- a compact duration such as `20s`, `4m`, or `1h 5m`

## Soonest Reset Name

```text
%asyncarenasplus_reset_soonest_name_<arena1,arena2,...>%
```

Returns the display name of the listed arena with the soonest scheduled reset.

Example:

```text
%asyncarenasplus_reset_soonest_name_mine_1,mine_2,mine_3%
```

Return values:

- `none`: no listed arena has a scheduled next reset
- the arena display name, if configured
- otherwise the arena's internal name

## Notes

- Arena names are comma-separated with no special escaping.
- Blank arena names in a list are ignored.
- Display names are configured with `/arena displayname <arena> <new display name>`.
- Placeholders use scheduled periodic reset times; manual resets do not create a future scheduled reset by themselves.
