# 01 · The Cartographer

> Map the full ladder of mastery in a domain *before* you build anything in it.

This is the spine of the kit and the single prompt that would have caught this
repo's missing-foundation gap on day one. It refuses to let you start at the rung
you find exciting until you've seen the rungs below it.

- **Fire when:** at the very start of a new creative venture, or when entering a
  sub-domain you don't yet have a map of.
- **Engine:** research-heavy — run via the `deep-research` skill (or
  [`/cartographer`](../skills/cartographer.md)).
- **Pairs with:** feeds [`02-canon-finder`](./02-canon-finder.md),
  [`04-roots`](./04-roots.md), [`05-first-principles`](./05-first-principles.md)
  (each zooms into one part of the map it produces).

## The prompt

```
Before we build anything in <DOMAIN>, map the full ladder of mastery —
from "arithmetic" to "PhD." What are the layers, and in what order does a
serious practitioner actually learn them? Where does the canonical,
tried-and-true FOUNDATION live (the stuff everyone internalizes before
specializing)? My actual goal is <GOAL> — mark exactly which foundational
rungs I'd be skipping if we jumped straight there, and whether skipping
them is fine or a trap.
```

## Variables

- `<DOMAIN>` — the craft (e.g. "song construction", "narrative game design",
  "short-story writing", "typeface design").
- `<GOAL>` — the specific thing you actually want to build, so the map can mark
  your intended landing rung and what sits beneath it.

## What good output looks like

- A **layered ladder** (foundation → intermediate → specialized → frontier), not a
  flat list.
- An explicit **learning order** with prerequisites.
- A clear marker: *"your goal lands here; the rungs below it that you have not
  established are X, Y, Z."*
- A verdict per skipped rung: **safe to skip** vs **load-bearing trap**.

## The failure it prevents

Starting at the most exciting/visible rung (the "PhD work") because the model will
happily take you straight there. The map makes the skipped scaffolding *visible*
and *named*, so skipping becomes a decision instead of an accident.
