---
name: ground-positions-in-tool-results
description: Use whenever the user asks about planetary positions, houses, aspects, moon phases, retrogrades, eclipses, Human Design gates, transit dates or any other astronomical or chart value, and the Open Ephemeris connector is available. Every such value must come from a tool result in this conversation, never from memory. Also use when a tool returns a credit-limit, plan or rate-limit error.
---

# Ground every position in a tool result

Open Ephemeris computes from the NASA JPL DE440 ephemeris. Recalled positions are often wrong by degrees, and a wrong degree changes the sign, the house, the aspect or the Human Design gate.

## The rule

State a position, degree, sign, house, aspect, orb, phase, retrograde status, eclipse date, gate, line or transit date only if it appears in a tool result from this conversation. This holds even for "easy" ones such as today's Moon sign or a well-known person's Sun sign.

## How to apply it

1. Before answering any astronomical or chart question, pick the tool that returns the value and call it. If no birth data is needed, do not ask for any. "What is the sky doing now" needs no birth date: call `explore_moon_phase` or `ephemeris_planet_position` with no birth details.
2. Quote values exactly as returned (sign, degree and minute). Do not round a degree into a different sign.
3. If a tool has not been called yet for a value, say so and call it. Do not fill the gap with an estimate.
4. When you interpret, keep the two layers separate: the computed fact (from the tool) and your reading of it. Say which is which if the user could confuse them.
5. If a result looks wrong to you, re-check the inputs (time, timezone, place) with the `birth-data-and-timezones` skill. Do not overrule the tool from memory.
6. Prefer `format: "llm"` on data tools when offered. It returns the same numbers in a compact form.

## When a tool cannot run

The server reports why in plain text. Pass the useful part on to the user and stop; do not invent the missing data.

- **Credit limit reached.** The account has run out of credits. The message includes a top-up link and a plan link. Show the user the link from the message as it is written and say what the options are. New accounts get 150 credits that do not expire.
- **Plan required.** Some tools (astrocartography, electional window search) need the Pro plan. Say which capability is gated, link the plans page from the message, and offer what is available on the current plan.
- **Rate limit.** Wait a moment and retry once. If it fails again, tell the user.
- **Not signed in or session expired.** Ask the user to reconnect the Open Ephemeris connector.

## Never

- Never recall coordinates for a city. Use `location_search`.
- Never convert a local time to UTC by hand. Pass the local time and the IANA timezone name and let the server resolve the offset.
- Never present a remembered value as "from the ephemeris".
