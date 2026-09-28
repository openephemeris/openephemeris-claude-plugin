# Open Ephemeris plugin for Claude

This plugin adds seven skills that make Claude accurate and consistent when it uses the
[Open Ephemeris](https://openephemeris.com/astrology-mcp) connector. Open Ephemeris computes
planetary positions from the NASA JPL DE440 ephemeris (sub-arcsecond precision, 1550–2650 CE) and
exposes natal charts, transits, progressions, returns, Human Design, bi-wheels, moon phases and
astrocartography as MCP tools.

## What is in the bundle

| Piece | What it does |
|---|---|
| `.mcp.json` | Connects to the hosted server `https://mcp.openephemeris.com/mcp`, the same server as the directory connector. Sign-in is OAuth in the browser. There are no keys to paste. |
| `skills/ground-positions-in-tool-results` | Every position, degree, house, gate or date comes from a tool result, never from memory. Also covers running out of credits. |
| `skills/birth-data-and-timezones` | Collect date, time, place and timezone correctly, and resolve places with `location_search`. |
| `skills/reading-human-design-charts` | Read a Human Design bodygraph in the right order: type, strategy, authority, definition, profile, centers, channels. |
| `skills/choosing-transits-progressions-returns` | Pick the right predictive technique for the question and the right tool for it. |
| `skills/reading-bi-wheels` | Read synastry, transit, progressed and return bi-wheels without mixing up the two rings. |
| `skills/choosing-open-ephemeris-tools` | Which tool answers which kind of request: interactive chart versus raw data, and the cheapest correct call. |
| `skills/reading-astrocartography-lines` | Read astrocartography lines and city hits, with the line types and orbs stated. |

## Before you use it

- You need a free Open Ephemeris account. The first sign-in creates it. New accounts get 150 credits that do not expire.
- Most tools work on the free plan. Astrocartography (`acg_power_lines`, `acg_hits`) and electional window search need Pro.
- Each tool call uses credits. When credits run out, the tool returns a clear message with a top-up link, and the skills tell Claude to pass it on.

## Data and privacy

Birth date, time and place are personal data. They are sent to the Open Ephemeris API only to compute the result you asked for.
The API does not save the birth details you send to a database. Results sit in server memory for a few minutes at most. It does keep usage metadata (which endpoint, when, how many credits).
Full detail: <https://openephemeris.com/privacy>. Support: support@openephemeris.com.

## Install

Add the plugin from the Claude directory (Customize > Plugins) and connect the Open Ephemeris connector when prompted.

To try it locally in Claude Code, clone this repository and run `claude --plugin-dir ./openephemeris-claude-plugin`.

## Licence

MIT. See `LICENSE`.
