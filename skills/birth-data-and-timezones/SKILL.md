---
name: birth-data-and-timezones
description: Use when the user gives a birth date, time or place, or asks for a chart of any kind, and the Open Ephemeris connector is available. Covers what to collect, how to resolve a place name to coordinates with location_search, how to pass the timezone, and what to do when the birth time is unknown.
---

# Collect birth data correctly

A chart is only as good as its inputs. A wrong timezone shifts the Ascendant by about 15 degrees per hour and can move every house.

## What to collect

- **Date** of birth.
- **Time** of birth, as the clock read at the place of birth. Ask whether it comes from a birth certificate, a memory or a guess.
- **Place** of birth: city and country (add region if the name is common).

Ask for all three together in one message. Do not start tool calls with a partial set, except for questions that need no birth data (the current sky, the current moon phase).

## Resolve the place

Most tools take latitude and longitude, not a place name.

1. Call `location_search` with the place (`query`, plus `country` or `region` if given).
2. If several places match, list them and ask which one the user means. Do not take the first result.
3. Use the coordinates from the result. Never type coordinates from memory.

The interactive `explore_*` tools also accept a `location` place name and resolve it themselves.

## Pass the time and timezone

- Pass the local clock time exactly as given, for example `1987-07-15T09:01:00`, and set `timezone` to the IANA zone name, for example `America/Chicago`. `timezone_resolve` returns the zone for a place and date if you need it.
- Or put the offset on the value (`1987-07-15T09:01:00-05:00`).
- A clock time with no zone is rejected. Do not assume UTC.
- Do not do the UTC conversion yourself. The server applies the historical daylight-saving rules for that exact date and place. A hand-converted value that carries a `Z` or an offset is trusted as written, so an off-by-one-hour mistake produces a confident, wrong chart.
- A bare date with no time is treated as 12:00 UTC. Say so if the user has no birth time.

## Unknown birth time

Say plainly which parts of a chart depend on the time: Ascendant, Midheaven, house cusps, and the Moon's exact degree. Offer sign-level readings for the planets, and label anything time-dependent as uncertain. For Human Design, a few minutes can change gates and lines; say that a rectified time is needed for a firm reading.

## Confirm before a large run

Batch and multi-year searches use more credits. State the scope and confirm it with the user first.
