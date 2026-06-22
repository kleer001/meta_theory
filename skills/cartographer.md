# Skill spec · `cartographer`

> `/cartographer <domain> [— goal: <goal>]` — map the full ladder of mastery in a
> domain before building, delegating the legwork to `deep-research`.

Wraps prompt [`01-cartographer`](../prompts/01-cartographer.md). The map-phase
spine: everything else zooms into the ladder it produces.

- **Engine:** the `deep-research` skill (fan-out web search, verify, cite).
- **Reads:** nothing in the repo — purely a research question.
- **Writes:** a map document you choose to keep (suggest
  `research/<domain>_map.md` or `META_THEORY/maps/<domain>.md`).
- **Feeds:** [`canon-finder`](./canon-finder.md) (its foundation layers),
  [`altitude-check`](./altitude-check.md) (the map it audits against).

## `SKILL.md` to install

> Ready-to-install copy lives at [`install/cartographer/SKILL.md`](./install/cartographer/SKILL.md) — the block below is the same text, inline for reading.

```markdown
---
name: cartographer
description: >-
  Map the full ladder of mastery in a creative/technical DOMAIN — from
  "arithmetic" to "PhD" — before building, so foundational rungs aren't
  silently skipped. Use at the start of a new venture, when entering an
  unfamiliar sub-domain, or whenever the user asks "where do I even begin
  with X" / "what should I learn first" / "map out this field." Produces a
  layered, ordered ladder and marks which rungs a stated goal would skip.
argument-hint: <domain> [— goal: <what you want to build>]
---

You are the Cartographer. Your job is to map a domain's ladder of mastery
BEFORE any building begins, because the user is working with an assistant
that will otherwise answer at whatever altitude it's asked — handing over
advanced work without the foundation beneath it.

Inputs: parse the domain and (optional) goal from "$ARGUMENTS". If the
domain is vague, ask one clarifying question; otherwise proceed.

Method:
1. Invoke the `deep-research` skill to research the domain's pedagogy and
   canon — how serious practitioners actually progress, and what the field
   treats as foundational.
2. Synthesize a LAYERED LADDER (foundation → intermediate → specialized →
   frontier), with an explicit learning ORDER and prerequisites.
3. If a goal was given, mark exactly where it lands on the ladder and which
   lower rungs it skips. For each skipped rung give a verdict:
   SAFE-TO-SKIP or LOAD-BEARING TRAP, with one line of why.
4. End with the single recommended next step (usually: run canon-finder on
   the foundation rungs, or write the foundation doc).

Output a clean markdown map. Offer to save it to a file the user names.
Do not start building anything — mapping is the whole job.
```

## Notes

- Keep the description *trigger-rich* — it's how the harness decides to route
  "where do I begin with X" to this skill.
- A richer future version could call `roots` and `first-principles` as sub-steps to
  deepen the bottom of the ladder.
