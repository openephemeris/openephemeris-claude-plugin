---
name: reading-astrocartography-lines
description: Use when the user asks about astrocartography, relocation, where to live or travel by their chart, planetary lines on a map, or how a specific city or place looks for their chart, and the Open Ephemeris connector is available. Covers the four line types, when to use acg_power_lines versus acg_hits, and how to state orbs and limits honestly.
---

# Reading astrocartography lines

Astrocartography maps where each planet in the birth chart was on an angle (rising, setting, overhead or underfoot) at the moment of birth. A place near a line puts that planet on an angle for someone relocating there.

## Tools and plan

- `acg_power_lines`: the lines for the chart. Inputs are `birth_datetime`, `timezone`, `birth_latitude`, `birth_longitude`, optional `bodies`, and optional `query_latitude`, `query_longitude` and `radius_deg` to look near one place.
- `acg_hits`: the lines and aspects that reach one place. Use it for "how is Lisbon for me". It needs the query coordinates.
- Both tools need the Pro plan. If the result says the plan does not include them, pass the plans link from the message on and offer a relocation chart (`ephemeris_relocation`) instead, which does not need Pro.

Resolve a city with `location_search` first, then pass its coordinates as the query point. Collect birth data with the `birth-data-and-timezones` skill. The birth time matters a lot here, because the Midheaven and the Ascendant lines move with it.

## The four line types

| Line | Meaning |
|---|---|
| AC (Ascendant) | The planet was rising there. It shapes how you present and how you are met. |
| DC (Descendant) | The planet was setting there. It shapes partnerships and who you attract. |
| MC (Midheaven) | The planet was overhead there. It shapes career, reputation and direction. |
| IC (Imum Coeli) | The planet was underfoot there. It shapes home, family and roots. |

## How to read a result

1. Name each line from the result: planet, then line type.
2. Give the distance from the place using the result. If you convert degrees to distance, say it is approximate: one degree of latitude is about 111 km.
3. A close line matters more than a distant one. Say how close it is. Do not call a line "on" a city unless the result puts it within the orb.
4. Read the planet's nature and the line's theme together (for example Venus on the DC for relationships, Saturn on the MC for weighty career pressure). A hard planet is a challenge with a use, not a ban.
5. Weigh several lines together. Two supportive lines and one hard line is a mixed picture. Say so.
6. Ask what the person wants (career, love, rest, growth) before ranking places.

## Be straight about limits

- Astrocartography is a symbolic tradition. The line positions are exact calculations, but the meanings are interpretation. Say that in a sentence.
- The lines do not account for local safety, visas, cost or personal circumstances. Do not tell someone to move because of a line.
