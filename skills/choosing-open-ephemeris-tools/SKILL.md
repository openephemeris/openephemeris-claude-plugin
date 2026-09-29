---
name: choosing-open-ephemeris-tools
description: Use whenever the Open Ephemeris connector is available and the user asks for a chart, a position, a moon phase, a retrograde, an eclipse, a Human Design chart, a forecast or a relationship comparison. Maps each kind of request to the right tool, including when to show an interactive chart and when to fetch raw data.
---

# Choosing the right Open Ephemeris tool

Two families exist. The `explore_*` tools return an interactive chart the user can click. The `ephemeris_*`, `human_design_chart`, `vedic_chart`, `acg_*` and `electional_*` tools return data you can read or calculate with. Pick by what the user needs.

## Show it, or give the numbers?

| The user wants | Tool |
|---|---|
| To see a birth chart, or "my big three" | `explore_natal_chart` |
| A chart as data: exact degrees, an aspect table, JSON | `ephemeris_natal_chart` (set the `format` argument to llm for a compact result) |
| To see a Human Design bodygraph | `explore_human_design` |
| Human Design activations, design and personality positions, as data | `human_design_chart` |
| To see a two-ring chart (synastry, transits, progressions, returns) | `explore_bi_wheel` |
| Cross-aspects between two charts as data | `ephemeris_synastry` |
| To see upcoming transits as a timeline | `explore_transit_timeline` |
| Transit hit dates as data | `ephemeris_transits` |
| To see the Moon right now | `explore_moon_phase` |
| The Moon's phase or sign at a past moment, as data | `ephemeris_moon_phase` |
| A Vedic chart: to see it / as data | `explore_vedic_chart` / `vedic_chart` |
| BaZi Four Pillars | `explore_bazi_chart`; `bazi_annual_pillar` for a single year |

## Everything else

| The user asks | Tool |
|---|---|
| "Where is Mars right now", "what is my sun sign" | `ephemeris_planet_position` |
| "Is Mercury retrograde now" (one instant) | `ephemeris_retrograde_status` with `planet_id` |
| "When does Mercury go retrograde or direct" | `electional_station_tracker` |
| "When is the next full or new moon" | `ephemeris_next_lunar_phase` |
| "When is the next eclipse" (add latitude and longitude for local visibility) | `ephemeris_next_eclipse` |
| House cusps, or Vertex and East Point | `ephemeris_house_cusps`, `ephemeris_angles_points` |
| Is this aspect within orb | `ephemeris_aspect_check` |
| What the sky is doing on a date, with no birth data | `electional_moment_analysis` |
| Best window to start something | `ephemeris_electional` (Pro) |
| Progressions and solar arc | `ephemeris_progressed_chart` |
| Solar return | `ephemeris_solar_return` (or `explore_bi_wheel` with `mode: "solar_return"` to see it) |
| A chart recast for a new city | `ephemeris_relocation` |
| Whole-world astrocartography lines | `acg_power_lines` (Pro) |
| Lines near one city | `acg_hits` (Pro) |
| A place name to coordinates and timezone | `location_search`; `timezone_resolve` when coordinates are already known |
| Credits, plan and usage | `account_usage` |
| Something no typed tool covers | `dev_read_api` (read-only GET endpoints); `dev_list_allowed` lists the paths |

## Habits that save credits

- Prefer one specific call over a sweep. `ephemeris_retrograde_status` costs 1 credit for one planet and 10 if you omit `planet_id`.
- Use a place name (the `location` argument) on the `explore_*` tools when you have one. They resolve it in the same call.
- Choose the interactive tool when the user wants to look at something, and the data tool when you need to reason over exact numbers. Do not call both for the same question unless the user asks for the numbers as well as the picture.
- Human Design and natal charts depend on the exact birth time. Confirm it before running.
