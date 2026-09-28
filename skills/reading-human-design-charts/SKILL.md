---
name: reading-human-design-charts
description: Use when the user asks for a Human Design chart, bodygraph, type, strategy, authority, profile, channels, gates or centers, or asks to compare two people's Human Design, and the Open Ephemeris connector is available. Tells Claude which tool to call and the order in which to read the result.
---

# Reading a Human Design chart

Human Design is computed from the birth moment and the moment about 88 degrees of solar arc before it. Open Ephemeris does both calculations. Do not derive any gate or channel yourself.

## Which tool

- The person wants to see the bodygraph, or says "show me my chart": `explore_human_design` (interactive). Input is `datetime`, plus either `location` (a place name) or `latitude` and `longitude`, plus `timezone`.
- The person wants the data as text, or you need to reason over it: `human_design_chart`.
- Two people, "how do we connect": `explore_human_design_connection`.
- "What is the sky doing to my design today": `explore_human_design_transit` (adds a transit overlay for `transit_datetime`, default now).

Collect birth data with the `birth-data-and-timezones` skill first. Human Design is time-sensitive: a few minutes can change a gate or a line.

## Read in this order

Read each item from the result, in this order, and state it before you interpret it.

1. **Type.** Manifestor, Generator, Manifesting Generator, Projector or Reflector.
2. **Strategy** for that type: Manifestor informs, Generator responds, Manifesting Generator responds and then informs, Projector waits for the invitation, Reflector waits through a lunar cycle before major decisions.
3. **Authority.** Use the authority the result gives. Do not re-derive it. The order of precedence is emotional, sacral, splenic, ego, self-projected, mental (environment), lunar.
4. **Profile** (for example 3/5) and what each line number means.
5. **Definition.** Single, split, triple split or quadruple split, or none for a Reflector.
6. **Centers.** Which are defined and which are open. An open center is where a person is receptive and can amplify others, so describe it as conditioning, not as a flaw.
7. **Channels and gates.** Name each defined channel by its two gate numbers and the name the result gives.
8. **Incarnation cross,** if the result provides it.

## Keep it honest

- Give the type, strategy and authority first. Everything else is detail.
- Use only the gate, channel and center names in the result. If you are unsure of a meaning, say so instead of inventing one.
- Present Human Design as a framework the person can test against their own experience, not as a prediction or a medical, legal or financial instruction.
- For a connection chart, describe which channels are electromagnetic, companionship, dominance or compromise only from what the result reports.
- If the birth time is uncertain, say which parts might change.
