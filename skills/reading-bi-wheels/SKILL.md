---
name: reading-bi-wheels
description: Use when the user asks for a synastry chart, a relationship chart, transits or progressions drawn around their birth chart, a solar or lunar return overlaid on the natal chart, or any two-ring chart, and the Open Ephemeris connector is available. Explains how to call explore_bi_wheel and how to read the inner ring, the outer ring, and the cross-aspects between them.
---

# Reading a bi-wheel

A bi-wheel draws two charts on one wheel. The value is in the cross-aspects, the aspects between a planet in one chart and a planet in the other.

## Call it

`explore_bi_wheel` takes two charts: `person1_*` and `person2_*` (datetime, latitude, longitude, timezone, name), plus `location` and `person2_location` as place names. `mode` sets what the second chart is:

- `synastry`: two people.
- `transit`: person 2 is a moment in time, such as today.
- `progressed`, `solar_arc`, `solar_return`, `lunar_return`: person 2 is the derived chart for the target date.

Collect both sets of birth data with the `birth-data-and-timezones` skill. For a text-only answer, use `ephemeris_synastry` (two people) or `ephemeris_natal_transits` (natal plus a moment).

## Read it in this order

1. **Say which chart is which.** Take the ring assignment and labels from the tool result. Do not assume which person is inside.
2. **Tightest cross-aspects first.** Sort by orb. Use the orbs the result reports, and give a tight aspect more weight than a wide one.
3. **Personal planets first.** Sun, Moon, Mercury, Venus, Mars and the Ascendant carry most of the day-to-day feel. Outer planets to personal points come next.
4. **Direction matters.** "Person 2's Venus trines person 1's Mars" is not the same statement as the reverse. Name the direction from the result.
5. **House overlays.** Where one person's planets fall in the other
