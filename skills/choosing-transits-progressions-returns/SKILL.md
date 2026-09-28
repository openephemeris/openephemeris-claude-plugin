---
name: choosing-transits-progressions-returns
description: Use when the user asks what is coming up, about timing, a forecast, a year ahead, a birthday chart, a solar or lunar return, progressions, or when a particular aspect will be exact, and the Open Ephemeris connector is available. Helps Claude pick between transits, secondary progressions, solar arc, and returns and call the matching tool.
---

# Choosing a predictive technique

Pick the technique from the question, then call the matching tool. All dates come from tool results.

| The user asks | Technique | Tool |
|---|---|---|
| "What is happening in my chart right now / this week" | Transits at one moment | `ephemeris_natal_transits` (`transit_datetime`, default now) |
| "When will Saturn cross my Moon" or "what hits me this year" | Transit search over a date range | `ephemeris_transits` (`start_date`, `end_date`), or `explore_transit_timeline` for a visual list |
| "Show the transits against my chart" | Transit bi-wheel | `explore_bi_wheel` with `mode: "transit"` |
| "What is my inner development right now" | Secondary progressions | `ephemeris_progressed_chart` with `method: "secondary"` |
| "Big life chapters, slow themes" | Solar arc directions | `ephemeris_progressed_chart` with `method: "solar_arc"` |
| "What does my year ahead look like" or "my birthday chart" | Solar return | `ephemeris_solar_return` (set `return_latitude` and `return_longitude` to where they will be on the birthday) |
| "Monthly mood cycle" | Lunar return | `ephemeris_lunar_return` if it is available, or `explore_bi_wheel` with `mode: "lunar_return"` |

## How they differ

- **Transits** compare the sky now to the birth chart. They are the timing tool: fast planets show days, slow planets (Saturn to Pluto) show months and years. They describe the weather, not a fixed event.
- **Secondary progressions** move the chart forward one day per year of life. The progressed Moon changes sign about every two and a half years and gives the personal rhythm. Progressions are slow and inner.
- **Solar arc** moves every point by the Sun's progressed arc. It is a single yardstick, often used for outer events.
- **Returns** cast a new chart for the moment a planet comes back to its birth position. The solar return is cast for the birthday, and the place matters, so ask where the person will be.

## How to work

1. Say which technique you are using and why, in one sentence.
2. For a range question, search first (`ephemeris_transits`), then explain the few strongest hits. Do not list every minor contact.
3. Give exact dates only from the result, with the aspect and the planets involved.
4. Keep ranges reasonable. Very wide date ranges take longer and use more credits, so narrow to the period the user cares about.
5. Say what a technique cannot do. Timing techniques show themes and windows, not certain events.
